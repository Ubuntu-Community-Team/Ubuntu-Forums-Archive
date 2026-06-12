---
title: "xenial: Watch out for boot failures due to /etc/mtab file"
date: 2015-10-29
forum: Ubuntu Development Version
---

### Post by flocculant on 2015-10-29
Just did an install from iso to hardware.

Got 

> /etc/mtab is not a symlink or not pointing to /proc/self/mounts


Chatted to Martin Pitt on irc, if you see this please Me Too [lpbug]1511376[/lpbug]
> 
Hello all,

/etc/mtab is supposed to be a symlink to /proc/self/mounts (or
/proc/mounts) for stuff to work. We've also shipped
"debian-fixup.service" since vivid to turn a file into a symlink on
boot.

However, if you have /etc/mtab as a file (e. g. right after
installation), current xenial's systemd will fail hard to boot with
something like


| systemd [1]: /etc/mtab is not a symlink or not pointing to /proc/self/mounts. This is not supported anymore. Please replace /etc/mtab with a symlink to /proc/self/mounts.
| systemd [1]: Freezing execution.

Detail on the why can be found at [https://lists.ubuntu.com/archives/ubuntu-devel/2015-October/038961.html](https://lists.ubuntu.com/archives/ubuntu-devel/2015-October/038961.html)

---

### Post by ronacc on 2015-10-29
I had done a fresh install of wiley and then changes my sources.list and updated to get here and my /etc/mtab IS a symlink  . I however have the opposite problem my box won't shut down from xenial , atleast not from the button , x stops but the system does not power off . it will shutdown if I do so from a terminal ( sudo shutdown -P ) and it will reboot normally from the button ?

---

### Post by flocculant on 2015-10-29
> I had done a fresh install of wiley and then changes my sources.list and updated to get here and my /etc/mtab IS a symlink .

because

> if you have /etc/mtab as a file (e. g. right after installation), current xenial's systemd will fail hard to boot

> We've also shipped "debian-fixup.service" since vivid to turn a file into a symlink on boot.

I expect.

Anything else you're seeing needs to be a thread/bug of it's own.

---

### Post by sudodus on 2015-10-29
Hi flocculant,

Installed Lubuntu i386 gets stuck at grub rescue. I created a bug report for it, #1511528.

Please help me find out if I'm affected by 'your mtab bug' or something else :-)

---

### Post by ronacc on 2015-10-29
do you have another install on the same box that will boot ?

---

### Post by sudodus on 2015-10-29
Not on the same drive, because I installed to the whole drive.

I'm testing now with 'Something else' to install into a system with two working systems (but not Xenial). That installation finished, and I'm testing if it works now: This one boots into rescue mode, but gets stuck after printing

3.815828 clocksource: Switched to clocksource tsc

and above that I can see a complaint about mtab :-)

/etc/mtab is not a symlink or not pointing ...,

so I am affected by the mtab bug, and I'll mark affects me too.

I don't know yet if the grub rescue problem is caused by the same or another bug.

---

### Post by ronacc on 2015-10-29
it wouldn't have to be on the same drive just the same computer . you can use the working install to examine the failed install to try to get a clue .

---

### Post by sudodus on 2015-10-29
Well, I have found the mtab bug, so I can wait for its bugfix. If 'my grub rescue bug' is squashed it was another manifestation of the same bug, otherwise we need to search for its cause.

I guess it should be possible to search while booted from the Lubuntu live system too.

---

### Post by flocculant on 2015-10-29
> **sudodus said:**
> Well, I have found the mtab bug, so I can wait for its bugfix. If 'my grub rescue bug' is squashed it was another manifestation of the same bug, otherwise we need to search for its cause.

I guess it should be possible to search while booted from the Lubuntu live system too.

Just so you know - I *didn't* get any grub problems today when I did this install. I did see your one pop up on the tracker though. 

I did get the installer hang on partitioning - [s]then couldn't find the bug which was reported recentlyish.[/s]

---

### Post by sgage on 2015-11-01
I tried a freshly downloaded daily this morning, and ran into the mtab bug. Easy enough to work around. The bug report indicates that it is fixed, so we should see daily iso's that work properly soon...

---

### Post by ventrical on 2015-11-01
Yep .. just got it here on gnome-desktop. What a bummer because the live session worked so well..

Systemd [1] Freezing Execution

---

### Post by sgage on 2015-11-01
> **ventrical said:**
> Yep .. just got it here on gnome-desktop. What a bummer because the live session worked so well..

