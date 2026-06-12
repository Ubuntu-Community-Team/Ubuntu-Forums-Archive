---
title: "ATI Catalyst 9.1 + WINE = Awesome"
date: 2009-01-30
forum: The Cafe
---

### Post by Vince4Amy on 2009-01-30
Just installed the new ATI drivers and WINE and I have to say it is probably the most awesome driver update ever! 

All my Windows games that work with WINE now have great FPS, on par or faster than Windows, this is absolutely awesome. Anyone else tried these yet?

---

### Post by Zero Prime on 2009-01-30
Downloading now.  Thanks for the info.

---

### Post by Baby Boy on 2009-01-30
Didn't even know about this, I'll definitely give it a try. I have the default drivers installed (8.4 I think), how much of an improvement would you say these are?

---

### Post by handy on 2009-01-30
I just tried to get 9.2 beta on Arch but they aren't good for 64bit yet. :-(

Great to hear that AMD have made good progress though, that's for sure. :-D

---

### Post by mihai.ile on 2009-01-30
interesting...

I am used to see topics like "ati dirvers suck, nvidia drivers crashing, x errors with intel", and now I see ati awsome, nvidia rocks.... great news...

---

### Post by Zero Prime on 2009-01-30
Even better than WINE, Composite rendering and video play back works with no flickering!!!!!!!!!!!!!!!!!!!!!

Now I can have Compiz or Gnome compositing on and watch video!!  I'm happy now.

---

### Post by blazemore on 2009-01-30
Any info on the gaming performance of Wine with the new Nvidia 180 driver?

---

### Post by Baby Boy on 2009-01-30
How do I install this driver? I can't run the ".run" file. Help. :(

---

### Post by Neural oD on 2009-01-30
also interested in peoples take on the nvidia driver under wine

---

### Post by zika on 2009-01-30
> **Zero Prime said:**
> Even better than WINE, Composite rendering and video play back works with no flickering!!!!!!!!!!!!!!!!!!!!!

