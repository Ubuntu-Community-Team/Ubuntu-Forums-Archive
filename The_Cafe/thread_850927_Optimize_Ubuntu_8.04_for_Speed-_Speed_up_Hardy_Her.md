---
title: "Optimize Ubuntu 8.04 for Speed
- Speed up Hardy Heron!"
date: 2008-07-06
forum: The Cafe
---

### Post by sharks on 2008-07-06
If HH is fast enough in your system dont tell me. this is for users whose HH system is slow.

So what if Ubuntu is a fast operating system?... There is always room for some more tweaking... and I am talking here about some aspects that are NOT useful for the end-users (yes YOU, the regular Ubuntu user). The hacks presented in this guide will greatly improve the overall performance of your Ubuntu 8.04 Linux OS.

WARNING: Please follow the instructions below very carefully, in the order in which they are listed and reboot your machine after each one. It is also possible to do them all at once, but rebooting after each one is much safer. Why? Because if your system won't work properly at a certain point of the tutorial, you'll know what's the last thing you did and you can revert back to the initial configuration. I've applied all these tweaks on three (3) different configurations (with SATA and IDE hard drives) with success!

This one will have it.

[http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml)

---

### Post by madjr on 2008-07-06
thanks, but hardy is already fast enough for me (even on my old pc with 256mb ram)

---

### Post by billgoldberg on 2008-07-06
It seems some of the steps are breaking peoples installs.

So use caution.

Most of the article seems to be about a faster boot up time.

Not something I'm interested in.

---

### Post by K.Mandla on 2008-07-06
Nice article. There are a lot more things you can do to improve Hardy's speed though.

[http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/](http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/)

An apology for the shameless self-promotion there. 

By the way, that /etc/fstab adjustment puts noatime and nodiratime together on the drive assignment line, but picking *noatime* includes *nodiratime*, so it isn't needed. Just thought I should mention it. ... :)

---

### Post by oldos2er on 2008-07-06
"http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml"

 sysv-rc-conf is much better at configuring services than Ubuntu's services menu. Also, I would backup each file before altering it; and where it says to use "sudo gedit ...", you should use "gksudo gedit ..." instead.

---

### Post by Sealbhach on 2008-07-07
> **oldos2er said:**
>  and where it says to use "sudo gedit ...", you should use "gksudo gedit ..." instead.

What's the difference?


.

---

### Post by damis648 on 2008-07-07
> **Sealbhach said:**
> What's the difference?


.

By gksudo he means gksu. This is the proper command... and the only difference between gksu and sudo is that sudo prompts for password in the terminal and gksu prompts in the GUI.

---

