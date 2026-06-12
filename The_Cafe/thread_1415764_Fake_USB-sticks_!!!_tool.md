---
title: "Fake USB-sticks !!! tool ?"
date: 2010-02-25
forum: The Cafe
---

### Post by newbie2 on 2010-02-25
Question : is there a linux(ubuntu) alternative for this H2testw handy tool ? :
[http://www.heise.de/software/download/h2testw/50539](http://www.heise.de/software/download/h2testw/50539)

because there are several fake usb-sticks sold on ebay and other 'usual' stores which do not even know that they are selling fake usb's to their customers :
[http://www.google.com/search?q=fake%20usb%20sticks%20sold&hl=en&ned=us&tab=nw](http://www.google.com/search?q=fake%20usb%20sticks%20sold&hl=en&ned=us&tab=nw)
:roll:

---

### Post by hebeallrusty on 2010-02-25
sureley doing a ```
dd if=/dev/zero of=/dev/(flash drive)
``` will tell you. It should fail after it tries to write to the phantom part. (and will tell you how much it wrote to too i.e. the true size) It will zero the entire drive so make sure you back up all the files on the drive. AND make sure you use the correct device (probably sdb or sdc) otherwise you could end up losing data on a wrong drive! Also code should be run with sudo

---

### Post by newbie2 on 2010-02-26
> **hebeallrusty said:**
> sureley doing a ```
dd if=/dev/zero of=/dev/(flash drive)
``` will tell you. It should fail after it tries to write to the phantom part. (and will tell you how much it wrote to too i.e. the true size) It will zero the entire drive so make sure you back up all the files on the drive. AND make sure you use the correct device (probably sdb or sdc) otherwise you could end up losing data on a wrong drive! Also code should be run with sudo
Thank you rusty,... i asked this because some Dutch monthly computer magazine ordered some 1000 2GB USB sticks at some Chinese 'firm', and they wanted to ship those 'freely' with such magazine filled with their own 'Linux-project PCtoGO' , but could not, because even their 1GB-image could not loaded on those sticks :
[http://webwereld.nl/nieuws/65268/usb-sticks-liegen-over-capaciteit.html](http://webwereld.nl/nieuws/65268/usb-sticks-liegen-over-capaciteit.html) 
:rolleyes:

---

### Post by megamania on 2010-02-26
> **hebeallrusty said:**
> sureley doing a ```
dd if=/dev/zero of=/dev/(flash drive)
``` will tell you. It should fail after it tries to write to the phantom part. (and will tell you how much it wrote to too i.e. the true size) It will zero the entire drive so make sure you back up all the files on the drive. AND make sure you use the correct device (probably sdb or sdc) otherwise you could end up losing data on a wrong drive! Also code should be run with sudo
Not sure about that. Some sticks have "smart" chipsets which will allow writing and reading up to the virtual size of the stick. So even a restore (i.e. copying back from the stick) will look successful, but you will get random data when you actually open the files.

So you need a tool that writes AND verifies data.

---

### Post by hebeallrusty on 2010-02-26
Therefore would doing something like 

```
sudo fdisk -l
```

and getting the size in bytes of the drive for example

```
Disk /dev/sdb: 120.0 GB, 120034123776 bytes

```

in this case is 120034123776 bytes, then doing a 

```
dd if=/dev/zero of=/dev/sdb1/temp.img bs=1024 count=117220824
```
since 1024*117220824=120034123776 also run as sudo

and when its done doing a

```
dd if=/dev/sdb1/temp.img | hexdump -C | head
 
```

tell you then if the end of the file is mangled? Obviously you'd also have to minus a few bytes for partition format

---

