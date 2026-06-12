---
title: "Searching text by regexp (not Grep!)"
date: 2008-09-21
forum: The Cafe
---

### Post by speedsix on 2008-09-21
I want a command line tool that can search some text (file or piped input) using regular expressions AND that can return only the part of the expression I specify, any ideas?

Grep searches line by line and afaik can't return only parts of a regular expressions.

Sed is purely for editing text is it not?


Thanks

---

### Post by speedsix on 2008-09-22
Anyone? :KS

---

### Post by Yannick Le Saint kyncani on 2008-09-22
Hi speedsix,

I usually use perl or sed for that.

There is egrep too (to some extent).

They all do different things, perl being the heavier but more powerful solution.

Example using sed :

cat file | sed '/reg.*exp/!d; s/^.*\(reg.*exp\).*$/\1/'

Of course, you will have to learn using sed for yourself, get some documentation on the web. Perl is another thing, you cannot use it if you don't spend (much?) time learning the language.

Just my .02$

---

### Post by koenn on 2008-09-22
> **speedsix said:**
> I want a command line tool that can search some text (file or piped input) using regular expressions AND that **can return only the part of the expression I specify**, any ideas?
Thanks

"return only the part of the expression I specify" doesn't seem to make sense. If you only want a partial match of your regexp, your regexp is too wide and you should narrow it down, no ? Or am i missing something ?

other than that, grep is exactly what you want. If I'm not mistaking, ' grep -e ' allows extended regexp syntax, allowing matchas on start and end of word etc, if that's what you"re after. 

As for piping and searching file, grep will do all that. It will read any text you feed it, ether from a pipe, a file, or all files in a given directory

---

### Post by spupy on 2008-09-22
Try this command:
```
man grep
```

In particular:
>        -E, --extended-regexp
              Interpret PATTERN as an extended regular expression (see below).

       -e PATTERN, --regexp=PATTERN
              Use PATTERN as the pattern; useful to protect patterns beginning
              with -.

>        -o, --only-matching
              Show only the part of a matching line that matches PATTERN.

Your grep-fu is not strong enough!

---

### Post by speedsix on 2008-12-13
But the pattern is sometimes the minimum required to match the line I want but more than I actually want to show, if that makes sense.

For example if I want to grep just the temperature reading (i.e 35c) for 'temp2' from the sensors output

chipset sensor blah01
temp 1  45c
temp 2  35c (max 70c)


Grepping temp2 will give me the correct line but I only want the 35c bit. Returning only the pattern will still give me the temp2 at the start of the line.

---

### Post by koenn on 2008-12-13
wow, 3 months later and you're still worrying about this ? :)

with your example in a file 't' :
```

:~$  grep 'temp 2' t |grep -o "[0-9]*c "
35c

```
the first grep selects the line with temp 2; the second grep selects the 35c-part from that line

in this case, where the output is formatted in fields and delimiters, you can also use cut
```
grep 'temp 2' t | cut -d' ' -f3 -

```
i.e. return the 3rd field (using space ' '  as delimiter)

---

