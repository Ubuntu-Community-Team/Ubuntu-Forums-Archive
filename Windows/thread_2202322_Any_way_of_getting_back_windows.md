---
title: "Any way of getting back windows?"
date: 2014-01-28
forum: Windows
---

### Post by jayfitz91 on 2014-01-28
So i was having trouble with windows and decided to give ubuntu a shot. When i loaded up the disc, it asked how i would like to install, so i chose to format everything on the C: drive and replace windows with ubuntu, this completely removed anything to do with windows from my PC.

I now need windows for college so i tried re-installing it, only when i put my installation disc in and boot into it, it loads the windows 8 symbol for about 2 minutes and then shows a blue screen with:

Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:
   1. Insert windows installation disc and restart your computer <<tried this>>
   2. Choose your language settings, the click "Next" <<Don't get this far>>
   3. Click "Repair your computer"

   File: \windows\system32\winload.exe

   status: 0xc000000e

   Info: The selected entry could not be loaded because the application is missing or corrupt

Thats the entirety of it, has anyone and understanding of what might fix this? I have a feeling its to do with the windows registry :confused:

Any help/response appreciated regardless

---

### Post by Bucky Ball on 2014-01-28
*Thread moved to **Other OS/Distro Support**.*

Is this a legal copy of Windows? If not it's possibly the issue.

Depending on what subject you're doing, being told by educational institutions that you 'need' Windows is often rubbish. Is there specific software you need to use that will only run in Windows? I've just finished seven years of uni and did 90% of it in Ubuntu. I have an old XP install for when I need to use Win for a couple of apps that there is just no alternative for in Ubuntu. 

Why don't you dual-boot? Shrink the Ubuntu partition, install Win in the free space you create, boot into Ubuntu, open a terminal and:

sudo update-grub

That should pick up Windows and you're set to go. You'll probably find you don't 'need' to use it much, if at all, once you get there, depending on what you are studying. 

Good luck with it. ;)

---

### Post by jayfitz91 on 2014-01-28
Yeah its the one i got with it so its definitely legal alright.

I actually prefer Ubuntu do most of my work lately, but we're using Web Matrix which is a Windows application only we're told :P

Yeah sure ill give that a go and see how i get on, thanks for the reply :)

---

### Post by Habitual on 2014-01-28
boot ubuntu CD and run gparted on the partition, then try the re-install of Windows?

---

### Post by zteam2 on 2014-01-28
Just as [**[COLOR=#000000]Habitual[/COLOR]**]("http://ubuntuforums.org/member.php?u=504341") says, just fire up Gparted and format the drive to NTFS before booting up from Windows, I'm pretty sure that should solve all your issues.

---

### Post by RadicaX on 2014-01-28
You could with a little work do as they say, but leave a bit of partition over for Ubuntu and the swap so you can have both. Ubuntu for most things, Windows for the crap you will never use in your life but will in university. Though to note, WebMatrix is open-source, odd to not find the code remade for a Linux.

---

### Post by Bucky Ball on 2014-01-29
WebMatrix is NOT open-source as such. It is a Microsoft product that works on WINDOWS, and is designed specifically for Windows, that works with open-source apps like Joomla and Wordpress.

---

### Post by Mark Phelps on 2014-01-29
> Yeah its the one i got with it so its definitely legal alright.

BY this , do you mean that the PC came with Windows pre-installed and this CD came with it?

In nearly all cases, CDs that are included with PC that come with Windows preinstalled are only able to boot the CD into a recovery mode -- from which a factory reset can be done using the Windows image file stored in a Recovery partition on the drive.  IF you erased that partition, and this is a recovery CD, then you have no Windows install media to use to restore it.

Also, Windows can't read Linux filesystems, so it's likely the Windows installer will not be able to reformat the drive in any way.

You need to use GParted to shrink the Linux filesystem to make room for Windows.

---

### Post by lykwydchykyn on 2014-01-29
If you have a friend or another machine with Windows 8.1, you can try this to create new installation media:

[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

### Post by hg-knight on 2014-01-29
could run windows in a virtual box [https://www.virtualbox.org/](https://www.virtualbox.org/)

---

### Post by RadicaX on 2014-01-29
> **Bucky Ball said:**
> WebMatrix is NOT open-source as such. It is a Microsoft product that works on WINDOWS, and is designed specifically for Windows, that works with open-source apps like Joomla and Wordpress.

That is odd. I thought I had read it was Open-source, but now I see, it just says it works great with Open-source. That is a pain, thanks for pointing that out.

---

