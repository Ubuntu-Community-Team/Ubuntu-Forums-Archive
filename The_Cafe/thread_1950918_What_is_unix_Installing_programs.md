---
title: "What is unix? Installing programs?"
date: 2012-04-01
forum: The Cafe
---

### Post by seal308 on 2012-04-01
Hello i'm new to ubuntu.
I was looking at the learning resources and i saw a book entitled "learn unix in 24 hours"
my question is what is unix?
is it the command line?
Are there any differences between the terminal in linux vs the terminal in mac (i just switched from mac)

Also i'm trying to install software. But i'm having a tough time doing so without the software centre.
I'm trying to install a java IDE called Dr Java. 
I have a dr java.jar file in the download folder but i don't get how to install it.

Any help would be much appreciated. Thanks!

---

### Post by CharlesA on 2012-04-01
Linux is based off UNIX but it is not the same.

The terminal is similar to that on OSX, but it is still not the same.

As for Dr. Java, see here: [http://ubuntuforums.org/showthread.php?t=1256676](http://ubuntuforums.org/showthread.php?t=1256676)

---

### Post by seal308 on 2012-04-01
so i'm still not getting it upon looking at that thread.
apparently this is the code the person used:
java -jar drjava-stable-20040326.jarhowever
my file is a drjava beta 
name of the file is: drjava-beta-20110822-r5448.jar
this is where it's located: '/home/user/Downloads/drjava-beta-20110822-r5448.jar'
so i tried
java -jar drjava-beta-20110822-r5448.jar
but i got :
Unable to access jarfile drjava-beta-20110822-r5448.jar
can ideas?

---

### Post by terrykiwi83 on 2012-04-01
how about trying

```

sudo java -jar drjava-beta-20110822-r5448.jar

```

---

### Post by KiwiNZ on 2012-04-01
Unix is a one wheeled exercycle

---

### Post by alexfish on 2012-04-01
> **KiwiNZ said:**
> Unix is a one wheeled exercycle
Get the updated Kernel

Unix E Ergometer Cross Trainer

---

### Post by seal308 on 2012-04-01
sudo java -jar drjava-beta-20110822-r5448.jar

didn't work
this is what i got:
Unable to access jarfile drjava-beta-20110822-r5448.jar

any more ideas?

---

### Post by CharlesA on 2012-04-01
Try using the full path to drjava-beta-20110822-r5448.jar

---

### Post by Mait on 2012-04-01
> **seal308 said:**
> so i'm still not getting it upon looking at that thread.
apparently this is the code the person used:
java -jar drjava-stable-20040326.jarhowever
my file is a drjava beta 
name of the file is: drjava-beta-20110822-r5448.jar
this is where it's located: '/home/user/Downloads/drjava-beta-20110822-r5448.jar'
so i tried
java -jar drjava-beta-20110822-r5448.jar
but i got :
Unable to access jarfile drjava-beta-20110822-r5448.jar
can ideas?

Looks like you entered wrong file path. Try this one.
```
java -jar ~/Downloads/drjava-beta-20110822-r5448.jar
```

'~' means your home directory.

---

### Post by Jerry N on 2012-04-01
For help with your question "What is UNIX", check the following link.  [http://en.wikipedia.org/wiki/Unix]("http://en.wikipedia.org/wiki/Unix")


Jerry

---

### Post by idoitprone on 2012-04-01
well to make things more confusing, regardless of 30 years of operating system research. all we get is unix again.

To add some extra confusion, Window NT kernel is a base off unix

So basically linux, mac, windows have characteristic of unix

[http://herpolhode.com/rob/utah2000.pdf](http://herpolhode.com/rob/utah2000.pdf)

yeah the mind blowing window unix thing

i wish that was a april fools joke

---

