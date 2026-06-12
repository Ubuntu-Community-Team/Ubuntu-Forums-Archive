---
title: "Upgrading to Ubuntu 11.04 Natty Narwhal"
date: 2011-04-28
forum: System76 Support
---

### Post by thomasaaron on 2011-04-28
[SIZE="4"]System76 Customers are clear to upgrade![/SIZE]

[SIZE="3"]**A couple of important notes:**[/SIZE]

[SIZE="2"]1. In pretty much every upgrade cycle, we see a number of corrupted upgrades due to Ubuntu's servers being overrun with early adopters. We would advise you to wait a week or so before doing the ***online*** upgrade. There are two advantages to waiting: First, you are less likely to experience a corrupted upgrade; and second, any bugs that were missed in initial testing most likely will be squashed in a week or two.

If you choose to go ahead and do the online upgrade, please ensure you are well backed up. If your upgrade is corrupted, we most likely will recommend a fresh installation.

Instructions for doing the online upgrade are **[[COLOR="Blue"]here[/COLOR]]("http://knowledge76.com/index.php/NattyUpgrade")**.

2. If you want to do a fresh install, those typically are less prone to problems. However, it is a good idea to double-check both your image and your burned CD / Flash Drive to make sure there is no corruption.

Instructions for doing a fresh install are **[[COLOR="Blue"]here[/COLOR]]("http://knowledge76.com/index.php/Restoring_Your_System")**.

3. There is an outstanding bluetooth bug in Natty that is being worked on by upstream developers. There is information on the bug in this [**[COLOR="Blue"]kernel mailing list[/COLOR]**]("https://lists.ubuntu.com/archives/kernel-team/2011-April/015366.html"). And you can follow it's progress via this [**[COLOR="Blue"]bug report[/COLOR]**]("https://bugs.launchpad.net/system76/+bug/762964"). **Additionally there is a work-around in post #6 of that bug report.**

4. Here is a [**[COLOR="Blue"]nicely done tour of Ubuntu 11.04[/COLOR]**]("http://omgubuntu.co.uk/natty/"), Natty Narwhal, and its Unity Interface.
__________________

Follow System76 on [COLOR="Blue"]**[Twitter]("http://twitter.com/system76")**[/COLOR] or **[COLOR="Blue"][Facebook]("http://facebook.com/system76")[/COLOR]**.[/SIZE]

---

### Post by alaaji on 2011-04-29
It may be worth mentioning that you can also upgrade 10.10 by using the 11.04 cd.  