Now I can have Compiz or Gnome compositing on and watch video!!  I'm happy now.
HD3650: now I can set video to xv and get no flicker but in not-full-screen picture is shifted down 1/2 of the player window ... ;( so, still with X11 on video.

---

### Post by binbash on 2009-01-30
I didn't try with wine yet but it fixes a lot of problems (video flicker etc).

---

### Post by zika on 2009-01-30
> **handy said:**
> I just tried to get 9.2 beta on Arch but they aren't good for 64bit yet. :-(
Great to hear that AMD have made good progress though, that's for sure. :-D
would You elaborate on this. what's new in 9.2? what's the problem with 6.4? I have HD3650.

---

### Post by handy on 2009-01-30
> **zika said:**
> would You elaborate on this. what's new in 9.2? what's the problem with 6.4? I have HD3650.

I saw this thread & went looking for the latest in the Arch AUR repo's, which happen to be 9.2.  But they need a patch or something before they will work on Arch 64bit, which is what I use.

I haven't done a search & read up on them; I'm just impressed with the positive responses coming into this thread.  As the ATi drivers have been quite poor on Linux.

---

### Post by zika on 2009-01-30
> **handy said:**
> I saw this thread & went looking for the latest in the Arch AUR repo's, which happen to be 9.2.  But they need a patch or something before they will work on Arch 64bit, which is what I use.

I haven't done a search & read up on them; I'm just impressed with the positive responses coming into this thread.  As the ATi drivers have been quite poor on Linux.
thanks.

---

### Post by Vince4Amy on 2009-01-30
> How do I install this driver? I can't run the ".run" file. Help.

If you're on Ubuntu 8.04 or 8.10 all you have to do is:

```
sudo sh drivename.run
```

Follow all the automatic steps and then do:

```
sudo aticonfig --initial -f
```

Then reboot.

---

### Post by zika on 2009-01-30
> **Vince4Amy said:**
> If you're on Ubuntu 8.04 or 8.10 all you have to do is:

```
sudo sh drivename.run
```Follow all the automatic steps and then do:

```
sudo aticonfig --initial -f
```Then reboot.
don't forget ```
sudo chown +x drivername.run ... ;)
```

[COLOR=Red]**update:[COLOR=Black] I made a typo. it's not chown but chmod ... :)[/COLOR]**[/COLOR]

---

### Post by Vince4Amy on 2009-01-30
> don't forget
Code:

sudo chown +x drivername.run ... ;)

I've never done that. What is the need to?

---

### Post by Skripka on 2009-01-30
Do they support anything more than DirectX 7 mode on Steam games yet?  I'm curious.

---

### Post by zika on 2009-01-30
> **Vince4Amy said:**
> I've never done that. What is the need to?
in my case (three times now, 8.11,8.12.9.01) after a download driver.run doesn't have privilege to be run. this command just gives it that privilege. nothing fancy but can make a problem. it's unix ... ;)

---

### Post by forrestcupp on 2009-01-30
> **zika said:**
> don't forget ```
sudo chown +x drivername.run ... ;)
```

Well, that's the other way to do it.  But if you run it with **sh**, you don't need to set it's executable permissions.

I'm glad to see they finally got around to fixing the flickering problem.  Maybe now we don't have to be forced to buy nvidia.

---

### Post by Go_Bucks on 2009-01-30
I thought the OpenGL support in 9.1 was supposed to fix the Google Earth screen flickering issue. I am surprised and disappointed to see that the problem still exists.

---

### Post by zika on 2009-01-30
> **forrestcupp said:**
> Well, that's the other way to do it.  But if you run it with **sh**, you don't need to set it's executable permissions.
on my (and some others, according to threads) *sh* is not enough. I say this not in order to compete but just for sake of those who obviously had problems with just *sh*... not a big deal but for some a stopper ... ;)

---

### Post by Zero Prime on 2009-01-30
There is the easy way.  Right click on the .run icon and select properties.  Under the permissions tab click on the make executable block.  Then run in terminal with sudo.

---

### Post by zika on 2009-01-30
> **Zero Prime said:**
> There is the easy way.  Right click on the .run icon and select properties.  Under the permissions tab click on the make executable block.  Then run in terminal with sudo.
terminal is always the easiest way ... :) I remember times when we did not have mouses ... ;)

---

### Post by forrestcupp on 2009-01-30
> **zika said:**
> on my (and some others, according to threads) *sh* is not enough. I say this not in order to compete but just for sake of those who obviously had problems with just *sh*... not a big deal but for some a stopper ... ;)

Oh.  I didn't know people were having that problem with this.  Sorry.

---

### Post by Zero Prime on 2009-01-30
> **zika said:**
> terminal is always the easiest way ... :) I remember times when we did not have mouses ... ;)

Not always.  Like some users have said, others have had trouble with this and newer users don't know all those commands.  I never could get the drivers installed using any of the above stated methods.  I only had luck with how I mentioned above.  Besides, a few clicks is easier than a bunch of typing, that is why we have a GUI :)

---

### Post by DOS4dinner on 2009-01-30
Would this do anything for an ATI Radeon 9800?

---

### Post by gloscherrybomb on 2009-01-30
> **zika said:**
> HD3650: now I can set video to xv and get no flicker but in not-full-screen picture is shifted down 1/2 of the player window ... ;( so, still with X11 on video.

This is a known bug, and should be fixed within the next couple of releases. They have only just managed to get composite videos to work, now they will try to fix all these bugs which have unsurprising popped up. It is certainly improving though.

---

### Post by mister_pink on 2009-01-30
When I saw the title of this thread I thought someone had tried to install the windows driver in Wine! I was just going to say that won't get you very far!

Nice to see the drivers improving though. When my old Radeon 9700 packed up a while ago I replaced it with a nvidia card because I knew their drivers were that much better.

---

### Post by jlx on 2009-01-30
ATI Radeon HD 3850. No video flickering with xv, but system crash going full screen and google earth flickering.
Hope AMD/ATI is on the right way to fix all issues and make ati cards usable on Ubuntu.

---

### Post by DrakeGis on 2009-01-30
I don't use WINE. But I agree, finally it is good to be able to reproduce video without having to disable compiz. However, it is very sad that I still need to do that to use google earth.

A mediocre update.

Update: See also the "effects" when using miro (old video over the buttons) and chesse (half of the screen is black), it also do funny things when resizing videos with totem.

---

### Post by Vince4Amy on 2009-01-31
Yes, I think that ATI have done a very good job this time. Definitely on of the best versions they've released so far.

---

### Post by Nostrafus on 2009-01-31
Good to hear they've improved the support on ATI cards, I remember a few years ago having tons of problems with ATI cards and games under Linux, especially with anything 3D, stuff getting rendered as grey blobs, simple games crashing, things like that.

Right now I'm having absolutely no luck with my setup for gaming, I have yet to get a single game to run out of the dozens I've tried, but I'm running 2 Nvidia cards and that's caused more than it's fair share of problems since I updated to 8.10. Such is my luck.

---

### Post by theApokalypsis on 2009-01-31
it was a decent update. but still some issues to be addressed. hopefully the next release makes things even more stable.

although having compiz and accelerated playback is great.

---

### Post by bigbrovar on 2009-01-31
can any one confirm if this is stable enough to install on a production system? .. i work in a school where the students are giving laptops that run ubuntu .. its my job to configure this laptops. for this i made a preconfigured ubuntu image using system imager. i am in the process of making a new image based on ubuntu 8.10 and i was wondering if its ok to install the latest version of ATI card or just use the one in the repo..

---

### Post by Vince4Amy on 2009-01-31
> **bigbrovar said:**
> can any one confirm if this is stable enough to install on a production system? .. i work in a school where the students are giving laptops that run ubuntu .. its my job to configure this laptops. for this i made a preconfigured ubuntu image using system imager. i am in the process of making a new image based on ubuntu 8.10 and i was wondering if its ok to install the latest version of ATI card or just use the one in the repo..

What version are you currently running? I've found releases 8.11 - 8.12 to be very unstable in comparison.

---

### Post by bigbrovar on 2009-01-31
> What version are you currently running? I've found releases 8.11 - 8.12 to be very unstable in comparison. 
Am using the open source version that comes default with intrepid ibex .. i i didnt install the restricted driver. my target is stability.. am not concerned about 3D acceleration. infact i uninstalled compiz. One of the reasons i decided to base the image on ibex is because the the last hardy image was very unstable and usually restart for know reason (i tracked the problem down to the ATI restricted driver) what i just need is a stable system (for the student's sake, its their first introduction to ubuntu). what ever achieves it. proprietary or open source driver which ever achieves it.

---

### Post by zika on 2009-01-31
> **bigbrovar said:**
> Am using the open source version that comes default with intrepid ibex .. i i didnt install the restricted driver. my target is stability.. am not concerned about 3D acceleration. infact i uninstalled compiz. One of the reasons i decided to base the image on ibex is because the the last hardy image was very unstable and usually restart for know reason (i tracked the problem down to the ATI restricted driver) what i just need is a stable system (for the student's sake, its their first introduction to ubuntu). what ever achieves it. proprietary or open source driver which ever achieves it.
if I were in Your shoes I'd stay with open source version. even though this latest version of ATI proprietary driver seems to be very good, latest kernel update proved me that in Your case I'd stay with open source and be sure that any further kernel update would go uneventful. now I'm wiser and would be more relaxed in case of such an update (knowing what to do and what to expect from proprietary driver and how to re-install it) with open-source driver for inexperienced users and if You do not use compiz and acceleration. added bonus is that they can not play with compiz even if it were installed ...  :)
it's different having just one machine to take care of and, in Your case, more ...

---

### Post by bigbrovar on 2009-01-31
> **zika said:**
> if I were in Your shoes I'd stay with open source version. even though this latest version of ATI proprietary driver seems to be very good, latest kernel update proved me that in Your case I'd stay with open source and be sure that any further kernel update would go uneventful. now I'm wiser and would be more relaxed in case of such an update (knowing what to do and what to expect from proprietary driver and how to re-install it) with open-source driver for inexperienced users and if You do not use compiz and acceleration. added bonus is that they can not play with compiz even if it were installed ...  :)
it's different having just one machine to take care of and, in Your case, more ...

thanks bro .. just what i thought

---

### Post by Vince4Amy on 2009-01-31
> if I were in Your shoes I'd stay with open source version. even though this latest version of ATI proprietary driver seems to be very good, latest kernel update proved me...

Always install any updates prior to installing these drivers. Also to prevent this happening again lock the Kernel version after you've upgraded but before you've installed the drivers. Though you can simply reinstall the driver after a kernel update.

---

### Post by zika on 2009-01-31
> **Vince4Amy said:**
> Always install any updates prior to installing these drivers. Also to prevent this happening again lock the Kernel version after you've upgraded but before you've installed the drivers. Though you can simply reinstall the driver after a kernel update.
I'm not complaining, I have time and will to tinker with Ubuntu and I love it (both Ubuntu and the new version of driver). in case of maintaining a bunch of students' computers (beside taking care of themselves ...), I am afraid, I wouldn't ... ;) that's the reason I gave advice as such ... :lol:

---

### Post by zika on 2009-01-31
> **bigbrovar said:**
> thanks bro .. just what i thought
I'm and educator myself and I admire what You are doing ... keep up...!

---

### Post by bigbrovar on 2009-01-31
> **Vince4Amy said:**
> Always install any updates prior to installing these drivers. Also to prevent this happening again lock the Kernel version after you've upgraded but before you've installed the drivers. Though you can simply reinstall the driver after a kernel update. thanks but my focus more than anyting is stability more than 3D acceleration.. and it seems the open source driver is more stable than the proprietary version.. that is why am sticking to the open-source version.

---

### Post by Vince4Amy on 2009-01-31
I wasn't saying anything against using the OSS driver, I was just posting instructions for those who are affected by Kernel updates.

---

### Post by zika on 2009-01-31
> **Vince4Amy said:**
> I've never done that. What is the need to?
You were right in one thing: neither have I done that. it should read:```
 sudo chmod +x ati-driver-installer-9-1-x86.x86_64.run
