---
title: "Big problems with booting into a dual boot system."
date: 2023-02-18
forum: Ubuntu/Debian BASED
---

### Post by mag-linares on 2023-02-18
I have a 2016 Toshiba laptop running Windows 10 and I've tried to dual-boot it with the LXLE distro, but I'm having a huge boot problem. 

I boot it in CSM Mode, not UEFI, because the distro did not allow UEFI mode.  

In grub I choose to boot LXLE and all that OS works perfect. But I choose Windows and it gives me an error:  

Windows failed to start. A recent hardware or software change might be the cause. file: \boot\bcd The boot configuration data for your pc is missing or contains errors.  

And after that it restarts.  So I go into LXLE to repair using boot-repair and after doing its scans it tells me: 

WindowsEFI detected. Disable Compatibility BIOS / CSM / Legacy mode in your UEFI firmware and use this program from a live CD (or a live USB) that supports UEFI boot mode. For example, use a live-USB from Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")), after making sure your BIOS is set to boot via USB in EFI mode.  

But, if I disable CSM mode to go back to UEFI, Grub won't load. what do i do then?  

My current situation is that in order to enter Windows, I have to enter BIOS and select UEFI mode, and in order to enter LXLE, I have to enter BIOS and select CSM mode. A rather considerable nuisance. 

I appreciate any guidance.

---

### Post by TheFu on 2023-02-18
So, Win10 is probably installed in UEFI boot mode, so if you have to swap between them, you'll need to swap your BIOS boot settings each time. There's no workaround.  OTOH, LXLE isn't an official Ubuntu distro. Have you considered LXQt as put out by the Lubuntu distro? It boots from UEFI.

I haven't dual booted in over a decade. When I need to run Windows, it is inside a virtual machine. No more issues like this.

---

### Post by oldfred on 2023-02-18
Moved to Other OS since not Ubuntu.

You need your Linux install in UEFI boot mode. Do not mix CSM/Legacy/BIOS with UEFI on same drive. And best to all in same boot mode even if multiple drives.

Almost all systems are UEFI and distributions are also. Check your distribution and tool used to make installer. Both should be for UEFI install.

---

### Post by mag-linares on 2023-02-19
Hello.

Thanks for your considerations.

I liked the LXLE distribution because I had a 2012 HP laptop with Windows 7 that, in 2018, suffered to boot this operating system, taking about 30 minutes to do so. I opted to install Ubuntu on it and it was revived, but only for two years. In 2020 it became just as slow as the previous Windows. So I formatted the computer and installed Lubuntu on it. It came back to life... but only 2 years... it's super slow again and I'll have to install the LXLE distribution when I have some time.

Then a friend gave me an old Acer laptop from 2005! that already started his windows in more than half an hour, and I thought that Lubuntu would not work for him, so I investigated and found that LXLE. I formatted it directly and with LXLE I have that archaic Acer running there, with almost 20 years behind it.

Now I have this Toshiba Satellite Pro from 2015 that can no longer handle its mammoth Windows 10 but I still don't want to delete it because it works for some applications that have no equivalent in Linux, such as the latest Photoshop and all the graphic design applications from the company TopazLabs . I discarded Ubuntu and Lubuntu so as not to have to delete it in a couple of years, that is, if the route is going to be Lubuntu --> LXLE, I considered it a good idea to go forward now, opting directly for a dual boot with LXLE, but I see which, according to your comment, was a bad decision because of the "UEFI" issue.

So I'll leave LXLE for the future, when that operating system is going to be the sole owner of that Toshiba, and I'll try a dual boot with Lubuntu which, as you say, supports UEFI boot.

Thank you so much.

---

### Post by oldfred on 2023-02-19
This says LXLE is Lubuntu with some addions.
[https://www.quora.com/Is-there-a-significant-difference-between-LXLE-and-Lubuntu-Linux-distributions](https://www.quora.com/Is-there-a-significant-difference-between-LXLE-and-Lubuntu-Linux-distributions)

And it looks like LXLE is UEFI.
So it may depend on how you make or boot the live installer.

---

### Post by mag-linares on 2023-02-19
Hello friends.


As this problem did not seem to have a solution, I have chosen to install Lubuntu on the problematic LXLE partition.


The installation process went amazingly well, but unfortunately once inside the Lubuntu system I ran into another problem that I posted here:

[https://ubuntuforums.org/showthread.php?t=2484181&p=14131657#post14131657](https://ubuntuforums.org/showthread.php?t=2484181&p=14131657#post14131657)

---