Systemd [1] Freezing Execution

It's real easy to fix:

Boot your live session, mount your installation, cd to the root of the installation filesystem. Then sudo ln -fs /proc/mounts etc/mtab. Then reboot, and you should be fine. Note, NO / in front of etc...

---

### Post by ventrical on 2015-11-01
> **sgage said:**
> It's real easy to fix:

Boot your live session, mount your installation, cd to the root of the installation filesystem. Then sudo ln -fs /proc/mounts etc/mtab. Then reboot, and you should be fine. Note, NO / in front of etc...

```

ubuntu-gnome@ubuntu-gnome:/media/ubuntu-gnome$ dir
51657144-e57d-44d2-aa4a-554119390992
ubuntu-gnome@ubuntu-gnome:/media/ubuntu-gnome$ 51657144-e57d-44d2-aa4a-554119390992
51657144-e57d-44d2-aa4a-554119390992: command not found
ubuntu-gnome@ubuntu-gnome:/media/ubuntu-gnome$ cd 51657144-e57d-44d2-aa4a-554119390992
ubuntu-gnome@ubuntu-gnome:/media/ubuntu-gnome/51657144-e57d-44d2-aa4a-554119390992$ cd root
bash: cd: root: Permission denied
ubuntu-gnome@ubuntu-gnome:/media/ubuntu-gnome/51657144-e57d-44d2-aa4a-554119390992$ sudo -i
root@ubuntu-gnome:~# cd root
-bash: cd: root: No such file or directory
root@ubuntu-gnome:~# sudo ln -fs /proc/mounts etc/mtab
ln: failed to create symbolic link ‘etc/mtab’: No such file or directory
root@ubuntu-gnome:~# 


```

?
How do I cd to the installation?

---

### Post by grahammechanical on 2015-11-01
I have never tried it from a live session but from an installed session. 
> 
graham@sdb7-Dev:~$ cd ..
graham@sdb7-Dev:/home$ cd ..
graham@sdb7-Dev:/$ 

I have tried it not from a live session but from an installed session on a second hard drive where I have used the file manager to mount the system-a and the system-b partitions

> graham@sdb7-Dev:~$ cd /media
graham@sdb7-Dev:/media$ ls
graham
graham@sdb7-Dev:/media$ cd graham
graham@sdb7-Dev:/media/graham$ ls
Data  system-a  system-b
graham@sdb7-Dev:/media/graham$ cd system-a
graham@sdb7-Dev:/media/graham/system-a$ ls
apps  dev   kernel  lost+found  oem  proc  sbin  tmp       var
bin   etc   lib     media       opt  root  srv   userdata  writable
boot  home  lib64   mnt         os   run   sys   usr
graham@sdb7-Dev:/media/graham/system-a$ 



I am now in the root of system-a of a Ubuntu personal installation. the command

```
cd ..
```

= move back a directory. Something I learned from my Msdos days.

Regards.

---

### Post by sudodus on 2015-11-02
> **ventrical said:**
> ```

ubuntu-gnome@ubuntu-gnome:/media/ubuntu-gnome$ dir
51657144-e57d-44d2-aa4a-554119390992
ubuntu-gnome@ubuntu-gnome:/media/ubuntu-gnome$ 51657144-e57d-44d2-aa4a-554119390992
51657144-e57d-44d2-aa4a-554119390992: command not found
ubuntu-gnome@ubuntu-gnome:/media/ubuntu-gnome$ cd 51657144-e57d-44d2-aa4a-554119390992
ubuntu-gnome@ubuntu-gnome:/media/ubuntu-gnome/51657144-e57d-44d2-aa4a-554119390992$ cd root
bash: cd: root: Permission denied
ubuntu-gnome@ubuntu-gnome:/media/ubuntu-gnome/51657144-e57d-44d2-aa4a-554119390992$ sudo -i
root@ubuntu-gnome:~# cd root
-bash: cd: root: No such file or directory
root@ubuntu-gnome:~# sudo ln -fs /proc/mounts etc/mtab
ln: failed to create symbolic link ‘etc/mtab’: No such file or directory
root@ubuntu-gnome:~# 


```

?
How do I cd to the installation?

See the [bug report](https://bugs.launchpad.net/bugs/1511376), comment #9

Mount if not mounted ...

-o-

But it seems the bug-fix will arrive very soon :-)

---

