---
title: "unity-greeter"
date: 2012-02-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bmbaker on 2012-02-14
latest unity greeter doesn't show correct background. shows the old warty background!

---

### Post by rburkartjo on 2012-02-14
and you cant change background on the latest greeter

---

### Post by AnojiRox on 2012-02-14
you **can** change the background for the greeter. just launch terminal, type:'gksudo nautilus', find the file /etc/lightdm/unity-greeter.conf and double click it. find the line 
background=whatever
change 'whatever' to the poath of the background and... **voila!**:P

---

### Post by bmbaker on 2012-02-14
ya i know that! it doesn't wk after the last update of unity-greeter ! but thanks though !

---

### Post by grahammechanical on 2012-02-14
In my case I can change the LightDM background image by selecting a static desktop background but the image does not remain on the screen while LightDM hands over to the user interface. I get staggered blocks of multicoloured pixels across the screen until the desktop loads. It is not nice to see.

**Update:** It is my guess that since the latest update of LightDM that it is no longer looking to /etc/lightdm/unity-greeter.conf for it configuration.

I use Simple LightDM Manager to set the background so I can have the desktop background slide show working. My unity-greeter.conf still has the same settings as before. The background image for LightDM is not set for the warty background but if I select the slide show as the desktop background then I get the warty image. If I select a static desktop background image then that is what I get as the LightDM background image. Further more, Simple LightDM Manager is no longer effective.

I also get the horrendous mix of pixels as LightDM hands over to the desktop.

Hence my conclusion the LightDM is looking somewhere other than /etc/lightdm/unity-greeter.conf. But where is it looking?

Regards.

---

### Post by arpanaut on 2012-02-14
From the changelog:
```
unity-greeter (0.2.1-0ubuntu1) precise; urgency=low * New upstream release

    - Fix session menu button not showing for first user
    - Skip indicators that fail to load
    - Distribute translations correctly
    - Load indicators from location specified in pkg-config
    [COLOR=Blue]- Use gsettings instead of /etc/lightdm/unity-greeter.conf[/COLOR]
    - Accept numpad arrow key presses
    - Instead of showing all layouts in the system in the keyboard indicator,
      only show the layouts a user has configured
    - Don't crash if gnome-settings-daemon's gsettings schema isn't as expected
    - Disable gnome-settings-daemon's new gsdwacom plugin as well as its older
      wacom plugin
    - Use vala-0.16 instead of valac-0.14
  * debian/control:
    - Bump valac build-depend to valac-0.16
    - Bump liblightdm-gobject build-depend to one that has backported
      keyboard layout query functions

 -- Michael Terry <mterry@ubuntu.com>  Mon, 13 Feb 2012 15:25:10 -0500

```That could be the reason for the change of behavior?
Woof...that hand-off IS pretty ugly!

---

### Post by nariub on 2012-02-14
could it have something to do with this?

