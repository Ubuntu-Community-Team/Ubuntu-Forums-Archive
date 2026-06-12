---
title: "[Windows 10] No device drivers were found, when trying to setup dual-boot"
date: 2019-02-17
forum: Windows
---

### Post by hiiamu on 2019-02-17
Alright, so I'm new to Linux, still trying to get used to everything, I had Win 10 running on my system before swapping to Linux with no issues. I have 2 drives, a 1tb HDD, and a 1tb SSD. Currently, the HDD is where all my data is and my SSD is clean and unformatted. Booting to my USB Win10 install, I get to
 [ATTACH=CONFIG]282569[/ATTACH]
I set my layout to DVORAK, next, install, then instead of getting to the drive partitioning page like this,
 [IMG]https://images.drivereasy.com/wp-content/uploads/2017/03/img_58d234cf04ff1.jpg[/IMG]

I get the page saying I need to install extra drivers, like this screen
 [IMG]https://weblance.com.ua/uploads/posts/2017-05/1493745389_0_error_install_windows7_from_usb_on_intel_100_200_series.png[/IMG]
I have tried installing my MOBOs drivers on the flashdrive to install but it doesnt see any of them.

Here are all my drives
[ATTACH=CONFIG]282570[/ATTACH][ATTACH=CONFIG]282571[/ATTACH][ATTACH=CONFIG]282572[/ATTACH]

Any extra info needed I can provide

---

### Post by oldfred on 2019-02-17
Please attach screen shots, not post in line. 
Not all users have high speed Internet.

       If you use the Forum's advanced editor, you can use the paperclip icon to attach screenshots. Post #4 1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098) 
    
Are drives gpt partitioned or MBR(msdos) partitioned?
Windows only installs in UEFI boot mode to gpt drives and only in BIOS boot mode to MBR drives.
And how you boot install media, is then the boot mode that install will be.

---

### Post by CharlesA on 2019-02-18
Based on the install screenshot, it looks like it is only seeing your USB drive. How are the hard drive and SSD set up on the machine?

---

