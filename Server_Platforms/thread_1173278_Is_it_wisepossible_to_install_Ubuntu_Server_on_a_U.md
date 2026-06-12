---
title: "Is it wise/possible to install Ubuntu Server on a USB key?"
date: 2009-05-29
forum: Server Platforms
---

### Post by crimsondr on 2009-05-29
Hi all,

I am interested in using Ubuntu Server as the OS for my file server.  But I want to use the onboard SATA ports for my raid drives.  Is it wise/possible to install the OS onto a USB key to keep the SATA ports free?

Thanks.

---

### Post by cdenley on 2009-05-29
> **crimsondr said:**
> Hi all,

I am interested in using Ubuntu Server as the OS for my file server.  But I want to use the onboard SATA ports for my raid drives.  Is it wise/possible to install the OS onto a USB key to keep the SATA ports free?

Thanks.

USB flash memory drives have a slow write speed, and can only be written to so many times. They're not really ideal for a server.

---

### Post by crimsondr on 2009-05-29
> **cdenley said:**
> USB flash memory drives have a slow write speed, and can only be written to so many times. They're not really ideal for a server.

I've read this before.  But I was hoping to setup something similar to unRAID but I want to manage it myself without paying.

---

### Post by wireonfire on 2009-05-29
The answer is yes.  I have a 512MB usb drive with cdlinux installed (only taken 250MB).

---

### Post by cdenley on 2009-05-29
> **wireonfire said:**
> The answer is yes.  I have a 512MB usb drive with cdlinux installed (only taken 250MB).

I don't doubt that it is possible, but I don't think it is wise. Peformance and reliability would work better with a hard drive. I'm guessing unRAID uses some tricks to limit write cycles to the flash drive.

---

### Post by Pnuts on 2009-05-29
What would a realistic read\write speed need to be to make it viable?

I have a key that when copying a 4gb file Ubuntu estimates write to the stick at 18mb/s and reads from it a little about 25mb/s.

The only real down side that I see is any type of access to the USB stick requires CPU power but depending on the use of the server, this could be negligible.

-Pnuts

Edit: add in the fact that USB stick controllers control writes so it is spread over the stick fairly evenly and given how much they can be written to now a days, I think its viable.

---

### Post by Alekz_ on 2009-05-29
Possible? Sure it is! I just don't think it's wise.. 

As cdenley said: "... can only be written to so many times ..." It works, but it's not safe! At least, not so safe as a hard drive.

---

### Post by cdenley on 2009-05-29
> **Pnuts said:**
> What would a realistic read\write speed need to be to make it viable?

I have a key that when copying a 4gb file Ubuntu estimates write to the stick at 18mb/s and reads from it a little about 25mb/s.

The only real down side that I see is any type of access to the USB stick requires CPU power but depending on the use of the server, this could be negligible.

-Pnuts

Edit: add in the fact that USB stick controllers control writes so it is spread over the stick fairly evenly and given how much they can be written to now a days, I think its viable.

I've never used a usb flash drive that writes that fast. If you have a drive like that, and USB controllers eliminate the write cycle limit issue as you claim, then I think it would be a viable alternative. I'll stick with hard drives for now when it comes to servers.

---

### Post by Pnuts on 2009-05-29
> **cdenley said:**
> I've never used a usb flash drive that writes that fast. If you have a drive like that, and USB controllers eliminate the write cycle limit issue as you claim, then I think it would be a viable alternative. I'll stick with hard drives for now when it comes to servers.

Here is a link to a PDF of how 1 company handles spreading the writes over the entire USB stick to extend life. [http://download.micron.com/pdf/technotes/nand/tn2942_nand_wear_leveling.pdf](http://download.micron.com/pdf/technotes/nand/tn2942_nand_wear_leveling.pdf)

It is also good to note that most name brand sticks support as many as 1 million rewites before failing. Just make sure to check the companies specs on the stick.

The exact stick I use is here: [http://www.cdw.com/shop/products/default.aspx?EDC=1646925](http://www.cdw.com/shop/products/default.aspx?EDC=1646925) This specific one is good for about 100,000 rewrites, but as the controller spreads that out over the disk, I do not worry about it failing. If it ever did, lifetime manufacturer warranty is in place.

-Pnuts

---

### Post by kustomjs on 2009-05-29
yes you can put a server on a usb flash drive its already done take a look at: [http://www.webservusb.com/](http://www.webservusb.com/)

---

### Post by cdenley on 2009-05-29
> **kustomjs said:**
> yes you can put a server on a usb flash drive its already done take a look at: [http://www.webservusb.com/](http://www.webservusb.com/)

Who would pay $70 for free closed-source Windows software? "ultra-secure", I doubt it.
```

cdenley@ubuntu:~$ echo -e "HEAD / HTTP/1.0\n"|nc demo.webservusb.com 80
HTTP/1.1 200 OK
Server: BRS-WebWeaver/1.32
Date: Fri, 29 May 2009 20:43:04 GMT
Last-Modified: Mon, 09 May 2005 03:36:46 GMT
Content-Type: text/html
Content-Length: 4783
Accept-Ranges: bytes
```
[http://www.brswebweaver.com/downloads.html](http://www.brswebweaver.com/downloads.html)

---

### Post by kustomjs on 2009-05-29
I was just putting that out there so everybody can see there 


> **cdenley said:**
> Who would pay $70 for free closed-source Windows software? "ultra-secure", I doubt it.
```

cdenley@ubuntu:~$ echo -e "HEAD / HTTP/1.0\n"|nc demo.webservusb.com 80
HTTP/1.1 200 OK
Server: BRS-WebWeaver/1.32
Date: Fri, 29 May 2009 20:43:04 GMT
Last-Modified: Mon, 09 May 2005 03:36:46 GMT
Content-Type: text/html
Content-Length: 4783
Accept-Ranges: bytes
```
[http://www.brswebweaver.com/downloads.html](http://www.brswebweaver.com/downloads.html)

---

### Post by cariboo on 2009-05-30
Freenas installs on a thumb drive, and it works quite well, it creates a swap file on one of the hard drives, so there isn't a lot of read/write cycles to the usb drive. I tried it, and found it worked quite well until I tried to add another hard drive to the computer, and from then on no matter what I did, including reinstalling it wouldn't work. I was/am running a 120Gb ide, 320Gb ide, and 2 400Gb sata drives, it was the 320Gb that was causing the problem. 

It was detected and setup with zero problems running Jaunty server.

---

