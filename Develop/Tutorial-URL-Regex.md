# RegEx URL 

This tutorial will show regular expressions, or known as regex. URL regular expressions can be used to verify if a string has a valid URL format as well as to extract a URL from a string. The URL pattern is /^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/, which uses special characters (or metacharacters) to decrypt specific URLs and paths, URL Regex is used to match URLs.

## Summary

The regex that I will be describing:

Match a URL: /^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/

Code snippet:

var expression = /^(https?://)?([\da-z.-]+).([a-z.]{2,6})([/\w .-])/?$/; var regex = new RegExp(expression); var d = 'https://uh.edu/about';

if (d.match(regex)) { alert("Successful match"); } else { alert("No match"); }

Output: String that matches:

https://uh.edu/about

String that doesn't match:

http://uh.edu/fake/web!.com (has an exclamation point)

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components
We can break down this expression into its individual elements in order to understand how it works. The individual elements are described below:

The grouping for URL matching is broken apart into four sections, starting with (https?:\/\/) for URL prefixing. This is followed by ([\da-z\.-]+) which matches any characters within the /d character class with either an escaped . or - afixed to the end, also containing a + quantifier for larger character sets. The third group is ([a-z.]2,6), which is only allowed to contain the 2-6 characters found in the 2-6 and is often used to match the domain name (most frequently .com). The fourth and final group is ([/w.-]*), which corresponds to pathing for sub-pages within a URL; the * qualifier indicates that this component of the grouping can be repeated as many times as required.

The grouping is split into four portions to match the URLs. The first is the URL prefix (https? :/). The second is ([da-z.-]+), which matches any character in the /d character class with an escaped. or - as a + quantifier at the end.


### Anchors
The at the ^ and the $ at the end of this regex expression serve as the two main anchors and represent an exact string match with the elements contained within the two anchors.

The symbol "^" designates an exact string match and a string that starts with the letters immediately after it. A string that ends with the characters before it is denoted by the $ anchor. It can be preceded by an exact string or a range of potential matches, much like with the ^ character.

We are requesting that the search function match exactly what is contained between these two anchors by encapsulating the regex between them.

### Quantifiers
The string boundaries that your regex matches are defined by quantifiers (or an individual section of the string). The minimum and maximum characters that your regex is looking for are typically included in them. Quantifiers are also used to specify how many times a particular expression can be recognized.

The quantifiers used in the expression above are?, *, and.

A single instance of the character before the quantifier can be optional with the? symbol, whereas several instances can be optional with the *.

- (https?:\/\/)?

The first capturing group mentioned above is optional. The URL can either start with http://, https://, or neither of those (the input begins with www.). The / at the very end of the statement has the same meaning.

URLs with http or https are permitted thanks to the? following the s. This entire group is made optional by appending a ? to the end of it.

- ([\/\w \.-]*)*

The above expression is optional thanks to the *, although there may be one or more optional instances in this situation. Any amount of filepath characters that may come after the first specified domain are permitted by the phrase.

The optional files and directories are in this section. We are looking for any combination of forward slashes, characters, digits, underscores, spaces, dots, and hyphens within the group. Then we declare that we can match this group several times if we so choose. This makes it possible to match several directories and a file at the end. Because the star indicates zero or more rather than zero or one, I've used it in place of the question mark.

- {2,6}

Finally, the {} quantifier specifies a range of scenarios in which a match might be found. The top level domain can have between 2 and 6 characters when it is evaluated by the regular expression.

### Grouping Constructs
Parentheses are used to do the grouping in a regex (). When we look at the expression, we can see that it has several parts that are separated by parentheses (). Regex uses parentheses to distinguish groupings of interests. There is a regex within each of these groups that we can examine independently to see what gets evaluated. These consist of:

- The initial https component: (https?:\/\/)
- The domain name: ([\da-z.-]+)\.
- The top level domain: ([a-z\.]{2,6})
- The file path: ([\/\w \.-]*)*

### Bracket Expressions
Anything enclosed in a set of square brackets is referred to as a bracket expression ([]). These patterns, which are sometimes referred to as positive character groups since they outline the characters we want to include, are known as bracket expressions. These expressions can be written to match any combination of characters. The expressions for brackets are as follows:

- [\da-z\.-]
The above expression matches for any digits (\d) OR any characters between a and z (a-z) OR any '.' (\.) OR any '-' (-).

- [a-z\.]
Same as the above excluding the digits.

- [\/\w \.-]
The above expression matches for any file path and it could include . or -.

### Character Classes
The d character class, which searches for any digit, and the w character class, which searches for any alphanumeric letter, are the two key character classes to take into account in the aforementioned expression.

Additionally,. matches any characters except than the newline (n).

### The OR Operator
The [ is the primary OR operator in the regex above. Any characters or character classes contained within the brackets will match the expression. For instance:

- [\da-z\.-] expression matches for any digits (\d) OR any characters between a and z (a-z) OR any '.' (\.) OR any '-' (-).

### Flags
After the second slash at the end of a regex, flags are added to describe any additional functionality or restrictions for the regex. They consist of:

- g for global search
- i for case-insensitive search
- m for multi line search

### Character Escapes

The backslash () in a regex allows a character that would otherwise be taken literally to escape. For instance, placing a backslash before an open curly brace () instructs the regex to search for that character rather than starting to define a quantifier.

Inside bracket expressions, all special characters—including the backslash ()—lose their unique meaning.

In the URL regex mentioned above, there are no character escapes.

## Author

This regex tutorial was created by Nico Vicinanza 

GitHub profile: https://github.com/nvici 
