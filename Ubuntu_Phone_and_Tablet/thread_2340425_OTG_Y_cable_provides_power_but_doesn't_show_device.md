---
title: "OTG Y cable provides power but doesn't show devices connected"
date: 2016-10-18
forum: Ubuntu Phone and Tablet
---

### Post by sitongia on 2016-10-18
I'm running OTA-13 on a Nexus 4. I have a Y OTG cable. When I plug power into the Y and then the Y into the phone, it shows power. Then, when I plug a USB thumbdrive into the USB, it doesn't show any action in the syslog. I've read elsewhere that this should work. Is the problem with my particular cable, or the micro-USB connector on the phone, or ? What should I try?

Thanks,
==Leonard

---

### Post by dtarrant on 2016-10-19
I've just used an OTG cable to transfer data between my M10 tablet and a USB thumbdrive. At first I coudn't see the thumb drive with the Ubuntu Touch file manager. Using a blank v32 FAT usb thumb drive, I fired up the tablet external drive app and selected format. This created a number of folders: Documents; Downloads; etc. Once the thumbdrive had been formatted in this manner, it was recognised by the file manager and I was able to cut and paste files between the thumb drive and the tablet. Note that the safely remove device option lies within the external drive app. Hope this is helpful. It took me a long time to discover the trick by trial and error.

---

### Post by sitongia on 2016-10-20
Thanks. Those are good ideas. It doesn't work for me on my Nexus 4. In the External Drives app the page says SD Card Management and it is blank below that line.

---

### Post by T2uiYKb7 on 2016-10-23
I've got a similar thread at the moment.

[https://ubuntuforums.org/showthread.php?t=2340122](https://ubuntuforums.org/showthread.php?t=2340122)

I don't have a Y cable though it's a little more complex (it has three modes to choose between) I'm also using x86 Ubuntu (a Windows tablet.)

Under Windows it works perfectly but I have various issues on Linux.

I've had my thread open a while had a bunch of views but no answers. I guess what you can take from this little rant of mine is that Linux uses USB differently than Android and Windows even on the same device.

They call it **[COLOR=#008000]USB ACA[/COLOR]** or **[COLOR=#008000]Power + Host[/COLOR] **(that may help you in Googling an answer) when a devices uses power and data at the same time. Some people say it's impossible and your imagining things or it's proprietary but it is part of the official USB standard.  You'll be looking for a way to manually change how Ubuntu uses USB. (I haven't had any luck.)

---

### Post by sitongia on 2016-10-23
andrew.nz, thank you for your response. I feel pretty discouraged about this. I recently started using Ubuntu Touch and it's really close to being great, but there's little help, here or Ask Ubuntu. I've been posting bug reports, too, and there's little response. I'm also trying to install the SDK so that I can get the code and try to fix it myself, but I can't get the SDK to run on my x86 Ubuntu desktop. All we can do is post and collect "me, too"s and hope that a developer will take it up.

---

### Post by T2uiYKb7 on 2016-10-23
I'm going to try [linuxforums.org]("http://www.linuxforums.org/") and [superuser.com]("http://superuser.com") in the future when I have complex questions.

I think there more likely to have Linux developers posting in them.

There  are some really knowledgeable people on this forum (far more so than  me) but I still think there are a fare few questions that go over  everyone's heads.

---

### Post by dtarrant on 2016-11-04
I have some more information to share. I have discovered that there are two variables that affect whether a usb flash drive connected via an OTG cable is recognised by the M10 file manager. 

These are:

1. How the flash drive was formatted. Using the M10 External Drive app works for me;

2. The brand of flash drive used.

I found that a 2GB Transcend flash drive was always recognised by the External Drive app, but frequently not seen by the file manager.

I had more success with an 8GB Toshiba flash drive which was detected by the file manager and I was able to copy 1GB of files to the M10.

---

### Post by sitongia on 2016-11-04
I've tried 4 USB devices and 2 OTG cables (one of which has power and the other does not). I suspect that the problem is the Nexus 4 phone. Thanks for working on this.

---

