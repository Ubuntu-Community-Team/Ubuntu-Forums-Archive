---
title: "How to install cyanogen on ubuntu phone nexus 4?"
date: 2016-05-01
forum: Ubuntu Phone and Tablet
---

### Post by alxgvr on 2016-05-01
Hi. Have Ubuntu touch Nexus 4. Want to install Cyanogen mod.
Can not copy cyanogen .zip to /sdcard to proceed instalation. Have only acces to /home folder. 

failed to copy 'cm-13.0-20160429-SNAPSHOT-ZNH0EAO2YJ-mako.zip' to '/sdcard/0/': Read-only file system&#65279;

There is a command to move image to the phone : adb push image.zip /sdcard/0/
This commant doesnt work with ubuntu phone. There is no "/sdcard/0/" on ubuntu phone, as I understand.  What path should I type?&#65279;
Or how can I get root acces (write permission) to nexus4 filesystem to copy this file manually?

P.S. I have cyanogen recovery installed sucesfully (fastboot). But can not install OS image with fastboot

"fastboot update cm-13.0-20160429-SNAPSHOT-ZNH0EAO2YJ-mako.zip

archive does not contain 'android-info.txt'
archive does not contain 'android-product.txt'
error: update package has no android-info.txt or android-product.txt"

---

### Post by NightCrawler on 2016-05-04
> **alxgvr said:**
> Hi. Have Ubuntu touch Nexus 4. Want to install Cyanogen mod.
Can not copy cyanogen .zip to /sdcard to proceed instalation. Have only acces to /home folder. 

failed to copy 'cm-13.0-20160429-SNAPSHOT-ZNH0EAO2YJ-mako.zip' to '/sdcard/0/': Read-only file system&#65279;

There is a command to move image to the phone : adb push image.zip /sdcard/0/
This commant doesnt work with ubuntu phone. There is no "/sdcard/0/" on ubuntu phone, as I understand.  What path should I type?&#65279;
Or how can I get root acces (write permission) to nexus4 filesystem to copy this file manually?

P.S. I have cyanogen recovery installed sucesfully (fastboot). But can not install OS image with fastboot

"fastboot update cm-13.0-20160429-SNAPSHOT-ZNH0EAO2YJ-mako.zip

archive does not contain 'android-info.txt'
archive does not contain 'android-product.txt'
error: update package has no android-info.txt or android-product.txt"

Update your android-tools and re-try again. That error with fastboot happened to me when my android tools were the older version then the image I was trying to install was built with. Best to download directly from android.com and try to push to phone with that version.

---

### Post by mike-chunkmedia on 2016-09-29
Hello, I've installed android-tools from the android web site and it is running fine on my Ubuntu 16.04Lts laptop. Please can you explain how to push to my Nexus 4 that is in CyanogenMod Recovery mode using the new android-tools? Thanks, Mike

---

### Post by krusty8 on 2016-09-30
> 
P.S. I have cyanogen recovery installed sucesfully (fastboot). But can not install OS image with fastboot

"fastboot update cm-13.0-20160429-SNAPSHOT-ZNH0EAO2YJ-mako.zip

archive does not contain 'android-info.txt'
archive does not contain 'android-product.txt'
error: update package has no android-info.txt or android-product.txt"

Looking here [https://wiki.cyanogenmod.org/w/Install_CM_for_mako](https://wiki.cyanogenmod.org/w/Install_CM_for_mako) , the next step after installing the recovery is to push to /sdcard

---

### Post by mike-chunkmedia on 2016-09-30
Thanks. I'm getting nothing with either lsusb or sudo adb devices - my phone is not listed. Any ideas? Also, will the now install of android-tools be in the PATH now rather than the old version I was using? Thanks again, Mike

---

### Post by krusty8 on 2016-09-30
> **mike-chunkmedia said:**
> Thanks. I'm getting nothing with either lsusb or sudo adb devices - my phone is not listed. Any ideas?

Mhm, can you paste the output of lsusb here? Maybe best to do three versions:
[LIST]
[*]nothing attached to usb 
[*]attach the device in fastboot mode 
[*]attach the device in recovery mode 
[/LIST]

Also, what do you mean with *nothing*. lsusb certainly doesn't produce no output at all. what output if any does adb devices produce *exactly*? with and without sudo.


> Also, will the now install of android-tools be in the PATH now rather than the old version I was using? Thanks again, Mike

Well, it's a bit hard to tell from a distance. Don't know what *exactly* you have done when 
> I've installed android-tools from the android web site
link? Or what *exactly *it means that 
> and it is running fine on my Ubuntu 16.04Lts laptop
Define *running fine*

I'd look at the details of what that installation did and the outputs of 
```

which adb
whereis adb
echo $PATH
adb --version

```

But, overall I'd say lets focus on the > getting nothing with either lsusb or sudo adb devicesbit first - I wouldn't expect that the different adb installations actually have a big impact here.

---

