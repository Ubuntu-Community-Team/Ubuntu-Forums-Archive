---
title: "shell utilities in Linux"
date: 2012-06-22
forum: Server Platforms
---

### Post by MakOwner on 2012-06-22
I learned shell scripting on AIX.  
Is it just me, (maybe I have exceptionally bad memory) or are the utilities like head, tail, grep, etc in the linux environment ... lacking?

I could use 'cat file.name | tail +3` and the contents of a file starting from the third line in AIX.

Head worked the same way, you could get the top of the bottom lines of a file using + or - ...

If you use 'cat file.name | tal +3` in linux tail looks for a file named "+3".

And grep.  don't get me started there.  the most useful feature "-p" doesn't exist, near as I can tell.

Is there some way to at least make head and tail work? Am I accustomed some assumed default in AIX that's I'm missing in Linux?

---

### Post by AnotherMuggle on 2012-06-22
> **MakOwner said:**
> I learned shell scripting on AIX.  
Is it just me, (maybe I have exceptionally bad memory) or are the utilities like head, tail, grep, etc in the linux environment ... lacking?

I could use 'cat file.name | tail +3` and the contents of a file starting from the third line in AIX.

Head worked the same way, you could get the top of the bottom lines of a file using + or - ...

If you use 'cat file.name | tal +3` in linux tail looks for a file named "+3".

And grep.  don't get me started there.  the most useful feature "-p" doesn't exist, near as I can tell.

Is there some way to at least make head and tail work? Am I accustomed some assumed default in AIX that's I'm missing in Linux?

To see the last 3 lines of a file:
```
tail -n 3 /path/to/file
```

What are you expecting out of grep -p?

---

### Post by kennethconn on 2012-06-22
> **AnotherMuggle said:**
> To see the last 3 lines of a file:
 
That was not what the OP was asking.
 
**@**MakOwner - did you look at the man pages for the tail command for any reference to the discrepancy you are experiencing? There could be something relevant there, perhaps you checked it already.

---

### Post by MakOwner on 2012-06-22
> **AnotherMuggle said:**
> To see the last 3 lines of a file:
```
tail -n 3 /path/to/file
```

What are you expecting out of grep -p?

Thank goodness - it is just me not knowing what I'm doing.
Still damned annoying ot have to change that on every occurrence :/

Anyway, "grep -p" is essentially paragraph function - by default it outputs all the text between two blank lines.

For example:
tapeutil -f /dev/smc0 gives you a nice pretty billboard of human readable text.  "grep -p Slot" will give you all the lines between the spaces in the Slots section of the billboard.

tapeutil -f /dev/smc0 inv | grep -p Slot | grep "Robot Access Allowed" | wc -l


I understand there is a "paragrep" utility out there - the current iteration of it is a python script or whatever.  After installing python, the python installer too, then installing the other install utility that install paragrep, it fails to install.  The installer and/or the repository for python is looking for version 3.1.0 that doesn't exist  at the URL where it's trying to obtain it.

Some googling hasn't gotten a me copy of 3.1.0 and I can't the install to install/compile or whatever it does an older version that IS available.

Not that I'm confident I could figure it out if I could get it installed at this point.

---

### Post by MakOwner on 2012-06-22
> **kennethconn said:**
> That was not what the OP was asking.
 
**@**MakOwner - did you look at the man pages for the tail command for any reference to the discrepancy you are experiencing? There could be something relevant there, perhaps you checked it already.

cat file.txt | tail -n +3 

will do the equivalent of 

cat file.txt | tail +3 

in AIX.

Edit:
In my script I could check the OS and alias 'tail' with 'tail -n' so that I can keep it portable.

---

### Post by AnotherMuggle on 2012-06-22
> **kennethconn said:**
> That was not what the OP was asking.

Wasn't it?  It looks to me like I understood correctly.  The output of both commands will be the same.

```
tail -n 3 /var/log/syslog
```

```
cat /var/log/syslog | tail -n 3

```

As for the grep question, I'm afraid I can't help on that one. It's not something I've ever had a requirement for, sorry.

---

### Post by kennethconn on 2012-06-23
The OP wanted to see the output of the file starting from line 3 of the file, not the last 3 lines of the file.
 
They have it working now, so all good.

---

### Post by sisco311 on 2012-06-23
[http://www.gnu.org/software/coreutils/manual/html_node/Standards-conformance.html](http://www.gnu.org/software/coreutils/manual/html_node/Standards-conformance.html)

```
_POSIX2_VERSION=199209 tail +3 filename
```

Oh, and also please check out [http://partmaps.org/era/unix/award.html](http://partmaps.org/era/unix/award.html) :evil:

---

### Post by jmate24 on 2012-06-23
> **MakOwner said:**
> Thank goodness - it is just me not knowing what I'm doing.
Still damned annoying ot have to change that on every occurrence :/

Anyway, "grep -p" is essentially paragraph function - by default it outputs all the text between two blank lines.

For example:
tapeutil -f /dev/smc0 gives you a nice pretty billboard of human readable text.  "grep -p Slot" will give you all the lines between the spaces in the Slots section of the billboard.

tapeutil -f /dev/smc0 inv | grep -p Slot | grep "Robot Access Allowed" | wc -l


I understand there is a "paragrep" utility out there - the current iteration of it is a python script or whatever.  After installing python, the python installer too, then installing the other install utility that install paragrep, it fails to install.  The installer and/or the repository for python is looking for version 3.1.0 that doesn't exist  at the URL where it's trying to obtain it.

Some googling hasn't gotten a me copy of 3.1.0 and I can't the install to install/compile or whatever it does an older version that IS available.

Not that I'm confident I could figure it out if I could get it installed at this point.

they skiped python 3.1.0 in favor of python 3.2.

---

### Post by codemaniac on 2012-06-23
> **MakOwner said:**
> cat file.txt | tail -n +3 

cat file.txt | tail +3 


You have just won a Useless Use of Cat Award. ;)

[http://partmaps.org/era/unix/award.html](http://partmaps.org/era/unix/award.html)

---

### Post by AnotherMuggle on 2012-06-23
> **kennethconn said:**
> The OP wanted to see the output of the file starting from line 3 of the file, not the last 3 lines of the file.
 
They have it working now, so all good.

Right you are, DOH!

> **codemaniac said:**
> You have just won a Useless Use of Cat Award. ;)

[http://partmaps.org/era/unix/award.html](http://partmaps.org/era/unix/award.html)

lol, love it.

---

