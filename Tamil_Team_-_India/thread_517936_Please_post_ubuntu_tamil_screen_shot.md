---
title: "Please post ubuntu tamil screen shot"
date: 2007-08-05
forum: Tamil Team - India
---

### Post by jeyaganesh on 2007-08-05
Hallo,
I would like to install ubuntu in tamil, currently I have some partioning problem in installing ubuntu. I asked for suggestions in 'General Help'. Before installing ubuntu in tamil, I would like to see some screen shot of tamil ubuntu. Could you please post your tamil ubuntu screen shots here? I will appreciate if you post the following screen shots;

1. Desktop with menu bar
2. Add or remove software window
3. Browser windows and other windows opened on screen
4. Any other shots you like to post

Thanks in advance

Jay:popcorn:

---

### Post by Taum on 2007-08-05
[This should help]("http://tinyurl.com/ywczhm").  May not help much, but I hope it helps at all.

---

### Post by jeyaganesh on 2007-08-05
hi I already did image search in google, I couldnt find any picture of ubuntu in tamil. Thats why I asked here.
Jay

---

### Post by amachu.techie on 2007-08-10
[http://ubuntuforums.org/showthread.php?t=408590](http://ubuntuforums.org/showthread.php?t=408590) 
 
[http://ubuntuforums.org/showthread.php?t=409311](http://ubuntuforums.org/showthread.php?t=409311) 
 
[http://ubuntuforums.org/showthread.php?t=409379](http://ubuntuforums.org/showthread.php?t=409379) 
 
[http://ubuntuforums.org/showthread.php?t=489009](http://ubuntuforums.org/showthread.php?t=489009)

---

### Post by sarutv on 2007-08-11
Ubuntu uses Gnome as the window manager and Kubuntu use KDE as the window manager. The screenshots my amachu is for Kubuntu. The following are the screenshots (click to see a large version) from my Ubuntu system:

This is the login screen:
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=40441&stc=1&thumb=1&d=1186868926[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=40441&d=1186868926")

Admin Menu with "Synaptic Package Manager" highlighted. This program allows you to add or remove programs from your computer.
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=40442&d=1186869017&stc=1&thumb=1[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=40442&d=1186868926")

When ever you run programs that can change your system, you would need to type in your password again. This is so that malicious programs cannot modify your system without your knowledge. 
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=40443&d=1186869017&stc=1&thumb=1[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=40443&d=1186868926")

Once you enter the password and grant access "Synaptic Package Manager" opens. Here you can search and install the programs, libraries and other packages you need.
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=40444&d=1186869017&stc=1&thumb=1[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=40444&d=1186868926")

This is the screenshot of a firefox browser showing a tamil webpage. On the background are other apps.
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=40445&d=1186869017&stc=1&thumb=1[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=40445&d=1186868926")

---

### Post by ashvala on 2007-08-12
You arn't supposed to post screenschots in the month of august

---

### Post by jeyaganesh on 2007-08-13
Hallo, Thank you very much for screenshots. I have a problem in installing Ubuntu on my Dell PC (Vista, 20" monitor, Intel integrated graphic card and intel VII V, two cores). Whenever I try to install it says following error during manual partition;

 'Files system doesnt have expected sizes for Windows to like it. Cluster size is 2K (1K expected); number of clusters is 20017 (39957 expected); size of FATs is 79 sectors (157 expected)'. 

Could anyone tell me what should I do next? If I ignore and continue the installation, system freeze at 'log-on' screen. Please give me some idea to install Ubuntu.

Thanks in advance,
Jay

---

### Post by sarutv on 2007-08-25
> **jeyaganesh said:**
> 
....
 'Files system doesnt have expected sizes for Windows to like it. Cluster size is 2K (1K expected); number of clusters is 20017 (39957 expected); size of FATs is 79 sectors (157 expected)'. 

Are you sure the Ubuntu installer gives this error? This sounds like an error caused by windows. In any case could you give us the exact error messages as they appear on screen (photos if you have a camera).
> **jeyaganesh said:**
> 
....
Could anyone tell me what should I do next? If I ignore and continue the installation, system freeze at 'log-on' screen.

System freeze's on Ubuntu log-on screen or vista's log-on screen? 

I am not an expert but I heard that Vista supports multiple OSs on a PC. So I just want to make sure that you are using grub (the bootloader that came with Linux) or did you use Vista's bootloader? 

Lastly did you try running Ubuntu from a Live CD? If you haven't may be you should try and find out if there are any unsupported hardwares.

---

### Post by jeyaganesh on 2007-08-26
Hi thanks for your reply. The exact error message I got was given in my previous reply to this thread. I think it may be due to the screen resolution. I have wide screen monitor (1680x1050) and ubuntu gives only 1280x1024 resolution. Do you have any idea to solve this problem. I think before installing this, Gusty Gibbon will release. :lolflag::lolflag:
Jay

---

### Post by jeyaganesh on 2007-09-02
Hi I found from where error is coming. It was because of my Belkin wireless adaptor, after removing ubuntu is working very smoothly. Now I have to make wireless adaptor to work, thats the only way I can get internet connection in my room.:guitar:

---

### Post by sarutv on 2007-09-04
Jey, what type of wireless adaptor do you have? Is it PCI or PCMCIA or USB?

You can use "lspci" or "lspcmcia" or "lsusb" to list information about the cards/adaptors attached to your computer. Then using grep you can filter out information about the desired card/adaptor.

For example, I have a Broadcom BCM406 Wireless PCI card. I can find this by executing the following commands in a shell
```
lspci | grep Wireless
```

and I would get the following output:
> 
02:08.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)


So could you post some details about your card, so that we can help?

---

### Post by jeyaganesh on 2007-09-07
Hi Saru, I have Belkin G USB network adapter. I installed rt73 and ndiswrapper using instructions from ubuntu forum. Still it is not working. After installing rt73 I could restart ubuntu without any problem when the usb adapter is connected. Could you please give me any idea to make this adapter work with ubuntu? Please give me step by step method, because i have no much programming skills. Thank you very much for y ou help.

-Jay

---

