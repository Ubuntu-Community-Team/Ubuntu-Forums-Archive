---
title: "Android development on Karmic"
date: 2009-10-30
forum: The Cafe
---

### Post by Red_Phoenix on 2009-10-30
A truncated step-by-step for getting started with Android development on Karmic. Some nice-to-have steps left as an exercise for the reader (eg: path setup, etc).

Thought I'd post it here to save others a bit of stuffing around.

$ mkdir Documents/Android
$ cd Documents/Android

Grab [http://developer.android.com/sdk/download.html?v=android-sdk-linux_x86-1.6_r1.tgz](http://developer.android.com/sdk/download.html?v=android-sdk-linux_x86-1.6_r1.tgz) using firefox. I'll assume you've left the default download directory.

$ tar xzf ~/Downloads/android-sdk-linux_x86-1.6_r1.tgz

$ cd android-*
$ cd tools
$ ./android create avd --target 2 --name my_avd

$ sudo -s
# apt-get install eclipse
<wait>

# echo 'SUBSYSTEM=="usb",SYSFS{idVendor}=="0bb4",MODE="0666"' > /etc/udev/rules.d/51-android.rules
# service udev restart

* Run Eclipse

Help Menu -> Install New Software

* Add:
[https://dl-ssl.google.com/android/eclipse/](https://dl-ssl.google.com/android/eclipse/)
[http://download.eclipse.org/datatools/updates](http://download.eclipse.org/datatools/updates)
[http://download.eclipse.org/webtools/updates/](http://download.eclipse.org/webtools/updates/)
[http://download.eclipse.org/modeling/emf/updates/releases/](http://download.eclipse.org/modeling/emf/updates/releases/)
[http://download.eclipse.org/tools/gef/updates/releases/](http://download.eclipse.org/tools/gef/updates/releases/)
[http://dl.google.com/eclipse/plugin/3.5](http://dl.google.com/eclipse/plugin/3.5)  (think this one's optional)

* Select Work With: [https://dl-ssl.google.com/android/eclipse/](https://dl-ssl.google.com/android/eclipse/)
Select "Developer Tools".. Next .. Next .. etc.

Restart when requested.

Window -> Preferences -> Android
- Set SDK Location to the Documents/Android/android-sdk-linux_x86-1.6_r1 directory.

Follow hello world here:
[http://developer.android.com/guide/tutorials/hello-world.html](http://developer.android.com/guide/tutorials/hello-world.html)


If you have your phone plugged into the USB port, and (Phone) Menu->Settings->Applications->Development->USB Debugging checked so that "$ adb devices" picks up your phone, and "allow non-market apps' configured, your app will be uploaded and run on the phone when you select Run->Run. Otherwise, it will go to the emulator.

Ok.. hopefully I've remembered everything there.

Additional terms for google to munch on, which would have probably helped me: *Android sdk karmic koala htc magic eclipse org.eclipse.datatools.connectivity.feature.feature.group emf wtp wst org.eclipse.wst.xml.core gef*

Regards,

Leigh.

---

### Post by amitabhishek on 2009-10-30
Thanks for this tut!

---

### Post by Huss on 2009-11-03
Great walk through,

Thank you.

I made a mistake along the way. I copied the text rather than the link for this source:

[http://download.eclipse.org/modeling...ates/releases/](http://download.eclipse.org/modeling...ates/releases/)

As you can see, part of the address was chopped off so the software source couldn't be accessed.

If you are trying to add the ADT plug-in and coming up with dependency errors, it might be worth checking this.

---

### Post by Dusty Wilson on 2009-11-15
Thanks for this information.  It was very helpful.

In addition, you might be interested in this:
[http://developer.android.com/guide/developing/device.html](http://developer.android.com/guide/developing/device.html)

It will help you setup udev to setup write permissions for your device.  Without this, you'll end up getting errors when trying to run your application from Eclipse when using a device instead of an emulator.

---

### Post by youbuntu on 2009-12-20
Thanks mate :)

---

### Post by WelterPelter on 2009-12-24
My Karmic installation hosed my Android/Eclipse setup. 

Spent several hours thrashing about, trying to restore it. 

Removing all the Android and Eclipse files, and then starting over, following these instructions to the letter, restored my setup. 

Thanks!

---

### Post by malmjako on 2009-12-28
I can't get adb to find my Samsung Galaxy Spica i5700. adb devices lists nothing. I've also added a udev rule, but this did not help. This is with USB debugging checked in settings.

---

### Post by skaboss on 2009-12-29
> **malmjako said:**
> I can't get adb to find my Samsung Galaxy Spica i5700. adb devices lists nothing. I've also added a udev rule, but this did not help. This is with USB debugging checked in settings.

Same problem here  :-(
Have you found a solution ?

---

### Post by stevenwagner on 2009-12-29
If you are on karmic and getting the error,
  The artifact file for osgi.bundle,org.eclipse.ant.ui,3.4.1.v20090901_r351 was not found.

this will fix:
sudo apt-get install eclipse-pde eclipse-jdt


reference: [https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/477944](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/477944)

---

### Post by kamitsukai on 2009-12-31
After running:

```
./android create avd --target 2 --name my_avd
```I get the error:

```
Error: Target id is not valid. Use 'android list targets' to get the target ids.

```

---

### Post by malmjako on 2010-01-04
> **skaboss said:**
> Same problem here  :-(
Have you found a solution ?
Nope. It's a bummer, because I bought the phone with the intent to do some android development. This makes it quite a bit harder...

---

### Post by venomix on 2010-01-05
> **malmjako said:**
> Nope. It's a bummer, because I bought the phone with the intent to do some android development. This makes it quite a bit harder...

I just got adb working with the Samsung Spica i5700. I used information from the following places:

[http://bbs.archlinux.org/viewtopic.php?id=70178](http://bbs.archlinux.org/viewtopic.php?id=70178)
[http://androidforums.com/samsung-i7500/19510-adb-linux.html](http://androidforums.com/samsung-i7500/19510-adb-linux.html)

First, /etc/udev/rules.d/51-android.rules looks like this:

```

SUBSYSTEM=="usb",SYSFS{idVendor}=="04e8",MODE="0666"
SUBSYSTEM=="usb|usb_device", ATTR{idVendor}=="04e8", ATTR{idProduct}=="681c", SYMLINK+="android_adb"

```Second, I downloaded a newer version of adb from here (see second link above): 
[http://floe.butterbrot.org/external/adb.gz](http://floe.butterbrot.org/external/adb.gz)

Now the device is detected by adb and debugging/running from Eclipse works.

I hope this helps!

Best regards,
Venomix

---

### Post by steve. on 2010-01-12
> **kamitsukai said:**
> After running:

```
./android create avd --target 2 --name my_avd
```I get the error:

```
Error: Target id is not valid. Use 'android list targets' to get the target ids.

```

I had that too.

There were no targets when I ran ./android list targets

I went into

Window > Android SDK and AVD Manager > Available Packages

and only selected the version to suit my phone for a faster download

After it was installed there was a target 1 to select.
"./android list targets" showed a target 1 for my phones OS but not a target 2

So I ran
./android create avd --target 1 --name my_avd

and about 10 minutes later "Hello, Android" was running on my Hero :)

Thanks for the guide Leigh.

I'm not sure what the code below from the guide does, but my HTC Hero ran "Hello, Android" via usb cable without using it.
# echo 'SUBSYSTEM=="usb",SYSFS{idVendor}=="0bb4",MODE="06 66"' > /etc/udev/rules.d/51-android.rules
# service udev restart

---

### Post by UbuKunubi on 2010-01-13
Hello!

I have 2 questions that other may find useful to have answered:

1) will the same installation instruction work for Jaunty?

2) when a program is ready for testing in the device, how does one go about getting the program into the phone, and running it?

Ubu.

---

### Post by ranunley000 on 2010-01-13
[SIZE=3]I have downloaded eclipse and recommended files, java, apache ant, and sdk, but when I try getting android from the repository within sdk I get the message:

Failed to fetch URL [https://dl-ssl.google.com/android/repository/repository.xml](https://dl-ssl.google.com/android/repository/repository.xml), reason: HTTPS SSL error. You might want to force download through HTTP in the settings.

I read to force https:// sources... but no luck.  Any ideas?  I'm really excited to try it out, especially now that I have a phone that I could (hopefully) make widgets for!
[/SIZE]

---

### Post by spigolo on 2010-01-22
great guide! thanks also for the spica part! now i just gotta dust off 20 years of coding inactivity and get over the "hello world" part!

---

### Post by k64 on 2010-01-22
It's a shame you can't [build the Android source code]("http://source.android.com/download/") on Ubuntu anymore. Karmic dropped support for Java 5.

---

### Post by guzzi333 on 2010-01-31
You can build it on Karmic see
[http://androidnexus.com/platform-developement/building-the-android-open-source-project-on-ubuntu-9-10](http://androidnexus.com/platform-developement/building-the-android-open-source-project-on-ubuntu-9-10)

---

### Post by jones139 on 2010-02-17
Great guide, thank you - I spent ages trying (and failing) to sort out the dependencies, but your instructions worked fine.

---

### Post by quicknick_26 on 2010-02-26
Hello all,

I'm new to development. I took two classes in Java at school. We learned on NetBeans, though.

I'd like to play around with making some Android apps for my new Samsung Moment. I got Eclipse up and running with the Android plugin. When I try to start a new project, however, the "Finish" button is grayed out. There's a red X at the top with "An SDK Target must be specified." The only field I see remaining that had not been manipulated is the "Build Target" field. It seems to have a drop down arrow, but I can't click on it or the field beside it. It seems to be ridiculously slim; like I wouldn't be able to read it, if there were something in the field. There is also no resizing option when I mouseover the divide between "Build Target" and the other fields in the new project window. Has anyone else had this problem or am I missing something completely obvious?

Another question: Is there a huge learning curve in switching from NetBeans to Eclipse? I saw that there is an Android plugin for NetBeans now, too. I wonder if it provides all of the same functionality that the Eclipse plugin has.

---

### Post by Queue29 on 2010-02-26
Go to Window -> Android SDK Manager -> Available Packages, and check and install everything with Android in the name. Google left that out of their instructions.

---

### Post by quicknick_26 on 2010-02-26
Thanks for responding, but I, in fact, do have all of the platforms from the SDK installed already (I was able to start a project in NetBeans and view all of the Android libraries). I think it's actually something wrong with the GUI on Eclipse.

I did figure out that the "Build Target" spot on the "New Android Project" window that I was talking about before has something inside it. I clicked on it and it displayed the name of one of the old APIs underneath. Then I discovered I was able to scroll with the arrow keys through all of the APIs three through seven, until I got to the end. I was only able to scroll in one direction. I can tell that it has four columns by clicking on different places horizontally. The red outline moves left and right (you can even see the column dividers if you zoom in on the image). I just can't tell what the four columns are or how to resize it so that I can view them properly. Any ideas?

---

### Post by android_rules on 2010-03-11
Hi Ubuntu Forums,

I am facing a problem about creating a new project in Android that build target is
not available in Eclipse. From  File->New->Project->android project, there is no build target displayed. Although I have installed ADT Plugin and created an AVD.

I have followed the instruction from: [http://source.android.com/download](http://source.android.com/download)
My environment is below:

1. Ubuntu 9.10 (32 Bit)
2. [Eclipse  Classic 3.5.2 (163 MB)]("http://www.eclipse.org/downloads/download.php?file=/eclipse/downloads/drops/R-3.5.2-201002111343/eclipse-SDK-3.5.2-win32.zip") ([http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/))
3. Installed [FONT=arial][FONT=courier new]sun-java5-jdk

What is solution of the prolem?

Thanks
Tonmoy

[/FONT][/FONT]

---

### Post by android_rules on 2010-03-12
Hi [quicknick_26]("http://ubuntuforums.org/member.php?u=666845"),

Just try to maximize the window. Then you will find that this problem is solved.
It is window redraw problem.

Cheers
Tonmoy

---

### Post by swiftwood on 2010-03-28
Been getting my Droid to work with Eclipse on Ubuntu this weekend

I've tried using the emulator, but unfortunately it takes FOREVER to come up, like 6 hours

fortunately I can get it to upload and run directly onto my phone, so it's not really a problem.

The funny part is that the phone doesn't show up under file manager like a regular USB device

> $ ./adb devices
List of devices attached 
040372410100F011	device


> $ lsusb
Bus 004 Device 003: ID 22b8:41db Motorola PCS 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


---

### Post by FreshP on 2010-03-31
Hello everybody. I have the following problem.

I cant connect my Android Dev 1 phone to my Ubuntu9.10 64-bit PC. I tried a lot of stuff. In /etc/udev/rules.d I have created 2 files named 50-android.rules  and 51-android.rules both having the following contents

```

SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666"
SUBSYSTEM=="usb",ATTR{idVendor}=="0bb4",ATTR{idProduct}=="0c02",SYMLINK+="android_adb"
SUBSYSTEM=="usb",ATTR{idVendor}=="0bb4",ATTR{idProduct}=="0c01",SYMLINK+="android_fastboot"

```when I type lsusb i get
```

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:183d Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```None of the entries corresponds to the phone.
Also when I plug in the phone nothing happens, except that is starts charging. I cant see the microSD or anything else.

I have usb-debugging on, and allow unknown sources on.

Any help? It is driving me crazy.
Thank you.

---

### Post by FreshP on 2010-03-31
SOLVED!!!!

It was the USB cable. I tried another one and everything works great!!!

---

### Post by syed.rakib.al.hasan on 2010-05-17
i am having some problems starting the AVD.

my android virtual device shows up when the AVD is hit to start. but it doesnt show up properly.
~ i am using android 2.1 API-7.
~ i am using linux ubuntu 9.10 karmic
~ i am using eclipse 3.5

[COLOR=Red]_**the problems is**_[/COLOR]

upon setting up the AVD from AVD Manager in eclipse - the defaul skin HVGA cannot be used. it says **"Skin HVGA does not exist"**

[COLOR=Green][B]please help.....
please help.....
please help.....

screenshot for the NO HVGA skin problem
[IMG]http://i.imgur.com/NX5Vs.png[/IMG]



[/B][/COLOR]

---

