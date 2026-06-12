---
title: "Android phones and Ubuntu"
date: 2011-12-19
forum: The Cafe
---

### Post by jespdj on 2011-12-19
I'm getting a new phone, a Samsung Galaxy Nexus. I'll probably get it next week. It will be my first Android phone.

Do Android phones work well in combination with Ubuntu? I'd like to hear people's experiences.

---

### Post by thatguruguy on 2011-12-19
Could you be more specific?

It's pretty easy to move files back and forth between Ubuntu and an Android device, if that's what you mean.

---

### Post by aeiah on 2011-12-19
android phones will show up as mass storage devices in ubuntu (or any other operating system i presume), or you could pull things via ftp / sftp whilst connected to the same LAN

---

### Post by Mikeb85 on 2011-12-19
You can drag and drop files to and from Android with Ubuntu, it works without a problem.  For updates and whatnot, Android only needs an internet connection, doesn't need a computer...  So yes, Ubuntu works just fine with android (they're both Linux after all...).

---

### Post by t0p on 2011-12-19
I've got a LG GT540, and it plays with my computer wonderfully.  I listen to music and audiobooks a lot, and I can transfer files between devices using bluetooth, with no hassles or fenickitiness.  I haven't bothered to connect them with a cable, as bluetooth caters for my needs well enough.

Apparently some Android phones can be used as a wifi "hot-spot", but I don't think my phone offers that facility.  I do enjoy the phone's wifi capabilities though, so when I'm out and about I can check email, browse the web, etc, without using my service provider's miserly data allowance (I mean, *come on* - what the hell kind of use is a 50MB per month?).  There are plenty of access points that are open intentionally, like at McDonalds etc - I would *never* suggest that one should use a neighbour's open access point without getting permission first!

---

### Post by LordFarquaad on 2011-12-19
Concerning the Galaxy Nexus (I have one), you won't be able to connect it as a mass storage device. This feature was disabled since Android 3 in favour of MTP. The reason is that you cannot mount the same file system on 2 different machines at the same time, so the internal storage had to be split, making you lose a lot of space. Now there is only one partition, accessible via MTP.

MTP also works on Ubuntu but you might need additional configuration to make it work. Personally I had to activate the USB debug mode in the developer settings so that Rhythmbox recognises it. Banshee still doesn't…
It is also possible to mount MTP devices in the filesystem but for the moment I only needed to transfer music files.

---

### Post by guyver_dio on 2011-12-19
If you have wireless, there's ways you can connect to it wirelessly too. I use to use that over the usb cable cause cables are just annoying. It's been awhile since I've done it so I'll get back to you when I find out what I use to use.

---

### Post by BrokenKingpin on 2011-12-19
I have the Galaxy GIO, works just fine with Ubuntu.

---

### Post by jespdj on 2011-12-20
Thanks for the useful answers.

> **thatguruguy said:**
> Could you be more specific?
I mean doing things like connecting it via USB or some other way to put music, podcasts and other files on the phone or using it to provide an Internet connection for your Ubuntu laptop when you're on the road. For example, is it possible to connect the phone to the laptop via USB or Bluetooth, and then let the laptop use mobile Internet through the phone? (Or maybe make it work as a WiFi hotspot as t0p says)?

---

### Post by LowSky on 2011-12-20
> **LordFarquaad said:**
> Concerning the Galaxy Nexus (I have one), you won't be able to connect it as a mass storage device. This feature was disabled since Android 3 in favour of MTP. The reason is that you cannot mount the same file system on 2 different machines at the same time, so the internal storage had to be split, making you lose a lot of space. Now there is only one partition, accessible via MTP.

MTP also works on Ubuntu but you might need additional configuration to make it work. Personally I had to activate the USB debug mode in the developer settings so that Rhythmbox recognises it. Banshee still doesn't…
It is also possible to mount MTP devices in the filesystem but for the moment I only needed to transfer music files.



