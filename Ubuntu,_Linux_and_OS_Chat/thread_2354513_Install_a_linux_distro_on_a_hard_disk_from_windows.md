---
title: "Install a linux distro on a hard disk from windows. Like LiLi with persistent memory."
date: 2017-03-03
forum: Ubuntu, Linux and OS Chat
---

### Post by nnenov on 2017-03-03
Hello,
I'm a bit of strange situation. I haven't got any usb sticks or a CD drive, but I do have an empty 50GB ssd drive.
I am trying to follow [this walkthrough on using DDrescue ]("https://www.data-medics.com/forum/how-to-clone-a-hard-drive-with-bad-sectors-using-ddrescue-t133.html")which requires a boot USB/CD to run gddrescue to attempt to clone a damaged drive. (I have the old disk a new empty drive to clone to in addition to the empty 50gb drive I want to use to boot into linux and store the log file in persistent memory)
In the walkthrough, a USB is used which has persistent memory. They say to use [LiLi]("https://www.linuxliveusb.com/"), and this does allow me to use my SSD, but it gives NO option for persistent memory. Why is this? 
Please, if you can help me, bear in mind I am a complete amateur, the more concise and in depth your response the better, thank you all in advance.

---

### Post by yancek on 2017-03-03
The link below has a description of the process of using Lili to create a bootable flash drive and includes using persistence.  Do the steps shown look like what you saw.  You might also try unetbootin if you can't get Lili to work.  You don't say what OS you are using, windows?  Seems like it would be a lot simpler to just buy a flash drive, given the low cost.

[https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)

---

### Post by oldos2er on 2017-03-03
Doesn't appear to be an Ubuntu support question, so moved to Ubuntu, Linux and OS Chat.

---

### Post by nnenov on 2017-03-03
I am using windows 7, I agree, need to just get a usb drive, I already tried with an old usb stick, but LiLi again would not let me set persistent memory, it just says "Built-in persistence". when I tried booting from this usb, it didnt work, just boots to next bootable drive, and if I disable all boot devices except the usb stick, it just boots straight to bios.. maybe the usb is too old.
Sorry about posting to wrong category, thank you for moving it.

---

### Post by sudodus on 2017-03-03
Maybe it would be easiest for you to get a light-weight Ubuntu flavour, for example the light-weight Lubuntu, into the SSD (as a full install).

How big is your old USB stick? 1 GB or bigger?

I think you can use ***Win32 Disk Imager*** to install Lubuntu 16.04.1 LTS into the USB stick. You need no persistence in this step.

In the next step you boot from the USB stick and install Lubuntu into the SSD. It is easier and safer to install into the SSD, if you remove the other drives before starting this installation.

And then you can boot Lubuntu from your SSD and install whatever programs you want, for example ddrescue,

```
sudo apt-get install gddrescue
```

See the following links,

[Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

[Repair the partition table and file system of a pendrive](https://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

### Post by nnenov on 2017-03-03
Thank you Sudodus, that sounds like excellent advice! 
 I just found an old external cd writer so have taken a different approach: Made a live CD of knoppix (which has ddrescue 1.22 already installed) and then navigated to the plugged in usb drive (2gb), where I will save the logfile created by ddrescue, its writing now, hope its ok!

---

### Post by sudodus on 2017-03-04
Knoppix is a good alternative. Good luck :-)

And please come back and share your result for the benefit of other people with the same or similar problems.

---

