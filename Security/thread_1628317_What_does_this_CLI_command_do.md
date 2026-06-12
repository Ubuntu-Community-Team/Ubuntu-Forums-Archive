---
title: "What does this CLI command do?"
date: 2010-11-22
forum: Security
---

### Post by nalgarryn on 2010-11-22
```
find / -name libjava.so 2> /dev/null
```

It supposedly finds the file named (identifies the path of your java install) but I don't understand the 2> /dev/null. I know what /dev/null is, but I don't understand "2>"; is this like the 'else' part of IF ... ELSE ... ?

Thanks.

---

### Post by matt_symes on 2010-11-22
Hi

> **nalgarryn said:**
> ```
find / -name libjava.so 2> /dev/null
```It supposedly finds the file named (identifies the path of your java install) but I don't understand the 2> /dev/null. I know what /dev/null is, but I don't understand "2>"; is this like the 'else' part of IF ... ELSE ... ?

Thanks.

That will redirect any errors to /dev/null. I.e not display them the screen.

Errors could be permission denied when trying at access a folder as a user

Kind regards

---

### Post by endotherm on 2010-11-22
I believe the command is actually:
```
find / -name libjava.so.2 > /dev/null
```

.so.# is a common suffix for a library. 

the > char redirects the output of a command to a file, instead of to the command window.

try running
```
netstat -ntlup
```

and then try
```
netstat -ntlup > netstat.txt
```

when you run the first command, you get lots of output, but when you run the second one, the output is placed in ~/netstat.txt

redirecting output to /dev/null basically drops teh data into a bottomless hole, never to return. it jsut throws it away. the reason you do that, is because find -name returns a line for every file it searches, not jsut those found.

---

### Post by FuturePilot on 2010-11-22
> **endotherm said:**
> I believe the command is actually:
```
find / -name libjava.so.2 > /dev/null
```


No it really is 2>
As stated above it redirects only errors to /dev/null.
Using just a redirect '>' will spit out a bunch of permission denied errors.
```
$ find / -name libjava.so 2> /dev/null
/usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/amd64/libjava.so
$
```

---

### Post by endotherm on 2010-11-22
interesting. so i presume 1 is stdout then?

---

### Post by matt_symes on 2010-11-22
Hi 

> interesting. so i presume 1 is stdout then?Yes.

0 is stdin
1 is stdout
2 is stderr

Kind regards

---

### Post by nalgarryn on 2010-11-30
> **matt_symes said:**
> 

0 is stdin
1 is stdout
2 is stderr

Kind regards

Stupendous! Thanks guys.

---

### Post by apollothethird on 2010-11-30
> **nalgarryn said:**
> Stupendous! Thanks guys.

By the way, there are some occasions where you want to see the error messages.  For some reason, some programs will output important information to the stderr?  An example if the command wput (a featured cli upload utility).

If you wanted to page view the help output you'd have to capture the stderr.

Notice:

This would output more information than will fit on one screen and you might miss the option you're looking for.

```
wput --help
```

If you tried to send the information to a text file that you can page through, this would give you a blank text file.

```
wput --help >wputhelp.txt
```

In this case you'd have to send stderr to the text file for page viewing.

```
wput --help 2>wputhelp.txt
```

You can also redirect the stderr on the fly to stdout to view the information in a pager (such as less).

```
wput --help 2>&1 | less
```

I find this invaluable for quite a few programs that output important information which are not necessarily error messages to stderr.

Finally another convenient option for this redirection is:

```
wput --help 2>error.txt > normal.txt
```

That will split the output into two files.  In this case your valuable information would be in the error.txt file and the normal.txt file would be blank.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by matt_symes on 2010-11-30
Hi

A nice summation apollothethird :)

Kind regards

---

