---
title: "Lenovo IdeaPad Yoga Ultrabook"
date: 2012-01-19
forum: Ubuntu, Linux and OS Chat
---

### Post by '76 on 2012-01-19
Not sure where to stick this but...

This new Ultrabook looks pretty freakin nifty..

How long do you think it will take Ubuntu or maybe the Gnome people to develop it uses if ever?

---

### Post by apauld on 2012-10-25
I will update my experience with 12.10 tomorrow!

I am a little worried about the EFI boot lock.



> **'76 said:**
> Not sure where to stick this but...

This new Ultrabook looks pretty freakin nifty..

How long do you think it will take Ubuntu or maybe the Gnome people to develop it uses if ever?

---

### Post by Mista Teaser on 2012-10-28
> **apauld said:**
> I will update my experience with 12.10 tomorrow!


Anything new yet?

I am curious about running Ubuntu on that yoga device.

Does anybody else have yet their hands on that device and has tried to run Ubuntu on it?

---

### Post by gogibby on 2012-10-28
I have successfully booted into both Ubuntu 12.10 and Xubuntu 12.10 on the Lenovo Yoga. It worked surprisingly well in terms of the touch screen interface, but I could not get a wireless connection working, and sadly it does not have an ethernet port. One way to boot in from USB is to go to the Settings in Windows 8, under the General tab, and there is an Advanced Restart option, which allows you to boot from USB device. The other option is there is a tiny 'Novo' button next to the power button, which when pressed with the computer off, will give you different boot options. Hopefully Lenovo will release wireless drivers soon. Right now, they don't even have a User Guide online yet! I plan to make post some videos soon.  I Love the form factor, but on the 128GB SSD, I only have 40GB available [all kinds of crazy Windows partitions], and I haven't barely installed anything yet! Because of that (and awful webcam) I plan on returning it.

---

### Post by apauld on 2012-10-29
Not as much luck for me but only spend a few minutes so far. I booted 12.10 and got a busybox prompt but haven't had the time to troubleshoot it. Windows 8 was interesting for about 24 hours, now it's time to get back to normal. If I can get Ubuntu to work, I will keep it. Otherwise, it's going back as well.

---

### Post by gogibby on 2012-10-29
For what it's worth, I used Unetbootin to create my USB stick with the 64 bit image... Mine is already back at the store!

---

### Post by odror on 2012-10-29
> **gogibby said:**
> For what it's worth, I used Unetbootin to create my USB stick with the 64 bit image... Mine is already back at the store!

Do you know if there is a similar laptop that will work with ubuntu. Did you try to use boot-repair in order to boot directly from the hard disk.

---

### Post by Mista Teaser on 2012-11-01
Thanks guys for sharing your experience.

That sounds not very good ... well - i thought lenovo is a partner of canonical - i really hoped that the yoga will be compatible with ubuntu

---

### Post by brdmn on 2012-11-06
Very useful for me as well.  And disappointing.  I guess it'll be another year or so before it is safe to buy a convertible tablet compatible with Ubuntu.

---

### Post by odror on 2012-11-06
> **brdmn said:**
> Very useful for me as well.  And disappointing.  I guess it'll be another year or so before it is safe to buy a convertible tablet compatible with Ubuntu.
look at the intel web site new ones are coming from other vendors. The Asus looks promising. I tried the acer V5 touchpad with the live CD of Ubuntu 12.10. It seams to work fine. The only issue is that I do not know how to change the HD to SSD. Otherwise I would keep it. It is $100 off at Costco now. It is also a little heavy (5 lb)

---

### Post by gogibby on 2012-11-07
I hope my post didn't discourage anyone- I was actually happily surprised by how well Ubuntu ran on it. Just personally, for what I wanted to use it for, the SSD was too small to attempt dual-booting, and I am sure that someone with a bit more experience with networking/wireless drivers could get the wireless working!

---

### Post by odror on 2012-11-07
> **gogibby said:**
> I hope my post didn't discourage anyone- I was actually happily surprised by how well Ubuntu ran on it. Just personally, for what I wanted to use it for, the SSD was too small to attempt dual-booting, and I am sure that someone with a bit more experience with networking/wireless drivers could get the wireless working!
You can have Best Buy replace the SSD for $50 without loosing the warranty.

---

### Post by j814wong on 2012-11-12
I hope someone, somewhere gets Ubuntu working on the Yoga.  It's a nifty device.

---

### Post by Mista Teaser on 2012-11-13
Has anybody tried these wifi drivers on the yoga?

[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized/165002#165002](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized/165002#165002)

---

### Post by yahooshua on 2012-12-13
You can get Ubuntu up and going on the Yoga [Lenovo 20175]. The problem is net access. Wifi doesn't work and no built-in RJ-45 (basic Ethernet jack). Need a USB to RJ-45 that will work with Ubuntu.

I used the Belkin F4U047. Which would overheat on Ubuntu (not Win8) and stop working off and on.

USB GigE that "just works" with Linux 2.6 kernels

Installing was pretty easy though. Turn off the comp, plug in your Ubuntu USB installer. Push the small button next to the power button in front with a pen/paperclip, choose to boot from USB. Then Install.

Touchscreen worked great. Seemed better than Win8. Especially with closing windows etc. with small areas. Pinching to zoom didn't work.

Multi-touch touch pad didn't seem to work. ex. 2 finger scroll. Scroll on right side of pad worked. Pinching, swiping from the the sides or top/bottom didn't do anything.

Display flipping didn't work at all. Fold into tablet mode, turn display upside down, this way that way, shake shake, nothing. Keyboard and touch pad should deactivate... nope.

Bluetooth can be turned on. But still showed disabled on setting window.???

Sure felt like being home after Win8 for a few months and glad to see it works as well as it does. Viva la Ubuntu!

---

### Post by Ashade on 2012-12-14
I installed ubuntu 12.04 amd64. I have been trying different versions but didn't reach to boot into 12.10 amd64, trying again right now. In my case, touchscreen is not recognized (I'll try to fix it later, as in a previous attemps it worked really well with i386), but the trackpad worked flawlessly, two fingers scroll and so on, I will try ndiskwrapper for the wifi and let you know. I think this laptop has a lot of potential for both Ubuntu or Hackintosh. I am open to any trials if anybody wants to cooperate.

---

### Post by odror on 2012-12-14
> **yahooshua said:**
> You can get Ubuntu up and going on the Yoga [Lenovo 20175]. The problem is net access. Wifi doesn't work and no built-in RJ-45 (basic Ethernet jack). Need a USB to RJ-45 that will work with Ubuntu.

I used the Belkin F4U047. Which would overheat on Ubuntu (not Win8) and stop working off and on.

USB GigE that "just works" with Linux 2.6 kernels

Installing was pretty easy though. Turn off the comp, plug in your Ubuntu USB installer. Push the small button next to the power button in front with a pen/paperclip, choose to boot from USB. Then Install.

Touchscreen worked great. Seemed better than Win8. Especially with closing windows etc. with small areas. Pinching to zoom didn't work.

Multi-touch touch pad didn't seem to work. ex. 2 finger scroll. Scroll on right side of pad worked. Pinching, swiping from the the sides or top/bottom didn't do anything.

Display flipping didn't work at all. Fold into tablet mode, turn display upside down, this way that way, shake shake, nothing. Keyboard and touch pad should deactivate... nope.

Bluetooth can be turned on. But still showed disabled on setting window.???

Sure felt like being home after Win8 for a few months and glad to see it works as well as it does. Viva la Ubuntu!

The other issue is that the laptop comes with 4 used partition. In order to install ubuntu side-by-side with w8. I had to cancel the w8 data partition. I open the laptop trying to change the HD to a larger ssd. I was not able to completely open it without risking it.

---

### Post by agklimit on 2012-12-15
Very useful experience... thanks guys for the info. I'd like the idea of Lenovo Yoga, but not at that price.

---

### Post by Ashade on 2012-12-15
> **Ashade said:**
> I installed ubuntu 12.04 amd64. I have been trying different versions but didn't reach to boot into 12.10 amd64, trying again right now. In my case, touchscreen is not recognized (I'll try to fix it later, as in a previous attemps it worked really well with i386), but the trackpad worked flawlessly, two fingers scroll and so on, I will try ndiskwrapper for the wifi and let you know. I think this laptop has a lot of potential for both Ubuntu or Hackintosh. I am open to any trials if anybody wants to cooperate.

I already added the second ssd. I can prepare a guide if you want. I already have taken the pictures. It's up to you, but it's really easy.

I added a disk with 256gb and partitioned it into two 128gb partitions. One of them holds ubuntu now.

---

### Post by odror on 2012-12-15
> **Ashade said:**
> I already added the second ssd. I can prepare a guide if you want. I already have taken the pictures. It's up to you, but it's really easy.

I added a disk with 256gb and partitioned it into two 128gb partitions. One of them holds ubuntu now.

Can you share your pictures or possibly a youtube video. I tried to open it, but I was not able to separate the back with light force. If the HD and memory can be upgraded. I will buy this laptop as soon as the WiFi driver become available for Linux.

---

### Post by Ashade on 2012-12-15
> **odror said:**
> Can you share your pictures or possibly a youtube video. I tried to open it, but I was not able to separate the back with light force. If the HD and memory can be upgraded. I will buy this laptop as soon as the WiFi driver become available for Linux.

I'm currently travelling but I'll try to make the tutorial tomorrow. I upgraded both of them, so now I have 128+256gb and 8gb of ram. The ram upgrade is pretty straightforward. The ssd upgrade is easy as well but it requires a little bit more of patient. The best way to open it is using a credit card or some rigid thin plastic.

Regarding the Wi-Fi, people has been working on that and looks like there is no driver yet, but I couldn't play a lot yet neither. Some people have talked about replacing the Wi-Fi card as an option which shouldn't be much more than 20 bucks.

As I said, I'll prepare something more elaborated tomorrow for reference.

---

### Post by alienoid on 2012-12-16
I have successfully installed Ubuntu 12.10 amd64 on the Yoga. Overall, the experience is positive: Touch screen is recognised and works well, touchpad with 2 button scroll and the overall laptop experience is good and snappy.

