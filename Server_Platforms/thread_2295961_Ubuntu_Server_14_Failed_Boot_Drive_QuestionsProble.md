---
title: "Ubuntu Server 14 Failed Boot Drive Questions/Problems"
date: 2015-09-22
forum: Server Platforms
---

### Post by Mike_Burt on 2015-09-22
Hi I have a Lenovo ThinkServer that had Ubuntu Server 14 running from an USB flash drive as the boot drive (Yes I know this wasn't the smartest thing to do) and X2 3TB drives inside the tower in which I used Webmin to configure the drives in Raid 1. This was all created a year ago and everything was running fine, used the server for storing my files,plex,remotely access my files, It was a headless server. A week ago I noticed that the server wouldn't start it would show a black screen after the Lenovo logo shows. The USB drive doesn't have any light to indicate any activity. I came to the conclusion that I may be the USB drive that failed on me so I plugged it into a Windows, Linux, and Mac machine and it wouldn't show up. So I guess it failed. My question is that how do I go about my Raid 1 configuration drives, Did I lose my data? Can I set up a new boot drive and still gain access to it? Can I remove the drives and connect them to an external adapter and copy off my files onto another drive? 
Also seeing that I have to start over would it be in my best interest to install and use a SSD drive as my primary boot drive (nothing will be stored on it just the operating system and updates file) Everything else will be stored on the X2 3TB drives. Thanks in advance for any suggestions and advice.

---

### Post by darkod on 2015-09-22
Did the stick have only the /boot partition on it?

First of all, the data on the raid should be fine. I assume you can boot the server with a cd or usb stick right? Get the Desktop version so you can boot it into live mode. That will help you saving the data and/or repairing the boot.

As for your ssd question, a ssd only to boot from would be sort of a waste. You could have the boot/root on the 3TB disks too, but that depends how you set things up and whether you are willing to start from scratch (using the saved data from the raid of course).

---

### Post by Mike_Burt on 2015-09-22
> **darkod said:**
> Did the stick have only the /boot partition on it?

First of all, the data on the raid should be fine. I assume you can boot the server with a cd or usb stick right? Get the Desktop version so you can boot it into live mode. That will help you saving the data and/or repairing the boot.

As for your ssd question, a ssd only to boot from would be sort of a waste. You could have the boot/root on the 3TB disks too, but that depends how you set things up and whether you are willing to start from scratch (using the saved data from the raid of course).



Thanks for your input, I will try using a live version of Ubuntu deskstop to copy over my data. For the SSD, I really meant it would be for the boot/root partition just as the usb flash drive was but this time it would be inside other than being attached to outside connected to a usb port. I really just want only my files on the drives. I will be starting from scratch using my saved data from the Raid.

---

### Post by darkod on 2015-09-22
OK, in that case it's best to use live mode and copy the data to external disk to have a backup. Then after you get the SSD make a new installation on it, and you can re-use the existing raid1, no need to destroy it and copy data from the backup. We can work on it when you get the SSD.

For now you can verify data is there and make copy. Note that mdadm is not included by default in live mode so you need to add it first and assemble all arrays:
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

You need to do that each reboot in live mode because it doesn't remember it from last time.

After that you should be able to access the raid.

---

### Post by Mike_Burt on 2015-10-05
> **darkod said:**
> OK, in that case it's best to use live mode and copy the data to external disk to have a backup. Then after you get the SSD make a new installation on it, and you can re-use the existing raid1, no need to destroy it and copy data from the backup. We can work on it when you get the SSD.

For now you can verify data is there and make copy. Note that mdadm is not included by default in live mode so you need to add it first and assemble all arrays:
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

You need to do that each reboot in live mode because it doesn't remember it from last time.

After that you should be able to access the raid.

Ok I was able to install the desktop version of ubuntu and I was able to run the set of commands you gave above. The drives came up and I was able to copy from it. Please explain to me how to get my raid drives (reusing existing raid 1) back as they are once I install the server version with webmin. Thanks in advance.

---

### Post by darkod on 2015-10-06
There are few options. Actually I think that while installing the server version it will detect the array and ask you if you want to activate it. Just be careful not to format it. You can also select not to include the array while installing and do it yourself later. It sounds like a safer option. And it's easy to re-assemble existing array, as you saw. You can even decide to have the raid disks disconnected during the server installation. You are not installing the OS onto the raid anyway. Just make sure you disconnect them together and to connect them together later.

As for webmin, I don't use it and have no clue how it deals with raid. Also it's not an official tool so I would avoid managing important things like the raid with webmin.

In fact, if you can avoid using it at all.

---

### Post by Mike_Burt on 2015-10-15
> **darkod said:**
> There are few options. Actually I think that while installing the server version it will detect the array and ask you if you want to activate it. Just be careful not to format it. You can also select not to include the array while installing and do it yourself later. It sounds like a safer option. And it's easy to re-assemble existing array, as you saw. You can even decide to have the raid disks disconnected during the server installation. You are not installing the OS onto the raid anyway. Just make sure you disconnect them together and to connect them together later.

As for webmin, I don't use it and have no clue how it deals with raid. Also it's not an official tool so I would avoid managing important things like the raid with webmin.

In fact, if you can avoid using it at all.


Ok I got my server back up running Ubuntu Server 14 and I am now able to you my raid drives just like before. I actually used Webmin for this process as that's how I did it the first time. Thanks

---

