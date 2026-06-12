---
title: "Making usb bootable"
date: 2014-12-06
forum: Windows
---

### Post by peter164 on 2014-12-06
Hi. I want to go back to Windows 7. I have the iso file downloaded, i opened startup disk creator and clicked the "other" and opened my file, but nothing happened? Is there any other way i can get windows 7 on my usb??

---

### Post by flaymond on 2014-12-06
That was known issue on the recent release. Startup disk creator contain bugs. You can try other alternative like mkusb (you need to manually installing it using ppa). If mkusb failed to detect your USB, you need to see if it in FAT32 format. If not, install GParted to reformat back the USB. Here is the code to install mkusb on your system.

```
 
sudo add-apt-repository ppa:mkusb/ppa  # and press Enter to accept it
sudo apt-get update
sudo apt-get install mkusb

```

and to run it :

```
 gksudo mkusb 
```

You can refer here if you stuck or need more information - [URL="http://ubuntuforums.org/showthread.php?t=1958073"]http://ubuntuforums.org/showthread.php?t=1958073

[/URL]

---

### Post by C.S.Cameron on 2014-12-06
I don't think UNetbootin works with Win 7.
Microsoft has a tool for making usb installer.

[http://www.microsoft.com/en-us/download/windows-usb-dvd-download-tool](http://www.microsoft.com/en-us/download/windows-usb-dvd-download-tool)

---

### Post by howefield on 2014-12-06
Thread moved.

---

### Post by peter164 on 2014-12-06
bump

I have the iso i just need a way to make it bootable????

---

### Post by flaymond on 2014-12-06
Use GParted to make it bootable. But, using installer is more better, why...you just need to set the iso file and the device...then it will do your work including make it bootable. Better use installer.


* Caution - Windows is not free. Maybe it prompt you a product key to input while in the installing process.

---

### Post by coffeecat on 2014-12-08
> **peter164 said:**
> bump

I have the iso i just need a way to make it bootable????

C.S.Cameron has already answered this in post #3

---

