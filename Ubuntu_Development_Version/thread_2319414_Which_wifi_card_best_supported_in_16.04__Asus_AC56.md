---
title: "Which wifi card best supported in 16.04?  **Asus AC56**"
date: 2016-04-04
forum: Ubuntu Development Version
---

### Post by psychedelicwonders2 on 2016-04-04
I want to get a new wireless PCI card for my dual boot Ubuntu 16.04 & Windows 7 build.

So which card company is best supported in 16.04?  TP Link or Asus?

It's between these 2 cards, since they seem to be the best in their class:

TP Link T9E AC1900:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833704241](http://www.newegg.com/Product/Product.aspx?Item=N82E16833704241)

Asus PCE-AC68:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833320173](http://www.newegg.com/Product/Product.aspx?Item=N82E16833320173)

Or would I be best to go with an Intel card, although with much slower speeds than the first 2 choices, but also has blutooth:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833106251](http://www.newegg.com/Product/Product.aspx?Item=N82E16833106251)

---

### Post by Bucky Ball on 2016-04-04
Can your router work at the speed of the cards you're looking at?

The brands are not really a factor. It is the wireless card inside the casing that is what is compatible or not, and that can be tricky to confirm.

There is no 'best' card. Some will be supported and some won't. There is no definitive list and once 16.04 LTS is actually released people will no doubt get other cards working.

As usual, when considering graphics or wireless, if the hardware came out tomorrow (it is very new), there's a good chance it won't work, even on the latest Ubuntu.

---

### Post by mörgæs on 2016-04-04
One of the places to get hardware with good support is [https://www.thinkpenguin.com/](https://www.thinkpenguin.com/) 
Besides this I agree with the post above: Before buying stuff you should consider the speed of your router and internet connection.

---

### Post by pqwoerituytrueiwoq on 2016-04-04
In general i would say anything with a Intel chipset is going to be well supported and a good quality part
unless you have a wireless AC router i would not spend over 15-20 on a wifi card, i prefer wired connections
if it is not a AC class router, you can probably find a quality second had card on ebay for a better price, that is what i did to get my wired network card with a intel chipset (my onboard one can't to WOL on linux)

---

### Post by Beren Camlost on 2016-04-05
> **psychedelicwonders2 said:**
> Asus PCE-AC68:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833320173](http://www.newegg.com/Product/Product.aspx?Item=N82E16833320173)

While an excellent antenna, this one sports a Broadcom chip and driver support is somewhat flakey. I got this one due to having the wi-fi router upstairs, with a concrete floor inbetween. For that particular purpose, this antenna is actually pretty good.

Now the downside, Broadcom linux support.. Their driver officially supports kernels 3.19 and older. Canonical does bundle a patched version that supports at least kernel 4.2 as of time of writing. I've had isues in the past where I simply had to compile the official driver from source myself in order to have a working driver.

I've yet to get 5Ghz to work with this card in linux, but then I didn't try much. 2.4Ghz works for me.

Basically, if you need solid support, go with something else.

---

### Post by psychedelicwonders2 on 2016-04-08
Because I'm watercooling my pc, I think it's best if I just go with dongles for wifi & blutooth so the PCI card isn't an issue when running my water lines to the video card, or the water lines are in the way if I need to remove my wifi card.

I searched new egg and based on reviews & specs, I've narrowed it down to these two wifi dongles:


Rosewill RNX:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833166104&SortField=0&SummaryType=0&PageSize=10&SelectedRating=-1&VideoOnlyMark=False&IsFeedbackTab=true#scrollFullInfo](http://www.newegg.com/Product/Product.aspx?Item=N82E16833166104&SortField=0&SummaryType=0&PageSize=10&SelectedRating=-1&VideoOnlyMark=False&IsFeedbackTab=true#scrollFullInfo)

Edimax EW 7822UAC:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833315123](http://www.newegg.com/Product/Product.aspx?Item=N82E16833315123)

Seems from the reviews on the Edimax there is some kind of work around for Linux, not sure about the Rosewill though.

Do you guys think the Rosewill would be an easier/better choice for 16.04 or should I go with the Edimax?

Both are also USB 3.0 which was a requirement I was looking for with a wifi dongle.  The Rosewill is considerably slimmer and won't block other USB ports like the Edimax will, but there are extension cables I could use if that is an issue and the Edimax also as a bit of an external antenna on it.

I don't have an AC router at the moment, but since both of these dongles are only $30, I might as well upgrade that end of it and plan on getting an AC router in the near future since it will be migrating to that frequency in the very near future.

---

### Post by Yellow Pasque on 2016-04-08
> **psychedelicwonders2 said:**
> Do you guys think the Rosewill would be an easier/better choice for 16.04 or should I go with the Edimax?

Perhaps neither. What chipset does the Rosewill use? Figure that out and we will be better able to answer that question. At any rate, the Edimax adapter uses an Ralink chipset with rt2800usb module that the user needs to compile him/herself. I would avoid any adapter that uses an Ralink (or Broadcom) chipset. Intel and Qualcomm/Atheros chips are the best bets on Linux.

---

### Post by kurt18947 on 2016-04-08
Quite a useful site for things wifi related is wikidevi.com. Here is what is says about the Edimax device:

[https://wikidevi.com/wiki/Edimax_EW-7822UAC](https://wikidevi.com/wiki/Edimax_EW-7822UAC)

There appears to be at least a chance of getting this device to work.

The Rosewill seems less promising according to this:
[INDENT]AC1200UB supports following encryptions 64/128 bit WEP,  WPA-PSK/WPA2-PSK and IEEE 802.1x with ability to run in Ad-Hoc or  Infrastructure modes. What I found strange is the lack of support for  Linux machines. AC1200UB is only supported on Windows machines. Digging  deeper I found out that this unit is compatible with 802.11AC and 11  a/b/g/n standards.
[http://www.modders-inc.com/rosewill-rnx-ac1200ub-wifi-adapter-review-balance-price-vs-performance/](http://www.modders-inc.com/rosewill-rnx-ac1200ub-wifi-adapter-review-balance-price-vs-performance/)[/INDENT]

A cursory search didn't turn up anything about the chipset in this device.

---

### Post by psychedelicwonders2 on 2016-04-08
Hmm ok, well back to the drawing board.  I know the broadcom is generally not good for linux.

Not sure why I'm having such a hard time finding an intel or Atheros chipped wifi AC dongle?

Should I just get rid of the AC idea for now and just focus on N or something?  These two dongles had pretty good ratings and a great price point of $30 for AC so I figured why not, but I def need something compatible with Ubuntu as I'm trying to migrate over to it as much as possible and away from windows.

---

### Post by kurt18947 on 2016-04-09
I find N speed perfectly adequate for my purposes but I use a wired connection if i anticipate heavy network usage. I tend to not buy 'bleeding edge' hardware for use on linux machines. Linux developers can't work on drivers and hardware support until a device is released for sale and hardware manufacturers may or may not care whether their devices work with linux.

---

### Post by psychedelicwonders2 on 2016-04-09
It seems the Asus USB-AC56 wifi USB 3.0 adapter offers a Linux driver:

[URL="http://www.asus.com/us/Networking/USBAC56/HelpDesk_Download/"]http://www.asus.com/us/Networking/USBAC56/HelpDesk_Download/
[/URL]
under the wifi driver section:

ASUS USB-AC56 Driver 4.2.5_10143.20140103 for Linux
1. Support Linux kernel 2.6.18 ~ 3.10
2. Update MAC/BB/RF parameters and mechanism to improve overall performance.

Or under the utilities driver section:

ASUS USB-AC56 Driver 4.3.1.4 for Linux
Release Note-
Support Linux kernel 2.6 ~ 3.18

So I should be good to go with that one even for 16.04 don't you guys think?

---

### Post by kurt18947 on 2016-04-09
Here's my current 16.04 Ubuntu-Gnome:

4.4.0-17-generic #33-Ubuntu SMP Tue Mar 29 17:17:28 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux.  4.4 > 3.18 so it's not guaranteed.

You don't have to possess the device to see if Asus' driver will build without errors. That won't tell you if it'll actually connect but building would seem like a step in the right direction. If it wouldn't build that would be good to know too. You could also see if Asus' driver supports DKMS so it would update itself when images update.

---

### Post by Yellow Pasque on 2016-04-09
[https://wikidevi.com/wiki/ASUS_USB-AC56](https://wikidevi.com/wiki/ASUS_USB-AC56)

You'll probably want to use this repo, as it provides a driver that works with newer kernels (like the one founf in Ubuntu 16.04):
[https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux)
[https://github.com/abperiasamy/rtl8812AU_8821AU_linux/blob/master/os_dep/linux/usb_intf.c#L267](https://github.com/abperiasamy/rtl8812AU_8821AU_linux/blob/master/os_dep/linux/usb_intf.c#L267)

---

### Post by psychedelicwonders2 on 2016-04-09
Yeah I really have no idea what you guys are talking about, it's been a  long time since I've been on ubuntu and I'm beyond rusty.

So is the Asus AC56 a yay nor nay? lol :confused:

I was in Microcenter today and they had a USB dongle by j5Create Wireless AC1200

[ATTACH=CONFIG]268279[/ATTACH]

(not sure why this picture is rotated and I can't figure out how to rotate it back - seems it's an issue with uploader as it's fine on my computer?)

Says it specifically supports Mac/Windows/Linux

It  is also 3.0 USB and dual band - but I think the Asus AC56 would still  get a better signal based on it's size and the available external  antenna to add on (unless it's going to be too much of a hassle to get  to work and the j5Create might just be it)

I honestly can't  believe that finding a working USB wifi adapter for Ubuntu is this much  of work... no way that many people are using hard wired.  Obviously hard  wired is best, but it's not possible in all situations.

---

### Post by Yellow Pasque on 2016-04-10
> So is the Asus AC56 a yay nor nay? 

It won't work "out of the box" because the driver has not yet found its way into the Linux kernel. So, you'll have to build your own driver. It's not that difficult if you can copy/paste commands. Of course, you're counting on Realtek to update the driver when new kernels come out which isn't ideal.

> I was in Microcenter today and they had a USB dongle by j5Create Wireless AC1200
It uses the same chipset and driver as the Asus AC56 (Realtek 8812AU).

---

### Post by psychedelicwonders2 on 2016-04-10
Ok so we're at least getting somewhere.  

Even though they have the same chipset, don't you think the Asus will get a much better signal based on it's size and external antenna?

I can surely copy and paste commands to get it to work then, so I may go with the Asus AC56 as it seems to meet most of the criteria and not many other choices for USB adapters that will work within Ubuntu.

---

### Post by psychedelicwonders2 on 2016-04-11
Well I bought the Asus AC56 as I feel I could benefit from the added antenna.

So does anyone have a link to the walk thru of creating/adding the driver for this particular adapter to get it to work properly in 16.04?

---

### Post by kurt18947 on 2016-04-14
> **psychedelicwonders2 said:**
> Well I bought the Asus AC56 as I feel I could benefit from the added antenna.

So does anyone have a link to the walk thru of creating/adding the driver for this particular adapter to get it to work properly in 16.04?

Step by step - this thread post #2

[http://ubuntuforums.org/showthread.php?t=2228244](http://ubuntuforums.org/showthread.php?t=2228244)

---

### Post by psychedelicwonders2 on 2016-04-14
Ok that link is in regards to the Edimax usb wifi adapter, but the same steps will work for the Asus AC56?

Thank you.

---

### Post by psychedelicwonders2 on 2016-04-14
> **kurt18947 said:**
> Step by step - this thread post #2

[http://ubuntuforums.org/showthread.php?t=2228244](http://ubuntuforums.org/showthread.php?t=2228244)

Ok so following post #2 this is the code that is suggested:

```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/gnab/rtl8812au.git
cd ~/rtl8812au
make
sudo make install
sudo modprobe 8812au
```

Everything seems to go well until the last step of 
sudo modprobe 8812au

When I do that I get the following:

```
psychwonders@MainStation:~$ cd ~/rtl8812au
psychwonders@MainStation:~/rtl8812au$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.4.0-18-generic/build M=/home/psychwonders/rtl8812au  modules
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-18-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-18-generic'
psychwonders@MainStation:~/rtl8812au$ sudo make install
[sudo] password for psychwonders: 
install -p -m 644 8812au.ko  /lib/modules/4.4.0-18-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 4.4.0-18-generic
psychwonders@MainStation:~/rtl8812au$ sudo modprobe 8812au
psychwonders@MainStation:~/rtl8812au$ ^C
psychwonders@MainStation:~/rtl8812au$ 


```

As you can see the last bit of code doesn't seem to do anything and when I unplug the ethernet the wifi adapter is not active

So what is going wrong here that I need to fix?



An update - Ubuntu can now see the wireless networks available, but no  matter how many times i enter the password, it will not connect to it?   I've like 10x and it still won't.

Also even though the Asus AC56  sees the wifi networks, there is a blue LED light that is supposed to be  on with this adapter and it currently is not.

If I unplug the adapter all of the available wifi networks disappear.  

So it's slightly working, but not quite 100%?


New update - now after continue to try the network password it seems to have finally taken/saved and actually connected via wifi and I have been able to disconnect the ethernet - no clue what happened and why it finally worked after the uptenth time, but seems to be good to go now?

Is there any wifi test within ubuntu that I should run to make sure everything is configured properly?

---

### Post by kurt18947 on 2016-04-14
I use a terminal command - iwconfig - just to make sure there's nothing glaring, like many errors or really low speeds. There is a program in the repositories - wavemon which is pretty lightweight and provides an ongoing check on signal and link. If my wifi connection is performing reasonably I tend to leave things alone. I try to avoid the "if it ain't broke fix it til it is" syndrome though it sure is tempting :redface:.

---

### Post by psychedelicwonders2 on 2016-04-14
So the adapter seems to work fine except when I shut down the computer  & restart it, Ubuntu doesn't recognize it and I have physically  unplug it and plug it back in and then it boots up the wifi network  right away - what is causing this and how do I fix it?

---

### Post by kurt18947 on 2016-04-17
> **psychedelicwonders2 said:**
> So the adapter seems to work fine except when I shut down the computer  & restart it, Ubuntu doesn't recognize it and I have physically  unplug it and plug it back in and then it boots up the wifi network  right away - what is causing this and how do I fix it?

I'm not sure if it's the same cause but this was an issue with a wifi adapter I had years ago. It was caused by the adapter not going into suspend properly.  Because it didn't suspend properly it could not resume. Here is a thread that shows the fix I used:

[http://ubuntuforums.org/showthread.php?t=2004690](http://ubuntuforums.org/showthread.php?t=2004690)

post #2 was the fix that worked for me. I haven't had to use this recently but perhaps your new driver has resurrected this bug. Or perhaps your problem is something else entirely. You could try this fix and if it doesn' help, simply delete what you added. Do remember to substitute the proper module name rather than "iwlwifi" (sorry if I'm stating the obvious).

---

### Post by psychedelicwonders2 on 2016-04-17
> **kurt18947 said:**
>  Do remember to substitute the proper module name rather than "iwlwifi" (sorry if I'm stating the obvious).

Not sure to be honest, where was this step in the code?  

This is exactly what I typed in the terminal:

```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/gnab/rtl8812au.git
cd ~/rtl8812au
make
sudo make install
sudo modprobe 8812au
```

I haven't done anything else since then but now all of a sudden the adapter seems to connect just fine every time upon startup, so who knows I'm sure it will work fine for a while and then give me issues again at some point lol this stuff never works right 100% of the time

---

### Post by psychedelicwonders2 on 2016-05-14
So I haven't been on Ubuntu for the last couple of weeks and now my wifi adapter isn't working again.

I unplugged it multiple times, put it in different USB 3.0 slots, did a full update and dist-upgrade just now and even re-ran all of this code:

```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/gnab/rtl8812au.git
cd ~/rtl8812au
make
sudo make install
sudo modprobe 8812au
```

And the adapter isn't lighting up (there's a blue light on it that shows when it's alive) or working at all and even Ubuntu isn't seeing any wifi networks at all.

Any suggestions on how to get this to work again?

---

### Post by jeremy31 on 2016-05-14
No longer pertains to a development version, so it will be closed.  Poster has a new thread [here](http://ubuntuforums.org/showthread.php?t=2324552)

---

