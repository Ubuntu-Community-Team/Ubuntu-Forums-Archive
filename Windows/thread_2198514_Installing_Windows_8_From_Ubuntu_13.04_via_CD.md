---
title: "Installing Windows 8 From Ubuntu 13.04 via CD"
date: 2014-01-09
forum: Windows
---

### Post by jsingleton12321 on 2014-01-09
Dear, Forums
 About 4-5 days ago I decided to install Ubuntu 13.04. (Not quite sure why taking into consideration that I'm a gamer). I would like to reinstall Windows 8, but I have no idea how to. I have a disk containing the packages extracted from the Windows 8 .iso (Legit download, with legit key [http://windows.microsoft.com/en-us/windows-8/upgrade-product-key-only](http://windows.microsoft.com/en-us/windows-8/upgrade-product-key-only) ). I am so lost in this new operating system. Please help if you can! :confused:

---

### Post by Bucky Ball on 2014-01-09
Boot from the Win8 CD and install it?

Or are you asking how to make a bootable Win8 ISO using the extracted packages?

I'm not a gamer but I hear more and more games are being ported to Linux. Perhaps not the games you play, though.

---

### Post by jsingleton12321 on 2014-01-09
I'm asking how to make a bootable win8 iso using the packages

---

### Post by Bucky Ball on 2014-01-09
From the link you provided

*You'll have the option to install Windows now, later, **_or using media with an ISO file._***

If you have the product key can't you get on a Windows box and download the .exe file offered and then choose the 'download ISO file for later' option? I don't see any options there to download extracted packages. Does this option appear when you run their .exe file on a Windows box or did you extract them yourself? If so, from what? The original ISO you downloaded??? :-k

---

### Post by jsingleton12321 on 2014-01-09
I did download the .iso to my linux machine and wrote it to a disk and when I wrote it, I was given options like "write file" or "write packages contained in file" and these were the packages contained in the ISO [URL="http://postimg.org/image/aekd0rw37/"]
*but wine will not run setup.exe
[/URL]

---

### Post by Bucky Ball on 2014-01-09
You're supposed to boot from the disk you burned the Windows ISO to. You don't boot that in Ubuntu (or Windows). That should be the Windows install, or recovery, disk.

You need to get into the BIOS of your machine at at boot (some machine F12 gives you the option of which device to boot) and boot from the DVD.

How did you burn the DVD?

---

### Post by jsingleton12321 on 2014-01-09
I used the default linux write to disc option whenever I right clicked my .iso. And I was thinking that the BIOS button was F12, Thank you so much!

---

### Post by jsingleton12321 on 2014-01-09
Also wondering, what can I use Ubuntu for? I like playing games on my newer computer but I was thinking about dual booting on my previous machine.

---

### Post by Bucky Ball on 2014-01-09
> **jsingleton12321 said:**
> Also wondering, what can I use Ubuntu for? I like playing games on my newer computer but I was thinking about dual booting on my previous machine.

I would copy and paste this into a new thread and post it with a descriptive thread title in [***Ubuntu, Linux and Other OS***](***Ubuntu, Linux and Other OS***) as it is off-topic to this thread title. You will get more input specific to the question that way.

Post a link to that thread here and I'll have a look.  ;)

---

### Post by Bucky Ball on 2014-01-09
PS: Have a look here:

[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin#.Us6zdfiEtAQ](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin#.Us6zdfiEtAQ)

Go for 12.04 LTS (very stable and long-term support release supported until April 2017) or 13.10 as both will upgrade directly to 14.04 LTS when it is released next April. 13.04 won't (you would need to upgrade to 13.10 then 14.04 LTS or do a clean install). Being an LTS release, that also has five years support. (Non-LTS releases now have nine months.)

---

### Post by oldfred on 2014-01-09
Just extracting an ISO whether Linux or Windows to a DVD or flash does not create a bootable drive. 
You have to use tools that also add a boot loader and make it bootable.

---

### Post by jsingleton12321 on 2014-01-12
Sorry I forgot to reply but, I got a bootable disk and booted Windows 8, and whenever I was given the option to which drive to put Windows 8 on, I couldn't use any of the partitions because the weren't formatted to NTSF. I went into Gparted but, obviously I couldn't edit the partition because it was in use...

---

### Post by jsingleton12321 on 2014-01-12
Alright fixed it! Here's a step by step
1. First thing you do is download the Windows 8 installer from the Microsoft website and install the ISO.
2. Now you grab the Windows 7 USB/DVD Download Tool.
3. Burn the .iso's packages onto the disk, therefore creating it as a bootable drive.
4. If you legally own Windows 8/8.1 with a product key, then keep reading, otherwise GG.
5. Now you open up notepad or some sort of text editor on the computer with the CD in it and enter this with your Windows 8 product key replacing the X's.
```
[PID]
Value=XXXXX-XXXXX-XXXXX-XXXXX-XXXXX
```
5.5. Save as PID.txt
6. Boot the disc from your desired installation computer's BIOS using either F2, F10, or F12.
7. Now all you have to do is go ahead and install Windows 8.
(Remember Different solutions to even the slightest bit of difference in the circumstance)

---

