---
title: "Slax is nice"
date: 2006-03-27
forum: The Cafe
---

### Post by towsonu2003 on 2006-03-27
and very fast if you have enough ram... 

I just tried this livecd distro upon a poster's advice (for a LiveCD that works without CD in the Drive). This is the web site [http://slax.linux-live.org/](http://slax.linux-live.org/)

Once you boot with "slax copy2ram" at boot prompt, it copies everything to the RAM (as read&writable). booting and shutting down takes a while of course (filesystem uncompressed to RAM takes some time, 5-15 minutes). although it is small, you can add stuff you want using the "modules" (which are packages converted from slackware packaging format tgz). And, it was the second ever distro that made my slmodem work (after Ubuntu). 

I'm amazed at what people can do with so little space (~160MB)! 

A few problems I encountered during my test: 
1. You **have** to read the "known bugs" section before downloading or using. 
2. wvdial doesn't work (reported to devel)
3. can't add new user (will post to their forum). 
4. Check out the modules. You can always install them during your live cd session as well I think (and possibly all Slackware packages??)

Anyone who want their friends / relatives to try Linux from a live cd while having the opportunity to eject the CD (which means: you can listen to music or watch DVDs, read documentation from CD, nd so on), this would be a nice distro. 

I wish there was a way (may be there is one that I don't know of) to load Ubuntu live CD to ram like this.

PS. This is not spam. Just in case someone will think of that :)

---

### Post by taurus on 2006-03-27
If you want to install Slackware based on your machine, Vector is another option, running Xfce4!  That baby flies on my old machine and in fact, I use it as my ftp server upstairs at work...

---

### Post by taurus on 2006-03-27
Argh!!!  Double post...

---

### Post by towsonu2003 on 2006-03-27
[QUOTE=taurus]If you want to install Slackware based on your machine, Vector is another option, running Xfce4!  That baby flies on my old machine and in fact, I use it as my ftp server upstairs at work...[/QUOTE]
Argh, I can't install Slackware... Kernel (2.4 in Slackware) isn't good for laptops. I need to learn how to compile Ubuntu's kernel (with modules) for Slackware, put it in grub (was it lilo?), and get the correct modules to load up on boot. I don't have time to learn that, unfortunately. The last time I did that, my lsmod showed only 3 modules up... I'll check out Vector though, thanks :)

---

### Post by majikstreet on 2006-03-27
slax is nice.. though I've actually never booted with it, I've remastered it.. I've never used the remasters lol... 

majikstreet

---

### Post by rado_london on 2006-03-27
Is there an option to install Slax on hard drive

---

### Post by towsonu2003 on 2006-03-27
[QUOTE=rado_london]Is there an option to install Slax on hard drive[/QUOTE]
yes, but I didn't try it. You'll need to check out their documentation I guess. 

Oh, and, it seems a newer version is coming up soon (from 5.0.8 to 5.1.0).

---

### Post by towsonu2003 on 2006-03-27
[QUOTE=majikstreet]though I've actually never booted with it, I've remastered it.. I've never used the remasters lol...[/QUOTE]
by "remastering" you mean? I'm just ignorant (and curious), sorry :)

---

### Post by majikstreet on 2006-03-28
ermm I guess it's not exactly remastering..
I mean like taking the cd and adding/removing stuff to/from it..

like you know the modules? well if you extract the iso you can put modules in the modules directory and then do the make iso bashscript thingy and make a new iso :D

---

### Post by towsonu2003 on 2006-03-28
[QUOTE=majikstreet]
like you know the modules? [/QUOTE]
oh yes the modules. They're cool, like firefox extensions or something: easy to use and just converted from Slack packages. 

PS. For anyone interested, I used the Archive Manager to extract the ISO and modify it. Than I remade the ISO with Gnomebaker and burned the CD with nautilus (bc my gnomebaker is stuck for some reason). Worked fine except wvdial module (couldn't write or read its configuration file).

---

### Post by taurus on 2006-03-28
[QUOTE=towsonu2003]Argh, I can't install Slackware... Kernel (2.4 in Slackware) isn't good for laptops. I need to learn how to compile Ubuntu's kernel (with modules) for Slackware, put it in grub (was it lilo?), and get the correct modules to load up on boot. I don't have time to learn that, unfortunately. The last time I did that, my lsmod showed only 3 modules up... I'll check out Vector though, thanks :)[/QUOTE]
You don't have to use the default kernel, 2.4.  You can install the latest kernel, 2.6 in the /test directory...  That's what I have running on my Slackware.  There is even instruction in that directory, /test, showing you exactly how to install the 2.6 kernel.

---

### Post by towsonu2003 on 2006-03-28
[QUOTE=taurus]You don't have to use the default kernel, 2.4.  You can install the latest kernel, 2.6 in the /test directory...  That's what I have running on my Slackware.  There is even instruction in that directory, /test, showing you exactly how to install the 2.6 kernel.[/QUOTE]
I heard that Slack 11 will be coming out soon. So I guess I will try that one, with its testing kernel, and may be Ubuntu's kernel (which means every Ubuntu kernel update = kernel compile in Slack). For the time being (3-4 months), I'm stuck with the current setup anyway (writing thesis, repartitioning not recommended ;) ).

---

### Post by Krigl on 2006-03-28
[quote=rado_london]Is there an option to install Slax on hard drive[/quote] 
It is, but it's just LILO overwriting your normal GRUB so it appears like only Slax bootable. You have to restore GRUB from install CD.

BTW. anyone met the problem with monitor frequency? I got just 76 Mhz, xconf helps just for KDE (slow), while Fluxbox remains unchanged.

---