### Post by sgage on 2015-11-02
Make sure your install filesystem is mounted (you can just click on it in Files). Once you're at /media/ubuntu-gnome, just cd to it. 'Dir' should show you the whole filesystem. (By 'root of the filesystem', I meant the base of the filesystem, not the root's directory (/root). Then ln -fs /proc/mounts etc/mtab. Note  - no / in front of etc, yes / in front of proc.



> **ventrical said:**
> ```

ubuntu-gnome@ubuntu-gnome:/media/ubuntu-gnome$ dir
51657144-e57d-44d2-aa4a-554119390992
ubuntu-gnome@ubuntu-gnome:/media/ubuntu-gnome$ 51657144-e57d-44d2-aa4a-554119390992
51657144-e57d-44d2-aa4a-554119390992: command not found
ubuntu-gnome@ubuntu-gnome:/media/ubuntu-gnome$ cd 51657144-e57d-44d2-aa4a-554119390992
ubuntu-gnome@ubuntu-gnome:/media/ubuntu-gnome/51657144-e57d-44d2-aa4a-554119390992$ cd root
bash: cd: root: Permission denied
ubuntu-gnome@ubuntu-gnome:/media/ubuntu-gnome/51657144-e57d-44d2-aa4a-554119390992$ sudo -i
root@ubuntu-gnome:~# cd root
-bash: cd: root: No such file or directory
root@ubuntu-gnome:~# sudo ln -fs /proc/mounts etc/mtab
ln: failed to create symbolic link ‘etc/mtab’: No such file or directory
root@ubuntu-gnome:~# 


```

?
How do I cd to the installation?

---

### Post by flocculant on 2015-11-02
should be fixed in latest builds

---

### Post by VMC on 2015-11-02
Its fixed for me as of todays ISO.
Edit:  Xubuntu

---

### Post by ventrical on 2015-11-02
> **sgage said:**
> Make sure your install filesystem is mounted (you can just click on it in Files). Once you're at /media/ubuntu-gnome, just cd to it. 'Dir' should show you the whole filesystem. (By 'root of the filesystem', I meant the base of the filesystem, not the root's directory (/root). Then ln -fs /proc/mounts etc/mtab. Note  - no / in front of etc, yes / in front of proc.

Ahhhh :)

---

### Post by ventrical on 2015-11-02
> **VMC said:**
> Its fixed for me as of todays ISO.

Ohhhhhh  :)

---

### Post by ventrical on 2015-11-02
> **sudodus said:**
> See the [bug report]("https://bugs.launchpad.net/bugs/1511376"), comment #9

Mount if not mounted ...

-o-

But it seems the bug-fix will arrive very soon :-)

Eeeeeeeee! :)

Ok .. I will zsync ..

Thanks everybody! :)

---

### Post by sgage on 2015-11-02
> **ventrical said:**
> Ohhhhhh  :)

Yes, life with the Ubuntu dev cycle is full of ohhh's and ahhh's!  :KS

---

### Post by sudodus on 2015-11-02
I can confirm that this mtab bug is fixed also in Lubuntu :-)

---

### Post by ventrical on 2015-11-02
> **sgage said:**
> Yes, life with the Ubuntu dev cycle is full of ohhh's and ahhh's!  :KS

I was just having one of those ubuntu moments - ya know - where we are supposed to know  this stuff but draw a complete blank :) lol

---

### Post by sgage on 2015-11-02
> **ventrical said:**
> I was just having one of those ubuntu moments - ya know - where we are supposed to know  this stuff but draw a complete blank :) lol

There's an awful lot to remember - that's why I rely on the Group Mind here  :p  And why I try to contribute when I can  :KS

---

### Post by mikodo on 2015-11-02
> **sgage said:**
> There's an awful lot to remember - that's why I rely on the Group Mind here  :p  And why I try to contribute when I can  :KS
Funny! I was remembering last of night of when I was twelve years old, reading George Orwell's "1984" in a hospital bed. Scared me at the time. 

"Group Mind".

---

### Post by sgage on 2015-11-02
> **mikodo said:**
> Funny! I was remembering last of night of when I was twelve years old, reading George Orwell's "1984" in a hospital bed. Scared me at the time. 

"Group Mind".

Now mikodo, don't let Big Brother hear that. But he will, he will - he always does...  :KS

I had in mind something a bit more benevolent :-)

---

### Post by howefield on 2015-11-03
Thread closed.

---

