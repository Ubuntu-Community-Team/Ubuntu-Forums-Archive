---
title: "Problem in Installing Internet Explorer"
date: 2010-08-21
forum: Wine
---

### Post by nogienugz on 2010-08-21
Hi, 

I'm trying to install internet explorer in ubuntu. I followed the instructions in the community official documentation but still it's giving me error messages like my WINE is not the updated. 

I've already installed the latest version of Wine but still got those errors. I took a snapshot of the error(see attachment). 

Can somebody give me help on this? I really need to install IE because most of the sites that I need to go to works only on IE. 

Thanks.

---

### Post by Ms_Angel_D on 2010-08-21
Don't use ies4linux it's not even being developed anymore. You can install the up to ie8 in wine using [winetricks]("http://wiki.winehq.org/winetricks")

---

### Post by ronnielsen1 on 2010-08-21
Open a terminal and type in winecfg. Click the About tab and post the wine version

[IMG]http://i80.photobucket.com/albums/j177/ronnielsen1/Screenshot-Wineconfiguration-2.png[/IMG]

If you don't have 1.2 or 1.3 beta installed I'd recommend installing it. You can enable the repository and stay current by typing in 

```
sudo add-apt-repository **ppa:ubuntu-wine/ppa**
```

in a terminal

---

### Post by Rubi1200 on 2010-08-21
Why not consider installing a virtual environment to run Windows and then use IE there?

---

### Post by kuramayoko10 on 2010-08-21
Sorry... I thought this solution was goign to work on linux...

---

### Post by nogienugz on 2010-08-22
Ms_Angel_D

I tried installing IE using winetricks but didn't get any success. I tried installing IE8 first but after installing it, it won't connect to the internet(message is that, it's still connecting... ). Even after 10 mins. the status is still connecting. 

I installed IE6 instead. The installation was successful but the problem is, I can't enter any text in it. I mean, if I tried opening my Gmail, I can't enter my username or my password. All that I can do is browse the web.

Btw, my wine version is 1.3. (See the attachments). I also attached an error message I got during the IE installation.


Rubi1200,

Virtual environment on Ubuntu? 'havn't heard of this yet, but I'll give this one a shot....

---

### Post by Ms_Angel_D on 2010-08-22
I'm not sure what the issues could be it was just a suggestion, I"m not really qualified to help troubleshoot wine. Hopefully my reply will at least bump your topic where someone who is qualified can help you. Also I will move this topic to the wine sub-forum hopefully you may see better support.


Good Luck!

---

### Post by nogienugz on 2010-08-22
> **Ms_Angel_D said:**
> I'm not sure what the issues could be it was just a suggestion, I"m not really qualified to help troubleshoot wine. Hopefully my reply will at least bump your topic where someone who is qualified can help you. Also I will move this topic to the wine sub-forum hopefully you may see better support.


Good Luck!
Ms_Angel_D, 

No problem. Wine sub-forum is good idea. Thanks!

---

### Post by nogienugz on 2010-09-18
Hi everyone,

I've been able to solved this issue. I followed Rubi1200's advice of using VM and installing IE there (see attached snapshots).

I installed Virtual Box and installed windows xp sp3 as my guest OS. Everything went fine. I've been using VM as a workaround for those apps and websites that would only work for windows OS for almost a month now.

One piece of advice though. For those who doesn't have any background to VM environment (like me) and are planning to use it, make the drive where you'll be putting the image of your guest OS *MOUNT AUTOMATICALLY*. This will save you from dealing with problems like "problem in attaching the image file....." in Virtual Box.

PS: Thanks Rubi1200 for the suggestion.;)

---

