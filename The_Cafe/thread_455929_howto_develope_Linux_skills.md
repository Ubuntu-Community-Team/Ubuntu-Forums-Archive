---
title: "howto develope Linux skills?"
date: 2007-05-27
forum: The Cafe
---

### Post by mbradlcu on 2007-05-27
Hi all,
recently I found a solution to a sound issue I was having, the fix was:
echo 'kingpin 0 0 direct' > /proc/asound/card0/pcm0p/oss
great! but,, I've been using Linux for some time, I know what the /proc dir does in a general way and use it to view system info and even set things on the fly... but how can I get to the point were I'd know that the above command would resolve a sound issue.. or other issues at that level? the 'man proc' is a deep step for me and it doesn't mention asound specifically.. I'd like to put the effort in but don't really know were to start.
thanks!!

---

### Post by Stephen Howard on 2007-05-27
I wouldn't expect anyone to know it 'naturally' except the guys who wrote the ALSA sound driver.  

The real skill is to know how to search for an answer and to recognise it when you see it - which you obviously did!

---

### Post by Stephen Howard on 2007-05-27
The other skill is to spread you knowledge around - and you've done that because now anyone searching for kingping and sound will find a likely answer.  Indeed, it helped me because I am having sound problems with another application, and I'll give the solution a try!

---

### Post by Boomy on 2007-05-27
Document everything in a journal and keep it for a reference.

---

### Post by trippinnik on 2007-05-27
Besides learning from doing and experimenting you could try [http://en.wikibooks.org/wiki/LPI_Linux_Certification](http://en.wikibooks.org/wiki/LPI_Linux_Certification) also looking around on the forums and trying to solve problems or reading about solutions or howtos on various things has helped me a bunch...

---

### Post by ThinkBuntu on 2007-05-27
Use a distro that makes you work a bit, but still is very useful. Two I'd recommend for this in a heartbeat are Arch and Zenwalk. Zenwalk requires less work than Arch, and both are the fastest out there. I'm not sure how much Gentoo will teach you about Linux (for practical purposes), but it will teach you portage and other tools needed in Gentoo. Ubuntu, Debian, and others pretty much take care of it all for you.

---

### Post by Stephen Howard on 2007-05-27
> Boomy said:  Document everything in a journal and keep it for a reference.

This is great advice.  I couldn't count how many hours my linux journal has saved me.   It goes back 10 years, and always comes in handy - not just when problems arise but as a record of my customisations.  Sometimes after a particularly traumatic debugging effort, I've thought, "I'll never forget that fix", but don't believe it, always add it to the journal.  

The journal doesn't have to be complicated - as an example, here's a cut&paste of my most recent entries (the important thing is to have consistent topic names to make searching easier):

> 26 April 07
**CRYPTO:		**Set up cswap and made /tmp a tmpfs ramdisk which swaps out to swap.  SDA11 is no longer used, it can be removed.

25 April 07
**THUNDERBIRD:	**Set it to autostart by adding a desktop file to /home/stephen/.kde/Autostart

23 April 07
**XORG:		**The x11 error, "bad device... etc" is caused by the wacom configuration sections in the xorg.conf file.  Delete those and it goes away.

22 April 07
**FIREFOX:	**Just realised that java wasn't working in firefox.  I fixed it by using the 17 Jan 05 symbolic link (after altering the directories which have changed).

21 April 07
**UBUNTU:	**Installed 7.4, Feisty Fawn.  Install went okay.  Very painless in fact.

17 March 07
**GRUB:		**I setup a boot option in the grub boot string "vga=791" which gives a nice console resolution.  I think it also starts up fbdevice.  Oops don't forget to run update-grub for the changes to stick.

7 January 07
**NVIDIA:		**I have installed the various Beryl programs.  I wasn't getting any window borders.  The fix is to add the following to the nvidia device section of xorg.conf:      Option  "AddARGBGLXVisuals"   "True"

---

### Post by ububaba on 2007-05-27
Smart but simple

---

### Post by joe.turion64x2 on 2007-05-27
Another distro that would make you think a bit is Fedora.

---

### Post by Mateo on 2007-05-27
Man pages really are terrible, for the most part. They are written for people who already know how to use the application.

---

### Post by emshains on 2008-10-25
Try compiling you're kernel you're self, then try to make a distribution that is specifically made for a box of yours, where everything is compiled from source!

---

### Post by Saint Angeles on 2008-10-25
i've been using Ubuntu as my sole OS for a little more than a year now, and I'm still learning more stuff...

thats what i like about linux: it forces you to learn more about your computer and how it works. this is different from windows or OS X which spoon-feed everything to you.

I would suggest learning your bash shell commands. you can get a lot done with CLI quicker than GUI most of the time... and it makes you look like a computer guru!

---

### Post by K.Mandla on 2008-10-25
Closed for necromancing.

---

