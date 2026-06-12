---
title: "List of Android Apps that store on SD Card"
date: 2010-08-03
forum: The Cafe
---

### Post by HappinessNow on 2010-08-03
Please list Android Apps that store on SD Card:

here are the ones I have found thus far:

Barcode Scanner (by ZXing Team), version 3.4

Chrome (aka as Fake Google Chrome by Honiware & Biosoft), version 4.0

ClearDefaultHome (by TeslaCoil Software), version 1.1

EarthRot (aka Earth Live Wallpaper by Unixseb), version 1.3.8

Fennec (by Mozilla), version 1.9.3

Fish Food (by Tom Moor), version 1.21

Google Sky Map (by Google Inc.), version 1.5.2

GPS Status (by EclipSim), version 3.2

LED Disco (by coolbeans), version 0.51

Painting Findings (aka, Spot Differences: Paint Find; by Oluss Studio), version 1.3

Places Directory (by Google Places Directory Team), version 1.0.24

Radiant (by Hexage), version 2.9

Shopper (by Google Inc.), version 1.12

Smiley Pops (by Boolba Labs LLC), version 1.1.3

Super Tumble (by Camel Games), version 1.2.5

Tetronimo (by Mahoney), version 1.5.1

xScope (by xScope Mobile), version 5.36

***Pandora (by Pandora), version 1.3 ***(Please note, that if you use the Pandora widget it will become inoperable when you place Pandora on the SD Card, I suggest leaving Pandora on the phone for full functionality.)

Please share any others that you have found. ;)

---

### Post by amitabhishek on 2010-08-03
If you want you can install any application on SD card. #app2SD

Amit

---

### Post by HappinessNow on 2010-08-03
> **amitabhishek said:**
> If you want you can install any application on SD card. #app2SD

AmitActually this doesn't add any other functionality that Froyo 2.2 build# FRF91 doesn't already come with by default! 

You can not install "any" application on the SD Card with the "apps2SD" app, only the ones already set up by the Devs of each App.

Uninstalling apps2SD, because it does nothing new.
Same goes for SDMove!

---

### Post by amitabhishek on 2010-08-03
> **HappinessNow said:**
> Actually this doesn't add any other functionality that Froyo 2.2 build# FRF91 doesn't already come with by default! 

I reckon you have stock Google version of Froyo. 

Actually the vice versa is correct. In fact Froyo's ability to store apps on SD card is courtesy app2sd. Only that app2sd does it better. 

> **HappinessNow said:**
>  You can not install "any" application on the SD Card with the "apps2SD" app, only the ones already set up by the Devs of each App.

I am not sure since I am not an app. junkie but all the application that I normally use such as Twitter, ebuddy, OI file manager, twidroid etc can be backed up on SD card. In fact I don't even use market to install these apps. I just use adb to install these apk(s)/apps from SD card.

> **HappinessNow said:**
>  Uninstalling apps2SD, because it does nothing, I highly suspect this may be malicious software, BEWARE! I made a report to Google for investigation.

Same goes for SDMove!

I have never heard of SDMove but app2sd is created by a renowned Android developers called Wes Garner & Chris Soyars and has been a permanent fixture on Cyanogen ROMs since Cupcake.

---

### Post by HappinessNow on 2010-08-03
> **amitabhishek said:**
> I reckon you have stock Google version of Froyo. 

Actually the vice versa is correct. In fact Froyo's ability to store apps on SD card is courtesy app2sd. Only that app2sd does it better. 



I am not sure since I am not an app. junkie but all the application that I normally use such as Twitter, ebuddy, OI file manager, twidroid etc can be backed up on SD card. In fact I don't even use market to install these apps. I just use adb to install these apk(s)/apps from SD card.



I have never heard of SDMove but app2sd is created by a renowned Android developers called Wes Garner & Chris Soyars and has been a permanent fixture on Cyanogen ROMs since Cupcake.Thanks for the update, I am glad to hear they are good people, I am just highly suspect when an app simply duplicates a default function, but it is a bling-bling gui, if your into that.

