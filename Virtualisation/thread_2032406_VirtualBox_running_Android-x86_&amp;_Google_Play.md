---
title: "VirtualBox running Android-x86 &amp; Google Play"
date: 2012-07-23
forum: Virtualisation
---

### Post by Lyfang on 2012-07-23
Hi, I'm using VirtualBox to run either Android-x86 4.0-RC2 live installation iso for ASUS Eee PC family [android-x86-4.0-RC2-eeepc.iso]("http://android-x86.googlecode.com/files/android-x86-4.0-RC2-eeepc.iso") or [android-x86-vm-20120130.iso.gz]("http://www.buildroid.org/Download/android-x86-vm-20120130.iso.gz") (use at your own risk as usual) however I'm not able to install apps from Google Play.

I downloaded VirtualBox from the repositories.
```
sudo apt-get install virtualbox
```

Then I have mounted the CD image in VirtualBox. I also recommend installing VirtualBox Extension Pack & Guest Additions.

See also: [android-x86 VirtualBox/VMWare support | BuilDroid]("http://www.buildroid.org/blog/?p=86")

---

### Post by Lyfang on 2012-07-26
Making progress, any help is still greatly appreciated! Mount in VirtualBox: [android-x86-4.0-RC2-eeepc.iso]("http://android-x86.googlecode.com/files/android-x86-4.0-RC2-eeepc.iso") 
No Internet at first. Browser displays: "Webpage not available"
Run from Terminal Emulator:
```
su
netcfg eth0 dhcp && setprop net.dns1 4.2.2.1
```
Browser displays: "Google"

You can also display networking adapters by using the following command from Terminal Emulator:
```
ip a
```

"Turning Wi-Fi on..." problem in Google Play. [QUOTE=Imrazor]I can not associate my Google account with either the Market or GMail. Every time I try, ICS insists on trying to connect via WiFi, which obviously fails since there is NO wireless card in my desktop.[/QUOTE] Source: [[android-x86] Force Market to use eth0?]("http://grokbase.com/t/gg/android-x86/123p4j9aba/force-market-to-use-eth0")

---

### Post by Lyfang on 2012-07-28
An alternative could be the QEMU (emulator) running [ARM with Android 2.3.4]("http://l4android.org/download/download.html").

---

### Post by Lyfang on 2012-07-30
Please help me install Socialcam on my PC using VirtualBox or QEMU: [Socialcam - Android Apps on Google Play]("https://play.google.com/store/apps/details?id=com.socialcam.android")

---

### Post by Lyfang on 2012-08-01
Searching for a wlan patch for the Android-x86 OS to get VirtualBox support; to access wlan0 with no wireless network available in VirtualBox.

---

