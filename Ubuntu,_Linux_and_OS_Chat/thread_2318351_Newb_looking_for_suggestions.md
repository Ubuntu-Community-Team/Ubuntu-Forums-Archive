---
title: "Newb looking for suggestions"
date: 2016-03-25
forum: Ubuntu, Linux and OS Chat
---

### Post by john532 on 2016-03-25
Hello,
I recently had on old Dell PowerVault 745N fall into my lap. It runs remarkably well, and while it's definitely on the low end as far as power goes (1 GB RAM, 4 250 GB drives, Pentium 4 @ 3 GHz, Windows Server 2003 Appliance Edition), I've only had to replace a CMOS battery to get it running smoothly. I thought it'd be fun to try messing around with it, and maybe use it as a multimedia server. I've done a little bit of research and, though I've never used Linux before, thought now might be a good time to try it out. I've ordered some additional RAM and eventually I'll be upgrading the drives as well.

To start though, I wanted to see what suggestions you folks might have as for the OS. It's a 32 bit system, so I'm a little bit limited, but I imagine the server version of Ubuntu is going to be the best fit? Will that work with PLEX? Also, I'd like to try running a ZFS system. Is that also going to work with the server version, or do I need to use the desktop version?

Finally, I understand the server version can be run without a GUI, which would improve performance. I'd like to squeeze out every bit of horsepower I can from this thing, but I'm wondering if it's possible to install a GUI as an option. In my head, it's the kind of thing I'd turn on/off with a command line function so it's available if I wanted to manage the server directly, but doesn't run otherwise. Is that a possibility or am I imagining things?

Thanks in advance.

---

### Post by grahammechanical on 2016-03-25
You do not mention the video adapter. If that uses shared RAM for video memory or it only has a small amount of its own video memory and it cannot do hardware accelerated 3D rendering then that removes desktop environments that require hardware accelerated 3D rendering off the list.

Do you want a sever OS or a desktop OS? Are you going to use the machine to run server type programs? Then install the server edition. We can access a Linux command line from a desktop edition of Linux. Also, all desktop Linux distributions come with a GUI terminal application of one sort or another.

Server applications are not part of the default set of applications that come with desktop Linux but they can be installed. Server editions & desktop editions of Ubuntu use the same software repositories.

Yes, we can install a desktop environment and user interface on a server edition but then we come up against the question of the video adapter being capable of running the desktop environment.

Being a desktop user and not a server user I cannot tell you if a desktop environment is something that can be switched off & on, as you put it.

Regards.

---

### Post by john532 on 2016-03-25
CPUID tells me I've got an ATI Rage XL/XC with 8 MB of RAM, but it's unclear if that's shared or not. Either way it's going to be pretty small, so I'm guessing any accelerated 3D stuff is out. I'm leaning towards a server OS, since I'm going more for media server kind of stuff. If the server and desktop editions of Ubuntu both use the same repositories, I guess that there's not a lot of reason to go with desktop version of the software.

Is there a specific version number of the OS that would be best? I understand the LTS version has longer term support, but wasn't sure if the newer version would be worth the trade off.

---

### Post by pfeiffep on 2016-03-25
The newest and greatest will be released in April - 16.04 and is LTS. [Beta 2 ]("http://releases.ubuntu.com/16.04/")available for testing now

---

### Post by Bashing-om on 2016-03-25
john532; Hello;

Desktop:
Consider Lubuntu:
Lubuntu is a faster, more lightweight and energy saving variant of Ubuntu using LXDE, the Lightweight X11 Desktop Environment. It is targeted at "normal" PC and laptop users running on low-spec hardware.
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

[INDENT][INDENT]welcome to our world
[/INDENT][/INDENT]

---

### Post by Geoffrey_Arndt on 2016-03-25
If you can add at least another GiB ram, then that opens up Xubuntu as another alternative for a desktop gui.    If not at all familiar with Linux server admin or the bash-shell, it might be a lot easier to run with a gui.    Plex, Kodi and others are supported.

---

### Post by coldraven on 2016-03-25
Hi and welcome! I won't advise you on what's best but you can get all versions, desktop, server 32 and 64 bit here: [http://releases.ubuntu.com/](http://releases.ubuntu.com/)
If you choose one and then scroll down the page to see download options (torrent etc.) and checksums.

---

### Post by mörgæs on 2016-03-26
> **john532 said:**
> I've got an ATI Rage XL/XC

Then I recommend a standard server install without GUI.

---

### Post by john532 on 2016-03-28
> **Geoffrey_Arndt said:**
> If you can add at least another GiB ram, then that opens up Xubuntu as another alternative for a desktop gui.    If not at all familiar with Linux server admin or the bash-shell, it might be a lot easier to run with a gui.    Plex, Kodi and others are supported.

I'm kind of leaning in this direction, just because I have near-zero experience with Linux admin. Obviously I'm going to have to learn some command line stuff, but having a bit of a gui will help I think. I'm not looking for any kind of fancy effects or pretty graphics, just something basic. Is Xubuntu pretty lightweight? I'm hoping whatever I end up with is going to have minimal performance impact.

---

### Post by mastablasta on 2016-03-29
Xubuntu is in the range of XP regarding system resoruces usage. maybe slightly less if you install xfce4 core. 

however if you only need some sort of GUi try only a window manager such as IceWM ore Jwm. they look like win98.

---

### Post by retr02 on 2016-03-29
Ubuntu Server would seem like a good idea. Although you could run something light weight like LXDE or XFCE

---

### Post by him610 on 2016-03-29
I used to have one of these...
> ATI Rage XL/XC with 8 MB of RAM back in 2001, pre-WinXP if I remember correctly. The 8MB was on the VGA card. I had it installed on my experimental  learning system along with a 6 GB SCSI drive. Learned a lot about SCSI drives and termination on that system.

---

