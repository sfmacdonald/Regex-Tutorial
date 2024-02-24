# Regex Tutorial

Welcome to a tutorial on Regular Expressions (regex), powerful tools for searching, matching, and manipulating text. They allow developers to define search patterns in a compact and expressive format. Whether you're validating user input, searching for specific patterns in text, or performing complex text manipulations, leveraging regex is an invaluable skill for any web developer. The main intention of this tutorial on regex is to break down its components and explain how they work together to define search patterns.

## Summary

In this tutorial, we will explore specific regex patterns and dissect its components to understand the search pattern it defines. It shall cover anchors, quantifiers, the OR operator, character classes, flags, grouping and capturing, bracket expressions, greedy and lazy matches, boundaries, back-references, and look-ahead and look-behind assertions. By the end of this tutorial, you'll have a solid understanding of how to use these components to craft effective regex patterns for your web development projects.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Matches](#greedy-and-lazy-matches)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)
- [Pracitcal Example](#practical-example)
- [Author](#author)

## Regex Components

### Anchors
Anchors match positions rather than characters. They are essential for specifying the boundaries of your search pattern.

1. '^' =  start of string
    - Example: '^Hello' matches any string that starts with "Hello".
2. '$' = end of string
    - Example: 'world$' matches any string that ends with "world".

### Quantifiers
Quantifiers determine the required occurrences of a character, group, or character class for a match.

1. '*'  = zero or more occurrences
    - Example: 'lo*' matches "l" followed by any number of "o"s.
2. '+' = one or more occurrences
    - Example: 'lo+' matches "l" followed by at least one "o".
3. '?' = zero or one occurrence
    - Example: 'lo?' matches "l" with or without an "o".
4. '{n}' = exactly n occurrences
    - Example: 'lo{2}' matches "loo".
5. '{n,m}' = between n and m occurrences inclusive
    - Example: 'lo{1,3}' matches "lo", "loo", or "looo".
6. '{n,}' = at least n occurrences
    - Example: 'lo{2,}' matches "loo" or more "o"s.

### OR Operator
The OR operator, denoted by |, allows for the matching of either one pattern or another. It's useful for searching multiple possible variations of a pattern within a text.

1. '|' = "OR" operator
   - Example: '(cat|dog)' matches either "cat" or "dog".

### Character Classes
Character classes match any one of a set of characters at a point in the pattern.

1. '\d' = any digit (0-9)
    - Example: '\d'+ matches "123" in "The numbers are 123 and 456".
2. '\w' = any word character (letters, numbers, underscores)
    - Example: '\w+' matches "Hello" in "Hello World_123".
3. '\s' = any whitespace character (\t, \n, \f, \r)
    - Example: 'Hello\sWorld' matches "Hello World" when there is a space between "Hello" and "World".
4. '\D' = non-digit characters
    - Example: '\D+' matches "The numbers are " in "The numbers are 123 and 456".
5. '\W' = non-word characters
    - Example: '\W+' matches ", " in "Hello, World_123!".
6. '\S' = non-whitespace characters
    - Example: '\S+' matches "Hello" in "\n\t Hello World".
7. 'a-z' = lowercase letters
    - Example: '[a-z]+' matches "hello" in "Hello world".
8. 'A-Z' = uppercase letters
    - Example: '[A-Z]+' matches "HELLO" in "HELLO World".

### Flags
Flags modify the behavior of the regex pattern.

1. 'i' = case isensitive
    - Example: '/hello/i' matches "Hello", "hello", "HeLLo".
2. 'g' = global search (find all instances rather than stopping after first match)
    - Example: '/hello/g' finds all "hello" instances.
3. 'm' = multiline search (^ and $ match beginning/end of each line)
    - Example: '/^hello/m' matches "hello" at the start of any line.
4. 's' =  dotall search where '.' matches anything except newline
    - Example: /hello.world/s matches "hello\nworld"

### Grouping and Capturing
Groups and captures allow for the combination of multiple characters into a single unit for operations like matching, quantification, or applying operators. Capturing groups also save the matched substring, which can be referenced later in the pattern.

1.  '()' = captures for backreferencing.
    - Example: '(abc)\1' matches "abcabc".
2.   '(?: ...)' = non-capturing group; does not affect backreferences
    - Example: The regex (?:abc)+ matches one or more repetitions of "abc" like "abc", "abcabc", but does not capture "abc" for back-referencing.

### Bracket Expressions
Bracket expressions '[]', match any one character inside the brackets.

1. '[a-z]' = single character in the range a to z
    - Example: '[a-z]+' matches a lowercase word like "hello".
2. '[^a-zA-Z]' = single character not in the range a to Z
    - Example: '[^a-zA-Z]+' matches non-letter characters

### Greedy and Lazy Matches
Greedy quantifiers match as much of the string as possible, while lazy quantifiers match as little as possible, stopping at the first successful match. The lazy quantifier is denoted by adding a ? after the greedy quantifier.

1. '*' = greedy - match as many as possible
    - Example: 'a*' matches as many "a"s as possible.
2. '?' = lazy
    - Example: 'a*?' matches the shortest possible string of "a"s.

### Boundaries
Word boundaries (\b) match positions where a word character is followed by a non-word character, or vice versa. They're crucial for ensuring matches occur at the beginning or end of words.

1. '(\b)' = word boundary
    - Example: '\bcat\b' ensures "cat" is a distinct word.
2. (\B) = not word boundary
    - Example: '\Ban\B' finds "an" within a larger word such as "fantasy."

### Back-references
Back-references allow a regex pattern to match the same text as previously matched by a capturing group. They're denoted by \n, where n is the number of the capturing group.

1. '\n' = backreference to nth captured group
    - Example: '(a)(b)\1\2' matches "abab".
2. '\k<name>' = named backreference
    - Example: '(?<word>\w+)\k<word>' matches repeated words like "hello hello".

### Look-ahead and Look-behind
Look-ahead and look-behind assertions enable the matching of patterns based on what comes before or after them without including those parts in the match. They're crucial for complex pattern matching scenarios.

1. '(?=...)' = Positive look-ahead. 
    - Example: '\d(?=px)' matches digits followed by "px" without including "px".
2. '(?!...)' = Negative look-ahead. 
    - Example: '\d(?!px)' matches digits not followed by "px".
3. '(?<=...)' = Positive look-behind. 
    - Example: '(?<=\$)\d+' matches digits preceded by a dollar sign.
4. '(?<!...)' = Negative look-behind. 
    - Example: '(?<!\$)\d+' matches digits not preceded by a dollar sign.

## Practical Example

'/\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b/g'

This example demonstrates a regex pattern that matches emails. The pattern is dissected into its components as follows:

- '/\b' and '\b/' are word [boundary](#boundaries) anchors. They ensure that the matched substring is an entire word, not a part of a word. This helps to prevent the regex from matching email-like patterns embedded in longer strings that aren't emails.

- '[A-Za-z0-9._%+-]+' is a [bracket expression](#bracket-expressions) matching the local part of an email address. This part can contain:

    - Uppercase letters A-Z
    - Lowercase letters a-z
    - Digits 0-9
    - Dots .
    - Underscores _
    - Percent signs %
    - Plus signs +
    - Hyphens -

    The '+' [quantifier](#quantifiers) means "one or more of the preceding element," allowing for any combination of these characters of any length greater than one.

- '@' is a literal character that matches itself. It is used here to separate the local part of the email from the domain part.

- '[A-Za-z0-9.-]+' is also a [bracket expression](#bracket-expressions) matching the domain name of an email address. This part can contain:

    - Uppercase letters A-Z
    - Lowercase letters a-z
    - Digits 0-9
    - Dots .
    - Hyphens -

    Similar to the local part, the '+' [quantifier](#quantifiers) allows for any combination of these characters of any length greater than one.

- '\.' is a literal dot character. It's used here to denote the separation between the domain name and the top-level domain (TLD) of an email address.

- '[A-Z|a-z]{2,}' is another [bracket expression](#bracket-expressions) matching the TLD of an email address. It can contain:

    - Uppercase letters A-Z
    - Lowercase letters a-z

    The '{2,}' [quantifier](#quantifiers) means "two or more of the preceding element," allowing for TLDs that are at least two characters long. The inclusion of the pipe symbol '|' inside a character class is unnecessary and doesn't alter the matching behavior; it's treated as a literal character within the class, though in this context, it doesn't impact the matches since the class already covers all letters.

- 'g' is a [flag](#flags) that stands for "global." It allows the regex engine to find all matches within the input text, rather than stopping after the first match.

Leveraging https://regexr.com/, we can test our regular expression with different inputs to see if it works as expected. This is confirmed in the screenshot below:

![Regex Example](<./Screenshot 2024-02-24 at 2.15.59 PM.png>)

## Author

This tutorial was created by Sean MacDonald, currently a student enrolled in the Arizona State University Coding Bootcamp. Visit my [GitHub profile](https://github.com/sfmacdonald) to view my portfolio. 