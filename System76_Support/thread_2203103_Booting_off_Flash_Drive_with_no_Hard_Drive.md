---
title: "Booting off Flash Drive with no Hard Drive"
date: 2014-02-01
forum: System76 Support
---

### Post by Line-X on 2014-02-01
I have a Lemur Ultra and I'm trying to boot Xubuntu off a flash drive on the laptop, but I want to be able to do that with no internal hard drive present.  If this does not belong in this forum, please let me know and move it to the appropriate one.  These are my head-scratching experiences so far:   1. I erase the internal hard drive, and install Xubuntu on a flash drive. It boots off fine from the flash drive.   2. I physically remove the hard drive from the laptop. I boot up with the flash drive still in place. It gives me an error: "Error loading operating system". I check and reset the BIOS settings to boot off the flash drive, but continue getting the error.   3. I reattach the internal hard drive to the laptop. I get the same error and it will not boot off the flash drive. I again check the BIOS and reset it- nothing.   4. I reboot several times. I get another error this time around.  "Error: no such device: 82a5aa6b-9568.../ Entering rescue mode.../ grub rescue >"   5. I reboot again. It boots off fine from the flash drive. I restart- it boots off fine again, and now seems to have no issue every following boot.  Can anybody explain this- or, even better- let me know how to boot off of the flash drive without the internal hard drive being present?

---

### Post by Herman on 2014-02-02
I often boot computers just from Ubuntu in a flash memory stick, and  most computers can boot without any hard drive attached. Sometimes if  the computer won't boot or is very slow to boot, removing the hard drive  fixes it. (In the case of a damaged or worn out hard drive, which can affect the whole computer).

You could try using your computer's BIOS boot menu to select a disk to boot. You might see some text messages while your computer is starting to booting up and going through the BIOS screens and one of them might tell you which key to press for the BIOS boot menu. Often it's F12, and in some computers it's F8, or it could be some other key. Your computer's motherboard manual should tell you if you still have it.

If you mean you have Xubuntu installed in the flash memory stick, you might want to make sure you definitely have GRUB installed to MBR in your USB flash memory drive, you could try re-installing GRUB. Here's a link, [Grub2/Installing]("https://help.ubuntu.com/community/Grub2/Installing") - Ubuntu Community Docs. Make sure you direct GRUB to your USB, not your internal hard disk.
If you mean you have the Xubuntu Live CD Installer for Xubuntu installed in the USB, (using USB Startup Disk Creator), then ignore the above two sentences as that boots with syslinux, not GRUB.

If the problems persist and it's a full install, it might be a problem with the flash memory itself. Hard drives and Solid State drives are usually made for installing and running an operating system, but most people use USB flash memory sticks just for temporary file storage and transfer. We happen to be able to install and run the operating system in them because mostly they tend to behave very similar to hard disks. Under the surface though, there is a lot going on. The USB flash memory has a 'controller', which silently shuffles the flash memory erase blocks around so any wear on the flash memory will be spread out evenly over the entire disk. I have experienced problems similar to some of the ones you described and ended up putting it down to problems in the flash memory disk's controller, but I can't prove it. I'm only guessing. If that's the case then I don't think there's much we can do about except try a different flash memory stick, preferably a different brand or at least a different model.

---

### Post by Line-X on 2014-02-02
Thank you for your response, Herman. I am simply trying to have the laptop regularly boot off a flash drive while not having an internal hard drive present. Currently, it will simply not boot without the internal HDD present, even though it IS indeed booting from the flash drive. Grub is installed on the flash drive, not the internal HDD. In fact, the internal HDD is totally empty and does not have a boot flag.   Unfortunately, I am also having occasional problems while working with the OS from the flash drive. The laptop just seems to disconnect from the USB bus and I start getting "not found" errors, missing graphics and text until all I can do is reboot the laptop and OS. I don't understand it. I could understand some sluggishness, but why is it randomly disconnecting? I am wondering if there is some (relatively easy way) to tell the computer to load the OS into RAM and work with it there, rather than continually pulling it from the flash drive. I have the RAM (16 GB) to do it. It may be as you said- simply an issue with the flash drive, although I made sure to purchase a relatively fast and well-reviewed flash drive. If flash drives are just not reliable for continual use, I may just have to let it go, though I'm not willing to do that just yet.

