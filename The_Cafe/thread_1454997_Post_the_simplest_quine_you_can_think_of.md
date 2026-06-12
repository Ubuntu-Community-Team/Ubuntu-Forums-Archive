---
title: "Post the simplest quine you can think of"
date: 2010-04-15
forum: The Cafe
---

### Post by epicoder on 2010-04-15
Post the simplest quine you can think of in any language EXCEPT HQ9+.

A quine is a program that prints its own source code.

sh:
```
#This is a quine in sh.
cat $0
```

Yeah, yeah, I'm cheating. :roll:

And a simpler one: (also cheap)

```
#!/bin/cat
```

---

### Post by Sporkman on 2010-04-15
That's pretty hard.

---

### Post by Barrucadu on 2010-04-15
The null program. Ok, so it's cheating. Oh well :P

---

### Post by Bachstelze on 2010-04-15
> **sh228 said:**
> 
sh:
```
#This is a quine in sh.
cat $0
```

Only works if the script doesn't have spaces in its filename.

---

### Post by Simon17 on 2010-04-15
Here's one in C:

```


```

---

### Post by FuturePilot on 2010-04-15
> **Simon17 said:**
> Here's one in C:

```


```

Looks more like ninja.

---

### Post by Objekt on 2010-04-15
Programming hurts my head.

---

### Post by Random_Dude on 2010-04-15
> **Simon17 said:**
> Here's one in C:

```


```

Well, that's it. Somebody close the thread.:lolflag:

---

### Post by DoktorSeven on 2010-04-15
CBM BASIC:

```
10 LIST
```

(Edit: Apparently this board software doesn't like all caps posting, even when appropriate. :) )

---

### Post by Simian Man on 2010-04-15
> **Simon17 said:**
> Here's one in C:

```


```

```

[ian@sanpedro ~]$ cat temp.c 
[ian@sanpedro ~]$ gcc temp.c
/usr/lib/gcc/i686-redhat-linux/4.4.3/../../../crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status
[ian@sanpedro ~]$ 


```
Nope.  In  some languages yes, but not in C.

---

### Post by Simon17 on 2010-04-15
> **Simian Man said:**
> 
Nope.  In  some languages yes, but not in C.

There's a special compiler trick you need to get it to work, but I don't remember what it is right now.

---

### Post by Simian Man on 2010-04-15
> **Simon17 said:**
> There's a special compiler trick you need to get it to work, but I don't remember what it is right now.

There's no way to compile a program without a main function in standard C.  You might be able to compile it into an empty static library, but that doesn't count as a quine because it isn't a program.  It is a Python quine though, why not just call it that?

---

### Post by falconindy on 2010-04-15
```
$ touch quine.c
$ gcc -nostdlib quine.c -o quine
/usr/bin/ld: warning: cannot find entry symbol _start; defaulting to 0000000000400078
$ ./quine
zsh: segmentation fault:  ./quine
```
I suppose you'd have to declare that stdout contains the source for this to be valid....

---

### Post by MaxIBoy on 2010-04-15
> **sh228 said:**
> Post the simplest quine you can think of in any language EXCEPT HQ9+.

A quine is a program that prints its own source code.

sh:
```
#This is a quine in sh.
cat $0
```That doesn't count. 

Here's a real quine (not mine)
```
b=\' c=\\ a='echo b=$c$b c=$c$c a=$b$a$b; echo $a'[FONT=monospace]
[/FONT]echo b=$c$b c=$c$c a=$b$a$b; echo $a
```
Source:
[http://c2.com/cgi/wiki?QuineProgram](http://c2.com/cgi/wiki?QuineProgram)

You can easily enough modify this to add stuff which is actually useful.

---

### Post by Frak on 2010-04-15
> **Simon17 said:**
> Here's one in C:

```


```
Beat me to it.

---

