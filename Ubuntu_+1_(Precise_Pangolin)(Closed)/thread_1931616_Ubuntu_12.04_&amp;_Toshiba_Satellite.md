---
title: "Ubuntu 12.04 &amp; Toshiba Satellite"
date: 2012-02-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by leon951 on 2012-02-25
I've notice that in the past, Ubuntu hasn't support Toshiba machines especially Laptops, and Note-books wireless cards, but Linux Mint dose. -Why? Will Ubuntu 12.04 work out of the box, with Toshiba Satellite (L755), since its going to be a DVD version (codex included?):confused: I really love Ubuntu, but since my Compaq died, I am left with a Toshiba satellite. I can only use Linux Mint, witch is not to my taste, and too much of a battery drainer. Thank you hope to hear from you.

(Pleas forgive my English it is not my first or second language but my 3rd)

---

### Post by wolfen69 on 2012-02-25
Only way to find out is to try the [12.04 daily build]("http://cdimage.ubuntu.com/daily-live/current/"). But make no mistake, it is not a finished product yet. You WILL encounter bugs. It will not be officially released until April.

---

### Post by leon951 on 2012-02-25
@ wolfen69, That's just what I did. I can say that the daily build 2/25/12 works flawlessly!(live USB of course Of course) in the Toshiba Satellite L755. Anyone ells that can vouch for their Toshiba (laptop/notebook/net-book)?

---

### Post by skewty on 2012-02-25
Did you test for the following?

1) Touchpad is properly recognized..  Touchpad tab exists in Mouse settings and tap to click can be disabled.

2) Fan speed control is working.  (Fans are not running at 100% all the time)

3) Suspend is working as expected.

4) Hybernate is working as expected

5) Wireless enable/disable switch is working as expected.

---

### Post by jbicha on 2012-02-26
I don't know. I've been using a Toshiba Satellite with Ubuntu for years.... You need to be more specific about what hardware you have that isn't supported, and then use ubuntu-bug linux to report it.

Hibernate is based on a number of factors, and hardware is only one of them. By the way hibernate is hidden in Ubuntu 12.04 because it's slow and doesn't work in a large number of cases.

---

### Post by leon951 on 2012-02-26
@skewty I did, but did not test the fans. All I was worried about was the wireless card. The mouse pad worked, the side drag did too (scrolling). The disable/enable  mouse pad button did just as well.
 but I will check with the hibernate and fans speed ASAP. Thank you for your response.

@jbicha: There are way to many, just google "Toshiba Ubuntu", and look at all the problems people have just trying to get a proper installation. My problem always has been with
 "LAN : 10/100 Ethernet
WLAN : 802.11 b/g/n" dosent response to rfkill hard blocked/ or soft blocked. Thank you for your response & am really happy that you haven't encounter any problems through out the years you have used Ubuntu.

 Specks? [http://laptops-specs.blogspot.com/2012/01/toshiba-satellite-l755-s5103.html](http://laptops-specs.blogspot.com/2012/01/toshiba-satellite-l755-s5103.html)

---

### Post by craig10x on 2012-02-26
chalk me up as another who has been using toshiba laptops over a bunch of years now and always found them to be very linux friendly....

I've been using linux since ubuntu 8.04 and have used ubuntu, mint, zorin, pclinuxos, kubuntu, and a bunch of other distros with toshibas and amd processors and now with intel and always had a good working linux os with them...

When you check the fans, run something like a streaming radio station in the background for at least an hour or two...if the fan doesn't start kicking in a lot then you are good to go.... :)

I'm running a new toshiba now with intel, 64 bit install of ubuntu 11.10 and using unity as well...

A note: there has been a power regression problem in the linux kernel since version 2.38 and on...which causes some laptops (regardless of brand) to consume much more power and also causes the fans to come on frequently or all the time...there is a patch that ubuntu is putting into the kernel that will be in ubuntu 12.04 but not sure if they have it working up to snuff yet, so you can try a current alpha or daily build and see...but if you do have a problem then check again when the FINAL VERSION is released, as it might work better by then...

---

### Post by leon951 on 2012-02-26
@craig10x Thank you craig10x, one thing though. Where you able to boot from CD/DVD or did you have to create a bootable USB/SD card? 
 Did you ever had any problems with the WIFI out of the box? Like dealing with the soft or hard block?

---

### Post by phaed on 2012-02-27
Toshiba has been using RealTek wireless cards, and the kernel has slowly been getting support over the last 10 releases or so. The Debian Wiki has a nice run down of the devices:

[http://wiki.debian.org/rtl819x](http://wiki.debian.org/rtl819x)

Most are supported now, although apparently there are still some bugs with a few USB devices. Also, you can get wireless drivers backported from newer kernel versions. Search for "backports-modules-cw".

---

### Post by leon951 on 2012-02-28
> **phaed said:**
> Toshiba has been using RealTek wireless cards, and the kernel has slowly been getting support over the last 10 releases or so. The Debian Wiki has a nice run down of the devices:

[http://wiki.debian.org/rtl819x](http://wiki.debian.org/rtl819x)

Most are supported now, although apparently there are still some bugs with a few USB devices. Also, you can get wireless drivers backported from newer kernel versions. Search for "backports-modules-cw".

Thank you so much, this is really valuable information.

---

### Post by craig10x on 2012-02-28
> **leon951 said:**
> @craig10x Thank you craig10x, one thing though. Where you able to boot from CD/DVD or did you have to create a bootable USB/SD card? 
 Did you ever had any problems with the WIFI out of the box? Like dealing with the soft or hard block?

Sorry i couldn't get back to you sooner...actually, i have my boot set up on my toshiba set to to boot the cd/dvd drive first....that way, if i stick an iso of any distro in my dvd drawer while on my installed system and restart, then it will automatically go to the live disc and boot off it....

When you have it set up like that, it always looks first to see if there is a dvd/cd to boot off of and if not, after a second or two just proceeds to boot into the hard installed system...

I set it that way to save extra bother, since i often like to test isos of different distros and newer versions of ubuntu of course :D

I guess the wireless business others have commented on...i just use an ethernet cable connection...though i do notice that though my wireless isn't turned on it seems to be recognizing locally wireless networks in my area, so i'd imagine that indicates that wireless (if i was using it) would have no problem setting up...

---

