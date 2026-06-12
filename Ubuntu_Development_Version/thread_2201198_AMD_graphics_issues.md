---
title: "AMD graphics issues"
date: 2014-01-23
forum: Ubuntu Development Version
---

### Post by bc.haynes on 2014-01-23
I have burned 4 different copies of 13.10 to DVDs and, when I run the live DVD, to try it, I get gibberish on the bottom half of my screen (black on top half). These copies were downloaded and burned at different times either in Windows 7 or in Ubuntu 12.04. The gibberish has occurred all four times. The last time, I downloaded the .iso, double-checked the md5sum, burned it with K3B to a Memorex DVD+R, and had K3B verify the write. It was okay, but I still get broken patterns on the bottom half of my screen. What am I doing wrong?  :confused:

---

### Post by dargaud2 on 2014-01-23
It's more likely a graphic card problem. What kind is it ? Try using the nomodeset (or other) boot option (I don't remember the correct procedure, not having had to do a fresh install in a long time).

---

### Post by coldraven on 2014-01-23
try Googling "<your video card>  13.10", and also "nomodeset 13.10".

---

### Post by mörgæs on 2014-01-23
Nomodeset is a classic solution to Nvidia problems, but seldom to other cards. Please wait with the advice before we know the card in question.

---

### Post by bc.haynes on 2014-01-23
Is there a Terminal command that will tell me what kind of video card I have? The machine is a Lenovo M78-5100 desktop.
EDIT: Also, How would I use* **nomodeset*** if I am just booting the live DVD to try 13.10?

---

### Post by coldcritter64 on 2014-01-23
> **bc.haynes said:**
> Is there a Terminal command that will tell me what kind of video card I have? The machine is a Lenovo M78-5100 desktop.
....

Try,
```
lspci | grep VGA
``` it should list your make and model of card. edit: removed sudo from the command, as unnecessary.

eg result from this machine,
> 01:00.0 VGA compatible controller: NVIDIA Corporation GT215 [GeForce GT 240] (rev a2)

---

### Post by bc.haynes on 2014-01-23
The output from** lspci** is :
ben@ben-ThinkCentre-M78:~$ lspci | grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Trinity [Radeon HD 7540D]
What do I do now?

---

### Post by bc.haynes on 2014-01-23
It's a bug in 13.10. I installed** fglrx**, as was done in the bug report, but when I ran the live DVD,  I got a full screen of gibberish instead of a half screen. EDIT: I did not understand a lot of what was in the bug report, and I may have missed something. I googled "ATI Trinity [Radeon HD 7540D] 13.10" to get the bug report.

---

### Post by mörgæs on 2014-01-23
Please link to the report. It will help others with the same problem.

---

### Post by bc.haynes on 2014-01-23
The bug report is at:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1262377](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1262377)

---

### Post by mörgæs on 2014-01-23
At least there is reason to believe that it's fixed in 14.04.
If you are ready for a little experimenting you could try this one.

---

### Post by bc.haynes on 2014-01-24
I tried the daily build for 01/23/14, and it is still not fixed in 14.04-Trusty Tahr. I am running 13.04 now, and that expires in a few days. I need for 13.10 or14.04 to work with my video card (ATI Trinity [Radeon HD 7540D]). If anyone has a solution to this, please PM me and post the solution.

---

### Post by mörgæs on 2014-01-24
No, please don't use PM for anything of value. 
We prefer to have advice in the open for everyone to benefit.

The report in Launchpad seemed to indicate that the problem was solved, but if that's not so I think the best you can do is to discuss the problem in the [development forum]("http://ubuntuforums.org/forumdisplay.php?f=427").

---

### Post by bc.haynes on 2014-01-24
The last time I posted a problem on two forums, I was chastized for double-posting. Is that not the case here?

---

### Post by BlinkinCat on 2014-01-24
> **bc.haynes said:**
> The last time I posted a problem on two forums, I was chastized for double-posting. Is that not the case here?

Hi,

I believe it would be in order to ask a Mod to move the thread to a more appropriate Forum via the "Report Post" button.

I hope that helps!

---

### Post by Elfy on 2014-01-24
*Thread moved to **Ubuntu +1**.*

title edited a bit too

---

### Post by bc.haynes on 2014-01-24
I have since tried Edubuntu 13.10, Lubuntu 13.10, and Ubuntu 14.04 (Daily Build 1/23/14), and I have the same problem with them. Please, somebody fix this, I don't want to deal with Windows any more.
The problem is this:
[quote=bc.haynes]00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Trinity [Radeon HD 7540D][/quote]
When I run the live DVD of any of these distros, I get gibberish for the opening screen (splash screen is okay).