---

### Post by Herman on 2014-02-02
There is a thread around here about how to boot and run Ubuntu in rams, heres the link: [Making Ubuntu Fast using RAM (updated and simplified)]("http://ubuntuforums.org/showthread.php?t=1594694").
I didn't mean to imply that flash memory drives are not good, just that  performance varies between different USB flash memory sticks. Most of  them seem to run Ubuntu quite well, but some have their own  personalities. There's one kind I know of which my favorite store recommended to me but after returning to the shop three times for an exchange under the warranty I resigned my self to the idea that they only work with a FAT32 file system. As soon as I formatted them to ext they seemd to fail. Everyone else in town loves them but they're only using them for what they were intended for. I'm the one who's trying to do something special, so I can't blame the manufacturer.
I'm one of the people who often posts in favour of having an auxilliary Ubuntu installation in a USB flash memory stick. I think it's a great idea and very useful.
The main thing is, you should be able to boot and run Ubuntu from a  flash memory stick without the HDD being present, in most normal  hardware when the hardware is working normally. Have you tried different USB ports in the same computer or booting the same flash memory stick in a different computer to try to find out where the problem is?

---

### Post by Line-X on 2014-02-10
I've given up on reliably booting the USB flash drive. The only problem is that I have an important file stuck on the flash drive, but the drive is encrypted, so I can't get access to it. I would REALLY appreciate some help with this.

---

### Post by Herman on 2014-02-11
If you have another recent Ubuntu operating system or a even a Live CD you should be able to just plug the flash memory stick in and a dialog should pop up asking you for your encryption password. Normally all you need is your password and Ubuntu should decrypt it and mount it for you. I assume Xubuntu and other 'buntu's would be similar, it has been quite a while now since I last tried out other flavours of Ubuntu so I'm not sure.

In older versions of Ubuntu we needed to run some commands first, you could try them for good measure but I don't think you need them.
```
sudo apt-get install lvm2 cryptsetup
```
```
sudo modprobe dm-crypt
```

 It should at least show up in the file browser if you open any folder, like your /home folder or Documents or anything and click 'go' and then 'computer', you should see an icon for it there and you should be able to double-click on it for a dialog titled 'Enter a password to unlock the volume'. After entering your password, ignore any message like 'unable to mount location' and take a look in your sidebar for the newly mounted file system. You should able to just go in and rescue your files if all things work normally.

If it still fails to mount it's possible that something else is wrong, perhaps it needs to file system check or maybe there's some other kind of problem like a hardware or firmware issue of some kind inside the flash memory stick. 

You could try a command like:
```
lsusb
```
That should tell you if the USB is being detected at all.

---

### Post by Line-X on 2014-02-11
Thank you Herman!  You set me off on the right path and I found my full answer here: [http://askubuntu.com/questions/214995/decrypting-private-folder](http://askubuntu.com/questions/214995/decrypting-private-folder)   I issued this command: "sudo ecryptfs-recover-private".   It then found the encrypted directories and asked me if I wanted to mount them. I said Yes and it mounted them on  /tmp/ where I was able to go in and copy what I needed.

---

### Post by sudodus on 2014-02-11
> **Line-X said:**
> I've given up on reliably booting the USB flash drive. The only problem is that I have an important file stuck on the flash drive, but the drive is encrypted, so I can't get access to it. I would REALLY appreciate some help with this.

1. I think you will get good experiences with USB pendrives, if you accept that they have a shorter average life compared to hard disk drives and more expensive solid state drives (SSDs), and you add the mount option **noatime** to reduce wear, and avoid swapping to it. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

A fast and reliable alternative is a USB 3 SSD. It is bigger than a pendrive, but not too big, and it is shock-resistant. Add the mount options **noatime** and **discard** if you run from an SSD.

2. I'm glad you were able to find what you needed from the encrypted pendrive :-)

---

### Post by Herman on 2014-02-11
Oh, wow! I had to google that one! This is the first time I have ever heard of sudo encrypt-recover-private. Link: [http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html](http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html)
I'm used to LUKS encrypted partitions, I haven't tried out encrypted /home or .private directories, it seems like a good idea though. Thanks Lin-X, I learned something from you. :)

---

