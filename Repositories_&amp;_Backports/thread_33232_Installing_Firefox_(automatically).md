---
title: "Installing Firefox (automatically)"
date: 2005-05-10
forum: Repositories &amp; Backports
---

### Post by walter.serner on 2005-05-10
I downloaded the file "firefox-1.0.3.installer.tar" and tried to install it on my Kubuntu machine.


Same for the auto-install version of Acrobat Reader.

None of them installs itself. What do I have to consider?

Thanks,
Walter

---

### Post by defkewl on 2005-05-10
why don't you use: 
$ apt-get install mozilla-firefox 
instead?

---

### Post by walter.serner on 2005-05-10
I can´t connect this machine to the internet and therefore have to depend on 
CDs.

Walter

---

### Post by nemin on 2005-05-10
[QUOTE=walter.serner]I can´t connect this machine to the internet and therefore have to depend on 
CDs.[/QUOTE]
Then you should better use *.deb file than *.tar, and install them with ```
sudo dpkg -i *.deb
```

---

### Post by walter.serner on 2005-05-10
Thanks, but didn't work.

I put the file xmms_1.2.7-1_i386.deb in the folder home/walter/test, changed into
this directory and ran the command. Only got an error message.

What have I done wrong?

Walter

---

### Post by nemin on 2005-05-10
[QUOTE=walter.serner]
I put the file xmms_1.2.7-1_i386.deb in the folder home/walter/test, changed into
this directory and ran the command. Only got an error message.
[/QUOTE]
Post the message here please.

---

### Post by walter.serner on 2005-05-10
dpkg: error processing xmms_1.2.7_i386.de (- - install):
cannot access archive: No such file or directory
Errors were returned while processing:
xmms_1.2.7_i386.de

Thanks,
Walter

---

### Post by hashimoto on 2005-05-10
Looks like you miss the letter "b" at the end of the file name. It should end with ".deb"

But I may be wrong

---

### Post by nemin on 2005-05-10
[QUOTE=walter.serner]dpkg: error processing xmms_1.2.7_i386.de (- - install):
cannot access archive: No such file or directory
Errors were returned while processing:
xmms_1.2.7_i386.de
[/QUOTE]Looks like you forgot the "b". Typ ```
ls
``` to see the exact filename.

---

### Post by walter.serner on 2005-05-10
The missing "b" is only a typo here in my posting. It had been included In the original 
command.

Thanks,
Walter

---

### Post by nemin on 2005-05-10
[QUOTE=walter.serner]The missing "b" is only a typo here in my posting. It had been included In the original 
command.[/QUOTE]Then you must have made a typo somewhere else in the command. Really, you can only get this error when the filename you enter doesn't exists in the directory. As I said, with `ls` you can see the directory content...

---

### Post by walter.serner on 2005-05-10
Thanks nemin,

you are right must have been a typo somewhere. Now I am facing a depency
problem which I will try to tackle tomorrow.

W.

---

### Post by nemin on 2005-05-10
[QUOTE=walter.serner]
you are right must have been a typo somewhere. Now I am facing a depency
problem which I will try to tackle tomorrow.[/QUOTE]Good luck with it, mixing packages from repositories and downloaded stuff won't give you the most easy-to-fix problems;)

---

### Post by walter.serner on 2005-05-11
That's a bit disappointing as I hoped for Linux/Ubuntu giving me more choices than
Windows. I am running Win98 SE on my laptop and can download, install heaps
of programs, test them and still my system is very reliable. 

It would be highly appreciated if anyone can suggest how to comfortably install
programs from a cd without the hassle of check all the dependencies of packages
manually.

---

### Post by fishfork on 2005-05-12
[QUOTE=][/QUOTE]
 Perhaps you could download the packages from the ftp server, and then make your own package CD using the instructions [here](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions) (look for "How to make your own package CD for offline use" near the end).

---

