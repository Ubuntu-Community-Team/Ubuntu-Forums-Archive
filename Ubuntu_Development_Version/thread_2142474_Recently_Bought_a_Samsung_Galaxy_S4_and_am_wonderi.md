---
title: "Recently Bought a Samsung Galaxy S4 and am wondering if 13.10 can be installed on it?"
date: 2013-05-05
forum: Ubuntu Development Version
---

### Post by kevpan815 on 2013-05-05
Before I ask my question: I must Apoligize for my recent Bad Behavior for trying to tell you guys what you can an can and can not post, I now realize that it's Cariboo907's job to due that (and the rest of the Moderator's here as well) and it is NOT my job to be Bossing you guys around about 13.04 discussions and that if I fell a Post is out of place I should instead click Report Post as I am NOT a Forum Admin or a Moderator. I am sorry for my bad behavior and hope that you guys will forgive me for my OutBurst.

I recently ordered a Samsung Galaxy S4 and have a few questions about trying to test 13.10 on it (if it is possible at all) and also if it requires me to Root my Android Jelly Bean 4.2 Phone (which is something I am NOT about to do because 1. It would Void my new Phone's Warranty, and 2. It is now Illegal in the U.S.A. to do that) and 2. If it would void my Warranty anyways (even if it does NOT require you to Root the Phone)? Thanks in Advance.

---

### Post by EgoGratis on 2013-05-05
The answer is no your device is (currently) not supported.

---

### Post by kevpan815 on 2013-05-05
Thank you for Replying to what may seem like a Silly Question BUT It has been a while since I owned an Android Cell Phone (I have been buying IPhone's for the Past couple of years and this is my first Android Cell Phone since some time in 2005 or earlier, BUT the Galaxy S4 looked like a too good of an Android Phone to pass up compared to the 5S IPhone that is coming from Apple this year so thank you for answering what was probably a stupid question to begin with. :-)

---

### Post by Nburnes on 2013-05-05
1. Is true. But you can easily gain it back with some form of restoring. Whether that is through Samsung's ODIN, or using your own stock backup made in recovery. 
2. Rooting is not illegal in the US. Only carrier unlocking through unofficial means. (But it's not like SWAT is going to come kicking down your door at night anyway)

---

### Post by EgoGratis on 2013-05-05
It's not stupid question the support for your device is AFAIK just not there yet. It might be in the future. 

You expressed some concerns and they would/will be best addressed when you will be able to buy Ubuntu phone. Let's hope this will happen in 2013/2014.

---

### Post by kevpan815 on 2013-05-05
> **EgoGratis said:**
> It's not stupid question the support for your device is AFAIK just not there yet. It might be in the future. 

You expressed some concerns and they would/will be best addressed when you will be able to buy Ubuntu phone. Let's hope this will happen in 2013/2014.

So there will be no way to get this Software on an Existing Android Cell Phone is what you are telling me right? I did Re-Read the Ubuntu Cell Phones Home Page and did NOT realize that you have to be an OEM or Operator to request the Software right now. All I had previously noticed is the AD about Ubuntu on Android and did NOT read the fine print. :-)

---

### Post by EgoGratis on 2013-05-05
> So there will be no way to get this Software on an Existing Android Cell Phone is what you are telling me right?

No i didn't say that it might be in the future but we are not there yet. BUT for the users that don't want to mess with default phone OS we do need Ubuntu phones on the market. Currently you can test tablet images for example this is possible but if you don't want to mess with default tablet OS you will have to wait until some Ubuntu tablets are on the market.

---

### Post by EgoGratis on 2013-05-05
BUT don't worry too much if you currently don't have compatible tablet you will be able to test a lot of technology/software used on Ubuntu Touch right from your desktop in this development cycle. This will gradually prepare you for future devices you will use...

PCs, tablets, smart phones... running Ubuntu.

---

### Post by Cheesemill on 2013-05-06
Ubuntu Touch has already been ported to other phones in the Samsung Galaxy range, it's probably just a matter of time before it is ported to the S4.

[https://wiki.ubuntu.com/Touch/Devices#Working.2C_but_not_available_from_cdimage.u.c](https://wiki.ubuntu.com/Touch/Devices#Working.2C_but_not_available_from_cdimage.u.c)

---

### Post by grahammechanical on 2013-05-06
As I understand it Ubuntu Touch images are now being built upon Raring but not for the desktop. A few of us installed MIR and the Ubuntu Touch core apps on the desktop while we were testing Raring. I have not yet tried this in Saucy but in one sense it is true that if we want to test MIR and the core apps we should run it on Raring and not Saucy. But there is nothing stopping us from experimenting.

I think that we should distinguish between Canonical and its aims for the future of Ubuntu and Community development. Ubuntu is open source and any community developer can take the source code and port it to any device that they want. Indeed Canonical encourages this to happen. And if we have one of those devices we can share in testing the port to that device.

Canonical, as far as I can tell, has other aims. 1) to assist OEMs in bringing Ubuntu mobile devices to market; 2) Assist developers in providing apps for Ubuntu mobile devices; 3) Producing a User Interface (called the Ubuntu platform) that scales across 4 types of device (PC, Phone, Tablet, TV).

As I see it, testing is useful. So, even if someone is not a developer or an OEM, it may be helpful if someone installed this stuff on their devices to give feed-back. We are doing this right now by running Saucy on our desktops. Stick with the development branch for a year and we will see a convergent user interface on the desktop.

QA.ubuntu has test cases for Ubuntu Touch on tablets. And there are daily builds built upon Saucy. But there is a limited device range.

[https://wiki.ubuntu.com/Touch/Install](https://wiki.ubuntu.com/Touch/Install)

Regards and good testing

---

### Post by leetleo on 2013-05-12
I'm also interested in getting Ubuntu up and going on my Galaxy S4, hopefully someone on the dev team picked one up :P

---

### Post by mr john on 2013-05-13
Actually you can install the desktop version of Ubuntu on almost any Android phone. However, when it's running on your phone you will need to use VNC to access the user interface. An ssh connection should also be possible from the terminal emulator on the phone (downloadable from Google play). Basically it involves running Ubuntu as a Virtual Machine on the phone and connecting to that VM via VNC. Because its a VNC connection the responsiveness and quality of the user interface will not be very good. It's worth experimenting with if you're bored or have some extra time on your hands. In theory the ssh capabilities should allow your phone to act as an Ubuntu Server.

[http://forum.xda-developers.com/showthread.php?t=1585009](http://forum.xda-developers.com/showthread.php?t=1585009)

---

### Post by klm46 on 2013-05-29
Hey there,

i get my S4 (snapdragon) these days and getting in this issue as an involved User :D
did anyone of you tried this? It Would be very interessting for me to get some Information about such testings...

[http://cdimages.ubuntu.com/ubuntu-touch/daily-preinstalled/current/](http://cdimages.ubuntu.com/ubuntu-touch/daily-preinstalled/current/)

---

### Post by klm46 on 2013-05-29
Sorry for the Second Post, but i got another question, and its Late :popcorn:

If i got this right Nobody is working on a native installation?

[https://wiki.ubuntu.com/Touch/Devices#Working.2C_but_not_available_from_cdimage.u.c](https://wiki.ubuntu.com/Touch/Devices#Working.2C_but_not_available_from_cdimage.u.c)

---

### Post by Cheesemill on 2013-05-29
No, not at the moment.

It's still a new phone though so give it a few months and I'm sure someone will have it ported.

---

