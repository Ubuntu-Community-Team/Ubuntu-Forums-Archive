---
title: "Should I give up on Ubuntu?"
date: 2008-10-02
forum: Testimonials &amp; Experiences
---

### Post by caligula08 on 2008-10-02
I am experiencing problems with Ubuntu Dapper Drake.  I have used Hardy Heron with some success but on another machine with considerable memory.

Recently, I acquired a Compaq Evo N600 at a good price from a swap meet.  Since it only had 256 megs of RAM, I wasn't able to install Hardy so I chose Dapper instead.

In the two weeks, I have experienced numerous issues trying to compile and integrate PCMCIA drivers into the kernel.  The kernel, itself, configures and installs ok but there are endless errors generated when I attempt to make the driver source code.  In researching it on the net,
I have come across uncountable problems with this same set-up.  Apparently, everyone is having problems like this.

Getting C/D recordable software to work has also been frustrating.  None of the domain packages perform and the functions included in the C/D
distro also bomb out.

Anyway, all I am wondering is if others also see a problem with Ubuntu?  It seems there is so much cross-modularization that it would take a super-computer just to keep track of all the packages.  It's funny how everyone in the Linux community pans Windows yet, when it comes to installing an application, Windows is vastly superior.

Well, perhaps my probem is insufficient memory?  But I thought that
Linux could function well at 256 megs.  Also the machine has actually
frozeon up on me several times now ... a la the Windows blue screen of
death yet I have read numerous times that Linux NEVER crashes!?

Anyway, I need a recommendation as to another package to experiment with.  Can anyone suggest a good distro for a 5-yr-old wireless pcmcia
card?  Thanks for taking time to read my woes ...

---

### Post by agurk on 2008-10-02
Get the Hardy alternate CD (non-graphical installer) instead, it should work fine on 256MB RAM.

---

### Post by rustybronco on 2008-10-02
> **caligula08 said:**
> 

In the two weeks, I have experienced numerous issues trying to compile and integrate PCMCIA drivers into the kernel.
Anyway, all I am wondering is if others also see a problem with Ubuntu?No, I use it on four machines.

> **caligula08 said:**
> It's funny how everyone in the Linux community pans Windows yet, when it comes to installing an application, Windows is vastly superior. Odd... I tried to put my oem copy of windows xp on a my wife's HP nc6000 laptop and it  took more than twice as long to install as 8.04, plus the wireless card was still not being recognized. I had forgotten you needed to download the drivers for the wireless card ,also the drivers for the IR, touch pad and who knows what else...I gave up the thought of continuing with the windows xp install because "I was spoiled using 8.04 with it's ease of install"

> **caligula08 said:**
> Well, perhaps my probem is insufficient memory?  But I thought that Linux could function well at 256 megs.  Also the machine has actually frozeon up on me several times now ... a la the Windows blue screen of death yet I have read numerous times that Linux NEVER crashes!?I've had it crash, mostly because of what I did to it learning my way around. (got to learn to stand before you walk)

> **caligula08 said:**
>  Can anyone suggest a good distro for a 5-yr-old wireless pcmcia
card?See the links in my signature to try getting your card working first or, do as I did, get one that works well with linux (the last pcmcia card I bought cost me 8.00 USD)

now on to your question... the choice is yours, not mine.

I made mine two years ago... was it easy at first? NO... but it was as foreign to me then, as windows is now  :)

---

### Post by 3rdalbum on 2008-10-03
As with any operating system, you should be using the latest version of it.

Dapper is over two years old, which is an eternity in Linux.

If 256mb of RAM is too little for Ubuntu Hardy, then you should try Xubuntu Hardy.

---

### Post by Crafty Kisses on 2008-10-03
Yeah you should probably upgrade, as much as I love Dapper, Dapper is getting older.

---

### Post by Sef on 2008-10-03
> Yeah you should probably upgrade, as much as I love Dapper, Dapper is getting older.
Dapper's Desktop updates will stop in June 09.

