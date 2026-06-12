---
title: "Rooting Android"
date: 2011-04-26
forum: The Cafe
---

### Post by moore.bryan on 2011-04-26
Just wondering if anyone's tried rooting their Android phone without access to Windows. I have no access to Windows whatsoever, by am interesting in rooting my LG Optimus V and am wondering if someone else has already blazed a trail.

Thanks, community!

---

### Post by tgm4883 on 2011-04-26
I rooted my evo with [unrevoked]("http://unrevoked.com/")

---

### Post by earthpigg on 2011-04-26
there's a mono program i came across a while back, with the .exe running with perfect nativity on ubuntu.

but, alas, the 2.2.2 update broke that root method for Sprint users.

EDIT: [link. ]("http://forum.xda-developers.com/showthread.php?t=803682")

---

### Post by moore.bryan on 2011-04-26
> **tgm4883 said:**
> I rooted my evo with [unrevoked]("http://unrevoked.com/")
That looks like what I'm looking for, but doesn't work for the LG Optimus line... :-(

Thanks, though!

---

### Post by moore.bryan on 2011-04-26
The LG Optimus V from VM still runs 2.2.1... any ideas where you found that program?

---

### Post by tgm4883 on 2011-04-26
> **moore.bryan said:**
> The LG Optimus V from VM still runs 2.2.1... any ideas where you found that program?

Probably from the link he posted

---

### Post by moore.bryan on 2011-04-26
Ah, thanks for that... didn't refresh the page to see the edit.

---

### Post by Donalt2010 on 2011-04-26
Try AmonRa. Havent used it myself, used UnRevoked though.

---

### Post by moore.bryan on 2011-04-26
> **earthpigg said:**
> EDIT: [link. ]("http://forum.xda-developers.com/showthread.php?t=803682")
Hmm... the zip file won't open; too many errors.

> **Donalt2010 said:**
> Try AmonRa. Havent used it myself, used UnRevoked though.
Searched around--briefly--and couldn't find any howto's... any ideas where I could find one?

---

### Post by Donalt2010 on 2011-04-26
Have you tried Android forums, they are usually helpful over there. [http://androidforums.com/lg-optimus-v/](http://androidforums.com/lg-optimus-v/)

---

### Post by PuddingKnife on 2011-04-26
I've been trying to root my Epic for a while now, so consider this post a bookmark.

---

### Post by Donalt2010 on 2011-04-26
> **PuddingKnife said:**
> I've been trying to root my Epic for a while now, so consider this post a bookmark.

Try Android forums buddy.

---

### Post by moore.bryan on 2011-04-26
SuperOneClick starts just fine, but hangs while chmod-ing something. Any other ideas?

---

### Post by Donalt2010 on 2011-04-26
Tbh i'm no expert in flashing roms/rooting etc. I usually follow guides on Android forums or xda. Although the members of xda dont like to help noobs or help when questions are repeated usually. Register on Android forums and ask in there dude. Sorry i cant be more help:-)

---

### Post by Dustin2128 on 2011-04-26
> **earthpigg said:**
> there's a mono program i came across a while back, with the .exe running with perfect nativity on ubuntu.

but, alas, the 2.2.2 update broke that root method for Sprint users.

EDIT: [link. ]("http://forum.xda-developers.com/showthread.php?t=803682")
What? You need to find exploits or workarounds to root android phones? And here I thought that was just for iphone jailbreaks...

---

### Post by moore.bryan on 2011-04-26
> **Donalt2010 said:**
> Have you tried Android forums, they are usually helpful over there. [http://androidforums.com/lg-optimus-v/](http://androidforums.com/lg-optimus-v/)

That's where I was headed next. I've already looked through the xda-dev pages and most of the Android forums; most of those posts revolve around Windows, so I thought this would be a more useful place.

---

### Post by PhillyPhil on 2011-04-26
> **Dustin2128 said:**
> What? You need to find exploits or workarounds to root android phones? And here I thought that was just for iphone jailbreaks...

iPhones need to be jailbroken to install unapproved apps.  Android has a tick box instead.  That's the origin of what you were thinking of. 
Google doesn't put out updates like Apple does to target the latest jailbreak method (although some OEMs do), or try to have jailbreaking ruled illegal in the US like Apple did. 

A little different for every phone, but to root Nexus One:
1. preparation
2. unlock bootloader
3. root

1. Preparation
- make sure this is on in your phone: settings -> applications -> development -> usb debuggging
- add the following two lines to this file on your computer:/etc/udev/rules.d/51-android.rules 
SUBSYSTEM=="usb", SYSFS{idVendor}=="18d1", MODE="0666"
SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666"
- make sure you have read and execute permissions for the file: sudo chmod a+rx /etc/udev/rules.d/51-android.rules
- get fastboot here: [http://www.romraid.com/paul/fastboot.zip](http://www.romraid.com/paul/fastboot.zip)
- check the phone Build Number in Settings > About Phone
- go here and get the superboot image for your build: [http://android.modaco.com/content/google-nexus-one-nexusone-modaco-com/298782/12-feb-erd79-ere27-ere36b-superboot-rooting-the-nexus-one/](http://android.modaco.com/content/google-nexus-one-nexusone-modaco-com/298782/12-feb-erd79-ere27-ere36b-superboot-rooting-the-nexus-one/) 

2. Unlock bootloader ### THIS STEP WIPES YOUR APPS -- backup first ###
- turn the phone off, start while holding trackball, to boot into bootloader
- Plug the phone into your computer with the usb cable
- extract fastboot and run: sh ./fastboot-linux oem unlock
- select yes on the phone.
- bootloader is unlocked. your phone will display an open lock at boot time. 

3. Root
- boot phone into bootloader as above, then plug phone in
- extract superboot and then run: sh ./install-superboot-linux.sh
- rooted. the superuser app will be in your installed apps.

Note root can be lost by an update, but the bootloader will remain unlocked.

---

### Post by SilverDragon on 2011-04-26
I used z4root on my Droid X. I downloaded and installed it from my phone and it worked flawlessly. It was removed from the market but finding a download link wasn't too hard. Strangely my windows machine blocked it claiming it was a virus. I'm still not sure what that was about. Good luck rooting your phone.

Any reason in particular you want to be rooted? I had mine rooted for a while for wireless tethering but currently running an unrooted gingerbread leak.

---

### Post by moore.bryan on 2011-04-27
I muddled my way through this last night and plan on posting how I did it later today... if work cooperates and doesn't keep its strangle-hold on my life! ;-)

@SilverDragon: As with Linux, I just wanted to be able to do it. :-P

---

### Post by MooseDog on 2011-04-27
depends also on your phone, if it's "friendly" to the rooting community:

[http://unrevoked.com/rootwiki/doku.php/public/root_friendly](http://unrevoked.com/rootwiki/doku.php/public/root_friendly)

i also found the android sdk to be very useful, and it's linux compatible too!

[http://developer.android.com/index.html](http://developer.android.com/index.html)

---

### Post by TeoBigusGeekus on 2011-04-27
> **tgm4883 said:**
> I rooted my evo with [unrevoked]("http://unrevoked.com/")

Thanks for this... I just rooted my desire - piece of cake.

---

### Post by moore.bryan on 2011-04-27
First, a disclaimer: **don't do this**. No, seriously, it could brick your phone and cause small puppies in Siam to suffocate for no apparent reason. 

Also, this guide is designed for the LG Optimus V and, therefore, some of the links are specific to that model (i.e., the "recovery stuff"); however, the principles are the same for most phones.

This covers the *rooting* of the phone, not the installation of ROMs... perhaps that will come later.

[LIST=1]
[*]Download the [Android SDK]("http://dl.google.com/android/android-sdk_r10-linux_x86.tgz"), fastboot from the [HTC Developer Center]("http://developer.htc.com/adp.html") (to find the file, just scroll down the page to it),  and [recovery stuff]("https://docs.google.com/leaf?id=0B094hoaCX7goOTg2MDAxMzgtNTlhOC00ZGM2LWFkYmQtNjg0M2I3MGRkNmVh&sort=name&layout=list&num=50").
[*]Unzip/unpack all the assorted things you just downloaded.
[*]Enter the "tools" directory in your unpacked Android SDK and run "android."
[*]Once the "Android SDK and AVD Manager" loads, you need to install the "Android SDK Platform-tools" package under "Available packages."
[*]Close-out the Manager, copy the fastboot file and the boot.img, recovery.img, and system.img files from the recovery stuff zip file into the "platform-tools" directory in the Android SDK directory you previously unpacked.
[*]Connect your Android phone to your computer, head to Settings > Applications > Development, and turn-on "USB Debugging."
[*]In the terminal, cd into your previously unpacked Android SDK directory and into the "platform-tools" directory.
[*]Become a superuser (sudo su) and enter "./adb root".
That will start the ADB tool in root (really important and, I know, pretty obvious).
[*]If all went well, nothing should really happen; enter "./adb devices", which should list a device connected, your phone.
[*]Now it's time to reboot your phone into the bootloader with "./adb reboot bootloader". At this point, you may notice your phone's screen go blue; don't worry, that's actually what it should do.
[*]Once in bootloader, you can flash your device with the recovery files:
```

fastboot erase system
fastboot erase boot
fastboot erase recovery
fastboot erase userdata
fastboot flash recovery recovery.img
fastboot flash boot boot.img
fastboot flash system system.img
fastboot reboot

```
[/LIST]
If all went well, you've rooted your Android without any icky Windows touching.

---

### Post by aysiu on 2011-04-27
> **moore.bryan said:**
> Just wondering if anyone's tried rooting their Android phone without access to Windows. I have no access to Windows whatsoever, by am interesting in rooting my LG Optimus V and am wondering if someone else has already blazed a trail.

Thanks, community!
I rooted my Android phones multiple times using Mac OS X and Ubuntu. Never Windows. I don't think you need Windows to root.

---

### Post by HappinessNow on 2011-04-27
> **aysiu said:**
> I rooted my Android phones multiple times using Mac OS X and Ubuntu. Never Windows. I don't think you need Windows to root.

To root you actually don't need Windows, OS X or even a Linux based distro...you only need the xScope Browser installed on your phone

I have rooted two Nexus Ones, one last year using Super One-Click and one earlier this week using GingerBreak

It honestly is not as difficult as everyone appears to make it out to be but with that said you should only proceed if you know what your doing and make backups before proceeding.

The best forums for anything Android is XDA, this is well known in Android Dev circles...

if you are on Android 2.3.3 follow the instructions using GingerBreak found on the XDA forums [here]("http://goo.gl/2shDG")

> Here is what I did:

- Make sure USB debugging is enabled [COLOR="SeaGreen"]---Check[/COLOR]
- Make sure you have an SD card (formatted and) inserted [COLOR="SeaGreen"]---SD Card inserted when I received new Nexus One from BrightStar (Android Dev. Supplier)[/COLOR]
- Get the APK on the phone somehow, and install it [COLOR="SeaGreen"]--- installed xScope browser, navigated to [this thread]("http://goo.gl/XmivG"), downloaded v1.10, opened it[/COLOR]
- Open the APK, press the root button [COLOR="SeaGreen"]---pressed "root"[/COLOR]
- Wait a few minutes. If there are no problems, the device will reboot [COLOR="SeaGreen"]---device rebooted and rooted[/COLOR]
- Make sure the Superuser app is install and working [COLOR="SeaGreen"]---installed Superuser, ROM Manager (Premium) and Titanium Backup[/COLOR]
- Optional: Uninstall GingerBreak, you don't need it on your phone anymore [COLOR="SeaGreen"]---uninstalled GingerBreak[/COLOR]

[COLOR="SeaGreen"]--- installed CyanogenMod 7 Nightly N1[/COLOR][http://goo.gl/98XtP](http://goo.gl/98XtP)

I have since installed CyanogenMod 7.0.1.2 N1, on both the brand new Nexus one and the one I rooted last year.

Please note the above directive is for rooting Gingerbread, on the older model I rooted using [Super One-Click]("http://goo.gl/KToaz") last year.

Do your research and I suggest referring to the XDA forums for more in depth support.

For the OP XDA has forums for LG Optimus V found [here]("http://goo.gl/pI6gk")

---

### Post by aysiu on 2011-04-28
> **HappinessNow said:**
> To root you actually don't need Windows, OS X or even a Linux based distro...you only need the xScope Browser installed on your phone

I have rooted two Nexus Ones, one last year using Super One-Click and one earlier this week using GingerBreak

It honestly is not as difficult as everyone appears to make it out to be but with that said you should only proceed if you know what your doing and make backups before proceeding.

The best forums for anything Android is XDA, this is well known in Android Dev circles...

if you are on Android 2.3.3 follow the instructions using GingerBreak found on the XDA forums [here]("http://goo.gl/2shDG")

[http://goo.gl/98XtP](http://goo.gl/98XtP)

I have since installed CyanogenMod 7.0.1.2 N1, on both the brand new Nexus one and the one I rooted last year.

Please note the above directive is for rooting Gingerbread, on the older model I rooted using [Super One-Click]("http://goo.gl/KToaz") last year.

Do your research and I suggest referring to the XDA forums for more in depth support.

For the OP XDA has forums for LG Optimus V found [here]("http://goo.gl/pI6gk")
The rooting process varies from phone to phone. I can assure you can't permaroot a MyTouch 4G with just xScope.

---

### Post by HappinessNow on 2011-04-28
> **aysiu said:**
> The rooting process varies from phone to phone. I can assure you can't permaroot a MyTouch 4G with just xScope.

In the linked XDA forum thread there is discussion of what works and what does not work with this exploit...before anybody makes the jump to root do your research thoroughly...

I will highlight and re-quote what I said above:

> [COLOR="Red"]Do your research and I suggest referring to the XDA forums for more in depth support.
[/COLOR]...and more in-depth research

There are many different Android models that just any "one" solution will not work for all devices, this I trust is understood clearly without having to be restated.

Also please note there is a new version of GingerBreak: [GingerBreak-v1.20.apk (295.2 KB)]("http://goo.gl/hQscM")

---

### Post by thecamelcoder on 2011-04-28
Hey mate, here is the one stop shop for all you'll need to root your phone

[[Video] Root Your Android]("http://www.linux-geek.co.nz/2011/04/28/video-how-to-root-your-android-device-z4mod-method/")

---

### Post by moore.bryan on 2011-04-28
Thanks for everyone's assistance. All the howto's about the LG Optimus V only show how to do this via Windows and that wasn't an option for me. The method I outlined above worked *perfectly* for me.

---

### Post by aysiu on 2011-04-28
> **thecamelcoder said:**
> Hey mate, here is the one stop shop for all you'll need to root your phone

[[Video] Root Your Android]("http://www.linux-geek.co.nz/2011/04/28/video-how-to-root-your-android-device-z4mod-method/")
One-stop except for: > 2. This will NOT work on the following devices:

    Desire (requires nand unlock)
    Desire HD (requires nand unlock)
    Magic (unknown)
    Evo (requires nand unlock)
    G2 (requires nand unlock)
    Archos 70 (unknown)
    myTouch 3G (unknown)
    Wildfire
    Droid Incredible
    MyTouch Slide (requires nand unlock)

---

### Post by joelzehring on 2011-06-26
Thanks for this step-by-step. In my Googling, I added a couple other steps like adding new rules file for udev and adding adb and fastboot to my PATH file.

So... My first question is related to steps 10 and 11. Once I boot into the bootloader, adb and fastboot seem to lose track of my Optimus V. Typing commands "adb devices" and "fastboot devices" return no devices. Fastboot doesn't return anything, actually.

Which leads to my second question: What exactly is happening to the phone through the fastboot commands? Are the fastboot commands simply rooting the Optimus V, or is fastboot flashing a rooted OS onto the Optimus V? Is there a difference?

Thanks again.

---

### Post by moore.bryan on 2011-06-27
> **joelzehring said:**
> Thanks for this step-by-step. In my Googling, I added a couple other steps like adding new rules file for udev and adding adb and fastboot to my PATH file.
Good optional steps... I just didn't include them because, well, I consider them optional; however, they can be helpful down the road.

[QUOTE=joelzehring]
So... My first question is related to steps 10 and 11. Once I boot into the bootloader, adb and fastboot seem to lose track of my Optimus V. Typing commands "adb devices" and "fastboot devices" return no devices. Fastboot doesn't return anything, actually.
[/QUOTE]
That *is* strange and did not happen to me. Is there *anything* printing to the screen?

[QUOTE=joelzehring]
Which leads to my second question: What exactly is happening to the phone through the fastboot commands? Are the fastboot commands simply rooting the Optimus V, or is fastboot flashing a rooted OS onto the Optimus V? Is there a difference?

Thanks again.[/QUOTE]
AFAIK, the fastboot commands are replacing the necessary root files with those needed to root it. If anyone lurking has a better explanation, please give it because I *am not* an expert! :-)

---

### Post by zieglerj on 2011-08-10
Does this interfere at all with the phone's service? Sorry to ask the noob question here. I just want to make sure this wont lead to a hell of a headache on the phone with Virgin Mobile's tech support trying to re-activate my phone. I just want to delete the perma-installed crap (twitdroid comes to mind) that they've put on my phone. 
Thanks for the great directions otherwise though!

---

### Post by zieglerj on 2011-08-10
Ok,so when I try to start ADB it informs me that I don't have enough permissions on the device. 
> root@fenguin-System-Product-Name:/home/fenguin/android-sdk-linux_x86/platform-tools# ./adb root
error: insufficient permissions for device


---

### Post by greenfrog on 2011-08-10
I rooted my LG P500 with Z4Root, have you tried that program?

---

### Post by moore.bryan on 2011-08-10
> **zieglerj said:**
> Does this interfere at all with the phone's service?
Service? Not at all; in fact, my reception is better running the IHO rom. Do note, however, I think this voids the *phone's* warranty.

> **zieglerj]Sorry to ask the noob question here. I just want to make sure this wont lead to a hell of a headache on the phone with Virgin Mobile's tech support trying to re-activate my phone.[/quote]
No worries... this is where you *should* ask those questions! If you root your phone, I'm pretty sure VM will tell you to go pound sand, but there are dozens of threads about putting-back the stock rom with which the Optimus V comes instaled.

[quote=zieglerj] I just want to delete the perma-installed crap (twitdroid comes to mind) that they've put on my phone.[/quote]
One of the deciding factors for me to root and flash a different rom... that and the ability to overclock the processor and get quite snappier program response.

> Thanks for the great directions otherwise though!
You're welcome... thanks for the kudos!

[QUOTE=zieglerj said:**
> Ok,so when I try to start ADB it informs me that I don't have enough permissions on the device.
Hmm... try running ```
.adb usb
``` and *then* ```
.adb root
```

---