[http://digitizor.com/2011/04/28/upgrade-to-ubuntu-11-04/]("http://digitizor.com/2011/04/28/upgrade-to-ubuntu-11-04/")

---

### Post by jeffran on 2011-04-29
My experience so far:

I performed a clean install of 11.04 on my ratu1 and panp4n - it's working great on both. Initially I wasn't sure about Unity but the more I use it the more I like it - I think it's a real improvement.

---

### Post by Cygnia on 2011-04-30
@Jeffran - I also have the PanP4n. How did you get the nVidia drivers to work? In the Additional Drivers (Jockey) dialog it says the driver is "activated but not currently in use." I've been searching the rest of the forums for hours and although many have the same problem no one has found a solution that's easy to understand. It's eventually going to be a deal breaker for me since although videos play even simple games won't work with the open source "experimental" drivers that I've had to switch to while seeking the answer. Thanks to all for any pointers.

---

### Post by jeffran on 2011-04-30
> **Cygnia said:**
> @Jeffran - I also have the PanP4n. How did you get the nVidia drivers to work? In the Additional Drivers (Jockey) dialog it says the driver is "activated but not currently in use." I've been searching the rest of the forums for hours and although many have the same problem no one has found a solution that's easy to understand. It's eventually going to be a deal breaker for me since although videos play even simple games won't work with the open source "experimental" drivers that I've had to switch to while seeking the answer. Thanks to all for any pointers.

Interesting, I didn't do anything special. After the clean install and restart, I opened the additional drivers dialog (a little icon for it automatically popped into the top toolbar on the right), clicked the radio button for the 'recommended' version, and clicked install/activate. From there it installed without a hitch. Did you do a clean install as well, or an upgrade? Maybe that would make a difference. I hope you get it working. - Jeff

---

### Post by Cygnia on 2011-04-30
> **jeffran said:**
> Did you do a clean install as well, or an upgrade? Maybe that would make a difference.

It's a fresh install as well. When you open up the Additional Drivers dialog at this point does it say the driver is in use, or just "Activated But Not Currently In Use"? And if you install a game such as Solarwolf or similar, does it play without problems? I'd just like to get this solved or else I'll have to reinstall Maverick. Thanks for your replying on a Saturday!:P

---

### Post by jeffran on 2011-04-30
> **Cygnia said:**
> It's a fresh install as well. When you open up the Additional Drivers dialog at this point does it say the driver is in use, or just "Activated But Not Currently In Use"? And if you install a game such as Solarwolf or similar, does it play without problems? I'd just like to get this solved or else I'll have to reinstall Maverick. Thanks for your replying on a Saturday!:P

No worries, here's a screen cap of my additional drivers dialog. Funny - now that I look at it mine also says "This driver is activated but not currently in use." - but it's clearly working since Unity wouldn't work for me (after initial restart following OS install I was put in the classic Gnome env) until I installed the driver. Also, graphic intensive apps like Inkscape work as I would expect. I hope this helps. - Jeff

---

### Post by zipmon on 2011-04-30
Just wondering, has anyone done the upgrade to 11.04 on a Starling? Is everything working, and is anything working better? 

I ran it off of a LiveUSB for a few hours and the only thing that didn't seem to work for me was the battery charge level indicator (it always said "estimating...") on the panel. Wireless and Unity both worked fine right off the bat, though!

---

### Post by azion1995 on 2011-05-01
I just finished the update, including the System76-specific directions, and everything worked absolutely perfectly. Color me impressed!
:guitar:

-Z

---

### Post by gamerchick02 on 2011-05-06
> **zipmon said:**
> Just wondering, has anyone done the upgrade to 11.04 on a Starling? Is everything working, and is anything working better? 

I ran it off of a LiveUSB for a few hours and the only thing that didn't seem to work for me was the battery charge level indicator (it always said "estimating...") on the panel. Wireless and Unity both worked fine right off the bat, though!

I've been running Natty from the beta on the Starling; everything works great!

This version of Unity is so much better from the last, it's unreal.

Amy

---

### Post by wazoo on 2011-05-06
It took a long time, but the upgrade seemed to go well. Interesting overall. One problem that my random Google searches haven't solved: it reset my resolution from 1280x1024 to 1024x768. The "monitors" program didn't offer the higher resolution, so I went looking for the xorg.conf file. Doesn't exist. I have no idea how to go about fixing this. Anybody else?

---

### Post by aranaea on 2011-05-09
> **wazoo said:**
> It took a long time, but the upgrade seemed to go well. Interesting overall. One problem that my random Google searches haven't solved: it reset my resolution from 1280x1024 to 1024x768. The "monitors" program didn't offer the higher resolution, so I went looking for the xorg.conf file. Doesn't exist. I have no idea how to go about fixing this. Anybody else?

Not sure which machine you have but on my serp7 I use the nVidia X server settings to change resolution settings.

---

### Post by isantop on 2011-05-09
> **wazoo said:**
> It took a long time, but the upgrade seemed to go well. Interesting overall. One problem that my random Google searches haven't solved: it reset my resolution from 1280x1024 to 1024x768. The "monitors" program didn't offer the higher resolution, so I went looking for the xorg.conf file. Doesn't exist. I have no idea how to go about fixing this. Anybody else?

What model is your computer? Aranaea just about hit it; it will depend on what kind of system you have.

---

### Post by nealaustin on 2011-05-10
> **gamerchick02 said:**
> I've been running Natty from the beta on the Starling; everything works great!

This version of Unity is so much better from the last, it's unreal.

Amy

Thanks gamerchick. Your post gave me the guts to try to to upgrade. My Star1 was running 10.04. I didn't do a clean install. I went through the upgrade manager and it offered 10.10 which I did. I then Immediately ran the update manager again and it offered me the 11.04 upgrade. I ran with it and I am blown away at how it worked. The finicky wireless works great, the wireless HP-printer drivers work out of the box, EVERYTHING works. The only beef I have with Natty Narwhal is how all of the system and administrative apps are all discombobulated into the other apps.

---

### Post by pocklecod on 2011-05-12
Ugg!  Did an upgrade on my star4 exactly as per system76's directions, including the driver update - after the driver update, restarted and my machine said I did not have the hardware required to run Unity.  The system is working right now, but in traditional ubuntu layout - making it much LESS visually efficient than 10.04 was.  In fact...this is borderline unusable.

Unity did work immediately after the upgrade and before the system76 driver update.
 
Gah!  This is so frustrating.  What happened here?  Do I need to go back to 10.04, and should other users be warned?

---

### Post by isantop on 2011-05-13
Did you upgrade through 10.10 to 11.04? I'm getting a Starling ready to test that with now, but my theory is a botched upgrade. Can you try a fresh installation?

---

### Post by aranaea on 2011-05-16
I'm getting ready to re-install 10.10 on my serp7 and thought I'd check in to see if anyone had comments about rolling back.  I expect to just do a clean install, set up the nVidia proprietary drivers, and then install the System76 drivers.  Really just following [this]("http://knowledge76.com/index.php/Restoring_Your_System") guide.

I'm guessing that if I don't want the auto updater to pull me back into 11.04 land I'll need turn off auto updates, which worries me a little.  I don't want to end up with any security holes down the line.

For the curious, I'm not rolling back out of spite for Unity.  I've been having three issues since updating to 11.04.

1) Periodically things just freeze up and I have to reboot.  May be unrelated but this never happened before.
2) No fingerprint scanner.  Probably sounds like a small thing but I like having it and it used to work.
3) External monitor switching.  11.04 seems to have switched to the open source nVidia drivers and I think these have broken my Fn+F7 monitor switching.  I use that a lot and it blows to have to open the XServer settings everytime.

