---
title: "Qualcomm Atheros QCA9377 wifi disapears, Zorin 12.4"
date: 2019-05-10
forum: Ubuntu/Debian BASED
---

### Post by orangeurge on 2019-05-10
Hello everyone!

I am new here, both on the forum and on Ubuntu/Zorin OS. Since Zorin is based on Ubuntu I hope it's ok that I post here. I apologize in advance if I broke any forum rules. 

I have this problem with wifi that I have had for a long time and its quite frustrating because this is my only laptop and I use it for studying at uni. When I was running windows, after some time wifi card started disapearing and would sometimes go back on after a reboot but only for a short while. When I did troubleshooting, this came up (i found similar case to mine on internet): 

[URL="https://filestore.community.support.microsoft.com/api/images/6b839d15-1551-4b65-ace8-90269582333f?upload=true"]https://filestore.community.support.microsoft.com/api/images/6b839d15-1551-4b65-ace8-90269582333f?upload=true


[/URL]I tried several things like driver update and to write in command line "netsh wlan set hostednetwork mode=allow". It seemed like that helped for a while, or maybe the wifi card just started working by itself for a few minutes/hours after reboot. Nothing else helped, and sometimes the wifi card disapeared also from the device manager.

Then a few days ago I decided to install Zorin. Wifi worked without problems the first day, then the next day it stopped working again, or worked for maximum 30 min to 1 hour after a reboot. Other times reboot didnt help at all. 

I did what was told on this page: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

but nothing helped. Here is the wireless info script: [URL="https://pastebin.com/ZtmNjiUc"]https://pastebin.com/ZtmNjiUc


[/URL]
Your help is greatly needed and will truly be appreciated beyond words.



Kind regards, 
orangeurge

Forgot to mention (if that is of any use) this additional information about the laptop:

4gb RAM
Intel® Celeron(R) CPU N3060 @ 1.60GHz × 2
Intel® HD Graphics 400 (Braswell)

---

### Post by howefield on 2019-05-10
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by orangeurge on 2019-05-11
Hi. Maybe you should have left it there because the fix is probably the same for Ubuntu as for Zorin. I fear not many people will see my post and the problem with the wifi card will remain unresolved.

---

### Post by him610 on 2019-05-11
orangeurge with Atheros QCA9377, welcome to the forums

Good News: Your wireless adapter can receive and pickup nearby APs. Some have strong signals.

Line 56 reads: SecureBoot enabled
In Bios/Eufi, change to SecureBoot Disabled

Line 293 reads: country 00: DFS-UNSET
You need to set your country code.
To set it temporarily, if you actually are in Norway; if not then insert correct country code.
```
sudo iw reg set NO
```

To set it permanently,
```
sudo nano /etc/default/crda
```
Bottom line, change to read *REGDOMAIN=NO*
Save the file and exit


The temporary setting should be good through the current session. The permanent setting should be good for future sessions.
To check your country code, ```
iw reg get
```
Reference for country codes: [https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2]("https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2")

---

### Post by orangeurge on 2019-05-12
Hi!

In the morning I did everything like you wrote, and wifi worked like it supposed to. Everything worked great for the whole day. Even when I restarted several times and closed the lid. I thought it was finaly fixed. But when I came home late at night from uni and opened the laptop, the problem came unfortunately back. 

I checked the country code with ```
iw reg get
``` and now it again shows "country 00: DFS-UNSET". But when I go to change again permanently with ```
sudo nano /etc/default/crda
``` the bottom line already say "REGDOMAIN=NO". Whats going on?

---

### Post by orangeurge on 2019-05-12
Also, just in case, I want to add a few more things here. After the wifi was working, I did two more things:

The first one was that I wanted to disable automatic remote printer installation. I followed what was written here: [https://askubuntu.com/questions/345083/how-do-i-disable-automatic-remote-printer-installation/556963](https://askubuntu.com/questions/345083/how-do-i-disable-automatic-remote-printer-installation/556963)


But then for some reason there was no sound from the laptop speaker, but when I plugged in the headset the sound was fine. I don't know if that had something to do with me removing remote printers. So after googling and trying several things to bring back sound to the speakers, I fixed the issue with this: [URL="https://zoringroup.com/forum/viewtopic.php?f=5&t=5844"]https://zoringroup.com/forum/viewtopic.php?f=5&t=5844
[/URL]

So after fixing the sound, everything was normal as it supposed to be. But when I came home, the wifi gone again. What could be the issue here?

---

### Post by orangeurge on 2019-05-14
Hello again him610 and thank you for reaching out.

So yesterday I googled for various solutions in regards to the wifi issue which I then applied, and voilà, it looks the wifi card is back online. 
Unfortunately I can't say for sure which of the solutions were indispensable, as I am not able when it comes to the programming world and was a bit frustrated while working in the terminal. 
Hopefully the issue will not reappear. 

When it comes to Zorin, I must say I enjoy it quite a lot. Simple and elegant, just what I need for the moment. I didn't mention this before, but there where other unpleasant cases too when I was running Windows. 
One of them was that one of the usb ports didnt function properly. And do I need to even mention all the updates that my laptop constantly has to be abused with? And 30+ GB of space that the system takes up?

The only minus for me with Zorin right now is that there is no SafeExamBrower for Linux systems, which means I will have to borrow a PC for when I will have to take the exams.
With that said, I will still stay with Zorin for the time being.

Cheers!

---

### Post by him610 on 2019-05-14
Congratulations on the apparent fix. Good luck on your exam. Please mark your issue as closed in the thread tools.

---

### Post by orangeurge on 2019-05-15
I knew I shouldn&#8217;t have put my hopes up too soon. It seemed to good to be true. We are back where we started with no wireless internet. Looks like this issues will never be resolved. I&#8217;m never buying Acer ever again.

---

### Post by orangeurge on 2019-05-15
Right now it says that its connected but the page never loads.

edit: nevermind. Now its gone :mad:

---

### Post by orangeurge on 2019-05-15
Please help?

---

