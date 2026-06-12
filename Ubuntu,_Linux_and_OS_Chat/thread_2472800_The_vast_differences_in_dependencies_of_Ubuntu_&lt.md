---
title: "The vast differences in dependencies of Ubuntu &lt;&gt; Debian. Why?"
date: 2022-03-13
forum: Ubuntu, Linux and OS Chat
---

### Post by Tadaen_Sylvermane on 2022-03-13
I've always flipflopped between Debian and Ubuntu. I don't know why. That being said where or why does Ubuntu modify the dependencies of packages so severely. 

I just now was doing a chroot install of Ubuntu Focal x64 on my desktop from my current logged in Debian. This was my line that caught my eye.

```
# apt install linux-image-generic lvm2 os-prober grub2 gamemode xorg

....

0 upgraded, 725 newly installed, 0 to remove and 0 not upgraded.
```

It just struck me so I did a quick test and made another chroot of debian.

```
# apt install linux-image-amd64 firmware-linux-nonfree lvm2 os-prober grub2 gamemode xorg

....

0 upgraded, 212 newly installed, 0 to remove and 0 not upgraded.
```

Ubuntu with relatively the same packages requires 3 times the disk space,  and over 3 times the  packages? I'm looking at the package list on Ubuntu. It's installing a ton of Gnome stuff + whatever comes with it.

I just ran the same command on Ubuntu with the --no-install-recommends and it cut the list down to 231 packages, but it doesn't even include the individual xorg packages for graphics... 

I just don't get why it's so bloated compared to Debian. People say they don't like bloat.... this is bloat at it's finest.

---

### Post by grahammechanical on 2022-03-13
> I'm looking at the package list on Ubuntu. It's installing a ton of Gnome stuff + whatever comes with it. 

Does that statement mean that you are not using the Gnome 3 desktop environment on Debian?

Regards

---

### Post by TheFu on 2022-03-13
> **Tadaen_Sylvermane said:**
>  
I just don't get why it's so bloated compared to Debian. People say they don't like bloat.... this is bloat at it's finest.

100% agree.  I still remember when bluetooth was added as a KVM dependency.  What?  Since when would any virtual machine use bluetooth anything ... er ... ever? I never want any BT stuff on any of my systems. After being hacked over BT, I go out of my way to disable the module and remove the programs at every boot. Seems I cannot trust that once removed, it will stay removed.  It keeps coming back, like a zombie that isn't decapitated properly. ;)

I have the same issue with btrfs.  Don't want it. Don't needed it. Will never, ever use it on 99% of my installs.  But it is installed on all of them.

Canonical is weighing the convenience of a package vs not having it.
Heck, even their "minimal install" has a full web browser. I pointed this out and suggested lynx, which was shot down.  OTOH, they did remove the other stuff I pointed out as unnecessary.

A server install can be less than 50MB.  Canoncial server install can be less than 600MB, but I think the default is around 1.8G once all the 'convenience' packages are added.

When I want minimal X/client libraries on a system, I install just xterm. Not any Gnome stuff.  The Qt or GTK+ libraries add 750MB by themselves. Just look at the snap libraries for those.

What you and I call bloat, lots of people consider highly convenient or necessary.
Some things I'm willing to have bloat over include bash-completion and manpages. I bet lots (even most) users don't use either of those things.  Just a matter of perspective, I suppose.

---

### Post by Tadaen_Sylvermane on 2022-03-13
> **grahammechanical said:**
> Does that statement mean that you are not using the Gnome 3 desktop environment on Debian?

Regards

