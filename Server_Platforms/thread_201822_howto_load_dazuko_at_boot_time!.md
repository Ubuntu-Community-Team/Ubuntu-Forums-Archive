---
title: "howto load dazuko at boot time?!"
date: 2006-06-22
forum: Server Platforms
---

### Post by tameritoke on 2006-06-22
Hi! 
I tried anbything but I don't find the sollution that the dazuko kernl module (which I compiled for my kernel) is being loaded at boot time. 

I know, that the dazuko module is dependent on 1 module cold "commoncap" and that the dazuko module itself can't be loaded if the capability module is being loaded. 

I thought the problem could be solved telling the ubuntu machine loading the modules in following order adding these 3 lines in the /etc/modules file: 

commoncap
dazuko
capability

what was simply wrong. Because if I run 

lsmod | less 

there is no dazuko module loaded. For any advise solving my problem, I would thank you very much. 

Please, don't tell me that I have to hack the initrd or the kernel itself, I don't believe this. I solved it once before on SuSE and on gentoo. I'm sure that case can be solved either on ubuntu. 


for any help, thank you 


Tamer:-k

---

### Post by MartinG on 2006-06-22
Adapting my solution in this thread:
[http://www.ubuntuforums.org/showthread.php?t=104507](http://www.ubuntuforums.org/showthread.php?t=104507)
Try the following:
Create a script called "dazuko" in /etc/init.rd, containing the following:

```
#! /bin/sh

rmmod capability && modprobe commoncap && modprobe dazuko && modprobe capability
```

 Then create a symlink to it in rc2.d, and rename it to S99dazuko.
 
 This will unload the capability module, load the commoncap and dazuko modules, and reload capability.

---

### Post by RavenOfOdin on 2006-06-24
Or you can just use your /etc/modules file and put "dazuko" and "commoncap" in there.

---

### Post by MartinG on 2006-06-25
[QUOTE=RavenOfOdin]Or you can just use your /etc/modules file and put "dazuko" and "commoncap" in there.[/QUOTE]But that doesn't work, because capability has already been loaded by the time /etc/modules is processed, and dazuko won't load if capability is already present.  See the original post.

---

### Post by RavenOfOdin on 2006-06-26
[QUOTE=MartinG]But that doesn't work, because capability has already been loaded by the time /etc/modules is processed, and dazuko won't load if capability is already present.  See the original post.[/QUOTE]

;) Works for me (tm) !

(tameritoke: If you haven't managed to get it installed yet, try the install instructions on the Dazuko webpage but after your "make" step do both "make install" and "make test", which will handle depmod and the associated work for you.)

---

### Post by silvagroup on 2006-07-01
RavenofOdin tried the install as per instructed and I get > insmod: error inserting 'dazuko.ko': -1 Unknown symbol in module.
I noticed there are several dazuko.ko files listed in the system. May I inquire is there a preferential one to use, may that be the problem haven't tried them all, kind of frustrated with this as it is, have spend half the day messing with this. Good thing it was a no work day.:-\"
So if there is no module inserted that would explain the problem Tameritoke is having, same one I am having.:-\"

---

### Post by harpomarx on 2006-09-03
Hello. I'm running dapper with amd64.xeon kernel, and I encountered the same problem.It seems that capability is loaded at boot time, and that dazuko is not "stackable" with capability when capability is loaded first. However, it works in the reverse order. I will try the script and keep you informed whether it works or not, but I believe the most effecient way of doing it should be to not loading capabilty at boot time, and sorry - as far as I unterstand it - this implies to modify the image ...:twisted: 
What I don't know is if capability is really compulsory at boot time, or if i t could be removed from the image with no damage at all.Futhermore, beeing a beginner with ubuntu (at not much more with linux) I experienced some difficulties to build a new initrd.
Maybe somebody can help ?

---

### Post by delphium on 2006-10-27
rmmod capability
modprobe dazuko
modprobe capability

Put these in /etc/rc.local, works fine on my laptop.

---