I figure these things will be fixed at some point but for now 11.04 fixes problems I didn't have and breaks things I need/want so I'm going back to my last known good build until it settles down a bit.

Thanks for any feedback/input about problems I might run into.

---

### Post by Flyers2391 on 2011-05-17
> **aranaea said:**
> 
I'm guessing that if I don't want the auto updater to pull me back into 11.04 land I'll need turn off auto updates, which worries me a little.  I don't want to end up with any security holes down the line.


Under System > Administration > Software Sources, go to the Updates Tab.  The bottom of that should show "Release Upgrade" I have it set to "Long Term Support Releases Only".  This is separate from the security updates above it.

---

### Post by adakite on 2011-05-20
Hi Guys,

 I tried to update my system76 (Lemur) from 10.04 to 11.04. The update run well but after rebooting the system, I got 

error: symbol not found: 'grub_env_export'
grub rescue>

I tried to deal with some grub rescue tips, but for some reasons the ls command gives me this strange return:
(hd0) (hd0,msdos5) (hd0,msdos1)

while no fat partitions are present on my system as only Ubuntu were installed by System76. Which is odd as well is that ls (hd0,msdos1)/boot/grub gives expected return (lot of *.mod files and so on) so something very funky happened during the update. Anyways, I thus created a bootable usb-stick from 11.04 (amd64) iso using dd command on my other laptop (Apple Macbook). this last is able to mount it, unfortunately, the Lemur isn't. I configured the Lemur so as to boot on the USB stick, but apparently is not able to do it correctly as I always get the grub error message mentioned previously. I don't really about my data, but I would really appreciate to use my lemur. 

