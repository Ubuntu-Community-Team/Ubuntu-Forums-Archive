---
title: "Bootable USB drive for Windows 10"
date: 2018-12-09
forum: Windows
---

### Post by 12pasdnker on 2018-12-09
I know ,questions like it has been asked by someone on this forum: [https://ubuntuforums.org/showthread.php?t=2385272](https://ubuntuforums.org/showthread.php?t=2385272)
But I want more info or tips about it

---

### Post by sudodus on 2018-12-10
Please tell us what you have, what you want, and what is your problem (with details). Otherwise we don't know what tips you need, and it will be difficult to help.

- Computer specs (at least brand name and model

- Version and flavour of Ubuntu

- Version of Windows (that you want to install) and if you want a Windows install drive or a portable Windows installed system 'Windows Preinstallation Environment'

- What have you tried?

- What is your problem?

---

### Post by 12pasdnker on 2018-12-10
Now i only have a 64 GB USB drive ,(All the DVD have been wasted,i have tried some burner / tools ),so the only thing that i can do is burn iso to USB ,right ?
This is a Windows 10 computer (64 bit ,home)

---

### Post by sudodus on 2018-12-10
Do you want

-  a Windows install drive or

- a portable Windows installed system 'Windows Preinstallation Environment'?

Which version of Windows do you want to install?

- What is the name of the windows.iso file?

- From where did you get the windows.iso file?

---

### Post by yancek on 2018-12-10
Your last post didn't really clarify much.  Are you trying to install windows to a usb drive?  That won't work by design of microsoft.

Are you trying to create a bootable usb to use to install windows 10 onto a computer hard drive?  That's possible, several methods.

Your last post indicates "This is a Windows 10 computer (64 bit ,home".  What does that mean?  Are you running windows 10 on your computer now?  Where does Ubuntu/Linux fit in?

---

### Post by 12pasdnker on 2018-12-10
> **sudodus said:**
> Do you want

-  a Windows install drive or

- a portable Windows installed system 'Windows Preinstallation Environment'?

Which version of Windows do you want to install?

- What is the name of the windows.iso file?

- From where did you get the windows.iso file?
I just want to make a bootable USB for re-installing a new Windows 10.
The .iso file is downloaded from Microsoft.

> **yancek said:**
> 

Are you trying to create a bootable usb to use to install windows 10 onto a computer hard drive?  That's possible, several methods.

Your last post indicates "This is a Windows 10 computer (64 bit ,home".  What does that mean?  Are you running windows 10 on your computer now?  Where does Ubuntu/Linux fit in?
How to do for making a bootable usb (I just want to re-install a new Windows 10 )
Now,the computer i am using is Windows 10 64 bit .

---

### Post by sudodus on 2018-12-11
> **12pasdnker said:**
> I just want to make a bootable USB for re-installing a new Windows 10.
The .iso file is downloaded from Microsoft.

Check the content of the Windows iso file

```

sudo mkdir -p /mnt/lp1
sudo mount -o loop windows-file-name.iso /mnt/lp1
find /mnt/lp1 -type f -ls | sort -nk7

```
In a recently downloaded 'pure Microsoft iso file' all files are smaller than 4 GiB = 4294967296 bytes.
```

     1307 4174058 -r-xr-xr-x   1 nobody   nogroup  4274234443 okt 30 00:52 /mnt/lp1/sources/install.wim

```

If no file inside the iso file exceeds 4 GiB = 4294967296 bytes, you can use the file system FAT32, and you can use the tool [**mkusb**](https://help.ubuntu.com/community/mkusb)

If a file exceeds that limit, it is usually install.wim. Then you need the file system NTFS and the tool [**woeusb**](https://askubuntu.com/questions/1097560/woeusb-error-code-256-with-ntfs-formatted-usb/1098185#1098185).

This can happen in some windows.iso files created for particular computers (OEM iso file versions).

---

### Post by C.S.Cameron on 2018-12-11
Using a Linux tool on Windows is like using a metric wrench on an imperial bolt,

sometimes it works.

Microsoft's Media Creation Tool works well for creating a Windows installer USB. 

See: [https://www.microsoft.com/en-us/software-download/windows10](https://www.microsoft.com/en-us/software-download/windows10)

---

### Post by howefield on 2018-12-11
Thread moved to the "*Windows*" forum.

---

### Post by yancek on 2018-12-11
> How to do for making a bootable usb (I just want to re-install a new Windows 10 )
Now,the computer i am using is Windows 10 64 bit . 				

If you are using a windows operating system and trying to create a bootable windows usb from it, you would be better off using the microsoft forums or knowledge database or a windows forum.  It is possible to create a bootable windows usb from Ubuntu but you don't have Ubuntu?

---

### Post by 12pasdnker on 2018-12-12
> **sudodus said:**
> Check the content of the Windows iso file

```

sudo mkdir -p /mnt/lp1
sudo mount -o loop windows-file-name.iso /mnt/lp1
find /mnt/lp1 -type f -ls | sort -nk7

```
In a recently downloaded 'pure Microsoft iso file' all files are smaller than 4 GiB = 4294967296 bytes.
```

     1307 4174058 -r-xr-xr-x   1 nobody   nogroup  4274234443 okt 30 00:52 /mnt/lp1/sources/install.wim

```

If no file inside the iso file exceeds 4 GiB = 4294967296 bytes, you can use the file system FAT32, and you can use the tool [**mkusb**]("https://help.ubuntu.com/community/mkusb")

If a file exceeds that limit, it is usually install.wim. Then you need the file system NTFS and the tool [**woeusb**]("https://askubuntu.com/questions/1097560/woeusb-error-code-256-with-ntfs-formatted-usb/1098185#1098185").

This can happen in some windows.iso files created for particular computers (OEM iso file versions).

Thanks , the.iSO file is 2.0GB.

---

### Post by 12pasdnker on 2018-12-12
> **C.S.Cameron said:**
> Using a Linux tool on Windows is like using a metric wrench on an imperial bolt,

sometimes it works.

Microsoft's Media Creation Tool works well for creating a Windows installer USB. 

See: [https://www.microsoft.com/en-us/software-download/windows10](https://www.microsoft.com/en-us/software-download/windows10)

Thanks for your advice,i'll do it again.

---

### Post by sudodus on 2018-12-12
> **12pasdnker said:**
> Thanks , the.iSO file is 2.0GB.

It seems small. What Windows 10 iso file is only 2.0 GB?

Are you sure that the download process was successful? Maybe the download was interrupted before the whole file was transferred.

---

### Post by 12pasdnker on 2018-12-13
> **sudodus said:**
> It seems small. What Windows 10 iso file is only 2.0 GB?

Are you sure that the download process was successful? Maybe the download was interrupted before the whole file was transferred.

Thank you for reminding me,maybe I should go over all the papers.

---

### Post by mappeay on 2018-12-18
My post was considered low quality and deleted.
Well, in general, the iso files are 2.2-3.0gb,you need an empty USB, I remember I prepared a 60gb USB last time (That's more than enough).
And most importantly,how did you get this iso files ? from Microsoft ?(Without question)
Secondly,the burner is also important to make bootable USB,look at this [tutorial]("https://www.iseepassword.com/how-to-make-bootable-usb-drive.html") for it .

---

