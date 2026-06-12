---
title: "meizu Pro 5 support"
date: 2016-06-29
forum: Ubuntu Phone and Tablet
---

### Post by luckj on 2016-06-29
Just bought my Pro 5 flyme version and thinking of flashing Ubuntu touch asap but looking at the guide [HTML]https://developer.ubuntu.com/en/phone/devices/installing-ubuntu-for-devices/[/HTML] 
that looks nice and easy :D the meizu is not yet included into the list. 
I suppose that is the guide not properly updated but I appreciate if someone can confirm so I would be more confident to start with it. 

Thanks for any help 

luckj

---

### Post by luckj on 2016-07-01
I'm near to decide what to do and I guess I will follow the guide however is not clear to me the part related to the recovery. Seems that if I have to flash Ubuntu on a production phone (like the Pro 5 is)  I should flash also the related recovery image, the "turbo" for instance. The fact is that I cannot understand if I have to flash it at the end of the procedure,  when Ubuntu touch have been fully installed or during the flashing procedure. 

Are there someone who knows it? 

Thanks 
luckj

---

### Post by krusty8 on 2016-07-01
Generally, I'd say ubuntu-device-flash should provide a stable and foolproof enough operation, that you can just use it and either it will just work and you're on the new system, or it just fails and you still run your old system and you have to try something else.

More specifically, to the best of my understanding you want to put your device into bootloader mode and use the --bootstrap optiion which does install the right recovery, then, i think reboots and continues the installation from that recovery.

Of course I can't take on the responsibility and guarantee that there's no way to mess up your device, but rest assured, from one random anonymous person on the internet to another random person, I don't advise people to just go ahead and do dangerous things ;) That being said, as long as you have all the data you care about safely on the side, I don't see a reason why you shouldn't just try it.

Be sure to report back!

---

### Post by luckj on 2016-07-05
I'm totally aware about the risk there are inside this kind of activity especially as I'm a noob, even if quite aged :cool:. Actually I sold my nexus 6 to buy this PRO 5, for the only reason to try ubuntu touch on a supported device; in the past I had a Nexus 5 and I gave a try to UT using multirom and was fine at least for my daily usage then I think with this high end hardware should better.
During next few day I will forgot all concern and I will do it but even if the wiki is quite clear, what I cannot understand is why I cannot find any guide related to a single person who have tryed to follow this wiki indeed, there are several incomplete guides around and the most popular seems to be the one on XDA forum where this guy speaks about a procedure where you need 2 terminal sessions and at a certain point, when you see a specific message on the screen, you must press a combo very fast and "maybe" it works. This sounds really strange to me so I guess I will follow the ubuntu wiki eventually and I will report here of course.

---

### Post by krusty8 on 2016-07-05
I hear you :) Give it a shot. I haven't heard of anybody flashing their device into a truely unfixable state.

Yeah, pressing some keycombo really fast and maybe it works sounds strange. Link? The utmost I can think of in that situation is trying to boot into recovery or into bootloader mode. Smt like volume up plus power ... Or vol down and power .... The worst that would happen if you manage to be too slow or impatient is that you need to reboot the device again which would equate too you having lost some 10 seconds of your lifetime staring at a rebooting device.

Courage!

---

