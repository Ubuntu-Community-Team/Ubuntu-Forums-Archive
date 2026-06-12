---
title: "Atheros Network Interface Drivers Issue"
date: 2010-03-26
forum: Server Platforms
---

### Post by datajock on 2010-03-26
Hi,

I didn't realize that there is a different place for the Server Edition issues and probably posted my question to the wrong place. So, I'm adding a link here to my other post in the hopes that someone here will have an answer for me.

[http://ubuntuforums.org/showthread.php?t=1439205](http://ubuntuforums.org/showthread.php?t=1439205)


Thanks,
DJ

---

### Post by volkswagner on 2010-03-26
You will need to copy the driver files from the live environment to the correct location on your hard drive.

After installing Sever Edition, boot a live CD/USB Ubuntu desktop edition.  You should be able to copy the drivers from /lib/modules/2.6.28-16-generic/kernel/drivers/net/wireless/ath5k/ath5k.ko to your hard drive install.

You may need to mount the hard drive if not mounted already.

While running the live cd you can verify the the driver is ath5k or similar by running

```
lsmod
```

Also note the Kernel number above will vary in you instance.  Also when copying to the server will be -server not -generic.

---

### Post by datajock on 2010-03-27
Thank you very much for this reply. I re-installed the server edition and then booted from the desktop cd as you proposed. I then copied over the directory from /lib/modules/2*/kernel/drivers/net/**atl1c** to the installation disk. Since I'm dealing with the wired network and not the wireless, this is the device driver module I seem to be missing under the server install.

I don't seem to be clear on how I them get this module actually added to the kernel though.

I tried doing a > modprobe -a atl1c but I just get an error saying that the module is not found.

Am I missing some step to tell the system that this new module directory (and file) are there?

Thanks again,
DJ

---

### Post by datajock on 2010-03-27
Update.

I ran the command ```
sudo modprobe
``` and then I was able to do a ```
sudo modprobe atl1c
``` but now get an error saying > Invalid module format.

So now I'm wondering if there is something different between these kernels that also makes it so this can't be done.

Thanks,
DJ

---

### Post by datajock on 2010-03-30
An update on this issue.

Just to see if this device driver is included in the beta-1 release of Ubuntu Server 10.04 LTS, I downloaded that ISO image as well and tried installing from it and even though I get the device driver kernel module 'atl1c' it does not support this Atheros Interface either.

After going back to Ubuntu Server 9.10, I attached a USB network adapter which was recognized and then did the following.
```
apt-get update
apt-get upgrade
```

After which this NIC is working! I believe the driver was upgraded in the process to a newer version.

So now I'm wondering if there is a way to get this updated driver included in the CD ISO image of the new version before it's officially released next month or is it too late.

I'm not sure this is the right place to make this request, so if this needs to be asked in some other place, please let me know.

Thanks,
DJ

---

### Post by datajock on 2010-04-02
After I did the previous "upgrade" stuff to get this working, I once again went back to see if I could figure out a better way to "fix" this issue.

I once again re-installed Ubuntu Server 9.10 and as it installed it complained about not finding a network interface. I went on with the installation and after rebooting the system I noticed that the network interface was in fact showing up when I ran ```
ifconfig -a
``` So I went ahead and just tried to configure the interface expecting it to get all kinds of errors.

I was pleasantly surprised to find that it works just fine. So it turns out that the device driver was there all along and it was only that the installing "probe" was not properly figuring it out.

I hope this is helpful to anyone else having a similar issue. Even if the network interface isn't being found during the install process, go ahead and finish it and look to see if it shows up anyway. Then see if you can configure it and have it work.

Turns out that's all I needed to do.

---