Is there any chance to have a clean install from USB, as lemur does not have any optic reader?

What did I miss?


Thanks for any help/ideas/suggestions….

A.

---

### Post by isantop on 2011-05-20
I think I answered your other forum post. We can continue here or there, wherever you prefer.

---

### Post by adakite on 2011-05-20
Hi,

yes, sorry for this double,

I provide a solution on the other thread: 

[http://ubuntuforums.org/showthread.php?p=10842959&posted=1#post10842959](http://ubuntuforums.org/showthread.php?p=10842959&posted=1#post10842959)


Cheers,
 A.

---

### Post by 130s on 2011-05-25
Just seconding to some guys, but I've been successfully updated my Star3 10.04 netbook edition to Natty 11.04 (via upgrading to 10.10) so far. Though I've seen some mischievous behavior with some apps and also performance might be a bit slower, overall it looks good enough. 
One question is that is it ok that System Monitor says the OS is 11.04, not netbook edition or similar stuff?

---

### Post by isantop on 2011-05-26
Starting with 11.04, there is no more dedicated Netbook edition. Instead, there is code in Unity that detects your screen size and optimizes the environment for that. Thus, there is only one version of Ubuntu, and it's now called simply "Ubuntu".

---

### Post by jhorsman on 2011-06-02
I have the Wild Dog Performance wil-p7. I did an upgrade from 10.10 first and got a message saying I do not have the correct hardware to run Unity and that I have to use classic Ubuntu to log in with. So, I decided to do a clean install (wiped out everything) and I no longer got this message, but I am having a heck of a time getting my software to compile (VisIt and VTK). After installing all kinds of libraries to no avail, I decided to start over so I could record everything I did. So, again, I did a clean install of Ubuntu 11.04 and now I am again getting the message that I do not have the correct hardware to run Unity!

It is strange to me that I didn't get the message once, but am getting it again. And I am frustrated that I can't get my software to compile, even though it worked fine in 10.04 (Lucid Lynx). I'm thinking of going back to 10.04 because at least I know it worked. I have seen some references to the Nvidia driver being a problem (I have the GeForce GTX 470 graphics card.)

By the way, one of the errors I get when compiling VTK is:
error: ‘vtkXMesaRenderWindow’ has not been declared

Jennifer

---

### Post by jhorsman on 2011-06-02
I just saw the web site that said I can activate the Nvidia driver (current), so I guess that problem is solved. I think what I must have done different last time is, after a clean install of Natty, I then used the Update Manager to apply all the updates. Then I did the System76 restore. This time, I did the restore before applying updates.

Not sure why I can't get VTK to compile, though. I will keep working on it.

Jennifer

---

### Post by gamx on 2011-07-03
I have a Darter Ultra 2. I have upgraded from Maverick to Natty and now, when the computer is idle, there is some flickering. I think there might be something wrong with the brightness controls. Any idea about what I can do?
Thanks in advance,

Gamx

---

### Post by drsnyder on 2011-08-28
I'm having some trouble with my panp7 after upgrading to natty. I get the following error after I login (see screenshot below). And the right-side-track-pad scroll bar is no longer working.

Could the two be related? Is there anyway I can restore my original configuration? Thanks!

---

### Post by isantop on 2011-08-30
The screenshot is too small, I can't make out what the error message is.

The trackpads now support two-finger scrolling, which will be enabled by default. If you want to change it back to edge scrolling, you can do so by changing the setting in the mouse preferences dialog.

---

### Post by drsnyder on 2011-08-31
Ok, this screen capture should be more visible. Sorry about that. 

Ah, I did not know about the two finger scroll! I like that better!

Thanks.

---

### Post by isantop on 2011-08-31
Try running this command from a Terminal:

```
sudo rm /etc/X11/xorg.conf
```

This will remove your existing X11 configuration settings, causing a new one to be autogenerated the next time you boot. After running this, you may need to reconfigure your monitor settings.

---

