---
title: "Running xv6 (unix) on qemu emulator"
date: 2013-03-21
forum: Virtualisation
---

### Post by skgskg on 2013-03-21
Hello,
I'm new here, but not on linux :P
I'm trying to run and load xv6 img that I'm working on to qemu on kubuntu (64bit updated).
I downloaded the source compiled it, and tried to run it, but it seems that I'm having a problem since qemu runs in a new "shell" windows, but it is stuck on screen saying SeaBIOS something something, and strangely it seem that the screen flickers, so I tried to screenshot this flickery thing, and seem to be another screen which written on it VGA stuff (detecting VGA etc..) 
[IMG]http://dl.dropbox.com/u/30037921/stam1.png[/IMG]
[IMG]http://dl.dropbox.com/u/30037921/stam.png[/IMG]

I run the emulator like this:
qemu-system-i386 -serial mon:stdio -hdb fs.img xv6.img -smp 1 -m 512 

the compilation seem to end just fine with no errors or warnings
tried reinstalling stuff, and tried x86_64 emulator nothing works, tried the same source code on other kubutnus and ubuntus (32/64bit) they worked like a charm.

also I tried to to configure the iPXE thing to boot or load the img, but I couldn't make it work, and it seems that there is no img loaded.
Btw: tried running it with -nographics it runs the emulator on the terminal, and stucks (can't write anything or do except emulator control stuff)

Any idea guys?? 
Thanx for your time I really appreciate it :).

---

### Post by sanderj on 2013-03-24
It works for me.

```
git clone git://pdos.csail.mit.edu/xv6/xv6.git
cd xv6/
make
qemu-system-i386 -serial mon:stdio -hdb fs.img xv6.img -smp 1 -m 512 
```

this one works too:

```
qemu -parallel mon:stdio -smp 1 -m 512 -hdb fs.img xv6.img
```

What is your output of:

```
sander@appelboor:~/temp/xv6$ ll *img
-rw-rw-r-- 1 sander sander  524288 mrt 24 10:15 fs.img
-rw-rw-r-- 1 sander sander 5120000 mrt 24 10:09 xv6.img
sander@appelboor:~/temp/xv6$
```

---

### Post by skgskg on 2013-03-25
> **sanderj said:**
> It works for me.

```
git clone git://pdos.csail.mit.edu/xv6/xv6.git
cd xv6/
make
qemu-system-i386 -serial mon:stdio -hdb fs.img xv6.img -smp 1 -m 512 
```

this one works too:

```
qemu -parallel mon:stdio -smp 1 -m 512 -hdb fs.img xv6.img
```

What is your output of:

```
sander@appelboor:~/temp/xv6$ ll *img
-rw-rw-r-- 1 sander sander  524288 mrt 24 10:15 fs.img
-rw-rw-r-- 1 sander sander 5120000 mrt 24 10:09 xv6.img
sander@appelboor:~/temp/xv6$
```

Thank mate for your reply, thought no one is gonna reply!

I know it is suppose to work, it work on lots of computers, I thought I'd give it a try with what you exactly did.
when runnging with :
```
 qemu-system-i386 -serial mon:stdio -hdb fs.img xv6.img -smp 1 -m 512 
```
got the same result of flickering BIOS screen.
when trying :
```
qemu -parallel mon:stdio -smp 1 -m 512 -hdb fs.img xv6.img
```
qemu was not recognized (only qemu-system-i386 or qemu-system-x86_64 wroks)
I ran :
```
 ll *img 
```
got the same result :
```
 picasso@picasso-ThinkPad-T400:~/Workspace/OS/xv6$ ll *img-rw-rw-r-- 1 picasso picasso  524288 Mar 25 16:46 fs.img
-rw-rw-r-- 1 picasso picasso 5120000 Mar 25 16:46 xv6.img
 
```

Don't know why it doesn't work :( but this really sucks!
HELP!

---

### Post by sanderj on 2013-03-25
DId you install qemu? If so: via the regular repository?

---

### Post by skgskg on 2013-03-25
> **sanderj said:**
> DId you install qemu? If so: via the regular repository?

yes I did using the command:
```
 apt-get install qemu 
```
But not sure it is from the regular repository (because I added a lot...)
How to check?

those were installed:
```
 qemu-ga             qemu-ifdown         qemu-img            qemu-nbd            qemu-system-x86_64  
qemu-i386           qemu-ifup           qemu-io             qemu-system-i386    qemu-x86_64 
```
but there is no qemu command

Thank you very much for your help!

---

### Post by skgskg on 2013-04-15
OK, after tons of searching, I found that you MUST NOT run qemu with sudo!!!! and thats what I did the first time so I got my system (only qemu was affected though) reinstalled and it now works like a charm :D

---

