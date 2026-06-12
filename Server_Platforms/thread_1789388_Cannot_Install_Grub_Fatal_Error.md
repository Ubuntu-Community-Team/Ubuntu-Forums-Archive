---
title: "Cannot Install Grub: Fatal Error"
date: 2011-06-23
forum: Server Platforms
---

### Post by Jcarr_toonist on 2011-06-23
Hello All,

I recently replaced the motherboard on my server and decided that it was time to do a clean install. The installation of the server errored out on the grub installation telling me that....

```
Cannot install grub on /dev/sda: fatal error during installation
```

or something along those lines. This hard drive has had a full working installation of ubuntu server before and the only thing that is different is the mobo. 

I loaded up a live version of kubuntu and chrooted into the drive and installed grub using apt-get. It seemed to install grub despite giving back a bunch of permission denied error (which I assume are related to chrooting).

Next I ran the grub console and tried 

```
find /boot/grub/stage1
```

which said that it could not find anything. I figured that would be ok because I could just guess the next part 

```
root (hd?,?)
```

but every combination of numbers I tried did not seem to work. In addition I could not find a menu.lst file which I can only guess is because 11.04 uses some version of grub which no longer uses the menu.lst. In frustration I tried installing kubuntu since I had the live cd loaded already and it give the exact same error. 

Does anyone know (a) how to stop this error during installation (b) how to get more information about why I am getting this error during installation or (c) manually install the version of grub 11.04 uses with a live CD.

---

### Post by oldfred on 2011-06-23
Do you have a setting in BIOS that locks the MBR, a few have that extra security.

Grub legacy was last used as the default with 9.04. Grub2 does not have a menu.lst nor a stage1.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

You can post this to see your entire install, but if it is a BIOS issue this will not show it.
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Jcarr_toonist on 2011-06-24
Thanks for the links.

I noticed on the third go-round that /dev/sda was not the OS drive and it was a simple manner of installing grub onto the correct drive and changing the boot device priority in the BIOS.

---

