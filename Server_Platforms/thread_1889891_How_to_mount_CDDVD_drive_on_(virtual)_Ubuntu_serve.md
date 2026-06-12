---
title: "How to mount CD/DVD drive on (virtual) Ubuntu server"
date: 2011-12-02
forum: Server Platforms
---

### Post by pinkfloyd65 on 2011-12-02
I am running Ubuntu server 11.10 on Windows Server 2008 R2 Hyper-V. I have only command line, no GUI, and I need to copy a file which is located on a CD. I have set the physical CD drive on the host server (E:) to be captured in the Hyper-V settings.

How do I mount the drive into Ubuntu?
How do I navigate to the files on the CD?

Your help is greatly appreciated.

---

### Post by rubylaser on 2011-12-02
If you've correctly passed the cdrom device, you should be able to mount it like this.
```
sudo -i 
mount /dev/cdrom /mnt/cdrom 
cd /mnt
```

---

### Post by rubylaser on 2011-12-02
Depending on what you're trying to mount, [this]("http://how-to.linuxcareer.com/how-to-mount-cdrom-in-linux") should be useful.

---

### Post by pinkfloyd65 on 2011-12-06
rubylaser,

Thanks for the commands and the link.
When I run #wodim --devices I get this:

0 dev=' /dev/sg1'   rwrw-- : 'Msft' 'Virtual CD?ROM'

If I run #mkdir /media/cdrom I get this:

mkdir: cannot create directory '/media/cdrom': File exists

But when I run #mount /dev/cdrom /mnt/cdrom or 
               #mount /dev/sg1 /mnt/cdrom      I get this:

mount: mount point /mnt/cdrom does not exist

Where am I going wrong?

---

### Post by rubylaser on 2011-12-06
Have you tried this?
```
ls /media/cdrom
```
to see if it's already automounted there?  If not, you'll need to make the /mnt/cdrom directory before being able to mount there.
```
sudo mkdir -p /mnt/cdrom
mount /dev/cdrom /mnt/cdrom
```

---

### Post by pinkfloyd65 on 2011-12-06
rubylaser,

I think I got it! With your help and with some tinkering of my own, I got it.

This is what I did:

- Went into the dev and saw dvd2 listed there
- Went into media and saw that I already have a cdrom there
- Next, I ran this: sudo mount /dev/dev2 /media/cdrom

Sure enough, I get the confirmation that "block device /dev/sr0 is write-protected, mounting read-only"
Running ls /media/cdrom shows the files on the CD.

Thanks!

---

### Post by rubylaser on 2011-12-06
Glad you got it working :)  Don't forget to mark the thread as solved under the thread tools at the top.

---

### Post by pinkfloyd65 on 2011-12-06
Done! Thanks again.

---