[http://ubuntuforums.org/showthread.php?t=1911498](http://ubuntuforums.org/showthread.php?t=1911498)

they were changing the greeter to show the user's desktop background while you enter the user's password.

---

### Post by arpanaut on 2012-02-14
Yeah, that was three weeks ogo, a Long time in Ubuntu +1.

Nevertheless I have one system that is acting as expected giving the user's BG in the greeter,
and one system that I can't get the user's BG to show no matter what I try. config file, gconf, or dconf editors.
The visual glitch on the hand-off to the desktop is present on both.

Going to dig in some log files.
LOL everybody trying to get their bits in before Feature Freeze.

 edit: Thanks mc4man, added a me too.

---

### Post by mc4man on 2012-02-14
Bug on corrupted 
[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/932324](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/932324)

---

### Post by Jdogzz on 2012-02-14
I remember a while back that the new version of the logon screen would change backgrounds depending on the user selected that would match the wallpaper of the user. However, I am unable to duplicate that in either of the 2 installs I have tried since then. Was this feature removed or is there a trick to getting it to work? Maybe having my home folder encrypted is part of the problem?

---

### Post by cariboo on 2012-02-14
Merged two threads on the same subject

---

### Post by jbicha on 2012-02-14
By the way, the lightdm wallpaper trick won't work on the .xml slideshow images (in other words, the Ubuntu contest wallpaper and the GNOME blue blinds wallpaper). Also, lightdm has to be able to access the wallpaper so if it's encrypted, it might not work. I don't use an encrypted home directory so I don't know for sure on that.

---

### Post by mc4man on 2012-02-16
The corruption and what happens after entering the password, (the hand off) can be affected in a multiboot by where grub is installed to. (which grub is 'controlling'

So for example I was getting corruption on a 12.04 login when grub was last installed in that 12.04 install.

Switching grub to a 11.04 install removes the corruption, but the 'hand off' now shows the default 11.04 greeter after entering password & pressing enter

---

### Post by ventrical on 2012-02-17
Anyone else get these?

[http://www.youtube.com/watch?v=ZO5r781ZZVc](http://www.youtube.com/watch?v=ZO5r781ZZVc)

```
camel2@ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI Radeon Xpress 200 Host Bridge (rev 01)
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI-X Root Port
00:06.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:11.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-PCI Bridge (rev 80)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce G210] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
03:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
camel2@ubuntu:~$ 

```

---

### Post by PaulW2U on 2012-02-17
Yes, I get other screen corruption too.

An example - the left hand side of the screen is in the centre and the right hand side wraps around to the left. But its not consistent, the corruption is different each time I log-in.

Hope that made some sort of sense. :)

---

### Post by ventrical on 2012-02-17
> **PaulW2U said:**
> Yes, I get other screen corruption too.

An example - the left hand side of the screen is in the centre and the right hand side wraps around to the left. But its not consistent, the corruption is different each time I log-in.

Hope that made some sort of sense. :)

Exactly.. I am getting different corruption each log on. I  have been getting it for a while now .. but just didn't say nothing .. assumed it would just go away :)

  I'm not sure what to file the bug against. The screen reverts back to normal after a few seconds and the  logical boot-up completes and I'm in. so it is not affecting the system as a whole.

---

### Post by philinux on 2012-02-17
No doubt a compiz bug. I'm not getting it with nvidia 8600gt.

---

### Post by bmbaker on 2012-02-17
its the same as this post [http://ubuntuforums.org/showthread.php?t=1925194&page=2](http://ubuntuforums.org/showthread.php?t=1925194&page=2)

---

### Post by cariboo on 2012-02-17
Merged the two similar threads.

---

### Post by ventrical on 2012-02-17
> **cariboo907 said:**
> Merged the two similar threads.

  Thanks .. at least I have a bug reference now.

---

### Post by ventrical on 2012-02-17
> **philinux said:**
> No doubt a compiz bug. I'm not getting it with nvidia 8600gt.

But the bug is against Unity Greeter..

---

### Post by PaulW2U on 2012-02-18
> **ventrical said:**
> But the bug is against Unity Greeter..

Nothing to do with compiz.

I also see this bug when logging into Gnome Shell which doesn't even use compiz.

---

### Post by ventrical on 2012-02-19
Recent updates have made it even worse.  The Unity Greeter was working  perfectly a week or so ago and now it has regressed to an awkward state.

---

### Post by ventrical on 2012-02-19
I just updated an ATi endowed machine which has not been updated for over a week and I now have the Unity Greeter corruption there too.

---

### Post by VinDSL on 2012-02-19
> **philinux said:**
> I'm not getting it with nvidia 8600gt.
Not getting it with my nVidia 7600GT either.  Been working perfectly, all along.

Maybe, it's ATI [COLOR="Gray"][s]related[/s][/COLOR]  specific :confused:

---

### Post by mc4man on 2012-02-19
Removed - one of the worst things I've ever suggested

---

### Post by VinDSL on 2012-02-19
Good job, detective!  ;)

Every little bit helps...

---

### Post by ventrical on 2012-02-19
> **mc4man said:**
> If you're getting corruption & or a Mosaic on the login, (I was till just a moment ago), then check here

Open /usr/share/backgrounds
If warty-final-ubuntu has a .png extension then change to .jpg, do a log out & all should be relatively well

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-wallpapers/+bug/936604](https://bugs.launchpad.net/ubuntu/+source/ubuntu-wallpapers/+bug/936604)

Edit: only worked for log out/ins, after a full restart went back to corruption (too bad

boy oh boy .. and would you be so kind as to instruct us how to rename that file.. I did it manually with other files in terminal .. but it won't work now..


this is unbelivable.. this is a security nightmare .. a small error such as that .. I mean what else is vulnerable ?

---

### Post by VinDSL on 2012-02-19
Oh, oh!

[LIST=1]
[*]Renamed file from .png to .jpg
[*]Ran a quick check
[*]Broke symlink in /usr/share/unity-2d
[/LIST]

Hrm...

---

### Post by PaulW2U on 2012-02-19
> **mc4man said:**
> If warty-final-ubuntu has a .png extension then change to .jpg, do a log out & all should be relatively well


I've marked that one as affecting me so the status is now showing as confirmed.

---

### Post by mc4man on 2012-02-19
READ my edit, only worked here for log out/ins, a reboot returned the nonsense

Actually - maybe they want that file to be named .png ?? It has been for quite a while

I just happened to try to open it in eog & it wouldn't unless I renamed.

Anyway this is the oddest bug I've seen in quite some time

IF it's renamed then can't be found to change too, my bad (**very**

---

### Post by ventrical on 2012-02-19
> **PaulW2U said:**
> I've marked that one as affecting me so the status is now showing as confirmed.


Uh oh .. I think I foobarred my system.. I renamed the file using gedit .. I'll be back :)

---

### Post by VinDSL on 2012-02-19
I renamed the file and symlink back to .png and all is good now.

I *think* I'll use Gimp and convert the graphic to a .png -- and let them handle it upstream.

No telling what the overall effect will be, otherwise.

Heh!  I hate messing with LightDM...  :D

---

### Post by VinDSL on 2012-02-19
> **ventrical said:**
> Uh oh .. I think I foobarred my system.. I renamed the file using gedit [...]
Congrats!

I might have to try that -- I'm bored.  :)

---

### Post by ventrical on 2012-02-19
> **VinDSL said:**
> Congrats!

I might have to try that -- I'm bored.  :)

  I got some recovery , used ;

sudo -i nautilus

 and changed the name of the .png file to .jpg and now it is just an empty space where the original file used to be and I still have corrupt screen after log-on .. so I think there is somthing more busted than that .png to jpg file...

---

### Post by mc4man on 2012-02-19
> **ventrical said:**
> Uh oh .. I think I foobarred my system.. I renamed the file using gedit .. I'll be back :)

That's a good trick - how do you rename an image file in gedit?
(Hope I didn't cause you too much issue with my idiocy  -

---

### Post by ventrical on 2012-02-19
> **VinDSL said:**
> I renamed the file and symlink back to .png and all is good now.

I *think* I'll use Gimp and convert the graphic to a .png -- and let them handle it upstream.


Thats what I was doing during Oneric testing and it worked great but Gimp will not recognize the file. only as corrupt ..
You might have better luck than me.

---

### Post by ventrical on 2012-02-19
> **mc4man said:**
> That's a good trick - how do you rename an image file in gedit?
(Hope I didn't cause you too much issue with my idiocy  -


No .. no .. no .. I'm the idiot here .. I should know better and used sudo -i nautilus. and I did that and  it didn't work anyways.

I just did this:

$cd /usr/share/backgrounds
$sudo -i gedit warty-final-ubuntu.png

Save as warty-final-ubuntu.jpg

sudo -i nautilus

filesystem>warty-final-ubuntu.jpg>sendtotrash
rename warty-final-ubuntu.png to warty-final-ubuntu.jpg

---

### Post by ventrical on 2012-02-19
> **mc4man said:**
> READ my edit, only worked here for log out/ins, a reboot returned the nonsense

Actually - maybe they want that file to be named .png ??

  I'm pretty sure that those background files are not the problem because I have tired different backgrounds will all the same results so, then , the question is  why would we assume that warty-final-ubuntu.png is a culprit here ?

---

### Post by mc4man on 2012-02-19
> **ventrical said:**
> I'm pretty sure that those background files are not the problem because I have tired different backgrounds will all the same results so, then , the question is  why would we assume that warty-final-ubuntu.png is a culprit here ?

I guess you didn't read my edits - was a poor, poor suggestion on my part, the odd thing was it did give me perfect logins for a while (then I rebooted & saw what a terrible idea it was

---

### Post by ventrical on 2012-02-19
> **mc4man said:**
> I guess you didn't read my edits - was a poor, poor suggestion on my part, the odd thing was it did give me perfect logins for a while (then I rebooted & saw what a terrible idea it was

 Thanks for sharing that .

However.. on my other installs this corruption is not happening.

Edit:

So it appears that  it is happening on ATi and Nvidia and not Intel.!!

Is that any help?


```

madame@madame-ME051:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:05.0 Ethernet controller: Atheros Communications Inc. AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] (rev 01)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
madame@madame-ME051:~$ 

```


edit: and btw .. i also tried creating new users and the corruption is still there on those new users.

---

### Post by VinDSL on 2012-02-19
> **mc4man said:**
> Hope I didn't cause you too much issue with my idiocy [...]
It's all good fun, man!  :D

After I renamed those files back n' forth, Unity decided to pin my desktop wall with the "Monkey Vomit Purple" default, in the middle of the session.  

Took a little idiocy, on my part, to switch it back to the wall I wanted.  LoL!

The fix survived a boot, and everything is back to normal... drat!

Anyway, that's how you learn about these things, no?

---

### Post by ventrical on 2012-02-19
> **VinDSL said:**
> It's all good fun, man!  :D

After I renamed those files back n' forth, Unity decided to pin my desktop wall with the "Monkey Vomit Purple" default, in the middle of the session.  



hehaehaehahah ..  you crack me up Vin :)

---

### Post by mc4man on 2012-02-19
The only reason I was looking at that image file (was going to alter it slightly) is because on a multiboot sometimes I don't get any 'corruption' on the newest 12.04 login, I get the greeter image from my 11.10 install which seems quite wierd.

Also at times when I get a mosaic, the snippets are from things I've viewed during the day, again it's weird that they are being 'saved' somewhere? And other user accounts can get snippets from what I was looking at

---

### Post by ventrical on 2012-02-20
> **mc4man said:**
> The only reason I was looking at that image file (was going to alter it slightly) is because on a multiboot sometimes I don't get any 'corruption' on the newest 12.04 login, I get the greeter image from my 11.10 install which seems quite wierd.

Also at times when I get a mosaic, the snippets are from things I've viewed during the day, again it's weird that they are being 'saved' somewhere? And other user accounts can get snippets from what I was looking at


Thats exactly it.. "snippets" . Like I'll see snippets  of avatars from firefox, messages , other backgrounds .. its like it is being saved in some kind of buffer and then unloaded after logon or restart.

 But I don't get them on the Intel based video adapter installs that I have.

---

### Post by ventrical on 2012-02-20
Fixed!!!!

Disable- Save plugin states on unload: from CCSM General !!

Note to Philinux... you were right !!

Edit.. so we can file a bug against CCSM at least , or so it appears.

---

### Post by ventrical on 2012-02-20
> **philinux said:**
> No doubt a compiz bug. I'm not getting it with nvidia 8600gt.

 It was the "save plugin states on unload" from the General Options of the CCSM.

---

### Post by mc4man on 2012-02-20
Really an interesting bug, still wonder how these image snips are surviving restarts, ect.

One thing I do that sometimes changes it up is this - 
create a color .html, open it up in firefox fullscreen (F11) & while in FF fullscreen force a restart
(I use the old Ctrl+Alt+backspace enabled in Keyboard > Layout settings > options, 
Something like this will often give me  stacked white & black stairways
```

<html>
<head>

<title>Fool Around</title>
</head>

<body style="background-color:#000000;">
</body>
</html>
```

Edit : will give the compiz thing a try, except - it's not enabled here ?
Didn't help here..

---

### Post by ventrical on 2012-02-20
Here is what I filed..

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/936866](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/936866)

---

### Post by ventrical on 2012-02-20
> **mc4man said:**
> Really an interesting bug, still wonder how these image snips are surviving restarts, ect.

One thing I do that sometimes changes it up is this - 
create a color .html, open it up in firefox fullscreen (F11) & while in FF fullscreen force a restart
(I use the old Ctrl+Alt+backspace enabled in Keyboard > Layout option > options, - 1st use does a log out, 2nd a restart, 3rd a log out, ect.

Something like this will often give me  stacked white & black stairways
```

<html>
<head>

<title>Fool Around</title>
</head>

<body style="background-color:#000000;">
</body>
</html>
```Edit : will give the compiz thing a try, except - it's not enabled here ?


 Hmmmm.. there was this 'oneconf' single update ... but I still had corruption until I disabled that CCSM setting .

Just plain weird this one is.

---

### Post by ventrical on 2012-02-20
Ok .. sorry all.. me idiot... that bug I filed .. nope !  All the relics are back after hard-boot..  so it is NOT compiz or CCSM.

---

### Post by ventrical on 2012-02-20
Sorry all.. this bug:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/936866](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/936866)

is a NON-bug.  I got so excited that I had thought I solved this corrupt logon problem that I filed a bug before hardbooting.

---

### Post by prusswan on 2012-02-20
anyone noticed that the session type is sometimes reset after installing certain packages? I noticed that one of my machines will go into Unity 2D from Gnome Classic, but haven't found a reliable way to reproduce it.

---

### Post by ventrical on 2012-02-20
I just still cannot figure out why  this corruption does not affect Intel graphics adapters and only ATi and Nvidia cards.!

---

### Post by MG&amp;TL on 2012-02-20
> **ventrical said:**
> I just still cannot figure out why  this corruption does not affect Intel graphics adapters and only ATi and Nvidia cards.!

Errrm. I think I can rule out lightdm (if it hasn't been done already), I have an Nvidia card and lightdm (but not unity-greeter-ified, Lubuntu :) ), but no ghosting, images, whatever. Are you guys on proprietary drivers? I'm on nouveau drivers.

---

### Post by ventrical on 2012-02-20
> **MG&TL said:**
> Errrm. I think I can rule out lightdm (if it hasn't been done already), I have an Nvidia card and lightdm (but not unity-greeter-ified, Lubuntu :) ), but no ghosting, images, whatever. Are you guys on proprietary drivers? I'm on nouveau drivers.

Nvidia current .. I'll try the switch..

I have Lubuntu desktop installed along with others on my Dell Opti. Thats and Intel graphics card too.. no corruption..

---

### Post by ventrical on 2012-02-20
WoW .. yet another clue... I just ran  <additonal drivers and got this:

*note* 'This driver is activated but not currently in use'.

It gets weirder and weirder... :)

---

### Post by ventrical on 2012-02-20
K, I installed the NVIDIA binary  driver and same results .. Now I will try to re-install Nvidia current.

---

### Post by MG&amp;TL on 2012-02-20
> **ventrical said:**
> K, I installed the NVIDIA binary  driver and same results .. Now I will try to re-install Nvidia current.

I might note that my driver (nvidia-173) failed to build for the latest kernel, so my jockey window is entirely blank...that just confuses matters entirely.

---

### Post by ventrical on 2012-02-20
> **MG&TL said:**
> I might note that my driver (nvidia-173) failed to build for the latest kernel, so my jockey window is entirely blank...that just confuses matters entirely.

  I re-installed nvidia current, got rid of the relic/crazed/corrupt screen after log on ,but , now I have Big Icon resolution and my logons default to Unity 2d and my monitor is not detected.

  Looks like a big Nvidia-driver problem after all but before  I assume that I am going to manually purge nvidia through the terminal and then reinstall it from there.

hrrmmmm... lemme see...

---

### Post by ventrical on 2012-02-20
and here ??

---

### Post by arpanaut on 2012-02-20
> Are you guys on proprietary drivers? 

I'm on the open source Radon driver, About one in five it pops straight through to the desktop.
I'm not seeing any errors in the lightdm or the Ubiquity logs, nothing in x-session-errors either.
Just before last Thrus. or Friday it was just fine in fact I thought the transition to the desktop was faster.
A real puzzler? Sometimes it pops me through to Unity 2d??? But when I log off U 3d is still selected.

...life goes on!

---

### Post by ventrical on 2012-02-20
> **arpanaut said:**
> I'm on the open source Radon driver, About one in five it pops straight through to the desktop.
I'm not seeing any errors in the lightdm or the Ubiquity logs, nothing in x-session-errors either.
Just before last Thrus. or Friday it was just fine in fact I thought the transition to the desktop was faster.
A real puzzler? Sometimes it pops me through to Unity 2d??? But when I log off U 3d is still selected.

...life goes on!

Oh joy .. oh rapture .. :)

I got the big screen!
sheesh ...

---

### Post by MG&amp;TL on 2012-02-20
> **ventrical said:**
> Oh joy .. oh rapture .. :)

I got the big screen!
sheesh ...


Whoah...mobile-sized screen. :shock:

I guess this it when the Intel lot get to look smug because their company is more helpful...mine's still going, but lightdm has been buggy, and has never felt secure, so I guess it will be buggy in future.

---

### Post by ventrical on 2012-02-21
> **MG&TL said:**
> Whoah...mobile-sized screen. :shock:

I guess this it when the Intel lot get to look smug because their company is more helpful...mine's still going, but lightdm has been buggy, and has never felt secure, so I guess it will be buggy in future.


  I did eventual get my screen back but activating/deactivating nvidia drivers from <additional drivers , but it is still very touchy with lots of broken pieces of avatars from the forums after log-on. Also appears that someone has remote access (I'm not worried) but them it may be a keyboard buffer problem also or zeitgiest.

---

### Post by ventrical on 2012-02-21
Did the same thing with Kubuntu 12.04 after update ... defaulted to 800X640 and can't control the res though display. No graphics corruption though.

---

### Post by petersonja on 2012-02-22
I can't login to my Desktop with Enter key (no password required), just when I click with the mouse ot the Login button.

Anyone else experienced it?

---

### Post by ventrical on 2012-02-24
With latest updates I now have a newer kind of distortion after log-on with the Unity Greeter. And Unity greeter was included in updates.

---

### Post by ventrical on 2012-02-24
This appears to be an itermittent problem as the distortion will disappear completely  from time to time after reboot.

---

### Post by LADmaticCA on 2012-02-25
Hello. I was curious if anyone else is having this minecraft-like screen after they login?

[IMG]http://imgur.com/zQdRN[/IMG][http://imgur.com/zQdRN]("http://imgur.com/zQdRN")

The desktop loads normally, but I always see that before-hand for like 2 seconds. It's probably my graphics card...Evga Geforce240 GT

---

### Post by skewty on 2012-02-25
You are correct in that it has to do with your graphics card.  It has to do with the nvidia graphics card driver.  There is nothing you can do about it.  Canonical and NVidia need to work together much closer to prevent things like this.  I doubt you will see a flicker free startup without garbage on the screen for another 6 or 7 years.  Welcome to GNU/Linux.

---

### Post by sgage on 2012-02-25
> **skewty said:**
> You are correct in that it has to do with your graphics card.  It has to do with the nvidia graphics card driver.  There is nothing you can do about it.  Canonical and NVidia need to work together much closer to prevent things like this.  I doubt you will see a flicker free startup without garbage on the screen for another 6 or 7 years.  Welcome to GNU/Linux.

This is alpha software. The graphical glitches at log on just started a couple of weeks ago or so, it was all fine before that - just a regression. It will be fixed before release, I am sure.

Welcome to the development cycle.

---

### Post by LADmaticCA on 2012-02-25
Thanks for the confirmation guys.

---

### Post by effenberg0x0 on 2012-02-25
> **skewty said:**
> You are correct in that it has to do with your graphics card.  It has to do with the nvidia graphics card driver.  There is nothing you can do about it.  Canonical and NVidia need to work together much closer to prevent things like this.  I doubt you will see a flicker free startup without garbage on the screen for another 6 or 7 years.  Welcome to GNU/Linux.

Ladmaticca, please disregard the information above as it is absurd. All you need to do is reinstall your NVidia kernel module and you'll get rid of this problem. Start grub recovery mode and select a network-enabled prompt. Accept the option to remount root as read-write. 

If you are using NVidia's proprietary binary installer (and you have it in your Home downloads folder), just run it again selecting "yes" to all questions. Or run it with the -K (rebuild kernel module) command-line argument and reboot. 

Regards,
Effenberg

---

### Post by ventrical on 2012-02-25
> **effenberg0x0 said:**
> Ladmaticca, please disregard the information above as it is absurd. All you need to do is reinstall your NVidia kernel module and you'll get rid of this problem. Start grub recovery mode and select a network-enabled prompt. Accept the option to remount root as read-write. 

Regards,
Effenberg

 So that would then be:

sudo apt-get purge nvidia*

then

sudo apt-get install nvidia-current

??
from root?

---

### Post by ventrical on 2012-02-25
The cat came back the very next day!

:)

---

### Post by effenberg0x0 on 2012-02-25
> **ventrical said:**
> So that would then be:

sudo apt-get purge nvidia*

then

sudo apt-get install nvidia-current

??
from root?

I would think so, as I do not use NVidia from repos. Using the installer for driver version 295.20 downloaded from NVidia website, the procedure is:
- Start in grub recovery mode
- Select a network-enabled console and let it remount / read-write
- If you don't have the installer already downloaded, then just get it:
32-Bit
```
cd && cd Downloads
wget http://us.download.nvidia.com/XFree86/Linux-x86/295.20/NVIDIA-Linux-x86-295.20.run
```64-Bit
```

cd && cd Downloads
wget http://us.download.nvidia.com/XFree86/Linux-x86_64/295.20/NVIDIA-Linux-x86_64-295.20.run
```- Run it:
```
cd && cd Downloads
sudo chmod +x NV*run
sudo ./NVIdia*295.20.run
```- And reboot
```
sudo reboot now

```Of course, when moving from nouveau or nvidia-current from repos to the one provided by NVidia installer, nouveau should be blacklisted (as the installer will build and load NVidia's own proprietary Kernel Module) and purging previous nvidia* would be a good idea too.

For people that already use NVidia installer and kernel modules, all it takes is to rebuild and reload the Kernel module. Just locate the installer and run:
```
sudo ./NVidia*.run -K
sudo reboot now

```Basically any working tutorial on how to install or reinstall NVidia drivers and kernel module applies and will work. 

Regards,
Effenberg

---

### Post by ventrical on 2012-02-25
cd && cd Downloads

returns 'no such file or directory'

root@ubuntu:~# dir

 gives me

Desktop warty-final-ubuntu.png

??

---

### Post by grahammechanical on 2012-02-25
Ooh! I get something like that during the interval between LightDM accepting the password and the Desktop loading. The LightDM background image fails to stay on the screen until the Desktop background image takes over. They are the same image by the way.

I thought that I was the only one to have this because I was using Simple LightDM Manager to set a LightDM background image and at the same time have the desktop slide show.

Things were working fine until an update of LightDM a few days ago. I did not see it as a bug but an incompatibility with the way Simple LightDM Manger (SLM) makes the changes. I think that LightDM is now looking at different scripts.

I have tried manually editing the LightDM configuration files (changed by SLM) to point to the correct image files.

I have re-installed LightDM and Unity. I can find nothing in the scripts that is wrong.

I have resigned myself to having this problem until 12.04 is released as a distribution. Then I will do a fresh install in preparation of moving this 12.04 testing install into a 12.10 testing install.

Regards.

P.S. In my case I think that this is definitely a case of the background image failing to be kept on screen during the switch over between display managers after log in.

---

### Post by ventrical on 2012-02-25
Got this far but there is no way that file wants to run:



cd && cd Downloads 
sudo ./NVIdia*295.20.run

---

### Post by sgage on 2012-02-25
> **ventrical said:**
> Got this far but there is no way that file wants to run:



cd && cd Downloads 
sudo ./NVIdia*295.20.run

You may have to chmod it to make it executable?

---

### Post by ventrical on 2012-02-25
> **sgage said:**
> You may have to chmod it to make it executable?

Ya know ... I have been working with computers since 1962 at the age of seven years old working in my fathers TV /electrical repair shop cleaning the contacts points on IBM cash Registers machines and when I see the code "chmod", my mind experiences a complete and absolute brain fart.. really .. it's not anyones fault here.. it's just that  I no capice'.. no comprende' ...

so.. you would be so kind as to detail what then I must do to "chmod" to get this  program to run?

thanks in advance..


note... I think that   I have some sort of block ...  like , for example, when I see the code "chmod" I think that it is some sort of exotic 'clam chowder' and at that point I just can't seem to wrap my head around it.


 I'm working on it ... I'm gettin there :)

---

### Post by skewty on 2012-02-25
> **sgage said:**
> This is alpha software. The graphical glitches at log on just started a couple of weeks ago or so, it was all fine before that - just a regression. It will be fixed before release, I am sure.

Welcome to the development cycle.

How would you explain similar graphical glitches in LTS releases?  I have seen this same issue over and over in releases since I first started with Ubuntu in 2007.

---

### Post by sgage on 2012-02-25
> **ventrical said:**
> Ya know ... I have been working with computers since 1962 at the age of seven years old working in my fathers TV /electrical repair shop cleaning the contacts points on IBM cash Registers machines and when I see the code "chmod", my mind experiences a complete and absolute brain fart.. really .. it's not anyones fault here.. it's just that  I no capice'.. no comprende' ...

so.. you would be so kind as to detail what then I must do to "chmod" to get this  program to run?

thanks in advance..


note... I think that   I have some sort of block ...  like , for example, when I see the code "chmod" I think that it is some sort of exotic 'clam chowder' and at that point I just can't seem to wrap my head around it.


 I'm working on it ... I'm gettin there :)

As I move on into my later 50's, believe me when I say that the brain farts (I prefer the term "brain cramps") come more and more frequently. :KS

Simply do this:

chmod a+x whatever-the-filename-is

and that will make it executable.

Or just do:

bash whatever-the-filename-is

and that will probably launch it as well - I believe the nvidia installer is a script.

---

### Post by ventrical on 2012-02-25
> **sgage said:**
> As I move on into my later 50's, believe me when I say that the brain farts (I prefer the term "brain cramps") come more and more frequently. :KS

Simply do this:

chmod a+x whatever-the-filename-is

and that will make it executable.

Or just do:

bash whatever-the-filename-is

and that will probably launch it as well - I believe the nvidia installer is a script.


 Hey !! Thanks .. :bash: worked just great !  Installed it , prompted me for input .. etc.. the whole shabang!!  and then ... rebooted .. and .. there it was ... a newly progressive distortion at log-on and it defaults now to Unity 2D:(

---

### Post by sgage on 2012-02-25
> **skewty said:**
> How would you explain similar graphical glitches in LTS releases?  I have seen this same issue over and over in releases since I first started with Ubuntu in 2007.

No you haven't. This is a simple regression in the LightDM package. For sure there have been various issues with the proprietary nvidia drivers over the years, but they've been different issues, and they get addressed.

To pass it off with "welcome to GNU/Linux" is not helpful. For example, Fedora does not have a problem, since it's using GDM. Ubuntu is member of the class 'GNU/Linux' - it is not GNU/Linux.

Just stick with Windows, and you won't have any problems ):P

---

### Post by ventrical on 2012-02-25
Ok .. I got the Unity 3D back, all bells and whistles working.. so far...

 what do ya think of this  doozer ??
..

---

### Post by ventrical on 2012-02-25
> **sgage said:**
> As I move on into my later 50's, believe me when I say that the brain farts (I prefer the term "brain cramps") come more and more frequently. :KS

.

Thanks..    I got to do some more read ups ... :)

---

### Post by effenberg0x0 on 2012-02-25
Just to add some explanation to the thread in case someone lands here on a search:

I'm seeing this exact same VGA patterns repeatedly during this cycle, generally after a Kernel update. Users at some of my country's Ubuntu/IT forums reported it too and the screenshots are identical. The working solution for 100% of such cases, including my machines, has been to reinstall the NVidia kernel module. Now, just copying here what I've been repeating elsewhere - that assumes that the user:

- Runs a standard system, i.e. a PC, with 1 VGA card brand only. I'm not sure how it would go on a hybrid system;
- Has a working NVidia VGA card, which worked fine with NVidia drivers previously;
- Has a NVidia card that uses current drivers, not the 173-dependent older models;
- Has the ability to download and install working drivers;
- Has a working set of NVidia driver files, if he chooses to just update the kernel module; Or performs the entire NVidia install procedure if unsure;
- Follows the procedures informed on-screen by the installer;
- Makes sure he is not using another VGA driver, or is loading the nouveau kernel module;
- Has a working Ubuntu install. If anything else is damaged, reinstalling VGA drivers won't help.

If such conditions are met, any working tutorial on how to install or reinstall NVidia drivers properly works. If such conditions can't be met by the user, running PP is a waste of time. Oneiric is stable enough. 

Regards,
Effenberg

---

### Post by ventrical on 2012-02-25
> **effenberg0x0 said:**
> Just to add some explanation to the thread in case someone lands here on a search:

I'm seeing this exact same VGA patterns repeatedly during this cycle, generally after a Kernel update. Users at some of my country's Ubuntu/IT forums reported it too and the screenshots are identical. The working solution for 100% of such cases, including my machines, has been to reinstall the NVidia kernel module. Now, just copying here what I've been repeating elsewhere - that assumes that the user:

- Runs a standard system, i.e. a PC, with 1 VGA card brand only. I'm not sure how it would go on a hybrid system;
- Has a working NVidia VGA card, which worked fine with NVidia drivers previously;
- Has a NVidia card that uses current drivers, not the 173-dependent older models;
- Has the ability to download and install working drivers;
- Has a working set of NVidia driver files, if he chooses to just update the kernel module; Or performs the entire NVidia install procedure if unsure;
- Follows the procedures informed on-screen by the installer;
- Makes sure he is not using another VGA driver, or is loading the nouveau kernel module;
- Has a working Ubuntu install. If anything else is damaged, reinstalling VGA drivers won't help.

If such conditions are met, any working tutorial on how to install or reinstall NVidia drivers properly works. If such conditions can't be met by the user, running PP is a waste of time. Oneiric is stable enough. 

Regards,
Effenberg

 All conditions met.  It just doesn't work, at least in this case.  It was working fine (no warty) before the .17 kernel upgrade so are all of  our PCs' hardware blacklisted now ? because if so then thats a lot of PCs  that are not in compliance. 

  I thought you ran mostly VMs.

---

### Post by kevin2849 on 2012-02-25
I have the same thing on one of my laptops but it still makes it to the desktop and all is good. I figure to leave it alone until Precise is finalized. I may re-install when we reach Beta status anyway, just to see how it goes.

---

### Post by ventrical on 2012-02-25
> **kevin2849 said:**
> I have the same thing on one of my laptops but it still makes it to the desktop and all is good. I figure to leave it alone until Precise is finalized. I may re-install when we reach Beta status anyway, just to see how it goes.


  Same here .. everything is great with the exception of the badly distorted psudeo-relics after log-on for just a brief moment. It appears that  after log-off that a conglamorate of video screens is being buffered , cached and not refreshed after log-off and being saved to a file (somehwere) waiting for the next bootup.! In somes ways it almost behaves like malware with the exception that it is not really doing any damage .. and actually the kalidascopic effects can be sometimes, refreshing :)

hahaha

ehe

---

### Post by ventrical on 2012-02-25
I did get this from one of the unity-greeter logs:

```
[+1.06s] DEBUG: Guessing max time width: 62
[+1.09s] DEBUG: unity-greeter.vala:673: Starting main loop
[+1.09s] DEBUG: Read 8 bytes from daemon
[+1.09s] DEBUG: Read 34 bytes from daemon
[+1.09s] DEBUG: Prompt user with 1 message(s)
[+1.23s] DEBUG: user-list.vala:158: Making background /usr/share/backgrounds/warty-final-ubuntu.png at 1024x768
[+1.23s] DEBUG: user-list.vala:1216: Rendered first frame
[+1.27s] DEBUG: Num devices: '0'

Error getting primary device[+1.34s] WARNING: Getting layout failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.dbusmenu' on object at path /com/canonical/indicator/users/menu
[+1.37s] DEBUG: user-list.vala:1204: Drew 2 frames in 1.0 seconds (1.906625 fps)
[+1.79s] DEBUG: notify visible signal received
[+1.79s] CRITICAL: ido_calendar_menu_item_set_date: assertion `IDO_IS_CALENDAR_MENU_ITEM(menuitem)' failed
[+1.80s] DEBUG: New calendar item
[+1.98s] DEBUG: user-list.vala:174: Render of background /usr/share/backgrounds/warty-final-ubuntu.png at 1024x768 complete
[+1.99s] DEBUG: user-list.vala:1179: Start background animation
[+2.01s] DEBUG: user-list.vala:910: Stop background animation
[+2.12s] DEBUG: user-list.vala:1204
```

---

### Post by VinDSL on 2012-02-25
You know...

There used to be a command, to test the unity-greeter, from cli, e.g. from your desktop.

Anybody know if that command still exists?!?!?!?

Or, do we have to take a snappie, before logging in, with a digital camera, et cetera?

---

### Post by ventrical on 2012-02-25
> **VinDSL said:**
> You know...

There used to be a command, to test the unity-greeter, from cli, e.g. from your desktop.

Anybody know if that command still exists?!?!?!?

Or, do we have to take a snappie, before logging in, with a digital camera, et cetera?

Vin,

Do your know where the unity-greeter conf file is . I was looking at the log files and noticed some pretty strange errors there.  I'm just trying a few things here .. mabey bust my systems a little more :)

---

### Post by jpeddicord on 2012-02-25
> **VinDSL said:**
> You know...

There used to be a command, to test the unity-greeter, from cli, e.g. from your desktop.

Anybody know if that command still exists?!?!?!?

Or, do we have to take a snappie, before logging in, with a digital camera, et cetera?

I'm not even going to tell you what it is, because I ran it myself not too long ago, and it corrupts your dconf database. Here's the bug on it:

[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/874616](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/874616)

Basically, the "solution" is to not do what the reporter described. :P

---

### Post by VinDSL on 2012-02-25
> **ventrical said:**
> Do your know where the unity-greeter conf file is [...]
No, sorry!

IMO, the greeter is a mind-wretching, insufferable app, to be avoided, if at all possible.  LoL!  :D

I'm just wondering if you can still conjure it up for screenshots...

---

### Post by VinDSL on 2012-02-25
> **jpeddicord said:**
> I'm not even going to tell you what it is, because I ran it myself not too long ago, and it corrupts your dconf database. Here's the bug on it:

[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/874616](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/874616)

Basically, the "solution" is to not do what the reporter described. :P
Heh!  Thanks, for the heads-up!

I'll forget that idea...  ;)

---

### Post by exploder on 2012-02-25
I get fairly minor artifacts on my laptop using the open source ATI graphics drivers. My system with NVidea GT220 graphics is just a hideous mess with the open source or proprietary drivers...

---

### Post by ventrical on 2012-02-25
> **VinDSL said:**
> No, sorry!

IMO, the greeter is a mind-wretching, insufferable app, to be avoided, if at all possible.  LoL!  :D

I'm just wondering if you can still conjure it up for screenshots...

  Sure can !.. Take a look at this one ! It has relics of your avatar all over the place. It seems to only happen when there is activity after log on. I tried just a null log-on/log-off and the psudeo relics did not appear , but , upon loading up firefox, reading your message : here it is !!

 So it appears that it is saving  the most recent screen activity to a file and then redirecting the greeter to the cached relics. I do not see where it is a Nvidia problem.. there is somthing more complex at work here.

---

### Post by ventrical on 2012-02-25
> **exploder said:**
> I get fairly minor artifacts on my laptop using the open source ATI graphics drivers. My system with NVidea GT220 graphics is just a hideous mess with the open source or proprietary drivers...


Yep .. here's some more..

---

### Post by exploder on 2012-02-25
> 
Yep .. here's some more..

That's pretty bad...

---

### Post by effenberg0x0 on 2012-02-25
> **ventrical said:**
> All conditions met.  It just doesn't work, at least in this case.  It was working fine (no warty) before the .17 kernel upgrade so are all of  our PCs' hardware blacklisted now ? because if so then thats a lot of PCs  that are not in compliance. 

  I thought you ran mostly VMs.

Nope, although I grew to prefer working with them, VMs are mostly for Job #1. Job #2 (my business) is all about real machines.

2 questions: 
1) How are you guys on non-stock software, I mean, stuff like xorg-edgers and Ricotz PPAs, for example? 
2) Isn't there anything that can help in the logs? I know it will be impossible to read logs in such a messy display, but do it in console via recovery. There has to be some lead. 

**EDIT:** Oh, forgot to add a stupid question: Is it OK when booting to a previous kernel in Grub?
**EDIT2:** If possible, see what you get for these commands:
```

lsmod | grep -i nouveau
lsmod | grep -i nvidia
nvidia-xconfig --version
sudo modinfo nvidia
X -version
unity --version
lightdm --version
cat /etc/X11/xorg.conf

```If you're doing it from the console with no GUI, it would be hard to type all commands results. It's easier to pipe their outputs to a file in USB, network drive, etc, which can be accessed in another PC or when booting with a Live CD/USB or another working OS. Then gedit the file to paste results here. To pipe their output to a single file you can use:
```

lsmod | grep -i nouveau | tee -a ~/output.log
lsmod | grep -i nvidia | tee -a ~/output.log
nvidia-xconfig --version | tee -a ~/output.log
sudo modinfo nvidia | tee -a ~/output.log
 X -version | tee -a ~/output.log
unity --version | tee -a ~/output.log
lightdm --version | tee -a ~/output.log
cat /etc/X11/xorg.conf | tee -a ~/output.log

```And then save /home/YOU/output.log somewhere you can access using a working OS to gedit it and paste contents here.

Regards,
Effenberg

---

### Post by ventrical on 2012-02-25
> **effenberg0x0 said:**
> Nope, although I grew to prefer working with them, VMs are mostly for Job #1. Job #2 (my business) is all about real machines.

2 questions: 
1) How are you guys on non-stock software, I mean, stuff like xorg-edgers and Ricotz PPAs, for example? 
2) Isn't there anything that can help in the logs? I know it will be impossible to read logs in such a messy display, but do it in console via recovery. There has to be some lead. 

**EDIT:** Oh, forgot to add a stupid question: Is it OK when booting to a previous kernel in Grub?
**EDIT2:** If possible, see what you get for these commands:
```

lsmod | grep -i nouveau
lsmod | grep -i nvidia
nvidia-xconfig --version
sudo modinfo nvidia
X -version
unity --version
lightdm --version
cat /etc/X11/xorg.conf

```If you're doing it from the console with no GUI, it would be hard to type all commands results. It's easier to pipe their outputs to a file in USB, network drive, etc, which can be accessed in another PC or when booting with a Live CD/USB or another working OS. Then gedit the file to paste results here. To pipe their output to a single file you can use:
```

lsmod | grep -i nouveau | tee -a ~/output.log
lsmod | grep -i nvidia | tee -a ~/output.log
nvidia-xconfig --version | tee -a ~/output.log
sudo modinfo nvidia | tee -a ~/output.log
 X -version | tee -a ~/output.log
unity --version | tee -a ~/output.log
lightdm --version | tee -a ~/output.log
cat /etc/X11/xorg.conf | tee -a ~/output.log

```And then save /home/YOU/output.log somewhere you can access using a working OS to gedit it and paste contents here.

Regards,
Effenberg

Hey,



  I just did a virgin install and I still have  the distorted unity-greeter screen after logon.

---

### Post by xajeiw9I on 2012-02-25
I have this problem with open ATI (now AMD) drivers too. I've got an E-350 with a Radeon 6310. This chipset is quite troublesome in most distros, the worst case is with Debian testing branch or SID, the screen gets corrupted before logging in, making it unusable. Generally it has just bad performance, artifacts and problems hibernating/suspending/wasting too much power.

It works ok with Ubuntu 12.04, but was kind of bad with 11.04 or 11.10 because of bad performance and random lockups.

But the artifacts after logging in annoy me, it just shows how bad the driver support is and make me feel the system is totally unreliable.

Since Debian has the worst case, it might be some important bug with driver compatibility, and they probably have an older version than Ubuntu that was in worse shape.

The Catalyst driver is still buggy too, it has trouble playing videos (crashes) or suspending, so it's hard for me to recommend using AMD/ATI at all. I am not sure if Intel is a safer bet for low powered machines like the E-350, their video chipset is made by PowerVR for the Atoms.

I am going to install 12.04 final on a Sandy Bridge i5 2410M, I hope they include a new Intel driver that doesn't show artifacts because I want it to be my main work machine.

---

### Post by cariboo on 2012-02-25
> **jpeddicord said:**
> I'm not even going to tell you what it is, because I ran it myself not too long ago, and it corrupts your dconf database. Here's the bug on it:

[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/874616](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/874616)

Basically, the "solution" is to not do what the reporter described. :P

I have the same Nvidia graphics card as ventrical, so I just had to try the lightdm test mode. See the screenshot. It looks like corrupting the dconf database may have improved font rendering, but theming is now broken. Restoring ~/.config from backup restored functionality

---

### Post by VinDSL on 2012-02-25
> **cariboo907 said:**
> Restoring ~/.config from backup restored functionality
Heh!  That's cheating!  :D

---

### Post by jpeddicord on 2012-02-25
> **cariboo907 said:**
> I have the same Nvidia graphics card as ventrical, so I just had to try the lightdm test mode. See the screenshot. It looks like corrupting the dconf database may have improved font rendering, but theming is now broken. Restoring ~/.config from backup restored functionality

> **VinDSL said:**
> Heh!  That's cheating!  :D

What VinDSL said. ;)

Apparently that bug was "fixed" in the sense that unity-greeter should refuse to run if it's in a user session. I'm not willing to test, however, and if you were able to do that just now it probably wasn't actually fixed.

---

### Post by LADmaticCA on 2012-02-25
Wow lots more replies. Interesting to see it's affecting ATi/AMD users too. I would like to make a bug report, but what should I log it under lightdm?

---

### Post by cariboo on 2012-02-26
I just used lightdm test mode using the following command:

[SIZE="2"][COLOR="Red"]Warning: the following command will corrupt the dconf database[/COLOR][/SIZE], make sure you have the database backed-up before trying this.

```
lightdm --test-mode
```

xephyr-server needs to be installed before the command will run

---

### Post by ventrical on 2012-02-26
> **xajeiw9I said:**
> I have this problem with open ATI (now AMD) drivers too. I've got an E-350 with a Radeon 6310. This chipset is quite troublesome in most distros, the worst case is with Debian testing branch or SID, the screen gets corrupted before logging in, making it unusable. Generally it has just bad performance, artifacts and problems hibernating/suspending/wasting too much power.

It works ok with Ubuntu 12.04, but was kind of bad with 11.04 or 11.10 because of bad performance and random lockups.

But the artifacts after logging in annoy me, it just shows how bad the driver support is and make me feel the system is totally unreliable.

Since Debian has the worst case, it might be some important bug with driver compatibility, and they probably have an older version than Ubuntu that was in worse shape.

The Catalyst driver is still buggy too, it has trouble playing videos (crashes) or suspending, so it's hard for me to recommend using AMD/ATI at all. I am not sure if Intel is a safer bet for low powered machines like the E-350, their video chipset is made by PowerVR for the Atoms.

I am going to install 12.04 final on a Sandy Bridge i5 2410M, I hope they include a new Intel driver that doesn't show artifacts because I want it to be my main work machine.

 All my laptops with intel graphics drivers work great. I have the same problem with ATi64bit.

---

### Post by ventrical on 2012-02-26
@mods

  This thread  is similar to the 'unity-greeter' thread.  Should they be merged?

---

### Post by ventrical on 2012-02-26
I think I am on to something.  I just did a fresh install and got the same problem (distorted screen after logon). I have a theory about the drivers.. but first I need to know how to tell what drivers I have installed. Is there a sudo command to identify which video drivers are running?

---

### Post by jpeddicord on 2012-02-26
> **cariboo907 said:**
> I just used lightdm test mode using the following command:

[SIZE="2"][COLOR="Red"]Warning: the following command will corrupt the dconf database[/COLOR][/SIZE], make sure you have the database backed-up before trying this.

```
lightdm --test-mode
```

xephyr-server needs to be installed before the command will run

Ah... the one I was thinking of was just running `unity-greeter` ([COLOR="Red"]**don't do this**[/COLOR]) directly.

---

### Post by confused57 on 2012-02-26
> **mc4man said:**
> The only reason I was looking at that image file (was going to alter it slightly) is because on a multiboot sometimes I don't get any 'corruption' on the newest 12.04 login, I get the greeter image from my 11.10 install which seems quite wierd.

Also at times when I get a mosaic, the snippets are from things I've viewed during the day, again it's weird that they are being 'saved' somewhere? And other user accounts can get snippets from what I was looking at

I'm seeing the same kind of artifacts, good to see this bug is being discussed.  Lucid is my primary operating system, but when I reboot into Precise on another partition, there are artifacts of websites that have been viewed in Firefox on 10.04(after entering login password & pressing Enter).  I even saw that my wife had been viewing handbags on amazon.com, she hadn't used the computer for hours.  I see these types of artifacts after a reboot from Lucid to Precise.

I tried shutting the computer down for several minutes, then booting directly into Precise.  The only artifacts were large gray light & dark checkerboard squares, no carryover from Lucid.  It appears that somehow, Precise is accessing information from stored memory(system or vram?) during login. I'm assuming that the memory lost all of what was stored after shutting down the computer for a while.

I know that intramfs is loaded into memory during bootup, but I would think
Precise's boot process would be past needing to access intramfs at the
login stage.  I haven't really seen any explanations of this problem that have definitively pinned down the cause.

Edited: Changed all references to Precise(instead of Oneiric), I personally use 12.04, 10.04, etc when referring to different versions.

---

### Post by ventrical on 2012-02-27
> **confused57 said:**
> I'm seeing the same kind of artifacts, good to see this bug is being discussed.  Lucid is my primary operating system, but when I reboot into Oneiric on another partition, there are artifacts of websites that have been viewed in Firefox on 10.04(after entering login password & pressing Enter).  I even saw that my wife had been viewing handbags on amazon.com, she hadn't used the computer for hours.  I see these types of artifacts after a reboot from Lucid to Oneiric.

I tried shutting the computer down for several minutes, then booting directly into Oneiric.  The only artifacts were large gray light & dark checkerboard squares, no carryover from Lucid.  It appears that somehow, Oneiric is accessing information from stored memory(system or vram?) during login. I'm assuming that the memory lost all of what was stored after shutting down the computer for a while.

I know that intramfs is loaded into memory during bootup, but I would think
Oneiric's boot process would be past needing to access intramfs at the
login stage.  I haven't really seen any explanations of this problem that have definitively pinned down the cause.

Hey .. thanks for your contribution but this is Precise beta testing .. but I appreciate you bringing that experience up about Oneiric because it may lead somewhere to get this bug fixed. I did a fresh install (of Precise alpha) on the same machine and it appears to have cleared that problem up.
  But I am assuming that there is a bigger problem than just with nvidia drivers... your suggestion sounds good .. there are relics being deferred at log-off or shutdown and they are being saved in a cache file somewhere and are being loaded up at reboot.

  Some hardware, both  motherboards and video adpater cards, have the feature of keeping stored static memory in their framebuffers, meaning that these buffers are not being cleared after log-off of shut-down. One way to validate this theory (for experienced beta testers only) is to shut down your machine, disconnect the power, pull out the nvidia adapter card, re-install the adapter card and then re-boot. If my theory is correct then there would be no relic distortion at boot up. You can also try removing our DDR memory sticks. Simply unplugging your machine will not suffice as some capacitors will hold a static  memory for months on end. Pulling the card will free anything that may be locked-up in a static (or dynamic) state on the adapter card. In fact I just may do this myself. (since I have the GEforce 210).

---

### Post by ventrical on 2012-02-27
Ok.. to followup.. I removed and re-installed my Nvidia card but to no avail... the distortion is still there after log-on.

---

### Post by confused57 on 2012-02-27
> **ventrical said:**
> Hey .. thanks for your contribution but this is Precise beta testing .. but I appreciate you bringing that experience up about Oneiric because it may lead somewhere to get this bug fixed. I did a fresh install (of Precise alpha) on the same machine and it appears to have cleared that problem up.
  But I am assuming that there is a bigger problem than just with nvidia drivers... your suggestion sounds good .. there are relics being deferred at log-off or shutdown and they are being saved in a cache file somewhere and are being loaded up at reboot.

  Some hardware, both  motherboards and video adpater cards, have the feature of keeping stored static memory in their framebuffers, meaning that these buffers are not being cleared after log-off of shut-down. One way to validate this theory (for experienced beta testers only) is to shut down your machine, disconnect the power, pull out the nvidia adapter card, re-install the adapter card and then re-boot. If my theory is correct then there would be no relic distortion at boot up. You can also try removing our DDR memory sticks. Simply unplugging your machine will not suffice as some capacitors will hold a static  memory for months on end. Pulling the card will free anything that may be locked-up in a static (or dynamic) state on the adapter card. In fact I just may do this myself. (since I have the GEforce 210).
Hello ventrical, thanks for the info & followup.  My primary computer has a 8600GT and I've tried nvidia-current(& updates) and nouveau, all have shown the same behaviour.  Another computer with a 9800GT shows the exact same kind of distortions at login.  The 8600GT pc is a gigabyte intel mobo(DDR2) and the 9800GT is an ECS amd(DDR3 memory), the only thing in common is a discrete Nvidia graphics card.  I'm wondering if anyone using nvidia(or intel, ati) onboard graphics or ATI discrete graphics card are having the same problem.  This may help pinpoint if the graphics card ram is an issue.
Both of my computers show the large gray checkerboard squares at a cold boot, but show stored artifacts at a warm reboot.

---

### Post by ventrical on 2012-02-27
> **confused57 said:**
> Hello ventrical, thanks for the info & followup.  My primary computer has a 8600GT and I've tried nvidia-current(& updates) and nouveau, all have shown the same behaviour.  Another computer with a 9800GT shows the exact same kind of distortions at login.  The 8600GT pc is a gigabyte intel mobo(DDR2) and the 9800GT is an ECS amd(DDR3 memory), the only thing in common is a discrete Nvidia graphics card.  I'm wondering if anyone using nvidia(or intel, ati) onboard graphics or ATI discrete graphics card are having the same problem.  This may help pinpoint if the graphics card ram is an issue.
Both of my computers show the large gray checkerboard squares at a cold boot, but show stored artifacts at a warm reboot.


All my Intel graphics PCs with Precise Installs are NOT showing the ill rendered and badly programmed cache residues which are currently plaguing a lot of NVidia and ATi graphical adapter cards. I tried the info that was posted by effenberg but to no avail.  Even , now, I have to belay a most recent previous message where I declared that a fresh install remedied the situation, which it did not.  I am working on a rolling theory here, in declaring that something wicked was seconded into the repositories and perhaps has to do with  some config files  that concern the unity-greeter. The error logs on all of this are interesting in pointing to same.

  Another theory I have is that Canonical is attempting to obsolete some older motherboard hardware platforms that may be utilizing newer nVidia cards, ATi etc. Erros on install  (Dell Optiplex GX270) will render a <verbose_code 'tainted ' Dell Corporation, Optiplex GX270> ad nauseum.  Of course then I am only then left  with the option of making the assumption that the 'taint' is a blacklist or fake false flag (because I just did a reinstall of a tainted flagged system and switched HDDs to prove that this was not a hybrid anomoly.)

  And then furthermore, with the Unity 3D not performing with <00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)> from a Precise install or Oneiric install and yet able to  render Compiz 3D Graphics with a Precise Kubuntu install from another system's HDD leaves me absolutely puzzled as to how the developers are programming their code to determine graphical ID bytes, flags and indentifiers  and assigning the proper drivers thereof.

 These anomolies are expected with these early releases of alpha but one would think that with such a profound obstruction with the hand-off from the Unity greeter into the  Desktop that the developers responsible for this would lean in harder to rectify this matter so that more serious beta testing can then be ensued concerning a  plethora of bugs. This little 'kalidascopic psychedelic trip" after the hand-off is not funny at all. I do not think it is "rocking" anyone's world.

---

### Post by snkiz on 2012-02-27
Is anyone else getting anything like this? [https://bugs.launchpad.net/bugs/938933]("https://bugs.launchpad.net/bugs/938933") Its as though the alignment is off, but hitting reset on the monitor doesn't fix it. fixing it manually screws up the alignment for the session. The strangest part, logging into and out of KDE temporarily fixes it. (until the next time you use a gnome based session.)

---

### Post by confused57 on 2012-02-27
> **ventrical said:**
> All my Intel graphics PCs with Precise Installs are NOT showing the ill rendered and badly programmed cache residues which are currently plaguing a lot of NVidia and ATi graphical adapter cards. I tried the info that was posted by effenberg but to no avail.  Even , now, I have to belay a most recent previous message where I declared that a fresh install remedied the situation, which it did not.  I am working on a rolling theory here, in declaring that something wicked was seconded into the repositories and perhaps has to do with  some config files  that concern the unity-greeter. The error logs on all of this are interesting in pointing to same.

  Another theory I have is that Canonical is attempting to obsolete some older motherboard hardware platforms that may be utilizing newer nVidia cards, ATi etc. Erros on install  (Dell Optiplex GX270) will render a <verbose_code 'tainted ' Dell Corporation, Optiplex GX270> ad nauseum.  Of course then I am only then left  with the option of making the assumption that the 'taint' is a blacklist or fake false flag (because I just did a reinstall of a tainted flagged system and switched HDDs to prove that this was not a hybrid anomoly.)

  And then furthermore, with the Unity 3D not performing with <00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)> from a Precise install or Oneiric install and yet able to  render Compiz 3D Graphics with a Precise Kubuntu install from another system's HDD leaves me absolutely puzzled as to how the developers are programming their code to determine graphical ID bytes, flags and indentifiers  and assigning the proper drivers thereof.

 These anomolies are expected with these early releases of alpha but one would think that with such a profound obstruction with the hand-off from the Unity greeter into the  Desktop that the developers responsible for this would lean in harder to rectify this matter so that more serious beta testing can then be ensued concerning a  plethora of bugs. This little 'kalidascopic psychedelic trip" after the hand-off is not funny at all. I do not think it is "rocking" anyone's world.

Thanks for your detailed theories & observations, my "hats-off" to everyone who is actively involved in testing.  I'm not really a tester, but like most users who just want everything to work to accomplish my everyday computing and testing is vital to a refined finished product.  I just hope the screen corruption is rectified before the final release of 12.04 and I believe that it will be.  I'll be following this thread very closely, as well as, other resources for any progress and contribute when & if I can.
It is interesting tho' to see what websites my wife has been visiting in 10.04, when I log in to 12.04 Beta.

I edited my original post to reflect Precise, not Oneiric...I refer to Ubuntu versions as 10.04, 12.04, etc, easier for me to keep track of than their names.

---

### Post by ventrical on 2012-02-27
I just did yet another fresh (Precise alpha 2USB) install on another system with an older Nvidia card: <01:00.0 VGA compatible controller: NVIDIA Corporation NV11 [GeForce2 MX/MX 400] (rev b2)>  and NOW the card will not be detected by Additional Hardware jockey (did fine before alpha 2) and I still have the distorted , kalidescopic, psudeo-relics on the screen after logon.  So, my assumption is that in (and from the repositories) somthing wicked has this way come !

---

### Post by ventrical on 2012-02-27
> **snkiz said:**
> Is anyone else getting anything like this? [https://bugs.launchpad.net/bugs/938933](https://bugs.launchpad.net/bugs/938933) Its as though the alignment is off, but hitting reset on the monitor doesn't fix it. fixing it manually screws up the alignment for the session. The strangest part, logging into and out of KDE temporarily fixes it. (until the next time you use a gnome based session.)

 No, I haven't seen this anomoly on any of my screens but it may be  an indicator that may lead to a work around.

---

### Post by ventrical on 2012-02-27
Here is an example of an error log from /var/log/lightdm:

```

[+0.00s] DEBUG: unity-greeter.vala:629: Starting unity-greeter 0.2.0 UID=104 LANG=en_CA.UTF-8
[+0.00s] DEBUG: unity-greeter.vala:632: Setting cursor
[+0.00s] DEBUG: unity-greeter.vala:636: Creating background surface
[+0.01s] DEBUG: unity-greeter.vala:639: Loading command line options
[+0.01s] DEBUG: unity-greeter.vala:666: Loading configuration from /etc/lightdm/unity-greeter.conf
[+0.01s] DEBUG: unity-greeter.vala:679: Setting GTK+ settings
[+0.09s] DEBUG: unity-greeter.vala:703: Creating Unity Greeter
[+0.09s] DEBUG: Connecting to display manager...
[+0.09s] DEBUG: Wrote 17 bytes to daemon
[+0.10s] DEBUG: Read 8 bytes from daemon
[+0.10s] DEBUG: Read 90 bytes from daemon
[+0.10s] DEBUG: Connected version=1.1.1 default-session=ubuntu hide-users=false has-guest-account=true
[+0.20s] DEBUG: unity-greeter.vala:203: Monitor is 1440x900 pixels at 0,0
[+0.32s] DEBUG: menubar.vala:291: LANG=en_CA.UTF-8 LANGUAGE=en_CA:en
[+0.34s] CRITICAL: g_error_free: assertion `error != NULL' failed
[+0.34s] DEBUG: get entries
[+0.34s] DEBUG: menubar.vala:444: Adding indicator object 0x9f69060 at position 0
[+0.35s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.35s] DEBUG: Checking against 2 possible times
[+0.37s] DEBUG: Guessing max time width: 62
[+0.37s] DEBUG: get entries
[+0.37s] DEBUG: menubar.vala:444: Adding indicator object 0x9e39364 at position 1
[+0.37s] WARNING: IndicatorObject class does not have an accessible description.
[+0.37s] DEBUG: get entries
[+0.37s] DEBUG: get entries
[+0.37s] DEBUG: menubar.vala:444: Adding indicator object 0x9ea2204 at position 2
[+0.38s] WARNING: IndicatorObject class does not have an accessible description.
[+0.39s] DEBUG: get entries
[+0.39s] DEBUG: get entries
[+0.39s] DEBUG: get entries
[+0.39s] DEBUG: menubar.vala:444: Adding indicator object 0x9fb90bc at position 3
[+0.39s] DEBUG: menubar.vala:305: LANG=en_CA.UTF-8 LANGUAGE=en_CA:en
[+0.41s] DEBUG: Loaded session /usr/share/xsessions/gnome-fallback.desktop (GNOME Classic (No effects), This session logs you into GNOME with the traditional panel without any graphical effect.)
[+0.41s] DEBUG: Loaded session /usr/share/xsessions/Fvwm.desktop (Fvwm, Fvwm)
[+0.41s] DEBUG: Loaded session /usr/share/xsessions/fvwm-crystal.desktop (FVWM-Crystal, Umm... Nice desktop. Transparent, and all...)
[+0.41s] DEBUG: Ignoring session /usr/share/xsessions/gnome.desktop
[+0.41s] DEBUG: Loaded session /usr/share/xsessions/cairo-dock-fallback.desktop (Cairo-Dock (with Gnome and without effect), This session logs you into GNOME with Cairo-Dock and without any graphical effect.)
[+0.41s] DEBUG: Loaded session /usr/share/xsessions/gnome-classic.desktop (GNOME Classic, This session logs you into GNOME with the traditional panel)
[+0.41s] DEBUG: Loaded session /usr/share/xsessions/ubuntu-2d.desktop (Ubuntu 2D, This session logs you into Ubuntu 2D Mode)
[+0.41s] DEBUG: Loaded session /usr/share/xsessions/gnome-shell.desktop (GNOME, This session logs you into GNOME)
[+0.41s] DEBUG: Loaded session /usr/share/xsessions/ubuntu.desktop (Ubuntu, This session logs you into Ubuntu)
[+0.41s] DEBUG: Loaded session /usr/share/xsessions/cairo-dock.desktop (Cairo-Dock (with Gnome and effects), This session logs you into GNOME with Cairo-Dock and with graphical effects.)
[+0.41s] DEBUG: unity-greeter.vala:131: Adding session cairo-dock (Cairo-Dock (with Gnome and effects))
[+0.41s] DEBUG: unity-greeter.vala:131: Adding session cairo-dock-fallback (Cairo-Dock (with Gnome and without effect))
[+0.41s] DEBUG: unity-greeter.vala:131: Adding session fvwm-crystal (FVWM-Crystal)
[+0.41s] DEBUG: unity-greeter.vala:131: Adding session Fvwm (Fvwm)
[+0.41s] DEBUG: unity-greeter.vala:131: Adding session gnome-shell (GNOME)
[+0.41s] DEBUG: unity-greeter.vala:131: Adding session gnome-classic (GNOME Classic)
[+0.41s] DEBUG: unity-greeter.vala:131: Adding session gnome-fallback (GNOME Classic (No effects))
[+0.41s] DEBUG: unity-greeter.vala:131: Adding session ubuntu (Ubuntu)
[+0.41s] DEBUG: unity-greeter.vala:131: Adding session ubuntu-2d (Ubuntu 2D)
[+0.43s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.43s] DEBUG: Loading user /org/freedesktop/Accounts/User1001
[+0.44s] DEBUG: Loading user /org/freedesktop/Accounts/User1003
[+0.46s] DEBUG: Loading user /org/freedesktop/Accounts/User1004
[+0.47s] DEBUG: Loading user /org/freedesktop/Accounts/User1002
[+0.49s] DEBUG: Loading user /org/freedesktop/Accounts/User1000
[+0.52s] DEBUG: Loading sessions from org.freedesktop.DisplayManager
[+0.52s] DEBUG: Loaded session /org/freedesktop/DisplayManager/Session4 (dale1)
[+0.52s] DEBUG: unity-greeter.vala:211: Adding/updating user camel (camel)
[+0.52s] CRITICAL: unity_greeter_get_layout_by_name: assertion `name != NULL' failed
[+0.52s] DEBUG: Setting keyboard layout to us
[+0.58s] DEBUG: unity-greeter.vala:211: Adding/updating user camel1 (camel1)
[+0.58s] CRITICAL: unity_greeter_get_layout_by_name: assertion `name != NULL' failed
[+0.58s] DEBUG: unity-greeter.vala:211: Adding/updating user dale (dale)
[+0.58s] CRITICAL: unity_greeter_get_layout_by_name: assertion `name != NULL' failed
[+0.58s] DEBUG: unity-greeter.vala:211: Adding/updating user dale1 (dale1)
[+0.58s] CRITICAL: unity_greeter_get_layout_by_name: assertion `name != NULL' failed
[+0.58s] DEBUG: unity-greeter.vala:211: Adding/updating user ventrical (ventrical)
[+0.58s] CRITICAL: unity_greeter_get_layout_by_name: assertion `name != NULL' failed
[+0.58s] DEBUG: unity-greeter.vala:170: Adding guest account entry
[+0.64s] DEBUG: Starting authentication for user camel1...
[+0.64s] DEBUG: Wrote 22 bytes to daemon
[+0.64s] DEBUG: unity-greeter.vala:706: Showing greeter
[+0.64s] DEBUG: unity-greeter.vala:230: Showing main window
[+0.64s] DEBUG: New style for time label
[+0.65s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.65s] DEBUG: Checking against 2 possible times
[+0.65s] DEBUG: Guessing max time width: 62
[+0.65s] DEBUG: New style for time label
[+0.65s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.65s] DEBUG: Checking against 2 possible times
[+0.65s] DEBUG: Guessing max time width: 62
[+0.66s] DEBUG: unity-greeter.vala:719: Starting main loop
[+0.66s] DEBUG: Read 8 bytes from daemon
[+0.66s] DEBUG: Read 36 bytes from daemon
[+0.66s] DEBUG: Prompt user with 1 message(s)
[+0.74s] DEBUG: background.vala:197: Regenerating backgrounds
[+0.74s] DEBUG: background.vala:55: Making background /usr/share/backgrounds/warty-final-ubuntu.png at 1440x900
[+0.83s] DEBUG: user-list.vala:655: Rendered first frame
Error getting devices: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `org.gnome.SettingsDaemon.Power' on object at path /org/gnome/SettingsDaemon/Power
[+0.98s] WARNING: Getting layout failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.dbusmenu' on object at path /com/canonical/indicator/users/menu
[+1.02s] DEBUG: notify visible signal received
[+1.02s] CRITICAL: ido_calendar_menu_item_set_date: assertion `IDO_IS_CALENDAR_MENU_ITEM(menuitem)' failed
[+1.05s] DEBUG: New calendar item
[+1.22s] DEBUG: background.vala:78: Render of background /usr/share/backgrounds/warty-final-ubuntu.png at 1440x900 complete
[+2.62s] DEBUG: indicator-sound: new_volume_slider_widget
[+2.63s] DEBUG: indicator-sound: new_voip_slider_widget
[+58.55s] WARNING: unity-greeter: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.

```

---

### Post by mc4man on 2012-02-27
> **confused57 said:**
> 
It is interesting tho' to see what websites my wife has been visiting in 10.04, when I log in to 12.04 Beta.

That's one of the more interesting or distrubing? things about this bug - I can get images not only from other users but other installs on a multi-boot

Just one simple ex. - 
sda1 - 11.10
sda5 - 12.04 A2
sda7 - 12.04 latest image, grub configured on

On 11.10 I went in & modified /usr/share/unity-greeter/logo.png in an obvious way
From 11.10 restarted into 12.04 A2, the hand-off uses the greeter image with modded logo.png from 11.10

When restarting into 12.04 - latest never know what going to show, have seen snippets from other users & other installs

---

### Post by TheNessus on 2012-02-27
> **mc4man said:**
> That's one of the more interesting or distrubing? things about this bug - I can get images not only from other users but other installs on a multi-boot

Just one simple ex. - 
sda1 - 11.10
sda5 - 12.04 A2
sda7 - 12.04 latest image, grub configured on

On 11.10 I went in & modified /usr/share/unity-greeter/logo.png in an obvious way
From 11.10 restarted into 12.04 A2, the hand-off uses the greeter image with modded logo.png from 11.04

When restarting into 12.04 - latest never know what going to show, have seen snippets from other users & other installs

Interesting. 
I believe Pangolin may be evolving into a sentient being, and will soon be intelligent enough not only to obtain snippers from other users, but to take over an entire computer. And then - the world.

---

### Post by VinDSL on 2012-02-27
> **TheNessus said:**
> Interesting. 
I believe Pangolin may be evolving into a sentient being, and will soon be intelligent enough not only to obtain snippers from other users, but to take over an entire computer. And then - the world.
Heh!  :D

That would be, "Colossus: The Forbin Project", not Precise Pangolin.

---

### Post by ventrical on 2012-02-28
Well.. here goes another experiment.

  I am running Ubuntu kernel 3.2.0-14 with version  0.2.0-0ubuntu6 of Unity Greeter and I do not have the distorted screen handoff as which we have  all been experiencing. I have 'locked" the Unity-greeter version in synaptic and am about to doupdates (this hdd hasn't been updated for a few weeks) so it has missed whatever came up the pipes  and I am assuming that locking the Unity Greeter will  prevent the nutty log-on screen snipper ... so .. here goes...

on

01:00.0 VGA compatible controller: NVIDIA Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

*note* .. by the way .. this was when synaptic was working :)

 Thats why  doing multiple installs at different states  can have certain advantages  (but we will see)

---

### Post by mc4man on 2012-02-28
> am about to do updates
Well then you won't be able to update gnome-settings-daemon which may also affect others, ultimately a dead end.
Sooner or later they'll need to fix lightdm/unity-greeter

---

### Post by ventrical on 2012-02-28
> **mc4man said:**
> Well then you won't be able to update gnome-settings-daemon which may also affect others, ultimately a dead end.
Sooner or later they'll need to fix lightdm/unity-greeter


Actually it is just amazing. After I locked the <unity-greeter> in synaptic  it , synaptic, proceeded to remove <unity-greeter> and then updated about 600MBs. Before I closed synaptic I had seen your above message and then decided at the last moment to unlock <unity-greeter> and then updated it.

Everything went well with the exception is that now I have this beautifully smooth GDM? (I think)and there is no horrible distorted graphics after log-on.

Whatever the case , the experiment worked, partially.

---

### Post by snkiz on 2012-02-28
> **ventrical said:**
> No, I haven't seen this anomoly on any of my screens but it may be  an indicator that may lead to a work around.

Not sure its related to the screen corruption issue, I'm not seeing that and I have a GeForce 7025 / nForce 630a integrated chip. I have seen the hand off degrade, I get a black screen now while logging in for a moment. That never used to happen. I had upgraded my monitor from a 4:3 crt to a 16:9 lcd. but it was working fine a few weeks ago.

---

### Post by ventrical on 2012-02-28
> **snkiz said:**
> Not sure its related to the screen corruption issue, I'm not seeing that and I have a GeForce 7025 / nForce 630a integrated chip. I have seen the hand off degrade, I get a black screen now while logging in for a moment. That never used to happen. I had upgraded my monitor from a 4:3 crt to a 16:9 lcd. but it was working fine a few weeks ago.


  I get this on one of my older MAG Innovision LCD monitors.  When Precise first starts up I get the purple screen offset to the top and left.

---

### Post by snkiz on 2012-02-28
> **ventrical said:**
> I get this on one of my older MAG Innovision LCD monitors.  When Precise first starts up I get the purple screen offset to the top and left.

That's  also strange, for me Grub/console is fine. It was "showing out of range" (bad resolution or refresh rate.) but I fixed that in grub. The issue I have also predates my grub fix. I actually tackled it because of the bug I filed hoping it would fix it.

---

### Post by mbah.pande on 2012-02-28
Can't find any configuration off unity-greeter on /etc/lightdm/

creater manually unity-greeter.conf doesnt work change my greeter background

any suggestion?

---

### Post by snkiz on 2012-02-29
I just had a thought. Most of the issues here happened after they switched to dconf configuration from the file in /etc/.. I think mine did to. So how do you edit the dconf settings for a user you can't login to?

---

### Post by mbah.pande on 2012-02-29
wher configuration file off unity greeter placed?

---

### Post by Baldrick_NZ on 2012-02-29
> **mbah.pande said:**
> Can't find any configuration off unity-greeter on /etc/lightdm/

creater manually unity-greeter.conf doesnt work change my greeter background

any suggestion?

Download 'Simple lightdm manager', which will do this for you, not currently in the repos. Sorry, I don't have the link, but your friend google will gladly help. :-)

---

### Post by ventrical on 2012-03-01
[QUOTE=effenberg0x0;11718591]Nope, although I grew to prefer working with them, VMs are mostly for Job #1. Job #2 (my business) is all about real machines.

2 questions: 
1) How are you guys on non-stock software, I mean, stuff like xorg-edgers and Ricotz PPAs, for example? 
2) Isn't there anything that can help in the logs? I know it will be impossible to read logs in such a messy display, but do it in console via recovery. There has to be some lead. 

**EDIT:** Oh, forgot to add a stupid question: Is it OK when booting to a previous kernel in Grub?
**EDIT2:** If possible, see what you get for these commands:
```

lsmod | grep -i nouveau
lsmod | grep -i nvidia
nvidia-xconfig --version
sudo modinfo nvidia
X -version
unity --version
lightdm --version
cat /etc/X11/xorg.conf

```

just getting back..

```
ventrical@dale:~$ lsmod | grep -i nouveau
ventrical@dale:~$ lsmod | grep -i nvidia
nvidia              10937322  40 
ventrical@dale:~$ nvidia-xconfig --version

nvidia-xconfig:  version 295.20 
(buildmeister@swio-display-x86-rhel47-01.nvidia.com)  Mon Feb  6 21:30:26 PST
2012
  The NVIDIA X Configuration Tool.

  This program is used to manipulate X configuration files, specifically to
  enable NVIDIA X driver functionality.

  Copyright (C) 2005 - 2010 NVIDIA Corporation.

ventrical@dale:~$ sudo modinfo nvidia
[sudo] password for ventrical: 
Sorry, try again.
[sudo] password for ventrical: 
ERROR: modinfo: could not find module nvidia
ventrical@dale:~$ unity --version
unity 5.4.0
ventrical@dale:~$ lightdm --version
lightdm 1.1.3
ventrical@dale:~$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory
ventrical@dale:~$ 

```

---

### Post by snkiz on 2012-03-01
I haven't tried edgers or  ricoz ppa. ppa's cause headaches during upgrades, and the repo isn't set in stone just yet. I'm trying to not use ppa's as much as I can this round

---

### Post by confused57 on 2012-03-02
I'm seeing the login artifacts(from other installs) on six different home-built computers, all with discrete Nvidia graphics cards(8400GS, 8600GT,
9600GSO, 2-9800GT, 450Fermi, after a warm reboot.  On a cold boot, I'm seeing the attached screenshot after pressing "Enter" at the login screen.  The image is really light & dark gray squares, not bluish-tinted ones from the camera snapshot.

I don't see the login screen corruption when using gdm, which also allows booting into gnome-session(unlike the most recent lightdm update).

---

### Post by ventrical on 2012-03-02
> **confused57 said:**
> I'm seeing the login artifacts(from other installs) on six different home-built computers, all with discrete Nvidia graphics cards(8400GS, 8600GT,
9600GSO, 2-9800GT, 450Fermi, after a warm reboot.  On a cold boot, I'm seeing the attached screenshot after pressing "Enter" at the login screen.  The image is really light & dark gray squares, not bluish-tinted ones from the camera snapshot.

I don't see the login screen corruption when using gdm, which also allows booting into gnome-session(unlike the most recent lightdm update).

  I think there is a certain "uniqueness" to each different computer.  I think it differentiates the aspect point of that certain PCs personality (if you will). After all, no two Steinway pianos are the same either.
 :)
kewl...

---

### Post by confused57 on 2012-03-02
> **ventrical said:**
> I think there is a certain "uniqueness" to each different computer.  I think it differentiates the aspect point of that certain PCs personality (if you will). After all, no two Steinway pianos are the same either.
 :)
kewl...

My primary reason for my last post was to illustrate that the lightdm "handoff" from login to the Desktop is probably a common issue. I don't believe it is a Nvidia issue, although I don't have any ATI graphics cards to support this.  I hope this gets resolved before the final release in April, new users wouldn't know to use gdm, and as mc4man pointed out it could be a privacy concern for multiple user accounts.  I must admit lightdm is more aesthetically pleasing and should make a good impression for new users, if the current bugs can be addressed.

---

### Post by cariboo on 2012-03-02
> **confused57 said:**
> My primary reason for my last post was to illustrate that the lightdm "handoff" from login to the Desktop is probably a common issue. I don't believe it is a Nvidia issue, although I don't have any ATI graphics cards to support this.  I hope this gets resolved before the final release in April, new users wouldn't know to use gdm, and as mc4man pointed out it could be a privacy concern for multiple user accounts.  I must admit lightdm is more aesthetically pleasing and should make a good impression for new users, if the current bugs can be addressed.

As far as I'm concerned, it is a Nvidia issue, as my netbook with Intel graphics doesn't do it, and if I remember correctly the Ubuntu devs are working with the Nvidia devs to solve the problem.

---

### Post by confused57 on 2012-03-02
> **cariboo907 said:**
> As far as I'm concerned, it is a Nvidia issue, as my netbook with Intel graphics doesn't do it, and if I remember correctly the Ubuntu devs are working with the Nvidia devs to solve the problem.

You're probably right, I was basing my supposition on this bug report:
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/933322](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/933322)

It may, or may not be related to the same bug seen with Nvidia graphics.

---

### Post by ventrical on 2012-03-02
> **confused57 said:**
> My primary reason for my last post was to illustrate that the lightdm "handoff" from login to the Desktop is probably a common issue. I don't believe it is a Nvidia issue, although I don't have any ATI graphics cards to support this.  I hope this gets resolved before the final release in April, new users wouldn't know to use gdm, and as mc4man pointed out it could be a privacy concern for multiple user accounts.  I must admit lightdm is more aesthetically pleasing and should make a good impression for new users, if the current bugs can be addressed.


Yes this is an ATI problem also.

---

### Post by VinDSL on 2012-03-02
> **cariboo907 said:**
> As far as I'm concerned, it is a Nvidia issue, as my netbook with Intel graphics doesn't do it, and if I remember correctly the Ubuntu devs are working with the Nvidia devs to solve the problem.
Heh!  Then, again...

I've never experienced the problem... not even once... on this purely nVidia-driven machine.

I dunno.  I'm just lurking, but from what I've read, it's a real problem, and largely inscrutable.

Truthfully, I haven't noticed any definable pattern, based on the posts...  ;)

---

### Post by cariboo on 2012-03-02
I just did a fresh install of Beta 1, I get a different form of corruption with the nouveau driver than I do with nvidia-current. If I'd been thinking, I would have taken a picture of the different screens. :(

---

### Post by VinDSL on 2012-03-02
> **cariboo907 said:**
> I just did a fresh install of Beta 1, I get a different form of corruption with the nouveau driver than I do with nvidia-current. If I'd been thinking, I would have taken a picture of the different screens. :(
Okay, so...

We've got a pattern of corruption with ATi, nVidia, and Nouveau graphics, but (as ventrical noted) only on certain "Steinways".  

There's more, here, than meets the eye. LoL!  :D

---

### Post by ventrical on 2012-03-02
> **VinDSL said:**
> Okay, so...

We've got a pattern of corruption with ATi, nVidia, and Nouveau graphics, but (as ventrical noted) only on certain "Steinways".  

There's more, here, than meets the eye. LoL!  :D

 hehehe ... Honestly Vin .. it's mutating. I kid you not.  But with three Intell based graphics adapters it works like a breeze. I have another machine which uses the old "96" nvidia driver and I have no problem on that machine.

---

### Post by effenberg0x0 on 2012-03-03
@ventrical Sorry, I totally forgot about this thread. It caught my eyes that you have no output for sudo modinfo nvidia, while normally you should see this:
```

$ sudo modinfo nvidia
[sudo] password for ahsl: 
filename:       /lib/modules/3.2.0-17-generic/kernel/drivers/video/nvidia.ko
alias:          char-major-195-*
version:        295.20
supported:      external
license:        NVIDIA
alias:          pci:v000010DEd00000E00sv*sd*bc04sc80i00*
alias:          pci:v000010DEd00000AA3sv*sd*bc0Bsc40i00*
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
depends:        
vermagic:       3.2.0-17-generic SMP mod_unload modversions 
parm:           NVreg_EnableVia4x:int
parm:           NVreg_EnableALiAGP:int
parm:           NVreg_ReqAGPRate:int
parm:           NVreg_EnableAGPSBA:int
parm:           NVreg_EnableAGPFW:int
parm:           NVreg_Mobile:int
parm:           NVreg_ResmanDebugLevel:int
parm:           NVreg_RmLogonRC:int
parm:           NVreg_ModifyDeviceFiles:int
parm:           NVreg_DeviceFileUID:int
parm:           NVreg_DeviceFileGID:int
parm:           NVreg_DeviceFileMode:int
parm:           NVreg_RemapLimit:int
parm:           NVreg_UpdateMemoryTypes:int
parm:           NVreg_InitializeSystemMemoryAllocations:int
parm:           NVreg_UseVBios:int
parm:           NVreg_RMEdgeIntrCheck:int
parm:           NVreg_UsePageAttributeTable:int
parm:           NVreg_EnableMSI:int
parm:           NVreg_MapRegistersEarly:int
parm:           NVreg_RegisterForACPIEvents:int
parm:           NVreg_RegistryDwords:charp
parm:           NVreg_RmMsg:charp
parm:           NVreg_NvAGP:int

```If you could run this command again (sudo modinfo nvidia), I think we're up to something here. I would at least expect you to have the module file at the right place. 

This command...
```
ls -la /lib/modules/3.2.0-17-generic/kernel/drivers/video/nvidia.ko
```...should output
> -rw-r--r-- 1 root root 16997172 Feb 24 14:35 /lib/modules/3.2.0-17-generic/kernel/drivers/video/nvidia.koRegards,
Effenberg

**EDIT: **If you can't find nvidia.ko where it was supposed to be, search /lib for it and post results here please.
```
sudo find /lib -name "nvidia.ko"
```

---

### Post by bmbaker on 2012-03-03
@ effenberg0x0 had todo a search using nautilus as it didn't find nvidia.ko from the terminal
```
/var/lib/dkms/nvidia-current/295.20/build/nvidia.ko
```

---

### Post by bmbaker on 2012-03-03
i just setup a fresh install of beta1 on a old samsung R50 with intel graphics and getting the same graphics noise!

---

### Post by fantab on 2012-03-03
Installed 12.04 Beta1 and Updated. There is this issue with Login Screen. When I choose a pre-installed background image that bundles with Ubuntu, the Login background changes to the one I have on my desktop background. 

However when I select a personal image (from Pictures folder) the desktop background changes but the Login background does not and reverts back to warty.png.

I tried moving my image to /usr/share/backgrounds but it does not change the login background. Also I have noticed that the image added to /usr/share/backgrounds does not show in the Settings-Appearance-Wallpapers. I am assuming that either the greeter is not looking at /usr/share/backgrounds or there is some sort of bug. Anyways there is no etc/lightdm/unity-greeter config. 

Has anyone figured this out yet?
Where are Settings-Appearance-Wallpapers Located? Or how are they linked to /usr/share/backgrounds?

:confused:

---

### Post by cariboo on 2012-03-03
@Effenber0x0, I don't have a nvidia.ko on my system. but in /lib/modules/3.2.0-17-generic/kernel/drivers/video/nvidia, there is a file called nvidiafb.ko, this is using the 295.20 nvidia driver from the repositories.

---

### Post by confused57 on 2012-03-03
> **cariboo907 said:**
> @Effenber0x0, I don't have a nvidia.ko on my system. but in /lib/modules/3.2.0-17-generic/kernel/drivers/video/nvidia, there is a file called nvidiafb.ko, this is using the 295.20 nvidia driver from the repositories.
My results are similar:
```
/lib/modules/3.2.0-17-generic-pae/kernel/drivers/video/nvidia/nvidiafb.ko
```

I uninstalled nvidia-current from the repositories, installed nvidia 295.* from Nvidia and get this:
```
/lib/modules/3.2.0-17-generic-pae/kernel/drivers/video/nvidia.ko
```
Now I have nvidiafb.ko and nvidia.ko in separate locations, but I'm still getting the artifacts between unity-greeter and the desktop.

---

### Post by mc4man on 2012-03-03
> **fantab said:**
> . 

However when I select a personal image (from Pictures folder) the desktop background changes but the Login background does not and reverts back to warty.png.

I tried moving my image to /usr/share/backgrounds but it does not change the login background. Also I have noticed that the image added to /usr/share/backgrounds does not show in the Settings-Appearance-Wallpapers. 

:confused:
I've never had an issue with any image from Pictures that's set as the Desktop background from being used in the greeter but for whatever reason some people do

Are you using an encrypted Home dir.?

When you pick a Desktop background that image should be saved to ~/.cache/wallpaper & if needed would be a resized image fitting your display. I'd assume the greeter would use that one.

The is a gsettings section on unity-greeter but never seen any need to adjust from the default (dconf-editor > com > canonical > greeter), it never reflects the actual image being used if not the default

While i don't see as needed  - To add any image to Backgrounds you also need to add to the .xml - ex. in screen, I added the bottom one. 

sudo gedit -H /usr/share/gnome-background-properties/ubuntu-wallpapers.xml

---

### Post by ventrical on 2012-03-03
> **effenberg0x0 said:**
> @ventrical Sorry, I totally forgot about this thread. It caught my eyes that you have no output for sudo modinfo nvidia, while normally you should see this:
```

$ sudo modinfo nvidia
[sudo] password for ahsl: 
filename:       /lib/modules/3.2.0-17-generic/kernel/drivers/video/nvidia.ko
alias:          char-major-195-*
version:        295.20
supported:      external
license:        NVIDIA
alias:          pci:v000010DEd00000E00sv*sd*bc04sc80i00*
alias:          pci:v000010DEd00000AA3sv*sd*bc0Bsc40i00*
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
depends:        
vermagic:       3.2.0-17-generic SMP mod_unload modversions 
parm:           NVreg_EnableVia4x:int
parm:           NVreg_EnableALiAGP:int
parm:           NVreg_ReqAGPRate:int
parm:           NVreg_EnableAGPSBA:int
parm:           NVreg_EnableAGPFW:int
parm:           NVreg_Mobile:int
parm:           NVreg_ResmanDebugLevel:int
parm:           NVreg_RmLogonRC:int
parm:           NVreg_ModifyDeviceFiles:int
parm:           NVreg_DeviceFileUID:int
parm:           NVreg_DeviceFileGID:int
parm:           NVreg_DeviceFileMode:int
parm:           NVreg_RemapLimit:int
parm:           NVreg_UpdateMemoryTypes:int
parm:           NVreg_InitializeSystemMemoryAllocations:int
parm:           NVreg_UseVBios:int
parm:           NVreg_RMEdgeIntrCheck:int
parm:           NVreg_UsePageAttributeTable:int
parm:           NVreg_EnableMSI:int
parm:           NVreg_MapRegistersEarly:int
parm:           NVreg_RegisterForACPIEvents:int
parm:           NVreg_RegistryDwords:charp
parm:           NVreg_RmMsg:charp
parm:           NVreg_NvAGP:int

```If you could run this command again (sudo modinfo nvidia), I think we're up to something here. I would at least expect you to have the module file at the right place. 

This command...
```
ls -la /lib/modules/3.2.0-17-generic/kernel/drivers/video/nvidia.ko
```...should output
Regards,
Effenberg

**EDIT: **If you can't find nvidia.ko where it was supposed to be, search /lib for it and post results here please.
```
sudo find /lib -name "nvidia.ko"
```

 Sorry .. none of those commands worked at all.  The last one to 'search' just did nothing .

---

### Post by ventrical on 2012-03-03
> **effenberg0x0 said:**
> @ventrical Sorry, I totally forgot about this thread. It caught my eyes that you have no output for sudo modinfo nvidia, while normally you should see this:
```

$ sudo modinfo nvidia
[sudo] password for ahsl: 
filename:       /lib/modules/3.2.0-17-generic/kernel/drivers/video/nvidia.ko
alias:          char-major-195-*
version:        295.20
supported:      external
license:        NVIDIA
alias:          pci:v000010DEd00000E00sv*sd*bc04sc80i00*
alias:          pci:v000010DEd00000AA3sv*sd*bc0Bsc40i00*
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
depends:        
vermagic:       3.2.0-17-generic SMP mod_unload modversions 
parm:           NVreg_EnableVia4x:int
parm:           NVreg_EnableALiAGP:int
parm:           NVreg_ReqAGPRate:int
parm:           NVreg_EnableAGPSBA:int
parm:           NVreg_EnableAGPFW:int
parm:           NVreg_Mobile:int
parm:           NVreg_ResmanDebugLevel:int
parm:           NVreg_RmLogonRC:int
parm:           NVreg_ModifyDeviceFiles:int
parm:           NVreg_DeviceFileUID:int
parm:           NVreg_DeviceFileGID:int
parm:           NVreg_DeviceFileMode:int
parm:           NVreg_RemapLimit:int
parm:           NVreg_UpdateMemoryTypes:int
parm:           NVreg_InitializeSystemMemoryAllocations:int
parm:           NVreg_UseVBios:int
parm:           NVreg_RMEdgeIntrCheck:int
parm:           NVreg_UsePageAttributeTable:int
parm:           NVreg_EnableMSI:int
parm:           NVreg_MapRegistersEarly:int
parm:           NVreg_RegisterForACPIEvents:int
parm:           NVreg_RegistryDwords:charp
parm:           NVreg_RmMsg:charp
parm:           NVreg_NvAGP:int

```If you could run this command again (sudo modinfo nvidia), I think we're up to something here. I would at least expect you to have the module file at the right place. 

This command...
```
ls -la /lib/modules/3.2.0-17-generic/kernel/drivers/video/nvidia.ko
```...should output
Regards,
Effenberg

**EDIT: **If you can't find nvidia.ko where it was supposed to be, search /lib for it and post results here please.
```
sudo find /lib -name "nvidia.ko"
```

Ok.. on one install I have it here : but I had to use nautilus to search for it.

---

### Post by ventrical on 2012-03-03
> **effenberg0x0 said:**
> @ventrical Sorry, I totally forgot about this thread
This command...
```
ls -la /lib/modules/3.2.0-17-generic/kernel/drivers/video/nvidia.ko
```...should output
Regards,
Effenberg

**EDIT: **If you can't find nvidia.ko where it was supposed to be, search /lib for it and post results here please.
```
sudo find /lib -name "nvidia.ko"
```

On the install where I tired your suggested proceedure about a week and a half ago:

(Your suggested proceedure) here> [http://ubuntuforums.org/showpost.php?p=11717610&postcount=77](http://ubuntuforums.org/showpost.php?p=11717610&postcount=77)


camel2@ubuntu:~$ sudo find /lib -name "nvidia.ko"
[sudo] password for camel2: 
/lib/modules/3.2.0-17-generic-pae/kernel/drivers/video/nvidia.ko
camel2@ubuntu:~$

---

### Post by effenberg0x0 on 2012-03-03
Thanks Ventrical and others. bmbaker, I got your PM too. 

I'm using the weekend to organize / redo cabling here. It all started as I was installing a broadband load balancer 8 hours ago... nothing is ever as simple as we imagine it will be. All my home and home-office infrastructure is offline, I'm using my smartphone as an access point now.

I'll study this Nvidia situation as soon as I finish reorganizing the cabling mess here. As far as I could understand, we shouldn't be having any of these issues. Why are only some people affected? Why does reinstalling the kernel module fixes it for some many users, but not for all of them? Fundamentally, I gotta be able to understand what are the differences between machines that work and those that do not. But the problem is: I don't have a Nvidia-based machine that doesn't work so I can diff it... :confused: How do I break working install to reproduce the behavior you're seeing? No idea.

I'll post as soon as (and if) I find out something more solid. Probably later today or even tomorrow.

Regards,
Effenberg

---

### Post by mc4man on 2012-03-03
> **effenberg0x0 said:**
>  How do I break working install to reproduce the behavior you're seeing? No idea.

Just curious - do any of your nvidia machines where i'm assuming you say the unity greeter > to Desktop works as intended, have another install with unity-greeter (an 11.10 or 12.04 install

(I would love it if a live session had a working log out/in so I could see if the greeter worked there, currently it always fails *here

---

### Post by ventrical on 2012-03-03
> **effenberg0x0 said:**
> Thanks Ventrical and others. bmbaker, I got your PM too. 

I'm using the weekend to organize / redo cabling here. It all started as I was installing a broadband load balancer 8 hours ago... nothing is ever as simple as we imagine it will be. All my home and home-office infrastructure is offline, I'm using my smartphone as an access point now.

I'll study this Nvidia situation as soon as I finish reorganizing the cabling mess here. As far as I could understand, we shouldn't be having any of these issues. Why are only some people affected? Why does reinstalling the kernel module fixes it for some many users, but not for all of them? Fundamentally, I gotta be able to understand what are the differences between machines that work and those that do not. But the problem is: I don't have a Nvidia-based machine that doesn't work so I can diff it... :confused: How do I break working install to reproduce the behavior you're seeing? No idea.

I'll post as soon as (and if) I find out something more solid. Probably later today or even tomorrow.

Regards,
Effenberg

 @mc4man too

  I have a hunch. I am curious as to what repositories are you using , Main , US ?? etc ?

  I have 2  and then 3 option here.

  On one install (same machine) I have  Main Server and Server from Canada, Other..then, on the other Install I have  Main Server and Server from US and Other..  so I am just wondering (as I postulated before) that could it be  that this anonoly is being propagated from one server and not another ???

brainsotrm anyone ?

Edit: this install I am running is Off of Main Server. (I'll be back).

ok .. back .. my Secondary install is pegged for Server for United States.

@effenberg (when you get back) &mac4man

what servers are you using ... or is this theory wasting time ?

---

### Post by ventrical on 2012-03-03
@ effenberg

1. What server do you use in your sources list.?
2. Do you choose third part updates during install?

---

EDIT

ok .. here goes .. upgrade to beta1 with  repos leaned out.

apologies .. to remain at topic .. this experiemnt is to test a theory about the Unity Greeter distorted screen after log-on with Precise.

---

### Post by ventrical on 2012-03-03
Ok .. did another development release upgrade of a perfectly good Oneiric install (a beaut) with no third party sources .. etc.. and .. same stuff.. only this time the Unity -greeter hand0off  took a greeter screen from another install (with users) and put that screen up in a paper mache'!-

 So what is happening here is that video buffers are being cached and then written to disk on shut-down or log-off. - sort of like some hidden program is trying to remember where the user left off <something like zeitgeist?> and/or the unity-greet subroutine is pointing to this scrambled cache and then putting it up on the screen. In my other experiments I tried removing my nvidia card, trying to trick Ubuntu into thinking something, but that did not work (and in that situation I thought somthing was being statically  locked in the nvidia harddware memory !!

so.. assuming then that during the startup sequence - perhaps even early on, there is a cache of  *recent activities* being grabbed into  a memory buffer and then being dumped after the Unity-greeter  hands off to the desktop. It sort of behaves like a malware or even a custom malware because the distorted screen is the complete antithesis of Unity is that is takes a users searches, screen shots and activities and then renders them in a 'dis-unity' fashion after log on.

  In some ways this could be a security nightmare if this is in fact the case.

---

### Post by VinDSL on 2012-03-03
> **mc4man said:**
> I've never had an issue with any image from Pictures that's set as the Desktop background from being used in the greeter but for whatever reason some people do[...]
Only problem I've ever had was...

My native res is 1280x1024.

If I use a 1280x1024 wall on my desktop, then the greeter will display it properly.

If I use some odd size like 2560x1600, then the desktop will display the wall properly, by the greeter gives me the middle finger.  LoL~  :D

---

### Post by VinDSL on 2012-03-03
> **ventrical said:**
> 
brainsotrm anyone ?

Edit: this install I am running is Off of Main Server. (I'll be back).

ok .. back .. my Secondary install is pegged for Server for United States.

what servers are you using ... or is this theory wasting time ?
I've used both... mostly Main, but now Server for United States (since a recent Flash update had a bad IP).

Haven't had a "corruption" problem with either.

---

### Post by ventrical on 2012-03-03
Thanks Vin ... 

Question?

Would you check your  x-0-greeter.log  in var/log/lightdm and see if you have this output near the bottom.

```
[+1.19s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+1.19s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+1.19s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+1.19s] WARNING: menubar.vala:508: Indicator object 0x8b760bc not in menubar
[+1.20s] WARNING: Getting layout failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.dbusmenu' on object at path /com/canonical/indicator/users/menu


```

thanks

you have to use nautilus as root to read that file

---

### Post by confused57 on 2012-03-03
> **ventrical said:**
> Thanks Vin ... 

Question?

Would you check your  x-0-greeter.log  in var/log/lightdm and see if you have this output near the bottom.

```
[+1.19s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+1.19s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+1.19s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+1.19s] WARNING: menubar.vala:508: Indicator object 0x8b760bc not in menubar
[+1.20s] WARNING: Getting layout failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.dbusmenu' on object at path /com/canonical/indicator/users/menu


```

thanks

you have to use nautilus as root to read that file

I'm getting the same warnings:
```
[+0.96s] WARNING: Getting layout failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.dbusmenu' on object at path /com/canonical/indicator/users/menu
[+0.97s] DEBUG: Num devices: '0'

[+0.97s] MESSAGE: Couldn't find primary device
[+0.97s] DEBUG: Num devices: '0'

[+0.97s] DEBUG: icon_policy is: 0 (present==0, charge==1, never==2)
[+0.97s] DEBUG: count_batteries found 0 batteries (0 are charging/discharging)
[+0.97s] DEBUG: should_be_visible: no
[+0.97s] DEBUG: menubar.vala:496: Removing indicator object 0xa0570bc
[+0.97s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+0.97s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+0.97s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+0.97s] WARNING: menubar.vala:508: Indicator object 0xa0570bc not in menubar
[+1.05s] DEBUG: unity-greeter.vala:191: starting system-ready sound
[+1.52s] DEBUG: background.vala:110: Render of background /home/james/Downloads/ubuntu-1110-keyboard-shortcuts-wallpaper.jpg complete
[+1.57s] DEBUG: background.vala:110: Render of background /usr/share/backgrounds/warty-final-ubuntu.png complete
[+1.62s] DEBUG: notify visible signal received
[+1.62s] CRITICAL: ido_calendar_menu_item_set_date: assertion `IDO_IS_CALENDAR_MENU_ITEM(menuitem)' failed
[+1.62s] DEBUG: New calendar item
[+1.63s] DEBUG: indicator-sound: new_volume_slider_widget
[+1.63s] DEBUG: indicator-sound: new_voip_slider_widget
[+1.64s] DEBUG: background.vala:110: Render of background /home/james/Downloads/ubuntu-1110-keyboard-shortcuts-wallpaper.jpg complete
[+5.98s] DEBUG: Providing response to display manager
[+5.98s] DEBUG: Wrote 26 bytes to daemon
[+6.03s] DEBUG: Read 8 bytes from daemon
[+6.03s] DEBUG: Read 17 bytes from daemon
[+6.03s] DEBUG: Authentication complete for user james with return code 0
[+6.03s] CRITICAL: gtk_widget_draw: assertion `!widget->priv->alloc_needed' failed
```

Would be interesting to see what VinDSL is getting, as well as others who're not getting the corruption.

---

### Post by confused57 on 2012-03-03
> **ventrical said:**
> Ok .. did another development release upgrade of a perfectly good Oneiric install (a beaut) with no third party sources .. etc.. and .. same stuff.. only this time the Unity -greeter hand0off  took a greeter screen from another install (with users) and put that screen up in a paper mache'!-

 So what is happening here is that video buffers are being cached and then written to disk on shut-down or log-off. - sort of like some hidden program is trying to remember where the user left off <something like zeitgeist?> and/or the unity-greet subroutine is pointing to this scrambled cache and then putting it up on the screen. In my other experiments I tried removing my nvidia card, trying to trick Ubuntu into thinking something, but that did not work (and in that situation I thought somthing was being statically  locked in the nvidia harddware memory !!

so.. assuming then that during the startup sequence - perhaps even early on, there is a cache of  *recent activities* being grabbed into  a memory buffer and then being dumped after the Unity-greeter  hands off to the desktop. It sort of behaves like a malware or even a custom malware because the distorted screen is the complete antithesis of Unity is that is takes a users searches, screen shots and activities and then renders them in a 'dis-unity' fashion after log on.

  In some ways this could be a security nightmare if this is in fact the case.

A very accurate & descriptive explanation of what I'm seeing and do believe you're right on with what's happening with framebuffer/cache at unity-greeter/lightdm login.  Post #23 in this bug report is a good example of what appears at a reboot login:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/931967](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/931967)
Would it help to mention this bug report(or another one) in the Sticky Bug Management Report thread?

---

### Post by effenberg0x0 on 2012-03-03
> **mc4man said:**
> Just curious - do any of your nvidia machines where i'm assuming you say the unity greeter > to Desktop works as intended, have another install with unity-greeter (an 11.10 or 12.04 install

(I would love it if a live session had a working log out/in so I could see if the greeter worked there, currently it always fails *here

HI mc4man, 
No, not the case here. 

Well, it's 1:10AM. It's been a horrible day. I have all my stuff in a broken (rebuilding) 10TB RAID5 now. At max reserved speed in a SATA 3 setup, it will take almost 11 hours to check/rebuild the whole thing........... So I better play with Nvidia now, before I break something else. I'll keep you guys posted if I find something interesting.


Regards,
Effenberg

---

### Post by mc4man on 2012-03-03
> **effenberg0x0 said:**
> HI mc4man, 
No, not the case here. 

Well, it's 1:10AM. It's been a horrible day. I have all my stuff in a broken (rebuilding) 10TB RAID5 now. At max reserved speed in a SATA 3 setup, it will take almost 11 hours to check/rebuild the whole thing........... So I better play with Nvidia now, before I break something else. I'll keep you guys posted if I find something interesting.


Regards,
Effenberg

I don't think having multiple lightdm installs has anything to do with though haven't been in a position to discount here (maybe I'll wipe this drive clean & do a single

What I do find interesting is depending on which install grub is configured on (11.10; 12.04; 12.04 atm) the top 12.04 install will sometimes access(?) the 11.10 partition & use the greeter & logo png's from there

That doesn't seem quite right..

---

### Post by VinDSL on 2012-03-03
> **ventrical said:**
> Thanks Vin ... 

Question?

Would you check your  x-0-greeter.log  in var/log/lightdm and see if you have this output near the bottom.

```
[+1.19s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+1.19s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+1.19s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+1.19s] WARNING: menubar.vala:508: Indicator object 0x8b760bc not in menubar
[+1.20s] WARNING: Getting layout failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.dbusmenu' on object at path /com/canonical/indicator/users/menu


```

thanks

you have to use nautilus as root to read that file

Here's the entire log...


```
Activating service name='org.a11y.atspi.Registry'
[+0.00s] DEBUG: unity-greeter.vala:589: Starting unity-greeter 0.2.4 UID=104 LANG=en_US.UTF-8
[+0.00s] DEBUG: unity-greeter.vala:592: Setting cursor
[+0.07s] DEBUG: unity-greeter.vala:596: Creating background surface
Successfully activated service 'org.a11y.atspi.Registry'
SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
[+0.10s] DEBUG: unity-greeter.vala:599: Loading command line options
[+0.10s] DEBUG: unity-greeter.vala:627: Setting GTK+ settings

** WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** WARNING **: Unable to register client with session manager
[+0.53s] DEBUG: unity-greeter.vala:650: Creating Unity Greeter
[+0.53s] DEBUG: Connecting to display manager...
[+0.53s] DEBUG: Wrote 17 bytes to daemon
[+0.53s] DEBUG: Read 8 bytes from daemon
[+0.53s] DEBUG: Read 90 bytes from daemon
[+0.53s] DEBUG: Connected version=1.1.3 default-session=ubuntu hide-users=false has-guest-account=true
[+1.81s] WARNING: unity-greeter.vala:95: Failed to load state from /var/lib/lightdm/.cache/unity-greeter/state: Key file contains line ' A' which is not a key-value pair, group, or comment

[+3.53s] DEBUG: menubar.vala:295: LANG=en_US.UTF-8 LANGUAGE=(null)
[+5.09s] CRITICAL: g_error_free: assertion `error != NULL' failed
[+5.18s] DEBUG: get entries
[+5.19s] DEBUG: menubar.vala:488: Adding indicator object 0x9181a7c at position 0
[+5.34s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+5.34s] DEBUG: Checking against 2 possible times
[+6.92s] DEBUG: Guessing max time width: 62
[+7.03s] DEBUG: get entries
[+7.03s] DEBUG: menubar.vala:488: Adding indicator object 0x916b2fc at position 1
[+7.07s] WARNING: IndicatorObject class does not have an accessible description.
[+7.23s] WARNING: IndicatorObject class does not have an accessible description.
[+7.23s] DEBUG: get entries
[+7.23s] DEBUG: get entries
[+7.23s] DEBUG: menubar.vala:488: Adding indicator object 0x90a292c at position 2
[+7.23s] DEBUG: menubar.vala:312: LANG=en_US.UTF-8 LANGUAGE=(null)
[+7.29s] DEBUG: Loaded session /usr/share/xsessions/gnome-shell.desktop (GNOME, This session logs you into GNOME)
[+7.30s] DEBUG: Loaded session /usr/share/xsessions/ubuntu-2d.desktop (Ubuntu 2D, This session logs you into Ubuntu 2D Mode)
[+7.31s] DEBUG: Loaded session /usr/share/xsessions/ubuntu.desktop (Ubuntu, This session logs you into Ubuntu)
[+7.34s] DEBUG: Loaded session /usr/share/xsessions/gnome-fallback.desktop (GNOME Classic (No effects), This session logs you into GNOME with the traditional panel without any graphical effect.)
[+7.36s] DEBUG: Loaded session /usr/share/xsessions/gnome-classic.desktop (GNOME Classic, This session logs you into GNOME with the traditional panel)
[+7.36s] DEBUG: Ignoring session /usr/share/xsessions/gnome.desktop
[+7.36s] DEBUG: session-chooser.vala:42: Adding session gnome-shell (GNOME)
[+7.36s] DEBUG: session-chooser.vala:42: Adding session gnome-classic (GNOME Classic)
[+7.36s] DEBUG: session-chooser.vala:42: Adding session gnome-fallback (GNOME Classic (No effects))
[+7.36s] DEBUG: session-chooser.vala:42: Adding session ubuntu (Ubuntu)
[+7.36s] DEBUG: session-chooser.vala:42: Adding session ubuntu-2d (Ubuntu 2D)
[+7.44s] CRITICAL: session_chooser_get_badge: assertion `session != NULL' failed
[+7.45s] CRITICAL: user_list_select_entry: assertion `entry != NULL' failed
[+7.45s] DEBUG: main-window.vala:95: Screen is 1280x1024 pixels
[+7.45s] DEBUG: main-window.vala:101: Monitor 0 is 1280x1024 pixels at 0,0
[+7.46s] DEBUG: Loading users from org.freedesktop.Accounts
[+7.46s] DEBUG: Loading user /org/freedesktop/Accounts/User1000
[+7.55s] DEBUG: Loading sessions from org.freedesktop.DisplayManager
[+7.55s] DEBUG: unity-greeter.vala:206: Adding/updating user vindsl (VinDSL)
[+7.57s] CRITICAL: session_chooser_get_badge: assertion `session != NULL' failed
[+7.89s] DEBUG: Setting keyboard layout to 'us'
[+8.44s] DEBUG: background.vala:63: Making background /home/vindsl/Pictures/Wallpaper/ubuntu.8.04.png at 1280x1024
[+8.44s] DEBUG: unity-greeter.vala:138: Adding guest account entry
[+8.58s] DEBUG: unity-greeter.vala:339: Failed to write state: Error writing to file: Bad address
[+8.58s] DEBUG: Starting authentication for user vindsl...
[+8.58s] DEBUG: Wrote 22 bytes to daemon
[+8.58s] DEBUG: unity-greeter.vala:653: Showing greeter
[+8.58s] DEBUG: unity-greeter.vala:235: Showing main window
[+8.59s] DEBUG: New style for time label
[+8.59s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+8.59s] DEBUG: Checking against 2 possible times
[+8.59s] DEBUG: Guessing max time width: 62
[+8.70s] DEBUG: background.vala:308: Regenerating backgrounds
[+8.70s] DEBUG: background.vala:63: Making background /usr/share/backgrounds/warty-final-ubuntu.png at 1280x1024
[+8.70s] DEBUG: background.vala:63: Making background /home/vindsl/Pictures/Wallpaper/ubuntu.8.04.png at 1280x1024
[+8.70s] DEBUG: New style for time label
[+8.70s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+8.70s] DEBUG: Checking against 2 possible times
[+8.70s] DEBUG: Guessing max time width: 62
[+8.74s] DEBUG: unity-greeter.vala:666: Starting main loop
[+9.68s] DEBUG: Read 8 bytes from daemon
[+9.68s] DEBUG: Read 36 bytes from daemon
[+9.68s] DEBUG: Prompt user with 1 message(s)
[COLOR="DarkRed"]**[+9.70s] WARNING: Getting layout failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.dbusmenu' on object at path /com/canonical/indicator/users/menu**[/COLOR]
[+9.71s] DEBUG: Num devices: '0'

[+9.71s] MESSAGE: Couldn't find primary device
[+9.71s] DEBUG: Num devices: '0'

[+9.71s] DEBUG: icon_policy is: 0 (present==0, charge==1, never==2)
[+9.71s] DEBUG: count_batteries found 0 batteries (0 are charging/discharging)
[+9.71s] DEBUG: should_be_visible: no
[+9.71s] DEBUG: menubar.vala:496: Removing indicator object 0x90a28d4
[COLOR="DarkRed"][B][+9.71s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+9.71s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+9.71s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+9.71s] WARNING: menubar.vala:508: Indicator object 0x90a28d4 not in menubar[/B][/COLOR]
[+9.74s] DEBUG: unity-greeter.vala:191: starting system-ready sound
[+11.72s] DEBUG: background.vala:110: Render of background /usr/share/backgrounds/warty-final-ubuntu.png complete
[+11.79s] DEBUG: notify visible signal received
[+11.79s] CRITICAL: ido_calendar_menu_item_set_date: assertion `IDO_IS_CALENDAR_MENU_ITEM(menuitem)' failed
[+11.80s] DEBUG: New calendar item
[+11.81s] DEBUG: indicator-sound: new_volume_slider_widget
[+11.81s] DEBUG: indicator-sound: new_voip_slider_widget
[+11.89s] DEBUG: background.vala:110: Render of background /home/vindsl/Pictures/Wallpaper/ubuntu.8.04.png complete
[+11.93s] DEBUG: background.vala:110: Render of background /home/vindsl/Pictures/Wallpaper/ubuntu.8.04.png complete
[+21.20s] DEBUG: Providing response to display manager
[+21.20s] DEBUG: Wrote 24 bytes to daemon
[+21.43s] DEBUG: Read 8 bytes from daemon
[+21.43s] DEBUG: Read 18 bytes from daemon
[+21.43s] DEBUG: Authentication complete for user vindsl with return code 0
[+21.43s] CRITICAL: gtk_widget_draw: assertion `!widget->priv->alloc_needed' failed
[+21.43s] DEBUG: Starting session ubuntu
[+21.43s] DEBUG: Wrote 18 bytes to daemon
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
No protocol specified
No protocol specified
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
```

---

### Post by effenberg0x0 on 2012-03-04
**!!!!!!!!!!!!!!! PLEASE TRY THIS BEFORE READING ANY FURTHER (AND REPORT BACK). !!!!!!!!!!!!!!!**
**CCSM Plugins:**
- OpenGL: Disable Lighting, Disable Texture Compression. 
- Copy to Texture: Disable
Stop Lightdm, Start Lightdm, Restart, reboot, etc. Does it fix that for you, or do you see any improvement?
(This is for the people that were seeing VGA corruption between pressing enter in Lightdm and loading the desktop)

**EDIT**: I think that's it! It effectively fixes the problem in one affected machine, even after reboots.


-----------------------------------------------------------------------------------------
Hi Guys, let me give you an update. I'm at that point in which feedback and brainstorming can really help. I have borrowed a PC with this exact symptom and managed tolook at it for a while. I'll post some of my impressions:

1) This is not a Nvidia bug. All Nvidia Files/Contents were diffed (Text/Binary) between both machines (affected / not-affected) and no diff was relevant. Nvidia logs on the affected machine show no relevant error in logs. I'm gonna assume it's not a VGA-related bug for now and only go back to this hypothesis if everything else fails.

2) "/var/lib/lightdm/.cache/unity-greeter/state" seems broken to me. I believe this should be a standard "pair" (key=value" file, but I have a lot of stuff in it. If I delete it, it is recreated and still seems corrupted. Can anyone tell me if that format is acceptable?

3) ```
cat /etc/lightdm/unity-greeter.conf | grep -i '^background'
```> background=/usr/share/backgrounds/warty-final-ubuntu.pngand
```
gsettings list-keys $(gsettings list-schemas | grep -i greeter) | grep -i '^background$'
```> background```
gsettings get com.canonical.unity-greeter background
```> '/usr/share/backgrounds/warty-final-ubuntu.png'Although this background does not show in the affected machine lightdm or desktop.
**EDIT:** But ```
gsettings set org.gnome.desktop.background picture-uri 'file:///home/ahsl/Pictures/planets-aligned-1920x1080-wallpaper-4218.jpg'
``` immediately changes the background. And ```
gsettings set com.canonical.unity-greeter background '/home/ahsl/Pictures/planets-aligned-1920x1080-wallpaper-4218.jpg'
``` does change the greeter background. What is it? Permissions for the warty file? Why are this keys not in sync? Meh. Irrelevant.

4) ```
xdg-open /usr/share/backgrounds/warty-final-ubuntu.png
```tells me this not a valid PNG file. 
```
sudo gimp /usr/share/backgrounds/warty-final-ubuntu.png
```...and "File/Save As" /usr/share/backgrounds/warty-final-ubuntu.png makes it into a valid PNG file.
Irrelevant.

**5) Now try this:**
A) ```
sudo ln -s /usr/share/backgrounds/warty-final-ubuntu.png $HOME/Pictures/warty-final-ubuntu.png && sudo chmod 664 $HOME/Pictures/warty-final-ubuntu.png
```B) Then, inside Ubuntu session, right click the desktop, select "Change Desktop Background", "Pictures", Select warty-final-ubuntu.png.
C) At a gnome-terminal: sudo service lightdm stop
(at some VT) sudo service lightdm restart
D) Now warty-final-ubuntu.png shows in lightdm. But, after login, you'll get VGA corruption before the desktop shows. 
E) At a gnome-terminal: sudo service lightdm stop
(at some VT) sudo service lightdm restart
F) warty-final-ubuntu.png shows in lightdm. But now, after login, you **WON't** get VGA corruption before the desktop shows.

And you can try to restart lightdm as much as you want, it won't show corruption in VGA again. You'll believe it is fixed, but it's not. That will only last until you decide to change the wallpaper again.

So, ***IMO*** we should really look at Cache, that is Saved States. I will insist in what I described at Item **2**. 

I have looked at /var/lib/lightdm/.cache/unity-greeter/state in **OO**. It looks like this:```
[greeter]
last-user=ahsl
```Therefore I edited this file to remove all that garbage, leaving only these two lines. And, just as a test, I tried:```
sudo chattr +i /var/lib/lightdm/.cache/unity-greeter/state
```No luck. All I know so far is that you only get screen corruption once, after changing background. If you stop lightdm and start it again, the problem does not manifest. 

**Programmatically:** "Let's load a cache of the user desktop fast, so that he sees something, while we're loading Unity. Then we load his background and refresh the screen." It makes sense: what we see in the corrupted screen is the previous session. Where's this thing cached/read from? We need to log which functions read the background file. To remote-dbg is hell, not in the mood, too tired.



To be continued: Gotta sleep.

**WAIT:** Compiz, CCSM:
- OpenGL: Disable Lighting, Texture Compression. 
- Copy to Texture: Disable
It *seems* like it's fixed?

**EDIT:** AHA! These options are not activated in my Nvidia machines that are **NOT AFFECTED**. They are active in the **AFFECTED** machine!

Ok, maybe this is not a fix but a workaround. Unity is loading a cache of the desktop to show something fast while it is loading other stuff. We disabled this possibility via Compiz. Is that it?

---

### Post by mc4man on 2012-03-04
> **effenberg0x0 said:**
> **!!!!!!!!!!!!!!! PLEASE TRY THIS BEFORE READING ANY FURTHER (AND REPORT BACK). !!!!!!!!!!!!!!!**
ect...
ect...

Nada, here have gotten either the snippets from anywhere & everywhere or an interesting B&W stepped stairs ever since this started quite some time ago with a unity-greeter upgrade (though the issue is in lightdm

The only time I get a decent 'handoff' as it's being termed is when it uses the one from 11.10

You'll probably want to revisit your last post tomorrow (those ccsm options are in OpenGl & likely off by default, ect.

I'll likely give it till release to get fixed, if not then I'll dump the greeter & use the gtk one

At this point it's just an annoyance though I still think lightdm is gaining access to places it has no business doing so. (what other users have been looking at, other installs, ect.

---

### Post by effenberg0x0 on 2012-03-04
> **mc4man said:**
> Nada, here have gotten either the snippets from anywhere & everywhere or an interesting B&W stepped stairs ever since this started quite some time ago with a unity-greeter upgrade (though the issue is in lightdm

The only time I get a decent 'handoff' as it's being termed is when it uses the one from 11.10

You'll probably want to revisit your last post tomorrow (those ccsm options are in OpenGl & likely off by default, ect.

I'll likely give it till release to get fixed, if not then I'll dump the greeter & use the gtk one

At this point it's just an annoyance though I still think lightdm is gaining access to places it has no business doing so. (what other users have been looking at, other installs, ect.

Damned. The thing is, now I have another Nvidia machine that is **NOT AFFECTED** by this bug. It's truly fixed, just like the others. I was sure it was the CCSM settings, but now that you mentioned it did nothing for you, I can't say which of the previous steps and attempts, or the sum of them, seems to have fixed it. And now I need to find someone to borrow me **ANOTHER **broken machine :(

---

### Post by ventrical on 2012-03-04
> **effenberg0x0 said:**
> Damned. The thing is, now I have another Nvidia machine that is **NOT AFFECTED** by this bug. It's truly fixed, just like the others. I was sure it was the CCSM settings, but now that you mentioned it did nothing for you, I can't say which of the previous steps and attempts, or the sum of them, seems to have fixed it. And now I need to find someone to borrow me **ANOTHER **broken machine :(

No luck here either. Iv'e been through most of the ccsm steps earlier on.
Trying different things.  Your right ... it keeps commign back !

 For example I just deleted warty-final from backgrounds, logged off , log on and it was perfect.  Then , reboot and worse than ever.  But I did notice some type of a change while trying your ccsm suggestions and perhaps there is something still there , somthing that we have not seen yet .. may be very simple indeed, mabey bot .

off back to busy for most of the day .. I'll be back later..

---

### Post by ventrical on 2012-03-04
> **mc4man said:**
> Nada, here have gotten either the snippets from anywhere & everywhere or an interesting B&W stepped stairs ever since this started quite some time ago with a unity-greeter upgrade (though the issue is in lightdm

The only time I get a decent 'handoff' as it's being termed is when it uses the one from 11.10

You'll probably want to revisit your last post tomorrow (those ccsm options are in OpenGl & likely off by default, ect.

I'll likely give it till release to get fixed, if not then I'll dump the greeter & use the gtk one

At this point it's just an annoyance though I still think lightdm is gaining access to places it has no business doing so. (what other users have been looking at, other installs, ect.


It gives a bad first impression  of Precise to the new_users. This bug should have been attended to long ago. But I agree  that it may be until release day that we see it fixed. I don't understand the logic in this.

---

### Post by effenberg0x0 on 2012-03-04
Guys can you give me some help here? I'm trying to understand a couple things:

**1)** Suppose $HOME/Pictures/background.jpg is a valid JPG background file.
gsettings set org.gnome.desktop.background picture-uri 'file:///$HOME/Pictures/background.jpg' and
gsettings set com.canonical.unity-greeter background '$HOME/Pictures/background.jpg both work, but the value at cat /etc/lightdm/unity-greeter.conf | grep -i '^background' is not changed. 

- I understand that /etc/lightdm/unity-greeter.conf is deprecated, so should it be deleted? Have you tried it? For now, I have manually edited it to match the same JPG file, just for safety. I don't know if something (and what) may still be reading from it.
- The fact that both keys are not in sync, or that the desktop-background and unity-greeter background are not being retrieved from the same key, should be considered a bug, right? We're supposed to see the desktop background in the greeter, as a PP feature.

**2)** What's your take on the amount of garbage inside /var/lib/lightdm/.cache/unity-greeter/state? Do you see it? It was not like that in OO and previous PP. Bug? I have manually cleaned it (leaving only the key-pairs) and chattr +i.

**3)** Also, just for kicks, I have added my user to the lightdm group (so I could play in /var/lib/lightdm*) and fixed permissions for /var/lib/lightdm to 775 recursively. While looking at stuff there, I have also verified /var/lib/lightdm/.nv/GLCache/* keeps files between sessions. You get the same inside $HOME/.nv/. Why should it? What's the logic? Well, I finished active sessions and cleared these files.

**4)** What is $HOME/.cache/unity/bgcachefile? It's empty for me.

**5)** At this point, in Nvidia hardware, I have verified that the first boot shows VGA corruption in the transition from lightdm to desktop. However, sudo service lightdm stop, sudo service lightdm start, there's no corruption anymore, no matter how many times I do it. It starts again only if I go to a VT, DISPLAY=:0.0 compiz --replace&, sudo service lightdm stop, sudo service lightdm start. Agreed? Or do you continue to get the VGA corruption?

**6)** This is when I though about GL, Compiz, Textures. I did had OpenGL/TextureCompression and CopyToTexture activated in the borrowed affected machine (and verified it was not activated in my not-affected ones). I disabled these settings and the borrowed machine seems fixed. I can switch backgrounds, restart sessions, reboot, and the machine shows no corruption from lightdm to desktop.

I mean, it's undeniable something positive happened - I see no VGA corruption. I just need to understand now what fixed it effectively.

Regards,
Effenberg

---

### Post by ventrical on 2012-03-04
> **effenberg0x0 said:**
> Guys can you give me some help here? I'm trying to understand a couple things:

**1)** Suppose $HOME/Pictures/background.jpg is a valid JPG background file.
gsettings set org.gnome.desktop.background picture-uri 'file:///$HOME/Pictures/background.jpg' and
gsettings set com.canonical.unity-greeter background '$HOME/Pictures/background.jpg both work, but the value at cat /etc/lightdm/unity-greeter.conf | grep -i '^background' is not changed. 

- I understand that /etc/lightdm/unity-greeter.conf is deprecated, so should it be deleted? Have you tried it? For now, I have manually edited it to match the same JPG file, just for safety. I don't know if something (and what) may still be reading from it.
- The fact that both keys are not in sync, or that the desktop-background and unity-greeter background are not being retrieved from the same key, should be considered a bug, right? We're supposed to see the desktop background in the greeter, as a PP feature.

**2)** What's your take on the amount of garbage inside /var/lib/lightdm/.cache/unity-greeter/state? Do you see it? It was not like that in OO and previous PP. Bug? I have manually cleaned it (leaving only the key-pairs) and chattr +i.

**3)** Also, just for kicks, I have added my user to the lightdm group (so I could play in /var/lib/lightdm*) and fixed permissions for /var/lib/lightdm to 775 recursively. While looking at stuff there, I have also verified /var/lib/lightdm/.nv/GLCache/* keeps files between sessions. You get the same inside $HOME/.nv/. Why should it? What's the logic? Well, I finished active sessions and cleared these files.

**4)** What is $HOME/.cache/unity/bgcachefile? It's empty for me.

**5)** At this point, in Nvidia hardware, I have verified that the first boot shows VGA corruption in the transition from lightdm to desktop. However, sudo service lightdm stop, sudo service lightdm start, there's no corruption anymore, no matter how many times I do it. It starts again only if I go to a VT, DISPLAY=:0.0 compiz --replace&, sudo service lightdm stop, sudo service lightdm start. Agreed? Or do you continue to get the VGA corruption?

**6)** This is when I though about GL, Compiz, Textures. I did had OpenGL/TextureCompression and CopyToTexture activated in the borrowed affected machine (and verified it was not activated in my not-affected ones). I disabled these settings and the borrowed machine seems fixed. I can switch backgrounds, restart sessions, reboot, and the machine shows no corruption from lightdm to desktop.

I mean, it's undeniable something positive happened - I see no VGA corruption. I just need to understand now what fixed it effectively.

Regards,
Effenberg


 the <sudo service lighdm stop, sudo service lightdm start> fixes it temporarily, but the corruption is back after a log-on log off  ( or I didn't understand you correctly.)

 I tried to read the /state file but it won't allow me to read it or ask for which application to use. (how do I readthat unrecognized file)?

---

### Post by effenberg0x0 on 2012-03-04
> **ventrical said:**
> the <sudo service lighdm stop, sudo service lightdm start> fixes it temporarily, but the corruption is back after a log-on log off  ( or I didn't understand you correctly.)

I am saying that, in the broken machine I had access to, if the unity-greeter background and desktop background are correctly defined (to a valid JPG background path/file) via the procedures I described (gsettings and manually editing the conf file), the machine presents VGA corruption only on first session start. After that, restarting the session as many times as you want will not show the bug. So, basically, it survives a restart of lightdm and compiz. But it doesn't survive a reboot, and that's mysterious to me.

However, considering the steps I described are done, including the CCSM setting, the bug is gone for good in the machine I had access to. 
 
> **ventrical said:**
> 
 I tried to read the /state file but it won't allow me to read it or ask for which application to use. (how do I readthat unrecognized file)?
Use nano, vi, pico, any console editor. Or just cat to view it's contents.

If someone could approach the procedures I outlined in a methodical way, it would be helpful.

Thanks,
Effenberg

---

### Post by ventrical on 2012-03-04
> **effenberg0x0 said:**
> I am saying that, in the broken machine I had access to, if the unity-greeter background and desktop background are correctly defined (to a valid JPG background path/file) via the procedures I described (gsettings and manually editing the conf file), the machine presents VGA corruption only on first session start. After that, restarting the session as many times as you want will not show the bug. So, basically, it survives a restart of lightdm and compiz. But it doesn't survive a reboot, and that's mysterious to me
Effenberg


Yes , yes... and what I did was delete warty-final-ubuntu.png from backgrounds, made a STANDARD user account with NO compiz settings manager and I too can log in, log off to sessions with no corruption with the exception of reboot.  I notice in some logs that  it (unity-greeter) tries to load menu items also at handoff and some of these are corrupt it appears   . so I too am still working on this one .. were close .. were that >'< close to it.!


 Thanks again for all your time effenberg, to this problem ..  I plan to give it as much time as I can .. but  taking a little stop check at the moment.. a  long day ...

---

### Post by mc4man on 2012-03-04
New install, no other installs on drive - worked properly once. then images started creeping in.

Have via another method gotten rid of all 'corrupted' images from login > to Desktop, _restarts are irrelevant_.
(I'd tried all that was mentioned, corruption remained

 There is one caveat though - 
If my Background is set to the the default warty then all is as intended - 
The greeter is warty, after entering password then the grid fades, warty remains & Desktop loads

If I switch to another Background  - 
That background is shown on greeter log in screen, after password the screen switches to warty (no corruption), then the  Desktop loads with my chosen background

So to clear up - when you 'fixed' there - if using any background but warty is **that chosen image maintained thru the complete login > Desktop?**

Edit - after a dozen or so restarts with various Desktop images - 
No sign of any 'corrupted', if using Warty as Desktop image all is perfect, any other Desktop image also shows no corruption but  do the switch off to warty after password instead of maintaining the initial greeter image

---

### Post by effenberg0x0 on 2012-03-04
> **mc4man said:**
> New install, no other installs on drive - worked properly once. then images started creeping in.

Have via another method gotten rid of all 'corrupted' images from login > to Desktop, _restarts are irrelevant_.
(I'd tried all that was mentioned, corruption remained

 There is one caveat though - 
If my Background is set to the the default warty then all is as intended - 
The greeter is warty, after entering password then the grid fades, warty remains & Desktop loads

If I switch to another Background  - 
That background is shown on greeter log in screen, after password the screen switches to warty (no corruption), then the  Desktop loads with my chosen background

So to clear up - when you 'fixed' there - if using any background but warty is **that chosen image maintained thru the complete login > Desktop?**

Edit - after a dozen or so restarts with various Desktop images - 
No sign of any 'corrupted', if using Warty as Desktop image all is perfect, any other Desktop image also shows no corruption but  do the switch off to warty after password instead of maintaining the initial greeter image

HI mc4man,

Yes, after I selected another JPG and set it as described, the image is maintained from login to desktop. No other image, like the warty one, shows at any point. The first session shows corruption in the transition from login to desktop, and from then on, corruption is gone, ever after reboots.

---

### Post by effenberg0x0 on 2012-03-04
So, let's explore what you're seeing there mc4man. 

You choose a unity-greeter background via... 
```
gsettings set org.gnome.desktop.background picture-uri 'file:///home/mc4man/Pictures/SomeBackground.jpg
```...and you set unity-greeter to use the same background. First via gsettings...
```
gsettings set com.canonical.unity-greeter background  '/home/mc4man/Pictures/SomeBackground.jpg 
```...and then just to play safe, define it also in the /etc conf file.
```
sudo nano /etc/lightdm/unity-greeter.conf
```> [greeter]
background=/home/mc4man/Pictures/SomeBackground.jpg1) Test 1
```
sudo service lightdm stop
sudo service lightdm start
```Do you still see the warty image?
2) Test 2
```
sudo service lightdm stop
sudo service lightdm start
```Do you still see the warty image? Is there corruption on Test 2?
If so: Where's it coming from. Do you have it defined in any key in gsettings? Do a gsettings list-recursively | grep -i "warty". Where the hell is it defined?

Regards,
Effenberg


EDIT: What if you rename or move the warty image file?

---

### Post by mc4man on 2012-03-04
> **effenberg0x0 said:**
> HI mc4man,

Yes, after I selected another JPG and set it as described, the image is maintained from login to desktop. No other image, like the warty one, shows at any point. The first session shows corruption in the transition from login to desktop, and from then on, corruption is gone, ever after reboots.

I'm going to try that from the top again & see. (which post?, which section?)

 What I was doing would survive reboots, log outs, & Background changes  but **not** a full shutdown & cold boot.

(simplified it to this - 
install the gtk-greeter
```
sudo /usr/lib/lightdm/lightdm-set-defaults -g lightdm-gtk-greeter
```
```
sudo rm -R /var/lib/lightdm/.nv
```
restart
```
sudo /usr/lib/lightdm/lightdm-set-defaults -g unity-greeter
```
restart

Then no corruption until an actual full shutdown

(at least here this is like a dog chasing it's tail..

Edit: missed your post > will review

---

### Post by effenberg0x0 on 2012-03-04
@mc4man, #178, #184.

I just found out something interesting. On machines that are "fixed", I can consistently recreate the bug, like this:
```

sudo service lightdm stop
sudo rm -rf /var/lib/lightdm/.nv/GLCache/*
sudo service lightdm start

```$HOME/.nv/GLCache/* seems to be irrelevant. I can rm everything and the sessions still show no VGA corruption.

Also, I just noticed the existance of ls -la $HOME/.cache/wallpaper/*. DOes anyone knows if it has always been there and what is it for?

Regards,
Effenberg

---

### Post by mc4man on 2012-03-04
Results of  - 
!st - full shutdown, restart back to  - chosen background at greeter > corruption > Desktop

> You choose a unity-greeter background via... 
```
gsettings set org.gnome.desktop.background picture-uri 'file:///home/mc4man/Pictures/SomeBackground.jpg
```...and you set unity-greeter to use the same background. First via gsettings...
```
gsettings set com.canonical.unity-greeter background  '/home/mc4man/Pictures/SomeBackground.jpg 
```...and then just to play safe, define it also in the /etc conf file.
```
sudo nano /etc/lightdm/unity-greeter.conf
```1) Test 1
```
sudo service lightdm stop
sudo service lightdm start
```Do you still see the warty image?
Result - 
Get chosen Background as greeter > corruption, (no warty) > Desktop

> 2) Test 2
```
sudo service lightdm stop
sudo service lightdm start
```Do you still see the warty image? Is there corruption on Test 2?
Result - 
Get chosen Background as greeter > corruption, (no warty) > Desktop

>  EDIT: What if you rename or move the warty image file?

Will give it a test - may be similar to what I erroneously suggested previously about a wk. ago, if so it'll fix till a reboot, then corruption won't be an issue, there'll be no greeter at all

==========================================================================
Just to note - after going above steps & tests, then just a switch to gtk, restart, switch to unity greeter & back to no corruption at all as described previously

also to note - as far as gsettings - the com.canonical.unity-greeter settings are somewhat irrelevant, in the past installs have unset them all to pretty much no effect

---

### Post by mc4man on 2012-03-04
> Also, I just noticed the existance of ls -la $HOME/.cache/wallpaper/*. DOes anyone knows if it has always been there and what is it for

Yes - it's been there for quite some time

Not exactly clear on it's use - you'll notice it's resized to Desktop (monitor rez) if different from Image copied/backed up from

I thought once it was what was being used instead of chosen Image, but if you were to remove your chosen Image from Pictures & log out ...

Edit: setting things back to where there is no corruption but that intermediate warty screen, if using custom Background - 
moving/renaming the png in /usr/share/backgrounds had no ill effect, but the image still showed. From where?, no clue - but
the gtk greeter does use that '.png', I replaced it with my current one & it is used with the gtk greeter

---

### Post by mc4man on 2012-03-04
This bug is pretty funny - realistically probably won't be fixed till upstream fixes 
 
Anyway - 
Copied my current image to /usr/share/backgrounds as warty-final-ubuntu.png
switched to gtk greeter
restarted
switched back to unity-greeter

Now I get chosen at greeter screen > stays on chosen, (my new warty-final-ubuntu.png) > Desktop

This stays good till a full shutdown, then chosen at greeter screen > corruption > Desktop

---

### Post by effenberg0x0 on 2012-03-04
I'm stracing lightdm and children processes. It's a huge output. But so far I can see that, although I have no "warty" set anywhere, and the image does not show to me, background.vala calls it.

---

### Post by ventrical on 2012-03-05
@Cariboo

I tried your suggestion and did a fresh Beta1 install from USB with NO third party drivers and it was a lone install  on a 20GB Maxtor EIDE (no other installs).  The install went beautifully with the:01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600]
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600] (Secondary)
adapted card and as soon as it rebooted from hard boot .. the distortion was there as if it had never left.

---

### Post by confused57 on 2012-03-05
> **ventrical said:**
> @Cariboo

I tried your suggestion and did a fresh Beta1 install from USB with NO third party drivers and it was a lone install  on a 20GB Maxtor EIDE (no other installs).  The install went beautifully with the:01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600]
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600] (Secondary)
adapted card and as soon as it rebooted from hard boot .. the distortion was there as if it had never left.

Had a similar experience(adding my "me too"), installed the 64-bit Ubuntu 12.04 daily build for Mar4 with no 3rd party drivers, except to an AMD mobo with Nvidia 9800GT...corruption at first boot.  I tried effenberg's suggestions in post #184, seemed to help at first; but the mosaic snippets of previous Desktop screens are back in all their glory.

---

### Post by ventrical on 2012-03-05
> **confused57 said:**
> Had a similar experience(adding my "me too"), installed the 64-bit Ubuntu 12.04 daily build for Mar4 with no 3rd party drivers, except to an AMD mobo with Nvidia 9800GT...corruption at first boot.  I tried effenberg's suggestions in post #184, seemed to help at first; but the mosaic snippets of previous Desktop screens are back in all their glory.


hehehe .. and ya know .. those snippets (even though they may be aggravating) do have a certain glory to them. Every once in a while the kaliedascopic effects can be surreal :)  Maybe it just may be  the birthing of  Hawkings'  red-life-form :)

---

### Post by ventrical on 2012-03-06
I was just doing some more brainstorming here and by default the  option on the screensaver is set to Grab screen. I changed it to <random> and I noticed that the behaviour of the start_up, log-on,log-off distortion also changed dramatically. I am not saying this is a clue but anyone willing to test it, please do and let me know if you see a change in the distorted screens.

thanks..

---

### Post by ventrical on 2012-03-06
> **mc4man said:**
> Just curious - do any of your nvidia machines where i'm assuming you say the unity greeter > to Desktop works as intended, have another install with unity-greeter (an 11.10 or 12.04 install

(I would love it if a live session had a working log out/in so I could see if the greeter worked there, currently it always fails *here


  I just did that with beta1  on a  2GB USB persistent drive. I created two users, logged off , logged back on and the corruption was there in all it's glory, (and this install was not connected to the internet) so , no updates at all.. a raw install with no third party software and no HDD connected. (Live Session) as you say.

Summary:

 The unity-greeter distortion has been  inherited into the Precise beta1 release.
 Graphics= ATI Radeon

 haven't tried nvidia yet.

---

### Post by bmbaker on 2012-03-06
ya well with a fresh install of Beta 1 with nvidia-current the graphics distortion is still there! i decided to try the lightdm-gtk-greeter and there was no distortion, but alot of flickers instead!!

---

### Post by ventrical on 2012-03-06
> **bmbaker said:**
> ya well with a fresh install of Beta 1 with nvidia-current the graphics distortion is still there! i decided to try the lightdm-gtk-greeter and there was no distortion, but alot of flickers instead!!


  I am going to try that. Thanks ... it appears that the devs have abandoned any attempt at trying to fix this bug.  One thing for sure .. I really like Unity .. I want it to be good and great ... and with all of you and your brainstorming I know were going to get this fixed.. I got one fix already by removing unity-greeter first, then  installing GDM . Removing unity-greeter also took the ubuntu-desktop with it so I had to install unity-greeter and ubuntu-desktop from terminal. Now I have that GDM on one machine and no distortion. That was on an older nvidia. I am going to try to emulate that an a GF210.

Hey .. thanks bmbaker for staying at this ! :)  This has to be the 'Bug of the Century' :)

---

### Post by ventrical on 2012-03-06
> **bmbaker said:**
> ya well with a fresh install of Beta 1 with nvidia-current the graphics distortion is still there! i decided to try the lightdm-gtk-greeter and there was no distortion, but alot of flickers instead!!

wow .. I just found out that lightdm-gtk-greeter was already installed alongside unity-greeter. What is this ?

---

### Post by ventrical on 2012-03-06
<TEMP FIX>

Ok .. so I went into terminal, removed lightdm, unity greeter and sudo apt-get install gdm and , voila' distortion be gone !!:)

---

### Post by bmbaker on 2012-03-06
something that Harry posted awhile back  

[http://ubuntuforums.org/showthread.php?t=1911186&page=2&highlight=lightdm](http://ubuntuforums.org/showthread.php?t=1911186&page=2&highlight=lightdm)

```
I have these lines in /etc/lightdm/lightdm.conf
Code:
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=gnome
allow-guest=false
LightDM does not offer any guest session (like I ordered it not to). That is OK.
LightDM uses Gnome as default session. I can change it if I like. That is OK.
LigthDM uses lightdm-gtk-greeter. Also OK.

```

you can change lightdm-gtk-greeter for unity-greeter

---

### Post by ventrical on 2012-03-06
> **bmbaker said:**
> something that Harry posted awhile back  

[http://ubuntuforums.org/showthread.php?t=1911186&page=2&highlight=lightdm](http://ubuntuforums.org/showthread.php?t=1911186&page=2&highlight=lightdm)

```
I have these lines in /etc/lightdm/lightdm.conf
Code:
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=gnome
allow-guest=false
LightDM does not offer any guest session (like I ordered it not to). That is OK.
LightDM uses Gnome as default session. I can change it if I like. That is OK.
LigthDM uses lightdm-gtk-greeter. Also OK.

```you can change lightdm-gtk-greeter for unity-greeter


When I removed lightdm and then re-installed gdm a pop-up came up telling me that X can only run one Desktop Manager at a time and to tic off the default  in   etc/init.d  I'll perhaps try (Harry's suggestion) that also . 

  Have you heard of any movement at all on this   (distortion) bug?

---

### Post by bmbaker on 2012-03-06
no just what has been posted here and other threads!
i have another machine intel graphics and the same distortion!
to my mind its a lightdm and unity-greeter problem!
gdm wks great, though i stick to the lightdm for the moment :-)
:-)

---

### Post by ventrical on 2012-03-06
> **bmbaker said:**
> no just what has been posted here and other threads!
i have another machine intel graphics and the same distortion!
to my mind its a lightdm and unity-greeter problem!
gdm wks great, though i stick to the lightdm for the moment :-)
:-)

My 3 Intell based machines all have no distortion with unity-greeter - but I agree that there is something wrong with the lightdm and unity-greeter.
i'm still hacking away at it here
one of us is going to nail this one , sooner , I hope than later :)

---

### Post by ventrical on 2012-03-06
Just want to report a strange anomoly here. <lightdm> after being removed, had reinstalled itself without authorization. When I removed unity-greeter and lightdm it did not mention any dependencies or remove any other propgrams. When I installed gdm it was just that one lone program that was loaded. therefore lightdm installed itself through he background.

edit* wow .. and unity-greeter re-installed itself again also !!?

---

### Post by ventrical on 2012-03-06
and even stranger yet I do not even have the ubuntu-desktop installed! :)

man oh man this is fun hehe

---

### Post by ventrical on 2012-03-06
The  lightdm-gtk-greeter with Harry's config worked great here .. no distortion or flicker.

---

### Post by ventrical on 2012-03-06
EDIT OUT**Just saw that there is a new lightdm GoObject  update.**

wrong system.
.

---

### Post by fantab on 2012-03-06
> **mc4man said:**
> I've never had an issue with any image from Pictures that's set as the Desktop background from being used in the greeter but for whatever reason some people do

Are you using an encrypted Home dir.?

When you pick a Desktop background that image should be saved to ~/.cache/wallpaper & if needed would be a resized image fitting your display. I'd assume the greeter would use that one.

The is a gsettings section on unity-greeter but never seen any need to adjust from the default (dconf-editor > com > canonical > greeter), it never reflects the actual image being used if not the default

While i don't see as needed  - To add any image to Backgrounds you also need to add to the .xml - ex. in screen, I added the bottom one. 

sudo gedit -H /usr/share/gnome-background-properties/ubuntu-wallpapers.xml

Thanks **mc4man**, I tried almost everything you suggested but nothing worked. 

Then in /usr/share/backgrounds in changed my favorite images to .png and re-edited /usr/share/gnome-background-properties/ubuntu-wallpapers.xml and voila! its working. My greeter background is changed to that of my desktop. 

However, I can still see the "Warty" image before greeter changes to my selected image. 

There is only "Warty" when I select an image for Pictures Folder.

---

### Post by ventrical on 2012-03-07
> **mc4man said:**
> Yes - it's been there for quite some time

Not exactly clear on it's use - you'll notice it's resized to Desktop (monitor rez) if different from Image copied/backed up from

I thought once it was what was being used instead of chosen Image, but if you were to remove your chosen Image from Pictures & log out ...

Edit: setting things back to where there is no corruption but that intermediate warty screen, if using custom Background - 
moving/renaming the png in /usr/share/backgrounds had no ill effect, but the image still showed. From where?, no clue - but


  I deleted warty from user/share/backgrounds and got a deep blue background, Unity launcher, desktop.. etc... and corruption at startup was still there but not at log-on, log-off.

 When I checked backgrounds by right-clicking the desktop it reported (null) in the screen Icon.

---

### Post by mc4man on 2012-03-08
The current bug on this has become fairly active the last coupe of days, hopefully a new unity-greeter  will be forthcoming shortly

---

### Post by VinDSL on 2012-03-08
> **mc4man said:**
> [...] hopefully a new unity-greeter  will be forthcoming shortly
Au contraire!

I was hoping to see the affects, before the "bug-of-the-century" disappears.

I know... I know.  

Better be careful what you wish for... because it might come true. LoL!  :D

---

### Post by mc4man on 2012-03-08
> **VinDSL said:**
> Au contraire!

I was hoping to see the affects, before the "bug-of-the-century" disappears.

I know... I know.  

Better be careful what you wish for... because it might come true. LoL!  :D
So you never did get?, if so too bad, quite interesting.
The talk now is about 'X's RetainPermanent function'

(My old P4 gamer finally bit the dust a few months ago, now relegated to the confines of a laptop, would have been curious if it would have been affected

---

### Post by ventrical on 2012-03-08
> **VinDSL said:**
> Au contraire!

I was hoping to see the affects, before the "bug-of-the-century" disappears.

I know... I know.  

Better be careful what you wish for... because it might come true. LoL!  :D


 I think it is because of the awesome backgrounds that you use and conky... that 'bug of the century' can't touch that' :)

jk

---

### Post by ventrical on 2012-03-08
> **mc4man said:**
> The current bug on this has become fairly active the last coupe of days, hopefully a new unity-greeter  will be forthcoming shortly

 @mac4man and effenberg and @bmbaker and all..

thanks for staying at this !!

---

### Post by VinDSL on 2012-03-08
> **mc4man said:**
> So you never did get?, if so too bad, quite interesting.
Never got a hint of it... and only 7 weeks 'til release.  :(

---

### Post by mc4man on 2012-03-08
I thought there was a lack of RetainPermanent(ly) here, guess not..

---

### Post by bmbaker on 2012-03-08
i just renamed warty.png to wartyhh.png and changed its name to room.png in /usr/share/gnome-background-properties/ubuntu-wallpapers.xml and then picked room.png as my new desktop background which also then changed it in the greeter when logging in/out.
One thing i have noticed if you do sudo reboot it brings up alot of stuff from the last program i.e. browser music player etc. when you do a cold boot with a full shutdown it is just black and white lge pixels!!! seems like the lightdm/unity-greeter is picking up from the graphics still for some reason.
does anyone have the 3.3.0rc kernels installed? does this effect happen with this kernel too?

---

### Post by ventrical on 2012-03-08
> **bmbaker said:**
> i just renamed warty.png to wartyhh.png and changed its name to room.png in /usr/share/gnome-background-properties/ubuntu-wallpapers.xml and then picked room.png as my new desktop background which also then changed it in the greeter when logging in/out.
One thing i have noticed if you do sudo reboot it brings up alot of stuff from the last program i.e. browser music player etc. when you do a cold boot with a full shutdown it is just black and white lge pixels!!! seems like the lightdm/unity-greeter is picking up from the graphics still for some reason.
does anyone have the 3.3.0rc kernels installed? does this effect happen with this kernel too?

 I think VinDSL has the 3.3 ?

no?

---

### Post by cariboo on 2012-03-08
Are those of you that don't see the video corruption between login and desktop using a driver directly from Nvidia?

---

### Post by bmbaker on 2012-03-08
yes i am using nvidia-current, the one from the  precise repos 295.20-0ubuntu1

---

### Post by VinDSL on 2012-03-08
nVidia driver is from the Ubu PPA. 

Linux 3.3.0-rc6 is a mainline kernel.

Here's my setup (no corruption).


```
vindsl@Zuul:~$ echo && date && lsb_release -sd || cat /etc/*release && uname -s -r && unity --version && echo && /usr/lib/nux/unity_support_test -p -f || echo && dpkg -s mesa-utils && echo

Thu Mar  8 18:17:32 MST 2012
Ubuntu precise (development branch)
Linux 3.3.0-030300rc6-generic
unity 5.4.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 295.20

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

vindsl@Zuul:~$ 

```

---

### Post by ventrical on 2012-03-09
> **VinDSL said:**
> nVidia driver is from the Ubu PPA. 

Linux 3.3.0-rc6 is a mainline kernel.

Here's my setup (no corruption).


```
vindsl@Zuul:~$ echo && date && lsb_release -sd || cat /etc/*release && uname -s -r && unity --version && echo && /usr/lib/nux/unity_support_test -p -f || echo && dpkg -s mesa-utils && echo

Thu Mar  8 18:17:32 MST 2012
Ubuntu precise (development branch)
Linux 3.3.0-030300rc6-generic
unity 5.4.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 295.20

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

vindsl@Zuul:~$ 

```

  Thanks Vin,
 I think that may explain why you have not had any corruption. Perhaps the 3.3 kernel has a fix built in already. I mean you can always try a beta1 install without the 3.3 kernel ppa and then perhaps you will see the corruption .

  I know too than effenberg has a lot of uncorrupt machines also.. but I am not sure if he is juiced in to the 3.3 ppa.  The answer may  lie in this.

However , as mac4man had pointed out , a commit  for a fix is on the way.

edit: ok .. there is a lighdm and an ubuntu-desktop update in the repo .. here goes.

---

### Post by bmbaker on 2012-03-09
welll just updated with a new lightdm and still there is corruption!
on another note i havve an old samsung running 12.04 with the 3.3.0rc6 kernel and intel graphics and it still has the same distortion.
funny though i still cannot get the nvidia to compile properly with the 3.3.0 kernels!! strange!

---

### Post by ventrical on 2012-03-09
> **bmbaker said:**
> welll just updated with a new lightdm and still there is corruption!
on another note i havve an old samsung running 12.04 with the 3.3.0rc6 kernel and intel graphics and it still has the same distortion.
funny though i still cannot get the nvidia to compile properly with the 3.3.0 kernels!! strange!

Thanks bm,

That quashes that theory. I think it is isolated to Ubuntu and not to K, L and X because I have run Lubuntu on the same machine(s) (lubuntu-desktop) and no corruption. This is an Ubuntu bug. A Unity bug!! If other releases (X.L.K) are using the same nvidia-current, etc then why are they not affected ?? Because they do not use Unity Greeter or the Unity Desktop .. or do I stand corrected here ?


btw ... distortion here also after latest lightdm update.

Will have to try a hard boot for the sake of honesty.

*edit*

the hard boot  did nothing. That update was absolutely useless in regards to that distortion bug.

---

### Post by VinDSL on 2012-03-09
> **bmbaker said:**
> [...] funny though i still cannot get the nvidia to compile properly with the 3.3.0 kernels!! strange!
Here's what I did with Linux 3.3-rc6 (paths will vary with each new kernel release)...  ;)

```

cd Downloads/Kernel [COLOR="Blue"][SIZE="1"](go to local .deb storage)[/SIZE][/COLOR]
sudo dpkg -i *.deb [COLOR="Blue"][SIZE="1"](nvidia module failed, of course)[/SIZE][/COLOR]
cd /usr/src/linux-headers-3.3.0-030300rc6-generic/arch/x86/include
sudo cp -v generated/asm/unistd* ./asm
cd Downloads/Kernel [COLOR="Blue"][SIZE="1"](back to .deb storage and reinstall)[/SIZE][/COLOR]
sudo dpkg -i *.deb [COLOR="Blue"][SIZE="1"](reinstall kernel - nvidia module compiled properly, this time)[/SIZE][/COLOR]

```

---

### Post by ventrical on 2012-03-09
> **VinDSL said:**
> Here's what I did with Linux 3.3-rc6 (paths will vary with each new kernel release)...  ;)

```

cd Downloads/Kernel [COLOR=Blue][SIZE=1](go to local .deb storage)[/SIZE][/COLOR]
sudo dpkg -i *.deb [COLOR=Blue][SIZE=1](nvidia module failed, of course)[/SIZE][/COLOR]
cd /usr/src/linux-headers-3.3.0-030300rc6-generic/arch/x86/include
sudo cp -v generated/asm/unistd* ./asm
cd Downloads/Kernel [COLOR=Blue][SIZE=1](back to .deb storage and reinstall)[/SIZE][/COLOR]
sudo dpkg -i *.deb [COLOR=Blue][SIZE=1](reinstall kernel - nvidia module compiled properly, this time)[/SIZE][/COLOR]

```


@VinDSL,or anyone else

could you walk me through on how to install the 3.3rc kernel? I did this on another machine a few times.. then .. I just forgot :)

---

### Post by ventrical on 2012-03-09
never mind .. I just remembered..:)

---

### Post by ventrical on 2012-03-09
OK .. I installed : linux-image-3.3.0-030300rc1-generic-pae_ etc , install went  great, ran VinDSL's fix for  the nividia, worked great too, rebooted and then , voila' the 'bug of the century' still there , and even Stg. Pepper  and his Lonley Hearts Club Band!1 ahaha!

 At least I got nvidia driver working so my screen don't look like a Commadore 64 :)

---

### Post by bmbaker on 2012-03-09
i think i do a fresh install and try to get the 3.3.0rc kernel to wk ..........i tried 7 or 8 times so far with fresh installs no ppa's no updates with updates but no joy!!!

on the other hand no matter which i do there is still corruption with lightdm/unity-greeter!

has anyone tried it with a down-graded version of nvidia ?

---

### Post by ventrical on 2012-03-09
> **bmbaker said:**
> i think i do a fresh install and try to get the 3.3.0rc kernel to wk ..........i tried 7 or 8 times so far with fresh installs no ppa's no updates with updates but no joy!!!

on the other hand no matter which i do there is still corruption with lightdm/unity-greeter!

has anyone tried it with a down-graded version of nvidia ?

  I thought about that very option also but I tried to look for that and I don't know the process for it.  I did , on one occasion, try to block out  (or downgrade) unity-greeter but I could not do that either.

---

### Post by cariboo on 2012-03-09
I just removed /var/lib/lightdm/.nv, and the corruption didn't show up when I logged in again. The directory wasn't recreated either. Could someone else give this a try?

**Edit:** I just did a reboot, the directory was recreated, but no corruption between login and desktop. I guess I'll have to give it a couple of reboots, to see if the corruption comes back.

---

### Post by ventrical on 2012-03-09
> **cariboo907 said:**
> I just removed /var/lib/lightdm/.nv, and the corruption didn't show up when I logged in again. The directory wasn't recreated either. Could someone else give this a try?

**Edit:** I just did a reboot, the directory was recreated, but no corruption between login and desktop. I guess I'll have to give it a couple of reboots, to see if the corruption comes back.


 It is back as ever !

 Thats with the 3.3 kernel..

I'll try another install.

*edit* nep .. no luck

---

### Post by cariboo on 2012-03-09
I'm running a system with no ppa's, and using the Nvidia 295.20 driver from  the repositories. I also checked my Intel based netbook, and of course /var/lib/lightdm/.nv isn't there.

---

### Post by ventrical on 2012-03-09
Same here . ppa and non ppa systems installed on the same drive. On one system with nvidia 96 driver .. no corruption and all Intel based pcs , no corruption. Ati radeons .. corruption .. so .. in summary , once again , Intel not affected, Nvidia/ATI affected

---

### Post by mc4man on 2012-03-09
The removal of that file & or some other fool arounds have worked for a while though it always returns.
A power down/up will always accelerate the return, (vs. restarts

this is the current active report, I don't think any new comments are needed unless  requested or providing a 'for real' fix. 

[https://bugs.launchpad.net/bugs/931967](https://bugs.launchpad.net/bugs/931967)

---

### Post by mesolithic on 2012-03-12
> **cariboo907 said:**
> I just removed /var/lib/lightdm/.nv, and the corruption didn't show up when I logged in again. The directory wasn't recreated either. Could someone else give this a try?

**Edit:** I just did a reboot, the directory was recreated, but no corruption between login and desktop. I guess I'll have to give it a couple of reboots, to see if the corruption comes back.

Doesn't work for me even for just a relog.

---

### Post by cariboo on 2012-03-12
It only worked for me, until the second reboot, and is was back to normal?

---

### Post by ventrical on 2012-03-12
> **cariboo907 said:**
> It only worked for me, until the second reboot, and is was back to normal?


 Iv'e tried multiple  workarounds and suggestions. At times , it even looks hopeful , but, after 1 or 2 <cold-boots> it back as worse as ever.

  It appears like there is some type of video-cache-logger collecting snippets of activity for logg-off or shut down. I think this is where we may find the bug - at log-off or shut-down- because it appears it is closing the file <bugofthecentury> and then grabbing it at start-up , displaying it there or doing a remaster of *it* and then ramming it up to video terminal at the log-on.

---

### Post by ventrical on 2012-03-12
Just had an mega update from the *repositories*, including  lightdm and unity-greeter. It appears that the opening start up screen distortion has been fixed but as for the log-in , it appears more  umm .. constrained in it's psychedelicness ?

:)

---

### Post by ventrical on 2012-03-13
Temporary psudeo-fix.

  I am using this wallpaper until they get this bug fixed and so I won't be distracted :)

---

### Post by PaulW2U on 2012-03-13
> **ventrical said:**
> Temporary psudeo-fix.

  I am using this wallpaper until they get this bug fixed and so I won't be distracted :)

Hey, that's my era, the 1960s!

Or you could do what I have done and install gdm. ;)

---

### Post by ventrical on 2012-03-14
> **PaulW2U said:**
> Hey, that's my era, the 1960s!

Or you could do what I have done and install gdm. ;)


 I just did a fresh install on a 7200baracuda SOYO mobo600MHz Celeron with Precise 3.2.0-18, Unity 2D, ATI Rage Pro 128 and the startup and log-on distortion is non-existent using lightdm and unity greeter!!!  I never wanted to admit to the theory that the nvidia and AMD drivers were buggy, but, looking at this benchmark it tells me something is up. I mean on release day, and the fix comes in .. then that would make NvidiaCorp and ATI corp look like heros :)

---

### Post by bmbaker on 2012-03-14
well i hope it comes in soon i was just showing a friend around gnome-shell and then unity! and they were asking if my computer was broken when i was logging in and out!!

---

### Post by mc4man on 2012-03-14
i still think this is a lightdm/unity-greeter issue & that's were the likely fix will come

One way or the other Ubuntu will have to fix this, otherwise they'd need to have an 'outer limits' style release note which would be a bit embarrassing I'd think

---

### Post by ventrical on 2012-03-14
> **bmbaker said:**
> well i hope it comes in soon i was just showing a friend around gnome-shell and then unity! and they were asking if my computer was broken when i was logging in and out!!


 I have one client that wants to update and I find now that I am making excuses not to show this person what is happening on the screen.

  But there also seems to be this wall of silence .. like the devs are not chiming in here   and I can't find any other chatter about this ... just that it is one heck of a bug... and as mac4man says .. a possible embarrassment on release day.

---

### Post by mc4man on 2012-03-14
> **ventrical said:**
> 

  But there also seems to be this wall of silence .. like the devs are not chiming in here  .

I wouldn't take much from that, - a very talented person is looking at the bug, when he has something to report then he will & it will proceed from there.

If you find it bothersome then I'd just use the gtk greeter for the moment.

( sudo apt-get install lightdm-gtk-greeter

```
sudo /usr/lib/lightdm/lightdm-set-defaults -g lightdm-gtk-greeter
```

---

### Post by ventrical on 2012-03-14
> **mc4man said:**
> I wouldn't take much from that, - a very talented person is looking at the bug, when he has something to report then he will & it will proceed from there.

If you find it bothersome then I'd just use the gtk greeter for the moment.

( sudo apt-get install lightdm-gtk-greeter

```
sudo /usr/lib/lightdm/lightdm-set-defaults -g lightdm-gtk-greeter
```

Yes.. I have done that already ... and I am not bothered ... just intrigued that it has lasted for so long - and I also have been trying  for a workaround.

---

### Post by ventrical on 2012-03-17
Latest updates of lightdm and unity-greeter have created distortion screens beyond the pale. Apparently now .. snippets from old webpages from weeks ago.

I'll try to have my camera ready the next time.

---

### Post by mc4man on 2012-03-17
If you set up a triple boot you may get images from the afterlife

---

### Post by ventrical on 2012-03-17
> **mc4man said:**
> If you set up a triple boot you may get images from the afterlife


Please explain this theory. I actually have a quadruple boot system. 3 Precise and one stable Maveric. Did you not hypothesize that these multiple boots on GRUB had something to do with this overall bug?

---

### Post by mc4man on 2012-03-20
Supposedly fixed
[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/931967](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/931967)

Works here - all gone

---

### Post by ventrical on 2012-03-20
Yeah .. just got it .... just beautiful.  There is a phenomenon though. Just updating the one install (of three on the same HDD) has fixed all of them so I think it also was a GRUB issue in there also.

Thanks Ubuntu devs for this fix!!

---

### Post by bmbaker on 2012-03-20
well i guess we can mark this as solved :-) :-)

---

### Post by ventrical on 2012-03-20
> **bmbaker said:**
> well i guess we can mark this as solved :-) :-)
Thanks for keeping at it.

---

