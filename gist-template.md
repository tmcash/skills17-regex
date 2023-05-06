# Regex for Email

The tutorial will explain the different components used in a regular expression for validating an email address in a form or any other application.

## Summary
 Regex: `^[a-z0-9\.-_]+@[a-z0-9\.-]+\.[a-z]{2,6}$`


This regular expression will validate supplied text to verify that the text follows these rules:
*  User name part of the email must contain 1 or more of the following:
  * lowercase alpha characters
  * digits
  * underscore
  * period (dot)
  * dash
* after the user name, there must be an at sign: @
* After the at sign will be  domain name, which consists of 1 or more:
  * digits
  * lowercase alpha characters
  * period (dot)
  * dash
* domain name must be followed by a period (dot)
* the last part of an email is the domain (com, gov, org, etc), which consists of 2 to 6 lowercase alpha characters

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Author](#author)

## Regex Components

### Anchors

The email expression uses two anchors, ^ and $:
 * `^` matches the beginning of a string
 * `$` matches the end of a string

For example, while 'abc<span>@</span>gmail.com' matches the expression in this tutorial, 'Aabc<span>@</span>gmail.com' does not. 'A' is not a valid character for the username part of the email address, and the 'abc' is not at the beginning of the string, which causes it to fail the match. Similarly for 'abc<span>@</span>gmail.coM': 'M' is not a valid character and the 'co' does not occur at the end of the string, and this makes the match fail.
 
### Quantifiers

Two quantifiers are used in this expression:
* `{2, 6}`
  * The domain part of the email contains `{2, 6}`. This quantifier means that the domain must contain at least 2 valid characters and at most 6 valid characters.
* `+`
  * Both the username and domain name use `+` to require that each one must have at least 1 valid character.

For example, 'a<span>@</span>b.com' is valid: It has 1 or more characters for both the user name and the domain name, 2 or more characters for the domain. 'a<span>@</span>b.c' is not valid: it only has 1 character for the domain.

### OR Operator

One OR operator, `[]`, is used in three parts of the expression: the username, the domain name, and the domain. Any characters between the braces is allowed, i.e. 'this character OR this character OR this character' etc. The allowed characters for each part can be see in the [Summary](#summary) above.

### Character Classes
* lowercase alpha characters cna only utilize `a-z`
* digits are y `0-9`
* period (dot) is a special character and must be escaped, i.e. preceeded by `\`, to be interpreted correctly: `\.`.
* underscore and dash are indicated by `_`  and `-`, respectively.

### Bracket Expressions
For the regular expression in this tutorial, the bracket expression, `[]` is used as an OR expression.

### Greedy and Lazy Match
The curly braces `{}` used in the domain portion of the email are used as a greedy operator. That is, they will expand the match as far as they can through the text that is being tested.

## Author
Tyler Cash is a junior web developer and maybe contacted though Github:
https://github.com/bjackels5