### Post by luckj on 2016-07-05
Here the link to the xda guide I mentioned [http://forum.xda-developers.com/meizu-pro-5/how-to/how-to-android-to-ubuntu-meizu-5-pro-t3396191]("http://forum.xda-developers.com/meizu-pro-5/how-to/how-to-android-to-ubuntu-meizu-5-pro-t3396191")

I'll keep you posted.

At the end I gave a try to the wiki guide without any luck since I was stucked at the start of the flash; I guess it's related to the bug 1455050 on launchpad.  I followed the xda guide but eventually I'm still using flyme. 
What I'm surprised about is that there is no supported guides by canonical since I was expecting that because this meizu is a retail phone running Ubuntu, the people who bought one should have been able to find an official support.

Anyway I will find a solution, I hope.  :-D

---

### Post by krusty8 on 2016-07-08
Can you paste all the exact commands and outputs? Which state was the device in? What was visible on the screen? Then maybe someone here can help you.

---

### Post by luckj on 2016-07-08
What I did was basically follow the wiki then, with the device in fastboot mode, (black scrren+meizu logo+at the bottom shown that the status was unlocked and unrooted) I checked if it was recognize by the PC with > sudo fastboot devices then I entered into the terminal the following
> ubuntu-device-flash touch --channel=ubuntu-touch/stable/ubuntu --bootstrap 
and I see
> 2016/07/17 22:52:19 Expecting the device to be in the bootloader... waiting

Nothing else happened for long time :confused:

I also tried with

> ubuntu-device-flash touch --channel ubuntu-touch/stable/ubuntu --bootstrap --recovery-image home/recovery.img 
where the recovery was the turbo.img

also changing the channel into /meizu.en but everytime stucked waiting that the device was recognize by ubuntu

---

### Post by krusty8 on 2016-07-08
You really have smt indicating *unrooted* on the bootloader screen?

Where did you take home/recovery.img from? Out of the ~/.cache/thatfolderwhereubuntudeviceflashcachesthedownloadedfiles ?

Pardon my ignorance, but is the Pro 5 the turbo?

What does the recovery that you have now (from flyme os) look like? Cwm ? Twrp? On my Nexus 7 it seems that the recovery installed by udf is a custom cwm. I recall using it at some point to check some logfiles in relation to udf operation. Have to find my notes.

One thing I'm thinking of now would be to install the recovery with fastboot. Smt like *fastboot flash recovery home/recovery.img*

---

### Post by luckj on 2016-07-08
Yes it is unlocked and unrooted. In order to unlock the meizu pro5 I find only one solution on XDA that basically consists in flashing a certain flyme stock daily bild  that can be unlocked via fastboot. 

I placed a copy of the recovery-turbo.img dowloaded from here [https://wiki.ubuntu.com/Touch/Devices]("https://wiki.ubuntu.com/Touch/Devices") into my home directory.

Yes the pro5 it's called turbo for ubuntu

It's the meizu stock recovery. It's a really basic recovery with 2 options: flash an update and erase data.

I was thinking the same, flash the recovery (turbo) via fastboot then reboot in fastboot mode and restart with the ubuntu-device-flash command but yesterday night after accepted that this way was not working I would gave a try to the xda forium guide [link]([http://forum.xda-developers.com/meiz...5-pro-t3396191](http://forum.xda-developers.com/meiz...5-pro-t3396191)) and I spent a cople of hours but with no luck as well. So I came back to my stock android meizu at the moment.

---

### Post by krusty8 on 2016-07-08
> **luckj said:**
> Yes it is unlocked and unrooted. In order to unlock the meizu pro5 I find only one solution on XDA that basically consists in flashing a certain flyme stock daily bild  that can be unlocked via fastboot. 


Ok. Got a link for those instructions as well? 

Are you really sure it is unlocked? I just wanna double check, because, well, firstly if the bootloader were still locked, that would be a valid explanation why your flashing doesn't work. Secondly, if you say that the unlock process itself depends on some specific daily build of an os, that sounds a bit fragile, so might warrant to verify somehow that it actually is unlocked. 

And lastly, I'm still a bit confused that you said:
> 
device **in fastboot** mode, (black scrren+meizu logo+at the bottom shown that the status was unlocked and **unrooted**) 


You said that the **fastboot** mode shows the device to be **unrooted**. I wouldn't actually have expected that the fastboot mode knows much of anything about the installed operating system and whether that is rooted or unrooted, or what that even means for that particular operating system, or how to detect that.

See, for example, on my Nexus 7 the bootloader screen shows "LOCK STATE - unlocked" as you can see e.g. in this video : [https://www.youtube.com/watch?v=EsebPBdQihw&t=204](https://www.youtube.com/watch?v=EsebPBdQihw&t=204)
(It's a bit shakey, but if you pause it you can read it - it looks exactly like this on my own device). My bootloader says that it is *unlocked* **and **you see that the booloader says** nothing about rooted or unrooted.** So, that's what's confusing me. 

Do you have a photo of your bootloader screen (cover the serial number) or find one online that looks exactly like yours?

> **luckj said:**
> 
I placed a copy of the recovery-turbo.img dowloaded from here [https://wiki.ubuntu.com/Touch/Devices](https://wiki.ubuntu.com/Touch/Devices) into my home directory.

Sounds good. That recovery should have adb as well, which could help.
> **luckj said:**
> 
Yes the pro5 it's called turbo for ubuntu

Clear.
> **luckj said:**
> 
It's the meizu stock recovery. It's a really basic recovery with 2 options: flash an update and erase data.

I was thinking the same, flash the recovery (turbo) via fastboot then reboot in fastboot mode and restart with the ubuntu-device-flash command but yesterday night after accepted that this way was not working I would gave a try to the xda forium guide [link]([http://forum.xda-developers.com/meiz...5-pro-t3396191](http://forum.xda-developers.com/meiz...5-pro-t3396191)) and I spent a cople of hours but with no luck as well. So I came back to my stock android meizu at the moment.

So, also that xda guide (of course) involves flashing recoveries. Initially a TWRP, that you're supposed to download from some website. Had you tried that? How did that go? How far into the xda guide did you get?

I'd definitely suggest to 
[LIST=1]
[*]double check the unlockedness situation and 
[*]try flashing the turbo recovery via fastboot. Afterall, I expect that you won't ever get further unless you get the turbo recovery onto the device via some means. And I believe that the fastboot command is the most low level means of doing it. (I think udf --bootstrap just wraps around fastboot. ) 
[/LIST]

---

### Post by luckj on 2016-07-09
> **krusty8 said:**
> Ok. Got a link for those instructions as well?
Are you really sure it is unlocked? I just wanna double check, because, well, firstly if the bootloader were still locked, that would be a valid explanation why your flashing doesn't work. Secondly, if you say that the unlock process itself depends on some specific daily build of an os, that sounds a bit fragile, so might warrant to verify somehow that it actually is unlocked.

And lastly, I'm still a bit confused that you said:


You said that the **fastboot** mode shows the device to be **unrooted**. I wouldn't actually have expected that the fastboot mode knows much of anything about the installed operating system and whether that is rooted or unrooted, or what that even means for that particular operating system, or how to detect that.


In the picture what the stock bootloader shows while the guide I mention is this [http://forum.xda-developers.com/meizu-pro-5/how-to/tutorial-unlock-bootloader-meizu-pro-5-t3303127]("http://forum.xda-developers.com/meizu-pro-5/how-to/tutorial-unlock-bootloader-meizu-pro-5-t3303127")

I was surprised that after unlock the bootloader all the data were not erased but this is confirmed also into the guide. I want to try again but this time wiping all data through the device settings. I did it through the flyme recovery last time, with the option clear data, but actually all pictures and music were still there.....

I tried from the beginning unlocking the bootloader and the 1st thing I find is that the bootloader is already unlocked after flashed the file update.zip :confused:
I set the usb debugging and do ```
adb devices
``` and it's fine
Reboot into fastboot and check ```
sudo fastboot devices
``` and it's fine
Flashed the recovery-turbo.img and reboot the devices to chech if it is fine and that's it
Reboot into fastboot mode then, in the terminal ```
ubuntu-device-flash touch --channel=ubuntu-touch/stable/ubuntu --bootstrap
``` Nothing happens
I tried with ```
sudo ubuntu-device-flash touch --channel=ubuntu-touch/stable/meizu.en --device turbo
``` I win an error message
```
2016/07/08 21:21:37 Device is |turbo|
2016/07/08 21:21:37 Flashing version 3 from ubuntu-touch/stable/meizu.en channel and server https://system-image.ubuntu.com to device turbo
2016/07/08 21:21:37 Target device cannot be reached over adb
```

mhmhmhm

---

### Post by krusty8 on 2016-07-09
> **luckj said:**
> In the picture what the stock bootloader shows while the guide I mention is this [http://forum.xda-developers.com/meizu-pro-5/how-to/tutorial-unlock-bootloader-meizu-pro-5-t3303127](http://forum.xda-developers.com/meizu-pro-5/how-to/tutorial-unlock-bootloader-meizu-pro-5-t3303127)

Ah, this thing: [http://i.imgur.com/AkqjrbW.png](http://i.imgur.com/AkqjrbW.png)
Indeed, it says unrooted. Ok.

> **luckj said:**
> I was surprised that after unlock the bootloader all the data were not erased but this is confirmed also into the guide. I want to try again but this time wiping all data through the device settings. I did it through the flyme recovery last time, with the option clear data, but actually all pictures and music were still there.....
I tried from the beginning unlocking the bootloader and the 1st thing I find is that the bootloader is already unlocked after flashed the file update.zip :confused:


Yeah, strange that it didn't really delete stuff, but then again, nothing here seems to be particularly pretty. Android/ARM at it's worst. Hacks piled on top of each other :(

I think the fact that it's unlocked, though is to be expected. You do that to the bootloader in the device. Once it is done, it doesn't undo itself again. Or anyway, it shouldn't. Not due to things like flashing roms, or wiping. Unless, I'm misinformed, which can never be ruled out :)

> 
I set the usb debugging and do ```
adb devices
``` and it's fine
Reboot into fastboot and check ```
sudo fastboot devices
``` and it's fine
Flashed the recovery-turbo.img and reboot the devices to chech if it is fine and that's it


Wait a minute. At this point you have the turbo recovery flashed? If you boot into the recovery, what does it look like? I don't have the recovery that was installed by udf anymore on my device, but if I remember correctly, it seems to have been a custom version of a clockworkmod (cwm) recovery. I think it showed an ubuntu icon on the screen and had a very small number of options you could cycle through with vol up/down. What's your recovery like at this point?

Most importantly: Can you access the device via adb WHILE in recovery?

If that is the case, then I don't think you need to use the ```
--bootstrap
``` option anymore. Because, to the best of my understanding, the purpose of that option is just to get the recovery onto the device. 

If you HAVE the turbo recovery AND adb access, then I think ```
ubuntu-device-flash touch
``` should just work. And if it doesn't, (which is to be expected, because otherwise we probably wouldn't have this conversation :P) my next best guess would be to open an ```
adb shell
``` and try to find the log file of the attempted installation on the device (can't find my notes:( ). My understanding was that udf copies a couple of files over to the device and then triggers a script that installs UT from these files.

Oh and I just remembered that udf has a ```
--verbose
``` flag.

So, in summary, I suggest:
[LIST=1]
[*]put it into turbo recovery 
[*]open an ```
adb shell
``` 
[*]have a look around, familiarize yourself with the folders. 
[*]run ```
ubuntu-device-flash --verbose touch
``` 
[*]try to find where the image files are on the device, and the script, and the log file. I think there was folders like, uhm, recovery?, cache?, temp?, or was it something with ubuntu in its name? If you can't find anything, you could just do a ```
adb shell ls -alR
``` and ```
adb shell ps aux
``` and copy/paste the output, maybe we catch the files and processes. 
[*]try to find out whether the script attempted an install, whether it produced a log and why it failed 
[/LIST]


> 
Reboot into fastboot mode then, in the terminal ```
ubuntu-device-flash touch --channel=ubuntu-touch/stable/ubuntu --bootstrap
``` Nothing happens

Well. You were here before, right? It didn't get any worse though *cough*, sorry :P

> 
I tried with ```
sudo ubuntu-device-flash touch --channel=ubuntu-touch/stable/meizu.en --device turbo
``` I win an error message
```
2016/07/08 21:21:37 Device is |turbo|
2016/07/08 21:21:37 Flashing version 3 from ubuntu-touch/stable/meizu.en channel and server https://system-image.ubuntu.com to device turbo
2016/07/08 21:21:37 Target device cannot be reached over adb
```


I think this one is clear. You are in bootloader mode. There is no adb. You are executing the udf command without --bootstrap, which means it tries to communicate over adb.

---

### Post by luckj on 2016-07-09
> Wait a minute. At this point you have the turbo recovery flashed? If you boot into the recovery, what does it look like? I don't have the recovery that was installed by udf anymore on my device, but if I remember correctly, it seems to have been a custom version of a clockworkmod (cwm) recovery. I think it showed an ubuntu icon on the screen and had a very small number of options you could cycle through with vol up/down. What's your recovery like at this point?

Actually here is the case in which 2 brains are more precise then one, especially when one (you) have knowledge of the matter. When I say that I boot into the recovery is not correct indeed I used the combo for the recovery (power+vol up) but it's clear now that it was not a recovery but something like a ubuntu's purple background with the orange ubuntu logo in the middle without any command to be done. Said that I'm asking myself what it, is since if I press power+vol down I have the meizu's bootloader screen.

> Most importantly: Can you access the device via adb WHILE in recovery?
May explain this? I really don't know what you mean. At least you mean I have to try ```
adb devices
``` while in recovery :(

What about if I try ```
sudo ubuntu-device-flash touch --channel=ubuntu-touch/stable/meizu.en --device turbo --bootstrap
``` ?

I never told that the daily flyme build it's working, except for the sim card :( so after every attempt I'm coming back through the TWRP to be stock international re configure my pro5 for my daily usage. I'm saying that because before to try catch the logs I have to take some time free during the coming week.

many thanks for you help till now krusty8

I'll keep you posted

---

### Post by krusty8 on 2016-07-09
> **luckj said:**
> something like a ubuntu's purple background with the orange ubuntu logo in the middle without any command to be done. Said that I'm asking myself what it, is since if I press power+vol down I have the meizu's bootloader screen.


Ookaay ..... photo? Video? Is there any interaction at all with this purple screen? Any reaction to touching the screen? Any reaction to vol up, down, power? How do you get out? By long-holding (5 seconds? 10? 20?) a vol-up or vol-down combination? Anything else worth mentioning?

> [quote]Most importantly: Can you access the device via adb WHILE in recovery?
May explain this? I really don't know what you mean. At least you mean I have to try ```
adb devices
``` while in recovery :(
[/quote]

Yes, that is *the first step *of what I meant :)

I'm not sure how familiar with adb and fastboot you are. Allow me to link a few videos showing the basics
 * [https://www.youtube.com/watch?v=vPth1owatwU](https://www.youtube.com/watch?v=vPth1owatwU)
 * [https://www.youtube.com/watch?v=YfWYKREeQeQ](https://www.youtube.com/watch?v=YfWYKREeQeQ)
 * [https://www.youtube.com/watch?v=1WcYXpFCjFs](https://www.youtube.com/watch?v=1WcYXpFCjFs) (this one becomes very Androidy after a few minutes, but I think the first couple minutes nicely point out that adb shell gives you a terminal access onto your device - think "telnet over usb" - you get a somewhat limited, but rather "normal" linux shell, you have ls, cd, cat, grep, maybe find, nano, etc, ...)
The videos are nothing special, just the best three out of the first ten that came up on top in my search engine. You would have no trouble finding a couple hundred more if you care. I don't want to spam or lecture you, but if you are unfamiliar with adb and fastboot you might want to skip through the videos. 

So, IF you have the turbo recovery installed, you SHOULD have adb access and that should allow you to open ```
adb shell
```. I hope that puts better into context what I had said before:
> **krusty8 said:**
> 
So, in summary, I suggest [...]


> 
What about if I try ```
sudo ubuntu-device-flash touch --channel=ubuntu-touch/stable/meizu.en --device turbo --bootstrap
``` ?
Well, again, *my understanding* is that you use ```
--bootstrap
``` **only **when the device is in** bootloader **mode. What ubunut-device-flash does then is installing the recovery. 

After it has installed the recover, it boots into this recovery and then proceeds in the same way as if you would have the recovery installed earlier **and** the device is in **recovery **mode **and **you run ubunut-device-flash **without** --bootstrap. What ubuntu-device-flash does then is install the system over the adb connection.

Makes sense?

> 
I never told that the daily flyme build it's working, except for the sim card :( so after every attempt I'm coming back through the TWRP to be stock international re configure my pro5 for my daily usage. I'm saying that because before to try catch the logs I have to take some time free during the coming week.

I kinda figured between the lines that you are flashing back and forth ;) Very committed!

 But, hang on, that also means you can reliably flash TWRP back onto the device, right? No purple screen then anymore? Do you have a link for the steps you go through for installing flyme? Maybe there is something interesting in there.

> 
many thanks for you help till now krusty8

I'll keep you posted
Welcome and please do! Good luck!

---

### Post by luckj on 2016-07-20
Starting from the beginning.
I would thank you for the you tube tutorial, I already knew some tips but there are a lot of new information for me, I would say almost over my knowledge capability :-k. 
I hadn't had time to go through all the steps but I can say that the device is every time accessible through adb command and also adb shell is available and also TWRP is every time flashable from fastboot so that's all fine.
Said that I have my pro5 ubuntu edition now thanks to this guide find into askubuntu thread [http://askubuntu.com/questions/767323/how-to-install-ubuntu-on-meizu-pro-5-that-was-originally-with-android]("http://askubuntu.com/questions/767323/how-to-install-ubuntu-on-meizu-pro-5-that-was-originally-with-android")
Basically I take both of the answer shown and now I have meizu ubuntu edition running with TWRP recovery, I don't know if this is really the same as the original ubuntu production device but I guess it is.
I stop the thread here because I would speak about my feelings with the systems but it should be OT.

So the main steps have been.

Factory reset with the stock Flyme
Enable usb debug
Flash the unlocked Flyme from here [http://forum.xda-developers.com/meizu-pro-5/how-to/tutorial-unlock-bootloader-meizu-pro-5-t3303127]("http://forum.xda-developers.com/meizu-pro-5/how-to/tutorial-unlock-bootloader-meizu-pro-5-t3303127")
Flash via fastboot the TWRP recovery [http://forum.xda-developers.com/meizu-mx/general/recovery-twrp-3-0-meizu-pro5-t3349888/post66148672#post66148672]("http://forum.xda-developers.com/meizu-mx/general/recovery-twrp-3-0-meizu-pro5-t3349888/post66148672#post66148672")
Full wipe with TWRP, including system, with option "use rm -f instead to formatting"  
Downloaded the system file from here [https://drive.google.com/folderview?id=0B-2xhhL1p3OtOWllRUtHODRYUEU&usp=sharing]("https://drive.google.com/folderview?id=0B-2xhhL1p3OtOWllRUtHODRYUEU&usp=sharing") then copied all into the TWRP folder into the device. This is the OTA11
TWRP flash for the kernel 
TWRP command line all the rest as explained inti the askubuntu page ahead

Next days we will see if also OTA 12 update will be running as it is

---

