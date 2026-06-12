---
title: "Virus transfer from Ubuntu to Windows on Dual boot system?"
date: 2011-06-13
forum: Security
---

### Post by Maxepr on 2011-06-13
I know that Linux has no viruses out in cyberland that affect it but would it be possible for a Micrcrap virus to wiggle through an Ubuntu partition and find its way into the Windows portion of the same hard drive on a dual boot system when the windows portion is not being used?

---

### Post by doas777 on 2011-06-13
possible but very improbable. 
not only would the malware delivery system have to detect a windows system and place a malcode file upon it, but it would also have to arrange for windows to execute it. on the ubuntu side of things, those actions are almost definitely going to need a sudo somewhere (especially if you don;t mount your windows disks in ubuntu).

---

### Post by Maxepr on 2011-06-13
Thanks. I was curious. It's one of those "what if the moon crashed into the earth...things". Highly improbable but not impossible.

---

### Post by Maxepr on 2011-06-15
briensmith,

I never considered the idea of physically transferring a virus from Ubuntu to windows when copying or moving a file. I know that windows viruses don't affect Linux but the idea of having one lying around on my Linux partition "waiting to attack" bothers me. 

I have always been about a 6.5 on the "virus paranoia scale" anyway. This is something that I was curious about. Personally, I wish I could go completely Linux but there are simply programs that are not written for Linux and I need them so I have to keep Microcrap on my PC. 

Thanks
Maxepr

---

### Post by dodo3773 on 2011-06-15
I do not see a Windows virus being able to "wiggle" through a Ubuntu system. Especially if your Windows partition is not mounted. Even if it was if you don't put it there yourself it would still have to go to the mount point which is probably /media or something similar which is usually owned by root. It would have to be a very very good virus.

---

### Post by SeijiSensei on 2011-06-16
If the Windows partition isn't mounted, the malware would have to run as root and mount the partition in the background before copying its payload into your Windows OS.  In Ubuntu, you'd need to be tricked into running a trojan and giving it root privileges.  That's a lot of work for a very small target population of users.

You have even less to worry about if you're concerned that malware hiding out in your Linux filesystem(s) might somehow be executed when you're running Windows.  Windows doesn't have a driver for ext filesystems, so it can't see the Linux filesystems at all.  (There is an [open-source driver]("http://www.ext2fsd.com/") for ext2/3 filesystems, but I'm guessing you don't use it.  There's [no good candidate yet]("http://ubuntuforums.org/showthread.php?t=1557151") for ext4.)

The best defense against malware resides between your ears.  Don't execute anything you don't trust completely.  That's just as true in the Linux world as anywhere else.  I install nearly all my software from the repositories and a few trusted PPAs.  For anything else, like [mplayer2]("http://www.mplayer2.org/"), I'm usually compiling from source.

---

### Post by jerome1232 on 2011-06-16
Rather than targeting win/linux dual boot machines to copy itself to a windows partition then lie in wait to exploit windows. A virus writer would be much more successful just exploiting windows directly.

That being said if you want to scan from Linux, eset has a linux version of their antivirus, it'll pickup all the same viruses as their windows version.

---

