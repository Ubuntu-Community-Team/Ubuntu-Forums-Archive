---
title: "HOWTO: Change the icons in the android application drawer"
date: 2011-02-23
forum: The Cafe
---

### Post by TheWeakSleep on 2011-02-23
I had searched for a few days to find this information, and decided to make it easy for all you would-be android customizers out there to find it as well. While this may be common knowledge for a lot of people, I'm hoping that this will help someone like me out somewhere along the line.

This is all done on a Samsung Captivate (2.2)

** Please note: to do this, you need root and you need to be able to sideload apps. You will also be changing system files so if you happen to accidentally brick your phone or make an application unusable, I will not be held responsible. You continue at your own risk. If you're uncomfortable with anything please make backups often, whether you use **[**Titanium Backup**]("https://market.android.com/details?id=com.keramidas.TitaniumBackup&feature=search_result")**, nandroid, or whatever.**

There are lots of ways to change the icons on your homescreen, so if you're content with that, check out Folder Organizer on the market. With that, lets get on with it.
**Step 1: The Setup**


We're going to need a few tools. First of all, grab the [Android SDK.]("http://developer.android.com")

After you've got that up and running, we also need [Ninjamorph]("https://market.android.com/details?id=stericson.ninjamorph.free&feature=search_result") and [Signapktic]("https://market.android.com/details?id=com.stericson.signapktic&feature=search_result") or [ZipSigner]("https://market.android.com/details?id=kellinwood.zipsigner&feature=search_result")I personally recommend Signapktic because ZipSigner can be a real pain (You have to type out the full path to the input file you want plus the path to the output file) but ZipSigner works fine. It's completely up to you.


Once you've got those applications up and running, theres a few things you should know about anroid applications if you don't already. First of all, most (all?) the system applications are found in /system/app and most (again, not sure if all) the applications you install from the market are found in /data/app. Each application will be a package with the extension .apk and all the resources are held within the archive. This wouldn't be a problem, theme wise, if it weren't for the fact that each pplication has to be digitally signed. Changing the contents of the archive breaks that and the application will no longer work (or even install).


**Step 2: Changing System Apps**


Get your icons ready! if you have a higher resolution screen, the icon should be found in /res/drawable-hdpi (or some variation of the name inside the .apk). For medium and low resolution screens they will be in /res/drawable-mdpi and /res/drawable-ldpi respectively. The icons should be 72x72 for hdpi, 48x48 for mdpi and i'm not sure about ldpi. 


We are goign to be changing system application's icons by using a different method than the market apps just because it is far easier to do so.


Open up NinjaMorph (the free version works perfectly, though it's an awesome app and always good to support the developers) and start a new project. The application will then prompt you to select an apk so navigate to /system/app and have a look at the applications that are there. Most of the time, the .apks aren't named too cryptically. For instance, if i wanted to change the icon for the Browser, i would select Browser.apk.


Once you have selected the application you want, you will see the contents of the package. Open up /res and navigate to the appropriate drawable folder. Find the icon you would like to change (a lot of the time it's named either icon.png , ic_launcher_application.png or application.png where application is the name.) and you'll be prompted to choose the icon you would like to replace it with.



That's it for system apps. Easy hey? The good news is that NinjaMorph automatically backs up any .apks or .jars that you work with to /sdcard/AndroidThemes so if you run in to trouble you can just push it back (More on that near the end). Oh, and not every app works. For instance I haven't been able to change the camera icon or the voice search icon (yet) so trial and error here, and I'll let you guys know if I manage to get them changed (and working).


**Step 3: Changing Market Apps**

Changing the icons for market apps is why I am writing this how to. I searched for a couple days for how to do it and I couldn't find a sure answer of how to do it. I had heard you needed to sign the .apk and push it to your device but couldn't figure out how to do it. There are tools available to do this but I've never been able to get any of them to work in Ubuntu and finding anything on xda is a pain.

SO let's get started. The first thing you're going to do locate the .apk of your choice. You could use something like root explorer on your phone, but we're going to use adb via your computer because, well, that's how I do it.


Make sure that you have USB debugging enabled on your phone and connect it via usb to your desktop. Navigate via the terminal to the platform-tools directory of the Android SDK. 

you can run:
```
./adb devices
```to see if your device is properly connected. If you get a "??????????? no permissions" error, unplug the phone and run:


```
./adb kill-server
sudo ./adb start-server
```run ```
./adb shell
``` to access the shell, become root, and navigate to /data/app.

Here you will see a list of the applications that you've installed via the android market. The naming conventions are a little trickier but MORE OFTEN THAN NOT the name of the application is in the name of the .apk (it happens where it's completely random :p) so for example, when I pulled Android Terminal Emulator .apk it's name was jackpal.androidterm-1.apk.


Now that you know where it is, exit the shell and run


```
./adb pull /data/app/com.example.application.apk
```which will pull the application from your device. You can specify a directory, else it will just be pulled into the working directory (the one with adb)


**You should keep a copy of this .apk**


Open the .apk, but don't extract it. Here you will see the familar layout, so navigate to where the icon is and replace it :) 


Copy the modified .apk onto your sd card and open it up in ZipSigner or Signapktic and sign away! :) if you skip this step, the application won't install! After the signing is complete (I always just use the default key but feel free to play around) uninstall the original application and reinstall the modified one, and you're done :) Not too hard hey? just an annoyingly long process. Like I said though, none of the tools I've seen have worked for me in Ubuntu (and I don't use any other OS)