---

### Post by zika on 2014-01-24
Try not using **nomodeset** and try forcing dpm (use **radeon.dpm=1)** in kernel-boot-line...

---

### Post by bc.haynes on 2014-01-24
Is *kernel-boot-line* a text file? Where is it located?
EDIT: I used the **find** command and was unable to find a file named *kernel-boot-line* (but I may have the wrong syntax for **find**).
EDIT2: I tried the **whereis** command and it did not find* kernel-boot-line*.

---

### Post by zika on 2014-01-24
> **bc.haynes said:**
> Is *kernel-boot-line* a text file? Where is it located?
EDIT: I used the **find** command and was unable to find a file named *kernel-boot-line* (but I may have the wrong syntax for **find**).
EDIT2: I tried the **whereis** command and it did not find* kernel-boot-line*.I meant in the kernel line on boot...
It could be used in many ways depending on if You're booting from Live-USB/DVD/CD or using Grub...
I.e. in a line such as:```
linux   /boot/vmlinuz-3.13.0-031300-generic root=UUID=*some_numbers_depending_on_disk* ro radeon.dpm=1
```or using option in Live media on boot...

---

### Post by bc.haynes on 2014-01-24
How do you get to options when booting a live DVD?

---

### Post by xc3RnbFO8P on 2014-01-24
F6 >ESC
[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

---

### Post by bc.haynes on 2014-01-24
I did as zika suggested and added **radeon.dpm=1** to the boot-line. I no longer have a patchwork color screen; I have a blank, white screen. I want to thank **zika** for the suggestion, and **Ringi** for showing me how to do it. sorry, guys, it didn't work.

---

### Post by ventrical on 2014-01-24
Works excellently on this card in both Lubuntu and Ubuntu Live sessions.

[CODE]
ubuntu@ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]
ubuntu@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Trusty Tahr (development branch)
Release:    14.04
Codename:    trusty
ubuntu@ubuntu:~$ 
[CODE]

and i didn't have to tweak anything or use nomodeset.

 Now I'll build a live persistive and try fglrx. There is a problem with newer AMD cards if you are using an exisiting install from another drive or using  previous install and then installing a new  AMD graphics card. Simply, it will not work in most cases.. at least from what I have seen so far.

---

### Post by bc.haynes on 2014-01-24
My graphics card was not mentioned in "Supported Cards" on Ubuntu Community Docs here:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

It is in a six-month old Lenovo-M78-5100 that is a business machine, and I don't know if it has 3D acceleration. I was going to put a low-profile NVidia card in it until I checked the PS (240 Watts).This machine came with Win 7 Pro on it that I have wiped. I really do not want to go back to Windows again. I was trying to use Ubuntu Dapper Duck years ago and was too lazy to stick with it. This time I'm here to stay. I cannot afford to build or buy another machine with a compatible video card, So, tell me what to do next, and I will give it my best shot.

This is my card:    00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Trinity [Radeon HD 7540D]

Any more suggestions?

[COLOR=purple] ventrical[/COLOR] I am not sure what you wanted me to do. I have not followed your suggestion.

---

### Post by bc.haynes on 2014-01-24
I went back through the posts in this thread and came across something I had not tried (post #2).

[QUOTE=dargaud2]It's more likely a graphic card problem. What kind is it ? Try using the  nomodeset (or other) boot option (I don't remember the correct  procedure, not having had to do a fresh install in a long time).[/QUOTE]

I had not tried that because I did not know what to do. Well, I tried it and it worked. I ran Live-DVDs for Ubuntu 13.10, Lubuntu 13.10, Edubuntu 13.10, and Ubuntu 14.04 Daily (1/23/14). They all worked with **nomodeset** on the boot line. 

Once I have installed one of the distros (14.04), how do I put **nomodeset** into the installed software so that it will boot?

---

### Post by coldcritter64 on 2014-01-24
> how do I put **nomodeset** into the installed software so that it will boot?         In any install that needs it edit the file /etc/default/grub.
```
gksu gedit /etc/default/grub
```
and alter the line
> GRUB_CMDLINE_LINUX_DEFAULT=""
To look like
> GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"After updating grub
```
sudo update-grub
```the nomodeset setting will be added to all kernel entries in /boot/grub/grub.cfg (DO NOT edit grub.cfg directly)

---

### Post by bc.haynes on 2014-01-25
Thank you coldcritter64, as usual, your posts are clear and concise. I appreciate your help. (Along with all those who contributed to this thread.

---

