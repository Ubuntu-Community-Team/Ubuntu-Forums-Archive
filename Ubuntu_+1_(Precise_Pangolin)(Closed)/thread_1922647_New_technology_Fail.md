---
title: "New technology Fail?"
date: 2012-02-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by gator on 2012-02-09
Ive been using ubuntu for years, but we now have new machines in our office and all linux distro's are struggling to display anything but grub.It has a 22 inch touch screen. I can hear the ubuntu music as it hits the desktop but i can not see anything. ALT+ 1,2,3 etc give nothing. The machine specs are here 

[http://www.mytoshiba.com.au/products/computers/all-in-one/dx1210/pqq09a-02900g/specifications#details](http://www.mytoshiba.com.au/products/computers/all-in-one/dx1210/pqq09a-02900g/specifications#details)

Also can we expect ubuntu to handle multiple displays using displaylink usb adapters? We struggled under other versions ( using multiple x-servers ) to get this working. making it easy would be a win.

Please help in getting my Toshiba to display a desktop.. that would be a start.

Cheers

---

### Post by shakabra on 2012-02-09
Have you tried booting with nomodeset?

---

### Post by dino99 on 2012-02-09
To get a better chance with this bleeding edge hardware, use also the lattest kernel (kernel-ppa) and the latest xorg and like (xorg-edgers ppa)

---

### Post by gator on 2012-02-09
> **shakabra said:**
> Have you tried booting with nomodeset?

No i havn't but i will tomorrow. I'm sure it will be good if i could just see something. As for adding xorg-edgers and other non standard stuff would be easy if i could see something.... anything

---

### Post by dino99 on 2012-02-09
> **gator said:**
> No i havn't but i will tomorrow. I'm sure it will be good if i could just see something. As for adding xorg-edgers and other non standard stuff would be easy if i could see something.... anything

maybe some tests in recovery mode and/or livecd will help: check /var/log/, driver activation (jockey)

---

### Post by gator on 2012-02-09
> **dino99 said:**
> maybe some tests in recovery mode and/or livecd will help: check /var/log/, driver activation (jockey)

Thanks for the reply Dino but recovery shows nothing on the screen as does a live CD. CTRL+ALT+ 1,2,3,4, etc show nothing but ubuntu does boot as i hear the desktop-loaded sound. We deploy these machines with a linux based "ghost" called "FOG" and a Win7 image. We had to upgrade fog to a 3.0+ kernel to pick up the ethernet card but it works great, and we get to see the console!. ubuntu shows nothing.

---

### Post by prusswan on 2012-02-09
so the only thing you can see is the grub boot menu, and x session is not loading for some reason?

---

### Post by gator on 2012-02-09
> **prusswan said:**
> so the only thing you can see is the grub boot menu, and x session is not loading for some reason?

exactly, the screen goes black after that. in desperation I even tried android x86 with the same result ( works great on my eeepc but thats another thread ). I'll try the nomodeset tomorrow at work.... boot alpha2, edit grub kernel and add 'nomodeset', right?

It appears like this beautiful 21.5" touch screen is causing problems.

---

### Post by dino99 on 2012-02-09
Googling around, you seems sadly not to be alone:

[http://www.google.com/search?q=ubuntu+hdmi+toshiba&hl=fr&biw=1161&bih=844&num=10&lr=lang_en&ft=i&cr=&safe=images](http://www.google.com/search?q=ubuntu+hdmi+toshiba&hl=fr&biw=1161&bih=844&num=10&lr=lang_en&ft=i&cr=&safe=images)

i suppose you can ask the tosh support to get detailed info about how the video is plugged. Seen a user talking about non standard edid used by tosh.

---

### Post by gator on 2012-02-09
> **dino99 said:**
> Googling around, you seems sadly not to be alone:

[http://www.google.com/search?q=ubuntu+hdmi+toshiba&hl=fr&biw=1161&bih=844&num=10&lr=lang_en&ft=i&cr=&safe=images](http://www.google.com/search?q=ubuntu+hdmi+toshiba&hl=fr&biw=1161&bih=844&num=10&lr=lang_en&ft=i&cr=&safe=images)

i suppose you can ask the tosh support to get detailed info about how the video is plugged. Seen a user talking about non standard edid used by tosh.

thanks Dino, i did google the same things myself, but i'm special, i have "new technologies" not supported by Ubuntu-daily-build-liveCD. Maybe the "nomodeset" will open the door to an install. I kinda thought someother user had one of these and could give me pointers. ALL distro's hate this display.

---

### Post by ELD on 2012-02-09
You realise this is the forum for the in-development version of Ubuntu right? Not a general support forum. Unless you are using 12.04 wrong forum and you shouldn't use 12.04 for production machines...

---

### Post by gator on 2012-02-09
> **ELD said:**
> You realise this is the forum for the in-development version of Ubuntu right? Not a general support forum. Unless you are using 12.04 wrong forum and you shouldn't use 12.04 for production machines...

Of couse i relise where i am.. its clear that all versions of Ubuntu.. even the daily build will not display. I'm not using this for production.. yet. I have my new toshiba + Win 7 + 2 X 22" displaylink USB adapters. I ( have to ) manage my linux servers with "superPutty" + WinSCP. I much prefer Ubuntu + Kubuntu to Win 7.. and who knows, if you tell people the problem they might tweak xorg and get that mega toshiba touchscreen working.:popcorn:

---

### Post by dino99 on 2012-02-09
maybe its possible to plug an external LCD and get the video output

---

### Post by gator on 2012-02-09
> **dino99 said:**
> maybe its possible to plug an external LCD and get the video output

it appeares i have a HDMI input ?( why would i use this? ) but no output. Bummer!, i have my money on the nomodeset.. what do you guys think?

---

### Post by Ibidem on 2012-02-09
> **gator said:**
> thanks Dino, i did google the same things myself, but i'm special, i have &quot;new technologies&quot; not supported by Ubuntu-daily-build-liveCD. Maybe the &quot;nomodeset&quot; will open the door to an install. I kinda thought someother user had one of these and could give me pointers. ALL distro's hate this display.

 IIRC, the tricks were something like &quot;nomodeset i915.blacklist xforcevesa&quot;  But I suspect that the issue is at least as much the graphics card. If you can boot in text mode (```
text
``` parameter), what's lspci|grep VGA say?

---

### Post by gator on 2012-02-09
WINNING !!!

nomodeset worked, i also removed the quiet splash. I'm typing this from Kubuntu 12.04. Thank you guys for your help. My next question is how to getmore than 1280x1024, any ideas?

 lspci|grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

---

### Post by effenberg0x0 on 2012-02-09
> **gator said:**
> WINNING !!!

nomodeset worked, i also removed the quiet splash. I'm typing this from Kubuntu 12.04. Thank you guys for your help. My next question is how to getmore than 1280x1024, any ideas?

 lspci|grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

I never played with such hardware, but I'd say maybe a custom xorg.conf can be necessary, given its particularities?

Regards,
Effenberg

---