```
sorry ... :)

---

### Post by zika on 2009-01-31
> **Vince4Amy said:**
> I wasn't saying anything against using the OSS driver, I was just posting instructions for those who are affected by Kernel updates.
Your advice on locking the kernel version was a very sound one. thank You.

---

### Post by DM2126@mac.com on 2009-12-24
This is the message I get when trying to install the ATI Catalyst 9.1 driver. I use Ubuntu 9.1 and Wine.

Archive:  /home/dennis/.wine/dosdevices/c:/Program Files/DexCom/DexCom DM3 11.0.0.9/DexCom.DataManager.exe
[/home/dennis/.wine/dosdevices/c:/Program Files/DexCom/DexCom DM3 11.0.0.9/DexCom.DataManager.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/dennis/.wine/dosdevices/c:/Program Files/DexCom/DexCom DM3 11.0.0.9/DexCom.DataManager.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/dennis/.wine/dosdevices/c:/Program Files/DexCom/DexCom DM3 11.0.0.9/DexCom.DataManager.exe or
          /home/dennis/.wine/dosdevices/c:/Program Files/DexCom/DexCom DM3 11.0.0.9/DexCom.DataManager.exe.zip, and cannot find /home/dennis/.wine/dosdevices/c:/Program Files/DexCom/DexCom DM3 11.0.0.9/DexCom.DataManager.exe.ZIP, period.




Help!

Sorry that is the message for another program. This is the one for the ATI driver.
Archive:  /home/dennis/Downloads/9-12_xp32_dd_ccc_wdm_enu.exe
[/home/dennis/Downloads/9-12_xp32_dd_ccc_wdm_enu.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/dennis/Downloads/9-12_xp32_dd_ccc_wdm_enu.exe or
          /home/dennis/Downloads/9-12_xp32_dd_ccc_wdm_enu.exe.zip, and cannot find /home/dennis/Downloads/9-12_xp32_dd_ccc_wdm_enu.exe.ZIP, period.

---

### Post by starcannon on 2009-12-24
Try asking in [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331"), I think you'll get more response.
[IMG]http://img94.imageshack.us/img94/3930/zombiegq.jpg[/IMG]

---

