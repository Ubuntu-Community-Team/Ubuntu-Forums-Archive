---
title: "Anyone unlocked Nexus One in ubuntu?"
date: 2010-01-31
forum: The Cafe
---

### Post by legolas_w on 2010-01-31
Hi,


I am going to unlock my Nexus one and install a custom ROM (CyanogenMod), I am wondering whether it is possible using Ubuntu or we need to have windows so it can use the USB driver and detect the Nexus one phone?


Thanks

---

### Post by KaYnemO on 2010-02-01
> **legolas_w said:**
> Hi,


I am going to unlock my Nexus one and install a custom ROM (CyanogenMod), I am wondering whether it is possible using Ubuntu or we need to have windows so it can use the USB driver and detect the Nexus one phone?


Thanks


Good question, actually, I was kinda roaming over the same issue...

---

### Post by legolas_w on 2010-02-01
hi,

Please share your findings about installing custom rom into Nexus one from inside ubuntu. I will do the same if I found any.

Thanks.

---

### Post by NCLI on 2010-02-01
It's very easy, don't worry. Google will easily get you the answers you seek ;)

---

### Post by hobo14 on 2010-02-14
> **NCLI said:**
> It's very easy, don't worry. Google will easily get you the answers you seek ;)

That's not terribly helpful.  Could you give us more info on how you did it, and/or point us at some good links?

I'm getting stuck unlocking the bootloader, my computer can see the phone in the Device Manager (from the repos) but fastboot in the terminal is stuck on:&#12288;"< waiting for device >"

---

### Post by hobo14 on 2010-02-15
Found the info I needed to do this with Ubuntu :p  but even following this I still couldn't successfully get the computer to recognise the phone....?

Anyone had any luck with this?  A detailed run-down would be great.


