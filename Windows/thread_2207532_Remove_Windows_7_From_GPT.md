---
title: "Remove Windows 7 From GPT"
date: 2014-02-24
forum: Windows
---

### Post by lannatwin on 2014-02-24
Asked about this on the Mint forum. So far no replies. Hoping someone here can help.

Mint 16, UEFI motherboard.

Had a a dual boot window 7 / Mint setup. I have deleted windows. Windows continues to show as a boot option in my BIOS. I would like to remove any reference to it in the GPT partition so it no longer lists in the BIOS. How would I accomplish this? 

Cheers.

---

### Post by Bucky Ball on 2014-02-24
*Thread moved to **Other OS/Distro Support**.*

---

### Post by lannatwin on 2014-02-24
I may be wrong, but I don't think the solution would be specific to Mint. This is why I put it in the installations forum.

---

### Post by Bucky Ball on 2014-02-24
Discussing. In the meantime, you have Linux Mint installed in UEFI? It makes a difference. Windows was installed in UEFI also? If so, the Win boot stuff is in the UEFI partition and you would need to extricate it from there. Don't know how you'd go about that. 

To remove the Win partition as an option at boot, open a terminal and edit /etc/fstab.

```
sudo nano /etc/fstab
```

Look for the Win partition and put a '#' in front of it or remove that line completely. It would then look something like this:

```
# UUID=1234567890 /media/Windows      ntfs    defaults,nls=utf8,umask=0222    0       0
```

Your UUID number will obviously be different to that. Always a good idea to backup fstab (or any important file) before tweaking. 

```
sudo cp /etc/fstab /etc/fstab.backup
```

To copy back if things go pear-shaped

```
sudo cp /etc/fstab.backup /etc/fstab
```

You can also move it back (replace 'cp' with 'mv' but I like to keep the original so prefer to copy). I'm presuming Mint has /etc/fstab and all this will work, but never used so not sure.

---

### Post by lannatwin on 2014-02-24
Thanks. I have managed to remove Windows from the Mint bootloader, no problem.  I am trying to figure out how to remove it from UEFI partition without reformatting reinstalling everything. Bugs me to see it when I go into the BIOS.

---

### Post by Bucky Ball on 2014-02-24
Just having a dig and removing the Win stuff from the EFI partition doesn't seem easy, or maybe even possible without some more serious digging. Win8, on the other hand, appears to get rid of itself when uninstalled, including the EFI info. 

PS: Staff have discussed and your thread has found its rightful home.

---

### Post by lannatwin on 2014-02-24
Yeah.., I spent about an hour searching and couldn't find a simple solution. :(

---

### Post by Bucky Ball on 2014-02-24
And off course, duh; don't think my previous instructions for removing from fstab will work anyhow as don't know if EFI works that way.

---

### Post by oldfred on 2014-02-24
You have to remove the Windows folder in the efi partition or UEFI will just add it again.
UEFI has its own NVRAM and saves entries.

 Really UEFI boot menu 
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu)
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
# from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by lannatwin on 2014-02-24
Ahh, that is what I am looking for. Much appreciated.

---

