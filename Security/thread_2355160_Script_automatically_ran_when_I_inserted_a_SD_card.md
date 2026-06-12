---
title: "Script automatically ran when I inserted a SD card in the Card slot?"
date: 2017-03-09
forum: Security
---

### Post by Gstrazds on 2017-03-09
Question; Why are scripts automatically allowed to run, when I inserted an SD card into the SD Card slot?

I wanted to know if my SD controller bad was or not. By extension; is the SD card bad - which it is.

I made the mistake of inserting someone else's SD Card into my slot to prove the controller works; in Ubuntu 16.4
It contained a malware script targeted at Linux.

What happened next; was all the pictures, documents were on their way to being sucked into the card - the script knew exactly where to look; halfway through the process which occurred quite quickly, I clicked cancel which stopped the half completed process.

Is there a switch to enable; to force a script to seek permission to launch? 

Reminds me of the Windows auto load feature which I could disable.

I installed chkrootkit V. 0.51 and ran it; happily, it found nothing.:)

---

### Post by TheFu on 2017-03-10
a) Don't allow automatic mounts. [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)
b) Don't make the mount permissions allow execute permissions - that is usually handled by the file_mode setting for mounts.  Use 640, not 777.  There is a 'noexec' mount option too.

*The power to mount is the power to destroy.* Sorta like taxes. Convenience should not override common sense security, IMHO.

[https://askubuntu.com/questions/489306/execute-script-on-insertion-of-sdcard](https://askubuntu.com/questions/489306/execute-script-on-insertion-of-sdcard) may be how it was setup to automatically run a program.  [https://ubuntuforums.org/showthread.php?t=1648939](https://ubuntuforums.org/showthread.php?t=1648939) has more examples.

---

### Post by Gstrazds on 2017-03-10
Useful advice from TheFu; 

Not worried about mounting the SD card; Just not letting the malicious script execute;

Autostart - removable media also assessable in the About this computer tab located in the Shutdown menu. 
 
I clicked on the Never prompt or start programs on media insertion. 

So my problem is solved. 

> Configuring Program Autostart

To control which programs automatically start when you plug in a device, go to System-Settings - Details - Removable Media. 
For more complex scenarios, see [UsbDriveDoSomethingHowto]("https://help.ubuntu.com/community/UsbDriveDoSomethingHowto").


The balance of TheFu reply offers system adjustments; should you want to go further; Examples of scripts that are executable in a good way.

---

### Post by lisati on 2017-03-10
@Gstrazds: I've edited your post to use the default font, to make it easier for those of us who use glasses to read.

If your problem is solved, please use the "Mark thread solved" option of the "Thread tools" drop-down menu.

---

