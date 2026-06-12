---
title: "Data Shredder"
date: 2008-11-07
forum: Security
---

### Post by Dervheid on 2008-11-07
I'm looking for a Linux data shredder utility that will allow me to erase data on my computer from a usb installed distro. I want to be able to erase data on windows partitions as well as linux.
Any good, reliable suggestions.

---

### Post by keplerspeed on 2008-11-07
I was looking into this today, concerning the application 'shred'.

have a look at some earlier posts:

[http://ubuntuforums.org/showthread.php?t=451264](http://ubuntuforums.org/showthread.php?t=451264)

[http://ubuntuforums.org/showthread.php?t=243876](http://ubuntuforums.org/showthread.php?t=243876)

Cheers

---

### Post by cdenley on 2008-11-07
[http://ubuntuforums.org/showthread.php?t=954445](http://ubuntuforums.org/showthread.php?t=954445)

---

### Post by timcredible on 2008-11-07
there are livecds that aren't linux based that will write all 0s or all 1s on a hard drive's partition.  if i remember correctly, it was called killdisk or something like that.

---

### Post by Dervheid on 2008-11-07
Thanks for the input guys.
I've had a look at those articles, and I realise I should have been more precise in describing my requirements.
I'm looking to be able to be able to erase 'specific' files/folders within the windows partition from a usb booted linux distro.

Here's hoping!

---

### Post by cdenley on 2008-11-07
> **Dervheid said:**
> Thanks for the input guys.
I've had a look at those articles, and I realise I should have been more precise in describing my requirements.
I'm looking to be able to be able to erase 'specific' files/folders within the windows partition from a usb booted linux distro.

Here's hoping!

Then anything that has the shred command or something similar, and can write to NTFS filesystems.

[http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)
[http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/](http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/)

---

### Post by HermanAB on 2008-11-07
Hmm, well, shredders don't really work - neither on Windows, nor on Linux, but if you have time to waste, boot with Knoppix or BartPE.

Cheers,

Herman

---

### Post by cdenley on 2008-11-07
> **HermanAB said:**
> Hmm, well, shredders don't really work - neither on Windows, nor on Linux, but if you have time to waste, boot with Knoppix or BartPE.

Cheers,

Herman

Don't work? They work in the sense that they will prevent 99.99% of people from reading that file. They don't work in the sense that if the NSA really wanted to read your file, they can. I wouldn't call it a waste of time if he needs to erase sensitive files without wiping entire drives. Even zeroing the file out would stop most recovery attempts.

---

### Post by persistentstubborn on 2008-11-07
> **cdenley said:**
> Don't work? They work in the sense that they will prevent 99.99% of people from reading that file. 

Exactly. No need for anything else apart from Ubuntu for erasing **a** file.

If one needs to erase a HDD, there is [www.dban.org](www.dban.org), or, for low-level format erase, the tools provided by respective HDD producers. But all of that could be recovered by *someone*. As dban.org suggested - if you really want to be sure no one could get your data, burn HDD to several **thousand** degrees temperature - and that's industrial burning.

Interesting and quite impressive results could be achieved by using the recovery tool available at Ubuntu repositories - testdisk, their site is [www.cgsecurity.org](www.cgsecurity.org) (mind, photorec is included in Linux version as part of testdisk, no need to download anything else but Ubuntu repositories - at least it was in 8.04, the last time I checked).

Run testdisk and instead of recovering a file, erase it. For better results, delete a directory, or, preferrably, create a partition to erase and place the files there.

---

