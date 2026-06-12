---
title: "what language is not safe to write script that will run as root?"
date: 2009-03-05
forum: Security
---

### Post by q.dinar on 2009-03-05
what language is not safe to write script that will run as root?
i think language interpreter will run as root and it should be trustable and checked. the most safe is sh script i think.
is sh, bash, zsh and other variations i have heard - different interpreters of similar languages?
what about php, perl, python?

i think it is possible to read file and split strings with sh language, is it?

---

### Post by bodhi.zazen on 2009-03-05
Writing secure scripts is not so much language dependent as it is in being aware of how security works.

Any script can be written with more or less security in mind.

Any script to be run as root (via sudo) should be owned by root and non-root users should not be able to modify the code for example.

---

### Post by HermanAB on 2009-03-05
English
;)

Herman

---

### Post by q.dinar on 2009-03-06
i have written the topic title erroneous, i mean not language, but interpreter.

---

### Post by albandy on 2009-03-06
it depends in your way of programming, if you allow parameters or not, if you use pointers or not, or the way you control loops, if you do forks, ...

---

