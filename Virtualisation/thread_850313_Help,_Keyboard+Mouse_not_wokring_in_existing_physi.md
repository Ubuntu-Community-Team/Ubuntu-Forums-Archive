---
title: "Help, Keyboard+Mouse not wokring in existing physical install (Host:Lin,Guest:Win)"
date: 2008-07-05
forum: Virtualisation
---

### Post by daniel_iversen on 2008-07-05
Hi there.

I really hope you can help me, I've googled and read everything it seems on Ubuntu, VirtualBox and other forums (and blogs) with no result.

I am booting my pre-existing Windows install from VirtualBox OSE 1.5.6 running on Ubuntu Linux 8.04 and both the keyboard and mouse does not work.

This is on a laptop (Dell XPS m1330).

To get the Windows install to boot in the first place I had to change the disk drivers to standard IDE etc. as is mentioned elswhere on this forum and also I had to (or at least thought it would be clearner) to create seperate hardware profiles).

I've tried the following to get the keyb+mouse working;
installed the Addition/Addon Utilities that comes with VirtualBox.
Used both the commercial/closed source version of VirtualBox (1.6.x) as well as the OSE version
I've not got the “Enable support to enter complex characters” enabled (I use Australian settings anyway)
I've done all sorts of USB black magic tricks as discussed in various forums, such as changing permissions on files, adding my user to different groups, enabling bits in init.d scripts and starting VirtualBox as root
I've enabled “VT-x/AMD-V” settings
I've disabled the “Auto capture keyboard” setting
I DO have Compiz Fusion enabled though (but even my keyboard does not work)

Now here is the weird bit...;

 If I install Windows on a new virtual disk from the same Windows installation CD, it works! Now that leads me to conclude that it must be something with not my host/Linux/VirtualBox, but rather the physical Windows installation that I am booting. My suspicion is around drivers, but for godness sake a keyboard and a mouse has never been a problem I've ever seem (there are always standard minimim drivers for these right?).. I think this could have something to do with the fact that this is a laptop...?

Any help would be appreciated (even just bullet points of what to check). This drives me crazy and precents me from using Linux everyday since I need some Windows-only apps that are perfectly installed on my physical installation.

Thanks a lot in advance for any help.. I hope to hear from someone with some good ideas ;)

Cheers,
Daniel

PS: I will try and post this in the VirtualBox Forum as well in case they have any ideas (but tell them it is posted here as well). Please don't let that stop you from actually answering this post. I will make sure answers from the VirtualBox forum are pasted here and we all share the learnings.

---

### Post by prshah on 2008-07-05
> **daniel_iversen said:**
> 
I am booting my pre-existing Windows install from VirtualBox OSE 1.5.6 running on Ubuntu Linux 8.04 and both the keyboard and mouse does not work.


Just a suggestion; don't know how valid it is; have you tried disabling the "mouse integration" feature in the guest OS?

---

