---
title: "WIndows users:  Not using Wubi is NOT reccomended."
date: 2009-10-25
forum: Testimonials &amp; Experiences
---

### Post by Dullstar on 2009-10-25
I hosed a Windows installation by not using Wubi.  Please, save your self a day or two of trouble if you need a dual boot, and use Wubi.

NOTE:  Placed in Absolute Beginner Talk as a warning to beginners.  Mods may wish to move this to testimonials and experiences (sometimes its hard to judge where the best place to put a thread is).

---

### Post by OpenGuard on 2009-10-25
Why ? I've never used Wubi for dual-boot :rolleyes:

---

### Post by Dullstar on 2009-10-25
I hear versions pre 9.10 work fine, but 9.10 introduced Grub2.  It didn't work so well.  It was Grub2's problem, not Ubuntu 9.10's.

---

### Post by VastOne on 2009-10-25
Never have used Wubi and never will

---

### Post by Wa1k3rTXRang3r on 2009-10-25
I've never had any trouble dual booting Windows and Ubuntu.

I've never used Wubi either.

---

### Post by NCLI on 2009-10-25
> **Dullstar said:**
> I hear versions pre 9.10 work fine, but 9.10 introduced Grub2.  It didn't work so well.  It was Grub2's problem, not Ubuntu 9.10's.
Did you run "sudo update-grub" after installation? I presume your Windows install didn't show up in the boot menu, right?

---

### Post by bkratz on 2009-10-25
Never used wubi either--matter of fact I didn't even know what a live-CD was (kinda wish I had--wireless problems) .  The first thing I did was dual boot.

---

### Post by QIII on 2009-10-25
I've run dual boots for years.

I have all of my machines using GRUB2, dual booting some flavor of Linux and Windows.  I have one machine that triple boots Karmic, Vista and OpenSolaris.

[sudo]sudo os-prober[/code]

[sudo]sudo update-grub2[/code]

Getting OpenSolaris to boot is just a matter of editing a config file.

You have had problems that we can sort out here and we'd be happy to help you with that.  But the problem is neither with GRUB2 nor Ubuntu.

Wubi is a test drive, not a final set up.

---

### Post by yanceypd on 2009-10-25
The only time I had trouble was using Wubi.

---

### Post by SkyNet2029 on 2009-10-25
> **yanceypd said:**
> The only time I had trouble was using Wubi.
 
agreed. I triple quad boot xp,7,ubuntu and opensolaris. before all of this madness I gave wubi a try. It destroyed everything.
As for grub2, it does cause problems, even in debian. to think it would work just cause its ubuntu is silly. Stick with what works, not with a fake install of a great system (wubi). This post seems prejudiced and pointed in the wrong direction. Maybe it should be moved before the trolls grab hold?

---

### Post by aktiwers on 2009-10-25
> **SkyNet2029 said:**
> agreed. I triple quad boot xp,7,ubuntu and opensolaris. before all of this madness I gave wubi a try. It destroyed everything.
As for grub2, it does cause problems, even in debian. to think it would work just cause its ubuntu is silly. Stick with what works, not with a fake install of a great system (wubi). This post seems prejudiced and pointed in the wrong direction. Maybe it should be moved before the trolls grab hold?

Dude you should use Virtualbox if you run so many OS's :D

---

### Post by LewRockwell on 2009-10-25
> **yanceypd said:**
> The only time I had trouble was using Wubi.

> **SkyNet2029 said:**
> agreed. I triple quad boot xp,7,ubuntu and opensolaris. before all of this madness I gave wubi a try. It destroyed everything.
As for grub2, it does cause problems, even in debian. to think it would work just cause its ubuntu is silly. Stick with what works, not with a fake install of a great system (wubi). This post seems prejudiced and pointed in the wrong direction. Maybe it should be moved before the trolls grab hold?

After all the horror stories regarding the wubi-buntu grenading-install-disasters found both here at the Ubuntuforums and elsewhere on the interwebs...

We won't be using it or recommending it to others either...

Still, everyone should have the fresh back-up/clone they just did right before screwing with their stuff...

So what's the big deal?

.

---

### Post by JoshuaRL on 2009-10-25
> **LewRockwell said:**
> So what's the big deal?

Well, not everyone takes rigorous backups like they should.  And some new users, even if they have good backups, get kind of freaked out if they screw up an install and can't figure it out.  Making sure things are smooth as possible on install is everyone's responsibility.

---