---

### Post by Elfy on 2010-08-03
I assume then that you will edit post #3.

---

### Post by HappinessNow on 2010-08-03
> **forestpiskie said:**
> I assume then that you will edit post #3.
Post already edited ;)

> **HappinessNow said:**
> Last edited by HappinessNow; **2 Minutes Ago** at 01:07 AM..

your post made:

> **forestpiskie said:**
> **1 Minute Ago**

---

### Post by Elfy on 2010-08-03
Thanks - I must have refreshed before you edited.

---

### Post by HappinessNow on 2010-08-03
> **forestpiskie said:**
> Thanks - I must have refreshed before you edited.
No worries, Thanks for keeping up on the Moding :p

---

### Post by Elfy on 2010-08-03
It's ok - I often have a quick look at [s]spammy[/s] cafe threads ;)

---

### Post by HappinessNow on 2010-08-04
> **amitabhishek said:**
> I reckon you have stock Google version of Froyo. 

Actually the vice versa is correct. In fact Froyo's ability to store apps on SD card is courtesy app2sd. Only that app2sd does it better. 



I am not sure since I am not an app. junkie but all the application that I normally use such as Twitter, ebuddy, OI file manager, twidroid etc can be backed up on SD card. In fact I don't even use market to install these apps. I just use adb to install these apk(s)/apps from SD card.



I have never heard of SDMove but app2sd is created by a renowned Android developers called Wes Garner & Chris Soyars and has been a permanent fixture on Cyanogen ROMs since Cupcake.

> 

To install an app to the SD card on Android Froyo, the application itself needs to support it. In my experience though, most current apps can be moved to the external storage. However, the Froyo system installs all new applications on your device’s internal memory by default, except for those that explicitly request external installation. Luckily, it’s possible to make your Android 2.2 phone put apps on the SD card by default instead. Here’s how:

1. First you have to enable USB debugging on your Android device from Settings > Applications > Development > USB debugging.

2. Now you need to download and install the Android SDK on your computer from [http://developer.android.com/sdk/](http://developer.android.com/sdk/). Once you’ve downloaded and extracted the package to the folder of your choice, run SDK Setup.exe and click on Available Packages to the left. If you get an error message at this point, enable “Force [https://…”](https://…”) in the Settings. From the list of available packages, select “Usb Driver package”, click on the Install Selected button in the bottom right corner and follow the prompts.

3. Connect your phone to your computer with a USB-cable. Your OS will prompt you to install new drivers. Choose to install them from the android-sdk/usb_driver folder. Do not mount your device; you only need to plug-in the cable.

4. Next, run a command prompt and navigate to the Android-SDK\tools folder. In Windows, this is done by selecting Run from the Start Menu (or by pressing Win+R) and typing cmd. You change drives in the command prompt by entering the drive letter followed by a colon (:), and change folders with the CD command. For example, to enter the Android-SDK folder, simply type cd android-sdk.

5. In the Android-SDK\tools folder, type in adb devices and you should get a serial number starting with “H” in return. All you have to do next is entering adb shell pm setInstallLocation 2. Voilà, you’re done! Android will now install apps to the SD card by default.

6. To switch back to storing software on the internal memory, enter adb shell pm setInstallLocation 0.

I should point out that it’s preferable to install certain apps to the main memory, since it will take a while before the SD card becomes available when you start your phone. Applications installed on the memory card will also be unavailable to the system each time you mount your phone as a disk drive. The internal storage is probably quicker as well, even though Google claims that “there is no effect on the application performance so long as the external storage is mounted on the device.” In general, apps that integrate with the Android OS and that often run in the background is better to install on the internal storage, while games and most other applications will have no problem chilling outside on your SD.[http://goo.gl/ggRg](http://goo.gl/ggRg)

---

