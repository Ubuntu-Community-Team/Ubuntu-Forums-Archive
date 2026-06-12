---
title: "Problem reinstalling Ubuntu - Busybox prompt"
date: 2009-01-08
forum: System76 Support
---

### Post by newdarteruser on 2009-01-08
I wanted to reinstall Hardy on my Darter Ultra 3 (maybe 2? I forget). But when I boot from the Live CD, after choosing a language and loading the kernel, I am presented a BusyBox initramfs prompt.

I looked around all of yesterday on the internet and found many people with the same kind of problem but no real solution. I strongly suspect it has to do with my CD/DVD drive not being properly configured or something like that. Some people said setting their CD drive as secondary slave fixed it, but I don't really know how to do that.

I also tried a Linux Mint Live CD and that didn't work either - it wouldn't let me access my hard drives.

The CD is not the problem - I burned it twice, with the slowest speed.

Please help - I'm in great need of a fresh installation.

---

### Post by Lee_Machine on 2009-01-09
I had the same problem with my Pangolin Performance when I wanted to put 32 bit Hardy back on it. I even had the same problem with Ibex 32bit. There is better support for the 32 bit flavor. ie. boxee, offical Java web plugin, ZSNES...
I was told that it came down to the hardware that is in the laptop is not supported out of the box, and will only work with 64 bit in Safe Graphics mode.

So I just run other OSes in Virtualbox when I want to either test them. Linux Mint is cool.

---

### Post by theozzlives on 2009-01-09
I've had that prob on my older boxes, I just used the alternate CD.

---

### Post by newdarteruser on 2009-01-09
Hmm, I'll try the 64 bit version then. I had hoped to be able to run 32 bit hardy to maybe get my webcam working.
Thanks.

---

### Post by Light821 on 2009-01-09
[http://www.kolotibablo.com/?ref=422881](http://www.kolotibablo.com/?ref=422881) good money be sure !

---

### Post by thomasaaron on 2009-01-09
newdarteruser,

It would help to know which computer model you are using. The DarU2 and DarU3 are radically different. 

Getting your webcam working, though, isn't a matter of 32-bit or 64-bit. It's just a matter of installing Ubuntu and running your System76 driver. 

Does your Darter have a P1 and P2 button above the keyboard? If so, it is a DarU2. If not, it is a DarU3. Or, if it is white, it is a DarU1. Judging by your name and the small number of posts you've been involved in, though, I'm guessing its a DarU3.

The Alternate CD idea is a good idea. Or, installing using the CD's Safe Graphics Mode probably will work as well.

---

### Post by newdarteruser on 2009-01-09
It's a daru3 (3 buttons above keyboard- mail, web, etc).

The webcam very briefly worked with cheese , never with skype, though now it doesn't work any where. 
Just see colors and bars on cheese.  Skype doesn't see any video device.  

Anyway, the webcam is not my biggest concern. I want a fresh install of either 32/64 bit to improve overall performance. Boot time has gotten long and there are some other weird bugs. 

I'll try 64 bit regular, 64 bit alternate and 32 bit alternate in that order. 
Thanks.

---

### Post by Lee_Machine on 2009-01-09
Dont bother with a fresh install. It will be just a waste of your time if there is nothing major wrong.

Slow system and load times are usually due to broken and orphaned depedancies. Here is to simple way how to fix it.

[http://knowledge76.com/index.php/Cleaning_up_System_Junk](http://knowledge76.com/index.php/Cleaning_up_System_Junk)

---

### Post by newdarteruser on 2009-01-10
Installing Hardy 64 bit regular also failed. I get the same BusyBox prompt after a bunch of errors like :

ata2 : revalidation failed
ata2 : exception emask something
ata2 : irq something

I feel like this is definitely something to do with the cd/dvd drive.

---

### Post by Lee_Machine on 2009-01-10
did you try booting up in safe graphics mode? Being a darter and with on board graphics you shouldbt need to but try.

Optical drives rarely fail like that. They usually have problems like, the motor to the door burns out, the optical reader goes bad or get a scratch...usually mechanical problems. 

if you can boot up normally and use the drive then its probably not the drive.

---

### Post by thomasaaron on 2009-01-10
Those errors could also represent a bad cd burn.

---

### Post by compholio on 2009-01-10
1) Assuming you're having difficulty using the CD:
There should be an option in the CD boot menu to check the CD, if that checks out then try hitting the key for "other options" (I do not remember what it is ATM) and select the kernel flag "all-generic-ide".

2) Assuming you're having difficulty after install from the CD:
Check that your CD is OK (see 1), it's possible it copied a bad file.  If the CD is ok then on boot use the "Esc" key to get your GRUB menu and then hit "e" to edit your boot options.  Hilight the "kernel" line and hit "e" to edit the line, at the end of the line add a space and then "all-generic-ide" then hit enter to end editing.  Now hit "b" to boot.  If that works it is only a one-time thing, you should run the System76 driver and all updates.  If that doesn't fix the problem for your next boot then you should edit /boot/grub/menu.lst to permanently add "all-generic-ide" to your kernel flags.

---

### Post by newdarteruser on 2009-01-10
I tried the all_generic_ide before. No luck. 

I didn't mean that the cd drive has failed - just that maybe some setting is wrong. 

I checked the md5 & it was correct. 

I've made 4 burns so far. 

When I choose Test cd for defects I get the same errors:
ata2: revalidation failed
ata2: COMRESET failed (errno=-16)
ata2: exception Emask
ata2: irq_stat some number

Safe graphics mode doesn't work either. Same error. 
The cd just stops spinning before these errors show up. 

The alternate cd also gave me the same errors when I said check CD for defects but then proceeds with the check which is successful. However I'm wary of completing the installation when I'm not sure if the errors will affect my installation.

---

### Post by newdarteruser on 2009-01-10
When I remove the quiet splash keywords from the boot options of the CD (and add all_generic_ide and irqpoll) the messages that I see at the very end before the BusyBox prompt are roughly

ata2: ATAPI something, Optiarc Drive ...
Then it stalls for a while and then 

ata2: qc timeout 
ata2: failed to IDENTIFY something
ata2: port slow to respond ... please be patient...
ata2: failed to recover some devices, retrying in 5 secs
(in some order)

and then the usual revalidation failed, etc.

Very similar to this : [http://lists.debian.org/debian-user/2007/06/msg01277.html](http://lists.debian.org/debian-user/2007/06/msg01277.html)

---

### Post by Lee_Machine on 2009-01-10
I personally would just give up. In your post you said you wanted to do a fresh install to increase system performance, right?

Just follow my previous post about how to clean out system junk. you can also google other things you can do.

---

### Post by newdarteruser on 2009-01-12
Any other suggestions? Basically no installation CD works (the same CDs work on other computers).

---

### Post by thomasaaron on 2009-01-12
Give me a call at support. Just use the sales number...
[http://system76.com/article_info.php?articles_id=24](http://system76.com/article_info.php?articles_id=24)

---

### Post by arepaking on 2009-02-08
Hi newdarteruser,
Would you mind updating your results? I also have a Daru3 and I would like to know what did you guys did to fix your issue.

Thanks in advance,
AK

---