### Post by oldos2er on 2008-07-07
See [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by gigabyte05 on 2008-07-18
Thanks I need this tutorial

---

### Post by Jumpmasterrt on 2008-08-02
Do these modifications make the ENTIRE system faster or just the boot up? I'm finding that I boot just fine but programs (even gedit) take a bit of time to load.

---

### Post by Masoris on 2008-08-02
These tweak is good, but dangerous. Especially "data=writeback" tweak is the most.

If you change your ext3 partition setting to Writeback. You can feel your hard disk much more faster when read and write small files. But when you power off accidentally you could lost data. In my experience, I lost data for ubuntu boot after few times of accidentally power off, so I had to  reinstall Ubnutu. :(

---

### Post by Tom--d on 2008-08-02
> **Masoris said:**
> These tweak is good, but dangerous. Especially "data=writeback" tweak is the most.

If you change your ext3 partition setting to Writeback. You can feel your hard disk much more faster when read and write small files. But when you power off accidentally you could lost data. In my experience, I lost data for ubuntu boot after few times of accidentally power off, so I had to  reinstall Ubnutu. :(

I've done the tweak but I'm on a Laptop. And when the mains gos out (which it never does) my battery will kick in.
I haven't done a hard shutdown in ages.

---

### Post by K.Mandla on 2008-08-02
> **Masoris said:**
> These tweak is good, but dangerous. Especially "data=writeback" tweak is the most.

If you change your ext3 partition setting to Writeback. You can feel your hard disk much more faster when read and write small files. But when you power off accidentally you could lost data. In my experience, I lost data for ubuntu boot after few times of accidentally power off, so I had to  reinstall Ubnutu. :(
I don't know that data=writeback is any more "dangerous" than any other file system setting. You could scan the original thread describing the tweak, two years ago, and see if it's any help.

[http://ubuntuforums.org/showthread.php?t=107856](http://ubuntuforums.org/showthread.php?t=107856)

I don't think any filesystem or setting is 100-percent proof against data loss in an accidental power-off. No matter what you use, there's always the chance something will be lost.

---

### Post by issueperson on 2008-08-07
> **K.Mandla said:**
> I don't know that data=writeback is any more "dangerous" than any other file system setting. You could scan the original thread describing the tweak, two years ago, and see if it's any help.

[http://ubuntuforums.org/showthread.php?t=107856](http://ubuntuforums.org/showthread.php?t=107856)

I don't think any filesystem or setting is 100-percent proof against data loss in an accidental power-off. No matter what you use, there's always the chance something will be lost.

What if I told you that increasing your journaling could speed up your system?

[http://www-128.ibm.com/developerworks/linux/library/l-fs8.html#4]("http://www-128.ibm.com/developerworks/linux/library/l-fs8.html#4")

and if you want to tweak your ext3 (experienced users only): [http://forums.gentoo.org/viewtopic-t-305871-postdays-0-postorder-asc-start-0.html]("http://forums.gentoo.org/viewtopic-t-305871-postdays-0-postorder-asc-start-0.html")

---

### Post by K.Mandla on 2008-08-16
> **issueperson said:**
> What if I told you that increasing your journaling could speed up your system?
Your link doesn't seem to work. 

Either way, you'd have to show me a lot to convince me that an old machine -- and by that I mean pre-Pentium III, just so we're on the same page, with commensurate hardware -- will get a speed burst by increasing the workload between no journaling and journaling.

---

### Post by binbash on 2008-08-16
totally crap howto.How can you talk about speed even you do not touch the kernel?If you want speed, you have to compile your own kernel.

---

### Post by issueperson on 2008-08-16
> **K.Mandla said:**
> Your link doesn't seem to work. 

Either way, you'd have to show me a lot to convince me that an old machine -- and by that I mean pre-Pentium III, just so we're on the same page, with commensurate hardware -- will get a speed burst by increasing the workload between no journaling and journaling.

Sorry about the bad links, I think they are fixed now (worked for me).

As far as speed goes, this is the first time I have ever used full journaling.  I have not noticed any speed difference and my drive is pretty safe if it ever goes down.

But for numbers, look at the link provided. Actual numbers are given.

---

### Post by K.Mandla on 2008-08-16
Cool, thanks. I'll check it out after work today. :)

---

### Post by K.Mandla on 2008-08-17
Interesting. I'll have to try it out. It looks like the best speed improvements were for servers trying to handle heavy disk access, which makes sense. I'll test it out on my own machine and see what results I can get. Thanks! :D

---

### Post by mike1234 on 2008-08-17
Disabling Bluetooth and Britty in services helps a little. I only use Compiz Fusion once in awhile because it's such a power hog. I have a decent Nvidia 256 meg card but I really notice a difference not running Compiz. Tweaks are asking for trouble in my opinion. Ubuntu runs just fine for me as is. Why risk breaking your system?

M.

---

### Post by K.Mandla on 2008-08-17
> **mike1234 said:**
> Tweaks are asking for trouble in my opinion. ... Why risk breaking your system?
[quote=John Milton]I cannot praise a fugitive and cloistered virtue, unexercised and unbreathed, that never sallies out and sees her adversary, but slinks out of the race where that immortal garland is to be run for, not without dust and heat.[/quote]
;)

---

### Post by mike1234 on 2008-08-17
> **K.Mandla said:**
> ;)

Poets smoke crack. You know that don't you? :lolflag:

M.

---

### Post by empty_tank on 2008-08-18
> **issueperson said:**
> 

As far as speed goes, this is the first time I have ever used full journaling.  I have not noticed any speed difference and my drive is pretty safe if it ever goes down.



I've been using data=writeback before I read your post about data=journal and I also noticed no difference in speed.  Thanks for the tweak.

---

### Post by vietanh on 2008-09-04
> **binbash said:**
> totally crap howto.How can you talk about speed even you do not touch the kernel?If you want speed, you have to compile your own kernel.

My computer is Laptop IBM ThinkPad T23. Cam you guide me for recompiling the kernel for Ubuntu 8.04? Thank you very much.

---

### Post by K.Mandla on 2008-09-08
> **vietanh said:**
> My computer is Laptop IBM ThinkPad T23. Cam you guide me for recompiling the kernel for Ubuntu 8.04? Thank you very much.
If your T23 is like [this]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=migr-4ytg43"), then you can probably use most of the settings [here]("http://kmandla.wordpress.com/2008/06/08/howto-16-second-boot-on-550mhz-celeron-with-crux/"). Here's a [howto for rebuilding Ubuntu's kernel]("http://ubuntuforums.org/showthread.php?t=56835"), and you might find a few tips [here]("http://kmandla.wordpress.com/2008/07/29/finally-grub-to-gnome-in-under-a-minute/").

The real difficulty in recompiling a kernel is making sure you disable the hardware you don't have, don't use and don't need, without disabling something that you do have, use or need. Since every machine is different, it gets a little tricky. Be prepared to start from scratch, in case you build something irrecoverable.

But otherwise, binbash is right. The best speedups come from trimmed kernels. There really is no substitute.

---

### Post by bp1509 on 2008-09-08
d

---

### Post by K.Mandla on 2008-09-08
Those are good times. What kind of hardware are you using?

---

### Post by bp1509 on 2008-09-08
d

---