---

### Post by stalkingwolf on 2008-10-03
I installed fiesty on a Compaq evo n600c and gave it to my neice. The only
problem she had was when she forgot her password.  She figured out how to recover that and used it until last summer when she got her new one before going to Fresno State.  As far as I know her Dad is still using it.

As I recall it does have 512 GB of ram though.  I also have a Toshiba Tecra
8200 that ran fiesty fine on 256 and now runs hardy on 512. I am currently using it
as a loaner when Im working on someones computer.  :D   I figure if I cant get them to try it Ill wait
till they break their windows then let them borrow mine.

---

### Post by azimuth on 2008-10-03
> **caligula08 said:**
> 
Anyway, I need a recommendation as to another package to experiment with.  Can anyone suggest a good distro for a 5-yr-old wireless pcmcia
card?  Thanks for taking time to read my woes ...

I would recommend Xubuntu 8.04.1 alternate install. This distro version runs fine business on my Gateway Celeron 550 w/ 192MB of ram and a PCMCIA wireless. It does require ndiswrapper for the unsupported Trendnet wifi, but there are dozens of tutorials here on using the wrapper and windows drivers.

I also have this version running on a Pentium 200 w/160 MB ram and a PII 450 w/256MB that I use for serving files on my LAN. All of these computers are 8 to 10 years old and 256Mb or less of ram.

I have found Hardy to run faster and smoother than Dapper on my older machines and the alternate install disk avoids the ram requirements of running the LiveCD.

Good Luck and I am sure you will be rewarded if you persevere.

---

### Post by Sef on 2008-10-03
> Recently, I acquired a Compaq Evo N600 at a good price from a swap meet. Since it only had 256 megs of RAM, I wasn't able to install Hardy so I chose Dapper instead.


> I have found Hardy to run faster and smoother than Dapper on my older machines and the alternate install disk avoids the ram requirements of running the LiveCD.

The alternate cd is not hard to use.  The only tricky part of it is partitioning manually if you have never done it.  If you want, download [Intrepid]("http://cdimage.ubuntu.com/releases/8.10/beta/"), which is beta and see if that runs better.

---

### Post by cardinals_fan on 2008-10-04
> **Sef said:**
> Dapper's Desktop updates will stop in June 09.
...which will signal the end of the golden days of Ubuntu.

*wipes away a tear*

---

### Post by Flimm on 2008-10-06
If you have only 256MB of memory I would not recommend Ubuntu. Try Xubuntu, or a totally different distribution of Linux.

---

### Post by yman on 2008-10-06
I used Dapper with this card:
3com megahertz model 3CCFEM556 B

I found a working solution here:
[http://ubuntuforums.org/showthread.php?t=238073](http://ubuntuforums.org/showthread.php?t=238073)

For me, I think all I had to do in the end is run the command
cardmgr
as root in order to make it work. That means entering
sudo cardmgr
in the terminal every time I wanted to use the internet. To make it permanent add it to the start up script at runlevel 3 (I think. This was over 1.5 years ago and I forgot the details).

After Dapper, support for my card got worse, and is probably non-existent at this point.

---

### Post by kspncr on 2008-10-07
> **caligula08 said:**
> It's funny how everyone in the Linux community pans Windows yet, when it comes to installing an application, Windows is vastly superior.

This simply is not true. "Everyone" in the Linux community does not pan Windows, nor is Windows "vastly" superior to Linux when it comes to installing programs. We can argue it's far simpler to install programs in Linux distros like Ubuntu (click add/remove programs, select program you want, click install... How can it get any simpler?)

But anyway, you should try Xubuntu.

---

### Post by caligula08 on 2008-10-10
ok.  well that was an interesting cross-section of opinions.  and not
one snotty reply in the batch ...

aas far as giving up on Linux goes, not a chance.   i realize that you have to invest more energy in low-level learning with Linux than windows
but the ultimate rewards will make it all worth it.

thanks again to everyone for contributing

---

