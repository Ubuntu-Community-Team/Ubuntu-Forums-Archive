---
title: "URGENT - SECURITY - Linux Kernel 2.6 Local Root Exploit Advice"
date: 2008-02-10
forum: Security Discussions
---

### Post by thewump on 2008-02-10
Looking at this which I got from a link from a link from a link submitted to Digg.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/190587](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/190587)

The issue is over my head.. can someone post a dumbies guide to what this is, what it can do, and what the recommended steps are?

Thanks

---

### Post by faulkes on 2008-02-10
It's a locally compiled root exploit.

If someone has shell access to a linux machine of the appropriate kernel versions, they can compile the code, execute it and have root privileges.

The community is currently working on patching this issue, at the current time, there isn't much you can do (short of reverting to a non exploitable kernel).  This should only be a worry to people who allow people shell access to there server as it is not remotely exploitable.

Faulkes

---

### Post by Tyche on 2008-02-10
Thank you for the information.  The report I had read was sparce on details and confusing.

---

### Post by SpiderGorilla on 2008-02-10
Good, I didn't want to have to be the one to start this thread. The Slashdot article on this thoroughly confused me. Here's a few rookie questions I have:

A) How can I check if vmsplice is enabled on my system? There seemed to be some concern as to whether or not Ubuntu came with it enabled out of the box.

