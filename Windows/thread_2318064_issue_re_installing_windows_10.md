---
title: "issue re installing windows 10"
date: 2016-03-22
forum: Windows
---

### Post by jesse49 on 2016-03-22
so im using winusb to make my external hard drive bootable and when i go to boot to it, windows just tells me that there is no operating system found, im not sure why this is happening, ive tried a few different things now, I tried unetbootin and all my different usb ports, nothing seems to be working, and now i cant boot back into ubuntu because its telling me that i need to select a proper boot device.


motherboard - gigabyte ga-970 gaming

was running ubuntu 14.04 lts

---

### Post by howefield on 2016-03-22
Moved to the "*Windows*" forum.

---

### Post by yancek on 2016-03-22
What operating system are you trying to boot from the external hard drive?  What are you using unetbootin to try to install?  Where is/was your Ubuntu?

---

### Post by jesse49 on 2016-03-22
I had ubuntu 14.04 but now it seems as if for some reason it is gone. Im using unetbootin on a seperate computer running linux mint trying to install windows 10 but also tried installing ubuntu again. I think the issue is that with my motherboard i had to us grub to install ubuntu and have my ethernet work. And now i can't install Windows because of grub

---

### Post by jesse49 on 2016-03-22
Also im using a 250gb external drive with unetbootin. Also tried WinUSB

---

### Post by yancek on 2016-03-23
I've never used winusb so I don't know anything about it.  Your original post seems to indicate you are trying to windows which you put on a flash drive with unetbootin.  That won't work, accoring to the home page for unetbootin quoted below:

>  Also, ISO files for non-Linux operating systems have a different boot mechanism, so don't expect them to work either.

If you tried to boot from a usb, you would have had to change the boot priority in the BIOS to have the usb is first boot priority.  If you want to boot from the hard drive, you need to change it back.

> I think the issue is that with my motherboard i had to us grub to install ubuntu 

No.  Your motherboard points to a specific location on the hard drive where boot code is stored and it doesn't matter what operating system you are using.
There are methods to put a windows installation medium on a flash drive and boot it from Grub but I'm not really sure what you're trying to do or what the status is?

---

### Post by jesse49 on 2016-03-23
> **yancek said:**
> I've never used winusb so I don't know anything about it.  Your original post seems to indicate you are trying to windows which you put on a flash drive with unetbootin.  That won't work, accoring to the home page for unetbootin quoted below:



If you tried to boot from a usb, you would have had to change the boot priority in the BIOS to have the usb is first boot priority.  If you want to boot from the hard drive, you need to change it back.



No.  Your motherboard points to a specific location on the hard drive where boot code is stored and it doesn't matter what operating system you are using.
There are methods to put a windows installation medium on a flash drive and boot it from Grub but I'm not really sure what you're trying to do or what the status is?


At this point im as unsure as you are, I decided to try and install the mini iso of ubuntu on a disk. and it gets to the point where i can select my language and the keyboard stops working.

---

### Post by yancek on 2016-03-23
> At this point im as unsure as you are, I decided to try and install the  mini iso of ubuntu on a disk. and it gets to the point where i can  select my language and the keyboard stops working. 		

That problem is often a result of a bad download.  You can verify the download by doing an md5checsum.  It might also be that the iso was not written correctly to the drive.  Do you not have your original Ubuntu install DVD/flash drive?  You should always keep that.  If you don't you could still get boot repair and run that if you have another computer on which to download and burn it and then boot it.  That should give enough information to see if your Ubuntu is recoverable.  Get it at the link below.


[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Generally, using unetbootin or other similar software is used with flash drives not actual external hard drives although this can be done.
Are you planning to install windows on an internal drive?  Windows cannot be installed to an external drive.

---

### Post by jesse49 on 2016-03-23
yes, i have 2, 1tb drives in my desktop, all i have to install them though is my external drive, all my discs are too small for windows. and were just big enough for ubuntus mini iso.

i will try running the boot repair and get back to you

---

### Post by jesse49 on 2016-03-23
ok, i ran the boot repair disk and its and issue with gpt and im assuming also with uefi

---

### Post by yancek on 2016-03-23
> ok, i ran the boot repair disk and its and issue with gpt and im assuming also with uefi 		

I have no idea what you mean by that?  If you ran boot repair, you should have selected the option to Create BootInfo summary to post here so that we have some useful information on your system.  I'm still not sure what you are trying to do.  It seems as if you are trying to put windows extracted files on the 250 external drive and use Grub from your installed Ubuntu (which is not working as I understand?) and then install windows to your 1TB drive. You can do this but you need to get Ubuntu running first.  Are the 1TB drives external drives?  You can't install windows to a usb drive.  Post the boot repair output or the link to it.

---

