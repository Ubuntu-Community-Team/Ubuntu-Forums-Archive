---
title: "Unfreeze SSD in Ubuntu Live for hdpram --security-erase-enhanced?"
date: 2018-12-27
forum: Security
---

### Post by Dáire Fagan on 2018-12-27
I am trying to securely erase my SSD using Ubuntu Live, before reinstalling, and I have been using the commands:

```
sudo hdparm --user-master u --security-set-pass <password I set> /dev/sda
sudo hdparm --user-master u --security-erase <password I set> /dev/sda
```

This always results with an error containing the following:

```
SG_IO: bad/missing sense data, sb[]
```

I have learned this is most likely due to the fact that when I run hdparm -I /dev/sda, I can see 'frozen', without 'not' before it.

To try and address this, in my BIOS, I enabled hot swapping for the port. Since doing so, I have tried turning on my computer with the SSD already disconnected from the SATA port and only plugging it in after logging into Ubuntu Live, and I have tried booting with it already connected and then after logging in disconnecting it for 10 seconds from the SATA port and reconnecting. Finally I tried turning on my computer with the drive already disconnected from the SATA port, and connecting it just as I press 'Try Ubuntu without installing'. Unfortunately this still shows the drive as frozen and I cannot --secure-erase or --security-erase-enhanced.

I have read that if you suspend your system with the SSD connected, and then turn it back on it can unfreeze SSDs, but unfortunately when I suspend Ubuntu Live or it suspends itself it will not resume, or it resumes but does not turn on my monitor which is connected to my GTX 970 by DisplayPort. This may be connected to the fact that I can only boot into Ubuntu Live by editing the grub options to include nomodeset.

Samsung SSD 840 EVO Basic 250GB SATA 6Gb/s
Gigabyte GA-Z97MX-Gaming 5, Sockel 1150, mATX

Is there anything else I can try? I was thinking I could perhaps try booting from another Live USB perhaps for another flavour of Linux, or even using Samsung's own bootable USB - would that erase the SSD just as well?

---

### Post by oldfred on 2018-12-27
I have this in my notes, but never had an issue. I have the same 840 SSD but 125GB.

       udisksctl status
Hard drive info - will show locked frozen status or not:
sudo hdparm -I /dev/sdd
Use hdparm to unfreeze
[http://ubuntuforums.org/showthread.php?t=2317805](http://ubuntuforums.org/showthread.php?t=2317805)
Info on freeze
[https://partedmagic.com/secure-erase/](https://partedmagic.com/secure-erase/)

---

### Post by Dáire Fagan on 2018-12-27
> **oldfred said:**
> I have this in my notes, but never had an issue. I have the same 840 SSD but 125GB.

       udisksctl status
Hard drive info - will show locked frozen status or not:
sudo hdparm -I /dev/sdd
Use hdparm to unfreeze
[http://ubuntuforums.org/showthread.php?t=2317805](http://ubuntuforums.org/showthread.php?t=2317805)
Info on freeze
[https://partedmagic.com/secure-erase/](https://partedmagic.com/secure-erase/)

Thanks for the input, resolved by removing power from the SSD, not the SATA cable from the motherboard.

---