if I recall you can force MTP by adding a small hidden file to a device. I can't recall details but I do remember doing it for a mp3 player I have. I also recall Android devices had USB debug modes that allow direct connection of the device to a PC, especially a rooted one.

---

### Post by satanselbow on 2011-12-20
Have a look in the blurb for your Galaxy and see if it makes mention of "USB Tethering" if not you may need an app for that. I find **EasyTether** to be excellent and includes a Linux client ;) It is about the only Android app i've felt compelled to pay for!

I must confess that I always update / root my SE Xperia X10 Mini Pro on a windows machine as getting it recognised under linux in flashmode can be a nightmare - even worse in a vbox :(

Not enough of a gotta to make me want an iPhone or WinPhone though :popcorn:

---

### Post by jacksonwalt on 2011-12-21
Android Phones are much better operating system and [Samsung galaxy Nexus]("http://www.androidapps4u.com/news/tehnology/tech-news/samsung-nexus-prime-vs-samsung-galaxy-s2-lte/") is good choice

---

### Post by N00b-un-2 on 2011-12-21
there is native support built into the linux kernel (not just on Ubuntu) for ALL Android devices.  Every single android device is capable of being mounted as a mass storage device on ANY operating system (you simply select it when you mount the phone via USB).  All Android phones are capable of being tethered (connecting to the internet using your phone's 3G/4G data connection via USB or Wifi), but virtually all of them will need to be rooted in order to gain access to this ability.  All Android phones are bluetooth enabled and can receive data from any operating system provided the host computer has a compatible bluetooth trxver.
When mounted as USB mass storage, Android phones should be automatically detected as a music player device in most programs like Banshee, Rhythmbox, etc.  MTP is not supported on Android to the best of my knowledge.
By law and terms of license, these specifications apply to ALL Android phones, as per the specifications of the Open Handset Alliance and the AOSP (Android Open Source Project).  For a device to utilize the Android operating system, it must meet certain criteria.
I hope this helps explain some things

---

### Post by N00b-un-2 on 2011-12-21
> **satanselbow said:**
> Have a look in the blurb for your Galaxy and see if it makes mention of "USB Tethering" if not you may need an app for that. I find **EasyTether** to be excellent and includes a Linux client ;) It is about the only Android app i've felt compelled to pay for!

I must confess that I always update / root my SE Xperia X10 Mini Pro on a windows machine as getting it recognised under linux in flashmode can be a nightmare - even worse in a vbox :(

Not enough of a gotta to make me want an iPhone or WinPhone though :popcorn:

If you paid money for this functionality you should demand a refund!  USB tethering is supported in the Linux kernel without any 3rd party applications.  It's possible on Windows with the right drivers and OSX via ssh tunneling or DHCP proxy.  paying to tether to an Android phone is ludicrous.

---

### Post by N00b-un-2 on 2011-12-21
As for MTP on Android, there is a distinction that MUST BE MADE about Android 3.0.  Honeycomb is NOT open source it is proprietary and the domain of tablets ONLY.  Honeycomb does not apply to the Open Handset Alliance specifications as it is only made for specific Android tablets which do not have removable storage, hence no MSC (mass storage controller) mode.
I was not aware that MTP had been adopted for ICS (Ice Cream Sandwich Android 4.x), and I would double check that that is the case.  Android 4.0 is an update to Android 2.3, not an update to Android 3.0.  MTP seems counter intuitive for the purpose of Android based smart phones because first of all it is a proprietary technology specification and Android is open source.

---

### Post by Stovey on 2011-12-21
> **jespdj said:**
> ...is it possible to connect the phone to the laptop via USB or Bluetooth, and then let the laptop use mobile Internet through the phone? (Or maybe make it work as a WiFi hotspot as t0p says)?

I have a Samsung Galaxy S with Android 2.3.3 (Gingerbread?), and it will most certainly create a hotspot.  The hotspot is very handy if you are stuck at some location that either does not broadcast internet or charges for it or the free connection is very poor (ie airports, conferences, hotels, etc...).  I use the hotspot quite often with my netbook.

Don't know about the nexus though, I would imagine it would be the same?  You can check with the Android forums:

[http://androidforums.com/samsung-galaxy-nexus/](http://androidforums.com/samsung-galaxy-nexus/)

---

### Post by N00b-un-2 on 2011-12-21
2.3.3 is indeed gingerbread.  hotspot is great, but it chews up battery life like no other.  try USB tethering, it's far more secure and charges your phone while you use it.

---

### Post by Claus7 on 2011-12-22
Hello,

I think that most of the things you would like to do will work fine with ubuntu. The only problem you might face are the updates, which will require to use:
i) either wine with usb support, which is not straightforward till the time of writing or
ii) virtualbox with usb support, which is not easy as well.

Regards!

---

### Post by thatguruguy on 2011-12-22
> **Claus7 said:**
> Hello,

I think that most of the things you would like to do will work fine with ubuntu. The only problem you might face are the updates, which will require to use:
i) either wine with usb support, which is not straightforward till the time of writing or
ii) virtualbox with usb support, which is not easy as well.