### Post by martrn on 2009-10-25
> **Dullstar said:**
> I hosed a Windows installation by not using Wubi.  Please, save your self a day or two of trouble if you need a dual boot, and use Wubi.

Instead of using wubi you should partition your hard drive or use vmware.  wmware gives you full acsees to your virtual disk drive however wubi installations  are noted for being unable to recover repair or have many tools for.  You can wreck you ubuntu installation by installing the wubi kernel, yea sure windoze is safe but not your virtual ubuntu drive if you loose your wubi install.

---

### Post by coldReactive on 2009-10-25
Never used Wubi either, but I don't dual boot, I use it as my only system (I'm using Windows right now, but am waiting for 9.10.)

---

### Post by LewRockwell on 2009-10-25
here's another exploded wubi-grenade:

[http://ubuntuforums.org/showthread.php?t=1301043](http://ubuntuforums.org/showthread.php?t=1301043)

.

---

### Post by LewRockwell on 2009-10-25
> **JoshuaRL said:**
> Making sure things are smooth as possible on install is **everyone's responsibility**.

***_everyone's responsibility????***_

Ummm...sorry...not even close...

Our equipment and installations are OUR responsibility...

And others are responsible for their own equipment, installations, and due-diligence

[http://en.wikipedia.org/wiki/Due_diligence](http://en.wikipedia.org/wiki/Due_diligence)

.

---

### Post by Locke_99GS on 2009-10-25
I've never used Wubi, and have never had a problem dual b ooting Windows and Linux; I've been doing it for years. I've been using Karmic since early alpha, and it found Windows just fine on it's own.

---

### Post by There Was A Time on 2009-10-25
I'd have to strongly suggest that if you're using a laptop/netbook, then you should do a proper install, as last time I checked, Wubi wouldn't allow you to hibernate, which is vital for school/work.
 
Wubi might be easier, but it's a lot messier when doing anything inside that Ubuntu install.

---

### Post by humphreybc on 2009-10-25
If you know what you're doing, there's no reason to use Wubi.

---

### Post by martrn on 2009-10-25
> **LewRockwell said:**
> Our equipment and installations are OUR responsibility... And others are responsible for their own equipment, installations, and due-diligence


Err not true.
I am only bound by contract law, nothing else.
[http://en.wikipedia.org/wiki/English_contract_law]("http://en.wikipedia.org/wiki/English_contract_law")

Eg. The GPL etc...

The only thing I can do is...
[URL="http://en.wikipedia.org/wiki/Computer_Misuse_Act_1990"]
http://en.wikipedia.org/wiki/Computer_Misuse_Act_1990[/URL]
Not to gain acsess to your computer without your permission.

I do not have to be in any way shape or form 'diligent'.

---

### Post by jfloydb on 2009-10-25
I've used wubi for 8.04, 8.10, and 9.04. I have never had a problem with the wubi install, and un-installing was always easy. I plan to do a wubi install for 9.10 as well.

I probably would have never tried Ubuntu if I had to repartition of my hard drive just to get past the live CD. As a matter of fact, I have read several "horror stories" on this forum concerning repartitioning a hard drive to create a true dual boot -- for now, no thanks. 

I have a dedicated Ubuntu box, but/and on my Windows computers, I use the wubi installed Ubuntu. I would recommend wubi for anyone who really wants to use Ubuntu without (perhaps, imagined) risk.

---

### Post by QIII on 2009-10-25
> **humphreybc said:**
> If you know what you're doing, there's no reason to use Wubi.

People often do not know what they are doing.  The end result is usually "Ubuntu is a POS!"

Few potential Linux users come into the world knowing what we were doing.  Most people don't have access to half a dozen computers at home to experiment with and not worry about screwing anything up.  Wubi is a fine way to learn what you are doing.  Asking questions on a forum like this before launching into the unknown is not a bad idea.

I started using *nix in the 70s.  For me, Windows was a distraction for a few years.  For most, it is all they know.  "If  you know what you are doing..." is a tall order when you take your first Linear Algebra course.

How is the OP supposed to learn what he is doing without doing?

---

### Post by steveneddy on 2009-10-25
IMHO - Wubi is for a short trial period so one can "try out" Ubuntu, kick the tires, so to speak.

Dual booting is effortless if done correctly and one does one's homework beforehand.

I personally prefer to run Ubuntu as the main OS and use VirtualBox to run Windows. I keep as .iso of Vista in my /home folder in case it gets hosed for some reason for fast reinstallation purposes.

Again, it is only my opinion that I think that Wubi sucks. Your mileage may vary.

My .02 - thank you for your time.

---

### Post by edin9 on 2009-10-26
I've had some minor issues with WUBI in the past. I uninstalled it but was still stuck with the boot menu on startup. Nothing major, but it was enough to destroy my confidence in WUBI to the point that I haven't used it again.

---

### Post by bumanie on 2009-10-26
I have a triple boot with 2 ubuntu's & 1 xp and am using grub 2 and have never had a problem with windows 'being hosed' by the ubuntu installation. IMO wubi is a hack for users only to try ubuntu for a short time while deciding whether to use it as a permanent OS or not.

---

### Post by jfloydb on 2009-10-26
> **bodhi.zazen said:**
> Just to clarify some common musunderstandings about wubi ....

wubi is an Ubuntu installation and is in fact dual booting and not virtualization.

wubi uses the windows boot loader and thus grub is not installed.

wubi installs into a file within windows and is mounted on a loop mount when ubuntu is booted.

...wubi is often misunderstood.

This is something that I came across. It was posted by one of the admins...

---

### Post by martrn on 2009-10-26
This is something I came across :

> Cooperative Linux, abbreviated as coLinux, is software which allows Microsoft Windows and the Linux kernel to run simultaneously in parallel on the same machine. Cooperative Linux utilizes the concept of a Cooperative Virtual Machine (CVM). In contrast to traditional VMs, the CVM shares resources that already exist in the host OS. In traditional (host) VMs, resources are virtualized for every (guest) OS. The CVM gives both OSs complete control of the host machine while the traditional VM sets every guest OS in an unprivileged state to access the real machine.
[http://en.wikipedia.org/wiki/Colinux]("http://en.wikipedia.org/wiki/Colinux")

See also :
Topologilinux, a Slackware-based distribution
Platform virtualization
Comparison of platform virtual machines
Cygwin
MSYS
Wubi 
Linux Unified Kernel

Host machine : Linux-Loopmounted Device
Guest machine : Linux virtual Kernel

If I am wrong correct me ?????????
It is not still virtualisation ????????

---

### Post by 3rdalbum on 2009-10-26
Wubi has some notable downsides:

1. If Windows crashes, you need to boot into Windows first successfully before you can boot into Ubuntu (due to the unclean state of the NTFS filesystem if it hasn't been properly unmounted).
2. If Windows crashes and will no longer boot, then you can't get to Ubuntu due to the reason above
3. Hibernation doesn't work with Wubi
4. You are limited to 30 gigabytes in Wubi
5. You don't get full speed
6. If your Windows partition is Fat32, you can't use Wubi (it installs Ubuntu into a file, and that file is going to be over the 4GiB fat32 filesize limit).
7. If you decide you don't want Windows anymore, it's not the easiest thing to migrate your Wubi to a real partition.

I installed Ubuntu using Wubi for a friend. He had a problem with Windows that was preventing him from booting it fully, and as a result he also couldn't boot Ubuntu.

I tend to recommend NOT to use Wubi due to these limitations. Just be careful with your partitioning and make sure you have a backup of any important data. Remember, filesystems are NEVER designed to safely resize, and PC BIOSes support partitioning only as an afterthought; it's amazing that partitioning works as reliably as it does!

---

### Post by mdsmedia on 2009-10-26
I haven't used Wubi, simply because when I think about Ubuntu being installed as a Windows "guest" I think "warning...warning...warning".

For the same reason I won't install any Linux distro as a "guest" of Windows, I won't install Wubi. 

To me, Windows is a guest on my machine. Ubuntu is the main OS, and if Windows seeks to exist, it will be the guest.

---

### Post by solwic on 2009-10-26
> **mdsmedia said:**
> I haven't used Wubi, simply because when I think about Ubuntu being installed as a Windows "guest" I think "warning...warning...warning".

For the same reason I won't install any Linux distro as a "guest" of Windows, I won't install Wubi. 

To me, Windows is a guest on my machine. Ubuntu is the main OS, and if Windows seeks to exist, it will be the guest.

+1.  Besides, Wubi runs off the NTFS file system, and you won't get the full effect of any Linux distro unless you go full-on, with journaling file systems to unlock all of Ubuntu's speed and efficiency.  

As for Windows...well, it's not even on my machine.  It was an unwelcome guest, so I gave it the boot.  Ubuntu only, please. :)

---

### Post by Pasdar on 2009-10-26
Dual boot? My PC is pure.

---

