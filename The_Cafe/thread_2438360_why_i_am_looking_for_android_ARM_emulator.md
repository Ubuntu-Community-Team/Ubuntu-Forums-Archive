---
title: "why i am looking for android ARM emulator"
date: 2020-03-10
forum: The Cafe
---

### Post by Skaperen on 2020-03-10
i have a special camera that can operate using an Android app they provide.  it connects via USB.  a usable emulator must be able to access a host USB port and make it appear as the emulation USB port.  a usable emulator must also emulate the ARM CPU enough to run the provided app.

*edit*:

i think i found a model (on Amazon) with direct support for Linux though it is $50.  i would have to buy a new one and waste this one that was given to me.  FYI, this is a rifle borescope.

---

### Post by grahammechanical on 2020-03-13
I am not completely clear on what you are asking for but if your are looking for a way to run an Android app on Ubuntu, then: Install the Google Chrome web browser and then install the Chrome ARCWelder extension. That will let you test Android apps though the Chrome browser. Place the APK file in a folder and load ARKWelder and direct it to the APK file and the app should run.

I use this method myself. There are websites that allow the downloading of free APK apps.

ARCWelder will complain that it is not running on the Chrome OS but the Android app still runs fine. There is one thing to watch out for. When Chrome is updated the link between the app's desktop icon and ARCWelder gets broken. We need to repeat the original process.

Regards


[URL="https://chrome.google.com/webstore/detail/arc-welder/emfinbmielocnlhgmfkkmkngdoccbadn"]https://chrome.google.com/webstore/detail/arc-welder/emfinbmielocnlhgmfkkmkngdoccbadn

[/URL]

---

### Post by Skaperen on 2020-03-13
is it really limited to *test apps*?  this is not a *test app*.  it is a regular app.

my understanding of this, if you are an app developer, you can build the source into a *test app* binary and run it in a test emulator.  this gets compiled into x86 code (which can run on an x86_64 CPU) which the test emulator runs.  it does not emulate ARM at all.  a regular app cannot run.  if what you are referring to is this, it is not what i want.

---

### Post by TheFu on 2020-03-13
> **Skaperen said:**
> is it really limited to *test apps*?  this is not a *test app*.  it is a regular app.

my understanding of this, if you are an app developer, you can build the source into a *test app* binary and run it in a test emulator.  this gets compiled into x86 code (which can run on an x86_64 CPU) which the test emulator runs.  it does not emulate ARM at all.  a regular app cannot run.  if what you are referring to is this, it is not what i want.

Android apps are almost always Java (the android-funky-flavor), which compiles into byte-code that any Android runtime environment can run, in theory. Not quite a binary - more like a cross-platform, Android Java Byte-code package.  It don't get converted to ARM or x86 code.

---

### Post by Skaperen on 2020-03-13
then what is the distinction of a "test app" vs. a (plain) "app"?

---

### Post by TheFu on 2020-03-14
> **Skaperen said:**
> then what is the distinction of a "test app" vs. a (plain) "app"?

Purely a google play store distinction.  Test apps aren't advertised and the number of downloads are limited - last time  did android stuff which was almost 10 yrs ago.  The links to any test app have to be provided directly by the dev.

---

### Post by Skaperen on 2020-03-16
i was also looking for an emulator in which i could switch versions of Android OS itself to try apps in different versions.  where does the Java engine run?  i presume it is in the OS.

---

### Post by grahammechanical on 2020-03-27
The purpose of ARCWelder is to help developers of Android apps use the Chrome OS to develop their apps. ARCWelder does not know the difference between an incomplete app that needs testing and an app that has been released into an Android app store.

You may be able to do what you want by installing Android-X86 on another partition.

[https://www.android-x86.org/](https://www.android-x86.org/)

I tried this a few years ago but could not get it to install. I think the failure was due to it needing to be installed on a FAT 32 partition and I was trying it on an EXT4 partition. I now see that things have moved on as EXT4 is a support filesystem.

[https://www.android-x86.org/installhowto.html](https://www.android-x86.org/installhowto.html)

Regards.

---

### Post by Skaperen on 2020-03-27
what do i need to run the latest version of Android?

---

### Post by TheFu on 2020-03-27
> **Skaperen said:**
> what do i need to run the latest version of Android?

A very new version of an Android phone.  Probably the $1200 Google Pixel phone.
if you want to develop for Android, then you need a fast Core i7, 64G of RAM, and the ADK bundle.  While the editor/ide is a personal preference, the bundled version will come with Eclipse which is about the slowest, most bloated, program i've ever seen. Far surpassing Outlook and iTunes in bloat and memory use.
[https://developer.android.com/studio](https://developer.android.com/studio)

I’m certain you've already found that link in all the vast searching that undoubtedly was performed before posting here.

---

### Post by Skaperen on 2020-03-27
what do i need to run the latest version of Android virtually on my x86-64 based laptop?

---

