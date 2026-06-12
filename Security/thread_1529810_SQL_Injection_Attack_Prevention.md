---
title: "SQL Injection Attack Prevention"
date: 2010-07-12
forum: Security
---

### Post by ChrisEiffel on 2010-07-12
I've been protecting my website from sql injection attacks by always filtering out three characters from database input and substituting them for other characters.

'  "  \     I always replace with & #39; & #34; & #92;

So say I have a search query 

SELECT * FROM stuff WHERE search LIKE "%{$user_input}%"; 

(either with double or single quotes)

That way if 

someone enters:    a"; drop table stuff
                            \ 
                            a' drop table stuff
                           
it gets replaced with

                          a& #34; drop table stuff
                          & #92;
                           a& #39; drop table stuff

Is this enough to prevent a sql injection attack or do I need to filter/change more? Specifically { and } are suspect

Thanks

---

### Post by ChrisEiffel on 2010-07-12
Hmm looking at some default PHP security

mysql_real_escape_string();

It escapes several more characters

**"mysql_real_escape_string()** calls 
MySQL's library function
   mysql_real_escape_string, which prepends backslashes to the following
 characters:
   *\x00*, *\n*,
   *\r*, *\*, *'*,
   *"* and *\x1a*."

[http://php.net/manual/en/function.mysql-real-escape-string.php](http://php.net/manual/en/function.mysql-real-escape-string.php)

---

### Post by JK3mp on 2010-07-12
Definately easier to use mysql_real_escape_string() function. Be sure to filter EVERY variable that passes through the SQL db.

---

