---
title: "how to install linux on a notebook that does not have a dvd-drive"
date: 2015-01-17
forum: The Cafe
---

### Post by dilbert_one on 2015-01-17
hello dear experts hello all ubuntuusers


i am about to buy a notebook with out any  dvd-drive. 

the question how to install linux?


what is the way to install Suselinux 


what is the procedure to install OpenSuse linux from a USB flash drive 

    Acquire the correct OpenSuse installation files ('the ISO')
    Put OpenSuse onto your USB flash drive
    Configure the computer to boot from USB flash drive and boot from it

    how to install opensuse to my internal drive (hard disk drive or solid state drive)
    
    
    note: i plan to buy a subnetbook that has no CD or DVD-Drive. 
    
    which ways do we have to do a 
    
    a. fresh installation on a notebook 
    b. do do updates from time to time 
    
    
    
    love to hear from you 
    
    
    btw: i allready did some steps: 
    
    
    a. i allready have created a rescue-system for the emergency-situation:

    i created a little resque-usb for SUSE-DVD on USB-Stick 

  a litle Rescue-USB while using Suse-ISO DVD on a USB medium 1:1 copied

step 1. Suse-ISO download:

here: [http://ftp5.gwdg.de/pub/linux/suse/opensuse/distribution/13.2/iso/openSUSE-13.2-Rescue-CD-x86_64.iso](http://ftp5.gwdg.de/pub/linux/suse/opensuse/distribution/13.2/iso/openSUSE-13.2-Rescue-CD-x86_64.iso)

step 2 copy the file onto a USB stick with the following command 

```
dd if=openSUSE-13.2-Rescue-CD-x86_64.iso of=/dev/sdX bs=32k

```

where sdX=sdb or sdc is the USB stick 
ready - now i can test the rescue-usb

question:  can i use this usb-stick to install the linux on a notebook?

love to hear from you
    

see more:
    
```

linux-70ce:/home/martin # dd if=openSUSE-13.2-Rescue-CD-x86_64.iso of=/dev/sdb bs=32k
18925+0 Datensätze ein
18925+0 Datensätze aus
620134400 Bytes (620 MB) kopiert, 71,5018 s, 8,7 MB/s
linux-70ce:/home/martin #
 
```   
    
   
other ways to do this are the following: 

a.  "SystemRescueCD"
[http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage)

b. However, the openSUSE website has much information on doing this exact thing already, 
both with command-line tools and via GUI:

[https://en.opensuse.org/SDB:Live_USB_stick#Using_commandline_tools](https://en.opensuse.org/SDB:Live_USB_stick#Using_commandline_tools)

---

### Post by sudodus on 2015-01-17
Yes, you can use a pendrive flashed with ***dd*** from an iso file to try, install and repair linux :-)

But dd is risky. It is nick-named 'disk destroyer' because there is no check-point, where it gives you a second chance to see, that you write to the correct drive. Many people have overwritten another drive and in some cases destroyed valuable data that were not backed up :-(

For this reason I made ***mkusb***, that wraps security around ***dd***, [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

There are many other tools, that also help you install from an iso file to a pendrive, [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by sudodus on 2015-01-17
Do you want to keep Windows? In that case things are more complicated - dual booting with UEFI can be hard depending on how UEFI is made in that particular computer.

There is a good wiki page about [booting with UEFI]("https://help.ubuntu.com/community/UEFI"), and a good tutorial thread, [UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295")

---

### Post by grahammechanical on 2015-01-17
What advice do you get from the OpenSuse forum? It seems like you already know. So, why are you here?

---

### Post by dilbert_one on 2015-01-17
hello dear ubuntu-experts, 


@graham - well i think that i have done some preliminary steps in creating a rescue stick for some other aims and reasons  - that was monts ago. 

now i think that i can use this knoweldge. 



@gaham: here i get more detailed infos. i love this forums. therefore i am here.



first of all many many thanks for the replies with the hints - they are very very valuable. i am happy to read your tips. 

well first of all: what is aimed. i want to buy a new notebook that has no (!!!) dvd.

and on this notebook there is installed either 

a. a windows 
b. no operating system at all 

well - if there a windows system on the machine - i guess it wold support my plans. 

and in the end i would erase the windows subsequently - after the linux is on the notebook 


**- btw:** i have to digg deeper  what all the **uefi-things** mean. i am no expert if it comes to these things.


and i am thankful for the hint

> 
For this reason I made ***mkusb***, that wraps security around ***dd***, [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)


thanks for all the tipps

and yes: 
here i get more detailed infos. i love this forums. therefore i am here.
keep up the great work here.

---

### Post by sudodus on 2015-01-17
If you have used linux before and you know what to expect, or if you have a friend, colleague or relative who can help you, you can buy a computer with no operating system at all or maybe with a minimal DOS. Otherwise it might be an overwhelming experience to start with linux.

Anyway, you are welcome here, and we will try to help you :-)

And we are not experts, we are users, some of us beginners, some of us more experienced, but all of us are volunteers.

---

