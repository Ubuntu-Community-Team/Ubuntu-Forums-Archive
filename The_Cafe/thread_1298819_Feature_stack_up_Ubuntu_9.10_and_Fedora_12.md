---
title: "Feature stack up Ubuntu 9.10 and Fedora 12"
date: 2009-10-23
forum: The Cafe
---

### Post by maflynn on 2009-10-23
Since fedora 12 is now in beta and we have the beta (actually the RC) of Ubuntu 9.10  It seems like a good idea to see what features both have.

From reading the [ars]("http://arstechnica.com/open-source/reviews/2009/10/ars-takes-a-first-look-under-the-hood-of-fedora-12.ars")  article regarding fedora 12 they're updating the memory management, KVM, power consumption tuning and compiled all of the 32bit code with i686 for netbook compatibility

I'm a little hazy on what changes 9.10 bring to the table, so if others could chime in I'd appreciate that.
I know Canonical wants to decrease boot time, and is looking to replace HAL with DeviceKit and the ubiquitous kernel update and a closer tie-in to ubuntu1

I've been playing with fedora 11 and there certainly things/areas I like about it. It was a royal pain to get the nvidia drivers installed - took me a weekend to figure out the proper steps.  Googling produced instructions but many of them failed to work.  It also took about a day to configure my cisco client.

In Ubuntu 9.04, I was able to do both within an hour.

---

### Post by vinutux on 2009-10-23
Debian family disrtos like ubuntu,use apt for installing and configuring......it is the finest tool compared to RPM/yum from fedora/redhat...........

---

### Post by maflynn on 2009-10-23
I'm not looking to discuss the   architectural differences between ubuntu and fedora but rather the features that have been added to 9.10 vs. f12

Looks like after doing some research, Fedora 12 is more major updates, where as 9.10 is a minor update with its focus on fast boot times.  

I'm asking to see what other features 9.10 has and how it stacks up against f12

---