Regards!

I've never, ever, had to run an update through my computer. Which version of the android OS are you using?

---

### Post by Claus7 on 2011-12-22
Hello,

> **thatguruguy said:**
> I've never, ever, had to run an update through my computer. Which version of the android OS are you using?
version 2.2.2

Is it possible to do an update with another way?

Regards!

---

### Post by treesurf on 2011-12-22
How to mount the Galaxy Nexus in Ubuntu, see this link:

[http://www.omgubuntu.co.uk/2011/12/how-to-easily-mount-the-galaxy-nexus-on-ubuntu-11-10-via-unity/](http://www.omgubuntu.co.uk/2011/12/how-to-easily-mount-the-galaxy-nexus-on-ubuntu-11-10-via-unity/)

---

### Post by castrojo on 2011-12-22
> **thatguruguy said:**
> I've never, ever, had to run an update through my computer. Which version of the android OS are you using?

I know someone with a Samsung Galaxy that needs a windows machine to be updated. They purposely shut off the OTA updates to make people use the windows thing to update it. Not all Androids are the same, manufacturers and carriers purposely cripple them (some worse than others, most of the US carriers disable tethering unless you pay for it for example).

Back on topic on the Nexus:

- You need MTP to use it, it doesn't mount as USB Mass Storage.
- It does wifi hotspot and tethering over USB out of the box (My old nexus one did this too so it's not a new feature).
- If you're using Google's services there's really no reason to connect it to your PC, I do it occasionally on my laptop to tether, but I don't even bother syncing music or photos to it since Google Music and Picasa do this for me. Though it might not be available in your country.

---

### Post by mamamia88 on 2011-12-22
> **Claus7 said:**
> Hello,


version 2.2.2

Is it possible to do an update with another way?

Regards!

root the phone and use a rom based on newer version of android then what you have.   personally running cyanogenmod 7.1 on my phone.

---

### Post by Claus7 on 2011-12-23
Hello,

> **mamamia88 said:**
> root the phone and use a rom based on newer version of android then what you have.   personally running cyanogenmod 7.1 on my phone.

thanks for the info. For the time being I'm content with what I have, yet I'll have this in mind for future consideration.

Apologies if my question was off-topic compared with OP's ones.

Regards!

---

### Post by N00b-un-2 on 2011-12-30
+1 cm7

---

### Post by Paqman on 2011-12-31
> **castrojo said:**
> I know someone with a Samsung Galaxy that needs a windows machine to be updated. They purposely shut off the OTA updates to make people use the windows thing to update it. Not all Androids are the same, manufacturers and carriers purposely cripple them (some worse than others, most of the US carriers disable tethering unless you pay for it for example).

Which is stupid, because it just drives more people towards custom ROMs like Cyanogenmod. If you've got a relatively vanilla Android on your handset, there's no real advantage to flashing it, but the more the networks ship with parts of the phone broken, the more incentive there is for even non-geeks to try it out.

Interestingly HTC have changed their mind about custom ROMs and now even provide a tool to unlock their bootloaders.

---

### Post by satanselbow on 2011-12-31
> **N00b-un-2 said:**
> If you paid money for this functionality you should demand a refund!  


Why? Easytether does exactly what it says on the tin has paid for itself 1000 times over (only about a £5 from what I remember). Why would supporting developers that have produced a useful product cause such consternation? I also donate financially to other software products that I personally find useful... such as Ubuntu... or is that not how it's meant to work?

> **N00b-un-2 said:**
> 
USB tethering is supported in the Linux kernel without any 3rd party applications.  


It may well be enabled in the kernel but many providers disable it at the phone end with their oem software bundles. I believe it was only stock in the kernel since v3 - I have had my phone much longer than that.

> **N00b-un-2 said:**
> 
It's possible on Windows with the right drivers and OSX via ssh tunneling or DHCP proxy. 

Fascinating... but I don't use windows or OSX on the machine I am likely to need tethered or need the added layers of tunnelling or unstable, frquently also "paid for" proxies.

> **N00b-un-2 said:**
> paying to tether to an Android phone is ludicrous.

Erm... no it isn't. It is an simple and effective way of bringing the functionality I require to the handset I own (SE Xperia X10 MiniPro) without having to jump through hoops.

---

### Post by N00b-un-2 on 2012-01-01
I hate to split hairs, but I've been tethering my android phone with Ubuntu since 9.10 without any issues.   I think that would have been kernel 2.24.x but I'm not sure.  So no... it's been supported long since before the recent release of 3.x.

Easy tether is simply a waste of money.  Every Android device is fully capable of tethering.  Some devices may require root access, mine did not.  And my phone is hardly a top of the line phone (LG P-509 "Optimus T").  I do not see it the way you do.  Buying Easy Tether is not paying hard working developers who created a valuable product, it's paying developers who are trying to trick unsuspecting consumers to pay for functionality that already is and SHOULD BE freely available.  Fundamentally, this just rubs me the wrong way as it seems far too much like Microsoft or Apple.
I paid for the phone, it belongs to me and I will do with it as I damn well please, and I refuse to pay any additional money to make my phone do what it's supposed to do.  That's the reason why Android and the open hand set alliance were created, as an open source alternative to Apple and Microsoft proprietary smart phone OSes.
There are plenty of free applications to set up a proxy or tunneling and in my experience they are no more or less stable than USB tethering.  Not only that but anyone who has a little bit of knowledge of how to use SSH can easily accomplish this with nothing but the terminal.  so once again, it makes no sense to pay for an app like Easytether or PDANet.

Like I've already said, USB or even Wifi tethering are available IN THE ANDROID SYSTEM MENU.  Go to Settings> Wireless & Networks > Tethering & Portable hotspot.  Even HTC, the king of mobile devices has reversed their position on modification and opened their boot loaders for easy modification.

There is nothing anyone can tell me that will ever convince me to pay for something that is three clicks away.  Hell, they even have a free widget on the Android market that will enable tethering or hotspot.  Android phones were designed to be used as a portable modem, it's only the cell phone providers that disagree and profiteering opportunists like the devs who put out apps like PDANet and Easy Tether are capitalizing on the counter intuitive restrictions that some cell phone providers place on their customers.

Enjoy burning your hard earned money, because that's smart...

---

### Post by N00b-un-2 on 2012-01-01
And another thing.  You mentioned jumping through hoops.  What hoops exactly are you talking about?  Literally just a few days after I bought my phone, I installed the JDK and Android SDK on my laptop (tools which ANY Android user should have IMHO).  From there, I installed Z4Root from the market and then rooted my phone which took about 2 minutes.  Then I pushed a custom recovery update.zip and a custom ROM to my SD card, which took another 3-4 minutes.  I could have actually done so without using the ADB by mounting as Mass Storage, but I digress.  From there I rebooted into recovery, flashed ClockworkModRecovery and then rebooted into recovery again, which took about 2 minutes.  Then I flashed my custom ROM which took about 3 minutes, and then first boot afterwards took another 10 minutes.
I would hardly call downloading one app and two files onto your phone "jumping through hoops".

The entire process of rooting, installing a custom recovery and then flashing a ROM on an Android phone is easy, requires virtually no technical ability especially if you have a popular phone like a Droid or HTC phone, can be accomplished without ever even looking at a computer and literally only takes a matter of minutes.  I went from stock to custom ROM in less than 20 minutes.

The benefits include overclock capability, full access to all of your phones capabilities (like tethering), improved battery life and of course the ability to "tinker" with your phone.  I can't imagine why anyone would ever own an android phone without at least rooting it, because not doing so would be like buying an expensive sports car and removing half the spark plugs.

... And did I mention it doesn't cost a single cent?

---

### Post by jespdj on 2012-01-02
I have my Galaxy Nexus now and it's a fantastic phone. The screen is incredibly nice, with its super-high resolution (1280 x 780) it's totally impossible to see pixelation. It works great and the integration with Google account services is very useful.

I've been using the app SSHDroid which allows you to transfer files and login via SSH on the phone easily from Ubuntu. The only thing I've noticed when putting on sound files to be used as a ringtone, I have switch the phone off and on before it sees the file that I've just put on there.

---

### Post by N00b-un-2 on 2012-01-02
that is because of how files are indexed at boot time on Android.  System Files for the most part are non-volatile.  The whole Android OS exists as a single compressed file image which is decompressed on the fly at boot.  Most system file edits will require a reboot to see change.

---

### Post by satanselbow on 2012-01-09
> **N00b-un-2 said:**
> I hate to split hairs

Well apparently you do.

If the service provider disables tethering on their android spin - as many still do it matters not one jot whether Ubuntu tethers out of the box or not.

I use what works for me - on the phone I own. Tethering through cyanogenmod and numerous derivative roms does not work - full stop. Easytether does.

I really do not see why that simple fact offends you so? 

Given it took you a whole 2 posts of text to outline the steps you took to tether your phone I would say my previous "hoops" related post was quite justifiable and accurate.

Not tried SSHDroid - might have a look at that - thanks for the heads up.

The whole tone of your post rather stinks of resentment than support for the opensource movement. I'm sorry if you have trouble paying for stuff - maybe you should ask Daddy to up your allowance.

Given it's **my** - not that hard earned actually - money thats being "burned" on something that does exactly what it's meant to I think that is smart. Thank you for the somewhat sideways compliment.

---

### Post by N00b-un-2 on 2012-01-09
root + recovery + rom + 20 minutes of your time = true open source Android as it was meant.  If you really had "money to burn" you would go buy a Nexus.  I don't, and I certainly don't have money to waste on paying for free services.  Your last comment was just plain rude and borders on violating the terms of use, so watch it.  Let's try to keep things civil, shall we?  We're all adults here.
I'm merely trying to help people out.  If somehow my opposition to paying for wasteful applications offends you, I apologize.  My point was that if enough people demanded that service providers not tamper with the Android system, change would inevitably take place.  Take for example Motorola and HTC changing their stance on after market modification due to customer demand, and thus opening up their boot loaders to enable easier flashing of custom ROMs.
Paying a 3rd party to enable a service that is intended to be free as a stop gap solution to your cell phone providers imposed software limitations is counter intuitive.
But I digress.  Do what works for you.  If offering a free and open source alternative to paid software is somehow not supporting open source software, then I'm not sure what is.

---

### Post by satanselbow on 2012-01-09
> **N00b-un-2 said:**
> root + recovery + rom + 20 minutes of your time = true open source Android as it was meant.  If you really had "money to burn" you would go buy a Nexus. 


Crippling particular services of the Android OS (by the vendor) does not make it any less OpenSource. Irritating - but not against the rules. Should a 3rd party dev choose to charge a small fee for their ingenuity in re-enabling it on devices that are crippled in this way then I have no problem in making the payment. 

Truth be told the ability of software devs to make a few quid on the Android Market contributes to Androids success and uptake as a platform and there are more "free" apps than paid (60/40 split I believe). Let us not forget that this is all run by Google who will of course be making a healthy profit on the ad streams... not particularly opensource of them... 

> **N00b-un-2 said:**
> 
I don't, and I certainly don't have money to waste on paying for free services.

You seem to miss the point that even (by the dev's own admission) that the CM tethering solution does not work on all devices and can be very unstable. 


Neither do I - it would be a bit dumb to pay for a freebie... Out of disinterest; Do you object to donating to opensource projects as well?

> **N00b-un-2 said:**
> 
We're all adults here.


I was wondering - glad you cleared that up

> **N00b-un-2 said:**
> 
I'm merely trying to help people out.


Maybe you would like to tell them that rooting / installing 3rd party roms will in all likelyhood invalidate their warranty on the device. It may also turn their £300 technotoy into poor excuse for a doorstop (way too light n thin). Small Technology insurers are increasingly wise to this and may not pay out on phones / laptops that are found not to have the stock rom/firmware etc.

> **N00b-un-2 said:**
> 
If somehow my opposition to paying for wasteful applications offends you, I apologize.

No it was your over-excited evangelicism that did that - but apology accepted.

---

### Post by N00b-un-2 on 2012-01-10
granted, modifying ANY part of the Android system from how it came on your phone will in almost all cases void your warranty.  But in my experience, it's damn near impossible to completely brick an Android phone.  I've "soft bricked" mine a couple times, and all it takes to recover it is to use the official update software provided by the manufacturer and/or service provider.  Virtually every Android phone has some form of flash/emergency mode, if not more than one.  My phone has fastboot, recovery, emergency and flash mode, so I have four different methods available to recover in case anything goes wrong.  the methods vary from phone to phone, but I root and rom people's phones for them all the time and have yet to manage to brick a phone.  Absolute worst case scenario is that the reflash doesn't take and you have to return the phone and tell your service provider or 3rd party insurer that you attempted an update which failed (which is actually true).  Since I got my first Android device, I've only had to return two phones, both of which were actually bricked by official OTA updates (Over the air, ie; from my cell phone provider and not using the software from LG's website) which came from my service provider on the stock firmware.  Actually its the very reason why I looked into after market modification in the first place.  I wanted to update my phone from Android 2.1 and the official method failed on two separate phones.  On the other hand, I've flashed new roms on my phone a hundred times over without a single issue.  The only time I've ever seen anyone have a return rejected was when a friend of mine took his HTC EVO with a custom ROM installed  (nothing wrong with the phone) and asked to get a handset upgrade to the EVO 3D.  They took one look at his phoen and of course immediately flagged his account and denied his request for an upgrade.  Obviously, you need to be smart about what you do and that was just a dumb move.
And no, I do not oppose donating to open source projects.  I've donated money to several devs, including they CM7 devs and the devs who ported CM7 to my phone (just to name a few).

---

### Post by N00b-un-2 on 2012-01-10
> **satanselbow said:**
> Crippling particular services of the Android OS (by the vendor) does not make it any less OpenSource. Irritating - but not against the rules.

HTC Sense firmware is not open source.  Neither is the Moto Droid, nor the Sony Xperia's firmware.  All of which contain mass amounts of proprietary code which deviates far from the AOSP (Android Open Source Project) base, which is what is found on the Nexus phones.  All three manufacturers came close to being forced out of the Open Handset Alliance, and thus would not be able to utilize Android as an OS on their phones because of the fact that they closed sourced their code and removed the ability to flash custom (open source) firmware.  Hence the reason that they have all since been forced to reverse their policy on modification and open their bootloaders again.

---

### Post by technoshaun on 2012-01-19
I utilize Easytether and I do have a rooted Android as well. The reasons are two fold for this. One I have a Boost Prevail that is both software and hardware locked out for tethering. My phone will never work as a Mobile WiFi Hot spot, and really it shouldn't. It will burn out the inside of the phone faster than Ice Cream in the hot sun (Pun Semi-Intended) if it does. The phone has some real hardware limitations to consider. Its a simple phone meant for basic usage. 

While there are a couple of rants about EasyTether being a ripoff I have to firmly disagree. It is one of two I am aware of that does not require your phone to be rooted to use. It utilizes only official APIs to function. That means up front that its not a hack job and development still continues. The $10 fee is a ONE time purchase and includes free updates for the lifetime of the phone. Yeah as long as that phone functions you can run the latest version of Easytether and never pay for the license on an upgrade.

Rooting an android, while desirable for those who have the tech savvy to understand the issues and risks of it, is not for everyday users and I know several people who should never have a rooted Android.

Carriers charge extra for the ability to use the onboard tethering ability of the phone, if they allow it at all. Some carriers will cut your service off if you do root your phone and turn on the tether ability or charge you for the same.

I put Easytether on my phone because it utilizes an entirely different method to allow tehering (again proof the app is not some slackers hack job) and my phone (which is prone to heating issues) barely gets warm when I use it. It was also the only app that would allow my phone to tether. Because the ability of my phone to act as a WiFi hot spot is hardware disabled none of the other apps I tried worked, even those that on a rooted phone bypass the software disables. However, with that ability shutoff at the manufacturing level, my options are severely limited. Easytether fixes that issue for me.

Another thing about Easytether, its not just a tethering app, its also a micro router, but unless you have a grasp on the mechanics of that you really wouldn't notice it.

Now for those who use Easytether and would prefer to not have an open terminal visible I wrote a simple script.

--------------------------------------------------

#!/bin/sh
#background easytether launcher
xterm -e nohup easytether connect &

--------------------------------------------------

Cut and paste the text into a file and save it to your desktop. Make it executable and when you want use Easytether just double click the file.

---

### Post by John Futter on 2012-01-19
I have the HTC Wildfire, and it's worked exactly as I've wanted it to with Ubuntu. :)

---

### Post by N00b-un-2 on 2012-01-19
as for mobile hotspot goes, I would recommend against using that feature on any phone whether it's supported or not as it destroys battery like no other, even if the phone is plugged in.  If Easy Tether works for you then by all means go ahead and use it.
I'm fully aware of how easy tether functions as a kind of USB router.  It accomplishes the exact same thing as USB tethering does when enabled on a custom firmware.  Enabling USB tethering on non supported devices is simply re adding the functionality already available in Android that was removed by your service provider.
My service provider does in fact charge an additional fee for data used while tethered if you use the application that is provided on their upper end phones which simply does not exist on the lower end models like mine.
The Cyanogenmod 7 ROM I'm running allows me to do everything with my phone that a Nexus owner can, although perhaps not quite as fast.
As for rooting goes, somehow millions of Windows users use their computers with full administrative rights every day and manage to not break their system.  Rooting a phone just enables administrative rights to the phone and as I already stated, since this >>is<< a Linux forum every single user here should have the "tech savvy" to understand what root is.  It is not dangerous, it just gives you the ability to do something that could potentially damage parts of the system if you're not careful.

I personally have never managed to actually brick my phone by doing anything dumb.  I have had two phones die on me after failign to complete an over the air update from my service provider which is what spurred my interest in flashing custom ROMs in the first place.

---

### Post by giowck on 2012-01-19
didn't read the whole thread, but maybe you'll like Airdroid: [http://airdroid.com/](http://airdroid.com/)

---