**Step 4: Troubleshooting or 'How do I write to /system?'**

One thing that I've learned in the three or so weeks that I've had this phone is that changing system files doesn't always work out the way you plan. I mentioned earlier that I wasn't able to change the icons for the camera or voice search. That's not entirely true, I was able to change them, however everytime I launched the application it would force close on me. That's never a good thing especially when it's something builtin like the camera or voice search :p So what do you do? You can't exactly uninstall and reinstall them like you can with a market application. My first instinct was to just grab the backup and install the backup over the modified one.


That didn't work out. The Camera.apk always failed to install and for whatever reason the voice search kept reverting back to the modified one upon restart. When I learned that, I decided to push it back to /system/app using adb however THAT didn't work either! (read only file system) so the only thing I could do is mount /system and do it that way. I moved the original Camera.apk to /sdcard and here is exactly how I installed it:


```
mount -o rw,remount -t yaffs2 /dev/block/mtdblock3 /system
```and:


```
[COLOR=#111111]cat /sdcard/Camera.apk > /system/app/Camera.apk[/COLOR]
```[COLOR=#111111]
[/COLOR]
[COLOR=#111111]**I can't promise that will work for everyone.**[/COLOR]

[COLOR=#111111]Before: [/COLOR]
[COLOR=#111111]
[/COLOR]
[COLOR=#111111][[IMG]http://farm6.static.flickr.com/5016/5470949296_e71526b60f_s.jpg[/IMG]]("http://farm6.static.flickr.com/5016/5470949296_e71526b60f_b.jpg")[/COLOR]
[COLOR=#111111]
[/COLOR]
[COLOR=#111111]After:[/COLOR]
[COLOR=#111111]
[/COLOR]
[COLOR=#111111][[IMG]http://farm6.static.flickr.com/5057/5470356489_597122d8f2_s.jpg[/IMG]]("http://farm6.static.flickr.com/5057/5470356489_597122d8f2_b.jpg")[/COLOR]


As you can see, I'm using Faenza. I'm a fan of consistency, what can I say? If anyone is interested in helping me make some android-specific icons to fit with Faenza I'd appreciate it. I suck at it haha! Also, if anyone has any questions or know of a better way to do it and want to laugh at me for being a noob, shoot me a message or a comment in this thread. I'll update tomorrow with more screenshots if you want some for the walkthrough. Hope this helps someone! And don't be afraid to play around a bit! You can change more than just the icons! I've seen some really elegant widgetlocker mods and the like. I'd just like to reiterate however:




**I am not responsible for any damage done to your device. You do this at your own risk.**

---