Been using xfce mainly on both. Was gonna try an openbox + tint2 when I realized it was dragging in all of gnome and made this thread. I find gnome (I think it's gdm specifically) a bit unstable. Random hangs and such especially when unlocking the screen. Stuff like that. Had these problems on both, more consistent on Ubuntu.

---

### Post by TheFu on 2022-03-13
I use lightdm and fvwm2.  No need for and DE.  fvwm2 isn't for everyone. The configuration is text only, but my same basic config has been working nearly 20 yrs - which could be seen as a major plus. Extensions tend to be created in perl, if you'd like to add GUI addons.
I used openbox for a few years and customized the rc.xml for that too, but it wasn't as powerful as fvwm2. Both are nice, light, WMs that behave as expected.  

fvmw2 can be customized for a TV-space show display look.  I suspect most displays on futuristic TV shows use FVMW.

---

### Post by breakdaze on 2022-03-14
Why? Because the technical board said so. [https://wiki.ubuntu.com/TechnicalBoard](https://wiki.ubuntu.com/TechnicalBoard)
They publish minutes (I didn't read).
Many stir the pot, never know what kinda soup you're gonna get. Also follow the money, the important decisions are based on what drives support revenue, and that's most likely Cloud Computing and servers, with the Desktop environment being lower on the priority list, I imagine. The free stuff we use is a good beta test environment for the stuff that sells support also. What are the top boxes here and what's at the bottom?

[https://ubuntu.com/advantage/subscribe](https://ubuntu.com/advantage/subscribe)
[https://ubuntu.com/pricing](https://ubuntu.com/pricing)

I definitely give Ubuntu and this community a lot of credit for exposing more people to Linux, which is a good thing, thus many volunteers, which is also good. But does everything make sense to everyone? Of course not.

Great question. I don't like bloat myself.

---

### Post by zebra2 on 2022-03-15
I use an out of the box Ubuntu Dev. Currently Jammy.  My experience so far with very few exceptions is "perfect".   The money says create a full service system and desktop that is robust and functional.  That is what I like and that is what I have. Of course I back it up with a terabyte hard drive and eight gig of ram. Everyone should know by now that the mainstream desktop users don't want or need a gutted OS run from a command prompt. 
What is being offered by Canonical right now is exactly what I need.  And don't forget all the bloat those snap apps require.  I started out years ago with a 40Mb hardcard.  Might need a 4 terebyte  before its over.

---

### Post by Tadaen_Sylvermane on 2022-03-15
> [COLOR=#000000]Everyone should know by now that the mainstream desktop users don't want or need a gutted OS run from a command prompt.

Fair enough. I didn't think about that. Well said.[/COLOR]

---

### Post by breakdaze on 2022-03-15
Absolutely, Ubuntu is mainstream, and that's great for the majority. Not great for those who can't afford to buy a lot of expensive PC hardware. Fortunately there are plenty of distros out there. I love how Ubuntu gets people into Linux, and is a great beginner (and advanced) Linux for people to easily use out of the box. They should fix the ubiquity and calamares bugs though. It's not super great to have buggy installers. However, it's free and open source, so who's complaining? Not me, certainly.

---

### Post by lammert-nijhof on 2022-03-16
I run Ubuntu 21.10 on a $349 PC, that I did build in Apr 2019. It has a  Ryzen 3 2200G; 16GB DDR4 (3000MHz) and a 512GB nvme-SSD (3400/2300MB/s).  I would not consider that a lot of expensive PC hardware. Ubuntu runs  fine. I run a lot of VMs and occasionally I run 2 modern Windows updates  (8.1 and 10) at the same time. I admit, in those case the CPU runs at  100%, but that's the $97 CPU not the bloat of Ubuntu. 
Before 2019 I  did use a 2008 HP dc5850 (Off-lease in 2014 $200) with an AMD Phenom II B97 (4C4T; 3.2GHz); 8GB  DDR2 (800MHz); a 128GB sata-SSD and 2 HDDs. I never had any complaints  about the bloat of Ubuntu. I admit, I could run only one modern Windows  VM, but mainly because Windows is bloated :) 
I don't understand the bloat issue, if you think the Gnome version uses too much memory for your PC, use e.g Xubuntu or Debian and be happy.

---

### Post by breakdaze on 2022-03-16
Bloat and inefficient code has been an issue for at least 30 years as storage and RAM got larger, and programmers were no longer forced to optimize as much.

When I took a discrete mathematics course, we went over writing an efficient algorithm, as well as the rules of logic. I don't know how many programmers have a computer science background like this, but if they do, they should provide guidance to those who don't.

We can save power, and help reduce global warming with more efficient code also. 

Yeah, I'm buying more RAM for my 2912 Acer that has only 2GB. $349 is a lot, I think I will buy food instead. Nice to hear some people have virtually unlimited disk space.

I appreciate your point of view, however. It's all a matter of perspective.

---

### Post by Tadaen_Sylvermane on 2022-03-17
> **lammert-nijhof said:**
> I run Ubuntu 21.10 on a $349 PC, that I did build in Apr 2019. It has a  Ryzen 3 2200G; 16GB DDR4 (3000MHz) and a 512GB nvme-SSD (3400/2300MB/s).  I would not consider that a lot of expensive PC hardware. Ubuntu runs  fine. I run a lot of VMs and occasionally I run 2 modern Windows updates  (8.1 and 10) at the same time. I admit, in those case the CPU runs at  100%, but that's the $97 CPU not the bloat of Ubuntu. 
Before 2019 I  did use a 2008 HP dc5850 (Off-lease in 2014 $200) with an AMD Phenom II B97 (4C4T; 3.2GHz); 8GB  DDR2 (800MHz); a 128GB sata-SSD and 2 HDDs. I never had any complaints  about the bloat of Ubuntu. I admit, I could run only one modern Windows  VM, but mainly because Windows is bloated :) 
I don't understand the bloat issue, if you think the Gnome version uses too much memory for your PC, use e.g Xubuntu or Debian and be happy.


It's not about using to much or a machine not being able to run it. It's just about why does claim it needs something that it doesn't actually need to run? My machine is more than capable of it and then some. Maybe in my mind it's some type of false sense of something . I don't know. To me it's like saying you can't play your Steam games without your printer attached.

---

