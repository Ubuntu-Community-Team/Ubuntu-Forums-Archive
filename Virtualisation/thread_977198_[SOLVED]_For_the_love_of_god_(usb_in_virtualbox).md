---
title: "[SOLVED] For the love of god (usb in virtualbox)"
date: 2008-11-10
forum: Virtualisation
---

### Post by nakama85 on 2008-11-10
Please can someone help me. 
I am running xp in Vbox on 8.10.
The only reason I am doing this is because I have a zune that will only run on windows.But n-e-ways
I can't get virtualbox to see my usb devices.(zune, printer,cam) 

After researching I only found something about fstab and I did what the post described (i think) still nothing.

I dont get any error or anything. It's just when I go usb devices in VB it says no devices connected or available or whatever.

Any help would be appreciated. (step-by-step...for the newb please)
thanks

......sorry for the rant I am just so mad at MS for making a device that only works with their stuff. At least apple made it so their stuff works with MS.

---

### Post by bumanie on 2008-11-10
[Follow this]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html") -it is a bit dated, but as far as I know it still works - to get usb support you need the proprietary 'free for home use' version.

---

### Post by Ocxic on 2008-11-10
you added ```
none      /proc/bus/usb       usbfs        devgid=46,devmode=664     0  0 
```to your /etc/fstab file then ran "sudo mount-a" or rebooted and it still doesn't work.

the above link will not work with 8.10 as the config files has changed, the above method should get you going, it's what worked for me.

---

### Post by bodhi.zazen on 2008-11-10
> **nakama85 said:**
> Please can someone help me. 
I am running xp in Vbox on 8.10.
The only reason I am doing this is because I have a zune that will only run on windows.But n-e-ways
I can't get virtualbox to see my usb devices.(zune, printer,cam) 

After researching I only found something about fstab and I did what the post described (i think) still nothing.

I dont get any error or anything. It's just when I go usb devices in VB it says no devices connected or available or whatever.

Any help would be appreciated. (step-by-step...for the newb please)
thanks

......sorry for the rant I am just so mad at MS for making a device that only works with their stuff. At least apple made it so their stuff works with MS.

What did you put in /etc/fstab ?

did you reboot or at least sudo mount -a and log off and back on ?

---

### Post by nakama85 on 2008-11-10
none      /proc/bus/usb       usbfs        devgid=46,devmode=664 0 0

yes this is the code i used accept devgid=126
thanks for the quick reply quys

---

### Post by nakama85 on 2008-11-10
i did reboot but not sudo mount -a.... what does this do?

---

### Post by nakama85 on 2008-11-10
so is the fact that i am using virtualbox ose the problem?

also if i have to switch to personal use will i be able to keep my current VB install of xp?

---

### Post by HotShotDJ on 2008-11-10
> **nakama85 said:**
> so is the fact that i am using virtualbox ose the problem?Yes.  The OSE version does not support USB
> **nakama85 said:**
> also if i have to switch to personal use will i be able to keep my current VB install of xp?Yes.  I have switched between OSE and PUEL versions using the same VDI.

---

### Post by nakama85 on 2008-11-10
> **HotShotDJ said:**
> Yes.  The OSE version does not support USB
Yes.  I have switched between OSE and PUEL versions using the same VDI.

Ok so the problem I have no is that when I look in the 
 /etc/init.d/mountdevsubfs.sh 
file to change the code like the above tutorial mentions. I get the exact same file as when I had ose.
another words there is no point in the file that says

#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

any ideas on how to rebuild that file
?

---

### Post by HotShotDJ on 2008-11-10
> **nakama85 said:**
> /etc/init.d/mountdevsubfs.sh You do NOT need to edit that file.  Put your hands where I can see them and step away from the keyboard. :)

See my post here: [http://ubuntuforums.org/showthread.php?p=6090383](http://ubuntuforums.org/showthread.php?p=6090383)

It should get you up and running with USB support.

---

