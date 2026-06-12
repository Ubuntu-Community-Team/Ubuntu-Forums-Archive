---
title: "USB Bootable Encrypted OS"
date: 2009-07-09
forum: Security
---

### Post by moldy on 2009-07-09
Hi all- firstly, please bear with me, I'm a novice.

What I want to do is make a truecrypt encrypted bootable USB key.

I know it is possible in traveller mode to fully encrypt a USB key, but what I want to do is create a bootable USB key.

That is, I want to be able to boot straight from the USB, rather than the HDD, and have the whole USB encrypted at the same time.  That way it is possible to do things like surf the net, without leaving any trace on the host computer AND have the whole thing encrypted.

Can anyone tell me if this is possible?
Any help you could give me would be appreciated.

Regards

Richard.

---

### Post by Villiam on 2009-07-09
I have found one for Debian Linux, if it may help you. A bootable USB drive can run a mainstream Linux distribution such as Debian GNU/Linux, and can be secured, personalised, upgraded, and otherwise modified to suit your needs. Check this link out: [http://www.linux.com/archive/feature/125625](http://www.linux.com/archive/feature/125625)

[ubuntu]("http://www.linux-archive.org/ubuntu-user/")

---

### Post by HermanAB on 2009-07-09
I think you can do that with Ubuntu using the Alternate Install CD.  

Unplug the internal HDD, plug in a USB memory stick and run the installer.  The memory stick will then be the only install option and you should end up with an encrypted bootable system.  After that, you can plug the internal disk in again.

---

### Post by twright on 2009-07-09
> **HermanAB said:**
> I think you can do that with Ubuntu using the Alternate Install CD.  

Unplug the internal HDD, plug in a USB memory stick and run the installer.  The memory stick will then be the only install option and you should end up with an encrypted bootable system.  After that, you can plug the internal disk in again.
if you are using that option then make sure that you ensure that grub (the bootloader) is installed to the usb stick not the mbr (master boot record). Otherwise you could just use a normal live usb but make it read only and have an additional encrypted partition on it for files you want to save.

---

### Post by HermanAB on 2009-07-09
Yup, that is why I recommend unplugging the hard disk before you start.  The installer will then only see the USB disk and put everything on it, including MBR, Grub and whatnot.

---

### Post by moldy on 2009-07-09
> **HermanAB said:**
> Yup, that is why I recommend unplugging the hard disk before you start.  The installer will then only see the USB disk and put everything on it, including MBR, Grub and whatnot.

Ah, thanks for your very good advice guys. May be hard for me though, as i only have a laptop. No way to do it without unplugging the hdd? i may have to rope in a friend!

---

### Post by twright on 2009-07-09
> **moldy said:**
> Ah, thanks for your very good advice guys. May be hard for me though, as i only have a laptop. No way to do it without unplugging the hdd? i may have to rope in a friend!
You do not need to unplug the hard drive, it just reduces the chances of you accedently installing to your hard drives boot record and then needing to plug in your usb stick every time you turn on your PC.

---

### Post by HermanAB on 2009-07-09
Anyhoo, it is very easy to remove a laptop HDD.  Usually just one or two Philips screws.

---

### Post by moldy on 2009-07-09
> **HermanAB said:**
> Anyhoo, it is very easy to remove a laptop HDD.  Usually just one or two Philips screws.

True - ok, will give it a try.
Is the encryption by this method proper "entire system" encryption?  As it would be for a truecrypt encrypted HDD?  If not, perhaps there's a way of putting the truecrypt bootloader onto the USB stick in a similar fashion?

---

### Post by HermanAB on 2009-07-09
Yup, LUKS has some advantages over TrueCrypt.

If you get the option, do use AES256, CBC, ESS IV with SHA256.

---

### Post by querent on 2009-07-22
Hi.  I was just trying to do the exact same thing.

So I tried using the alternate installation cd (ubuntu 8.10), selecting encryption at the disk partition phase.

the installation seemed to proceed normally.

now all I get is a blinking cursor.

I've attached the original grub/menu.lst and the my modified version (what I tried based on the link given above for doing this with Debian).  Note that the ".txt" was just added so the forum would let me upload them.

Any help appreciated!

---

