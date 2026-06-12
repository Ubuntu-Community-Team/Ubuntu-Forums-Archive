---
title: "Multi boot CD"
date: 2007-11-07
forum: The Cafe
---

### Post by Lostincyberspace on 2007-11-07
I would like to design a multi boot CD and was wondering if any one has done this before if it is new territory that i will have to go it alone.

I was also wondering what people would like in one.
So far the list of what i have so far is DSL, Super Grub, Parted Magic.

I will continue to look for more things to while i figure out how to set it up.

Please post your ideas

---

### Post by maybeway36 on 2007-11-07
You could add a FreeDOS rescue floppy.
[http://www.finnix.org/files/balder10.img]("http://www.finnix.org/files/balder10.img")
You can boot it directly from ISOLINUX boot loader, or use MEMDISK if that doesn't work.
Not sure how you're going to get multiple Linuxes on there, though.

---

### Post by Lostincyberspace on 2007-11-07
Thanks for the reply I will try to work that in.

PS I am also looking for people to be initial seeders for the CD vi bittorent it might not be for a while though.

---

### Post by Dragonbite on 2007-11-07
What about *(links to distrowatch for additional information)*
[LIST]
[*][[COLOR="Blue"]System Rescue[/COLOR]]("http://distrowatch.com/table.php?distribution=systemrescue")
[*][[COLOR="#0000ff"]TinyMe[/COLOR]]("http://distrowatch.com/table.php?distribution=tinyme")* (which is based off of PCLinuxOS but lighter)*
[*][[COLOR="#0000ff"]Puppy[/COLOR]]("http://distrowatch.com/table.php?distribution=puppy") *(popular light distro as DSL)*
[/LIST]

---

### Post by init1 on 2007-11-07
> **Lostincyberspace said:**
> I would like to design a multi boot CD and was wondering if any one has done this before if it is new territory that i will have to go it alone.

I was also wondering what people would like in one.
So far the list of what i have so far is DSL, Super Grub, Parted Magic.

I will continue to look for more things to while i figure out how to set it up.

Please post your ideas
This has been done before, but not the way I think you intend to go. The Ultimate Boot CD is mainly a repair/utility disk, and includes many non-open source applications. I think it would be cool to have a CD that would boot a number of distros and OS's. With the help of memdisk, you can boot any floppy image, so I recommend adding these:
[Menuet]("http://www.menuetos.net/")
[Kolibri]("http://www.kolibrios.org/")
[Visopsys]("http://visopsys.org/")
[Solar_OS]("http://www.oby.ro/os/")
[Freedos]("http://www.freedos.org/")
[RxDOS]("http://rxdos.sourceforge.net/")
[http://ubcd.sourceforge.net/index.html](http://ubcd.sourceforge.net/index.html)
I would be glad to contribute to this project.

---

### Post by Lostincyberspace on 2007-11-07
Thanks I will try to include those,

I also will try to work in the Minimal Ubuntu ISO.
located here [Minimal Ubuntu CD]("https://help.ubuntu.com/community/Installation/MinimalCD")

---

### Post by init1 on 2007-11-07
> **maybeway36 said:**
> You could add a FreeDOS rescue floppy.
[http://www.finnix.org/files/balder10.img]("http://www.finnix.org/files/balder10.img")
You can boot it directly from ISOLINUX boot loader, or use MEMDISK if that doesn't work.
Not sure how you're going to get multiple Linuxes on there, though.
It can be done. Might require some linuxrc modification though.

---

### Post by az on 2007-11-07
It's easy to make a multi-boot cd.  Just use isolinux.  You add an entry into the isolinux.cfg for every image you have.

As for what I would like on it:
ubuntu-rescue-remix

Also, is there an XAMMP live cd?  If not, maybe just a base server install with the LAMP task.

---

### Post by Lostincyberspace on 2007-11-07
Thanks for the link to the ultimate boot cd i shows how to add a linux os on to it so i will probably start from there

---

### Post by Lostincyberspace on 2007-11-08
*bumb*

---

### Post by Dragonbite on 2007-11-08
I can't find the link right now, but Solaris provided a DVD they would ship (for free) or I assume you could download. I'm on dial-up so I didn't even bother to look at that option.

Anyway, the DVD allowed for booting up into 4 different distributiions and had options for them as well (boot to KDE version, XFCE version, etc.).  

Could look around there and see how they did it. Sorry I'm not more helpful.

---

### Post by NotRoot:-) on 2007-11-08
I was just wondering if it will be possible to create a multi boot DVD?   One disk to rule them all.  :-)   That way we'd have more room for mutiple linux distro's and other tools.

---

### Post by Dragonbite on 2007-11-08
> **NotRoot:-) said:**
> I was just wondering if it will be possible to create a multi boot DVD?   One disk to rule them all.  :-)   That way we'd have more room for mutiple linux distro's and other tools.
Possible? Yes.  I have the openSolaris DVD at home to prove it :)
How? um.. uh.... magic?! ;)

---

### Post by zachtib on 2007-11-08
> **Lostincyberspace said:**
> Thanks for the reply I will try to work that in.

PS I am also looking for people to be initial seeders for the CD vi bittorent it might not be for a while though.

i'll help seed it for you (it's free advertising for deluge)

