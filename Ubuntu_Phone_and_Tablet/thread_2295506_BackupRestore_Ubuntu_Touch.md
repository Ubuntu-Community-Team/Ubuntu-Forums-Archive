---
title: "Backup/Restore Ubuntu Touch"
date: 2015-09-19
forum: Ubuntu Phone and Tablet
---

### Post by ubogreg on 2015-09-19
Hi Ubuntu Phone Experts/Fans,  

after a system update or other changes to the system it could be that your phone is unresponsive or does not work as expected. 
Therefore it is important to have a backup of your system, so it can be restored to the state before the changes/update.  

How do you do full system backup/restore? 

 Is it possible to backup/restore single partitions?  

What can be restored in the recovery mode? 

 How can adb activated if the developer mode on the phone cannot be activated on the graphical user interface?  

What's your experience?    


Any information you can provide me would be greatly appreciated.  

Greg

---

### Post by grahammechanical on 2015-09-19
And there was I thinking that you were going to tell us the answer. :)

If I was to purchase a Ubuntu mobile device because it was a commercial product  I would expect the manufacturer to provide that information in a user guide. Here is the user guide for one of the Ubuntu Phones models on the market.

[https://static-bqreaders.s3.amazonaws.com/file/Ubuntu-Aquaris_E4_5/Manual_Aquaris_E4.5_ubuntu_EN.pdf](https://static-bqreaders.s3.amazonaws.com/file/Ubuntu-Aquaris_E4_5/Manual_Aquaris_E4.5_ubuntu_EN.pdf)

And here is a relevant page

[https://static-bqreaders.s3.amazonaws.com/file/Ubuntu-Aquaris_E4_5/Manual_Aquaris_E4.5_ubuntu_EN.pdf](https://static-bqreaders.s3.amazonaws.com/file/Ubuntu-Aquaris_E4_5/Manual_Aquaris_E4.5_ubuntu_EN.pdf)

I would not think of a Ubuntu mobile device in the same way as I think of Ubuntu on the desktop. I would also keep in mind that smart phones are meant to store their documents in the cloud. Or on a desktop or laptop.

[http://askubuntu.com/questions/602760/ubuntuphone-does-not-connect-to-ubuntu-desktop](http://askubuntu.com/questions/602760/ubuntuphone-does-not-connect-to-ubuntu-desktop)

Or may be run the latest version of Ubuntu which may have that library by default. Ubuntu 15.10 has at present libmtp 1.1.8.

Regards.

---

### Post by qduaty on 2015-10-14
/home/phablet is worth archiving because it contains user data (such as contacts, text messages). You can mount sshfs via adb or use adb as a shell to install and run archive tools on the device, such as 7zr.

---

### Post by Jaris on 2015-10-20
Hello,

I'm also interested in the FULL phone backup and restore solution as I plan play with software a little. 

From what I found (on the Meizu MX4 phone):

"fdisk" command showed, that there is only one physical disc:
Disk /dev/mmcblk0: 14,7 GiB, 15758000128 bytes, 30777344 sectors

So, theoretically I can backup /dev/mmcblk0 with dd. But backuping is only the half of what is expected: I'm not sure if I'm be able to restore that image in case of OS crash.

---

