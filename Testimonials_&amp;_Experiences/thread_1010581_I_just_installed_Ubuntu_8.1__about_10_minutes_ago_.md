---
title: "I just installed Ubuntu 8.1  about 10 minutes ago !!"
date: 2008-12-13
forum: Testimonials &amp; Experiences
---

### Post by morph999 on 2008-12-13
Wow...this is really good.   I am impressed.  Only thing that bugs me a bit is that the font is a little small.  I think I'm working in like 1280 x 1024 or something and I'm not used to that.   I'm used to 1024 x 768 .   Other than, everything works great and it works almost exactly like Windows XP and it's fast.  I can load webpages much faster with Linux/firefox 3.0  than with windowx xp/IE8beta2  .   I was impressed with IE8 beta2 as well, though but they have some bugs to work out before it's ready.  I didn't know it was this easy to make a dual boot linux and windows xp or I would have done it earlier.  Nice job guys.   I did have to disable my anti-virus and firewall to get it to install but that was no problem.   Hell yeah.   I think open source software is the future.  Maybe a day will come when the linux guys will have websites and rake in the amount of money that guys like thepiratebay are doing, that would be nice and create incentives to make even better software.  It'd create a new industry just like torrents did.   

Anyone know what computer language that Ubuntu was written in?

BTW, I'm using the AMD64 version.

---

### Post by cdtech on 2008-12-13
From the "wiki" page "Linux kernel":
> Linux is written in the version of the C programming language supported by GCC (which has introduced a number of extensions and changes to standard C), together with a number of short sections of code written in the assembly language (in GCC's "AT&T-style" syntax) of the target architecture. Because of the extensions to C it supports, GCC was for a long time the only compiler capable of correctly building Linux. In 2004, Intel claimed to have modified the kernel so that its C compiler also was capable of compiling it.[25]

Many other languages are used in some way, primarily in connection with the kernel build process (the methods whereby the bootable image is created from the sources). These include Perl, Python, and various shell scripting languages. Some drivers may also be written in C++, Fortran, or other languages, but this is strongly discouraged. Linux's build system only officially supports GCC as a kernel and driver compiler.
[http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)

---

### Post by dennis0623 on 2008-12-13
> **cdtech said:**
> From the "wiki" page "Linux kernel":

[http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)
I loaded Ubuntu 8.1 but cannot get my Huawei EC228 Wireless Internet Card to work.  It recognize's the card but I cannot configure it.  The card is from alltel wireless as is supported by windows vista, Mac OSx 10.4 or higher.  Do I assume it will not operate on the Linux platform?  Any help would be appreciated.

---

### Post by morph999 on 2008-12-13
btw, I have a compaq presario  AMD AthlonTm 64 x2 dual core processor 3800

And I got a Nvidia graphics card  7300GT.  All I did was turn my modem on and ubuntu instantly said I was connected.  

Only thing I had to do once I installed  Ubuntu was do some upgrading using the terminal becuase I needed the flash player and I couldn't upgrade the flash player via the macromedia website because it wouldn't work.  but now I'm okay

I typed in this stuff to get my flash to work

Open a Terminal from the menu Applications &#8594; Accessories &#8594; Terminal and type:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

sudo apt-get install flashplugin-nonfree

sudo apt-get clean

give your user password when requested, you don't see nothing when you type it, then press enter.

************************************

I know how to program in C programming.  Wonder if I could be any help to them.  I'm not real good but I know how to program some things.

---

### Post by morph999 on 2008-12-13
> **dennis0623 said:**
> I loaded Ubuntu 8.1 but cannot get my Huawei EC228 Wireless Internet Card to work.  It recognize's the card but I cannot configure it.  The card is from alltel wireless as is supported by windows vista, Mac OSx 10.4 or higher.  Do I assume it will not operate on the Linux platform?  Any help would be appreciated.

Mine is a wired configuration so I can't help you there.   I have a basic AT&T DSL setup without a router.

---

### Post by cdtech on 2008-12-13
> **dennis0623 said:**
> I loaded Ubuntu 8.1 but cannot get my Huawei EC228 Wireless Internet Card to work.  It recognize's the card but I cannot configure it.  The card is from alltel wireless as is supported by windows vista, Mac OSx 10.4 or higher.  Do I assume it will not operate on the Linux platform?  Any help would be appreciated.

It will work on the Linux platform, the kernel writin in c has nothing to do with your hardware. Post a separate thread titled "alltel wireless config help" with your problem and it will be answered.

---

### Post by morph999 on 2008-12-14
I've decided that I'm never upgrading to Vista or Windows 7.  I'm finished with Windows.   Whatever I need for Ubuntu or any Linux installation, I'll make do or figure something out but I'm done with Microsoft.  I don't trust them.  I think open source is the future unless Govt comes in or big business comes in and wrecks everything or buys people off...which is a possibility but we always have hope even if that happens.   I think Microsoft has hit a dead-end, only place for them to go is more DRM, more intrustion into our privacy to make money.   I realize that and that's why I've come to the Linux community.  After witnessing Vista on my machine, I realized that MSFT is really selling out to spyware companies and probably music companies and that's a bad sign.  I don't feel like getting fines in the mail for watching movies so I'm switching operating systems.

---

### Post by solwic on 2008-12-14
> **morph999 said:**
> I've decided that I'm never upgrading to Vista or Windows 7.  I'm finished with Windows.   

Same here.  I keep my XP Home CD and Key in case Ubuntu ever goes under, but I would only use Windows again until I could order a Mac.  

I'm done with Windows, unless they make some very, very radical changes in their OS.  

:D

---

### Post by wolfen69 on 2008-12-14
> **morph999 said:**
> I did have to disable my anti-virus and firewall to get it to install but that was no problem.

you lost me there. did you install wubi style? if so, it's not a true dual boot. anyway, glad you like it.

---

### Post by armandh on 2008-12-14
welcome
font size can be changed 
system>preferences>appearances font tab

---

### Post by JC Cheloven on 2008-12-15
> **morph999 said:**
> I've decided that I'm never upgrading to Vista or Windows 7.  I'm finished with Windows.   Whatever I need for Ubuntu or any Linux installation, I'll make do or figure something out but I'm done with Microsoft. 

Glad to hear that. 

Nevertheless, I'm a bit worried about your early enthusiasm, and wouldn't like to see it turning into a later disappointment. Keep in mind that despite the titanic effort of the community, gnu-linux in general and ubuntu in particular has still a number of things to improve. Some depend on the community, but some doesn't (as for example hardware support).

So please, be prepared to learn new things, to be patient and constructive when you find a bug, and to develop a feeling of community. A community that will make a difference in terms of freedom in the society, indeed :-)

To better explain my thoughts: I'm a free software advocate, and everyone around me knows about gnu, linux, debian and ubuntu. I "converted" about ten people last year. But my advice to them is not to suddenly give up the OS they're used to. I think it's just unpractical. Instead, I usually suggest: 

Take your responsibility in using free software for as many things as you can. It will improve if we use it. And if there is something that eventually you don't manage to do (yet), well, that's why you didn't deleted (yet) that "evil partition".

I've found this to be a good piece of advice ;-)

---

