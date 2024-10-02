# Intro
> This repo contains two files:
1. `script.php`: Bracket Balance Checker
2. `duplicate_records.sql`: SQL query to find non-unique id values a in a table

# Project Overview

### script.php :
    <?php
        function checkBracketsBalance($expression) {
        // Closing brackets
        $pairs = [
        ')' => '(',
        ']' => '[',
        '}' => '{'
        ];
        $stack = [];
        
            for ($i = 0; $i < strlen($expression); $i++) {
                $char = $expression[$i];
        
                // If chat is opening brackets add to stack
                if (in_array($char, $pairs)) {
                    $stack[] = $char;
                } elseif (isset($pairs[$char])) {  //if it is closing bracket
                    if (empty($stack) || array_pop($stack) !== $pairs[$char]) {
                        return "Неправильно";
                    }
                }
            }
            return empty($stack) ? "Правильно" : "Неправильно";
        }
        
        $expression = "[({})]";
        echo checkBracketsBalance($expression); // Вывод: Правильно

### duplicate_records.sql :
    SELECT id
    FROM table
    GROUP BY id
    HAVING COUNT(id) > 1;
