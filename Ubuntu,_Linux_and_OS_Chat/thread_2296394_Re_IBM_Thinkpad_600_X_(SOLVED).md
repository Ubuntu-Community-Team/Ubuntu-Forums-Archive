---
title: "Re: IBM Thinkpad 600 X (SOLVED)"
date: 2015-09-25
forum: Ubuntu, Linux and OS Chat
---

### Post by alan41 on 2015-09-25
Hi
First I have to say I love my xubuntu installation on my old PC.

So I thought I would install a version of Linux on an old but very good IBM Thinkpad 600E and I thought it would be easy !!!

It only has a CD drive so I was limited to what fits on a CD 700MB.  I does have a USB but it cannot be booted from this I have researched.

After several attempts with several different distributions non of which completed installation I decided to wipe the HDD using DBan and try again.  The same result..... crashed installs or installs that never completed.

I tried:
Ubuntu mini.iso
Lubuntu

I have now used the IBM Product Recovery disk and installed WIN 98 in the hope that this would better prepare the machine for an install but no luck.

Can anyone help as I have run out of ideas.  Any Ubuntu distribution on this machine would make me happy as the sole os.

thanks in anticipation

---

### Post by coffeecat on 2015-09-25
According to one link I found, the IBM ThinkPad 600E comes with a maximum of 64MB RAM. Which would be insufficient even for Lubuntu, the lightest of the Ubuntu flavours. And that is possibly why the Lubuntu installer crashed. And you'll never get Ubuntu itself to work in such a tiny amount of RAM.

I suggest you post the full specifications of your ThinkPad and confirm the amount of RAM you have on it. Then members can advise what your best option would be. In the meantime, you might find the Old hardware brought back to life sticky thread useful reading:

