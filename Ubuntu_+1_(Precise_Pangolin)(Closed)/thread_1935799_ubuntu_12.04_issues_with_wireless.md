---
title: "ubuntu 12.04 issues with wireless"
date: 2012-03-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by linuxaddix on 2012-03-05
ive been running the kubuntu 12.04 for a while and have had no issues getting my b43 installed.when i tried the ubuntu 12.04 beta unity i have been getting nothing but headaches.the firmware-b43-installer doesnt work and when i googled it i found this:
[http://www.ubuntuupdates.org/package/core/precise/multiverse/base/firmware-b43-installer](http://www.ubuntuupdates.org/package/core/precise/multiverse/base/firmware-b43-installer)

but it doesnt work?ive been stumped on it.i just want to see the new highlights of ubuntu 12.04.
as ive said ive been running kubuntu12.04 and it is very stable.
if anyone can help me install the b43 firmware i'd appreciate it

---

### Post by ewz on 2012-03-05
Hello, when you say it doesn't work is your wireless card detected at all?
I have an old Leovo laptop with a b43 chip running 11.10, the card wasn't detected at all, even though the driver was installed, I found the fix for this problem here [https://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/]("https://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/")

turns out the wrong driver was being installed.

it is strange that it worked in Kubuntu 12.04 and not Ubuntu 12.04 though
really they are the same system apart from the desktops I would have thought...

---

### Post by nothingspecial on 2012-03-05
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

---

### Post by linuxaddix on 2012-03-06
the problem is right ther when i put in terminal:
sudo apt-get install firmware-b43-installer

i ran that after running a sudo update and it says it cant find the package i get errors.
and yes they are the same distro thats what i am so confused about.
any other solutions?

---

### Post by kauboy on 2012-03-10
I have the exact same problem. I have a MacBook Pro 8,1 Late-2011 that has the Broadcom BCM4331 wireless card and tried Ubuntu 12.04 x86-64 beta-1 in Live USB.

The Network applet in the top panel says

"Wireless Networks
device not ready (firmware missing)"

```

lsmod | grep b43
#Output:
b43
mac80211
cfg80211
ssb
bcma
```

/etc/modprobe.d/blacklist.conf has "blacklist bcm43xx" although ```
modprobe bcm43xx
``` says "FATAL: Module bcm43xx not found."

```
sudo apt-get install firmware-b43-installer
``` says unable to locate package.

Very frustrating that everything EXCEPT wireless works out of the box on my MacBook - touchpad with gestures, keyboard hotkeys, awesome battery life! :D Especially when linux kernel 3.2 supposedly added support for BCM4331. :(

---

### Post by josemanuel on 2012-03-18
The same for me: absolutely frustrated after many trials. I just got it once miraculosly working after patching (with message errors)+ updating ... and working suddenly. But system crashed afterwards , corrupted and I had to reinstall ... no more chances

 Any help will be very welcome

---

### Post by zedstar on 2012-03-19
Hi.

I can confirm that the following works on a Macbook Pro 8,1:

[http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html](http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html)

---

### Post by josemanuel on 2012-03-19
It worked!!!. I had tried several times exactly the same recipe and it didn't work. Don't ask me why it worked just now! But I had to use the bleeding edge driver. compat-wireless-2011-10-09 gave many errors at compilation. I used compat-wireless-2012-03-18  and wireless worked like a charm (I'm now using it, as readily and happily unplugged the ethernet cable). 

Now I'm afraid to make an update which probably will force me to recompile with the new kernel headers..I'll wait several days until stable distribution. 


 Many thanks

---

### Post by ias on 2012-03-31
Excellent.:KS It worked! Damn complicated, if you ask me. This should be much easier. As I extracted using the archiver, I had to backtrack, and do it again by hand, as the command line instructions assume you are in certain directories at certain times.

Why is this so hard on the mac? Even getting ubuntu to install on a macbook pro 8,1 takes a cd AND a usb. That's the only thing that works as far as I know.. But that's off topic, I know.:D

---

### Post by cariboo on 2012-03-31
> **josemanuel said:**
> It worked!!!. I had tried several times exactly the same recipe and it didn't work. Don't ask me why it worked just now! But I had to use the bleeding edge driver. compat-wireless-2011-10-09 gave many errors at compilation. I used compat-wireless-2012-03-18  and wireless worked like a charm (I'm now using it, as readily and happily unplugged the ethernet cable). 

Now I'm afraid to make an update which probably will force me to recompile with the new kernel headers..I'll wait several days until stable distribution. 


 Many thanks

I hope you documented your problem, and created a bug report, as that's what we are here for.

---

### Post by Chillyguess on 2012-04-06
Hi guys, 

I am having similar issues with the wireless. Why is it so hard to get it to work? So frustrated with it. 

My specs:

Thinkpad W510
Dual-boot with Ubuntu 12.04 and Windows 7

issue:

Wireless "connects" but can't use the internet at all! There is no connection even in Software Updates.

---

### Post by cariboo on 2012-04-06
@Chillyguess, It looks like your problem is different from the op's. Can you open a terminal and try the following two commands:

```
ping www.google.com
```

and next 

```
ping 173.194.33.48
```

IF you don't get an answer back from [www.google.com](www.google.com), but you do get a result from 173.194.33.48, then you have a DNS problem.

---

### Post by dhruvraj on 2012-04-06
ive a broadcom driver as well and it was working well on 11.10

now i have wifi connecting, but keeps dropping every minute. and i have to keep giving my password every minute to make it work, for another few seconds!!

---

### Post by eB0Y on 2012-04-07
Same problem like dhruvraj here on Toshiba® Satellite® c660!

---

### Post by jerrylamos on 2012-04-07
Ubuntu kernel hasn't supported my IBM Thinkpad wireless 
Cisco Aeronet Wireless 802.11b
since Narwhal.  Yes I wrote a bug.  

What ubuntu does is connect, get started, then the ubuntu kernel disconnects.
So I found an old dusty pc card
Realtek RTLB8180L 802.11b MAC
which the kernel does support.

Now, every time I boot, the kernel tries to connect with the Aeronet, connects, then disconnects, I get a drop down message to cancel.  Then ubuntu does it again. And again.  So I go to the wireless applet and disconnect Aero manually.  Get another "disconnect" message, then no more until I boot again.

All the meanwhile the old Realtek has been working O.K.

I fiddled around with the forum suggestions for wireless for a while, got frustrated, and just put up with it.

Jerry

---

