---
title: "SSD drive question re: Pangolin Performance"
date: 2010-05-20
forum: System76 Support
---

### Post by Mendel314 on 2010-05-20
I ordered my Pan Performance with a 640 gb 5400rpm hdd, and I'm wondering about SSD drives.  I need the space, and like the battery life, which is why I went for the 5400rpm drive.  I was wondering if it is possible to install a secondary hdd, or perhaps just get one to connect externally via SATA, to improve speed. I like the idea of a large native drive for storage, but I want an SSD for speed and reliability, so ideally I'd like to do what has begun to happen in desktops and install a smaller SSD drive to run as my primary, and use the 640 gb as pure storage, I fill up space really quickly.  This was why I went for the larger hdd.  I can't find any consensus on SSD power consumption.  would replacing the 640 improve battery life? Obviously having both would reduce it.  Also, how severe is the performance degradation in SSDs?  what sort of lifetime would an SSD have before replacing it? this is a large consideration, since the biggest obstacle to my purchasing an SSD is $
 
I guess my main questions are these:
1. is it physically possible to install a second, SSD hdd into the pan performance?
2. if not, could I get the same performance benefits by using an external SSD drive attached via SATA?  I know I could just wait until a 500 gb SSD hdd comes out that is in my price range (300~ish, plus or minus 100$) and replace the 640, but I fear that that won't be for some time.
3. has anyone done anything like this? an SSD and a standard HDD in the same laptop, or a SATA connected SSD?
4.  If these are possible, how would Ubuntu handle it? my primary concern with this is: if I connect an external SSD drive, can the computer temporarily use it as the primary hdd whenever it's attached? then it might just function as a portable computer accelerator, and I could get a smaller, cheaper one.  
 
Why do I need this performance? I don't, I just like really cool toys.  I want the satisfaction of knowing my system can handle anything I can throw at it, and the comfort of knowing that if I find a use for the performance, then I will have it at the ready.

---

### Post by thomasaaron on 2010-05-20
> 1. is it physically possible to install a second, SSD hdd into the pan performance?

Nope. There's only room for one drive.

> 2. if not, could I get the same performance benefits by using an external SSD drive attached via SATA? I know I could just wait until a 500 gb SSD hdd comes out that is in my price range (300~ish, plus or minus 100$) and replace the 640, but I fear that that won't be for some time.

From what I've read, the SSD's we're selling is about the equivalent of a 10K RPM hard drive. I doubt you'll get the advantages of the full speed of the SSD through a USB port. But maybe through an eSATA port. Maybe.

I think I'd put the SSD in the computer and put the external storage drive in a casing. That way the laptop can take advantage of the speed, and the other drive can be storage.

> 3. has anyone done anything like this? an SSD and a standard HDD in the same laptop, or a SATA connected SSD?

Laptops with two hard drives isn't all that common. But they do exist.

> 4. If these are possible, how would Ubuntu handle it? my primary concern with this is: if I connect an external SSD drive, can the computer temporarily use it as the primary hdd whenever it's attached? then it might just function as a portable computer accelerator, and I could get a smaller, cheaper one. 

That's going to be a bit tricky, but it probably could be done with endless fiddling. But I think my answer to #2 makes more sense. Just my opinion.

---

### Post by zaphod777 on 2010-07-05
If the CD/DVD drive is removable you might be able to get a OBHD (optical bay HDD caddy) and put the bigger slower drive in there and just boot off the SSD

[http://www.newmodeus.com/pics/OBHD/OBHD-Matrix-6.html](http://www.newmodeus.com/pics/OBHD/OBHD-Matrix-6.html)

[http://youtu.be/eQuJrswnJ5g](http://youtu.be/eQuJrswnJ5g)

I am very interested if the built in drive is removable on this laptop if so I will do this.

---

### Post by PabloH on 2010-07-06
The SSD is blazingly fast. I don't think I will ever go back. 

If you enable TRIM support, the performance does not degrade (need 2.6.33 or newer kernel). You can manually TRIM the disk with a wiper.sh utility that comes with newer versions of hdparm. Getting it to work on an Intel disk on Lucid is a PITA, however. 

The Intel SSD hard drives are very reliable. People have nice things to say about the newer OCZ drives as well-- they are cheaper and easier to TRIM-- but they really need TRIM or they will loose random write speeds much quicker than the Intel drives.

---

### Post by zaphod777 on 2010-07-07
> **zaphod777 said:**
> If the CD/DVD drive is removable you might be able to get a OBHD (optical bay HDD caddy) and put the bigger slower drive in there and just boot off the SSD

[http://www.newmodeus.com/pics/OBHD/OBHD-Matrix-6.html](http://www.newmodeus.com/pics/OBHD/OBHD-Matrix-6.html)

[http://youtu.be/eQuJrswnJ5g](http://youtu.be/eQuJrswnJ5g)

I am very interested if the built in drive is removable on this laptop if so I will do this.

Any official response on if this is possible?

---

### Post by isantop on 2010-07-08
That looks like a good idea, and it could work, but since we don't test it, we can't be sure. Also, if you accidentally damage a bit of the hardware in your pangolin while installing it, you wouldn't be covered under warranty.

---

### Post by zaphod777 on 2010-07-08
> **isantop said:**
> That looks like a good idea, and it could work, but since we don't test it, we can't be sure. Also, if you accidentally damage a bit of the hardware in your pangolin while installing it, you wouldn't be covered under warranty.

No problem there I have been working in IT departments for years. Just as long as the CDROM can be removed it should work I think.

---

