---
title: "[SOLVED] 'expr' command problems"
date: 2008-06-19
forum: Server Platforms
---

### Post by Richard_ on 2008-06-19
For some reason I'm unable to get **expr** to work with any parameters on strings that contain spaces. For example,


This works:
```
$ temp='Fantastic'
$ expr substr $temp 1 3
Fan
```


Whereas this doesn't:
```
$ temp='Fantastic work'
$ expr substr $temp 1 3
expr: syntax error
```

The only difference is the added space. This problem occurs for all parameters of **expr**, including the length parameter.
Suggestions welcome. :-)

---

### Post by pedro_orange on 2008-06-19
temp = "white space in string"
echo temp: $temp

---

### Post by Richard_ on 2008-06-19
> **pedro_orange said:**
> temp = "white space in string"
echo temp: $temp

In the way that I originally posted, I am able to echo the variable without problems. It's only once I pass it to expr that I have a problem.

---

### Post by pedro_orange on 2008-06-19
Aye spaces are weird in bash script variables.

Quotes seem to act differently in interactive shells compared to automated. 

There is some method to do it, however it's been a long time since I've written a script. 
I'm pretty sure having double quotes around it in a script makes a difference, but that might just be to do with $variables within the "s.

---

### Post by Richard_ on 2008-06-19
Thanks! You put me onto something, and after a quick Google I came across a solution [here]("http://www.unix.com/shell-programming-scripting/35417-difference-between-double-inverted-coma-single-inverted-comma.html"). The following taken from the aforementioned site:

```
if [ -f $filename ] translates $filename - if it has spaces the shell "thinks" $filename
         is really separate values  with no spaces
if [ -f "$filename" ] translates $filename - if it has spaces the shell "thinks" $filename
         is realy one single value, spaces included
if [ -f '$filename' ] does not translate filename - the shell takes the $ literally, not
         as a shell token meaning return the value of a variable
```

So basically, my problem is solved by adding double quotes around the variable name:

```
$ temp='Fantastic work'
$ expr substr [COLOR="Red"]"[/COLOR]$temp[COLOR="#ff0000"]"[/COLOR] 1 3
Fan
```

---