I finally gave up and did it on a windows box :(

---

### Post by legolas_w on 2010-02-15
> **hobo14 said:**
> Found the info I needed to do this with Ubuntu :p  but even following this I still couldn't successfully get the computer to recognise the phone....?

Anyone had any luck with this?  A detailed run-down would be great.


I finally gave up and did it on a windows box :(

You had a windows box to do it, I have none :d

I will work on the rooting thingy during next week and post the instructions here/.

---

### Post by hobo14 on 2010-02-15
> **legolas_w said:**
> You had a windows box to do it, I have none :d

I will work on the rooting thingy during next week and post the instructions here/.

Sorry legolas, I forgot to post a link in the last post ;)

[http://developer.android.com/guide/developing/device.html]("http://developer.android.com/guide/developing/device.html")

I kind of suspect it's not really up to date though.

0bb4 is the vendor id for HTC, but I had to use 18d1, which I think is the id for Google.  Check with **lsusb -vv | less**

After you edit the file, use **sudo service udev restart**
then unplug and replug the phone into the computer.

Of course, this _didn't_ work for me, so take it with a pinch of salt...

---

### Post by hobo14 on 2010-02-19
Here's how to connect the phone to Ubuntu:

$ **sudo gedit /etc/udev/rules.d/51-android.rules**
save these two lines into the file:
```
SUBSYSTEM=="usb", SYSFS{idVendor}=="18d1", MODE="0666"
SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666"
```
$** sudo chmod a+rx /etc/udev/rules.d/51-android.rules**
$ **sudo service udev restart**
plug in the phone, and away you go without any need for a windows box.:D

---

### Post by legolas_w on 2010-02-20
Hello everyone and thanks for contributing to this thread.

I want to flash my phone today. So far I downloaded the following things and performed the following tasks and have some questions which are included below.


- Downloaded android sdk and installed it (the bin folder is in the path). I can use adb to install software into the phone so I assume that the SDK is fine.

- Downloaded and installed fastboot (I put its files inside the android sdk bin folder)

- Downloaded 3 zip files from [http://forum.xda-developers.com/showthread.php?t=623496](http://forum.xda-developers.com/showthread.php?t=623496) which are CyanogenMod 5.0.3, its radio and its Google Addon.

- Downloaded the recovery-RA-nexus-v1.5.3.img from [http://forum.xda-developers.com/showthread.php?t=611829](http://forum.xda-developers.com/showthread.php?t=611829)

Now I want to install these stuff into my phone. I think I should do the following steps, please let me know whether they are correct or not.

- Use fastboot command to unlock the phone. [COLOR="Red"]**(how?)**[/COLOR]
- use the fastboot command shown below to install the RA
```
fastboot flash recovery recovery-RA-nexus-v1.5.3.img
``` 
The image file path should be correct and it should be accessible to the fastboot command.

- create a nandroid backup.[COLOR="Red"]**(how?)**[/COLOR]
- install the CyanogenMod. [COLOR="Red"]**(how?)**[/COLOR]
- install the CyanogenMod radio image using the following command:

```
fastboot flash radio Radio_20100203_2_Signed_PASSION.img
```
- install google add-ons [COLOR="Red"]**(how?)**[/COLOR]

I assume that the above steps are all I need to do in order to root the phone and install the CyanogenMod. Please let me know [COLOR="Red"]**(how?)**[/COLOR] to do the things I marked and also please let me know whether these are all I should do or some stuff are still missing.

Thanks

---

### Post by hobo14 on 2010-02-20
Don't know abot the recovery tool or custom rom but to unlock do this:

- Turn the phone off.
- Hold the trackball down, and turn it back on. The phone will boot into the white bootloader screen with Androids on skateboards.
- Plug the phone into the computer
- Enter "sh ./fastboot-linux oem unlock". 
- If you still see "< waiting for device >" use the power button to switch between the BOOTLOADER and FASTBOOT a couple of times.
- The phone will now ask if you want to unlock the bootloader, select yes.
The bootloader is now unlocked, the bootloader screen will have a pink UNLOCKED at the top, and an open lock is displayed in the phone startup graphics.

To root the phone: (altough this might be where you want to use cyanogen)
- Check Build Number in Settings > About Phone.  Mine was ERE27
 - Get the appropriate Superboot image from [here.]("http://android.modaco.com/content/google-nexus-one-nexusone-modaco-com/298782/12-feb-erd79-ere27-ere36b-superboot-rooting-the-nexus-one/")  I used the himem version of ERE27, to make full use of my RAM. 
 - Turn the phone off, and back on with the trackball held down to get into the bootloader screen
 - Plug the phone into the computer
 - Unzip the Superboot file, and run ./install-superboot-linux.sh
 - Go to Settings > Applications > Development > allow USB debugging on the phone. 
Now if you enter "su" into a terminal app on the phone such as Android Terminal Emulator (don't use Terminal Emulator - no virtual keybd) you will be root. You also have the Superuser Permission icon available in the phone applications

---

### Post by hobo14 on 2010-02-22
Here's Debian running on my N1.

I've written a howto, but they have to be approved by a mod now (?), and it hasn't come out yet.

EDIT: Here's the HOWTO: [http://ubuntuforums.org/showthread.php?t=1413313]("http://ubuntuforums.org/showthread.php?t=1413313")

---

### Post by snares on 2010-04-21
Just to make it easier for anyone looking here is Cyanogen(mod) instruction for ubuntu

[http://wiki.cyanogenmod.com/index.php/Install_the_Latest_Android_sdk](http://wiki.cyanogenmod.com/index.php/Install_the_Latest_Android_sdk)

that should do it. Took me a while to find it. Didn't see a link for it on Cyan's site but this will make it easier for everyone else. One note though. He says to use 11-android.rules but I have had much better luck with 70-android.rules . don't why it makes a difference but it did for me.

cheers
snares

---

### Post by Pat_Primate on 2010-06-04
I just wanted to thank Hobo14 for mentioning the "settings -> applications -> development -> usb debuggging"

I wasn't able to get the 'adb devices' and 'ddms' working before I did that

Cheers

Pat

---

### Post by jonathanbhirst on 2010-06-10
Android, fastboot, Ubuntu 10.4

Here is what I had to do in order to get fastboot and adb working on Ubuntu 10.4

First, why it is not working... fastboot and adb must be run with root privledges in order to get the usb devices to show up for use...

Simply running sudo ./fastboot will not work because fastboot is likely not in a path that is in the root $PATH location. You can either be explicite and run sudo /your/complete/path/to/fastboot or you can do like I did to ease your life in the future.

1)enable root account – You can do this by setting the password for the root account with $ sudo passwd root (Enter your password for root when prompted)
2)Log out of the console and log in as root (You will need to log in as other)
3)open the computer browser under places and navigate to your user path where you have .../mydroid/out/host/bin/fastboot & adb located...
4)Create a shortcut to said files...
5)Drag and drop those shortcuts into /usr/local/bin and rename them to fastboot and adb... (this must be done as root or you can't get the links moved there)
6)Log out of root, and log back in as user... You should now be able to sudo fastboot or sudo adb from anywhere you need to...

Alternatively while logged in as root you could add your .../mydroid/out/host/bin path into the root users paths in .bashrc... that would give you the ability to execute anything as su from the directory...

The reason to link this as opposed to copy into /usr/local/bin is so that any updates in the future in fastboot or adb get automatically used.

This worked for me... Good luck... (If someone knows how to get devices to show up without needing to sudo it would be great to know)

---

