---
title: "New installer ready for test"
date: 2021-06-19
forum: Ubuntu Development Version
---

### Post by corradoventu on 2021-06-19
If You download the ISO from [http://cdimages.ubuntu.com/daily-canary/pending/](http://cdimages.ubuntu.com/daily-canary/pending/) and select 'try Ubuntu' in the dash you can find both old and new installer, try it!
Attention: if You install you will have Ubuntu canary (a developer version?) with many apps missing from standard gnome install.

---

### Post by bobbicat on 2021-06-24
Miners in the UK used to take a caged canary down with them. If there was gas the bird would stop singing and fall off its perch. [no need for monty python fish jokes here]
 A simple easy to observe safety test.
Does this perhaps define Canary? 
I'll give it a whirl as soon as today's version is available.

---

### Post by sudodus on 2021-06-24
Interesting :-P

I zsynced the daily canary pending file and checked how it plays with [mkusb](https://help.ubuntu.com/community/mkusb).

I made a persistent live drive with mkusb version 12 alias mkusb-dus, and there is a new feature. The first time I booted into Ubuntu Canary, I entered a wizard, that gave me an opportunity to configure the system (e.g. keyboard, user name, password). Next time I booted, I arrived at a login screen like a typical installed system. So it was not the typical live user 'ubuntu' with numeric ID 999 and no password.

See the attached screenshot.

---

### Post by bobbicat on 2021-06-25
I could only find the usually offered installer.
...but it would be interesting to see how the proposed version is proceeding.

---

### Post by sudodus on 2021-06-25
The new installer,

```

ubuntu-desktop-installer

```

can be found via command line or by entering **install** in the search window for applications,

Activities -- Type of search -- 'install' -- select 'install RELEASE'

The other alternative, 'install Ubuntu ...', starts the old [FONT=Courier New]**ubiquity**[/FONT] installer.

-o-

But this installer failed for me (could not find the internal SSD in a Toshiba laptop). Maybe it works in some virtual machine (e.g. VirtualBox or KVM)? Ubiquity works as expected from the same canary iso file in the same computer. (The iso file is dated 2021-06-23).

---

### Post by corradoventu on 2021-06-25
In the live from [http://cdimages.ubuntu.com/daily-canary/pending/](http://cdimages.ubuntu.com/daily-canary/pending/) in the dash you find 2 installers: the old Ubiquity and the new one.
Tying the new installer from the ISO dated 2021-06-15 10:10 the screen for Keyboard layout is empty so i can't select a keyboard and continue with installation.
... will try a new ISO

---

### Post by C.S.Cameron on 2021-06-27
I gave Canary a try with persistent USB's made using Rufus, UNetbootin, Etcher-(manual persistence), and mkusb. I could not get YUMI and UUI to install it. I have not got around to Ventoy or hand made ISO install.

mkusb made the only USB that started for me with **Set Up**?. It's a great option as long as is it ends up as an *option*.

Am I missing something with Setup?

---

### Post by sudodus on 2021-06-27
> **C.S.Cameron said:**
> I gave Canary a try with persistent USB's made using Rufus, UNetbootin, Etcher-(manual persistence), and mkusb. I could not get YUMI and UUI to install it. I have not got around to Ventoy or hand made ISO install.

mkusb made the only USB that started for me with **Set Up**?. It's a great option as long as is it ends up as an *option*.

Am I missing something with Setup?

You know as much as we about this new feature. I saw no direct way to get away without walking through the setup when the persistent live system was made with mkusb-dus. But you can use mkusb-plug to get a persistent live system without this new feature.

---

### Post by C.S.Cameron on 2021-06-27
Why does it happen just on mkusb?

---

### Post by sudodus on 2021-06-28
@C.S.Cameron,

I discovered it, but *I have no idea why* [this setup feature is activated in persistent live drives created by mkusb-dus].

It might be controlled by a boot option. I did some testing with mkusb-plug (tried with/without some of the boot options), but could not activate this setup feature. I have *[COLOR="#0000CD"]not[/COLOR] tested all possible combinations of boot options* created by mkusb-dus and mkusb-plug and those present in the canary iso file. Another thing to test is *'grub-n-iso' alias iso-boot*, which is rather similar to what is made by mkusb-dus. So if you have the time and patience ...

Otherwise, if we really want to know, we can try to find and ask the programmer.

---

### Post by corradoventu on 2021-06-28
I downloaded the ISO from [http://cdimages.ubuntu.com/daily-canary/pending/](http://cdimages.ubuntu.com/daily-canary/pending/) both the one dated 2021-06-15 10:10 and 2021-06-25 09:26 and successfully created the USB key using Ubuntu startup disk creator. Both live started successfully and the live was working fine on my Dell laptop. The live contains 2 different installers; the old one (Ubiquity) works fine and creates an usable system (with few applications), the new one starts ok, the 1st 2 windows are ok, but the window 'keybord layout' is empty and selecting 'continue' also 'allocate disk space' is empty... abandoned.
I reported the problem in [https://discourse.ubuntu.com/t/refreshing-the-ubuntu-desktop-installer/20659/67](https://discourse.ubuntu.com/t/refreshing-the-ubuntu-desktop-installer/20659/67) and in [https://github.com/canonical/ubuntu-desktop-installer/issues/29](https://github.com/canonical/ubuntu-desktop-installer/issues/29) from [https://github.com/canonical/ubuntu-desktop-installer/issues?q=is%3Aissue+is%3Aopen+Screen](https://github.com/canonical/ubuntu-desktop-installer/issues?q=is%3Aissue+is%3Aopen+Screen)

---

### Post by corradoventu on 2021-07-25
The new ISO from [http://cdimages.ubuntu.com/daily-canary/pending/](http://cdimages.ubuntu.com/daily-canary/pending/) dated 2021-07-24 10:00 contains only the new installer snap:ubuntu-desktop-installer	stable/ubuntu-21.10	45
I downloaded the ISO and successfully created the USB key using Ubuntu startup disk creator. Live booted successfully and was working fine on my Dell laptop.
Install started ok, but at 4th screen 'Updates and other software' click on 'Continue' has no effect, install does not crash but just stop.
Will try some future ISO...
If You try the new installer post your result here, so we can have an idea of the work progress.

---

### Post by VMC on 2021-07-26
Failed. All stores grayed out. Also took several attempts to get beyond keyboard area. Also several crashes. I only install to read HD, not VM.

[https://imgur.com/a/Fbl8kFa](https://imgur.com/a/Fbl8kFa)

---

### Post by VMC on 2021-07-27
well,well. Yesterday it failed to install. Today we get both, the new installer:called "ubuntu-desktop-installer", AND Ubiquity! Ubiquity wasn't installed on yesterdays Canary.
It still fails using "ubuntu-desktop-installer", but not Ubiquity. Here's the results:
```
ubuntu@ubuntu:~$ ubuntu-desktop-installer
[ERROR:flutter/lib/ui/ui_dart_state.cc(209)] Unhandled Exception: getGuidedStorage('0', 'true') returned error 500
Traceback (most recent call last):
  File "/snap/ubuntu-desktop-installer/45/bin/subiquity/subiquity/common/api/server.py", line 123, in handler
    result = await implementation(**args)
  File "/snap/ubuntu-desktop-installer/45/bin/subiquity/subiquity/server/controllers/filesystem.py", line 221, in guided_GET
    probe_resp = await self._probe_response(wait, GuidedStorageResponse)
  File "/snap/ubuntu-desktop-installer/45/bin/subiquity/subiquity/server/controllers/filesystem.py", line 185, in _probe_response
    await self._start_task
AttributeError: 'FilesystemController' object has no attribute '_start_task'

#0      SubiquityClient.checkStatus (package:subiquity_client/subiquity_client.dart:24)
<asynchronous suspension>
#1      SubiquityClient.getGuidedStorage (package:subiquity_client/subiquity_client.dart:188)
<asynchronous suspension>
```

---

### Post by VMC on 2021-07-27
Here's the [Bug Report ]("https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/1938187")I created. If it fails please "it affects me".

---

### Post by sudodus on 2021-07-28
@VMC,

Your bug in the new installer affects me too, actually fails at an earlier stage than one month ago.

The live and persistent live systems work (like they did one month ago), and also the old ubiquity installer works.

---

### Post by VMC on 2021-07-28
Today the "ubuntu-desktop-installer" doesn't fail but doesn't complete either. All stores are grayed out. Also Ubiquity is no longer installed.
The bug report was premature, because obviously its being worked on.

---

### Post by xyz-t on 2021-07-28
Bootable stick was made in the Mint installer and it boots pretty slowly.

There were two options before, install RELEASE was removed. It does not detect the existing OS and offers no option other than deleting the HDD (multiple disks greydout). Selecting English is not working, but french triggers other languages. We did not proceed with the install = no alongside option nor manual partitioning.

---

### Post by corradoventu on 2021-08-10
Downloaded canary ISO Ubuntu 21.10 "Impish Indri" - Alpha amd64 (20210810). Started install in virtualbox, install screen 'Allocate disk space' is confusing but being in virtualbox I ignored the problem but after filling fields on the screen 'Who are you?' and a long time i had a crash.
[https://bugs.launchpad.net/subiquity/+bug/1939422](https://bugs.launchpad.net/subiquity/+bug/1939422)
Installer version is: snap:ubuntu-desktop-installer	stable/ubuntu-21.10	59

Edit: following suggestion in above bug: sudo snap refresh --edge ubuntu-desktop-installer
the installation was successful.

Install screens: [https://photos.app.goo.gl/y7o1SQmiuxBWYJup7](https://photos.app.goo.gl/y7o1SQmiuxBWYJup7)

---

### Post by corradoventu on 2021-10-27
Tested in virtual box with a recent ISO, the install works fine. Log and screenshots here: [https://drive.google.com/drive/folders/1-YRlVMPIeTfkUOebpyWvfBCJm3h2JriE?usp=sharing](https://drive.google.com/drive/folders/1-YRlVMPIeTfkUOebpyWvfBCJm3h2JriE?usp=sharing)
Developers need testers [https://discourse.ubuntu.com/t/refreshing-the-ubuntu-desktop-installer/20659/70](https://discourse.ubuntu.com/t/refreshing-the-ubuntu-desktop-installer/20659/70)
try it too if you can

---

### Post by dirtydog01 on 2021-11-28
Thanks for the Tip.

---

### Post by dirtydog01 on 2021-12-01
Thanks, downloading it now :biggrin:

---

### Post by corradoventu on 2021-12-01
nstalled from canary ISO: Ubuntu 22.04 LTS &#8220;Jammy Jellyfish&#8221; - Alpha amd64 (20211126)
with ubuntu-desktop-installer 191
manual partition on a preformatted partition
INSTALL SUCCESFUL also if at end install I see an error message&#8230;
Screenshots and logs here:
[https://drive.google.com/drive/folders/1eW_2CsPwpzd0U1wGYYS4_FNrotxatzEc?usp=sharing](https://drive.google.com/drive/folders/1eW_2CsPwpzd0U1wGYYS4_FNrotxatzEc?usp=sharing)

---