### Post by surj08 on 2009-10-23
Ubuntu has been doing minor updates since its last long term release of 8.04. They seems to do a major update to one area at a time since that release. All the new features (some/most would even be noticed) are here [http://www.ubuntu.com/getubuntu/releasenotes/910overview#New%20features%20since%20Ubuntu%209.04](http://www.ubuntu.com/getubuntu/releasenotes/910overview#New%20features%20since%20Ubuntu%209.04) <<< Read them. if you don't know what something means google it. Its all pretty good stuff compared to the other linux distros. Ubuntu's focus is on easy of use, thats where most of their updates will go.

If you want a major update I would look to 10.04 as thats the next long term one.

---

### Post by Xbehave on 2009-10-23
[https://fedoraproject.org/wiki/Releases/12/FeatureList](https://fedoraproject.org/wiki/Releases/12/FeatureList) < a detailed list

A few that i think matter are:
networkmanager [full Ipv6 support]("https://fedoraproject.org/wiki/Features/NetworkManagerIPv6"), [improved mobile broadband]("https://fedoraproject.org/wiki/Features/MoreNetworkManagerMobileBroadband"), [Easier bridging]("https://fedoraproject.org/wiki/Features/Network_Interface_Management")
[improved support for multiple inputs]("https://fedoraproject.org/wiki/Features/XI2") (MPX is the biggest thing to note)
[webcam support]("https://fedoraproject.org/wiki/Features/BetterWebcamSupportF12") (HW dependant)
[display port for intel]("https://fedoraproject.org/wiki/Features/DisplayPort") (HW dependant)
[all]("https://fedoraproject.org/wiki/Features/KSM") [the]("https://fedoraproject.org/wiki/Features/KVM_Huge_Page_Backed_Memory") [kvm]("https://fedoraproject.org/wiki/Features/KVM_NIC_Hotplug") [stuff]("https://fedoraproject.org/wiki/Features/KVM_qcow2_Performance") [that]("https://fedoraproject.org/wiki/Features/KVM_Stable_Guest_ABI") [fedora 12]("https://fedoraproject.org/wiki/Features/libguestfs") [has]("https://fedoraproject.org/wiki/Features/VirtPrivileges")

Not much of that is particular exciting, ubuntu has more user facing changes
Grub2 support (Dear god why?) (but not that interesting, if you like uptime)
appArmor improvement for the desktop (security)
other security features (which are probably already in Fedora)
[software centre]("https://wiki.ubuntu.com/SoftwareCenter")
a slew of KDE improvements :D


I think the main rundown is pretty similar
ubuntu vs fedora 
kernel 2.6.31 v 2.6.31
xorg-server 1.6.4 v 1.7 (don't know about xorg versions, this adds mpx,etc)
kde 4.3.2 v 4.3 (.2 implied)
gnome 2.28 v 2.28

I think both will be good releases and while fedora is always slightly ahead of ubuntu in terms of upstream enhancements (e.g they get a better NM,etc) the main differences between them will as always be apparmor/selinux & apt/yum (although both are moving towards packagekit for interaction with this)

---

### Post by Merk42 on 2009-10-23
> **surj08 said:**
> If you want a major update I would look to 10.04 as thats the next long term one.

Isn't the exact opposite true? Aren't LTS releases focused on stabilizing and not introducing features?

---

### Post by samh785 on 2009-10-23
> **Merk42 said:**
> Isn't the exact opposite true? Aren't LTS releases focused on stabilizing and not introducing features?

That's what my interpretation of a LTS release was.

---

### Post by surj08 on 2009-10-23
Same here but 8.04 seemed to change ubuntu a lot from 7.10

---

### Post by froggyswamp on 2009-10-23
If one just wants to know about the new features one should just read the release notes, count the checkboxes and do simple math.
What matters most is end user experience, and Ubuntu here reigns supreme. On Fedora 12 beta I couldn't even get codecs to listen mp3s and watching avi video, clicking on mp3s produced a dialog that in the end didn't help. Googling resulted in suggestions that didn't work, no obvious way to install the nvidia driver (since nouveau is still raw and without 3d) and so on.
More check-boxes in the release notes doesn't necessarily mean better experience and I'm not trolling on Fedora, I'd like to drop Ubuntu and move to Fedora cause it decided to get rid of Mono, but it's still a frustrating experience for me just like the prev 2 version I tried: 10 & 11. I know it's in Beta, that doesn't change much.

---

### Post by kevin2849 on 2009-10-23
I have Fedora 12 installed on one of my laptops in the hope I can further my horizons a little, learning a different approach to the linux desktop. Since I use gnome on both Ubuntu and Fedora, I find the differences to be very minor.

Having used Ubuntu since the beginning, I have developed a preference for the apt package management but I am willing/wanting to learn rpm/yum. The command line is a more reliable way to manage packages in both distrobutions (my experience-so far) keeping in mind both are beta.

I installed from DVD and found that MONO was included in the F12 install so I am not sure what froggyswamp is refereing to.

Suspend is not working on the laptop, with Fedora 12, so I am sure I have some digging to do. It worked out of the box with Karmic. 

This is not a proper response to the OP but is my comparison so far between the two. The best might just be what we are used to.

---

### Post by Xbehave on 2009-10-23
> **surj08 said:**
> Same here but 8.04 seemed to change ubuntu a lot from 7.10
8.04 was weird because there were a lot of upstream changes around that time and canonical didn't want to be lumbered supporting old upstream for a whole LTS so crammed a lot in. 9.10 and 10.04 are IMO going to be fairly tame releases, upstream is not doing anything big for either of them. Perhaps there will be a flurry of activity around 10.10 (gnome3 by default), but other than btfs most users will only be noticing continuing improvement across core systems, especially if securing your desktop isn't particularly exciting. 

> **froggyswamp said:**
> What matters most is end user experience, and Ubuntu here reigns supreme. On Fedora 12 beta I couldn't even get codecs to listen mp3s and watching avi video, clicking on mp3s produced a dialog that in the end didn't help.
Can't we all get along? I had no trouble getting mp3 codecs working on fedora11, I just needed to enable the rpmfusion repository (much like you need mediabuntu in ubuntu (or did last time i used ubuntu anyway)).

> I'd like to drop Ubuntu and move to Fedora cause it decided to get rid of Mono
Switching distro over some optional software you can add/remove in either seams pretty silly, I mean there are lots of reasons to switch to fedora but that is not one of them. Anyway if you do want to switch  [fedora guide]("http://www.fedoraguide.info/index.php?title=Main_Page#RPM_Fusion") is very useful and while [fedora forums]("http://forums.fedoraforum.org/index.php") are not as active as UF they are useful too.

---

### Post by Mander on 2009-10-23
I have to say that I am tempted to switch to Fedora.  I've had some annoying problems since I upgraded to Jaunty, most of which I am just ignoring for the moment, that I didn't see when trying the live CD of Fedora 11.  The biggest persistent irritation is the funky black bars that appear at random.  Apparently this has something to do with Nvidia but I haven't found anything that works to make them go away.  I still haven't been able to fix the shut down problem, either (you have to hit a key after the screen shuts off, otherwise the computer doesn't shut down all the way).  But on the Fedora live CD neither of these happened.

The biggest thing for me was that the live CD had the correct screen resolution and the wireless card worked without any tweaking, installing drivers, or changing settings at all.  True, 3D didn't work, but I've had to turn it off on Jaunty anyway, because it was causing random freezes and crashes.

---

### Post by samjh on 2009-10-23
> **Merk42 said:**
> Isn't the exact opposite true? Aren't LTS releases focused on stabilizing and not introducing features?

LTS just means "Long Term Support".  It's not an extra-stable version of Ubuntu, if by stable, you mean reliable.

Canonical provides LTS versions with longer update support periods than normal versions, which makes them good for corporate servers (because businesses don't like upgrading server software too often).  That's all.

---

### Post by Xbehave on 2009-10-23
> **Mander said:**
> The biggest thing for me was that the live CD had the correct screen resolution and the wireless card worked without any tweaking, installing drivers, or changing settings at all.  True, 3D didn't work, but I've had to turn it off on Jaunty anyway, because it was causing random freezes and crashes.
F11 is pretty good, however it sounds like your problems came from using the nvidia closed drivers (vs [nouveau]("http://nouveau.freedesktop.org/wiki/") that are (probably) what's used on the liveCD):
1) I think nouveau should be available for ubuntu (even if only nv are installed by default)
2) I think installing the prop drivers on Fedora11 is harder because there is no drivers program like you get in ubuntu (although tbh its probably not that hard, but i have ATI so i don't know)
3) In particular both ubuntu 9.10 and Fedora 12 ship with the same xorg so short of bugs they should support your card the same (aslong as the same drivers are in use)

That's not to say you shouldn't try fedora its a great distro (more updates after release), just that it sounds like your problem isn't fedora vs ubuntu related.

---

### Post by AdamWill on 2009-10-24
A few misc. notes:

F12 has a later X server than Ubuntu 9.10 (and the rest of the distros in this round). Most distros, including Ubuntu, decided to stay with X server 1.6. F12 has 1.7, because we're crazy that way. ;) In most cases this won't really be that noticeable for users, though.

Most of the NetworkManager improvements listed on the F12 features have probably landed in Ubuntu too, I'd expect. U usually stays pretty up to date with NetworkManager updates.

For proprietary drivers, patent-encumbered codecs and so on for Fedora, go to RPM Fusion - [http://www.rpmfusion.org/](http://www.rpmfusion.org/) . That's where all that stuff is. Installing codecs and drivers from RPM Fusion on pre-releases of Fedora doesn't always work - NVIDIA driver won't work without tweaking on F12 Beta due to debugging code in the kernel still being enabled - but for final releases it's usually pretty smooth.

---

### Post by Mander on 2009-10-27
> **Xbehave said:**
> F11 is pretty good, however it sounds like your problems came from using the nvidia closed drivers (vs [nouveau]("http://nouveau.freedesktop.org/wiki/") that are (probably) what's used on the liveCD):
1) I think nouveau should be available for ubuntu (even if only nv are installed by default)

That's not to say you shouldn't try fedora its a great distro (more updates after release), just that it sounds like your problem isn't fedora vs ubuntu related.

I was wondering if my problems (also have the problem with apallingly slow SATA and USB read/write times) might have something to do with the difference between kernel versions.  Now, I am pretty much still a newbie so I'm probably talking nonsense, but in [this thread]("http://www.uluga.ubuntuforums.org/showthread.php?t=1150108&page=11") about the SATA problems, several people had good results from installing the mainline kernel instead of the normal Ubuntu version.  I'll try that before I reinstall, of course.

I've tried all the drivers I can think of: nv, nouveau, installing via Envy, installing with the Ubuntu Hardware Drivers dialog, and manually downloading and installing the proprietary driver from the Nvidia website, and trying various experimental and svn builds (is that the right term?).  I get the same wierd artifacts no matter which one I try.  I got tired of messing around with it so I'm just ignoring it for the time being.  I do have a probably-unfounded suspicion that it has to do with 64 bit vs 32 bit.  The Fedora CD I tried was 32 bit.

I still haven't figured out the shutdown/suspend problem. Seems like I've tried a zillion different tweaks but none of them seem to work.

---