[http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

By the way, you don't need to do any "better preparation" of the machine prior to installing. The installer will write a new MBR if necessary and create the partitions for you. Windows 98 would simply get overwritten. The reason for the installer crash is most likely the lack of RAM.

---

### Post by sudodus on 2015-09-25
Please specify your computer

- Brand name and model (we know already, but the other details are important)
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It makes it easier to help. Before knowing more, I would suggest an ultra-light linux distro, Wary Puppy, TahrPup or Tiny Core.

See also this link: [Old hardware brought back to life](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by Bucky Ball on 2015-09-25
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by stalkingwolf on 2015-09-25
according to the specs here [http://www.engadget.com/products/ibm/thinkpad/600/specs/]("http://www.engadget.com/products/ibm/thinkpad/600/specs/")  it only has a 6gb hdd.  if so that will 
drastically limit choices.

---

### Post by ArgentWarrior on 2015-09-25
> **stalkingwolf said:**
> according to the specs here [http://www.engadget.com/products/ibm/thinkpad/600/specs/](http://www.engadget.com/products/ibm/thinkpad/600/specs/)  it only has a 6gb hdd.  if so that will 
drastically limit choices.

Maybe the OP should consider Arch with a tiling WM.

---

### Post by alan41 on 2015-09-25
Many thanks for the help and suggestions.

for those that need extra information to help me I have gleaned the following info:
IBM Thinkpad 600x
WIN 98 
576MB RAM
Available on drive C 698 MB of 2044 MB FAT
Available on drive D 9448 of 9448 MB FAT32
windows manager swap file on drive C 698 MB free
(I presume these are partitions as I recall putting a 10GB HDD in it many years ago.)
intel pentium [r] II processor Intel MMX [tm]
standard PCI Graphics Adapter
the wifi is a plug in KLS 611 802.11g wireless notebook network card.

---

### Post by sudodus on 2015-09-25
With 576 MB RAM and a 10 GB HDD and a Pentium II CPU it should be possible to run Puppy and Tiny Core. You cannot expect that it will work well to browse the internet to modern web-sites with a lot of bells and whistles ;-)

Maybe Wary Puppy is better than TahrPup for such an old computer, but you should try both of them.

A current version of Lubuntu did not work for you. I guess you tried 14.04 LTS. An alternative is a community re-spin based on Ubuntu 12.04 LTS with older hardware drivers. The graphics driver might be critical. Maybe you can try LXLE or ToriOS.

Summary: I think that Wary Puppy and Tiny Core are the best alternatives. And I think this computer will be more for playing with linux than for daily use.

---

### Post by grahammechanical on 2015-09-25
Here is a thought. When you install do not tick the box "Install third party software." That will give you not only some proprietary video and audio codecs but also a proprietary video driver. And the driver will be the latest one for that version of Ubuntu. Which in turn will not have support for such an old video adapter. And that means failure on restart.

If the live session runs then it is running on an open source video driver. And that is what you will get for the installed OS by not ticking the box "install third party software." This is the same for all flavours of Ubuntu.

Regards.

---

### Post by alan41 on 2015-09-26
> **sudodus said:**
> With 576 MB RAM and a 10 GB HDD and a Pentium II CPU it should be possible to run Puppy and Tiny Core. You cannot expect that it will work well to browse the internet to modern web-sites with a lot of bells and whistles ;-)

Maybe Wary Puppy is better than TahrPup for such an old computer, but you should try both of them.

A current version of Lubuntu did not work for you. I guess you tried 14.04 LTS. An alternative is a community re-spin based on Ubuntu 12.04 LTS with older hardware drivers. The graphics driver might be critical. Maybe you can try LXLE or ToriOS.

Summary: I think that Wary Puppy and Tiny Core are the best alternatives. And I think this computer will be more for playing with linux than for daily use.

Following your suggestion I have now just downloaded Puppy wary-5.5.iso and burnt to a CD

it all started well with a 'puppy screen logo etc' then I got:
puupy-wary-5.5.sfs not found !
i do not understand why this file would not be included in the download, I do recall my installation on Ubuntu on my other machine installing seamlessly so why is this happening?

---

### Post by sudodus on 2015-09-26
I tested, and it works for me to boot with wary-5.5.iso. There is no complaint about that file. Please check with md5sum, that the iso file was downloaded correctly. You may need to burn a new CD at the slowest burning speed possible.

```
$ [COLOR="#0000FF"]md5sum wary-5.5.iso[/COLOR]
3763175a51a6428aaf2bb28de868b00b  wary-5.5.iso
```

---

### Post by stalkingwolf on 2015-09-26
damn small linux is another option

---

### Post by PaulW2U on 2015-09-26
> **stalkingwolf said:**
> damn small linux is another option
Really?

Current Release Candidate: 4.11.RC2, [http://www.damnsmalllinux.org/forums/index.php?topic=59](http://www.damnsmalllinux.org/forums/index.php?topic=59)

A release from over **three** years ago?

---

### Post by night_sky2 on 2015-09-26
Puppy Linux is the best for dinausor computers. I would try Precise Puppy which is based on Ubuntu 12.04 LTS: [http://puppylinux.org/main/Long-Term-Supported%20Puppy.htm](http://puppylinux.org/main/Long-Term-Supported%20Puppy.htm)

You don't even need to install it. It's so lightweight you just burn the iso on your CD, it will boot on (very limited) RAM. You can save files & settings between sessions.

---

### Post by tgalati4 on 2015-09-27
Also, it helps to create a swap partition on your disk drive before trying to install.  Since you only have 10 GB, you could try a small swap partition of 600 MB, which is slightly larger than your RAM.  That will help you get through the installation.  Understand that any distro using a modern browser will clobber your RAM which means using swap.  Using swap on an old hard disk is painfully slow.

Your computer could be useful for programming Arduino's or other embedded projects or to use as a graphical ssh terminal for other machines.  To use as a daily Desktop Linux machine, not so much.

---

### Post by alan41 on 2015-09-27
[QUOTE=Summary]: I think that Wary Puppy and Tiny Core are the best alternatives. And I think this computer will be more for playing with linux than for daily use.[/QUOTE]

Why can this old laptop run XP just fine but seems from what has been said that very few Linux distros are available ?

---

### Post by sudodus on 2015-09-27
XP was created very long ago, made to work with the hardware of that time. It is also possible to run many old linux operating systems (from the same time), but we do not recommend them, because they are no longer supported (no updates: no bug fixes, no development, not even security bug fixes).

This is also the case with XP, no more updates, ... not even security bug fixes. (I think the lifetime of XP was prolonged because big companies, important customers for Microsoft, needed it and were not willing to change to a new operating system. But it has passed end of life now.)

Fortunately there are a few current linux distros for very old hardware :-)

---

### Post by coffeecat on 2015-09-27
@alan41, you can discount the comment I made about RAM in post #2. That was based on the specifications I found and before you confirmed that you have 576 MB RAM. That is more than enough for Lubuntu, so there is probably another explanation for the installer crashing. 

What you haven't clarified is what graphics card the machine has. Some GPUs from that vintage can be problematic in Linux. Do you know the details of the graphics?

---

### Post by The_Forgotten_King on 2015-09-27
Damn Small Linux. VERY low system requirements.

---

### Post by The_Forgotten_King on 2015-09-27
Also Slimboat browser for web if you want.

---

### Post by tgalati4 on 2015-09-27
Damn Small Linux is no longer supported, but it will run.  I have it running on an HP Omnibook, Pentium 1, 166 MHz, 64 MB.  And everything works.  But yes, XP will run on it, but not modern Linux distros.  Use XP if it serves your needs, otherwise, there are several Linux options, just none with the latest desktops and bells and whistles on that vintage machine.  

The build quality of those old Thinkpads is excellent.  So send it to me when you are tired of it.

---

### Post by alan41 on 2015-09-28
> What you haven't clarified is what graphics card the machine has. Some GPUs from that vintage can be problematic in Linux. Do you know the details of the graphics?

All I can find from the machine using the win98 menu is that it is a "Standard PCI Graphics Adapter" which I agree does not tell us much if you know od a better way to find out what it is let me know, I am no computer expert so need direction.

I have just tried a Peppermint-6 CD which fails even to run from the cd menu option i.e. trial mode.
 Set
I only want the machine to use as a back up database using LAMP.

The Peppermint is now running a mem test which revealed that the machine is a pentium III 498.3 MHz Mem 575 Chip set i440BX

---

### Post by sudodus on 2015-09-28
If you run a server operating system without graphics, only text interface, it might serve you well. Try an up to date version of Ubuntu Server 14.04.1 LTS.

---

### Post by alan41 on 2015-09-29
Have installed Tiny Core Plus which although very basic seems stable enough.  The repository however does not have MySQL server or phpmyadmin so if anyone can advise how I update the repository or how I Get them this would help.  I have installed apache2 and php5 as they were in the repository.

---

### Post by sudodus on 2015-09-29
Let us hope someone can help you find those packages for Tiny Core Plus.

Otherwise it might be an option to run Ubuntu Server without a graphical user interface. This is the recommended way to run a server, and it will let the services use as much as possible of the hardware (and not waste it on a user interface).

---

### Post by tgalati4 on 2015-09-29
Ubuntu server should run on that machine.  Install it using the "alternate install CD, 32-bit".  It will give you a minimal, text-based, server install.  Then install MATE on top of that to get a desktop environment.  Then you have all of the repositories at your disposal.  500 MHz PIII will not be fast.

---

### Post by alan41 on 2015-10-03
Hi There and thanks to all who have responded to my thread.

I was delighted to find in the latest issue (No.1382) of the magazine Micro Mart a Group Test of Small Linux Distros.

Having worked my way through them with various degrees of success I finally settled on Porteus as the best one for my IBM machine.

The place to find it should anyone want to try it is here  goo.gl/7lqBaj

Its a great little distro and much easier to set up than the others on my machine.

Thanks again

---

### Post by sudodus on 2015-10-03
Thanks for sharing your solution :-)

---

### Post by coffeecat on 2015-10-06
> **zangxuma said:**
> i have a one ibm think pad t60 laptop iwant to reinstall the oprating system but cnot done. the error is comming on the screen is
setup didnot find any hard disk drives installed in your computer.
but hard disk showing in bios and already installed os are woking normally.what is the reason !

@zangxuma, please start your own thread if you need help. Your problem is different from what this thread is about and this thread is already marked as solved, so people are unlikely to see your question. 

I'll close this thread now.

---

