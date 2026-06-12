---
title: "Cant make a format USB"
date: 2016-10-27
forum: Windows
---

### Post by helplease27 on 2016-10-27
Hey guys , I need to install win7 to my pc but I don't have cd/dvd rom so I need to format my pc from usb
 Unetbootin Did not work so I tried winusb but it errored that says exit code 256 and when I try to run command "sudo winusbgui" it errors
21:15:43: Debug: Failed to connect to session manager: SESSION_MANAGER environment variable not defined

(winusbgui:4477): IBUS-WARNING **: The owner of /home/user/.config/ibus/bus is not root!
^C
So , Could you help please ?

---

### Post by howefield on 2016-10-27
Moved to the "*Windows*" sub forum.

---

### Post by helplease27 on 2016-10-27
Sorry about that , I just did not know the right topic

---

### Post by yancek on 2016-10-27
As stated on the unetbootin page, it won't work to create a bootable usb of any windows.
What operating system do you have on the computer to work with?

---

### Post by helplease27 on 2016-10-28
> **yancek said:**
> As stated on the unetbootin page, it won't work to create a bootable usb of any windows.
What operating system do you have on the computer to work with?

Thanks for reply , my operating system is ubuntu and I'm trying to make a bootable usb to install windows alongside ubuntu . 
 I guess it is not about winusb but ubuntu . Thing is I cant copy anything or create folder in my usb it's like read-only but there is nothing in it because i formatted it to fat32 and it never was read-only

---

### Post by sudodus on 2016-10-28
You can try ***mkusb-nox*** from the unstable PPA (it is a new feature, so it is not tested enough to go into the stable PPA).

I understand that you run standard Ubuntu or a flavour of Ubuntu: Kubuntu, Lubuntu ... Xubuntu). ***mkusb-nox*** works in some (but not all) other linux distros.

See these links,

[How to install mkusb-nox from the unstable PPA](https://help.ubuntu.com/community/mkusb/gui#from_the_unstable_PPA)

```
sudo add-apt-repository universe  # this line only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/unstable
sudo apt-get update

sudo apt-get install mkusb-nox

# or if you want all three packages
sudo apt-get install mkusb mkusb-nox usb-pack-efi
```

[Making a USB drive to install Windows](https://help.ubuntu.com/community/mkusb/v7#Making_a_USB_drive_to_install_Windows)

[mkUSB-quick-start-manual-nox.pdf](http://phillw.net/isos/linux-tools/mkusb/mkUSB-quick-start-manual-nox.pdf)

-o-

Notice that you can only boot the Windows ***installer*** from USB, not an installed Windows system. Windows must be installed into an internal drive.

Microsoft provides a tool, that you can use, if you can borrow a computer with Windows.

---

### Post by sudodus on 2016-10-28
> **helplease27 said:**
> Thanks for reply , my operating system is ubuntu and I'm trying to make a bootable usb to install windows alongside ubuntu . 
 I guess it is not about winusb but ubuntu . Thing is I cant copy anything or create folder in my usb it's like read-only but there is nothing in it because i formatted it to fat32 and it never was read-only

If mkusb or mkusb-nox cannot write to the USB pendrive, I'm afraid that it is damaged, maybe 'grid-locked'. See this link,

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

Maybe the USB port is bad, so you can try another port, or maybe try in another computer.

---

### Post by helplease27 on 2016-10-28
> **sudodus said:**
> If mkusb or mkusb-nox cannot write to the USB pendrive, I'm afraid that it is damaged, maybe 'grid-locked'. See this link,

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

Maybe the USB port is bad, so you can try another port, or maybe try in another computer.

Thanks for help , I just looked into permissions of my usb , It says that owner is root , You are not the owner so you cant change these permissions I tried gksu nautilus command but when I do that I cannot see my usb It just disappears , What should I do ?

---

### Post by sudodus on 2016-10-28
How do you intend to use the USB pendrive? That will pretty much decide what to do.

- If you want to make it into a USB boot drive with Windows installer, you can do that with mkusb-nox.

- If you want to restore it into a standard USB pendrive to store and transfer files, you can do that too with mkusb-nox (or mkusb with a GUI).

- If you want to recover files in that USB pendrive you need other tools. See this link,

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

-o-

But maybe the drive is good and the only problem is with the permissions. In that case it can help to unmount it and remount it with correct permissions for you. That might be done by making you the owner of the mountpoint of the directory where the mountpoints are created automatically.

Unmount the pendrive 'eject it safely' and after that unplug it.

Try this command

```
sudo chown $USER /media/$USER
```

and see what happens when you plug it back to the computer. It might be enough to make it automount with read and write access for you.

It is also possible to create a custom mountpoint, but that would be the next step, if this does not work.

---