As stated by others, there are a few major issues:
1- WiFi is not recognised.
2- Bluetooth is disabled.
3- Screen does not rotate automatically. If you manually rotate the screen, the inputs are incorrectly mapped. Anyone had success with this? [http://cc.oulu.fi/~rantalai/synaptics/](http://cc.oulu.fi/~rantalai/synaptics/) Unfortunately, it is not available for 12.10 yet so I can't confirm.

For the Bluetooth and WiFi, anyone tried external USB cards?

Another issue with 12.10 is that there are random errors popping up. They are not critical but appear relatively frequently. I don't know what the cause is. I feel it has to do with the on-screen keyboard. The on-screen keyboard also gets stuck on a key at times.

Happy to help others moving this forward.

---

### Post by Ashade on 2012-12-16
> **alienoid said:**
> I have successfully installed Ubuntu 12.10 amd64 on the Yoga. Overall, the experience is positive: Touch screen is recognised and works well, touchpad with 2 button scroll and the overall laptop experience is good and snappy.

As stated by others, there are a few major issues:
1- WiFi is not recognised.
2- Bluetooth is disabled.
3- Screen does not rotate automatically. If you manually rotate the screen, the inputs are incorrectly mapped. Anyone had success with this? [http://cc.oulu.fi/~rantalai/synaptics/](http://cc.oulu.fi/~rantalai/synaptics/) Unfortunately, it is not available for 12.10 yet so I can't confirm.

For the Bluetooth and WiFi, anyone tried external USB cards?

Another issue with 12.10 is that there are random errors popping up. They are not critical but appear relatively frequently. I don't know what the cause is. I feel it has to do with the on-screen keyboard. The on-screen keyboard also gets stuck on a key at times.

Happy to help others moving this forward.

I am still working with Ubuntu in several ways... For the wifi, I am currently working with a shared connection on my Android phone. This worked since I plugged the phone on the computer. I am trying an Airlink 101 N150 and it is recognized but I am not able to get internet connection if a password is set up...

Another issue is the brightness. It does not work with the keys, but I got to change it through the terminal with this command:

xrandr --output LVDS1 --brightness 0.5

Still working on all of this. Will be posting updates.

EDIT:

To solve the brightness problem permanently:

sudo gedit /etc/default/grub

You will find this line in the new opened window:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
Change it to:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
Save and close the window and type this in the terminal:

sudo update-grub

and reboot. 

Found in: [http://www.techjail.net/solved-brightness-problem-in-ubuntu-12-04-precise-pangolin.html](http://www.techjail.net/solved-brightness-problem-in-ubuntu-12-04-precise-pangolin.html)

---

### Post by alienoid on 2012-12-16
Thanks Ashade! Confirming the fix for brightness works with 12.10.

---

### Post by alienoid on 2012-12-18
Regarding wifi and bluetooth, I have been trying to install the realtek driver for rtl8723 as described here [http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)

It seems this is the card installed in the Yoga even though the manual mentions rtl8732. So far, no success, even with the driver compatible with kernel 3.5. Continuing to work on it... If someone has had success, please let me know!

---

### Post by Ashade on 2012-12-19
> **alienoid said:**
> Regarding wifi and bluetooth, I have been trying to install the realtek driver for rtl8723 as described here [http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)

It seems this is the card installed in the Yoga even though the manual mentions rtl8732. So far, no success, even with the driver compatible with kernel 3.5. Continuing to work on it... If someone has had success, please let me know!

I tried them with the same result... Wi-Fi is not going to have an easy solution. I am going to play today a little bit more.

---

### Post by Ashade on 2012-12-19
> **Ashade said:**
> I'm currently travelling but I'll try to make the tutorial tomorrow. I upgraded both of them, so now I have 128+256gb and 8gb of ram. The ram upgrade is pretty straightforward. The ssd upgrade is easy as well but it requires a little bit more of patient. The best way to open it is using a credit card or some rigid thin plastic.

Regarding the Wi-Fi, people has been working on that and looks like there is no driver yet, but I couldn't play a lot yet neither. Some people have talked about replacing the Wi-Fi card as an option which shouldn't be much more than 20 bucks.

As I said, I'll prepare something more elaborated tomorrow for reference.

A link to the promised tutorial. :)

[http://forum.notebookreview.com/ideapad-essential/700890-lenovo-ideapad-yoga-upgrade-tutorial.html](http://forum.notebookreview.com/ideapad-essential/700890-lenovo-ideapad-yoga-upgrade-tutorial.html)

---

### Post by Triskite on 2012-12-22
I also made a walkthrough for opening her up. Mine includes how to fix the fan noise that afflicts many units.

Also keep in mind you can leave an SD//microSD permanently in the machine as it fits flush. You can get a 20mB r/w/s 64gB microSD on Amazon for $49. Great to store movies & TC volumes on.

[http://uselesspuzzles.blogspot.com/2012/11/how-to-fix-lenovo-yoga-fan-noise.html]("http://uselesspuzzles.blogspot.com/2012/11/how-to-fix-lenovo-yoga-fan-noise.html")

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ ~~~~~~~~~~~

check out my crowd-sourced 3d-printed tech accessories (most of them are your ideas) on my site:
techneesh.com
and lmk if you think of something new

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ ~~~~~~~~~~~

---

### Post by chrisdotcode on 2012-12-25
**[This post isn't quite yet complete. I just uploaded it in this almost-finished form so that people who are just getting the Yoga for the holiday season can have some sort of comphrehensive-ish reference. Merry Christmas Everybody!]**

So I am a proud owner of the Yoga, and I'd like to share some information with you guys.

**Wifi**

> **Mista Teaser said:**
> Has anybody tried these wifi drivers on the yoga?

[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized/165002#165002](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized/165002#165002)


I downloaded the Linux 3.8 kernel because I found out that they were adding RTL8723A support with a new patch (search either "rtk_btusb linux kernel" or "rtl8723a.bin" on google). It seems to be the bluetooth/wireless driver referenced from this question: [http://askubuntu.com/questions/212029/help-identifying-device-and-driver-for-0bda1724,]("http://askubuntu.com/questions/212029/help-identifying-device-and-driver-for-0bda1724") which Windows says the Yoga has (but it still might be an ethernet driver). I updated the Linux kernel to the latest nightly build, and it still didn't work for me, but I still have hope that I just did something wrong, and the solution is in fact there. I've attached the source for what seems the be the driver, but I couldn't compile it. Maybe somebody smarter than I can evaluate the situation.

**Touch Screen**

The touchscreen works flawlessly, and with a firefox addon or two (grab and drag), it works really well in stand mode.

Multi-touch doesn't seem to work. Thanks to this link (find phoronix article), we can see that we'll get kernel-level support for multitouch in 3.8 ...Or do we already have it?

Unity supports gestures, actually. And already, out of the box, 3-finger tap works. If you three-finger tap any open window in Unity, it switches to resize/move mode, and you can move things around. I don't know if any other gestures  work, because I haven't tried any other ones. Let me know of your progress if you guys try this.

 But wait, there's more! Either we've always supported multitouch, or Ubuntu has backported the hid-multitouch (find source link) drivers from the 3.8 kernel, because we *do* in fact have true, ten-finger support. I've included a shell script that does the following, but this is what you do to test it all:

1. Download the *amazing* mtdiag from ENAC:
```
$ cd /tmp
$ git clone git://git.lii-enac.fr/linux-input/mtdiag.git
```2. Download dependencies:
(Ubuntu doesn't defaultly come with aptitude, so if you don't have it, install it using the method they recommend)
```
$ sudo aptitude install python-tk tix
```3. Go to its directory, and run it
```
$ cd mtdiag
$ sudo ./mtdiag.sh
```(WARNING: this won't run properly if you've changed your default color configuration (and/or default shell). I tested this earlier and got it working, but doesn't seem to work on my zsh solarized configurations. If you're a standard Ubuntu user, this should work fine.)

4. After running this program, you will be presented with two options to "activate". Like I said, I can't run it anymore, so I can't tell you which one, but I think it says something like "touchscreen" in the name or something. Figure it out and let me know so I can update this documentation, guys.

5. After choosing the correct touchscreen, touch away!

6. You might notice that the screenpoints are mis-calibrated. That's because you need to hit "fullscreen" and then, voila! Full ten-finger touch like magic on Linux Kernel 3.5 (WARNING: On Unity (and maybe other Window Managers,) holding and dragging with all ten fingers (at least with all ten fingers, but I didn't try any other possible combinations of fingers) can make your machine freeze or lag or do other strange things.

So yes, we have full ten-finger touch support on Linux Kernel 3.5 and Ubuntu!

The reason that it doesn't seem to work with most applications is because they just don't support it. TFT is brand spanking new, and so it would make sense that your favorite application wouldn't have support for it just quite yet. Opera Mobile, for web browsing, would have worked great (and has a fantastic on-screen keyboard) ...but the version I found crashed instantly, because the desktop version is technically discontinued.

**Laptop Modes**

There's *partial* support for modes. When going past 180 degrees, the keyboard is disabled sometimes, and sometimes it's not. The trackpad is *always* operational, however. Keys *do* get stuck from time to time, but *only* in non-laptop mode.

I really wish this issue was *fully* resolved, because it's impractical to switch between modes, scared of accidentally triggering either the touchpad or keys and having to fiddle with the unwieldy USB wifi dongle I have attached at the side to get it folded.

Also, Linux needs more touchscreen software, but that's an issue that can only be solved with time.

**Battery Life**

Battery Life is... pathetic. I get around 3 hours and 15 minutes from full, non-stop youtube/torrenting (Ubuntu torrents, don't worry ;) ). Advertised is 8, but the realistic trend has been said to be 5 and a half. What gives?

**Booting / Virtualization**

Booting works fine after disabling EFI. Virtualization also works fine after enabling something from the BIOS (don't quite remember what it was). 

**Brightness**

> **Ashade said:**
> I am still working with Ubuntu in several ways...  For the wifi, I am currently working with a shared connection on my  Android phone. This worked since I plugged the phone on the computer. I  am trying an Airlink 101 N150 and it is recognized but I am not able to  get internet connection if a password is set up...

Another issue is the brightness. It does not work with the keys, but I got to change it through the terminal with this command:

xrandr --output LVDS1 --brightness 0.5

Still working on all of this. Will be posting updates.

EDIT:

To solve the brightness problem permanently:

sudo gedit /etc/default/grub

You will find this line in the new opened window:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
Change it to:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
Save and close the window and type this in the terminal:

sudo update-grub

and reboot. 

Found in: [http://www.techjail.net/solved-brightness-problem-in-ubuntu-12-04-precise-pangolin.html](http://www.techjail.net/solved-brightness-problem-in-ubuntu-12-04-precise-pangolin.html)

Brightness works fine after the fix suggested. On MATE, there was some more problems, but nothing I couldn't fix by fiddling with the Power Management options in the preferences.

**Touchpad / Gestures**

On Linux Mint, the touchpad sucks. ...Ubuntu, for some reason fixes the jumpy touchpad to a much more sane level. After some adjustments to my own preferences, it works decently. Two-finger touch works nicely as well. Oddly enough 4+ finger scrolling also works, but not three-finger scrolling. Maybe three-fingers on the touchpad has another meaning?


**Other issues:**

Some of the keypad buttons don't work, like the "disable touchpad" function key. Also, the button on the right side of the device doesn't work. SD slot works, but I haven't got a chance to test HDMI yet.

> **odror said:**
> You can have Best Buy replace the SSD for $50 without loosing the warranty.

I don't believe this is true. According to [http://forums.lenovo.com/t5/IdeaPad-IdeaTab-Slate-Tablets/Yoga-13-mSata-storage-limit/td-p/907267/page/2](http://forums.lenovo.com/t5/IdeaPad-IdeaTab-Slate-Tablets/Yoga-13-mSata-storage-limit/td-p/907267/page/2)  , only one person says that it voids it, and they don't work for Lenovo  nor Microsoft. Everyone else says that there are no warranty stickers or  anything like that, plus there's a whole other SSD slot on the inside,  so I'm thinking it won't void your warranty. Granted, none of that comes  from Lenovo themselves, so modify your system at your own risk.

Hope all this helped! :D

---

### Post by Ashade on 2012-12-27
Thank you very much chrisdotcode I am going to try these codes during the evening and will come back with some feedback.

---

### Post by chrisdotcode on 2012-12-27
> **Ashade said:**
> Thank you very much chrisdotcode I am going to try these codes during the evening and will come back with some feedback.

 When you come back, can you also tell me your battery life? Hopefully 3 hours isn't the norm, and mine is just defective in someway. Because I really do love this machine.

---

### Post by Ashade on 2012-12-28
> **chrisdotcode said:**
> When you come back, can you also tell me your battery life? Hopefully 3 hours isn't the norm, and mine is just defective in someway. Because I really do love this machine.

I don't use Ubuntu yet as my regular OS but I get easily more than 5h out of this thing with Windows 8. I'm very happy with its performance. 

I'm being a little bit lazy these days as I've gotten a nexus 10. Give me some more days to try your advances.

---

### Post by chrisdotcode on 2012-12-29
Can anyone else who uses a Linux tell me if they get anything more than 3 hours with this thing?

---

### Post by a3n1ma on 2013-01-07
> **chrisdotcode said:**
> Can anyone else who uses a Linux tell me if they get anything more than 3 hours with this thing?

I'll be installing ubuntu on it within the next few days. I'll let you know how long it lasts then.

Still sad about the wireless no driver issue tho.

---

### Post by crawnDg on 2013-01-08
I ordered a Yoga 13 today and will post my battery results with linux as well.

---

### Post by jordi62 on 2013-01-31
I have too a Lenovo Yoga 13, I have write to Realtek and they have emailed to me 2 drivers   p, li { white-space: pre-wrap; }  rtl8723A_WiFi_linux_v4.1.3_6044.20121224 and 8723AE_8723AU_Linux_BT_20121109_v35 I will try later.


You see the wifi driver is rtl8723A,  here is reported that it works [http://askubuntu.com/questions/212029/help-identifying-device-and-driver-for-0bda1724](http://askubuntu.com/questions/212029/help-identifying-device-and-driver-for-0bda1724)


Jordi

---

### Post by odror on 2013-01-31
> **jordi62 said:**
> I have too a Lenovo Yoga 13, I have write to Realtek and they have emailed to me 2 drivers   p, li { white-space: pre-wrap; }  rtl8723A_WiFi_linux_v4.1.3_6044.20121224 and 8723AE_8723AU_Linux_BT_20121109_v35 I will try later.


You see the wifi driver is rtl8723A,  here is reported that it works [http://askubuntu.com/questions/212029/help-identifying-device-and-driver-for-0bda1724](http://askubuntu.com/questions/212029/help-identifying-device-and-driver-for-0bda1724)


Jordi
Is the driver working with no problems?

---

### Post by jordi62 on 2013-02-01
> **odror said:**
> Is the driver working with no problems?

I have not tested yet, I will try on the week end, but it is reported in the link that works.


[http://askubuntu.com/questions/212029/help-identifying-device-and-driver-for-0bda1724](http://askubuntu.com/questions/212029/help-identifying-device-and-driver-for-0bda1724)

Jordi

---

### Post by nago on 2013-02-06
Excellent thread, thank you all for the phenomenal detective work.

I can confirm on my Lenovo Yoga 13 (8GB, 128GB) that these WiFi drivers did the trick.

Note, you have to move them / rename the folders they come in such that there are no spaces in the path. Try moving them to ~/rtek for instance-- from there, using make/make install worked wonders. You may need to run ./make_drv to choose which driver to build/use prior to the make/make install -- I wound up compiling and installing both.

Make sure you keep these wifi drivers handy, as every time you update your kernel via regular updates you're going to need them again ...

Edit: Since I haven't seen another good Lenovo Yoga thread on these forums, I should elaborate on my setup:
I purchased the 128GB model, but upgraded manually to a crucial 256GB. I cloned the 128 over to the 256 and then swapped the disks -- This broke windows. I was unable to use any of the built-in recovery tools successfully to repair the installation, but performing a new installation from disc (using a USB cd rom) worked without having to re-enter a key-- W8 recognized the Lenovo/OEM info. I then installed my drivers/programs from the former D:\Lenovo partition to get everything working again.

I then installed Ubuntu 12.10 onto HDD1, the 128GB. The installation worked, but linux was unable to boot successfully -- it couldn't find the root filesystem. I unplugged my 256gb leaving the 128 in the second slot (hdd1) and reinstalled ubuntu. I then plugged the 256gb back in and now I can switch back and forth between W8 and Ubuntu by using the bios button on the Yoga to choose between the two drives at boot time.

I have left Intel Rapid Start, UEFI and secure boot enabled, and everything appears to be working great! The rapid start in particular is still functioning well with windows -- I have startup times of about 4 seconds from a cold boot.

If anyone was interested in a similar setup -- Yes, it can be done. Great machine so far, even if UEFI/GPT and so forth is a little more of a headache than MBR used to be.

---

### Post by chrisdotcode on 2013-02-07
When I try to make either the packaged wifi or bluetooth drivers, I keep getting this error:  

(wifi error): 
cp: target `driver/rtlwifi/include/autoconf.h' is not a directory
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.5.0-17-generic/build M=/home/cdc/Downloads/RTL8723AS-VAU linux driver/rtlwifi  modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
make[1]: *** No rule to make target `linux'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'
make: *** [modules] Error 2


(bluetooth error):
cp -f rlt8723a_chip_b_cut_bt40_fw_asic_rom_patch-svn8521-0x00203499-20121106-LINUX_USB_NOLPS.bin /lib/firmware/rtk8723a
make -C blutooth_usb_driver -s
make[2]: *** No rule to make target `linux'.  Stop.
make[1]: *** [all] Error 2
make: *** [install] Error 2



So apparently, I'm missing something, most likely a dependency. I'm on Linux Mint, if that makes any difference.

---

### Post by nago on 2013-02-07
> **chrisdotcode said:**
> When I try to make either the packaged wifi or bluetooth drivers, I keep getting this error:  

(wifi error): 
cp: target `driver/rtlwifi/include/autoconf.h' is not a directory
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.5.0-17-generic/build M=/home/cdc/Downloads/RTL8723AS-VAU linux driver/rtlwifi  modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
make[1]: *** No rule to make target `linux'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'
make: *** [modules] Error 2


(bluetooth error):
cp -f rlt8723a_chip_b_cut_bt40_fw_asic_rom_patch-svn8521-0x00203499-20121106-LINUX_USB_NOLPS.bin /lib/firmware/rtk8723a
make -C blutooth_usb_driver -s
make[2]: *** No rule to make target `linux'.  Stop.
make[1]: *** [all] Error 2
make: *** [install] Error 2



So apparently, I'm missing something, most likely a dependency. I'm on Linux Mint, if that makes any difference.

See my post above: You have to move these drivers out of the folders they come in, because it can't tolerate spaces in the path.

---

### Post by chrisdotcode on 2013-02-07
Excellent! Thank you!

Can you also comment on your battery life? I get about anything from 3-4, from a heavy system load, to a light one that plays music on and off again.

---

### Post by SargTeX on 2013-02-08
Hey people...

I just installed Ubuntu on my Lenovo Yoga 13 (Germany) and can't get the wifi driver to work.

I followed the steps mentioned @ askubuntu and tried both specified drivers, the first one as well as the suggested driver for linux kernel version 3.5, but it didn't work!

There was no error message. I tried "modprobe r8723e" after both installations and it didn't say anything.

uname -r = 3.5.0-23-generic

Best greetings,
SargTeX

/EDIT: Unfortunately, as I didn't use it much, I can't tell you anything about the battery life. As far as I can calculate (via battery life and percentage) it also makes around 3 hours at my yoga, although the battery survives for nearly 6h under windows 8.

---

### Post by nago on 2013-02-08
> **chrisdotcode said:**
> 
Can you also comment on your battery life? I get about anything from 3-4, from a heavy system load, to a light one that plays music on and off again.

Sorry, I haven't really "tried it out" yet. I know in my dual boot environment I'm getting about 6 hours in Windows 8, but I haven't run out the battery working in Linux just yet, because I'm usually coding at a desk with it plugged in...

I could try to just play a movie or something and see how long I'd get. I'll reply back when I have a number for you.

Edit: Off of a full charge, I opened up the Steam game "The Polynomial." I let it run until my machine bottomed out, I got two hours even. [http://dmytry.com/games/](http://dmytry.com/games/)

---

### Post by nago on 2013-02-08
> **SargTeX said:**
> 
I just installed Ubuntu on my Lenovo Yoga 13 (Germany) and can't get the wifi driver to work.


Heya, make sure you grab the drivers linked on that askubuntu thread: [http://www.mediafire.com/?sanq19s3vv1d9c9](http://www.mediafire.com/?sanq19s3vv1d9c9)

Extract and then extract: "rtl8723A_WiFi_linux_v4.1.3_6044.20122124.tar.gz"

Move the folder "rtl8723A_WiFi_linux_v4.1.3_6044.20121224" to something more manageable like ~/rtek_wifi/ -- make sure you get rid of spaces in the filename.

you should be able to run the following as root:
```
# make clean
# ./make_drv RTL8723as-vau
# make
# make install
# modprobe 8723au
```

You should now have WiFi!

---

### Post by PatheticMoFo on 2013-02-08
KDE user here, I get about 5-6 hours on a normal load with about 80% brightness. I use the laptop in lectures, for browsing, and some light computational work.

BTW, thanks to all those other posts on getting Wi-Fi working -- it really helped and I've got Wi-Fi on my awesome new Yoga! :D

---

### Post by sv0101 on 2013-02-09
Hey guys,

great that the wifi-driver seems to work on the Yoga 13. :D
I really want to get the Lenovo Yoga 11s  - it will be available in summer 2013. 

What would you gess: Will these tricks also help von the 11s to get the wifi-driver working? Seems to be the same i5-processor. But same wifi-card? 
I really dont want a convertible notebook just with an working Windows 8, cause i need Linux (Ubuntu or Mint) for studies.

Thanks for your replies and greets from Berlin, Germany.

---

### Post by Iakouben on 2013-02-11
Hey guys, I have a lenovo 13 and I'm planning to put 8 Gigs RAM and I just would like to make sure that it's compatible.

[http://www.amazon.co.uk/Crucial-SODIMM-1-35V-Memory-Module/dp/B008PSL89Q/ref=lh_ni_t?ie=UTF8&psc=1](http://www.amazon.co.uk/Crucial-SODIMM-1-35V-Memory-Module/dp/B008PSL89Q/ref=lh_ni_t?ie=UTF8&psc=1)

And I must say it was one hell of a thread!

---

### Post by nago on 2013-02-12
1) I don't think there's any way of knowing if it will use the same WiFi chipset or not. It's entirely possible, but you'll have to wait and see. Worst case scenario, you have to email the chipset vendor for linux drivers -- which worked out well for Yoga 13 owners :)

2) I think the Yoga 13 has only one memory slot, so I wouldn't get this. Data spec sheet says "Up to 8GB DDR3L – 1600Mhz memory ( [1 SODIMM slot
(1x2GB/1x4GB/1X8GB)];"

---

### Post by odror on 2013-02-12
> **nago said:**
> 1) I don't think there's any way of knowing if it will use the same WiFi chipset or not. It's entirely possible, but you'll have to wait and see. Worst case scenario, you have to email the chipset vendor for linux drivers -- which worked out well for Yoga 13 owners :)

2) I think the Yoga 13 has only one memory slot, so I wouldn't get this. Data spec sheet says "Up to 8GB DDR3L – 1600Mhz memory ( [1 SODIMM slot
(1x2GB/1x4GB/1X8GB)];"

Do you know of any tutorial that shows how to open this laptop and replace the disk and the memory. I tried to open it myself. It would not open from the back. I did not want to be forceful.

---

### Post by alek66 on 2013-02-13
REALLY LOOKING FORWARD to get a yoga 11 and install linux on it.

---

### Post by alek66 on 2013-02-14
I am planning to buy a yoga 11, how does ubuntu works? are there some limitataion?

---

### Post by Triskite on 2013-02-15
> **odror said:**
> Do you know of any tutorial that shows how to open this laptop and replace the disk and the memory. I tried to open it myself. It would not open from the back. I did not want to be forceful.

here's one I made:
[uselesspuzzles.blogspot.com/2012/11/how-to-fix-lenovo-yoga-fan-noise.html]("uselesspuzzles.blogspot.com/2012/11/how-to-fix-lenovo-yoga-fan-noise.html")

---

### Post by zafu on 2013-02-16
Hi,

I've successfully setup Linux with wifi and touchscreen support on my Yoga13 thanks to you guys. Thanks a lot for posting.

One thing remains: middle click support. I used to click both mouse buttons (equivalent to middle click) to paste the X11 select buffer. But on the Yoga I can't seem to click on both sides of the trackpad simultaneously.

How can I paste the selection buffer in GUI applications (in xterms Shift+Insert works fine)?

[LATER]

I found the answer: two finger tap on the trackpad.

---

### Post by jordi62 on 2013-02-17
Hi,

I have success with the wifi, but I can not make work the bluetooth.

You have success with the bluetooth?

I need help

Thanl you.

Jordi

---

### Post by andremfp29 on 2013-02-17
I'm realy struggling with the instalation of the wifi driver. tried everything you guys said above but I can't get this done. can anyone post a step-by-step guide or something?
as you can see I'm new at this.

tanks

---

### Post by RugbyPlayer on 2013-02-18
Im having some trouble trying to remove an Ubuntu install. I am doing so because i partitioned my disks wrong, i ended up completely shrinking my windows drive to minimum instead of the ubuntu size. I deleted the partitions, expanded my windows one to fill the space.

Booted from my usb recovery stick, ran command prompt and did bootrec /fixmbr

I also ran bcdedit from windows 8 and it did not show a ubuntu partition anywhere. However when i boot with the yoga button it still shows me 2 ubuntu options. Also these boot option appear in my BIOS under the boot priority order.

On a side note just after installing ubuntu the bootloader would not let me boot into windows when selected and im not sure why.

I fixed that by changing the boot order to windows first, and then just using the yoga button if i wanted to get into ubuntu but this was rather cumbersome. Any help is greatly appreciated

---

### Post by andremfp29 on 2013-02-18
Just managed to install de drivers! They work!

Thanks

---

### Post by RugbyPlayer on 2013-02-21
> **nago said:**
> Heya, make sure you grab the drivers linked on that askubuntu thread: [http://www.mediafire.com/?sanq19s3vv1d9c9](http://www.mediafire.com/?sanq19s3vv1d9c9)

Extract and then extract: "rtl8723A_WiFi_linux_v4.1.3_6044.20122124.tar.gz"

Move the folder "rtl8723A_WiFi_linux_v4.1.3_6044.20121224" to something more manageable like ~/rtek_wifi/ -- make sure you get rid of spaces in the filename.

you should be able to run the following as root:
```
# make clean
# ./make_drv RTL8723as-vau
# make
# make install
# modprobe 8723au
```

You should now have WiFi!
I cant get these drivers to install. i have followed all the instructions. 

The path name as is right now is name@name-Lenovo-IdeaPad-Yoga-13:/~rtek_wifi 

when i do make clean is seems to do something but idk what.
it gives me a bunch of cd and rm print outs to the screen. when i do ./make_drv RTL8723-vau it says "You have selected RTL8723-vau" "Unknown NIC type


if i do just ./make_drv it gives me two options so i hit 1 which is RTL8723as-vau it says "You have selected RTL8723as-vau" "rtw_version.h has existed!"

now when i do make

it gives me

make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.5.0-17-generic/build M=/home/name/rtek_wifi modules

make: ***/lib/modules3.5.0-17-generic/build: No such file or directory. Stop.
make: *** [modules] Error 2"

Sorry if there is mis-spellings or anything as i had to type this all in here on my laptop seeing as how i dont have wifi on my yoga!

---

### Post by chauveau on 2013-02-21
> **RugbyPlayer said:**
> 
make: ***/lib/modules3.5.0-17-generic/build: No such file or directory. Stop.
make: *** [modules] Error 2"


you need to install the linux header files for your current kernel (linux-headers-3.5.0-17)
you can find the debian package here:
[http://packages.ubuntu.com/fr/quantal/linux-headers-3.5.0-17-generic](http://packages.ubuntu.com/fr/quantal/linux-headers-3.5.0-17-generic)

---

### Post by RugbyPlayer on 2013-02-21
> **chauveau said:**
> you need to install the linux header files for your current kernel (linux-headers-3.5.0-17)
you can find the debian package here:
[http://packages.ubuntu.com/fr/quantal/linux-headers-3.5.0-17-generic](http://packages.ubuntu.com/fr/quantal/linux-headers-3.5.0-17-generic)

i downloaded this file and linux is saying it is already installed

---

### Post by chauveau on 2013-02-21
> **RugbyPlayer said:**
> i downloaded this file and linux is saying it is already installed

we need the 2 packages  [linux-headers-3.5.0-17]("http://packages.ubuntu.com/fr/quantal/linux-headers-3.5.0-17") and [linux-headers-3.5.0-17-generic]("http://packages.ubuntu.com/fr/quantal/linux-headers-3.5.0-17-generic")

if they are well installed both, that's strange (/lib/modules/3.5.0-17-generic/build is supposed to be a symbolic link to /usr/src/linux-headers-3.5.0-17-generic)

---

### Post by RugbyPlayer on 2013-02-21
> **chauveau said:**
> we need the 2 packages  [linux-headers-3.5.0-17]("http://packages.ubuntu.com/fr/quantal/linux-headers-3.5.0-17") and [linux-headers-3.5.0-17-generic]("http://packages.ubuntu.com/fr/quantal/linux-headers-3.5.0-17-generic")

if they are well installed both, that's strange (/lib/modules/3.5.0-17-generic/build is supposed to be a symbolic link to /usr/src/linux-headers-3.5.0-17-generic)

on the second link do i use the amd64 for a 64 bit intel chip? the i386 is only for 32 bit architecture it seems

---

### Post by chauveau on 2013-02-21
> **RugbyPlayer said:**
> on the second link do i use the amd64 for a 64 bit intel chip? the i386 is only for 32 bit architecture it seems

yes amd64 indeed

---

### Post by RugbyPlayer on 2013-02-21
> **chauveau said:**
> yes amd64 indeed

using that file if i do dpkg -l then the file name it is telling me "no packages found matching linux-headers-3.5.0-17-generic_3.5.0-17_amd64.deb

---

### Post by chauveau on 2013-02-21
> **RugbyPlayer said:**
> using that file if i do dpkg -l then the file name it is telling me "no packages found matching linux-headers-3.5.0-17-generic_3.5.0-17_amd64.deb

dpkg **-i**  PACKAGE_FILE_NAME   to install a package man!  ;)

---

### Post by RugbyPlayer on 2013-02-21
indeed it is, fonts appear weird sometimes ;) forgive the linux amateur

---

### Post by veoozo on 2013-02-21
I'm pretty noobish when it comes to this kind of stuff. I seriously don't get how you fix wifi. I've been trying for hours to do what the posts are saying, but I just don't get it! Could someone please explain the process of getting wifi on my Yoga like you're talking to a 10 year old? I am currently trying to do this with Linux Mint 14. When I install Ubuntu, there are too many bugs. But it's essentially the same. Thanks!

---

### Post by RugbyPlayer on 2013-02-21
I'm having a significant amount of trouble getting ubuntu installed on my Yoga. I am constantly and i mean constantly having issues with booting. Does anyone a have a step by step guide on how to properly install it on the yoga?

---

### Post by veoozo on 2013-02-21
To install Ubuntu on your Yoga, you will need three things. The first is a USB flash drive that is at least 2GB. The second is the Unetbootin software (link: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)). The third is the Ubuntu 12.10 64 bit download. Step 1 is to plug in your flash drive and do a quick format. To do this, go to My Computer and right click on your drive. Click on "Format". A box will pop up, and under "File System", and "Allocation Unit Size" make sure the defaults are selected. Also, make sure "Quick format" is selected. Then, go ahead and click "start". Click "OK" when prompted. Next, open the Unetbootin software. Select "Diskimage" when it opens. Next to "ISO", click the three dot button and browse your computer for the Ubuntu 12.10 64 bit download. Leave the space alone where it says "Space used to preserve .....", as you do not need to do anything there. Where it says "Drive", make sure your flash drive is selected. Then click "OK". It will proceed to create the drive. When it is done, exit the program. Don't click "Reboot Now". Go and SHUT DOWN your Yoga. Once it is off, find a pin and click the Nova button (it's the small button to the left of the power button). When the menu comes up with four options, click "Boot Menu". Then select the "USB" boot option. Proceed with install. Be patient! Follow the install directions carefully. Choose the option to run Ubuntu alongside Windows 8. When the partition option comes up, give Ubuntu at least 10GB. Then, proceed with installation and you're done! Everytime you want to boot up Ubuntu, you will need to shut down the computer and press the Novo button and select the "Boot Menu" button. I know, it sucks.

Wifi doesn't work and there are some other quirks. Does anyone know how to get wifi up and running?

---

### Post by RugbyPlayer on 2013-02-21
> **veoozo said:**
> To install Ubuntu on your Yoga, you will need three things. The first is a USB flash drive that is at least 2GB. The second is the Unetbootin software (link: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)). The third is the Ubuntu 12.10 64 bit download. Step 1 is to plug in your flash drive and do a quick format. To do this, go to My Computer and right click on your drive. Click on "Format". A box will pop up, and under "File System", and "Allocation Unit Size" make sure the defaults are selected. Also, make sure "Quick format" is selected. Then, go ahead and click "start". Click "OK" when prompted. Next, open the Unetbootin software. Select "Diskimage" when it opens. Next to "ISO", click the three dot button and browse your computer for the Ubuntu 12.10 64 bit download. Leave the space alone where it says "Space used to preserve .....", as you do not need to do anything there. Where it says "Drive", make sure your flash drive is selected. Then click "OK". It will proceed to create the drive. When it is done, exit the program. Don't click "Reboot Now". Go and SHUT DOWN your Yoga. Once it is off, find a pin and click the Nova button (it's the small button to the left of the power button). When the menu comes up with four options, click "Boot Menu". Then select the "USB" boot option. Proceed with install. Be patient! Follow the install directions carefully. Choose the option to run Ubuntu alongside Windows 8. When the partition option comes up, give Ubuntu at least 10GB. Then, proceed with installation and you're done! Everytime you want to boot up Ubuntu, you will need to shut down the computer and press the Novo button and select the "Boot Menu" button. I know, it sucks.

Wifi doesn't work and there are some other quirks. Does anyone know how to get wifi up and running?

this isnt at all the trouble that i am having. It is grub, when i just install alongside as you noted using my install disks (i used a burned .iso disk) everytime i boot up it sends me to the grub menu. And grub does not seem to automatically fill the correct paths to boot into windows. I want to just use grub to control all of my booting not the novo button. I cant boot into windows at all now

---

### Post by veoozo on 2013-02-21
> **RugbyPlayer said:**
> this isnt at all the trouble that i am having. It is grub, when i just install alongside as you noted using my install disks (i used a burned .iso disk) everytime i boot up it sends me to the grub menu. And grub does not seem to automatically fill the correct paths to boot into windows. I want to just use grub to control all of my booting not the novo button. I cant boot into windows at all now
Oh. Well, the only way that I have found that works is the Novo button. Try to get Windows back up and running and then delete the Ubuntu volume and merge the two partitions together and then start over. Use my instructions (including the USB stick), and then go from there.

---

### Post by veoozo on 2013-02-22
Come on, nobody? All I need is a walkthrough on how to fix wifi!

---

### Post by veoozo on 2013-02-23
Someone? Anyone?

---

### Post by Drl123 on 2013-02-23
Email Realtek (wlanfae@realtek.com) and ask for their linux driver.  They emailed me back within 1 business day.  After building and installing their driver (and rebooting) my wifi works great.  Although it comes with a BT driver too, that doesn't seem to work. 

I'd upload the file here but it is too large for the forum (~2MB).  You can try searching for the file named 'RTL8723AS-VAU linux driver.zip'.

Only downside is that you have to keep reinstalling it when they update the linux headers, but a small price to pay.

---

### Post by veoozo on 2013-02-23
> **Drl123 said:**
> Email Realtek (wlanfae@realtek.com) and ask for their linux driver.  They emailed me back within 1 business day.  After building and installing their driver (and rebooting) my wifi works great.  Although it comes with a BT driver too, that doesn't seem to work. 

I'd upload the file here but it is too large for the forum (~2MB).  You can try searching for the file named 'RTL8723AS-VAU linux driver.zip'.

Only downside is that you have to keep reinstalling it when they update the linux headers, but a small price to pay.
Thanks! I already have that .zip (it's 1.80MB), but I have no idea how to install it. Could you please explain to me how to install it?

---

### Post by Drl123 on 2013-02-23
> **veoozo said:**
> Thanks! I already have that .zip (it's 1.80MB), but I have no idea how to install it. Could you please explain to me how to install it?

unzip each driver into its own folder.  navigate to the folders one at a time in terminal and type  sudo make install.  when done, reboot and your wireless should work.  The bluetooth one did not work, but the wifi one works fine.

PS...my zip has two archives (one for BT one for WiFi) and a readme file that explains how to build the drivers.  They did not include the install script that the readme talks about, so you have to build it, but it is simple.

---

### Post by veoozo on 2013-02-23
I'm sorry, but I still don't get it! I usually understand Linux very well, but for some reason I just don't get this. Can you quickly go over this in like baby steps? And include what everything is and EXACTLY what to type? (For example, when I type make clean in terminal I get an error, so I need specifics). Thanks-

---

### Post by Drl123 on 2013-02-24
> **veoozo said:**
> I'm sorry, but I still don't get it! I usually understand Linux very well, but for some reason I just don't get this. Can you quickly go over this in like baby steps? And include what everything is and EXACTLY what to type? (For example, when I type make clean in terminal I get an error, so I need specifics). Thanks-

OK, I will try.  Just re-reading the pdf and explaining as I type since I did it some time ago.

1. download the zip
2. open zip with archive mgr
3. zip should contain three files (8723AE....BT...v35.rar, rtl8723A_WiFi....tar.gz, Quick_start...pdf)
4. create a folder in Home called rtl8723A and extract the ...WiFi archive into that folder.
5. run the make_drv script (the step I forgot because you only do this the first time...when reinstalling, you just do make install) with ./make_drv.
6. this script gives two options to choose from, I selected #1 (RTL8192cu)...note that the 8192 driver contains the 8723 driver files too.
7. type ./make (note - the script may do steps 7 & 8 for you, can't recall exactly)
8. when that finishes do make install (note, you may need to prefix make and make install with sudo)
9. after installs, reboot and wireless should work.

Anytime you get an update to the kernel/headers from Ubuntu, you will need to reinstall the driver.  Just open a terminal and cd to the rtl8723A directory and type sudo make install, then reboot and it will work again. (no need to re-make the files or run scripts).

I was able to install the bluetooth driver, but I was never able to get it to do anything.  BT will enable but you can't add devices and devices don't see the computer.  I have to use a USB BT adapter when I need BT. :-(

---

### Post by veoozo on 2013-02-24
When  I extract it into the folder and run make_drv in a terminal, it gives me two options (1) RTL8723as-vau and 2) RTL8723as). When I choose either one, it displays something but goes away before I can read it. What do I do?

---

### Post by Drl123 on 2013-02-24
did you run it from a terminal session or double-click from the file manager?  If in a terminal (the way you should do it), the window should stay open and the text visible.

Try rebooting to see if it installed.  If not, open terminal and navigate to that directory and do a make install and reboot when it is done.  As I mentioned before, it has been a while since I did this and I can't remember if the script installs the driver or just builds it.

You will have to reboot for it to take effect regardless.

---

### Post by RugbyPlayer on 2013-02-25
this was working yesterday, and it randomly stopped, the wifi no longer works. I tried going through the whole installation process again but now I keep getting this error:
 
RCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.5.0-25-generic/build M=/home/usr/rtl  modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make: *** [modules] Error 2

---

### Post by Drl123 on 2013-02-25
does your folder name have a space in it "rtl modules"?  I know it doesn't like directory names with spaces.  Try renaming if that is the case.  Otherwise, I'm afraid I won't be much help as I'm not a Linux expert by any means.

What happened to your machine between when it worked and when it didn't work anymore?  Did anything update software in between?

---

### Post by RugbyPlayer on 2013-02-25
> **Drl123 said:**
> does your folder name have a space in it "rtl modules"? I know it doesn't like directory names with spaces. Try renaming if that is the case. Otherwise, I'm afraid I won't be much help as I'm not a Linux expert by any means.
 
What happened to your machine between when it worked and when it didn't work anymore? Did anything update software in between?
 
 
no the folder name is just rtl
 
and yes I let Ubuntu update which apparently is a bad idea. this driver needs to be supported better. if you cant even install the driver after performing updates then its a broken driver no ifs ands or buts about it

---

### Post by chauveau on 2013-02-25
> **RugbyPlayer said:**
> this was working yesterday, and it randomly stopped, the wifi no longer works. I tried going through the whole installation process again but now I keep getting this error:
 
RCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.5.0-25-generic/build M=/home/usr/rtl  modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
make: *** [modules] Error 2

Now it looks that you need the header for the kernel 3.5.0-25, you updated your system (kernel) that's why.
So you need to install the following package: [linux-headers-3.5.0-25]("http://packages.ubuntu.com/fr/quantal/linux-headers-3.5.0-25") and [linux-headers-3.5.0-25-generic]("http://packages.ubuntu.com/fr/quantal/linux-headers-3.5.0-25-generic")
Reboot and select an older kernel version in GRUB, the wifi driver will still work here and you will be able
to install these package using apt-get

Re-do the full compiling procedure (when you are using the new kernel):
```
make clean
./make_drv RTL8723as-vau
make
sudo make install

```the module will be loaded automatically after reboot, but you can load it immediately by hand :
```
sudo modprobe 8723au
```If you update again the kernel, after rebooting into the new kernel, the wifi will not work again, it is like that!
So we ALL have to re-do this compiling procedure at this stage.

The problem you had here, I guess, is that the kernel update by ubuntu did not download also the header for the new kernel,
may be because you installed it manually. Normally the package linux-headers-generic is supposed to do that. 

I wonder if the full desinstallation/reinstallation can fix that : ```

sudo apt-get purge linux-headers-generic
sudo apt-get install linux-headers-generic
```We will see that on the next kernel update..

---

### Post by klingo on 2013-03-01
hello guys, so what is the situation with the wifi ? Has anybody a working wifi on yoga currently ?

---

### Post by liquidator87 on 2013-03-01
The wifi works great for me, using the method found in this thread. Anyone has a good script to rotate the touchscreen in portrait mode?

---

### Post by klingo on 2013-03-02
I would like to know, what versions of linux are you using on yoga:
ubuntu + unity, or other?
precise (12.04), quantal (12.10), or other?
x86, or x64 ?

---

### Post by liquidator87 on 2013-03-11
Ubuntu 12.10 x64 with Unity

---

### Post by gandalf147 on 2013-03-26
hi, i'm on ubuntu 13.04 beta but seems brightness fix doesn't works. any suggestions? thanks

---

### Post by flygin on 2013-03-30
using 12.10 with kernel 3.7.8, wifi works!, but you have to understand that any spaces (also in upper folder!!!!) make the compiling fail.

Brighness, sound buttons:

sudo gedit /etc/default/grub
[INDENT][/INDENT]change line to:
[INDENT][/INDENT]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
sudo update-grub

---

### Post by joonpy on 2013-04-01
Larry Finger has set up a github repo of the wireless driver: [https://github.com/lwfinger/rtl8723au](https://github.com/lwfinger/rtl8723au)

$ git clone [http://github.com/lwfinger/rtl8723au.git](http://github.com/lwfinger/rtl8723au.git) 
(if you don't have git, download the .zip archive)

$ cd [rtl8723au]("http://github.com/lwfinger/rtl8723au.git")

$ make && sudo make install

Will compile & install the driver. I have tested it and it works well on my Yoga 13.

-Joon

---

### Post by klingo on 2013-04-04
Many thanks joonpy and larry finger, the original driver didn't compile for me with ubuntu 13.04 beta, this one works.

---

### Post by ctowne on 2013-04-09
Hey guys. I can't get my generic header to install. When I type in "dpkg i- nameofheaderfile.deb" is just comes back with dpkg: error: need an action option.. then it lists the help commands. I already have the other header installed and I just need this one so that I can make the wifi drivers install.

---

### Post by drxdrx on 2013-04-13
> **joonpy said:**
> Larry Finger has set up a github repo of the wireless driver: [https://github.com/lwfinger/rtl8723au](https://github.com/lwfinger/rtl8723au)

$ git clone [http://github.com/lwfinger/rtl8723au.git](http://github.com/lwfinger/rtl8723au.git) 
(if you don't have git, download the .zip archive)

$ cd [rtl8723au]("http://github.com/lwfinger/rtl8723au.git")

$ make && sudo make install

Will compile & install the driver. I have tested it and it works well on my Yoga 13.

-Joon


Hi all , ,thanks for the wifi driver, its works .. but there is an issue , when doing a speed test or downloading from any website, it does not go over 1mb. I think its a driver issue. cuz when booting to windows i can download / speedtest 9mb. 
any help would be appreciated . 
best wishes

---

### Post by diafygi on 2013-04-14
> **drxdrx said:**
> Hi all , ,thanks for the wifi driver, its works .. but there is an issue , when doing a speed test or downloading from any website, it does not go over 1mb. I think its a driver issue. cuz when booting to windows i can download / speedtest 9mb. 
any help would be appreciated . 
best wishes

I can confirm that my wifi download speed is capped at around 1.3Mbps (on Ubuntu 12.04). On my other computer (also 12.04), my wifi download speed is around 12Mbps.

---

### Post by SargTeX on 2013-04-24
I just reinstalled Ubuntu 12.10 on Yoga 13 and updated it completely.
Afterwards, I wanted to install that wifi driver, but I wasn't able to.
The error message:

make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.5.0-27-generic/build M=/home/martin/rtl8723A_WiFi_linux_v4.1.3_6044.20121224  modules
make: *** /lib/modules/3.5.0-27-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2

I don't know why; it worked yesterday with my previous Ubuntu 12.10 installation, should be the exact same platform...I have no idea why the directory "build" does not exist.
Any suggestions?
All packages are up to date to the latest stable release.


/EDIT: Sorry for that. Solution: Install the header package for your linux kernel version, e.g.: linux-headers-3.5.0-27-generic

---

### Post by mattrition on 2013-04-26
[quote=diafygi][COLOR=#000000]I can confirm that my wifi download speed is capped at around 1.3Mbps (on Ubuntu 12.04). On my other computer (also 12.04), my wifi download speed is around 12Mbps.[/COLOR][/quote][COLOR=#000000] Perhaps email realtek about this issue? This is how we got the compatible drivers in the first place so I suspect they will be happy to look in to it.

Thank you for a very informative thread everyone! I will install ubuntu on my machine, too, once I have my second SSD.[/COLOR]

---

### Post by mehanzhi on 2013-04-26
Aloha,

I am a Fedora user,  but this is the best topic about Yoga laptop on Linux across the internet, so I registered here.
I am up for sending mail to realtek support, if I had the address:). May be [EMAIL="support@realtek.com"]support@realtek.com[/EMAIL]?
I am using yoga 13 with 4GB RAM 128GB Disk. I installed everything on Fedora 17, the only trouble I had troubled was the wi-fi driver. Worked on kernel 3.4, but touch screen worked only on kernel 3.6+.
I removed the daemonize function call from that file and it worked with speed about 1MB/sec on kernel 3.8. Still trying to run Bluetooth. 

For everybody that wrote lots of posts about the wi-fi driver compile/install problems, I'd suggest to start reading the entire topic from the beginning carefully, not just the 1,2,3... steps for installing the driver.  all 10 pages + few external links took me 15-20 minutes, but answered questions that could save me 3-4 hours if I knew earlier ;).

However, I wanted to ask if anybody did something about screen automatic rotation and keyboard/touch pad turn off in tablet mode?

I am up for writing custom shell scripts as soon as I find way to detect screen rotation and closure of the keyboard in tablet mode.
If anybody has an idea about this, please let me know. 

And I wanted to ask if anybody did try the button that should lock the screen rotation. It is for sure not working as it was made to, but does Ubuntu recognize it as a multimedia key and can you assign functions to it?

Touchscreen has lots of fingers support in Fedora (may be they are 10 fingers), but the gnome-shell doesn't support that well multi touch. Most of the applications doesn't support it too. Does Unity in Ubuntu handle it well?

Thank you.

Edit: In fedora 18 the keyboard turns off automaticly when opened more than about 270 degrees. I found very nice scripts for disabling the touchpad, I'll spend some time this weekend to find a way to detect the the keyboard turning off/on moment and execute touchpad turn off/on script in the same time. The button for display rotation lock appears to response like Super+O and you can assign commands to it. I'll find some usefull purpose to it. If there is none, I may put it as a touchpad on/off switch.
To be done: 
stable wi-fi driver
bluetooth
screen rotation (found some applications that should be able to do it but didn't have the time to install and test them)
fix touchpad on/off

---

### Post by gandalf147 on 2013-04-28
> **flygin said:**
> 
Brighness, sound buttons:

sudo gedit /etc/default/grubchange line to:GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
sudo update-grub
this doesn't work with my ubuntu 13.04

---

### Post by jordi62 on 2013-04-28
> **mehanzhi said:**
> Aloha,

I am a Fedora user,  but this is the best topic about Yoga laptop on Linux across the internet, so I registered here.
I am up for sending mail to realtek support, if I had the address:). May be [EMAIL="support@realtek.com"]support@realtek.com[/EMAIL]?
I am using yoga 13 with 4GB RAM 128GB Disk. I installed everything on Fedora 17, the only trouble I had troubled was the wi-fi driver. Worked on kernel 3.4, but touch screen worked only on kernel 3.6+.
I removed the daemonize function call from that file and it worked with speed about 1MB/sec on kernel 3.8. Still trying to run Bluetooth. 

For everybody that wrote lots of posts about the wi-fi driver compile/install problems, I'd suggest to start reading the entire topic from the beginning carefully, not just the 1,2,3... steps for installing the driver.  all 10 pages + few external links took me 15-20 minutes, but answered questions that could save me 3-4 hours if I knew earlier ;).

However, I wanted to ask if anybody did something about screen automatic rotation and keyboard/touch pad turn off in tablet mode?

I am up for writing custom shell scripts as soon as I find way to detect screen rotation and closure of the keyboard in tablet mode.
If anybody has an idea about this, please let me know. 

And I wanted to ask if anybody did try the button that should lock the screen rotation. It is for sure not working as it was made to, but does Ubuntu recognize it as a multimedia key and can you assign functions to it?

Touchscreen has lots of fingers support in Fedora (may be they are 10 fingers), but the gnome-shell doesn't support that well multi touch. Most of the applications doesn't support it too. Does Unity in Ubuntu handle it well?

Thank you.

Edit: In fedora 18 the keyboard turns off automaticly when opened more than about 270 degrees. I found very nice scripts for disabling the touchpad, I'll spend some time this weekend to find a way to detect the the keyboard turning off/on moment and execute touchpad turn off/on script in the same time. The button for display rotation lock appears to response like Super+O and you can assign commands to it. I'll find some usefull purpose to it. If there is none, I may put it as a touchpad on/off switch.
To be done: 
stable wi-fi driver
bluetooth
screen rotation (found some applications that should be able to do it but didn't have the time to install and test them)
fix touchpad on/off

Hello,

The bluetooth driver will be on Kernel 3.10 , Larry Finger is working on it, also is working on the wifi driver, he thinks will be ready for kernel 3.10

See attached link [http://forums.opensuse.org/english/get-technical-help-here/wireless/477285-rtl8723ae-realtek-wirless-driver-hell-8.html](http://forums.opensuse.org/english/get-technical-help-here/wireless/477285-rtl8723ae-realtek-wirless-driver-hell-8.html)

I use opensuse 12.3. with KDE with kernel 3.8.8 for rotating screen there is a button but not rotate the mouse. the synaptiks touchpad is not dissabling when turning the screen, but there is a button to dissable manually

Jordi

---

### Post by mehanzhi on 2013-04-29
Hello,

**Keyboard and touchpad disabling in tablet mode:**

I have a script that disables and enables the touchpad. It is working fine, but I need an idea how can I detect the screen turning, so I can put there the script execution. 
The keyboard is disabled then turning the screen, but I have no idea how to trace the action. If anybody have idea, please share it and I'll test ;).
So far I just made a shortcut to that script with the little button that suppose to lock the screen rotation on windows.

```

!/bin/bash
# toggleTouchpad by Brendon Dugan
# Toggles a touchpad on or off depending on it's current state or CLI argument
#
# To configure, run the command 'xinput list' in terminal and identify your
# touch pad.
# Using the output of the above command, change the touchpadString variable
# to a substring of your touchpad's description that is unique to that device.
#
# To run, simply type 'toggleTouchpad' to toggle your touchpad on or off, or
# 'toggleTouchpad on' to explicitly turn your touchpad on, or
# 'toggleTouchpad off' to explicitly turn it off.
#
# Enjoy!
touchpadString="SynPS/2 Synaptics TouchPad"
touchpadID=$(xinput list | grep "$touchpadString" | awk -F " " '{print $6}' | awk -F "=" '{print $2}')
touchpadEnabled=$(xinput list-props $touchpadID | grep "Device Enabled" | awk -F ":" '{print $2}')

# Check for arguments on the command line
if [ $# -eq 1 ]; then               # Any arguments?
    arg1=$(echo $1 | tr [:upper:] [:lower:])    # Yes, convert to lower case
    cliArg=1                    # Set flag that we have one
else                        # There is no argument.
    cliArg=0                    # Clear flag
fi

if [ $cliArg -eq 1 ]; then          # Did we get an argument?
    if [ $arg1 = 'on' ]; then           # Yes, was it "on"?
    xinput --set-prop $touchpadID "Device Enabled" 1
                        # Yes, enable the touchpad
    elif [ $arg1 = 'off' ]; then        # No, was it "off"?
    xinput --set-prop $touchpadID "Device Enabled" 0
                        # Yes, disable the touchpad
    else                    # None of the above, so...
    sleep 1                 # ...sleep one second, exit
    fi

else                        # No argument, toggle state
    if [ $touchpadEnabled -eq 1 ]; then     # Enabled now?
    xinput --set-prop $touchpadID "Device Enabled" 0
                        # Yes, so disable it
    else                    # Must be disabled, so...
    xinput --set-prop $touchpadID "Device Enabled" 1
                        # ...enable it
    fi
fi
```

**Screen Rotation**

xrandr does rotate the screen and it is very easy scriptable, but as  jordi62 said, it doesn't rotate the mouse/touchpad/touchscreen orientation. So you get into a real mess when screen is rotated. 

About the screen rotation I found this topic: [http://www.fedoraforum.org/forum/showthread.php?p=1601297](http://www.fedoraforum.org/forum/showthread.php?p=1601297).
This should work, I build it from the source. But I ran on this bug: [https://bugs.launchpad.net/magick-rotation/+bug/1033065](https://bugs.launchpad.net/magick-rotation/+bug/1033065) - *Please install 62-magick.rules in /etc/udev/xorg.d*. Looks like there is not fix or workaround. 
Anyway, I think it will not hurt trying it on other distributions and kernel versions. If it run, it will be nice.

---

### Post by jvcdk on 2013-05-01
Hi

I am running Ubuntu 13.04 on my Yoga 13, and have had problems with the backlight control. I tried the solutions pointed out here (acpi_backlight=vendor in grub) and other places - but no luck. I finally figured out a solution, and I just wanted to share it with you - hoping it will help somebody else as well.

So... the main problem, I figured out, was that there is two devices available for controlling backlight. You can see this in the directory /sys/class/backlight/ . In my directory, I would have
```
  acpi_video0 -> ../../devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/
  intel_backlight -> ../../devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/
```

Manipulating the intel_backlight by e.g. ```
echo 1000 | sudo tee intel_backlight/brightness
``` would work, but the software (via the brightness buttons) would manipulate the acpi_video0 - which would not work. Perhaps that is the brightness for the DVI output - I don't know.

So, one thread suggested to remove (blacklist) the module that created the acpi_video0 device. That, however, was a no go. It is (I think) the video kernel module which is used by the i915 video driver. Not a good thing not to have working. I then noticed that the previous mentioned acpi_backlight=vendor fix replaced the acpi_video0 device with an ideapad device - and that device I could remove by blacklisting the ideapad_laptop module. In other words:
[LIST=1]
[*]Add the acpi_backlight=vendor to your grub default command line (as described before in this thread) 
[*]Run the update-grub (or in my case; update-grub2) command 
[*]blacklist the ideapad_laptop by adding "blacklist ideapad_laptop" to your /etc/modprobe.d/blacklist.conf file. 
[*]Reboot 
[/LIST]

If things works, you should just have the intel_backlight device available - which the brightness keys then will control.


Question... won't I miss some of the features from the ideapad_laptop kernel model? No, probably not. Reasons:
[LIST=1]
[*]Your computer is an Yoga - not Ideapad. Not entirely sure how much architecture they share, though. 
[*]I looked up the doc for the module. The functionality it described did not work for me anyway when I loaded the module. 
[*]It was not loaded anyway from the beginning, remember. It only shows up after you make the acpi_backlight-fix. 
[/LIST]

Best regards
Jørn Christensen

---

### Post by mehanzhi on 2013-05-03
Hello,

I have news about the screen rotation coming from here [https://github.com/wolneykien/xrandr-align](https://github.com/wolneykien/xrandr-align) .

What I did was:
```

yum install xorg-x11-util-macros libXi-devel libXi   # This is for fedora users, in different distributions, the packages may have different names.
yum groupinstall "Development Tools"                  # You probably did this already for the wi-fi driver.
wget [https://github.com/wolneykien/xrandr-align/archive/master.zip](https://github.com/wolneykien/xrandr-align/archive/master.zip)

unzip master.zip
cd xrandr-align-master
autoreconf -fi 
./configure 
make 
make install

```

Then you end up with the binary /usr/local/bin/xrandr-align .
This is from the xrandr-align page:
```
xrandr-align -v monitor --input="eGalax Inc. USB TouchController"
xrandr-align -v gravitate --input="Pegatron Lucid Tablet Accelerometer"
```

The first line does the touchpad/mouse/touchscreen monitoring and when screen is rotated, it also rotates the orientation of the mouse.
The second line does the rotation sensor monitoring and should rotate the screen when the tablet is rotated. However I am still not able to find the drivers for the rotation sensor, so for now the second line is useless for us. We will do the rotation manually with scripts.

This is what I did: 
```


[root@yoga ~]# vi /usr/bin/monitor-touchpad.sh 
#!/bin/bash
/usr/local/bin/xrandr-align  monitor --input="ELAN Touchscreen"
[root@yoga ~]# 

[**username**@yoga ~]$ gnome-session-properties  ## Here you add on startup the script above (I named it monitor-touchpad.sh). 


[root@yoga ~]# vi /usr/bin/rotate-left.sh 
#!/bin/sh
rotation=`xrandr -q --verbose |grep LVDS1 |cut -d ' ' -f6`
if [ $rotation = "normal" ] ;
then
  xrandr -o left
else
  xrandr -o normal
fi
[root@yoga ~]# 
[root@yoga ~]# vi /usr/bin/rotate-right.sh 
#!/bin/sh
rotation=`xrandr -q --verbose |grep LVDS1 |cut -d ' ' -f6`
if [ $rotation = "normal" ] ;
then
  xrandr -o right
else
  xrandr -o normal
fi
[root@yoga ~]# 

```
Both scripts rotate-left/right.sh will rotate the screen in the direction you wish on first execute and will rotate it back to normal on second execute. You can write another script that will rotate left then flip over than right and then return to normal after every execute, but I find this to be more practical way, because when I wish to return to normal I have to execute it only once, not 3 times :)

You can of course put keyboard shortcuts for this scripts on the keyboard or the special buttons (I still use the one that suppose to lock the screen for touchpad disabling).
However I found out that screen rotation is mostly used in tablet mode, so your keyboard will probably be off and the screen keyboard is not very comfortable for key combinations. In fact in tablet mode, the best way to do it is with single tap on the touchscreen. So I did gnome menu icons:

File: /home/username/.local/share/applications/rotate-left.desktop:
```
[Desktop Entry]
Name=Rotate Screen Left
Comment=Rotate Screen Left
Categories=Categories=GNOME;GTK;Utility;TerminalEmulator;System;
Exec=/usr/bin/rotate-left.sh
Type=Application
Terminal=false
Encoding=UTF-8
Icon=/home/username/.local/share/applications/icons/rotate-left.png## This is a nice PNG icon with rotating arrow found on internet :)
```

File: /home/username/.local/share/applications/rotate-right.desktop:
```
[Desktop Entry]
Name=Rotate Screen Right
Comment=Rotate Screen Right
Categories=Categories=GNOME;GTK;Utility;TerminalEmulator;System;
Exec=/usr/bin/rotate-right.sh
Type=Application
Terminal=false
Encoding=UTF-8
Icon=/home/username/.local/share/applications/icons/rotatel-right.png ## Here I got the same arrow, but made it mirror
```

And also for touchpad disabling - /home/username/.local/applications/touchpad-disable.desktop:
```
[Desktop Entry]
Name=Touchpad switch
Comment=Touchpad mouse
Categories=Categories=GNOME;GTK;Utility;TerminalEmulator;System;
Exec=/usr/bin/touchpad.sh  ## I posted this sctipt in previous post above. 
Type=Application
Terminal=false
Encoding=UTF-8
Icon=/home/username/.local/share/applications/icons/touchpad.png ## A nice touchpad icon from internet :)
```

I am left hander, so I add only the rotate right icon to favorites because I will use it mostly. The rotate left icon is in the programs menu under section System Tools, you can always change this. Now it is handy and needs just a single finger tap. I also added touchpad disable icons to favorites, because it's easier to hit the icon on the screen than to find that little button with your fingers. 

I will continue searching for rotation sensor driver, so I can turn it into input device and I can put listener to it, but so far manually execution seems to be the only option.

Hope this help, thank you.

---

### Post by drxdrx on 2013-05-03
> **jvcdk said:**
> Hi

I am running Ubuntu 13.04 on my Yoga 13, and have had problems with the backlight control. I tried the solutions pointed out here (acpi_backlight=vendor in grub) and other places - but no luck. I finally figured out a solution, and I just wanted to share it with you - hoping it will help somebody else as well.

So... the main problem, I figured out, was that there is two devices available for controlling backlight. You can see this in the directory /sys/class/backlight/ . In my directory, I would have
```
  acpi_video0 -> ../../devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/
  intel_backlight -> ../../devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/
```

Manipulating the intel_backlight by e.g. ```
echo 1000 | sudo tee intel_backlight/brightness
``` would work, but the software (via the brightness buttons) would manipulate the acpi_video0 - which would not work. Perhaps that is the brightness for the DVI output - I don't know.

So, one thread suggested to remove (blacklist) the module that created the acpi_video0 device. That, however, was a no go. It is (I think) the video kernel module which is used by the i915 video driver. Not a good thing not to have working. I then noticed that the previous mentioned acpi_backlight=vendor fix replaced the acpi_video0 device with an ideapad device - and that device I could remove by blacklisting the ideapad_laptop module. In other words:
[LIST=1]
[*]Add the acpi_backlight=vendor to your grub default command line (as described before in this thread)
[*]Run the update-grub (or in my case; update-grub2) command
[*]blacklist the ideapad_laptop by adding "blacklist ideapad_laptop" to your /etc/modprobe.d/blacklist.conf file.
[*]Reboot
[/LIST]

If things works, you should just have the intel_backlight device available - which the brightness keys then will control.


Question... won't I miss some of the features from the ideapad_laptop kernel model? No, probably not. Reasons:
[LIST=1]
[*]Your computer is an Yoga - not Ideapad. Not entirely sure how much architecture they share, though.
[*]I looked up the doc for the module. The functionality it described did not work for me anyway when I loaded the module.
[*]It was not loaded anyway from the beginning, remember. It only shows up after you make the acpi_backlight-fix.
[/LIST]

Best regards
Jørn Christensen


Thank you for sharing this info. I really needed that.. thanks again

---

### Post by andremfp29 on 2013-05-05
Hi everyone.
I'm trying the wifi drivers posted above, but when I use "make" I always get the same error:
```
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.8.0-19-generic/build M=/home/andre/rtl/rtl8723A_WiFi_linux_v4.1.3_6044.20121224  modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /home/andre/rtl/rtl8723A_WiFi_linux_v4.1.3_6044.20121224/core/rtw_cmd.o
In file included from /home/andre/rtl/rtl8723A_WiFi_linux_v4.1.3_6044.20121224/core/rtw_cmd.c:23:0:
/home/andre/rtl/rtl8723A_WiFi_linux_v4.1.3_6044.20121224/include/osdep_service.h: In function ‘thread_enter’:
/home/andre/rtl/rtl8723A_WiFi_linux_v4.1.3_6044.20121224/include/osdep_service.h:1418:2: error: implicit declaration of function ‘daemonize’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/home/andre/rtl/rtl8723A_WiFi_linux_v4.1.3_6044.20121224/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/andre/rtl/rtl8723A_WiFi_linux_v4.1.3_6044.20121224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'
make: *** [modules] Error 2

```

I thought it was because of the headers, but I tried to update them and they the latest.
I can't figure this out.
By the way, I'm running Lubuntu 13.04 64 bit

---

### Post by bhowlett on 2013-05-05
> **mehanzhi said:**
> Hello,

I have news about the screen rotation coming from here [https://github.com/wolneykien/xrandr-align](https://github.com/wolneykien/xrandr-align) .

What I did was:
```

yum install xorg-x11-util-macros libXi-devel libXi   # This is for fedora users, in different distributions, the packages may have different names.
yum groupinstall "Development Tools"                  # You probably did this already for the wi-fi driver.
wget [https://github.com/wolneykien/xrandr-align/archive/master.zip](https://github.com/wolneykien/xrandr-align/archive/master.zip)

unzip master.zip
cd xrandr-align-master
autoreconf -fi 
./configure 
make 
make install

```

Then you end up with the binary /usr/local/bin/xrandr-align .
This is from the xrandr-align page:
```
xrandr-align -v monitor --input="eGalax Inc. USB TouchController"
xrandr-align -v gravitate --input="Pegatron Lucid Tablet Accelerometer"
```

The first line does the touchpad/mouse/touchscreen monitoring and when screen is rotated, it also rotates the orientation of the mouse.
The second line does the rotation sensor monitoring and should rotate the screen when the tablet is rotated. However I am still not able to find the drivers for the rotation sensor, so for now the second line is useless for us. We will do the rotation manually with scripts.

This is what I did: 
```


[root@yoga ~]# vi /usr/bin/monitor-touchpad.sh 
#!/bin/bash
/usr/local/bin/xrandr-align  monitor --input="ELAN Touchscreen"
[root@yoga ~]# 

[**username**@yoga ~]$ gnome-session-properties  ## Here you add on startup the script above (I named it monitor-touchpad.sh). 


[root@yoga ~]# vi /usr/bin/rotate-left.sh 
#!/bin/sh
rotation=`xrandr -q --verbose |grep LVDS1 |cut -d ' ' -f6`
if [ $rotation = "normal" ] ;
then
  xrandr -o left
else
  xrandr -o normal
fi
[root@yoga ~]# 
[root@yoga ~]# vi /usr/bin/rotate-right.sh 
#!/bin/sh
rotation=`xrandr -q --verbose |grep LVDS1 |cut -d ' ' -f6`
if [ $rotation = "normal" ] ;
then
  xrandr -o right
else
  xrandr -o normal
fi
[root@yoga ~]# 

```


I tried your scripts but they didn't work for me. Modified them and changed them so no matter what the current orientation is it will change to the desired orientation. Even easier than running the same script again!

Here are the scripts after my modification:

to make orientation normal:
```

!/bin/bash
xrandr -o normal

```

make orientation to the left:
```

!/bin/bash
xrandr -o left

```

make orientation to the right:
```

!/bin/bash
xrandr -o right

```

and finally to make the orientation inverted:
```

!/bin/bash
xrandr -o inverted

```


Hope this helps someone else!

---

### Post by mehanzhi on 2013-05-06
> **andremfp29 said:**
> Hi everyone.
I'm trying the wifi drivers posted above, but when I use "make" I always get the same error:
```
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.8.0-19-generic/build M=/home/andre/rtl/rtl8723A_WiFi_linux_v4.1.3_6044.20121224  modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /home/andre/rtl/rtl8723A_WiFi_linux_v4.1.3_6044.20121224/core/rtw_cmd.o
In file included from /home/andre/rtl/rtl8723A_WiFi_linux_v4.1.3_6044.20121224/core/rtw_cmd.c:23:0:
/home/andre/rtl/rtl8723A_WiFi_linux_v4.1.3_6044.20121224/include/osdep_service.h: In function ‘thread_enter’:
/home/andre/rtl/rtl8723A_WiFi_linux_v4.1.3_6044.20121224/include/osdep_service.h:1418:2: error: implicit declaration of function ‘daemonize’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/home/andre/rtl/rtl8723A_WiFi_linux_v4.1.3_6044.20121224/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/andre/rtl/rtl8723A_WiFi_linux_v4.1.3_6044.20121224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'
make: *** [modules] Error 2

```

I thought it was because of the headers, but I tried to update them and they the latest.
I can't figure this out.
By the way, I'm running Lubuntu 13.04 64 bit


Hello andremfp29,

It is known issue with kernel 3.8, I suggest start reading the topic  from the beginning with the side links pointing to the driver source  download. There is a solution for you. 
Or I'll give you the quicker way:  [http://wiki.debian.org/InstallingDebianOn/Lenovo/IdeaPad%20Yoga%2013%20%28wheezy%29](http://wiki.debian.org/InstallingDebianOn/Lenovo/IdeaPad%20Yoga%2013%20%28wheezy%29)  . There they say: 
> **WiFi**

 Wifi does  NOT work out of the box  at all. There is a beta-grade non-free driver  which you can get by  sending an e-mail to Realtek support and ask for  the "RTL8723AS-VAU"  driver. 

[LIST]
[*]Unpack the driver
[*]./make_drv
[*]make
[*]sudo make install
[/LIST]
If  you are running Linux 3.8, as suggested for the touch screen,  you may  get an error when running "make" mentioning the "daemonize"  function.  This function has been removed from the kernel, for reasons  the author  is not familiar with so the following may create security  problems. Open  *include/osdep_service.h* and remove the line calling the *daemonize*   function. (You do this at your own risk. Neither the author nor the   Debian team will take any responsibility if this makes your system   unstable).

---

### Post by andremfp29 on 2013-05-06
Hi [**[COLOR=#000000]mehanzhi[/COLOR]**]("http://ubuntuforums.org/member.php?u=1815008").

It worked! I'm postinng this reply on Lubuntu using my WiFi network!
Thank you very much ;)

---

### Post by mehanzhi on 2013-05-09
Hello,

Anybody have news about the bluetooth driver?

---

### Post by Jiang Liu on 2013-05-10
> **andremfp29 said:**
> Hi everyone.
I'm trying the wifi drivers posted above, but when I use "make" I always get the same error:
```
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.8.0-19-generic/build M=/home/andre/rtl/rtl8723A_WiFi_linux_v4.1.3_6044.20121224  modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /home/andre/rtl/rtl8723A_WiFi_linux_v4.1.3_6044.20121224/core/rtw_cmd.o
In file included from /home/andre/rtl/rtl8723A_WiFi_linux_v4.1.3_6044.20121224/core/rtw_cmd.c:23:0:
/home/andre/rtl/rtl8723A_WiFi_linux_v4.1.3_6044.20121224/include/osdep_service.h: In function ‘thread_enter’:
/home/andre/rtl/rtl8723A_WiFi_linux_v4.1.3_6044.20121224/include/osdep_service.h:1418:2: error: implicit declaration of function ‘daemonize’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/home/andre/rtl/rtl8723A_WiFi_linux_v4.1.3_6044.20121224/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/andre/rtl/rtl8723A_WiFi_linux_v4.1.3_6044.20121224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'
make: *** [modules] Error 2

```

I thought it was because of the headers, but I tried to update them and they the latest.
I can't figure this out. 
By the way, I'm running Lubuntu 13.04 64 bit

Hi all,
        I have successfully adopted the solution from thread [http://www.serverphorums.com/read.php?12,681196](http://www.serverphorums.com/read.php?12,681196).
It works perfectly with Yoga13 and Ubuntu 13.04. Basically three steps:
1) git clone [http://github.com/lwfinger/rtl8723au.git](http://github.com/lwfinger/rtl8723au.git)
2) make
3) sudo make install

---

### Post by Jon O on 2013-05-11
> **mehanzhi said:**
> Hello,

Anybody have news about the bluetooth driver?

The Bluetooth driver has appeared here: [https://github.com/lwfinger/rtl8723au_bt](https://github.com/lwfinger/rtl8723au_bt)
It's working (so far) for me.

---

### Post by mehanzhi on 2013-05-11
Hello,
```
[root@yoda work]# git clone http://github.com/lwfinger/rtl8723au_bt.git
Cloning into 'rtl8723au_bt'...
remote: Counting objects: 10, done.
remote: Compressing objects: 100% (8/8), done.
remote: Total 10 (delta 2), reused 10 (delta 2)
Unpacking objects: 100% (10/10), done.
[root@yoda work]# 
[root@yoda work]# cd rtl8723au_bt/
[root@yoda rtl8723au_bt]# make
make -C /lib/modules/3.8.11-200.fc18.x86_64/build M=/root/bluetooth/work/rtl8723au_bt modules
make[1]: Entering directory `/usr/src/kernels/3.8.11-200.fc18.x86_64'
  CC [M]  /root/bluetooth/work/rtl8723au_bt/rtk_btusb.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /root/bluetooth/work/rtl8723au_bt/rtk_btusb.mod.o
  LD [M]  /root/bluetooth/work/rtl8723au_bt/rtk_btusb.ko
make[1]: Leaving directory `/usr/src/kernels/3.8.11-200.fc18.x86_64'
[root@yoda rtl8723au_bt]# 
[root@yoda rtl8723au_bt]# make install
mkdir -p /lib/firmware/rtk_bt
cp -f rlt8723a_chip_b_cut_bt40_fw_asic_rom_patch-svn8511-0x0020342E-20121105-LINUX_USB.bin /lib/firmware/rtk_bt/rtk8723a.bin
cp -f rtk_btusb.ko /lib/modules/3.8.11-200.fc18.x86_64/kernel/drivers/bluetooth/rtk_btusb.ko
depmod -a /lib/modules/3.8.11-200.fc18.x86_64
echo "install rtk_btusb success!"
install rtk_btusb success!
[root@yoda rtl8723au_bt]# 

```

Then reboot and it is not working:

```
[root@yoda rtl8723au_bt]# lsmod |grep -i rtk
rtk_btusb              22936  0 
bluetooth             359871  9 bnep,rtk_btusb
[root@yoda rtl8723au_bt]# rmmod bluetooth
rmmod: ERROR: Module bluetooth is in use by: bnep rtk_btusb


```
The module is loaded, but bluetooth is still not working.
Any idea how to troubleshoot it?

Thank you.

---

### Post by elfsternberg on 2013-05-12
Thank you all for all your help!  On your recommendations and advice, I've bought a Yoga 13 and begun the great brain transfer from my Thinkpad T61.  Installation was pretty easy off a USB stick, and I did get the WiFi working, and installed a ton of stuff.  I'm coming over from Gentoo, but I've decided I don't have time to waste on rebuilding the universe.

According to some reviewers, there's an accelerometer on the Yoga.  Has anyone found it?  There was one on the T61, too, but it wasn't easy to find: you had to build the tp_mapi and tp_hdaps, and it was hidden in HDAPS (hard drive acceleration protection system), which locked the drive head in a safe position when you dropped the laptop.  The Yoga has an SSD, so doesn't have an HDAPS subsystem.  It doesn't show up on LSPCI, LSHW, or LSUSB, so I'm at a loss to figure out where on this mobo the thing is hidden.  

Maybe the reviewers are wrong?  There doesn't seem to be anything about accelerometers or stuff like that on the specs sheet.

[EDIT:] An in-depth examination of the motherboard's PCI responses shows the presence of an Intellisense Motionapps Sensor.  Are there any HID drivers for it?

---

### Post by elfsternberg on 2013-05-12
Oh, another question: Isn't the screen hinge supposed to generate some kind of event when the screen is flipped over?  I don't want to have to do this manually every time.

[EDIT]: YES.  Moving the hinge past the 90° point will generate e03e, but X doesn't get the message because there's no keycode associated with "Unknown key 0xBE."  It's not possible to detect *where* the hinge is quite yet (toward the keyboard or away from it), but I'm one step closer to distinguishing between "keyboard mode," "portfolio mode" (widescreen, for watching video), and "tablet mode" (longscreen, for reading).

---

### Post by daneturner on 2013-05-15
I just bought a Yoga 13, i5-3337u, and have been testing with Ubuntu 12.04.2 64-bit.  Thanks to the helpful posts in this thread, I was able to get wireless and screen brightness contorls working without a fuss.  I'm curious how often people use the device in tablet mode, with only the touchscreen for input.  Any suggestions on touchscreen web browsing?  Things like zoom, forward/back, and scroll would be handy to know how to do using the touchscreen.

I'm also curious about TLP for power management on the Yoga.  Any recommendations for/against?  Perhaps with TLP I could silence the internal fan, which seems to always be running.

Thanks,
Dane

---

### Post by elfsternberg on 2013-05-25
Anyone getting Invert Axes to work?   I tried using the Coordinate Transformation Matrix, but the math defeated me, even though it seemed simple enough in the explanation.  I also tried these commands, and after running them xinput *says* they've changed the values in the configuration, but the screen behavior is unchanged and the transformation is broken.  Any help?

  xinput set-prop --type=int --format=8 "ELAN Touchscreen" "Evdev Axes Swap" 1
  xinput set-prop --type=int --format=8 "ELAN Touchscreen" "Evdev Axis Inversion" 0 1

---

### Post by elfsternberg on 2013-05-25
I got Invert Axes to work!

I hate being made to feel like a fool, especially by a software bug.  I wasted four hours over the past two days trying to get my new Lenovo Yoga's touchscreen to work.  It was fine in desktop mode, but rotated (for tablet mode) or inverted (for media mode), and the touchscreen's geometry would freak out; the touchscreen pointer wouldn't track anymore, gestures stopped working, it was a pain.


I tried using the event driver (evdev) settings, both "Axes Swap" and "Axis Inversion".  It didn't help.  I got desperate, and tried to teach myself the <a href="http://www.x.org/wiki/XInputCoordinateTransformationMatrixUsage">Coordinate Transformation Matrix</a>, but that link is one brutally nasty "If you can't do matrix math, I'm not stupid enough to help you" bit of writing.  I <i>am</i> knowledgeable enough to do matrix math, but his explanation is as clear as landfill, and about as useful.


It turns out that none of my confusion was my fault.  There's a bug xf86-input-evdev-2.7, the version that ships with Ubuntu 12 (Quantal).  It doesn't handle rotation or inversion well on the ELAN Touchscreens that ship with the Yoga.  It's somewhat understandable-- the Yoga is a very new piece of hardware-- but damn, it's annoying.


I downloaded, compiled and installed xf86-input-evdev-2.8, and now it works.  So if you're feeling brave, that's the way to do it.  Along with the WiFi, you need the latest evdev driver from Xorg, and you'll also be one step closer to having a full set of yoga positions.

---

### Post by mehanzhi on 2013-05-27
Hello elfsternberg,

Did you get automatic screen rotation with the sensor, or you was just able to turn the screen and touchpad/touchscreen orientation manually with scripts?

I post how-to steps to rotate the screen and touchscreen orientation manually in this topic at page 11 I think. It's done by the 3rd party tool xrandr-align and works great. But I was not able to get the sensor driver and do automatic rotation.

So remains not working now is:
wi-fi driver at full speed: wi-fi is working now great and rock stable, but the max speed you get is 2.5 megabytes per second.
Bluetooth: There is a driver and a post of Jon O above with github link. I installed it but it didn't work for me, the kernel module is loaded, but bluetooth is still disabled. He didn't respond with how-to build or how-to troubleshoot it. 
Automatic screen rotation sensor: So far I was unable to find driver for the sensor, I got it working by manual execution of simple scripts transformed into a desktop menu items. 


P.S. I am Fedora 18 user, but all this should apply to ubuntu too. Only the screen rotation script didn't work for bhowlett, but he posted a very simplified scripts that really has to work on any Linux.

---

### Post by saint9121 on 2013-05-28
sry next post, meant to quote...

---

### Post by saint9121 on 2013-05-28
> **Jiang Liu said:**
> Hi all,
        I have successfully adopted the solution from thread [http://www.serverphorums.com/read.php?12,681196](http://www.serverphorums.com/read.php?12,681196).
It works perfectly with Yoga13 and Ubuntu 13.04. Basically three steps:
1) git clone [http://github.com/lwfinger/rtl8723au.git](http://github.com/lwfinger/rtl8723au.git)
2) make
3) sudo make install





I'm pretty unfamiliar with a command line. Do you think you could actually write out what to type into the terminal to install the driver? I've already downloaded git and cloned the link. so i got step 1 done but dont know how to do 2 or 3.
what is the line for make and the line for sudo make install?

Thanks

---

### Post by elfsternberg on 2013-05-29
Mehanzi: I'm doing it manually.  xrandr-align didn't work for me because of the evdev driver bug.  The evdev driver 2.7 is broken.  2.6 seems to work fine, as does 2.8, so maybe your Fedora has a working driver.  I haven't tried using xrandr-align, but I've written a bash script to do both display and touchscreen rotation and it's working fine.  I've even written a touchegg config file for qcomicbook so now I can read manga in portrait mode, and swipe with two fingers to turn the page.  Sweet.  (And a three-finger top for boss mode!)  

I've found the InvenSense MotionApps hardware in lsusb.  It's the thing that identifies itself as a Texas Instruments component. It says it's a HID (Human Input Device) device.  It shows up as a USB device (/dev/bus/usb/002/003, but it may be different on your machine obviously), but no input devices associate with it.  You can find the kernel endpoint in /sys/bus/usb/devices.  I can't get any output out of it, obviously, since there are no input streams to be found in /dev.

---

### Post by PatheticMoFo on 2013-05-30
> **saint9121 said:**
> I'm pretty unfamiliar with a command line. Do you think you could actually write out what to type into the terminal to install the driver? I've already downloaded git and cloned the link. so i got step 1 done but dont know how to do 2 or 3.
what is the line for make and the line for sudo make install?

Thanks

So steps 2 and 3 are the commands: you literally type "make" and "sudo make install" (without the quotes) into a terminal in order to install it. But, first make sure you are IN the source directory. So after step 1, cd into the directory. For the sake of completeness:

```

git clone http://github.com/lwfinger/rtl8723au.git
cd rtl8723au
make
sudo make install
```

---

### Post by Mista Teaser on 2013-06-01
Hi guys,

thanks for all your help in this thread. I appreciate that very much!

I bought a yoga several weeks ago and installed ubuntu on it this weekend.

The following things are working:
1. Screen-rotation with the help of 6 scripts (Thanks to [**[COLOR=#000000]mehanzhi[/COLOR]**]("http://ubuntuforums.org/member.php?u=1815008") (post 104) and [**[COLOR=#000000]bhowlett[/COLOR]**[COLOR=#000000] (post 107))[/COLOR]]("http://ubuntuforums.org/member.php?u=1818155")
2. Wifi 
3. Bluetooth (Thanks to [**[COLOR=#000000]Jon O[/COLOR]**]("http://ubuntuforums.org/member.php?u=1819998") for the link to the driver in post 112)
4. Brightness (Thanks to [**[COLOR=#000000]Ashade[/COLOR]**]("http://ubuntuforums.org/member.php?u=1765982") in post 23 and [**[COLOR=#000000]jvcdk[/COLOR]**]("http://ubuntuforums.org/member.php?u=1816677") in post 103)
5. some gestures are working: 2-Finger-scroll on the right side of the touchpad and 3-Finger-resize. The problem is, that these two gestures are not always working. 

So far so good :-)

And thanks for the tutorial in post 29 from [**[COLOR=#000000]chrisdotcode[/COLOR]**]("http://ubuntuforums.org/member.php?u=1769439"). I tried especially the section "Touch Screen". The "mtdiag" tool is running on my machine, but i don't know what opportunity it should give me?!

The following things are not working:
1.auto-screen-rotation
2.bluetooth does not work, after awaking from suspend (rmmod and modprobe solves it)
3.gestures not working properly.
4.The touchscreen does not accept a click-input. I got this error sometimes, but not reproduceable. I am still able to navigate, but not to click anything.Could this error be caused by the use of the evdev 2.7 driver? UPDATE: I can still double click on my Desktop-Icons while the error occurs 

Thats all for now.

I am using ubuntu 13.04 32bit.

Best regards
Mista Teaser

---

### Post by veoozo on 2013-06-01
Please help a noob out. I can't figure out for my life how to enable wifi. Please help me out! I need it to be explained like you were talking to a 10 year old. Thanks!

---

### Post by mehanzhi on 2013-06-01
Hello **Veoozo**,

And other guys new on linux\yoga.
There are lots of answers on this topic, but please start reading it from the beginning. 
I am really sorry to say this so straight, but there are bunch of posts like your of guys that didn't read the first pages and keep asking the same questions.
Please start reading the topic from the beginning and you will find at least 3-4 posts of how-to build wi-fi driver and another 3-4 posts of how-to troubleshoot issues building the driver.
If you read it all and try everything described here, but you still have issues, then please post here and then we all will be happy to look for solution together.

Thank you and please take my apologies for not answering you straight.

**Mista Teaser**

I was unable to run the bluetooth driver.
I don't know if there are new versions in the github, but the last time I tryed it (about 2 weeks ago) I installed the module and reboot. After that bluetooth was not working. No standby, no hibernate. Right after nice good reboot the module gets loaded but the bluetooth doesn't work. What distribution and kernel are you working on?

Thank you.

---

### Post by Mista Teaser on 2013-06-02
Hi mehanzhi,

i am working on ubuntu 13.04 32 bit with kernel 3.8. (Standard desktop version).

cat /proc/version
Linux version 3.8.0-23-generic (buildd@aatxe) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #34-Ubuntu SMP Wed May 29 20:24:54 UTC 2013

I got my mobile and my headset up and running via bluetooth with the driver described in this thread.
I downloaded the driver from github about 2 days ago.

---

### Post by Isidith on 2013-06-03
Hi everyone,

First thanks for the wifi drivers, it s running fine.

Using the following version :
```
...@Yoooga:~$ uname -a
Linux Yoooga 3.8.0-19-generic #30.2 SMP Tue May 7 08:05:59 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

I noticed that while running Ubuntu,the fans are always at the same speed, even if the machine is idle. I wouldn't say its running full speed, but the fans are definitely more noisy than in Windows 8.

Running sensors gives :

```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +45.0°C  (crit = +110.0°C)


coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +45.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +44.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +41.0°C  (high = +87.0°C, crit = +105.0°C)
```
Running sensors-detect only proposes adding the coretemp module.

Finally running pwmconfig gives :

```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```

Have you guys noticed this too ?

---

### Post by mehanzhi on 2013-06-04
Hello,

In post 116, **daneturner** suggest installing the TLP utilities, but I didn't try it because the sound is not a problem for me.

---

### Post by Isidith on 2013-06-04
Hi mehanzhi,

Thanks for your suggestion.
My main concern on the fan was mainly related to power consumption, I m wondering if we can squeeze some more battery life if the fans stop running at full speed all the time :)
I installed tlp utilities and interesting enough the utilities fails to read the fan speed.

---

### Post by liquidator87 on 2013-06-04
Does anyone have problems with build-in microphone and Skype? The microphone is recognized, but it works very badly... it produces a lot of noise and my words are understandable if I shout and speak slowly

---

### Post by veoozo on 2013-06-04
I still need help getting wifi to work! I'm running 13.04 on my Yoga. Please, someone, help a noob out!

---

### Post by themanhimself on 2013-06-05
[FONT=arial]CATCH-ALL GUIDE FOR INSTALLING WIFI DRIVER:

1) Download the driver from here [http://mediafire.com/?sanq19s3vv1d9c9](http://mediafire.com/?sanq19s3vv1d9c9). You'll need a computer with wi-fi to find it, once you've downloaded it put it on a usb stick and move it to your yoga.
[/FONT][FONT=arial]
2) Once it's on the yoga, unzip it, take the folder called 'rtl8723au' and drag and and drop it to your Home folder. Then open the application 'Terminal' and type in 
```
cd rtl8723au
```
and hit enter.

3) Copy and paste this ```
make
``` into the terminal window and hit enter. 

4) [/FONT][FONT=arial]Copy and paste this ```
sudo make install
``` into the terminal window and hit enter. [/FONT][FONT=arial]It will ask you to enter your password, do so, no dots or characters will appear as you type your password. Then hit enter.

5) [/FONT][FONT=arial]Copy and paste this ```
[/FONT][COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe 8723au[/FONT][/COLOR][FONT=arial]
``` into the terminal window and hit enter.[/FONT]
[FONT=arial]
6) There is no 6. You're done.

Hopefully having one guide will help people work this out.

PS If this going to be a catch-all guide I sure hope it's correct, please post corrections or necessary modifications, I'm fairly new at this myself![/FONT]

---

### Post by themanhimself on 2013-06-05
> **Mista Teaser said:**
> 
4.The touchscreen does not accept a click-input. I got this error sometimes, but not reproduceable. I am still able to navigate, but not to click anything.Could this error be caused by the use of the evdev 2.7 driver? UPDATE: I can still double click on my Desktop-Icons while the error occurs 

Thats all for now.

I am using ubuntu 13.04 32bit.

Best regards
Mista Teaser

I've noticed the same thing. Sometimes a touch is a click sometimes it's just a navigation and I can't seem to figure out what sets it in one mode or another. That's probably one of the more frustrating things for me because it makes the touchscreen essentially useless.

---

### Post by veoozo on 2013-06-05
Thanks! I'm going to try this out when I get home from school. I'll tell you guys if this works soon.

---

### Post by veoozo on 2013-06-05
HELP! I've installed Ubuntu many times in the past. No problem. But now, I was trying to install 13.04 on my Yoga 13 and I accedently had "replace Windows 8 with Ubuntu" selected. I didn't mean to click start installation. It went to the next slide where you choose your country for about 10 seconds before I relized what it was doing and I shut everything down. Now I can't boot ANYTHING. When I go to the "Try Ubuntu without installing" boot option, I can see how the only drive that Ubuntu is showing is a 124 GB drive. When I go into Partition Manager, I can see how all of my Yoga's crazy partitions are GONE, including my main Windows C:// one. I have no idea what to do. Somebody, please help!

---

### Post by mehanzhi on 2013-06-05
Hello **Veoozo**,

The first thing I did as soon as I found out how to shutdown windows 8 so I can boot and enter BIOS (took me 30 minutes to figure out how to power off windows 8), I booted Fedora installation media and deleted all that useless partitions. They was may be 5-6, may be more. Probably they was some kind of system recovery partitions that use about 20-25% of your hard drive and you will never needed anyway. 
> When I go into Partition Manager, I can see how all of my Yoga's crazy partitions are GONE, including my main Windows C:// one. Nicely done, this is what I did too. You can now start building you clean new system the way you like it, not the way Lenovo and Microsoft tells you to like.

> I have no idea what to do. Somebody, please help!
1. Get installation media (Linux live USB installer or windows USB flash installer).
2. Boot the installation media and follow the instructions to install your brand new nice clean operating system.
3.1 For Linux follow the instructions in this topic to install 1. wi-fi driver, 2. Bluetooth driver, 3. screen rotation scripts/tools. 
3.2 For windows download the 5743981387(or may be even more) drivers and utilities from the Lenovo web site and install them. 
4. You are done, install the applications you need to start working/having fun :)

Good luck, if you have any troubles installing/configuring Linux, you will find everything you need in this topic, if you can't find it then just ask. :)


Hello **liquidator87**,

> liquidator87 	 	 		[INDENT] 			 				Re: Lenovo IdeaPad Yoga Ultrabook
 			 			Does anyone have problems with build-in microphone and Skype? The  microphone is recognized, but it works very badly... it produces a lot  of noise and my words are understandable if I shout and speak slowly 		[/INDENT] 	

I got the same issue, with any standard sound recorder, the build in MIC is working great. But with skype  on the test call I got almost absolute silence. Tried to to remove the auto level tuning of skype, but didn't work. Tried with skype 4.1 x86 RPM from the Skype web site and with older, I think it was about version 2. Still the same result. 
I have no idea how this happens, because skype uses pulse audio/alsa and the sound recorders use it too. I have no idea how every normal sound recorder can get crystal sound, but skype can not.
I wonder if there is the same problem on skype in windows.

Thank you.

---

### Post by veoozo on 2013-06-06
Mehanzhi-

Thanks to you and to everyone else for helping me! I ended up just saying "screw it" and installing Ubuntu over everything. I am typing this from my Yoga right now! I no longer have Windows now, which is a problem. I have contacted Lenovo support (horrible support, I had to lie to get them to help me) and tried to get help there. They are sending me a Windows recovery disk. Now, on to what you said, about you deleting Windows, how did you get a W8 ISO? And how did you find your product key? Thanks

---

### Post by mehanzhi on 2013-06-06
I never had to install windows, I just get rid of it at the moment I power it on for the first time.
However I think you can download windows 8 ISO from the Microsoft web site. It's free trial and you just have to fill that horrible form to register and log in. 
Then after installation you don't need the product key if we believe the Lenovo documentation, because it is integrated or something like that with the hardware product. Just do online windows activation and the Microsoft servers will know that you are using Lenovo Yoga 13 laptop. They only sell them with windows 8, so there is no way you cheat and steal that copy of windows, because you've already buy it with your hardware. Your windows should be activated with no troubles. At least this is what the documentation says, I didn't try it my self.

Good luck :)

P.S. I would still reconsider staying on ubuntu but it's a personal choice of everyone. ;)

---

### Post by themanhimself on 2013-06-06
[B]Veoozo
[/B]If you have some money to drop and you're confident you could follow an instruction guide on disassembling and reassembling your computer then I have another option. As mentioned previously the Yoga ships with one mSATA SSD hard drive installed (128 GB) and an open slot for another one. You could leave Ubuntu running on the one you have now and buy another one (here; [http://www.amazon.com/s/ref=nb_sb_ss_i_0_13?url=search-alias%3Daps&field-keywords=msata+ssd&sprefix=lenovo+yoga+s%2Caps%2C218]("http://www.amazon.com/s/ref=nb_sb_ss_i_0_13?url=search-alias%3Daps&field-keywords=msata+ssd&sprefix=lenovo+yoga+s%2Caps%2C218"); or at your local electronics store), install it (instructions here; [http://vmtoday.com/2013/01/how-to-upgrade-memory-and-storage-on-the-lenovo-ideapad-yoga-13/](http://vmtoday.com/2013/01/how-to-upgrade-memory-and-storage-on-the-lenovo-ideapad-yoga-13/); video here; [http://www.youtube.com/watch?v=At-Br20OAvg](http://www.youtube.com/watch?v=At-Br20OAvg)) and then install Windows 8 on the second hard drive. I did this myself and I'm very happy with it. Furthermore I put a 32GB SD card in the slot and use it as common storage space between the two operating systems (For instance, I keep my music on there and have my Banshee library in Ubuntu and my iTunes library in Windows set to that location, that way I can listen to or edit my music on Ubuntu and still sync my iPhone on Windows without having to have two copies of the library).

---

### Post by themanhimself on 2013-06-06
> **mehanzhi said:**
> Hello,

I have news about the screen rotation coming from here [https://github.com/wolneykien/xrandr-align](https://github.com/wolneykien/xrandr-align) .

What I did was:
```

yum install xorg-x11-util-macros libXi-devel libXi   # This is for fedora users, in different distributions, the packages may have different names.
yum groupinstall "Development Tools"                  # You probably did this already for the wi-fi driver.
wget [https://github.com/wolneykien/xrandr-align/archive/master.zip](https://github.com/wolneykien/xrandr-align/archive/master.zip)

unzip master.zip
cd xrandr-align-master
autoreconf -fi 
./configure 
make 
make install

```

I installed yum to do this but I don't have any repos, what repo should I enable for this download?

---

### Post by mehanzhi on 2013-06-06
Hello [**[COLOR=#000000]themanhimself[/COLOR]**]("http://ubuntuforums.org/member.php?u=1825356") 	 ,

I am sorry for the misunderstanding, but I use yum, because it's my default package manager system in Fedora. I use mostly default Fedora repos and sometimes rpmfusion. But you should not use them if you are running different distribution, they are just for Fedora.
This RPM packages installed by yum are maiden for Fedora. Even Red Hat that also use RPM Packages and yum package manager, has different packages than Fedora. If you are using another distribution, it may have another package manager and I would very strongly recommend it. If you are running ubuntu for example, you should use apt-get.
The package named may also have some differences, but a simple search with a part of the package name should give you the right package for your distribution. Google search may do the trick too.
About that yum groupinstall "Development tools", I don't know if ubuntu and other distributions have ready sets of multiple packages ready for installation. The set Development Tools include c/c++ compiler, libraries for developers, kernel sources and headers and so on. If you like I can give you the full list packages of the Development Tools set.

Sorry for the wrong direction I gave you and good luck.

Thank you.

---

### Post by themanhimself on 2013-06-06
Ah, no worries. I'm not super familiar with other distros so I didn't know that was a native Fedora thing. I should be able to track down the correct package(s) but if anyone has a direction to point me I'd appreciate it.

---

### Post by veoozo on 2013-06-06
I need some more help. I need to have Windows 8 back on my Yoga mainly due to the fact that the touchscreen doesn't work, battery life sucks, can't use modes, no on screen keyboard, ect. I used Ubuntu on my last laptop and it was my primary OS. I loved it. I just need Windows back. Basically what happened is I accedently started the process of reeplacing Windows 8 with Ubuntu during the installation process. By then it was too late, as Ubuntu had already destroyed the C:// partition and the recovery partitions. I'm now stuck with a Windowless Yoga. I've tried to install Windows 7 on it and then use the 8 upgrade assistant, but that failed (couldn't detect drivers). I really need  Windows 8 back on this thing. Could anybody help?

---

### Post by mehanzhi on 2013-06-07
**Veoozo**
As I already said, if you need windows, just go ahead and install it. 
Download Windows ISO from microsoft web site, convert it into a bootable flash with the microsoft tool and install it. It shouldn't be a problem. 

If you need both ubuntu and windows both, you get second hard drive as suggested by **themanhimself **and install dual boot PC. If you are not confident you can disassemble and reassemble the laptop, you can always go to any PC service and leave it to people that do this every day. It shouldn't cost you more then few dollars and if you buy the second hard drive from them, they can even mount it for free : ). Or you can even contact Lenovo support and they do it for you.
By the way, I am not sure how much disk space Windows 8 needs, but may be it is possible even to turn off the UEFI and install both Windows ans Linux on single hard drive. If Windows doesn't require lots of disk space it is quite possible.
Anyway, installation of Windows should be very straight and simple (this is windows after all, they always say it's very user-friendly), just get the installation media and install it :)

**themanhimself**,

What I did was just start compiling that stuff, on step ./configure and  make, I got multiple errors for missing libraries, so I just did "yum search" or "yum provides" (yum provides tells you which package you need to install to get this binary, library or any other file).
So I was able to trace all the package my self with just a few retries. If this package list doesn't do the job, I am sure you have tools with the same function on your package system and very easy you can find the ones you need.

---

### Post by themanhimself on 2013-06-07
[B]Veoozo
[/B]Do you have an installation key?

---

### Post by veoozo on 2013-06-07
[B]Themanhimself and mehanzhi

[/B]
That's my problem. I can't find a Windows 8 ISO anywhere. The only way to get an ISO from Microsoft is to use the Upgrade Assistant, but you need to have Windows 7 installed to use that. All I have on this computer is Ubuntu. And sense the Yoga comes with an OEM installation of 8, there is no product key. Well, there is, but it's encrypted into BIOS. This really sucks. Anyone?

---

### Post by themanhimself on 2013-06-08
I did the same thing as you, accidentally deleted Windows and had to recover. I torrented the ISO and then called Microsoft for a product key, I recommend the same

---

### Post by mehanzhi on 2013-06-08
You can download windows 8 trial ISO from the microsoft web site. 
I just typed in google "windows 8 trial download microsoft" and the first link that appear is for the microsoft web site: [http://msdn.microsoft.com/en-us/evalcenter/jj554510.aspx](http://msdn.microsoft.com/en-us/evalcenter/jj554510.aspx) (hope this link works for you as it works for me). At the bottom of the page you have download buttons for x32 and x64 bit OS. You have to login with your Microsoft account. Agree and press continue 2 times and you got your trial ISO.
Ones you have the ISO, the activation shouldn't be a problem.
Torrent trackers are still good solution, but if I have a choice I always prefer the official source :)

---

### Post by asymingt on 2013-06-08
I'm also interested in getting the motion sensor up and running. I did a bit of investigation myself. The command 'lsusb -vv' showed that the motion processor is based on an Invensense chip. However, since Invensense doesn't have a USB vendor ID they are probably using a TI chip to arbitrate communication with the motion processor. The product ID seems to be unknown, but I don't think all is lost. I noticed that the USB device has the following two end points:

>      Endpoint Descriptor:        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              20
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes


This is a strikingly similar configuration to an FTDI USB-to-serial chip. I'm no expert, but I believe that this USB device may be as simple as a rebranded [COLOR=#444444][FONT=arial]TUSB3410. Since their focus is not inertial navigation, It would make sense for Lenovo to use a third party configuration (like [/FONT][/COLOR][COLOR=#444444][FONT=arial]TUSB3410 <-> MSP430 <-> INVENSENSE) to provide motion processing capability to their products. I downloaded the MotionApp 5.1 SDK from the Invensense website, and this seems like a good starting point to work from. It may be the case that this is the exact configuration being used in the Yoga 13. The best way to confirm this / work out how to communicate with the device may be to run wireshark in Windows with USB packet capture.[/FONT][/COLOR]

---

### Post by veoozo on 2013-06-08
.

---

### Post by veoozo on 2013-06-08
I have also torrented the ISO, but I haven't installed it yet. I called Lenovo many times and told many lies, but I was able to get them to send me the recovery disks (they shipped it via UPS Next Day Air :D). I have been trying all day to get them to work, but they don't seem to work. I've used multiple USB sticks and created dozens of ISOs, but the recovery fails when it tries to initilize the CD/DVD ROM. I am now downloading that trial version of W8. I called Microsoft and asked for help, but they told me that they couldn't help. What did you do to get them to give you a product key? And where did you get your torrent? I downloaded a torrent of my own but I don't know how trustworthy it is. Thanks everyone-

---

### Post by themanhimself on 2013-06-08
I believe it's against forum policy to link you to a torrent of a paid software but I can assure you they're easy to find. As far as talking to Microsoft, what you need to know is that owning a Lenovo Yoga entitles you to one install of Windows 8 on one hard drive, I'll let you fill in the nefarious bits yourself.

---

### Post by veoozo on 2013-06-08
I've been able to install Windows 8 Enterprise Evaluation (trial) on my Yoga. Now all I need is a danged product key! I've called both Lenovo and Microsoft, but they said that they can't help me. To the user who said they called and got a product key, who did you call, and what did you say?

---

### Post by themanhimself on 2013-06-08
The side button, for locking screen rotation, it's assigned as Super+O in the keyboard shortcut menu but I can't reassign it. Anytime I try to it just performs the samefunction as hitting the Windows key, that is, opening the Unity launcher. Has anyone else played with this? Because what I'm thinking is that we could assign a script to rotate the screen/touchpad orientation to that button while we work on the driver that detects the screen being flipped.

**&#8203;Veoozo**
I don't really think we're on topic with this thread right now, but I told them I had attempted to migrate Windows 8 to a new hard drive and it become deactivated in the process because it was an OEM install. It took a lot of trying.

---

### Post by veoozo on 2013-06-08
I ended up formatting my SSD and installing a pirated version of 8 and using some pirate software to bypass the activation. Thanks everyone for help!

---

### Post by nnod on 2013-06-09
> **themanhimself said:**
> The side button, for locking screen rotation, it's assigned as Super+O in the keyboard shortcut menu but I can't reassign it. Anytime I try to it just performs the samefunction as hitting the Windows key, that is, opening the Unity launcher. Has anyone else played with this? Because what I'm thinking is that we could assign a script to rotate the screen/touchpad orientation to that button while we work on the driver that detects the screen being flipped.

For now I've mapped screen rotation with xrandr and xrandr-align to Ctrl-Alt-O. It would be great to have this side button for that purpose though. I use GNOME 3 and tried to assign it as you suggested but it doesn't work.

xev reports the following on keypress:

```
KeyPress event, serial 37, synthetic NO, window 0x1e00001,
    root 0xa3, subw 0x0, time 16522057, (408,44), root:(410,155),
    state 0x40, keycode 32 (keysym 0x6f, o), same_screen YES,
    XLookupString gives 1 bytes: (6f) "o"
    XmbLookupString gives 1 bytes: (6f) "o"
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x1e00001,
    root 0xa3, subw 0x0, time 16522226, (408,44), root:(410,155),
    state 0x40, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x1e00001,
    root 0xa3, subw 0x0, time 16522231, (408,44), root:(410,155),
    state 0x0, keycode 32 (keysym 0x6f, o), same_screen YES,
    XLookupString gives 1 bytes: (6f) "o"
    XFilterEvent returns: False

```

Holding Super and then pressing 'o' twice results in the shortcut being recognised on the second press of 'o', but the same doesn't work for the side button.

---

### Post by themanhimself on 2013-06-10
> **elfsternberg said:**
> 
It turns out that none of my confusion was my fault.  There's a bug xf86-input-evdev-2.7, the version that ships with Ubuntu 12 (Quantal).  It doesn't handle rotation or inversion well on the ELAN Touchscreens that ship with the Yoga.  It's somewhat understandable-- the Yoga is a very new piece of hardware-- but damn, it's annoying.


I downloaded, compiled and installed xf86-input-evdev-2.8, and now it works.  So if you're feeling brave, that's the way to do it.  Along with the WiFi, you need the latest evdev driver from Xorg, and you'll also be one step closer to having a full set of yoga positions.

I was hoping someone could go into a little more detail on what exactly this means and how best to execute it. Rotating the screen is working quite well but I haven't been able to get the touchpad or touchscreen to orient to the screen direction. I tried what mehanzi said but that didn't work for me so I was hoping to give this a go.
[B]
UPDATE:[/B]I download and installed this ([http://www.linuxfromscratch.org/blfs/view/svn/x/x7driver.html#xorg-evdev-driver](http://www.linuxfromscratch.org/blfs/view/svn/x/x7driver.html#xorg-evdev-driver)), what should I try next?

---

### Post by elfsternberg on 2013-06-11
I've gotten the card reader (the little slot on the right side of the Yoga 13) working.  It's a Realtek 5139.  Unless you've got a kernel that includes all the staging drivers, you'll probably have to rebuild your own kernel, enable staging, and enable Device Drivers -> USB Devices -> Realtek USB Storage.  

Since I'm already feeling crowded on my 256GB hard drive, it's nice to know I can add SSD storage in 128GB increments for about $1 a GB.

---

### Post by themanhimself on 2013-06-12
Hm, that's funny, my card reader worked out of the box

---

### Post by mehanzhi on 2013-06-14
Hello,

I updated the wi-fi driver today from github, but it's working still the same way. 2.5 MB/s max speed.

Anybody manage to get the speed above it? May be wi-fi N standard speed?

---

### Post by adolfino on 2013-06-15
Hello.
Sorry for my english . Thanks to Google Translate.

I installed the kernel 3.9.4 and the speed increased to my maximum.

 If you want to this ,open a terminal and navigate to temporary directory

> cd /tmp

Download the necessary packages:

32bit:

> wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.4-saucy/linux-headers-3.9.4-030904_3.9.4-030904.201305241545_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.4-saucy/linux-headers-3.9.4-030904-generic_3.9.4-030904.201305241545_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.4-saucy/linux-image-3.9.4-030904-generic_3.9.4-030904.201305241545_i386.deb
 
 64bit:

> wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.4-saucy/linux-headers-3.9.4-030904_3.9.4-030904.201305241545_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.4-saucy/linux-headers-3.9.4-030904-generic_3.9.4-030904.201305241545_amd64.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.4-saucy/linux-image-3.9.4-030904-generic_3.9.4-030904.201305241545_amd64.deb


> sudo dpkg -i *.deb 

Update GRUB

> sudo update-grub2

Restart your computer.
Remember that you do so at your own risk.

---

### Post by themanhimself on 2013-06-15
Just thought I'd point out this article about touch features coming to 13.10
[http://www.omgubuntu.co.uk/2013/06/ubuntu-touch-apps-arrive-on-ubuntu-desktop](http://www.omgubuntu.co.uk/2013/06/ubuntu-touch-apps-arrive-on-ubuntu-desktop)

---

### Post by bhowlett on 2013-06-15
I can confirm that this kernel update fixed wifi speeds for me too. Maybe its obvious, but I thought I should mention that the drivers need to be reinstalled after the update.

---

### Post by Jun 1980 on 2013-06-25
> **nago said:**
> Excellent thread, thank you all for the phenomenal detective work.

I can confirm on my Lenovo Yoga 13 (8GB, 128GB) that these WiFi drivers did the trick.

Note, you have to move them / rename the folders they come in such that there are no spaces in the path. Try moving them to ~/rtek for instance-- from there, using make/make install worked wonders. You may need to run ./make_drv to choose which driver to build/use prior to the make/make install -- I wound up compiling and installing both.

Make sure you keep these wifi drivers handy, as every time you update your kernel via regular updates you're going to need them again ...

Edit: Since I haven't seen another good Lenovo Yoga thread on these forums, I should elaborate on my setup:
I purchased the 128GB model, but upgraded manually to a crucial 256GB. I cloned the 128 over to the 256 and then swapped the disks -- This broke windows. I was unable to use any of the built-in recovery tools successfully to repair the installation, but performing a new installation from disc (using a USB cd rom) worked without having to re-enter a key-- W8 recognized the Lenovo/OEM info. I then installed my drivers/programs from the former D:\Lenovo partition to get everything working again.

I then installed Ubuntu 12.10 onto HDD1, the 128GB. The installation worked, but linux was unable to boot successfully -- it couldn't find the root filesystem. I unplugged my 256gb leaving the 128 in the second slot (hdd1) and reinstalled ubuntu. I then plugged the 256gb back in and now I can switch back and forth between W8 and Ubuntu by using the bios button on the Yoga to choose between the two drives at boot time.

I have left Intel Rapid Start, UEFI and secure boot enabled, and everything appears to be working great! The rapid start in particular is still functioning well with windows -- I have startup times of about 4 seconds from a cold boot.

If anyone was interested in a similar setup -- Yes, it can be done. Great machine so far, even if UEFI/GPT and so forth is a little more of a headache than MBR used to be.



Hi hi,

I am also trying to install the wireless drivers to my yoga 13 on ubuntu 13 however I am new and inexperienced to Ubuntu, can you share the commands for installing the drivers using terminal?

Thank you 
J

---

### Post by Jun 1980 on 2013-06-26
Hi all, 

My attempt to install the wireless driver for my yoga 13 got stalled at the make command line

jun@Thinktoy:~/rtl8723a$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.8.0-25-generic/build M=/home/jun/rtl8723a  modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-25-generic'
  CC [M]  /home/jun/rtl8723a/core/rtw_cmd.o
In file included from /home/jun/rtl8723a/core/rtw_cmd.c:23:0:
/home/jun/rtl8723a/include/osdep_service.h: In function &#8216;thread_enter&#8217;:
/home/jun/rtl8723a/include/osdep_service.h:1418:2: error: implicit declaration of function &#8216;daemonize&#8217; [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/home/jun/rtl8723a/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/jun/rtl8723a] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-25-generic'
make: *** [modules] Error 2

then I try installing the wireless driver: 

jun@Thinktoy:~/rtl8723a$ make install
install -p -m 644 8723au.ko  /lib/modules/3.8.0-25-generic/kernel/drivers/net/wireless/
install: cannot stat &#8216;8723au.ko&#8217;: No such file or directory
make: *** [install] Error 1

I got these, how do I solve these issues and eventually successfully install the wireless driver?

Thank you 
J

---

### Post by bhowlett on 2013-06-26
Hi Jun 1980,

Did you follow the instructions that Joon posted? (see below)

> **joonpy said:**
> Larry Finger has set up a github repo of the wireless driver: [https://github.com/lwfinger/rtl8723au](https://github.com/lwfinger/rtl8723au)

$ git clone [http://github.com/lwfinger/rtl8723au.git](http://github.com/lwfinger/rtl8723au.git) 
(if you don't have git, download the .zip archive)

$ cd [rtl8723au]("http://github.com/lwfinger/rtl8723au.git")

$ make && sudo make install

Will compile & install the driver. I have tested it and it works well on my Yoga 13.

-Joon

This worked for me. Also I had my system up to date with:

```
sudo apt-get update && sudo apt-get upgrade

```

I had a working internet connection through a usb adapter though, if you don't have that then I'm not sure what you can do to get your system up to date.

---

### Post by Jun 1980 on 2013-06-26
Thanks a million bhowlett, it works wonderfully now

---

### Post by Jun 1980 on 2013-06-26
Hi bhowlett, 

The internet works but when i tried to increase the speed as suggested i got the following

jun@Thinktoy:~/tmp$ wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.4-saucy/linux-headers-3.9.4-030904_3.9.4-030904.201305241545_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.4-saucy/linux-headers-3.9.4-030904_3.9.4-030904.201305241545_all.deb) [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.4-saucy/linux-headers-3.9.4-030904-generic_3.9.4-030904.201305241545_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.4-saucy/linux-headers-3.9.4-030904-generic_3.9.4-030904.201305241545_amd64.deb) [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.4-saucy/linux-image-3.9.4-030904-generic_3.9.4-030904.201305241545_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.4-saucy/linux-image-3.9.4-030904-generic_3.9.4-030904.201305241545_amd64.deb)
--2013-06-27 09:18:47--  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.4-saucy/linux-headers-3.9.4-030904_3.9.4-030904.201305241545_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.4-saucy/linux-headers-3.9.4-030904_3.9.4-030904.201305241545_all.deb)
Resolving kernel.ubuntu.com (kernel.ubuntu.com)... 91.189.94.216
Connecting to kernel.ubuntu.com (kernel.ubuntu.com)|91.189.94.216|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 12436934 (12M) [application/x-debian-package]
Saving to: &#8216;linux-headers-3.9.4-030904_3.9.4-030904.201305241545_all.deb&#8217;


100%[======================================>] 12,436,934  2.37MB/s   in 9.0s   


2013-06-27 09:18:58 (1.32 MB/s) - &#8216;linux-headers-3.9.4-030904_3.9.4-030904.201305241545_all.deb&#8217; saved [12436934/12436934]


--2013-06-27 09:18:58--  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.4-saucy/linux-headers-3.9.4-030904-generic_3.9.4-030904.201305241545_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.4-saucy/linux-headers-3.9.4-030904-generic_3.9.4-030904.201305241545_amd64.deb)
Reusing existing connection to kernel.ubuntu.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 968486 (946K) [application/x-debian-package]
Saving to: &#8216;linux-headers-3.9.4-030904-generic_3.9.4-030904.201305241545_amd64.deb&#8217;


100%[======================================>] 968,486     58.1KB/s   in 9.7s   


2013-06-27 09:19:08 (97.6 KB/s) - &#8216;linux-headers-3.9.4-030904-generic_3.9.4-030904.201305241545_amd64.deb&#8217; saved [968486/968486]


--2013-06-27 09:19:08--  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.4-saucy/linux-image-3.9.4-030904-generic_3.9.4-030904.201305241545_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.4-saucy/linux-image-3.9.4-030904-generic_3.9.4-030904.201305241545_amd64.deb)
Reusing existing connection to kernel.ubuntu.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 45035436 (43M) [application/x-debian-package]
Saving to: &#8216;linux-image-3.9.4-030904-generic_3.9.4-030904.201305241545_amd64.deb&#8217;


100%[======================================>] 45,035,436  2.45MB/s   in 30s    


2013-06-27 09:19:38 (1.42 MB/s) - &#8216;linux-image-3.9.4-030904-generic_3.9.4-030904.201305241545_amd64.deb&#8217; saved [45035436/45035436]


FINISHED --2013-06-27 09:19:38--
Total wall clock time: 51s
Downloaded: 3 files, 56M in 49s (1.14 MB/s)
jun@Thinktoy:~/tmp$ sudo dpkg-i*.deb
[sudo] password for jun: 
sudo: dpkg-i*.deb: command not found

how to proceed if the command is not recognised? 

Thank you 
J

---

### Post by bhowlett on 2013-06-26
try:

sudo dpkg -i *.deb

you need the spaces in there.

EDIT: ok, so the font in this forum (at least on my computer) makes it look like all one command. Either copy and paste what I typed or remember to put a space between 'dpkg', '-i', and '*.deb'

---

### Post by Jun 1980 on 2013-06-26
Hi bhowlett, 

Thanks again, I install the 3 kernels from the software centre and also update the grub then I reinstalled the drivers but now the laptop established wireless connection but I can't get internet connection. 

How do I find out what the issue is and how do i remedy it?

Thanks yet again
J

---

### Post by Jun 1980 on 2013-06-26
Hi bhowlett, 

I fixed the problem by getting windows to release the ip

ipconfig /release on windows

it worked

thanks all the same ;)

---

### Post by Jun 1980 on 2013-06-27
Hi again, 

It seems the ipconfig /release on my windows 8 desktop worked momentarily only. Again I have wireless established but internet connection. Please help. 

Thank you 
J

---

### Post by mehanzhi on 2013-06-27
Hello [**[COLOR=#000000]Jun 1980[/COLOR]**]("http://ubuntuforums.org/member.php?u=1833918"),

Did you try setting up a static IP? Did you try ping something in your local network? The router or the DHCP server for example.
Can you post the output of "ifconfig -a"  and "netstat -rn" commands please? Should be executed after you connect to the wi-fi network.

Thank you.

---

### Post by mehanzhi on 2013-06-30
Hello penguins,

I notice that the speakers on my Yoga 12 are 2 stereo in the 2 ends of the keyboard. 

But using Fedora 18, only the left speaker works. Putting the headset, both speakers work perfectly. But when I am using the Yoga speakers, I got only left speaker.

First idea I got was a hardware problem, because if it was a driver issue, headset wouldn't work on stereo too. However I don't have the time and patient to install Windows 8 and test it.

Does anybody else have the same problem? If it's just me I guess I'll assume that it's a hardware issue :(

Thank you.

---

### Post by insyder5000 on 2013-07-01
Using 13.04, It seems like both of my speakers are working

---

### Post by esion on 2013-07-03
Hi, 

Does anyone knows how to setup automatic screen rotation ?

I saw this thread for an Acer : [http://ubuntuforums.org/showthread.php?t=1486671&page=5](http://ubuntuforums.org/showthread.php?t=1486671&page=5) . I suppose the Yoga has a gyro-sensor-thing somewhere, I don't know how to detect it.

PS: I created a french wiki page for the lenovo using this thread; Thank you all. 
[http://doc.ubuntu-fr.org/lenovo_yoga_13](http://doc.ubuntu-fr.org/lenovo_yoga_13)

---

### Post by asymingt on 2013-07-07
The Lenovo 13 motion sensor is connected over USB. If you type 'lsusb' you'll see it detected as "Bus 002 Device 003: ID 2047:0855 Texas Instruments". I am under the impression that Invensense (the motion processor manufacturer) produces a chipset that registers itself as a TI instrument. Unfortunately, the Product ID is not known. The USB device descriptors look something along the lines as the MSP Debug protocol (see here: [http://mspdebug.sourceforge.net/usb.html](http://mspdebug.sourceforge.net/usb.html)). My guess is that the motion processing chipset is an vendor solution offered by invensense. Lenovo is likely to have written some custom device firmware (+ window drivers) to offload orientation estimation to the chipset. My guess is that we may need to reverse engineer some drivers.


> **esion said:**
> Hi, 

Does anyone knows how to setup automatic screen rotation ?

I saw this thread for an Acer : [http://ubuntuforums.org/showthread.php?t=1486671&page=5](http://ubuntuforums.org/showthread.php?t=1486671&page=5) . I suppose the Yoga has a gyro-sensor-thing somewhere, I don't know how to detect it.

PS: I created a french wiki page for the lenovo using this thread; Thank you all. 
[http://doc.ubuntu-fr.org/lenovo_yoga_13](http://doc.ubuntu-fr.org/lenovo_yoga_13)

---

### Post by AbsoluteZ3r0 on 2013-07-10
Hey guys and gals,

I just got a yoga and am having a difficult time trying to get WiFi up and running.
I have spent over 7 hours now and have gotten no where.
I'm assuming I'm just doing something wrong from the start but I'm not really sure.
I keep having trouble when I type:
make

I get an output that is saying something about 'implicit declaration of function 'daemonize'
and then it goes on to say:
make: *** [modules] Error 2

Are you guys able to give me any assistance?
Thank you in advance!

---

### Post by bhowlett on 2013-07-10
> **AbsoluteZ3r0 said:**
> Hey guys and gals,

I just got a yoga and am having a difficult time trying to get WiFi up and running.
I have spent over 7 hours now and have gotten no where.
I'm assuming I'm just doing something wrong from the start but I'm not really sure.
I keep having trouble when I type:
make

I get an output that is saying something about 'implicit declaration of function 'daemonize'
and then it goes on to say:
make: *** [modules] Error 2

Are you guys able to give me any assistance?
Thank you in advance!

Hey,

Have you tried what I said in post #166? I believe having your system up to date should help. Also what version of ubuntu are you using?

---

### Post by AbsoluteZ3r0 on 2013-07-10
bhowlett,
Thank you so very much! I can't belive I spent all day trying different things when it was right there!!!!

I am running 13.04 and internet is running smooth!!

Thank you again!!!

---

### Post by bhowlett on 2013-07-10
No problem! Usually the first thing I try is an update.

---

### Post by ajicaribe on 2013-07-18
I'm going to install UBUNTU in my new Yoga 11S, the one with the I5 not the Arm Processor, I am almost sure it has the same wifi module you mention in this thread... It has the same number as the Drivers I will have to install... but I need to know which version of Ubuntu you would recommend the 12.04 or the 13 ??

---

### Post by themanhimself on 2013-07-19
I don't know a reason not to go with the 13

---

### Post by mrayyy on 2013-08-13
Having a Yoga 13 and running Ubuntu 13.10.

Touchscreen has some nasty issue: right after boot tipping the screen stops behaving like a left-click!
This means it is impossible to start launchers from the side or scroll in a browser,... what to do?
Is anybody else having that issue?

I would be happy for any directions or ideas how to tackle this.

---

### Post by esion on 2013-08-13
Similar behavior here with 13.04.

Sometimes touch screen only move cursor and sometimes lock screen or restart session do the touch events working as expected. I didn't find why.
But certain applications always work great with touch : pdf reader, [gitg]("https://wiki.gnome.org/Gitg").

---

### Post by mehanzhi on 2013-08-15
Hello,

I am not sure how it is looking in ubuntu, but there is bug with gnome-shell 3.8 and touchscreen.
Please check this bugzilla ticket and the links in the description [https://bugzilla.redhat.com/show_bug.cgi?id=990104](https://bugzilla.redhat.com/show_bug.cgi?id=990104) 
The issue seems to be in the xorg server and in the gnome bugzilla, they say it is fixed, but it is not applied yet in Fedora and probably ubuntu too. 

Still if this is the same thing I am thinking :)

---

### Post by don-park on 2013-08-26
I use Ubuntu 13.10 on my Yoga 13 every day and I overall love the experience. At the same time I overlook plenty of problems but there is one that is driving me *insane*.

The keyboard will go into a key-repeat for no reason while using the arrow keys. About every 15 minutes of regular keyboard usage, I'll go left once or hold it down for a few repeats, and the system will do a thousand left repeats.

the only clue is the dmesg log fills up with

[86632.115526] atkbd serio0: Unknown key pressed (translated set 2, code 0xbe on isa0060/serio0).
[86632.115537] atkbd serio0: Use 'setkeycodes e03e <keycode>' to make it known.

I've googled for this error and there is a report of it being a 'kernel regression' in the touchpad driver, but no solutions that I saw.

Are other people seeing this? Has someone found a fix? I would really like to get this fixed!

Thanks
Don

---

### Post by mehanzhi on 2013-08-31
Hello,

I am a Fedora user and I have never experience such troubles. 
I tried to reproduce your bug, but didn't work.

Can you post your kernel version please?

Also have you tried to update the kernel? May be different release will have this issue fixed.

Thank you.

---

### Post by elfsternberg on 2013-09-01
> **asymingt said:**
> The Lenovo 13 motion sensor is connected over USB. If you type 'lsusb' you'll see it detected as "Bus 002 Device 003: ID 2047:0855 Texas Instruments". I am under the impression that Invensense (the motion processor manufacturer) produces a chipset that registers itself as a TI instrument. Unfortunately, the Product ID is not known. The USB device descriptors look something along the lines as the MSP Debug protocol (see here: [http://mspdebug.sourceforge.net/usb.html](http://mspdebug.sourceforge.net/usb.html)). My guess is that the motion processing chipset is an vendor solution offered by invensense. Lenovo is likely to have written some custom device firmware (+ window drivers) to offload orientation estimation to the chipset. My guess is that we may need to reverse engineer some drivers.

Yeah, I was afraid of that.  I'm not much for writing m own device drivers, although I did write one, for a joystick, many years ago, for the 2.2 kernel line.  I've tried hooking up wireshark to usbmon, or even cat'ting the usbmon directly for that device, and nothing happens!  I'm not sure why we're not even seeing events of any kind off the Invensense device.  I suspect there's something the driver has to do to "awaken" the device, but I wouldn't know where to begin with that.

---

### Post by andrew-c-symington on 2013-09-03
> **elfsternberg said:**
> Yeah, I was afraid of that.  I'm not much for writing m own device drivers, although I did write one, for a joystick, many years ago, for the 2.2 kernel line.  I've tried hooking up wireshark to usbmon, or even cat'ting the usbmon directly for that device, and nothing happens!  I'm not sure why we're not even seeing events of any kind off the Invensense device.  I suspect there's something the driver has to do to "awaken" the device, but I wouldn't know where to begin with that.

I also tried Wireshark in Ubuntu with no luck. I had better luck sniffing the USB packets from within Windows 8. Busdog and USSSnoop didn't work for me, but USBlyzer did. However, it caused many other USB peripherals to function strangely. I unfortunately didn't have the time to finish off what I was doing, and record a trace. Perhaps you will have better luck!

---

### Post by internalkernel on 2013-09-07
Thanks to everyone in this thread... All 19 pages, helped me decide that I'd give the Yoga 11 a try. After a couple days of fiddling, I think I've finally got this thing to a workable state. The wireless instructions in this thread got me online, as well as the backlight instructions. I can also report that the touchscreen is working very well; I can click and double-click... It took a good amount of fiddling, but in the end proved useful.

I have the Yoga 11S with the 3rd Gen I5, running 13.04. The video card proved to be problematic at first, the i915 driver had to be downloaded and installed from Intel directly. They did make it rather easy, I found an installer for the drivers here:

[https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)

For compatibility needs I also installed the xorg-edgers ppa, then ran the intel installer. I should probably mention that particular ppa is fraught with dire warnings about xserver eating kittens or something - it seems to work, but be warned... YMMV.

The touchscreen was flaky at first... It would work as expected for about 30 seconds and then fail - as others reported. Xorg.log showed a bug trace, I started searching this down and it brought me to this bug report on Xserver: 

[https://bugs.freedesktop.org/show_bug.cgi?id=56578](https://bugs.freedesktop.org/show_bug.cgi?id=56578)

which is a long read, almost as long as this thread... I actually read it and finally performed these instructions:

[http://askubuntu.com/questions/339365/ubuntu-13-04-touch-screen-points-though-doesnt-click](http://askubuntu.com/questions/339365/ubuntu-13-04-touch-screen-points-though-doesnt-click)

and after a reboot... the touchscreen has been surprisingly stable. Just don't try to resize any windows... it doesn't like that. But, hey... that's life on the bleeding edge, right?

Some probably relevant details:

```

lspci
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)

xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Atmel Atmel maXTouch Digitizer          	id=9	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]

```

Scrolling in Firefox doesn't work, but an add-on called Grab and Drag fixed that. 

Right click is non-functional, I haven't traced this down and don't know if it's possible. A work around is to use the mouse functions on Onboard but even then, it's been flaky.

On a side note, I discharged it once yesterday and it seemed to be just under 5 hours of medium usage at about 50% brightness.

---

### Post by chrisandharris on 2013-09-10
Wonderful thread, huge thanks to everyone contributing here!

Just a note for those with troubles attempting a clean install, I was having trouble installing on newly defined partitions (even through manual means) with the following error "The attempt to mount a file system with type vfat in SCSI2 (0,0,0), partition #1 (sda) at /boot/efi failed. You may resume partitioning from the partitioning menu."  I found out that I had to delete the ntfs efi partition manually in a live boot before I could attempt the install using gpart.  Thanks to this thread: [http://ubuntuforums.org/showthread.php?t=202153](http://ubuntuforums.org/showthread.php?t=202153)

Finally feels good to get be clean of that icky M$ feeling :p

---

### Post by Graham_White on 2013-09-14
Thanks for this thread: really helpful. I have a Lenovo Yoga 11S (i5 processor), and I have installed the
Realtek drivers, and the wireless not works very well. What doesn't seem to work well is the touchpad, which is periodically very flaky: I get the cursor suddenly shifting to top right or bottom left corners of the screen, or 
random cursor movements. Also the output of xinput test shows that the scroll wheel (however that's mapped inot
touchpad gestures), is periodically being activated, even though I don't think I'm doing anything to do that (though it's 
hard to tell because the touchpad seems to be richly endowed with mysterious gestures). Anybody else come across these problems? I'll try to get together some documentation on this in the next day or so.

Graham

---

### Post by xanxa2 on 2013-09-15
Hello all :D

after skimming all 20 pages - all the progress is only on Yoga with intel procesor

so is it safe to say that its impossible to install ubuntu on Yoga 11 - ARM processor??

---

### Post by andrew-c-symington on 2013-09-17
Did anybody else have WiFi issues return when upgrading to kernel 3.8.0-30-generic? I'm using a third party kernel driver ([https://github.com/lwfinger/rtl8723au](https://github.com/lwfinger/rtl8723au)) which, up until this point, has worked for every kernel; I've needed to recompile it every time, though. I've also tried a git pull and recompile with no luck. Any suggestions? A

---

### Post by Habermas on 2013-09-20
What do you think, is there a chance that in the future we might be able to install ubuntu on Yoga 11 (ARM cpu)? And if so then what are your estimations on when?

---

### Post by Alkasel on 2013-09-20
Hi All! I've read half of this 20-pages topic and still I'm hesitant: should I but or not Lenovo Yoga 11s? (My choice would be that: [http://compraonline.mediaworld.it/webapp/wcs/stores/servlet/ProductDisplay?catalogId=20000&storeId=20000&productId=23726780&langId=-1](http://compraonline.mediaworld.it/webapp/wcs/stores/servlet/ProductDisplay?catalogId=20000&storeId=20000&productId=23726780&langId=-1))
What you suggest me? I use linux since 2 years, but I prefer not to have to spend one week to configure it...(I would like to use Debian or Ubuntu or Linux Mint)
thanks! (sorry for bad english!)

---

### Post by ABBzptT on 2013-09-22
> **don-park said:**
> I use Ubuntu 13.10 on my Yoga 13 every day and I overall love the experience. At the same time I overlook plenty of problems but there is one that is driving me *insane*.

The keyboard will go into a key-repeat for no reason while using the arrow keys. About every 15 minutes of regular keyboard usage, I'll go left once or hold it down for a few repeats, and the system will do a thousand left repeats.

the only clue is the dmesg log fills up with

[86632.115526] atkbd serio0: Unknown key pressed (translated set 2, code 0xbe on isa0060/serio0).
[86632.115537] atkbd serio0: Use 'setkeycodes e03e <keycode>' to make it known.

I've googled for this error and there is a report of it being a 'kernel regression' in the touchpad driver, but no solutions that I saw.

Are other people seeing this? Has someone found a fix? I would really like to get this fixed!

Thanks
Don

I have this problem too. It happens with PgUp, PgDn and the arrow keys. I've also noticed it with Delete. It is particularly annoying in eog when browsing photographs, you have to be careful - you think you are deleting one photo but the key gets stuck and deletes hundreds if the confirmation is turned off!

I have checked with xev and it appears that the key release signal is not received. I thought it might be a BIOS issue. Has anyone noticed this while using Windows 8?

The messages you see are not related to the sticky keys. You can turn those off using sudo setkeycodes e03e 255 for your current session, but it seems to revert to that behaviour again after waking up from sleep.

---

### Post by della2 on 2013-09-25
Hello everybody,

I'm considering whether to buy an IdeaPad... and I'm a bit confused about the status of Ubuntu support.

Is there a list of what works & what doesn't at the moment? Is it possible to use multi-touch on the touchscreen?

thanks a lot!

---

### Post by themanhimself on 2013-09-27
Does the 13.10 beta have any better touchscreen support?

---

### Post by vak on 2013-10-11
> **ABBzptT said:**
> I have this problem too. It happens with PgUp, PgDn and the arrow keys. I've also noticed it with Delete. It is particularly annoying in eog when browsing photographs, you have to be careful - you think you are deleting one photo but the key gets stuck and deletes hundreds if the confirmation is turned off!

I have checked with xev and it appears that the key release signal is not received. I thought it might be a BIOS issue. Has anyone noticed this while using Windows 8?

The messages you see are not related to the sticky keys. You can turn those off using sudo setkeycodes e03e 255 for your current session, but it seems to revert to that behaviour again after waking up from sleep.
This is 1 of 3 things why I am going to return the nice Lenovo Yoga to the seller:
1. Random sticky key issue
2. WiFi works not for all WiFi-routers
3. One can't easily click the desired target without having the mouse pointer moved. The touchpad buttons are unwantedly sensitive to mouse pointer movements :(

---

### Post by accek on 2013-10-14
> **liquidator87 said:**
> Does anyone have problems with build-in microphone and Skype? The microphone is recognized, but it works very badly... it produces a lot of noise and my words are understandable if I shout and speak slowly

I think this has just been patched in the kernel, see [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1239392](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1239392).
It should end up in the audio drivers daily builds soon, and then they can be installed this way:

```
sudo apt-add-repository ppa:ubuntu-audio-dev/alsa-daily
sudo apt-get update
sudo apt-get install oem-audio-hda-daily-dkms
```

---

### Post by ozydingo on 2013-11-05
> **mehanzhi said:**
> Hello,

**Keyboard and touchpad disabling in tablet mode:**

I have a script that disables and enables the touchpad. It is working fine, but I need an idea how can I detect the screen turning, so I can put there the script execution. 
The keyboard is disabled then turning the screen, but I have no idea how to trace the action. If anybody have idea, please share it and I'll test ;). 

Have you made any progress on this? I am trying to figure out how to automatically kick off a script when the yoga flips into tablet mode.  Apparently some lenovo convertibles have events that trigger acpi actions listed in /etc/acpi/events, but I cannot figure out how to detect such events form the Yoga.

---

### Post by mehanzhi on 2013-11-06
Hello **ozydingo**

I haven't found a way to trace the turning of the screen. 
I think that the keyboard switch is a hardware not software, because I know that the keyboard is switched off after flippIing the screen. I tried to monitor with *udevadm monitor*, but I saw not a single event. Still the keyboard is turned off.
Then I tried it in the BIOS and in grub2 menu during boot. I am sure that there can not be loaded any drivers and I was right. The keyboard was turned off even outside the OS.

But the touchpad is using some kind of software switch and since udev detects no events, I can not execute any action. That ACPI events may be a good idea, I'll try to get something as a trigger based on this events and I'll post answer. 

However, so far I was perfectly happy using software scripts and gnome menu items for triggers to disable touchpad and rotate the screen. Earlier I could trigger a script using the small button on the right side that I think is used to lock screen rotation in windos. But after some kernel updates, I can't assign any action to this button. It's detected as "O", or Ctrl+O and the keyboard shortcuts tool can capture it and assign action on this button, but when I try to trigger it, nothing happens. Anybody have the same issue? Any workaround? 

Thankyou.[B]


[Edit1][/B]

Sorry, but I wasn't able to detect any acpi events with acpid. The command is very simple, you just type as root: ***acpi_listen*** and you rotate the screen, push buttons or whatever you wish to.
Pressing the buttons for volume control or brithness of the screen works fine and generates ACPi events, but the screen rotation and flip does not.

---

### Post by CaptainFuzzyFace on 2013-11-26
Did anyone ever find a way to get bluetooth working? I have Ubuntu on my Yoga 13 but still no bluetooth. The Software Centre doesn't work either, but I have a work around for that.

---

### Post by ozydingo on 2013-11-29
Thanks for the effort & info. I've found the same results with the rotate lock button, though it's detected here as Super + O (even down to using showkey -s to monitor the scan code). I wonder what's going on that it can't be used to trigger anything.

The last lead I was trying to work on is here - [https://gist.github.com/emiller/6488449](https://gist.github.com/emiller/6488449) - where he claims the yoga emits the keycode e03e at regular intervals when the screen is flipped. I cannot see this code emitted. Perhaps it's a difference with the Yoga vs. Yoga 2? Can you confirm anything that post says on your end?

---

### Post by ozydingo on 2013-11-29
Bluetooth worked out of the box for my Yoga 2. I don't know what the hardware & software differences are exactly, but I'm happy to report the contents of any configuration files if you can tell me where to look.

---

### Post by DOS286 on 2013-12-31
I spent some time and got screen rotation functioning with scripts, following post 104 by mehanzhi (Thank you!). It took me a while to sort out the dependencies. I thought that I would post them in case it helps any one else:

sudo apt-get install xutils-dev libx11-dev libxi-dev libxrandr-dev

I was able to assign a script to the "lock screen" button on the right side of the keyboard. Others have said that it does not work for them. I did not do anything special, it just worked, so I don't know what to tell you. The script I assigned rotates through each of the orientations. It also turns off the touch pad for right, inverted, and left, and turns it back on when it gets to normal. I also have Gnome Shell favorite buttons to toggle the touch pad, jump to a specific screen orientation, and bring up the On Board keyboard. These scripts also assume default touchpad states. For me that's the simplest solution until automatic screen rotation and touchpad deactivation are figured out.

Thanks to this thread, I now have a very functional Ubuntu Yoga!

---

### Post by tumerictj on 2013-12-31
Hey Brave Ones---

I have skimmed this whole thread.
I was raving about how nice it would be for my sister (a Windows user) to have a Yoga, and then my family got me one for Christmas.

I would like to keep it and use as much as possible with Ubuntu, but it would be my primary machine for school (I'm a Math undergraduate, last year).
I have an i7 with 256GB of storage, so I though maybe I could dual boot 128GB/128GB with Windows until the scarier Linux issues are ironed out.
Poor wifi and the repeating key thing are my biggest concerns.
I'm no Linux guru, but do have a little bit of technical experience/interest from school and using Ubuntu for a couple years.

On the other hand, it might not make that much sense to have a computer the special feature of which is tablet functionality if I have to use Windows all the time.  As Ubuntu 13.10 is out now, I just thought I would ask if any people are successfully using this for work, etc., and what their recommendations are.
And, specifically,
(1) Should the Windows partition still have the same performance if I dual boot?
(2) Is compatibility likely to be better with Ubuntu 14.04?

Thanks in Advance,
T

---

### Post by DOS286 on 2013-12-31
Hi Tumerictj,

I'm running Ubuntu 13.10 on a Yoga 13 I received for Christmas. I never had any issues with wifi or repeating keys. Reading the thread it sounds like the WIFI issue was fixed with a kernel update some time ago. Apparently repeating keys only affects some.

I'm still setup to dual boot, but I've not used Windows for anything, only Ubuntu. Tablet mode is surprisingly usable for me. The only thing lacking is auto-rotate of the screen and auto-deactivate of the touchpad. These are done with scripts that are run from shortcuts on the screen and the little button on the right side of the machine. The built-in supper key on the screen is very useful in tablet mode as well.

I'm not a computer expert but I don't know why the windows partition would suffer from dual boot. Should be just as fast. I don't know what changes are in store for 14.04, but in general compatibility with existing machines increases with each new version.

Have fun!

---

### Post by christopherhartley on 2014-01-08
Just got my Yoga 13 and added a crucial SSD into the second SSD.  I tried to create an EFI partition on the second SSD and point the Ubuntu (13.10) installer to that one, thus leaving the factory SSD unchanged.  When I reboot the first time I get GRUB, but after that I see 3 boot options in the BIOS, one for windows and two for Ubuntu, but all three reference the factory SSD and all three boot into Windows.  I should also mention that I thought I had dual boot working fine in this configuration, but my next step was to upgrade to windows 8.1 and it would seem that broke my dual boot.  I'm just not confident that is what did it because I didn't switch back and forth very many times before I did the 8.1 update.  My other idea is to reset back to factory and do the 8.1 update first and then install Ubuntu second.

---

### Post by qwesp on 2014-01-09
You could try to repair boot with [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") first.

---

### Post by tumerictj on 2014-01-09
I'm not sure if my situation is pertinent to yours, but something similar happened to me when I tried to dual boot.
After a bit of research, I decided to install from a live usb without disabling secure boot or fast startup.
Niether was mentioned as necessary to disable by the Ubuntu [documentation]("https://help.ubuntu.com/community/UEFI") which I consulted on UEFI.
However, I did read here the recommendation to have only a single EFI boot partition.

I have now disabled fast startup because Ubuntu (and the Web) warned me that Ubuntu-Windows data sharing was unstable without Windows fully shut down.
That is, fast boot is not a problem, but it must be disabled so that Windows may be fully shut down before one accesses files from Windows through Ubuntu.

The Ubuntu installer did not detect another operating system, so I had to use the "something else" manual partitioning option.
After the installation, I was left with an option for Ubuntu and an option for Windows at the GRUB menu .
I tried the Ubuntu option and it worked fine.
I tried the Windows options and it didn't work.

I searched for what the problem might be and decided to try pressing F12 at startup before the GRUB menu popped up.
This gave me a different option to boot into Windows which was successful. 
 I had read that there was a [GRUB bug]("http://ubuntuforums.org/showthread.php?t=2085530") which lead to the useless option.

---

### Post by christopherhartley on 2014-01-10
Thanks, I'll be doing some experimenting this weekend.  So do you now have 1 EFI partition or 2?

---

### Post by rangedenemy on 2014-01-10
Hi, I'm trying to dual boot ubuntu on my new yoga ultrabook, but every time I boot from my 13.10 flash drive, I can hear the loader make that drumming noise in the background, but the screen is blank and I can't see anything. I had this experience with my last laptop, but I disabled safe boot and it worked fine. This time I have disabled safe boot and switched to legacy instead of uefi. Any help would be appreciated thanks.

---

### Post by tumerictj on 2014-01-13
Just one.

---

### Post by pfpschneider on 2014-01-14
Has anyone been able to get all the keys on the Yoga 13 (and Yoga 2 Pro) to work correctly?

Most of them work out of the box, I'm having various issues:
1/ Pause and Break seem to be producing the same scan codes
2/ Refresh (F5), Open Apps (F8), and Switch Display (F10) don't seem to be hooked up to anything (in XFCE)
3/ ToggleTouchpad (F6), Toggle Airplane (F7), and Toggle Screen Light (F9) don't appear to produce any output, although the last does toggle the screen light
4/ The Windows button on the screen produces the same code as the Windows button on the keyboard
5/ The Volume Up and Down buttons on the side produce the same codes as the Volume Up and Down keys
6/ The Rotation Lock button isn't hooked up to anything (in XFCE)

Any pointers in getting these things to work?


Also, has anyone had any luck in getting the sensors to work?  [I have had some luck, but there are still issues.]

---

### Post by tumerictj on 2014-01-14
Regarding the screen rotation, I obtained the following error when trying to install xrandr-align:
/usr/bin/install: cannot remove '/usr/local/bin/xrandr-align': Permission denied.
Installing as root was successful, but maybe a bad idea.

In any case, the xrandr -o rotation commands rotated the display for me, but not the touchpad (or touchscreen) input.

---

### Post by tumerictj on 2014-01-14
I found a straightforward answer to one of my questions by reading the helpful information at [https://wiki.ubuntu.com/X/InputCoordinateTransformation](https://wiki.ubuntu.com/X/InputCoordinateTransformation).

The commands  
(1)```
xrandr -o <orientation>
``` and  
(2)```
`xinput set-prop '<device name>' 'Coordinate Transformation Matrix' <matrix-elements-rowwise>`
```  
can be used to align rotations of the input devices (that is, the touchscreen and touchpad) and the display.

The first command rotates the display, where ```
<orientation>
``` is left, right, normal, or inverted.
The second command remaps the input device, where ```
<matrix-elements-rowwise>
``` is 0 -1 1 1 0 0 0 0 1, 0 1 0 -1 0 1 0 0 1, 1 0 0 0 1 0 0 0 1, or -1 0 1 0 -1 1 0 0 1 corresponding to the orientations above.

The names of the touchscreen and touchpad can be found with ```
xinput list
``` and either can be disabled entirely with ```
xinput disable <device-name>
```
Subsequently, ```
xinput enable <device-name>
``` will re-enable the input device.

---

### Post by arttuhon on 2014-01-22
Hi forum,
I'm a bit confused is there good automatic rotation at the moment or not? 
atleast seems like we are really close to it? If you have ok working solution please let me know.
I'm also really interested on applications where you use touch screen, which are your favorite ones?

I got my ultrabook yesterday and already clean installed ubuntu on it. I'm really happy how it works :) After reading forums I expected way worse.
Cheers,
Arttu

ps. batterylife about 6h here with surfing and downloading software and emails.

---

### Post by vak on 2014-01-24
"Random sticky key" issue disappeared about two months ago and today after an ubuntu update it returned back ((
Anyone knows why?

---

### Post by mehanzhi on 2014-01-24
Hello my fellow penguins,

I'd like to put a few words about the screen rotation.
In the thread, I suggested some pages backward that xrandr-align is nice solution. However, after I updated to Fedora 20 (gnome-shell 3.10, because Fedora 19 with version 3.8 has touchscreen issues) I got some nasty errors and troubles during xrandr-align install. Some google search and another post in this thread gave me the right idea that xrandr can do this all without installing another software. 
Then I rewrite my scripts as follows:
Left rotation:
```
bash-4.2$ cat /usr/bin/rotate-left.sh 
#!/bin/sh
rotation=`xrandr -q --verbose |grep LVDS1 |cut -d ' ' -f6`
if [ $rotation = "normal" ] ;
then
  xrandr -o left
   xinput set-prop 'SynPS/2 Synaptics TouchPad' 'Coordinate Transformation Matrix' 0 -1 1 1 0 0 0 0 1
   xinput set-prop 'ELAN Touchscreen' 'Coordinate Transformation Matrix' 0 -1 1 1 0 0 0 0 1
   /usr/bin/touchpad.sh
else
  xrandr -o normal
  xinput set-prop 'ELAN Touchscreen' 'Coordinate Transformation Matrix' 1 0 0 0 1 0 0 0 1
  xinput set-prop 'SynPS/2 Synaptics TouchPad' 'Coordinate Transformation Matrix' 1 0 0 0 1 0 0 0 1
  /usr/bin/touchpad.sh
fi

```
RIfht rotation:
```
bash-4.2$ cat /usr/bin/rotate-right.sh 
#!/bin/sh
rotation=`xrandr -q --verbose |grep LVDS1 |cut -d ' ' -f6`
if [ $rotation = "normal" ] ;
then
  xrandr -o right
   xinput set-prop 'SynPS/2 Synaptics TouchPad' 'Coordinate Transformation Matrix'  0 1 0 -1 0 1 0 0 1
   xinput set-prop 'ELAN Touchscreen' 'Coordinate Transformation Matrix'  0 1 0 -1 0 1 0 0 1
   /usr/bin/touchpad.sh
else
  xrandr -o normal
  xinput set-prop 'ELAN Touchscreen' 'Coordinate Transformation Matrix' 1 0 0 0 1 0 0 0 1
  xinput set-prop 'SynPS/2 Synaptics TouchPad' 'Coordinate Transformation Matrix' 1 0 0 0 1 0 0 0 1
  /usr/bin/touchpad.sh
fi
```
Flip over:
```
bash-4.2$ cat /usr/bin/rotate-flip.sh 
#!/bin/sh
rotation=`xrandr -q --verbose |grep LVDS1 |cut -d ' ' -f6`
if [ $rotation = "normal" ] ;
then
  xrandr -o inverted
   xinput set-prop 'ELAN Touchscreen'  'Evdev Axis Inversion' 1, 1
   xinput set-prop 'ELAN Touchscreen' 'Evdev Axes Swap' 0
else
  xrandr -o normal
   xinput set-prop 'ELAN Touchscreen' 'Evdev Axis Inversion' 0, 0
   xinput set-prop 'ELAN Touchscreen' 'Evdev Axes Swap' 0
fi
```
And I also added the touchpad disable trigger in the scripts. My practice shows that if you are rotating the screen, you will not need the touchpad for sure. 
The script touchpad.sh detects if the touchpad is enabled or disabled and switch it over, it is not changed since my previous post but still here it is:
```
bash-4.2$ cat /usr/bin/touchpad.sh 
#!/bin/bash
if [ $# -eq 1 ]; then               # Any arguments?
    arg1=$(echo $1 | tr [:upper:] [:lower:])    # Yes, convert to lower case
    cliArg=1                    # Set flag that we have one
else                        # There is no argument.
    cliArg=0                    # Clear flag
fi

if [ $cliArg -eq 1 ]; then          # Did we get an argument?
    if [ $arg1 = 'on' ]; then           # Yes, was it "on"?
    xinput --set-prop $touchpadID "Device Enabled" 1
                        # Yes, enable the touchpad
    elif [ $arg1 = 'off' ]; then        # No, was it "off"?
    xinput --set-prop $touchpadID "Device Enabled" 0
                        # Yes, disable the touchpad
    else                    # None of the above, so...
    sleep 1                 # ...sleep one second, exit
    fi

else                        # No argument, toggle state
    if [ $touchpadEnabled -eq 1 ]; then     # Enabled now?
    xinput --set-prop $touchpadID "Device Enabled" 0
                        # Yes, so disable it
    else                    # Must be disabled, so...
    xinput --set-prop $touchpadID "Device Enabled" 1
                        # ...enable it
    fi
fi
```
And also as I said before, I got nice little desktop/menu-favorite icons with rotation arrow images that points to the right script and since I am left-header, I use mostly the rotate right icon and I got it in favorites. So instead of hardware switch, I got a software one. It doesn't make much difference.
Hope this answers some previous questions. 
And I would like to ask if anybody have a solution for the following issue:
The little button that is suppose to lock the screen rotation works as Super+O. This comes from some Windows standard. now gnome-shell 3.10 (Fedora 20) recognize it too. I got that image of rotation lock when I press it. 
It's cool, but of course it doesn't work because the gyroscope sensor don't work. However I am unable to assign function or keyboard shortcut (such as rotate-left.sh for example) to that key combination because the gnome-shell got other plans for it. And so I can't rotate the screen with that little button. It would be really cool to be able to do it. Did anybody manage to set functions to that button?
Thank you!

And a final few words, please don't hesitate to try linux on your Yoga, it is all working great. The wifi and bluetooth makes no trouble, the touchscreen and all other stuff too.
I useed windows for 15 minutes and Fedora for about 9 months and I have no issues at all with the hardware. Of course it will take you 1-2 hours to tune it up, but you have all you need right in this thread, just start reading from the beginning. But setting up windows and installing all your programs and stuff will take even more time, which you could do here with a single yum/apt-get command.
I would say that linux is about 99% operational with Yoga and what doesn't have solution, has very beautiful workarounds.


Please note that I am using Fedora, but so far all of this stuff seem to work on Ubuntu too.

---

### Post by arttuhon on 2014-01-26
Thanks you Mehanzhi for your scripts. Could you also post short walkthrought here since I have no script experience under linux. 
Just how to make them and how to create hotkey combinations to run them.

Another question is does anyone have any software recommendations to edit pdf files? maybe to create own pages there, equations, draw, screen clips? 

Third question is does any else have sometimes problems with screen? like the picture curruptes but gets back to normal when you scroll or do something else?

Thanks in advance,
Arttu

---

### Post by mehanzhi on 2014-01-26
Hello arttuhon,

I have no problems with the screen and about modifying pdf files, I think it can be done with libreoffice or GIMP :)

That stuff below is for newbies into linux/unix, these are common stuff that every unix/linux user should know. You can read it in everywhere on the internet.

Creating shell scripts is as simple as putting that text into a file and then make that file executable. 
The shell is a basically a command interpreter and it doesn't care if you give the commands directly form keyboard, or you put them into a file and execute it. 
In order to be able to execute a command/shell script just with it's name instead of writhing it's full path (rotate-left.sh instead of /path/to/file/rotate-left.sh) you should consider putting the scripts in a bin directory /bin or /usr/bin or /usr/local/bin. I prefer /usr/bin , because /bin in unix is used for the most critical tools and scripts when all other filesystems are unmounted.
Making scripts executable is done by executing the following command:
```
chmod +x /path/to/file/filename
```
Please note that some of this stuff like putting files into a bin directory, or making them executable will require root privileges.

Making shortcut/menu-item with nice icon and putting it into a place where it will appear in your desktop menus is a matter of the graphical environment you use - mate, gnome, KDE, ubuntu type of gnome (unity)... etc.

Making a keyboard shortcuts is also a matter of the graphical environment you use, but for sure any of them have nice and easy graphical settings section and there you should see a keyboard settings and probably there will be the keyboard shortcuts. 
What you need there is a key combination and a path to the script/binary file to be executed. 
Forgive me for not giving you more details, but I am Fedora user and this is Ubuntu forum and things probably look a lot more different on other distributions and GUIs. The reason I am posting here is because this is the best thread on the topic Lenovo yoga on Linux :)

And there is another thing I wanted to say, if you read the thread some pages back you will see that there was a problem with skype and microphone. The microphone was working great with all other applications, but skype conversations had issues. 
I manage to solve this reading this thread [https://bbs.archlinux.org/viewtopic.php?pid=1288881](https://bbs.archlinux.org/viewtopic.php?pid=1288881) . 
The solution was executing the Skype binary with the following arguments:
```
PULSE_LATENCY_MSEC=30 skype
```
Please note that putting this into the desktop menu item didn't work, so I had to put it into another file and make it executable script, then pointing the desktop menu item to the scripts instead of the skype binary:
```
bash-4.2$ cat /usr/bin/skype.sh 
#!/bin/bash
PULSE_LATENCY_MSEC=30 skype

```

And the desktop menu item.

File /usr/share/applications/skype.desktop
```
bash-4.2$ cat /usr/share/applications/skype.desktop 
[Desktop Entry]
Name=Skype
Comment=Skype Internet Telephony
Exec=skype.sh %U
Icon=skype.png
Terminal=false
Type=Application
Encoding=UTF-8
Categories=Network;Application;
MimeType=x-scheme-handler/skype;
X-KDE-Protocols=skype

```

Now skype conversations work with no issues :)

---

### Post by arttuhon on 2014-01-26
Many thanks mehanzhi! good information for me.

For the skype problem: I have never had problems with skype and microphone in ubuntu 13.04. Worked great straight out of the box.

Happy Sunday,
Arttu

---

### Post by vak on 2014-01-27
has anyone found the reason why the "sticky arrow keys" issue appeared again in Ubuntu 13.10 after two monthes?

---

### Post by mehanzhi on 2014-01-28
No idea, probably kernel update returns old issues.

Have you tried BIOS update?

---

### Post by vak on 2014-01-28
> **mehanzhi said:**
> Have you tried BIOS update?

on the Lenovo site there is an 66cn55ww BIOS release from May 2013. I have 66CN54WW, which is indeed probably a previos one. However I've seen some posts in Internet of kind "don't do this update yet!". What is exactly in this update? i can't find its description.

---

### Post by andrew-c-symington on 2014-01-30
Spent ages wondering why my yoga 13 would resume quickly from suspend-to-ram; it was taking about 20 seconds. I checked /var/log/syslog and found the following line: "PM: resume of devices complete after 16597.169 msecs". After much googling... turns out that the Lenovo Yoga 13 doesn't like having a microsd adapter plugged into the sd card reader without a microsd card physically plugged into it. I think it has to do with power management and there being no response from the device on boot. I hope this helps somebody else :)

---

### Post by pfpschneider on 2014-01-31
[QUOTE=arttuhon;12907450]Hi forum,
I'm a bit confused is there good automatic rotation at the moment or not? 
atleast seems like we are really close to it? If you have ok working solution please let me know.
I'm also really interested on applications where you use touch screen, which are your favorite ones?


I have code that does automatic rotation using the accelerometer.  However, the device hangs on a regular basis, so I wouldn't call this a complete solution yet.

Any, if you want to play around with this, just send me email at [email]pfpschneider@gmail.com[/email]

PS:  I run Fedora 20, but the code should work on Ubuntu as well.

---

### Post by mehanzhi on 2014-02-01
Aloha pfpschneider.

The scripts for rotation are working fine, but I was unable to find driver for the gyroscope. I hope this is the same device you call accelerometer. 
Could you please share your experience with it, how did you manage to get it working? Do you use custom scripts that execute on some event received by this device, or it's got an included functionality of rotating the screen. 

What driver or kernel module did you use, where did you find the source and how did you build it?

I am using fedora 20 too with gnome-shell and pretty much every application including the window manager works great with touchscreen.



Thank you.

---

### Post by pfpschneider on 2014-02-01
There are eight sensors run from the sensor chip in the Yoga 2 Pro.   In Fedora 20 the kernel module for running the sensor hub is available and there are four kernel drivers for sensors from the chip - light sensor, accelerometer, gyroscope, and magnetometer - that use the IIO bus.  These drivers are automatically loaded on startup and set up a sysfs interface for user code.  You can see the devices under /sys/bus/iio/devices/  To find out which device is which, you have to look at /sys/bus/iio/devices/iio:deviceX/name (where X is the number for one of the files in /sys/bus/iio/devices/).

What I did was get some demo code for the IIO bus from the linux kernel documentation, fix the bugs in it, and arrange to get the numbers from the accelerometer.  I then added a little bit of code to turn these numbers into a symbolic orientation - FLAT, TOP, BOTTOM, LEFT, RIGHT - and then rotate the screen and touchscreen appropriately.

Getting the sensor to work correctly was NOT easy, and the code is not production quality.  However, it can be downloaded from [https://github.com/pfps/yoga-laptop](https://github.com/pfps/yoga-laptop) in the sensors directory.   I also have semi-usable drivers for the other four sensors there.  The custom sensor reports acceleration for the base, which can be combined with the acceleration for the screen to determine the hinge angle, but I have only the beginnings of code for this.



What I would *really* like to do is improve the ACPI stuff to be able to get the buttons (particularly the one on the screen) to work better. I stripped out  the part of ideapad_laptop that handles the non-existant hardware RF kill switch, to produce yoga_laptop, which does correctly handle the Airplane Mode and Novo keys.   This kernel module needs a lot more work, but is available from [https://github.com/pfps/yoga-laptop](https://github.com/pfps/yoga-laptop) in the yoga_laptop directory.

---

### Post by oscar-tiderman on 2014-02-04
Just for documenting: I had a lot of errors from usb and drm in dmesg output when it was trying to detect the touch screen, when I added i915.i915_enable_fbc=0 to GRUB_CMDLINE_LINUX_DEFAULT I got rid of those totally, haven't seen any downside to this yet. I do have some trouble with supending that I try to hunt down the cause to, because it does only work every 2-3 time I close the lid. I also seem to have some freezes on boot sometimes if I enable usb auto power mode, hopefully this is now resolved when skipping framebuffer. Will test some more

---

### Post by mehanzhi on 2014-02-08
Hello [[COLOR=#000000]pfpschneider[/COLOR]]("http://ubuntuforums.org/member.php?u=1897879") 	 

Great job with this sensors, I will try them today and see if I can help with something. I am not much of a driver developer, but I will see if I can do something useful. 

And while on this topic, I wanted to ask if anybody has idea about the gnome screen rotation function?
I am using xrandr scripts to rotate my screen, but since Super+O is doing rotation lock, then gnome should have it's mechanism for rotating screen right? Otherwise what this lock stands there for?
So I needed to know if somebody knows how to send signals to gnome in order to get screen rotation automatically handled by gnome and to see if it will look/work better then xrandr scripts.

Thank you.

---

### Post by emin2 on 2014-02-16
> **joonpy said:**
> Larry Finger has set up a github repo of the wireless driver: [https://github.com/lwfinger/rtl8723au](https://github.com/lwfinger/rtl8723au)

$ git clone [http://github.com/lwfinger/rtl8723au.git](http://github.com/lwfinger/rtl8723au.git) 
(if you don't have git, download the .zip archive)

$ cd [rtl8723au]("http://github.com/lwfinger/rtl8723au.git")

$ make && sudo make install

Will compile & install the driver. I have tested it and it works well on my Yoga 13.

-Joon

Hi
I am not a so familiar with linux commands... 

in larry finger's wifi driver fixing page ... there is a quote 

         [rtl8723au: Fix build problem with dkms]("https://github.com/lwfinger/rtl8723au/commit/a1c3032d930e2a506930d4b53913a96fee980fdc")         […]("https://github.com/lwfinger/rtl8723au#")     
       It has been reported that under Ubuntu 13.10 (at least), the 8723au module
won't auto-build correctly with new kernels. The error can be seen explicitly
with dkms status, which gives:
dkms.conf: Error! No 'BUILT_MODULE_NAME' directive

Making BUILT_MODULE_NAME the same as BUILD_MODULE_NAME fixes the problem.

How to make this fixing?? as I renew kernel with typical dpkg installation there was some error about dkms.conf.. I think this fixing is related to this problem. 

So how can I fix it??
-----[B]
(solving)
Finally I understood that I had to make small changing on a misspelled line in dkms.conf file. ( BUILD_MODULE_NAME >> BUILT_MODULE_NAME).. This could happen to some newbies like me. :)[/B]

---

### Post by arttuhon on 2014-02-23
Hi all,
after yesterdays update I lost voice output. It's totally numb.

Anyone else have the same problem or/and any advices or solutions or ways how to start figuring out the problem.

Thanks,
Arttu

---

### Post by mehanzhi on 2014-02-26
Hello,

I had no such troubles with Fedora, I updated yesterday.
However my right build-in speaker doesn't work. 
With headphones it works perfectly, but the one below the keyboard don't work. 
Here in Bulgaria they don't serve the idea products, so they offered me to send it to Poland and wait 30 days, but when they heard that I with Linux, they refused me any support :D
They told me to install WinDos and then send it. I am not willing to wait 30 days anyway, so I just use it with only 1 build-in speaker :)

So my advise would be to try headphones. 
If not, probably rollback kernel and modules and see what happens.

---

### Post by matthewlbeckers on 2014-04-03
Seeing as everyone else is dumping their (very useful) modifications and tips on getting ubuntu up and running on the yoga, I think I will chip in with a small one:

Tapping my touchpad would cause a small delay before any action was made in ubuntu, compared to clicking the touchpad. I fixed this simply by changing a setting for synclient:

```
synclient SingleTapTimeout=0
```

It's a small thing, but hopefully it helps make the touchpad more comfortable to use in ubuntu!

---

### Post by DOS286 on 2014-04-08
Has anyone tried 14.04 on the Yoga? I believe it's scheduled for official release on the 17th. I'm curious if the wireless card is handled out of the box in ubuntu 14.04.

---

### Post by qwesp on 2014-04-10
I tried to boot it, but no success. The boot loader could not find some files.  The reason might be that my boot setup was too complicated (i use MULTISYSTEM for multiple cds) or that its still beta. I decided to wait for the full release.

---

### Post by Jacob_Strandlien on 2014-04-19
After a lot of trial and error, I have gotten the screen to automatically roatate when my Lenovo IdeaPad Yoga 13 is physically turned.  This works for both the display and the touchscreen orientation.  All of the tools are out there, but I couldn't find a good concise set of instructions on how to do it.  The following is my attempt to provide those instructions:

**Caveat:**
I'm not exactly a linux guru; I'm sure there are better and more proper ways to do many of these steps.  But this is what worked for me, and if you have a similar enough setup and follow these steps exactly, it should work for you too.

**My setup:**
Laptop model: Lenovo Ideapad Yoga 13 (though this should work on at least a few other Lenovo Yoga models)
Operating System: Ubuntu 14.04 Trusty Tahr x64, clean install

**How I did it:**
**1.** Download the files at this git repo [https://github.com/pfps/yoga-laptop](https://github.com/pfps/yoga-laptop).  You can do this by opening a terminal and entering:
```
sudo apt-get install git-core #Use this command if you don't already have git
git clone https://github.com/pfps/yoga-laptop.git
```
This repo has many warnings that it is not production-ready, so your mileage may vary.  However, the needed files worked perfectly for me.


**2.** Install the drivers for the orientation sensors:
```
cd yoga-laptop/sensors/drivers
make
sudo make install
```
Note: this step will have to be done everytime you upgrade the kernel (which is sometimes done with Ubuntu's routine updates).  Eventually, these drivers are expected to be included in the kernel, so someday this step will no longer be necessary.


**3.** Reboot your laptop


**4.** Open the terminal again and modify your sudo settings to allow the orientation setup script to be run without a password:
```
sudo visudo
```
At the bottom of the file add the following line where <username> is your user name in Ubuntu:
```
<username> ALL=(ALL) NOPASSWD:/home/<username>/yoga-laptop/sensors/setup
```
Save with ctrl-o and exit with ctrl-x


**5.** This step will set the orientation script to run when you log into the laptop.  If anyone knows a way to make it run when your computer boots instead (so your login screen rotates too), please speak up.  I tried several methods and couldn't find a way.
Edit a file called .gnomerc in your home folder (create it if it isn't there).  I prefer nano as my editor:
```
sudo nano .gnomerc
```
Add the following lines, and replace <username> with your username in Ubuntu
```
cd /home/<username>/yoga-laptop/sensors
nohup sudo /home/<username>/yoga-laptop/sensors/setup &
cd ~/
```
Save with ctrl-o and exit with ctrl-x


**6.** Reboot, log in, and you're done!  Your screen should now rotate when you physically turn it.


If you see ways to improve these instructions, please do speak up, and I'll edit them appropriately.

---

### Post by majeka on 2014-04-20
Hi Jacob,

Thanks for your very clear and detailed instructions! I also have a Yoga 13 with 14.04, and followed your steps - worked like a charm. 

Like an idiot, the first time I followed them I didn't notice that on both lines where you need to replace <username> with your username, there are 2 instances to replace. I was obviously a bit gung-ho and didn't notice that first time round, and was confused to see it not working. Just thought I'd mention that in case it catches anyone else out. (Probably just me though!)

Cheers mate

---

### Post by Charles_THOMAS on 2014-04-21
Hi!
Thanks a lot, I was looking for it for months!
Tried on Debian Wheezy GNOME 3.14.1 (Vanilla Kernel) with success.

Does anyone know how to disable the touchpad and how to activate a virtual keyboard when the touchpad is used?

Thanks again!

---

### Post by strikeoncmputrz on 2014-04-21
> **Jacob_Strandlien said:**
> After a lot of trial and error, I have gotten the screen to automatically roatate when my Lenovo IdeaPad Yoga 13 is physically turned.  This works for both the display and the touchscreen orientation.  All of the tools are out there, but I couldn't find a good concise set of instructions on how to do it.  The following is my attempt to provide those instructions:

**Caveat:**
I'm not exactly a linux guru; I'm sure there are better and more proper ways to do many of these steps.  But this is what worked for me, and if you have a similar enough setup and follow these steps exactly, it should work for you too.

**My setup:**
Laptop model: Lenovo Ideapad Yoga 13 (though this should work on at least a few other Lenovo Yoga models)
Operating System: Ubuntu 14.04 Trusty Tahr x64, clean install

**How I did it:**
**1.** Download the files at this git repo [https://github.com/pfps/yoga-laptop](https://github.com/pfps/yoga-laptop).  You can do this by opening a terminal and entering:
```
sudo apt-get install git-core #Use this command if you don't already have git
git clone https://github.com/pfps/yoga-laptop.git
```
This repo has many warnings that it is not production-ready, so your mileage may vary.  However, the needed files worked perfectly for me.


**2.** Install the drivers for the orientation sensors:
```
cd yoga-laptop/sensors/drivers
make
sudo make install
```
Note: this step will have to be done everytime you upgrade the kernel (which is sometimes done with Ubuntu's routine updates).  Eventually, these drivers are expected to be included in the kernel, so someday this step will no longer be necessary.


**3.** Reboot your laptop


**4.** Open the terminal again and modify your sudo settings to allow the orientation setup script to be run without a password:
```
sudo visudo
```
At the bottom of the file add the following line where <username> is your user name in Ubuntu:
```
<username> ALL=(ALL) NOPASSWD:/home/<username>/yoga-laptop/sensors/setup
```
Save with ctrl-o and exit with ctrl-x


**5.** This step will set the orientation script to run when you log into the laptop.  If anyone knows a way to make it run when your computer boots instead (so your login screen rotates too), please speak up.  I tried several methods and couldn't find a way.
Edit a file called .gnomerc in your home folder (create it if it isn't there).  I prefer nano as my editor:
```
sudo nano .gnomerc
```
Add the following lines, and replace <username> with your username in Ubuntu
```
cd /home/<username>/yoga-laptop/sensors
nohup sudo /home/<username>/yoga-laptop/sensors/setup &
cd ~/
```
Save with ctrl-o and exit with ctrl-x


**6.** Reboot, log in, and you're done!  Your screen should now rotate when you physically turn it.


If you see ways to improve these instructions, please do speak up, and I'll edit them appropriately.

Jacob, thank you for your instructions. I can confirm that auto-rotation worked with a Yoga 11S.  However, the touchscreen input is off by a few inches. I'll take a look at the source tomorrow and see if there is something hardcoded for the Yoga 13's resolution.

---

### Post by raffi.lueckl on 2014-04-22
Hello

I did a dualboot for WIndows 8.1 Update 1 and Ubuntu 14.04. NOTE: I'm a newbie to linux and there might be better ways.

I'm still using UEFI, because I'll use Windows-oS more. To do that, you have to put the installation of the bootloader on the partition, where ubuntu will be installed (when you choose the partition of ubuntu, you can choose this option in the same window).
I disabled fastboot (don't know if this necessary).
Now always when I boot up the computer, I have to hit FN+F12 to get to the boot screen, from there I can choose ubuntu.

Wireless does work after the fix, the brightness option needed a fix and the screen rotation. I have no issues with the touchscreen until now.

Here are some links I used and can recommend:

[http://ubuntuforums.org/showthread.php?t=1911972&p=12993611#post12993611](http://ubuntuforums.org/showthread.php?t=1911972&p=12993611#post12993611)
[https://www.youtube.com/watch?v=H3WdsSHo5Sw](https://www.youtube.com/watch?v=H3WdsSHo5Sw)
[https://forums.lenovo.com/t5/Linux-Discussion/Yoga-13-What-to-do-when-you-install-UBUNTU/td-p/1246211](https://forums.lenovo.com/t5/Linux-Discussion/Yoga-13-What-to-do-when-you-install-UBUNTU/td-p/1246211)

---

### Post by DOS286 on 2014-04-26
Hi all. I've got an annoyance with 14.04. It will not suspend properly. I think there might be 2 bugs at play in this.

It does not suspend when the lid is shut. There is some indication that it's not receiving the lid closed signal properly. Many times when I close the lid, the screen does not even turn off. I can still see it glowing through the seam. Other times it does turn off the screen, but still does not suspend. I thought that Jacob_Strandlien's excellent instructions might fix the lid switch sensor as well, but it did not work. The screen rotation works a champ (except that it does not turn off the track pad), but it does not fix the suspend / screen off issues when the lid is closed.

It also does not suspend after the inactive time set in the Power settings module. I read a post (I can't remember where now) that sugested a bios, wake on lan setting could block the suspend when idle. I could not find a wake on lan setting in the Yoga13 bios. In trying to trouble shoot, I noticed that the screen dim on idle function works but not the suspend. After the screen dimmed, I noticed that it would periodically wake up and show the gnome lock screen as if someone had touched the track pad. The lock screen showed at almost precisely 4 minute intervals when it was set to suspend after 5 minutes of inactivity. If I changed the inactive time to 10 minutes the lock screen showed at regular 8 minute intervals.

If I force suspend by holding down alt and clicking the gnome power button, which is changed to a pause button, it suspends just fine, and then wakes when needed without an issue.

Has any one else had these issues in 14.04? More importantly, has anyone found a solution?

---

### Post by mehanzhi on 2014-04-27
Hello,

The screen rotation works perfectly fine, thank you very much.

But still I wonder if I could write a script that can read the value of screen rotation lock status (Windows+o or the little button on the right side) or it could be implemented in the driver.
See, the command:  (in Fedora it's that variable, in ubuntu it may be on a different place)
```

bash-4.2$ dconf read /org/gnome/settings-daemon/peripherals/touchscreen/orientation-lock
false

```
This will return you the orientation lock status. So if I press the rotation lock button it will change. It is very very very easy to write a simple script that checks the status and run or stop the **orientation **binary that watches for rotation.
So if rotation lock is TRUE it will not rotate, if the lock is FALSE it will rotate. The trouble is that it has to be executed for frequently check (every 5 seconds for example) and react - run **orientation**, kill **orientation**, or don't do anything for no change since the last check. I couldn't find a way to detect only status change of a value within the dconf and trigger an action :(. Frequently check of that value with script shouldn't load the CPU at all, but including it into the driver and running that check within the **orientation** binary would be much more elegant way.

I've examine the driver code and it seems that it's not possible to include that check without major rewrite the entire watch function. So I wonder if the developer of the driver would have an opinion about it. 

Unfortunately I don't have registration in github and I would like to ask if anybody here has one, so can post comment there and see if the developer will do a proper response. 
If not within a few days I will post the orientation lock script here. 

Thank you.

---

### Post by spooner1 on 2014-04-28
hello jacob,

great work, runs pretty well!

the file orientation.c contains a state called "flat". is this a is this a real state, or do you just whish this state would exist?

regards

---

### Post by Jacob_Strandlien on 2014-04-28
> **spooner1 said:**
> hello jacob,

great work, runs pretty well!

the file orientation.c contains a state called "flat". is this a is this a real state, or do you just whish this state would exist?

regards

I have no idea; it's not my repo.  I've noticed that there are also other features among those files, such as hinge state detection, that are unfinished.  I would contribute to it if I were a better programmer than I am.

---

### Post by emin2 on 2014-04-29
After installing TLP (battery improver) brightness control solution does not work. Has Anyone got same and have any solution?

---

### Post by spooner1 on 2014-04-30
same issue here

---

### Post by StefanX on 2014-04-30
Thanks Jacob_Strandlien! Your instructions work very well for me on Ubuntu 14.04.

But when flipping the Yoga into tablet mode the touchpad is still active. Interestingly, the keyboard is disabled automatically - as desired. Any idea how to automatically disable the touchpad?

---

### Post by Jacob_Strandlien on 2014-04-30
> **StefanX said:**
> Thanks Jacob_Strandlien! Your instructions work very well for me on Ubuntu 14.04.

But when flipping the Yoga into tablet mode the touchpad is still active. Interestingly, the keyboard is disabled automatically - as desired. Any idea how to automatically disable the touchpad?

I haven't found an ideal solution for that.  I use touchpad-indicator to manually turn it on and off.  You can install it like this:

```
sudo add-apt-repository ppa:atareao/atareao
sudo apt-get update
sudo apt-get install touchpad-indicator
```

---

### Post by emin2 on 2014-05-03
> **StefanX said:**
> Thanks Jacob_Strandlien! Your instructions work very well for me on Ubuntu 14.04.

But when flipping the Yoga into tablet mode the touchpad is still active. Interestingly, the keyboard is disabled automatically - as desired. Any idea how to automatically disable the touchpad?


am I missing something I don't know but with Ubuntu14.04 I don't have so much possibilities with Touch screen. For example in web browser do we have any web browser with touch capabilities?

---

### Post by emin2 on 2014-05-03
If you succeed with bluetooth and have problem with sending to PC something then you can try this solution. It worked by my 14.04. 

[http://digantabiz.wordpress.com/2013/07/08/bluetooth-problem-in-ubuntu-12-04-solved/](http://digantabiz.wordpress.com/2013/07/08/bluetooth-problem-in-ubuntu-12-04-solved/)

---

### Post by emin2 on 2014-05-11
> **emin2 said:**
> After installing TLP (battery improver) brightness control solution does not work. Has Anyone got same and have any solution?


somebody has a solution for this issue.. check 

[http://itsfoss.com/fix-brightness-ubuntu-1310/](http://itsfoss.com/fix-brightness-ubuntu-1310/)

here.. it worked at my yoga13 with ubuntu 14.04

---

### Post by emin2 on 2014-05-11
as I attach HDMI cable I dont have any sound with TV. Does anyone have a solution for it?

---

### Post by anton_mellit on 2014-05-12
> **emin2 said:**
> am I missing something I don't know but with Ubuntu14.04 I don't have so much possibilities with Touch screen. For example in web browser do we have any web browser with touch capabilities?

Chromium supports scrolling, pinch zoom and back/forward gestures (at least on 14.04)

---

### Post by PJSingh5000 on 2014-05-14
I wrote a script to turn Touchpad-indicator and the Onboard indicator into a "Tablet Mode Switcher".  The script and instructions are posted below.

This script creates a custom keyboard layout called "Lenovo" that excludes quit, lock, and macro-keys that do not work on the lock-screen or could prevent you from loging back in.  (Without the changed made by this script, while on the lock-screen, if you accidentally quit or hide the onscreen keyboard, there would be no way to bring it back).

The script achievs mode switching by installing and modifying Touchpad-indicator to control the behavior of the Onboard virtual keyboard, enablig and disabling it concurrently with the touchpad.

If you use this script, please be aware that it adds a ppa (ppa:atareao/atareao) to your system and installs the Touchpad-indicator applet.  The script modifies the code for both the Touchpad-indicator and the Onboard virtual keyboard, that are installed on your system.  After running the script, I recomend that you do not change the Preferences for Touchpad-indicator or Onboard virtual keyboard, because they are specifically configured to work concurrently.

Switching between Tablet Mode and Laptop Mode...

[LIST=1]
[*]To convert to Tablet Mode, select the Touchpad-indicator icon at the top right of your desktop.  The icon looks like a touchpad with two buttons, and is located just left of the Wireless Network Connection indicator.  Select *Activate Tablet Mode (Disable Touchpad & Keyboard)*. 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=253137&d=1400039697[/IMG]


[*]Once selected, your laptop's keyboard and touchpad will become deactivated.  You can only interact with your computer using the touch-screen.  A virtual keyboard will automatically appear whenever you need to type.  (For example, if you click on the URL bar in Firefox, or if you open a text editor). 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=253141&d=1400041647[/IMG]


[*]You can now flip your screen all the way around and use your computer like a tablet, and you will not accidentally press keys or operate the touchpad. 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=253140&d=1400041246[/IMG]


[*]Although the virtual keyboard should pop-up or hide automatically, if you need to manually show or hide it, tap the "Onboard" indicator icon at the top of your desktop.  The icon looks like four little squares.  There will be an option to *Show Keyboard*, if the keyboard is currently not visible, or an option to *Hide Keyboard*  if the keyboard is currently visible.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=253135&d=1400039697[/IMG]


[*]To convert to Laptop Mode, select the "Touchpad-indicator" icon at the top right of your desktop.  The icon looks like a touchpad with an "X" through it, and is located just left of the Wireless Network Connection indicator.  Select *Activate Laptop Mode (Enable Touchpad & Keyboard)*.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=253136&d=1400039697[/IMG]
[/LIST]

(The custom keyboard and the modifications are designed to prevent you from getting stuck on the lock-screen without an active keyboard to enter your password.  As a tip, if for some reason the virtual keyboard is not working on the lock-scren, select *Switch User* and your physical keyboard and touchpad will become activated; then just type your current user's id and password to log back in).

To run the script shown below, copy it into a file, and save it as "create_tablet_mode_switcher.sh".
Then, from a terminal do the following:
```
$ cd <directory where you saved the script>
$ chmod +x create_tablet_mode_switcher.sh
$ ./create_tablet_mode_switcher.sh
```

Here is the create_tablet_mode_switcher.sh script.  (Note that this script was written for version 1.0.0-0ubuntu4 of Onboard and for version 1.0.0-0extras14.04.0 of thouchpad-indicator).
```

#!/bin/bash

################################################################################
#
# Create Tablet Mode Switcher
# Versin 2014.05.12
# 
# Setup Onboard and Touchpad-indicator to switch between Tablet and Laptop Modes
# for touchscreen computers.
#
# This script sets up the Unity panel Touchpad-indicator applet to enable
# "Laptop Mode" or "Touchpad Mode".  Either mode can be selected using the
# Touchpad-indicator applet in the unity panel at the top of the screen.
#
# In Laptop mode, the touchpad and keyboard are both active.  In Tablet mode,
# the touchpad and keyboard are both inactive, and you can only interact with
# the desktop using the touch-screen and the onscreen virtual keyboard that
# automatically appears whenever you need to type text.  The onscreen virtual
# keyboard can also be shown or hidden using the Onboard applet in the unity
# panel at the top of the screen.
#
# This script creates a custom keyboard layout called "Lenovo" that excludes
# quit, lock, and macro keys that do not work on the lock screen or could
# prevent you from loging back in.  (While on the lock-screen, if you
# accidentally quit or hide the onscreen keyboard, there would be no way to
# bring it back).
#
# Finally, the script achievs mode switching buy installing and modifying
# Touchpad-indicator to control the behavior of the Onboard virtual keyboard,
# enablig and disabling it concurrently with the touchpad.
#
# Here is a list of steps the script takes:
#
# 1. Setup Onboard virtual keyboard
#    1a. Create a new Onboard virtual keyboard layout called "Lenovo"
#    1b. Remove the Quit option from the Onboard unity indicator applet
#    1c. Configure Onboard
#    1d. Setup Onboard to start whenever a user logs in
#
# 2. Setup Touchpad-indicator applet
#    2a. Install and configure the Touchpad-indicator applet
#    2b. Update Touchpad-indicator to also control the keyboard (in addition to
#        the touchpad)
#    2c. Update Touchpad-indicator to not enter Tablet mode if Onboard is not
#        running
#    2d. Update Touchpad-indicator user interface
#
#
# LICENSE
# 
# Copyright 2014, P. Singh, GNU GPL v3
#
# This program is free software: you can redistribute it and/or modify it under
# the terms of the GNU General Public License as published by the Free Software
# Foundation, either version 3 of the License, or (at your option) any later
# version.
#
# This program is distributed in the hope that it will be useful, but WITHOUT
# ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS
# FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details
# (http://www.gnu.org/licenses/).
#
# For License information for Onboard, please visit:
# https://launchpad.net/~onboard
# Copyright 2006-2007, Chris Jones and Authors
#
# For License information for Touchpad-indicator, please visit:
# https://launchpad.net/touchpad-indicator
# Copyrignt 2010-2014, Miguel Angel Santamaría Rogado, Lorenzo Carbonell Cerezo
#
################################################################################


################################################################################
#
# (1) Setup Onboard virtual keyboard
#
################################################################################

################################################################################
# (1a) Create a new Onboard virtual keyboard layout called "Lenovo"
################################################################################

sudo cp /usr/share/onboard/layouts/Small.onboard /usr/share/onboard/layouts/Lenovo.onboard

FILE="/usr/share/onboard/layouts/Lenovo.onboard"
SEARCH='id="Small"'
REPLACE='id="Lenovo"'
sudo perl -i -pe "BEGIN{undef $/;} s*$SEARCH*$REPLACE*smg" $FILE

FILE="/usr/share/onboard/layouts/Lenovo.onboard"
SEARCH='summary="Space efficient desktop keyboard"'
REPLACE='summary="Simple keyboard for touch screens"'
sudo perl -i -pe "BEGIN{undef $/;} s*$SEARCH*$REPLACE*smg" $FILE

FILE="/usr/share/onboard/layouts/Lenovo.onboard"
SEARCH='<key group="bottomrow" id="layer4"/>'
REPLACE='<!--<key group="bottomrow" id="layer4"/>-->'
sudo perl -i -pe "BEGIN{undef $/;} s*$SEARCH*$REPLACE*smg" $FILE


################################################################################
# (1b) Remove the Quit option from the Onboard unity indicator
################################################################################

# Backup original source code file(s) that will be modified.

sudo cp "/usr/lib/python3/dist-packages/Onboard/Indicator.py" \
"/usr/lib/python3/dist-packages/Onboard/Indicator.py.original"

# Remove the Quit option from the Onboard unity indicator.

FILE="/usr/lib/python3/dist-packages/Onboard/Indicator.py"
SEARCH="self._menu.append\(quit_item\)"
REPLACE="#self._menu.append\(quit_item\)"
sudo perl -i -pe "BEGIN{undef $/;} s*$SEARCH*$REPLACE*smg" $FILE


################################################################################
# (1c) Configure Onboard
################################################################################

gsettings set org.gnome.desktop.screensaver embedded-keyboard-command "onboard --xid"
gsettings set org.gnome.desktop.screensaver embedded-keyboard-enabled true
gsettings set org.onboard key-label-font "Ubuntu"
gsettings set org.onboard key-label-overrides "['LWIN:&#57599;:super', 'RWIN:&#57599;:super']"
gsettings set org.onboard layout "/usr/share/onboard/layouts/Lenovo.onboard"
gsettings set org.onboard schema-version "2.1"
gsettings set org.onboard start-minimized true
gsettings set org.onboard system-theme-associations "{'Default': '', 'Ambiance': '/usr/share/onboard/themes/Nightshade.theme', 'HighContrastInverse': 'HighContrastInverse', 'HighContrast': 'HighContrast', 'LowContrast': 'LowContrast'}"
gsettings set org.onboard theme "/usr/share/onboard/themes/Nightshade.theme"
gsettings set org.onboard use-system-defaults false
gsettings set org.onboard xembed-onboard true
gsettings set org.onboard.auto-show enabled false
gsettings set org.onboard.icon-palette resize-handles ""
gsettings set org.onboard.keyboard audio-feedback-enabled true
gsettings set org.onboard.keyboard touch-feedback-enabled true
gsettings set org.onboard.theme-settings color-scheme "/usr/share/onboard/themes/Charcoal.colors"
gsettings set org.onboard.theme-settings key-fill-gradient "8.0"
gsettings set org.onboard.theme-settings key-gradient-direction "-3.0"
gsettings set org.onboard.theme-settings key-size "94.0"
gsettings set org.onboard.theme-settings key-stroke-gradient "8.0"
gsettings set org.onboard.theme-settings key-stroke-width "0.0"
gsettings set org.onboard.theme-settings key-style "gradient"
gsettings set org.onboard.theme-settings roundrect-radius "20.0"
gsettings set org.onboard.window docking-enabled true
gsettings set org.onboard.window docking-shrink-workarea false
gsettings set org.onboard.window enable-inactive-transparency true
gsettings set org.onboard.window force-to-top true
gsettings set org.onboard.window resize-handles ""
gsettings set org.onboard.window.landscape dock-expand false
gsettings set org.onboard.window.portrait dock-expand false


################################################################################
# (1d)) Setup Onboard to start whenever a user logs in
################################################################################

cp /etc/xdg/autostart/onboard-autostart.desktop ~/
sudo rm /etc/xdg/autostart/onboard-autostart.desktop
sudo cp /usr/share/applications/onboard.desktop /etc/xdg/autostart/


################################################################################
#
# (2) Setup Touchpad-indicator applet
#
################################################################################


################################################################################
# (2a) Install and configure the Touchpad-indicator applet
################################################################################

# Install Touchpad-indicator.

sudo add-apt-repository --yes ppa:atareao/atareao
sudo apt-get -qq update
sudo apt-get --yes install touchpad-indicator

# Backup original source code file(s) that will be modified.

sudo cp "/opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/touchpad_indicator.py" \
"/opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/touchpad_indicator.py.original"
sudo cp "/opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/touchpad.py" \
"/opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/touchpad.py.original"

# Configure Touchpad-indicator.

gsettings set org.gnome.settings-daemon.peripherals.touchpad horiz-scroll-enabled true
gsettings set org.gnome.settings-daemon.peripherals.touchpad natural-scroll true
gsettings set org.gnome.settings-daemon.peripherals.touchpad scroll-method "two-finger-scrolling"

mkdir -p ~/.config/touchpad-indicator
touch ~/.config/touchpad-indicator/touchpad-indicator.conf
echo '{"first-time": false, "enable_on_exit": true, "seconds": 2.0, "theme": "light", "on_mouse_plugged": false, "touchpad_enabled": true, "start_hidden": false, "shortcut_enabled": false, "disable_on_typing": false, "is_working": false, "shortcut": "<Primary><Alt>c", "disable_on_exit": false, "show_notifications": true, "autostart": true, "disable_touchpad_on_start_indicator": false, "version": "1.0.0-0extras14.04.0-src"}' > ~/.config/touchpad-indicator/touchpad-indicator.conf

# Setup Touchpad-indicator to start whenever you login.

mkdir -p ~/.config/autostart
touch ~/.config/autostart/touchpad-indicator-autostart.desktop
echo -e "[Desktop Entry]\nType=Application\nIcon=/opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/icons/touchpad-indicator.svg\nExec=/opt/extras.ubuntu.com/touchpad-indicator/bin/touchpad-indicator\nHidden=false\nNoDisplay=false\nX-GNOME-Autostart-enabled=true\nName[es_ES]=touchpad-indicator-autostart\nName=touchpad-indicator-autostart\nComment[es_ES]=Touchpad-Indicator official shortcut\nComment=Touchpad-Indicator official shortcut\n" > ~/.config/autostart/touchpad-indicator-autostart.desktop


################################################################################
# (2b) Update Touchpad-indicator to also control the keyboard (in addition to the touchpad)
################################################################################

# Disable the physical keyboard whenever the touchpad is disabled.

FILE="/opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/touchpad.py"
SEARCH="\t\treturn not self.are_all_touchpad_enabled\(\)"
REPLACE="\
\t\t# Show Onboard keyboard and set it to auto-show\n\
\t\tejecuta\('dbus-send --type=method_call --dest=org.onboard.Onboard /org/onboard/Onboard/Keyboard org.onboard.Onboard.Keyboard.Show'\)\n\
\t\tejecuta\('gsettings set org.onboard.auto-show enabled true'\)\n\
\t\t# Disable the physical keyboard\n\
\t\tkeyboard_id = ejecuta\('xinput list --id-only \"AT Translated Set 2 keyboard\"'\)\n\
\t\tejecuta\(\('xinput set-prop %s \"Device Enabled\" 0'\)%keyboard_id\)\n\
\t\treturn not self.are_all_touchpad_enabled\(\)"
sudo perl -i -pe "BEGIN{undef $/;} s*$SEARCH*$REPLACE*smg" $FILE

# Enable the physical keyboard whenever the touchpad is enabled.

FILE="/opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/touchpad.py"
SEARCH="\t\treturn self.are_all_touchpad_enabled\(\)"
REPLACE="\
\t\t# Hide the onscreen Onboard keyboard and set it to not auto-show\n\
\t\tejecuta\('gsettings set org.onboard.auto-show enabled false'\)\n\
\t\tejecuta\('dbus-send --type=method_call --dest=org.onboard.Onboard /org/onboard/Onboard/Keyboard org.onboard.Onboard.Keyboard.Hide'\)\n\
\t\t# Enable the physical keyboard\n\
\t\tkeyboard_id = ejecuta\('xinput list --id-only \"AT Translated Set 2 keyboard\"'\)\n\
\t\tejecuta\(\('xinput set-prop %s \"Device Enabled\" 1'\)%keyboard_id\)\n\
\t\treturn self.are_all_touchpad_enabled\(\)"
sudo perl -i -pe "BEGIN{undef $/;} s*$SEARCH*$REPLACE*smg" $FILE


################################################################################
# (2c) Update Touchpad-indicator to not enter Tablet mode if Onboard is not running
################################################################################

# Add a new method to check if Onboard is running.

FILE="/opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/touchpad.py"
SEARCH="import shlex, subprocess"
REPLACE="import os, shlex, subprocess"
sudo perl -i -pe "BEGIN{undef $/;} s*$SEARCH*$REPLACE*smg" $FILE

FILE="/opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/touchpad.py"
SEARCH="\tdef disable_all_touchpads\(self\):"
REPLACE="\
\tdef is_onboard_running\(self\):\n\
\t\tif os.popen\('ps -eo comm | grep onboard'\).readline\(\).strip\('\\\n'\) == 'onboard':\n\
\t\t\t# print\('Onboard is running.'\)\n\
\t\t\treturn True\n\
\t\telse:\n\
\t\t\t# print\('Onboard is not running.'\)\n\
\t\t\treturn False\n\
\t\t\t\n\
\tdef disable_all_touchpads\(self\):"
sudo perl -i -pe "BEGIN{undef $/;} s*$SEARCH*$REPLACE*smg" $FILE

# Add an error message to indicate that tablet mode could not be activated because Onboard is not running.

FILE="/opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/touchpad_indicator.py"
SEARCH="\t\t\t\t\t\t_\('Touchpad Disabled'\), self.attention_icon\)"
REPLACE="\
\t\t\t\t\t\t_\('Touchpad Disabled'\), self.attention_icon\)\n\
\t\telif kind == 'warning':\n\
\t\t\tself.notification.update\('Touchpad-Indicator',\n\
\t\t\t\t\t\t_\('Warning: The Onboard virtual keyboard is not running. \
Tablet Mode will not be activated, and the touchpad and keyboard will remain enabled.'\), self.attention_icon\)"
sudo perl -i -pe "BEGIN{undef $/;} s*$SEARCH*$REPLACE*smg" $FILE

# If Onboard not running, display an error, and do not disable the keyboard and touchpad.

FILE="/opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/touchpad_indicator.py"
SEARCH="\t\telif not enabled and self.touchpad.are_all_touchpad_enabled\(\):"
REPLACE="\
\t\telif not enabled and not self.touchpad.is_onboard_running\(\):\n\
\t\t\tif self.show_notifications:\n\
\t\t\t\tself.show_notification\('warning'\)\n\
\t\telif not enabled and self.touchpad.are_all_touchpad_enabled\(\):"
sudo perl -i -pe "BEGIN{undef $/;} s*$SEARCH*$REPLACE*smg" $FILE


################################################################################
# (2d) Update Touchpad-indicator user interface
################################################################################

# Update Touchpad-indicator menu options for Tablet mode and Laptop mode.

FILE="/opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/touchpad_indicator.py"
SEARCH="Enable Touchpad"
REPLACE="Activate Laptop Mode \(Enable Touchpad & Keyboard\)"
sudo perl -i -pe "BEGIN{undef $/;} s*$SEARCH*$REPLACE*smg" $FILE

FILE="/opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/touchpad_indicator.py"
SEARCH="Disable Touchpad"
REPLACE="Activate Tablet Mode \(Disable Touchpad & Keyboard\)"
sudo perl -i -pe "BEGIN{undef $/;} s*$SEARCH*$REPLACE*smg" $FILE

# Remove the hide option from the Touchpad-indicator menu.

FILE="/opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/touchpad_indicator.py"
SEARCH="\t\tadd2menu\(menu, text = _\('Hide icon'\), conector_event = 'activate',\n\
\t\t\t\tconector_action = self.on_hide_item\)"
REPLACE="\
\t\t#add2menu\(menu, text = _\('Hide icon'\), conector_event = 'activate',\n\
\t\t#\t\tconector_action = self.on_hide_item\)"
sudo perl -i -pe "BEGIN{undef $/;} s*$SEARCH*$REPLACE*smg" $FILE

# Update Touchpad-indicator messages for Tablet mode and Laptop mode.

FILE="/opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/touchpad_indicator.py"
SEARCH="Touchpad Enabled"
REPLACE="Laptop Mode has been activated. The touchpad & keyboard are now enabled."
sudo perl -i -pe "BEGIN{undef $/;} s*$SEARCH*$REPLACE*smg" $FILE

FILE="/opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/touchpad_indicator.py"
SEARCH="Touchpad Disabled"
REPLACE="Tablet Mode has been activated. The touchpad & keyboard are now disabled."
sudo perl -i -pe "BEGIN{undef $/;} s*$SEARCH*$REPLACE*smg" $FILE


################################################################################
#
# Done
#
################################################################################

echo
echo "Done setting up Onboard and Touchpad-indicator for Tabet mode and Laptop mode."
echo "Please reboot your computer now."
echo

```

Attachments:
[ATTACH=CONFIG]253137[/ATTACH] [ATTACH=CONFIG]253141[/ATTACH] [ATTACH=CONFIG]253140[/ATTACH] [ATTACH=CONFIG]253135[/ATTACH] [ATTACH=CONFIG]253136[/ATTACH]

---

### Post by pizzadragon on 2014-05-14
> **raffi.lueckl said:**
> Hello

I did a dualboot for WIndows 8.1 Update 1 and Ubuntu 14.04. NOTE: I'm a newbie to linux and there might be better ways.

I'm still using UEFI, because I'll use Windows-oS more. To do that, you have to put the installation of the bootloader on the partition, where ubuntu will be installed (when you choose the partition of ubuntu, you can choose this option in the same window).
I disabled fastboot (don't know if this necessary).
Now always when I boot up the computer, I have to hit FN+F12 to get to the boot screen, from there I can choose ubuntu.

Wireless does work after the fix, the brightness option needed a fix and the screen rotation. I have no issues with the touchscreen until now.

Here are some links I used and can recommend:

[http://ubuntuforums.org/showthread.php?t=1911972&p=12993611#post12993611](http://ubuntuforums.org/showthread.php?t=1911972&p=12993611#post12993611)
[https://www.youtube.com/watch?v=H3WdsSHo5Sw](https://www.youtube.com/watch?v=H3WdsSHo5Sw)
[https://forums.lenovo.com/t5/Linux-Discussion/Yoga-13-What-to-do-when-you-install-UBUNTU/td-p/1246211](https://forums.lenovo.com/t5/Linux-Discussion/Yoga-13-What-to-do-when-you-install-UBUNTU/td-p/1246211)

I finally found the right forum for my Yoga 11s! 

I too just finished setting up a Dualboot after upgrading my SSD to 250GB (the Samsung 840EVO is easily compatible and is a performance screamer so far) and I must say 14.04 is detecting the hardware fantastically! with 13.10 I had brightness and backlight issues that i resolved after some googling, but works great now on a fresh 14.04 install. Some of the special F-key functions didn't work well in 13.10 but most seem to work not, aside from the trackpad disabling button which i do find myself using frequently. 

The wireless driver from Larry Finger was quite easy to do. As my 11s doesn't have an ethernet jack I just I downloaded it in Windows and after the Ubuntu install I could easily navigate to the windows partition which was already mounted and copy it over to my home directory for the install. The only issue it that it seems to take longer than usual to detect my homne/work wifi network when switching from one OS to the other.
   
I found this forum while looking for help on the rotation issue and there are some great suggestions here, thanks! I plan on working on this over the weekend so I'll report my success/failure then. 

I'm so satisfied with this machine now! Though I'm stuck using windows for a few bits of work-related software, having Ubuntu working so well is the best! Boots up faster, the touchpad and touchscreen function superbly and I'm getting almost 1.5 hrs more battery life than with windows, close to 9 hrs with Ubuntu!

I haven't seem it mentioned in this forum yet so I'll share this one link on SSD optimization which I found quite useful: 
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by emin3 on 2014-05-15
> **anton_mellit said:**
> Chromium supports scrolling, pinch zoom and back/forward gestures (at least on 14.04)

thx.. I had installed just chrome and it doesnt have a working touch capability. 

By the way ubuntu-browser has touch capability either.. but too weak as function.

---

### Post by Xaikar on 2014-05-21
> **emin2 said:**
> as I attach HDMI cable I dont have any sound with TV. Does anyone have a solution for it?
 You need to manually go in and select the HDMI as your audio source.

---

### Post by emin3 on 2014-05-23
> **Xaikar said:**
> You need to manually go in and select the HDMI as your audio source.

I cant see HDMI source under Settings>Sound? I think I have stock driver for ubuntu. How can I find conextant driver (:) and install instructions)

---

### Post by daylight2 on 2014-06-04
I'm having problems with yoga 2 pro. Sometimes, when the screen turns off automatically after some inactivity time (settings -> brightness & lock -> turn screen off when inactive), it does not turn on afterwards. The backlight turns on, but the screen is black. Also I remeber, in previous versions of ubuntu screen was turnining off slowly with visual affect, so that one could touch the mouse to stop it, now it turns off very fast, which is very inconvient :(. Does anyone else have such problems?

---

### Post by pizzadragon on 2014-08-07
> **strikeoncmputrz said:**
> Jacob, thank you for your instructions. I can confirm that auto-rotation worked with a Yoga 11S. However, the touchscreen input is off by a few inches. I'll take a look at the source tomorrow and see if there is something hardcoded for the Yoga 13's resolution.

Hey strikeoncmptrz, I'm curious what kind of modifications you made to Jacob's process of getting the rotation working for your 11s. I picked one up a few months ago and i absolutely LOVE this machine. I've spent well above 90% of my time in Linux but for reading ebooks and comic books.

I don't have any experience tinkering with kernel level stuff like modules other than getting lwfinger's wifi driver working. Any advice would be greatly appreciated and I'll report my progress to share with anyone else interested.

---

### Post by sda-essentialforms on 2014-08-19
I had this problem too initially, but if you go to chrome://flags you should find an entry for Enable Touch Events.  Set it from Automatic to Enabled.  Some folks have claimed that they had to touch the screen somewhere before loading Chrome, but I haven't experienced that yet.

In my multi-touch dev sandbox I've putting together I've been able to track and record all digits on the screen.

---

### Post by DOS286 on 2014-08-20
I updated my Yoga 13 to Ubuntu 14.04 and now I can't get bluetooth to work. The install from [https://github.com/lwfinger/rtl8723au_bt](https://github.com/lwfinger/rtl8723au_bt) says that it installed successfully, but bluetooth still does not work. When I launch the bluetooth manager, all options are greyed out and there is a note in the device list that says "Bluetooth is disabled"

Has anyone got bluetooth working on the Yoga 13 under 14.04? If so, any pointers?

---

### Post by pfpschneider on 2014-09-23
I run Fedora, which may be somewhat different, but this looks as if Ubuntu 14.04 has the new ideapad_laptop module.  This module works fine, but it tends to turn off bluetooth and wifi, and your system may not be turning bluetooth on again.

To see if this is the problem run `rfkill list`.  If all the blocked values are no, then there is some other problem.  If some values are yes, then this is very likely the problem.  You need to `rfkill unblock bluetooth` to get bluetooth back.

peter


> **DOS286 said:**
> I updated my Yoga 13 to Ubuntu 14.04 and now I can't get bluetooth to work. The install from [https://github.com/lwfinger/rtl8723au_bt](https://github.com/lwfinger/rtl8723au_bt) says that it installed successfully, but bluetooth still does not work. When I launch the bluetooth manager, all options are greyed out and there is a note in the device list that says "Bluetooth is disabled"

Has anyone got bluetooth working on the Yoga 13 under 14.04? If so, any pointers?

---

### Post by DOS286 on 2014-09-27
Thanks for the reply peter. I had found many hits mentioning the rfkill list solution. On my machine, the results of rfkill list are variable. Sometimes it lists a "yes" on one or both of the values, but most of the time it's all "no"s. When it lists a "yes", I can change it to all "no"s with the rfkill unblock bluetooth command, but it doesn't actually activate bluetooth. There must be some other issue at play as well. Any ideas what else I can try?

Thanks!

---

### Post by k3ksc0r3 on 2014-10-08
i have some issues with my yoga 13 

1) the orientation script /yoga-laptop isnt working for me ( it starts to execute a orientation program, that doesnt exist) 
   update on this one: gyro_3d accel_3d magn_3d always show (0 | 0| 0)
2) the key to disable my touchpad isnt working
3) the orientation lock button is just an "o" :O
4) palm detection for the touchpad is missing

---

### Post by Wernervw on 2014-10-28
Hello, i've got dual boot ubuntu 14.10 and win8. My wifi conexion is much slower in ubuntu. Is there a way to optimize it?

Thank you very much.

Best regards.

---

### Post by arttuhon on 2014-11-01
Kernel update will probably take care of that problem.

You can check your kernel version by typing 
> uname -r

I'm not sure which version is the best for the yoga at the moment. With the latest 3.17 I had some freezing problems.
I'm currently using  3.13.0-38-generic and it's working pretty good. You can try several and pick up the best one. I also dont know which one is the best at the moment.
Would be nice to hear which version of kernel are you guys using at the moment?

Here's some video how to update kernel: [https://www.youtube.com/watch?v=X6z61bcf-d8#t=164](https://www.youtube.com/watch?v=X6z61bcf-d8#t=164)

---

### Post by Bucky Ball on 2014-11-01
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by ferabra on 2014-11-18
I am using the last kernel but i have to blacklist the wifi module that comes with the kernel and use the module from git to avoid freeze and kernel panic.

---

### Post by StefanX on 2014-11-21
> **Wernervw said:**
> Hello, i've got dual boot ubuntu 14.10 and win8. My wifi conexion is much slower in ubuntu. Is there a way to optimize it?

When you are running Windows, shutdown the computer before booting Ubuntu. Avoid a soft reboot from Windows to Linux.

---

### Post by minigts on 2014-11-28
> **pfpschneider said:**
> Has anyone been able to get all the keys on the Yoga 13 (and Yoga 2 Pro) to work correctly?

Most of them work out of the box, I'm having various issues:
1/ Pause and Break seem to be producing the same scan codes
2/ Refresh (F5), Open Apps (F8), and Switch Display (F10) don't seem to be hooked up to anything (in XFCE)
3/ ToggleTouchpad (F6), Toggle Airplane (F7), and Toggle Screen Light (F9) don't appear to produce any output, although the last does toggle the screen light
4/ The Windows button on the screen produces the same code as the Windows button on the keyboard
5/ The Volume Up and Down buttons on the side produce the same codes as the Volume Up and Down keys
6/ The Rotation Lock button isn't hooked up to anything (in XFCE)

Any pointers in getting these things to work?


Also, has anyone had any luck in getting the sensors to work?  [I have had some luck, but there are still issues.]

Did you ever get this figured out on yours?  All my function keys work except the mouse pad "kill" button, F6.  Audio, screen brightness and all the rest work as intended.  In fact, every key on my keyboard works, except for the mouse function via F6.

> **anton_mellit said:**
> Chromium supports scrolling, pinch zoom and back/forward gestures (at least on 14.04)

I just installed 14.04 on my Yoga 13, already used some tips and tricks to get me going, much appreciated.  Chrome was just installed and both it and Firefox (native to the installation) allow for touch in some ways, but neither allow for scrolling via the touch screen.  Scrolling does work for Terminal, assuming other applications.  Chrome actually doesn't respond to touch on hyperlinks, i.e., it will not get the link, only allow highlighting it.

Pretty new to Linux as a regular user, so is there something I can try or is there something I am missing?

Again, thanks for the information and as I find things out there, I will be more than happy to share.

---

### Post by alex299 on 2014-12-06
Hi lucky Yoga owners. (I myself have yoga 2 pro)
I read the whole thread, but never found one thing: how do you perform **right click**with a **touchscreen? **(Ubuntu 14.10, Unity)

I've been trying to find an answer for two days, tried many settings and tools, and no luck. Touch*pad* does this well - either with a long click or with two-fingers tap. But nothing works for the touch*screen*. It accepts three-fingers gesture, and scrolls in a filemanager, but nothing helps for a right click. I think I got it a couple times, but not sure how, probably with a long tap. Seems it generates a lot of jitter with this hi-res screen, but even when I manage to hold my finger really still (checking with xinput) - anyway no context menus appear. 

Any secrets?

---

### Post by oldrocker99 on 2014-12-09
Hmmm. I used Chrubuntu with an Acer C7 Chromebook, and, although the touchpad did allow a right click, I ended up using a good old mouse, which I have always preferred over a touchpad.

---

### Post by alex299 on 2014-12-15
> **oldrocker99 said:**
> Hmmm. I used Chrubuntu with an Acer C7 Chromebook, and, although the touchpad did allow a right click, I ended up using a good old mouse, which I have always preferred over a touchpad.

I was talking about the touchscreen, not a touchpad. In case I use Yoga as a tablet (rarely, though), I'd like to have some way of making right clicks.

---

### Post by arttuhon on 2014-12-16
> **ferabra said:**
> I am using the last kernel but i have to blacklist the wifi module that comes with the kernel and use the module from git to avoid freeze and kernel panic.

Can you share the name of module that comes with the kernel? I tried lspci -v but didnt see the wifi module.

This freezing and kernel panicing are making me crazy. I also need to reconnect wifi like every 10mins.

I'm really thankful for all the answers.

---

### Post by gandalf147 on 2014-12-19
> **DOS286 said:**
> I updated my Yoga 13 to Ubuntu 14.04 and now I can't get bluetooth to work. The install from [https://github.com/lwfinger/rtl8723au_bt](https://github.com/lwfinger/rtl8723au_bt) says that it installed successfully, but bluetooth still does not work. When I launch the bluetooth manager, all options are greyed out and there is a note in the device list that says "Bluetooth is disabled"

Has anyone got bluetooth working on the Yoga 13 under 14.04? If so, any pointers?

same problem for me. any news?

---

### Post by gandalf147 on 2014-12-21
> **jvcdk said:**
> 
So, one thread suggested to remove (blacklist) the module that created the acpi_video0 device. That, however, was a no go. It is (I think) the video kernel module which is used by the i915 video driver. Not a good thing not to have working. I then noticed that the previous mentioned acpi_backlight=vendor fix replaced the acpi_video0 device with an ideapad device - and that device I could remove by blacklisting the ideapad_laptop module. In other words:
[LIST=1]
[*]Add the acpi_backlight=vendor to your grub default command line (as described before in this thread)
[*]Run the update-grub (or in my case; update-grub2) command
[*]blacklist the ideapad_laptop by adding "blacklist ideapad_laptop" to your /etc/modprobe.d/blacklist.conf file.
[*]Reboot
[/LIST]

Best regards
Jørn Christensen

This works for me, but now the button f7 stops to work. or better, i try to explane. without this tricks, my touchpad doesn't works but button f7 works, with this string the opposite, touchpad works but f7 stops

---

### Post by jan-hermann-91 on 2015-02-07
Hi! I had exactly the same problem on my Yoga 13, running Ubuntu 3.13.0-45. Installing the bluetooth driver from Larry Finger worked, but then it showed "Bluetooth is disabled". 'rfkill list' would show that nothing is blocked. I tried rolling back Larry Finger's driver to the version of the [28 April 2014]("https://github.com/lwfinger/rtl8723au_bt/commit/ce2c77c06765ae627a3f491ef2eda807ca530faf"), which some confirmed as a working solution, but it still didn't work. Blindly going through the file system, I stumbled upon the bluetooth daemon /usr/sbin/bluetoothd which for some reason was NOT executable. I made it executable ('sudo chmod a+x /usr/sbin/bluetoothd'), restarted and voilà! it worked! I have absolutely no idea why it wasn't executable.

I then tried using the up-to-date version of the driver ([from the 22 August 2014]("https://github.com/lwfinger/rtl8723au_bt/commit/21fb2413ba56de29cb0a646d0e75e0a602c09a6e")), but I couldn't get it to work.

Therefore my solution was to:
- Roll back the driver to the version of the 28 April 2014
- make /usr/sbin/bluetoothd executable
- restart

I hope this helps.

---

### Post by Su_Heng on 2015-02-14
> **elfsternberg said:**
> Oh, another question: Isn't the screen hinge supposed to generate some kind of event when the screen is flipped over?  I don't want to have to do this manually every time.

[EDIT]: YES.  Moving the hinge past the 90° point will generate e03e, but X doesn't get the message because there's no keycode associated with "Unknown key 0xBE."  It's not possible to detect *where* the hinge is quite yet (toward the keyboard or away from it), but I'm one step closer to distinguishing between "keyboard mode," "portfolio mode" (widescreen, for watching video), and "tablet mode" (longscreen, for reading).

Any hints to implement it ?

---

### Post by allen_tools on 2015-02-18
So I bought a miix 2 11.6 and I love it, it's mostly like a  tablet and slate when you detach it from the keyboard but screen rotation with sensor input is out of the question as of currently as far as I can tell, thought if anyone has the answer to it or puts it into code I'd love to grab that off of you. I had a bit of trouble just looking around on the internet for screen rotation based off of screen orientation, or just automatic rotation so when I came across article and noticed some configuration, I wanted to put this out there for community use. if someone comes across or wants to work on automatic screen rotation i'll be on freenode as skweek

screen rotate

ubuntu 14.10 unicorn install lenovo miix 2 11.6 

```
sudo apt-get install autoreconf autoreconf2.5 xutils-dev libxi-dev cgmanager libcgmanager0 

wget https://github.com/wolneykien/xrandr...ive/master.zip
unzip  master.zip
cd xrandr-align-master
autoreconf -fi 
./configure 
make 
make install

xrandr -align list-input
xrandr 


```these two commands report "eDP1" and "Atmel Atmel maXTouch Digitizer" for use in scripts

```
sudo nano /usr/bin/monitor-touchpad.sh
#!/bin/bash
/usr/local/bin/xrandr-align  monitor --input="Atmel Atmel maXTouch Digitizer"

sudo nano /usr/bin/rotate-left.sh 
#!/bin/sh
rotation=`xrandr -q --verbose |grep eDP1 |cut -d ' ' -f6`
if [ $rotation = "normal" ] ;
then
  xrandr -o left
else
  xrandr -o normal
fi


sudo nano /usr/bin/rotate-right.sh 
#!/bin/sh
rotation=`xrandr -q --verbose |grep eDP1 |cut -d ' ' -f6`
if [ $rotation = "normal" ] ;
then
  xrandr -o right
else
  xrandr -o normal
fi

sudo chmod 755 /usr/bin/monitor-touchpad.sh
sudo chmod 755 /usr/bin/rotate-*.sh

gnome-session-properties 


```add moniter-touchpad, command /usr/bin/monitor-touchpad.sh to run at boot

make sure to change username to your username

```

mkdir ~/.local/share/applications/icons/
cp ~/Downloads/rotate-left.png ~/.local/share/applications/icons/rotate-left.png
nano ~/.local/share/applications/rotate-left.desktop
[Desktop Entry]
Name=Rotate Screen Left
Comment=Rotate Screen Left
Categories=Categories=GNOME;GTK;Utility;TerminalEmulator;System;
Exec=/usr/bin/rotate-left.sh
Type=Application
Terminal=false
Encoding=UTF-8
Icon=/home/username/.local/share/applications/icons/rotate-left.png


cp ~/Downloads/rotate-right.png ~/.local/share/applications/icons/rotate-right.png
nano ~/.local/share/applications/rotate-right.desktop
[Desktop Entry]
Name=Rotate Screen Right
Comment=Rotate Screen Right
Categories=Categories=GNOME;GTK;Utility;TerminalEmulator;System;
Exec=/usr/bin/rotate-right.sh
Type=Application
Terminal=false
Encoding=UTF-8
Icon=/home/username/.local/share/applications/icons/rotate-right.png

```

search and drag them to them to the desktop or elsewhere

[ATTACH=CONFIG]260078[/ATTACH][ATTACH=CONFIG]260079[/ATTACH]

---

### Post by DOS286 on 2015-04-02
I just got a Yoga 3 14. I like the computer over all, but I have a few annoying glitches that I'm having a hard time solving. I get random sticky keys and key drops. Sometimes they seem to come as frequently as 10 seconds, sometimes it goes quite a while without an issue. When the key sticks, it will repeat that character about 20 or so times and then back to normal. Periodically, the mouse will freeze as well. I believe that the mouse freezes happen at the same time as the keyboard issue but I'm never wiggling the mouse at the same time as typing so I don't know for sure. I read that others here have had random sticky key issues, but I have not found a solution that works. Can anyone help me trouble shoot this issue?

---

### Post by Bucky Ball on 2015-04-02
> **DOS286 said:**
> I just got a Yoga 3 14. I like the computer over all, but I have a few annoying glitches that I'm having a hard time solving. I get random sticky keys and key drops. Sometimes they seem to come as frequently as 10 seconds, sometimes it goes quite a while without an issue. When the key sticks, it will repeat that character about 20 or so times and then back to normal. Periodically, the mouse will freeze as well. I believe that the mouse freezes happen at the same time as the keyboard issue but I'm never wiggling the mouse at the same time as typing so I don't know for sure. I read that others here have had random sticky key issues, but I have not found a solution that works. Can anyone help me trouble shoot this issue?

Best to improve your chances of support by posting a new thread in a support area of the forums rather than bury yourself here on a non-support thread in a non-support area. Good luck. ;)

---

### Post by kamlesh3 on 2015-04-04
Even i have the same Lenovo ideapad yoga Ubuntu is running successfully & Smoothly. Let me where if you are facing any issues installing it.

---

### Post by felix25 on 2015-04-15
Hey Every1,

I freshly set up my YOGA IDEAPAD 13 yesterday to introduce some changes. I formerly used to rotate my screen with a modified version of rubo77's [rotate-screen.sh]("https://gist.github.com/rubo77/daa262e0229f6e398766#file-rotate-screen-sh") for some time but I stumpled over the work of pfpschneider (see [post #232]("http://ubuntuforums.org/showthread.php?t=1911972&p=12916659#post12916659")) and gave it a try.

Unfortunately I was not able to get it to work properly.

What I did so far: (... that I think is relevant for this problem)
Fresh ubuntu install - kernel 3.16.0-34-generic
apt-get upgrade (at 15apr15, 02:00 GMT)
installed libxrandr-dev packages and dependencies
installed git and dependencies
followed the guide of jacob_strandlien to the end (see [post #241]("http://ubuntuforums.org/showthread.php?t=1911972&p=12993611#post12993611")) - EXEPT after step 1 additionally doing 'make programs' and 'make programs-install' out of the main direcory of yoga-laptop (as instructed in the readme of the script))
checked if the setup script is actually running after login - ```
ps aux | grep setup
```
Output: ```
root      2032  0.0  0.0  91192  4640 ?        S    01:05   0:00 sudo /home/.../yoga-laptop/sensors/setup
root      2045  0.0  0.0  18612  3340 ?        S    01:05   0:00 /bin/bash /home/.../yoga-laptop/sensors/setup
...     6778  0.0  0.0  17456  2204 pts/0    S+   12:45   0:00 grep --color=auto setup
```

What I can do:
When executed manually, the orientation script in the sensors section (~/yoga-laptop/sensors) reports information about the screen position - along with a correct (at least logical) interpretation of them (left,right, normal, inverted, flat) - that tells me that the sensors are workng properly
Output: ```
Orientation 1, x:   -7, y:  -90, z:  -53
Orientation 1, x:   -7, y:  -91, z:  -52
Orientation at 1.0 is normal
```
xrandr is able to rotate the screen into all 4 orientations when executed manually with ```
xrandr -o <orientation>
```

What I can't do:
The orientation script should also execute the xrandr command with the interpreted output of the sensors - but i doesn't.
If run in a shell it "only" reports the above three lines in a periodical interval. No additional action is initiated if the screen is rotated. No additional output, no rotation.
I have issued the same question to the developer of the yoga-laptop scripts but would like to share this problem with you hoping that someone has figured it out.

How I successfully solved this:
There seems to be a small mistake in the current version of the orientation script. I already reported the possible solution to the author but (as I already wrote all this) I would like to share the Do-It-Yourself guide to you - its actually pretty simple:
 1) Download the files from pfps git hub using the
```
 git clone [https://github.com/pfps/yoga-laptop.git](https://github.com/pfps/yoga-laptop.git) command in the shell 
```
2) NEW --> BEFORE compiling the files with "make" open the orientations.c raw script with an editor (gedit)
In the Lines 406 to 411 (almost at the end of the file) you should find a sequence of code like this:

```
if (previous_orientation == orientation /* only rotate when stable */ && orientation != 
screen_orientation && orientation != FLAT && !orientation_lock) {
rotate_to(orientation);
previous_orientation = orientation;
}

```
This sequence is responsible to execute the actual rotation sequence IF the requirements behind the "if" are all met.
The mistake is that the "previous_orientation=orientation" command must be executed after each routine sequence of the program, not only after the requirement are met (because it's actually a prerequisite to meet them)
So, long story short: just take the command out of the sequence (the code between { } and place it in the line below
It should look like
```

if (previous_orientation == orientation /* only rotate when stable */ && orientation != 
screen_orientation && orientation != FLAT && !orientation_lock) {
rotate_to(orientation);
}
previous_orientation = orientation;

```
3) You can now compile the files
either from the ~/yoga-laptop directory using 'make programs' and 'sudo make programs-install'
or from the ~/yoga-laptop/sensors directory using 'make' and 'sudo make install'

4) What you SHOULD DO afterwards is running a test run by manually executing the freshly compiled "orientation" out of a shell by the command 
```

./orientation --count=10 --debug=4

```
This will run a sequence of only 10 turns and give you some additional feedback. Try to rotate the screen during these 10 sequences. It should work now.
The script might (highly likely) run into errors but will restart after a pause of 10sec. That's normal. The intended way to run it (the one you are going to use after the test-phase) is through the "setup" script that will set some additional rights for the files and that will avoid most of the errors. 
Anyway.. the first part of your output should look like this:
```

iio device number being used is 0
iio trigger number being used is 0
Finding orientation 0
Polling the data
Reading the data
Read the data
Orientation 1, x:   -4, y:  -98, z:  -28
Orientation 1, x:   -4, y:  -98, z:  -28
Found orientation: or:1, prev:-1, scr:-1, 0
Orientation at 0.0 is normal
Finding orientation 1
Polling the data
Reading the data
Read the data
Orientation 1, x:   -3, y:  -98, z:  -28
Orientation 1, x:   -3, y:  -98, z:  -28
Found orientation: or:1, prev:1, scr:-1, 0
Orientation at 1.0 is normal
ROTATE to normal

```
Please check if the Output "ROTATE to ..." is produced after the SECOND sequence. Thats intended as the programs is programmed to wait for the screen to come to rest in one orientation before it defines the orientation.

If thats all done you can continue with step 3 of[ jacob_strandliens guide]("http://ubuntuforums.org/showthread.php?t=1911972&p=12993611#post12993611").

Oh yeah.. and if you should find your cursor icon somehow messed up (mine has a 90° rotated and right shifted second image) then .. well there surely is a solution somewhere.

Thanks to pfp-schneider for creating a functioning auto-rotation for the YOGA13 and jacob_strandlien for his guide to auto-run it on login. I have been waiting for this for 3 years! Great job!



Thanks for your help folks

Felix

---

