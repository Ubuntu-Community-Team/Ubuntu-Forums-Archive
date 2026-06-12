---
title: "Linux Finally"
date: 2006-01-17
forum: Testimonials &amp; Experiences
---

### Post by PhrankDaChickenGeek on 2006-01-17
Thank you ubuntu! I finally have a linux system that *just works!* :D 

I've tried DSL, SLax, SuSE, Mandrake, Madrivia, Knoppix, but none fit the need.

One thing I could never get to work was sound. Old computer, on board sound driven through ISA, but with the all the help of these forums got it working!!

I'm now a gnome person too. Works better for me, flows, and seems faster than anything else I've used.

Now installed Ubuntu BB 5.10 on Dell Optiplex GX1
550Mhz (yeah, maybe slow, but seems faster than XP did)
512Ram (that helps)
32Mb Nvidia +
8Mb Maxtor M II (took a little conf to get xorg working)
Hp Scanjet 5P
Still working on getting all buttons on HP 5302  internet keyboard mapped correctly.

Hope to take Ubuntu to college on a laptop!

---

### Post by Sef on 2006-01-18
Congrats on getting your system up and fully working.   That's the nice things about linux; if one distro don't work, then there are others to try.  Once I went through about a few distros before finally finding out that vector linux worked on this old computer.

---

### Post by bloodborne on 2006-01-19
For me, this is the huge advantage of Ubuntu: it's level of operability out of the box. Glad to hear you got sound working, for me tweaking my wireless connection was the only thing that required a bit of work. But it's all good now. Welcome!

---

### Post by zeroconf on 2006-08-25
> **PhrankDaChickenGeek said:**
> Thank you ubuntu! I finally have a linux system that *just works!* :D 

Hp Scanjet 5P


I have the same scanner and Kubuntu 6.06 and this scanner does not work :(
I wrote also here full story:
[http://kubuntuforums.net/forums/index.php?topic=8244.0](http://kubuntuforums.net/forums/index.php?topic=8244.0)

---

### Post by loockb on 2006-10-03
> **zeroconf said:**
> I have the same scanner and Kubuntu 6.06 and this scanner does not work :(
I wrote also here full story:
[http://kubuntuforums.net/forums/index.php?topic=8244.0](http://kubuntuforums.net/forums/index.php?topic=8244.0)

Hi,

I got a bit further. I'm using SimplyMepis 6 (based upon Dapper).
Xsane is version 0.97, sane is 1.0.14-1.

1) I defined in /etc/udev/rules.d/50-mepis-overrides.rules :

# hp scanner
BUS="scsi", SYSFS{model}="C5110A*", KERNEL="sg*", NAME="%k", SYMLINK="scanner", MODE="0666"

2) In /etc/modules :

sym53c416


Results :

a) Running sane-find-scanner, it shows the scanner (twice) :
found SCSI processor "HP C5110A 3701" at /dev/scanner
found SCSI processor "HP C5110A 3701" at /dev/sg1

b) But 'scanimage -L' hangs.  :(

c) However, when running : scanimage -d "hp:/dev/scanner" > image.pnm
it actually made the scanner scan the page.

d) I could run once : xsane "hp:/dev/scanner"
It was as root, but I'm not sure this has a real effect. I could not do it twice. 

Remark : my hp printer often takes a page when running the xsane or scanimage -L command. 

Cheers, Ben

---

### Post by cunawarit on 2006-10-04
> **PhrankDaChickenGeek said:**
> 
550Mhz (yeah, maybe slow, but seems faster than XP did)

You could try a lighter distro, I have two old machines at home a PII300 and a Celeron 700. The PII300 in particular wasn’t exactly that fast with Ubuntu or Fedora, in fact I think it was slower than it was with a clean install of XP. But worked great with Damn Small Linux and Debian using fluxbox. 

I settled for Debian and fluxbox for the Celeron, at some point I’ll try another light distro for the PII.

You could look into Xubuntu (Xfce is much lighter than Gnome), Damn Small Linux, or Puppy Linux (I haven’t tried this one myself).

Anyway, I am new to Linux too. Have fun :) 

> *just works*

In my experience most popular OSs, just work A-OK.

---

### Post by dolphinsonar on 2006-10-05
Taka a deep breath and delete your windows partitian.  Pretty envigorating.

---