B) This is a local exploit, right? So the fact that I don't let anyone else touch my precious should mean that I don't have to worry. I mean, someone has to be at the box, not remotely browsing in (I don't have remote desktop enabled anyway), correct?

---

### Post by faulkes on 2008-02-10
The average user need not worry about this exploit as the average user does not typically allow other users into/onto there boxes with shell access (shell access being the key).

For people who run servers, especially those where there are many users or many potential avenues to gain remote access - either legitimately or not - say for instance a provider who gives customers shell access, then this is where the biggest threat exists as this is where it can be compiled/executed.

Faulkes

---

### Post by SpiderGorilla on 2008-02-10
Good enough. I don't let people near my box anyway. Thanks.

---

### Post by p_quarles on 2008-02-10
"Local" doesn't mean physical access. It means shell access. So, if you're running an ssh/telnet server that is not properly secured, this could be a problem for you.

---

### Post by bluewraith on 2008-02-10
As far as the "can it work on my pc?" question... thats as simple as getting the source code, compiling it, and running it. I'm running GG and tested the code out on my laptop. Lets just say that it.. uh... works. Kinda scary, but I'm also the only one who uses my laptop so I'm not too concerned. Keeping a binary of it on a pendrive though to show some friends this week though. :)
```

brandon@brandon-laptop:~$ gcc -o roottest roottest.c
brandon@brandon-laptop:~$ ./roottest
-----------------------------------
 Linux vmsplice Local Root Exploit
 By qaaz
-----------------------------------
[+] mmap: 0x0 .. 0x1000
[+] page: 0x0
[+] page: 0x20
[+] mmap: 0x4000 .. 0x5000
[+] page: 0x4000
[+] page: 0x4020
[+] mmap: 0x1000 .. 0x2000
[+] page: 0x1000
[+] mmap: 0xb7e56000 .. 0xb7e88000
[+] root
root@brandon-laptop:~# 

```
Pretty quick, too.

---

### Post by jordanmthomas on 2008-02-10
It works here too (at least until I update my kernel...it's already fixed in Arch.)
For you Ubuntu users who don't always have the latest kernel (though I'd imagine this one will be in the security updates very soon), there's a temporary fix that actually uses the exploit to run and disable it until the next reboot:
[http://www.ping.uio.no/~mortehu/disable-vmsplice-if-exploitable.c](http://www.ping.uio.no/~mortehu/disable-vmsplice-if-exploitable.c)
(source:  [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=464953#14](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=464953#14) )

> Keeping a binary of it on a pendrive though to show some friends this week though. 
I'm doing the same.  :lolflag:

---

### Post by SpiderGorilla on 2008-02-11
As far as I know, I don't run any sort of shell script to access my rig. I'm pretty certain that's something you have to set up on purpose.

---

### Post by jordanmthomas on 2008-02-11
> **SpiderGorilla said:**
> As far as I know, I don't run any sort of shell script to access my rig. I'm pretty certain that's something you have to set up on purpose.

Yes, by default only you can run things on your machine unless you install ssh or something similar.  However, all it takes is for someone to trick you into running some code to get root.  So basically, don't go running binaries that you're not 100% sure of the source of (this is never a good idea anyway).

---

### Post by xoai on 2008-02-11
Thanks god,I just upgraded to 2.6.25-rc1

---

### Post by dbeaart on 2008-02-11
> **xoai said:**
> Thanks god,I just upgraded to 2.6.25-rc1

How did you do that ? 
I don't see it in my upgrade list.
Do you have a special source for this, or did you home compile it ?

Tnx

---

### Post by dbeaart on 2008-02-11
Btw, I run a couple of servers, some with shell access....
I found out yesteray night about this exploit, via slashdot.

If you're in the same position as me, you might want to run the altered exploit, to disable the real exploit...
The slashdot page is [http://it.slashdot.org/article.pl?sid=08/02/10/2011257&from=rss](http://it.slashdot.org/article.pl?sid=08/02/10/2011257&from=rss)
The fix for the exploit is here : [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=464953#14](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=464953#14)
(as far as I know, when you reboot, you have to run the realtime patch again)

---

### Post by pedx1ng on 2008-02-11
Be careful, I read this link:

[DO NOT USE THE HOTFIX]("http://lists.debian.org/debian-kernel/2008/02/msg00387.html")

It says that it leads to kernel memory corruption which can lead to data loss.  I am not knowledgeable enough to know if this is true or not, but I am going to wait for an official fix for my Ubuntu and Debian boxes.

---

### Post by ubunyou on 2008-02-12
I confirmed the exploit on a Hardy Heron development kernel:
uname -a
>Linux kyle-ubuntu 2.6.24-5-generic #1 SMP Thu Jan 24 19:45:21 UTC 2008 i686 GNU/Linux

If you want to check if you are running ssh or other network services you could confirm all your ports are closed using:
>nmap -p 1-1024 localhost 

and look for the following line:
22/tcp  open   ssh     OpenSSH 3.9p1 (protocol 1.99)

generally if you are a home user and you haven't explicitly set and services up this command should return little to no results.

Alteranitely run:
>sudo ps -ef | grep sshd to see if the sshd daemon is running.

So question to security types out there then (prepare for runon sentence):
What prevents the sequence of commands that set the uid and gid on the kernel page to zero from being included as instruction code used in a buffer overflow against a process with normal user privileges that doesn't necessarily grant 'shell access'. (i.e., internet browser X, say firefox for examples sake).

---

### Post by PetePete on 2008-02-12
i use ubuntu gutsy server, just ran apt-get update and apt-get upgrade
updated new kernel

but the exploit still works ?!!

pete@server:~$ uname -a
Linux server 2.6.22-14-server #1 SMP Fri Feb 1 05:28:54 UTC 2008 i686 GNU/Linux

---

### Post by dbeaart on 2008-02-12
> **PetePete said:**
> i use ubuntu gutsy server, just ran apt-get update and apt-get upgrade
updated new kernel

but the exploit still works ?!!

pete@server:~$ uname -a
Linux server 2.6.22-14-server #1 SMP Fri Feb 1 05:28:54 UTC 2008 i686 GNU/Linux

Yes, for some reason, the security update STILL isn't released!!
So every ubuntu box on the planet is vulnerable to local root exploits.
This is crazy!

---

### Post by jordanmthomas on 2008-02-12
> **dbeaart said:**
> Yes, for some reason, the security update STILL isn't released!!
So every ubuntu box on the planet is vulnerable to local root exploits.
This is crazy!

[http://ubuntuforums.org/showpost.php?p=4312743&postcount=15](http://ubuntuforums.org/showpost.php?p=4312743&postcount=15)
Until the patch is pushed into the update system for Ubuntu users, you can use this kernel module that will cause the exploit to segfault.

---

### Post by yaztromo on 2008-02-12
Found my server was borked this morning following playing with the exploit last night. Had to run fsck several times to clear up all the mess, and there's now a fair amount of stuff in lost+found, hope it's not important.

This was all on a Fiesty box where the exploit seg faults. It seems the exploit can still wreck your system through memory corruption over time even if it is immune to root elevation. Makes me wonder if future patched systems will be vulnerable to this memory corruption too?

Please reboot if you play with this thing, it really does screw up your system.

---

### Post by dbeaart on 2008-02-12
> **yaztromo said:**
> Found my server was borked this morning following playing with the exploit last night. Had to run fsck several times to clear up all the mess, and there's now a fair amount of stuff in lost+found, hope it's not important.

Please reboot if you play with this thing, it really does screw up your system.

I have the patch running on 6 servers. I really like to reboot, but I need to have a secure system. I rather have a crash now, than a hacked server tomorrow. I know it is really sucky, so I am still praying for the kernel update...

(If there was a smiley with a guy pulling out all his hair, I would put it here...)

---

### Post by evilghost on 2008-02-12
Note, I am now using this module until kernel packages have been released. Testing with the 5092 and 5093 exploit does not show exploitation and /var/log/messages reports the attempted exploit.  The kernel module does not produce the same mmap corruption as seen by the 'RET' live-patch derived from the exploit itself.

[http://home.powertech.no/oystein/ptpatch2008/ptpatch2008.c](http://home.powertech.no/oystein/ptpatch2008/ptpatch2008.c)

To compile be sure you get the Makefile and the .c file.

After the module is built simply "insmod ./ptpatch2008.ko"

```

   1. sudo su  
   2. apt-get install build-essential linux-headers-2.6-686 (adjust arch as needed).  
   3. cd ~  
   4. mkdir ptpatch2008 && cd ptpatch2008  
   5. wget http://home.powertech.no/oystein/ptpatch2008/ptpatch2008.c  
   6. wget http://home.powertech.no/oystein/ptpatch2008/Makefile  
   7. make  
   8. insmod ./ptpatch2008.ko  
   9. echo "#vmsplice mitigation module" >> /etc/rc.local  
  10. echo "/bin/insmod `pwd`/ptpatch2008.ko" >> /etc/rc.local  

```

---

### Post by galeron on 2008-02-12
Out of curiousity, how does this thing actually work? I've looked at the source code and can't make head or tail of it.

---

### Post by Whiffle on 2008-02-12
> **galeron said:**
> Out of curiousity, how does this thing actually work? I've looked at the source code and can't make head or tail of it.

Kinda makes ya wonder how they figured it out, doesn't it? :D  I can't figure it out either.

I manually updated to 2.6.24.2, its fixed.  I suspect ubuntu should have a new package out soon...

---

### Post by evilghost on 2008-02-12
It hooks the sys_vmsplice syscall, replacing it.

---

### Post by tubezninja on 2008-02-12
It appears a fix is out:

[http://www.ubuntu.com/usn/usn-577-1](http://www.ubuntu.com/usn/usn-577-1)

Anyone try it yet?

---

### Post by ssam on 2008-02-13
> **galeron said:**
> Out of curiousity, how does this thing actually work? I've looked at the source code and can't make head or tail of it.

LWN has a very detailed article [http://lwn.net/Articles/268783/](http://lwn.net/Articles/268783/)

(if you are not a subscriber you'll need to wait another few days for it to be publicly readable)

---

### Post by freakymousemats on 2008-02-14
I'm running a 7.04 Server with Xen, and these kernel hasn't been updated along with the rest as part of the security update (USN-577-1), is there a fix coming for this?

---

### Post by honeydew on 2008-02-15
hrmm anyone try the fix? this guy affects a handful of machines on our network, and I would say that there is some level of distrust of the users.    It only affects 4 of our machines I am wondering if I should go through the trouble of compiling a new kernel or wait it out for a fix.

---

### Post by dbeaart on 2008-02-15
> **honeydew said:**
> hrmm anyone try the fix? this guy affects a handful of machines on our network, and I would say that there is some level of distrust of the users.    It only affects 4 of our machines I am wondering if I should go through the trouble of compiling a new kernel or wait it out for a fix.

I have the hotfix now running on 6 Ubuntu servers (6.04 & 7.04). One of them crashed after a couple of hours, I rebooted it, runned the fix again.
Since then I've had no problems with any of the machines.

Still, I am dying for a kernel update from ubuntu. I really can't understand why there isn't a solution...


Edit:
Last updates fixed it for me...

---

### Post by ubunyou on 2008-02-16
Hardy has a patch out too - yay hardy.

kyle@kyle-ubuntu:~$ cat /etc/apt/sources.list.d/hardy.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

kyle@kyle-ubuntu:~$ uname -a
Linux kyle-ubuntu 2.6.24-8-generic #1 SMP Thu Feb 14 20:40:45 UTC 2008 i686 GNU/Linux

kyle@kyle-ubuntu:~$ ./a.out
-----------------------------------
 Linux vmsplice Local Root Exploit
 By qaaz
-----------------------------------
[+] mmap: 0x0 .. 0x1000
[+] page: 0x0
[+] page: 0x20
[+] mmap: 0x4000 .. 0x5000
[+] page: 0x4000
[+] page: 0x4020
[+] mmap: 0x1000 .. 0x2000
[+] page: 0x1000
[+] mmap: 0xb7da1000 .. 0xb7dd3000
[-] vmsplice: Bad address

---