you may want to look at Ultimate Boot CD ([http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)) for ideas.  you can also use it as a starting point for your own CD.

---

### Post by maybeway36 on 2007-11-08
Suggestion: add as many floppy images as you can find. Memdisk makes it easy :P

---

### Post by Lostincyberspace on 2007-11-08
I have begun to take in to consideration all that has been said and have begun work on weeding out as many as possible i have a bout 8 gigs of small distos and tools that I need to weed out to make sure I don't have any duplicates. I thank every one for all the input there has been and I will try to update my progress at least daily so continue to post any ideas you have.

---

### Post by NotRoot:-) on 2007-11-08
I just came across this URL for multiple live CD to DVD:
[http://www.linuxquestions.org/questions/linux-general-1/multiple-live-cd-to-dvd-523091/?](http://www.linuxquestions.org/questions/linux-general-1/multiple-live-cd-to-dvd-523091/?)

---

### Post by blithen on 2007-11-08
Dude this is seriously a great idea. I will download ASAP once the ISO comes out.

---

### Post by Lostincyberspace on 2007-11-08
I have a question would people rather like this to a Linux Show Off Disk or would you like it to be a system repair tool. I am leaning more towards the second as of now.

---

### Post by az on 2007-11-09
> **Lostincyberspace said:**
> I have a question would people rather like this to a Linux Show Off Disk or would you like it to be a system repair tool. I am leaning more towards the second as of now.

If you want a linux system repair tool, it would be a lot easier to maintain if you included all the repair tools in one OS on the disk.  You could pick a distro like Ubuntu, install all of the relevant packages from the repos and put that on the disk along with other non-linux images.  That would be a lot more useful than having several distros, each with their own little subset of tools.

For one thing, it would make it a lot easier to maintain.  Just think of how may projects you are going to have to keep track of.  If you use the ubuntu package manager, you get the latest versions of the software in one place.

---

### Post by init1 on 2007-11-12
> **Lostincyberspace said:**
> I have a question would people rather like this to a Linux Show Off Disk or would you like it to be a system repair tool. I am leaning more towards the second as of now.
I think the best idea would be to make it a show off disk. There are plenty of repair distros already, including Ultimate Boot CD. The other purpose would simply be to consolidate some distros and make them easier to try out.

---

### Post by Lostincyberspace on 2007-11-12
As of just a little while ago, Sunday some time, I decided that it would be good to do both so I will probably start of with a show off disc since their are plenty of system repair tools but no multi distro show off tools. 

PS. I would do a DVD but I don't have a burner right now so I wouldnt be able to test it. and CD's are cheaper to mess up with so no worry if something goes wrong. Once I get a DVD burner I will start work on a multi boot with the 3 most popular distros from distrowatch.

---

### Post by brennydoogles on 2007-11-14
> **Lostincyberspace said:**
> As of just a little while ago, Sunday some time, I decided that it would be good to do both so I will probably start of with a show off disc since their are plenty of system repair tools but no multi distro show off tools. 

PS. I would do a DVD but I don't have a burner right now so I wouldnt be able to test it. and CD's are cheaper to mess up with so no worry if something goes wrong. Once I get a DVD burner I will start work on a multi boot with the 3 most popular distros from distrowatch.

Install Virtualbox, and you can at least make an initial test on your DVD image without burning a dvd

---

### Post by NullHead on 2007-12-12
Awesome idea! I will seed and download/use when/if you make it. I have something similar to this it has all kinds of gentoo based distros such as gparted and system rescue. When you make this disk I would ask you put super-grub on it:D that bust be the best MBR toolI've ever used!! :popcorn:

---

### Post by smartboyathome on 2007-12-12
I did a little research and found a post on Linuxquestions.org which says how to do it:
[QUOTE=m4mach]This is not so difficult:

1. Unpack all ISOs to /live
2. Make one /live/isolinux/isolinux.cfg for all kernels
3. Run:
```
# cd /live
# mkisofs -N -J -R -D -o /m_boot.iso -b /live/isolinux/isolinux.bin -c /live/boot.catalog -no-emul-boot -boot-load-size 4 -boot-info-table .
# qemu -cdrom /m_boot.iso -boot d
```[/QUOTE]

You can leave out the last line (just boots it in QEMU), but it looks pretty easy. I wonder how this would work with an Ubuntu/Kubuntu/Xubuntu ISO and installing since it copies the filesystem from the disk... ;)

---

### Post by Lostincyberspace on 2007-12-12
I have been trying to work on integrating super grub in to be part of the main boot loader it has been problematic trying to figure out how to work with it.

---

### Post by smartboyathome on 2007-12-12
Try using isolinux, like it says in the quoted post above.

---

### Post by Lostincyberspace on 2007-12-12
I am trying to Integrate the super grub disc in to the boot and it takes more than just putting everything together like that.

---

### Post by smartboyathome on 2007-12-12
Btw, check [this]("http://ubuntuforums.org/showthread.php?t=378021") thread, it might give you more insight on how difficult it is.

---

### Post by init1 on 2007-12-12
> **Lostincyberspace said:**
> I have been trying to work on integrating super grub in to be part of the main boot loader it has been problematic trying to figure out how to work with it.
Actually, it's rather easy. Super Grub is available on a floppy, so you can simply memdisk boot it.

---

