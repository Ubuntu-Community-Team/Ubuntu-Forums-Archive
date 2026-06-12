---
title: "SSD solid state hard drive fail"
date: 2013-11-18
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2013-11-18
I've had an Intel 80 GB hard drive running well for a year on this 15" Acer notebook.  Then:
Occasional fsck error message booting
Got a machine check and automatic reboot
Ran trim to clean up 
A couple days later would not boot /dev/sda1.  Machine check and a bunch of error messages.  Nothing much is up at that early stage so I wasn't able to get error messages short of a camera.
There are three bootable images.  I was able to get the third one to boot.  Would not connect to network wired or wireless.
Booted up on a USB 80 GB SATA drive everything worked.
Busily copied off my files from the SSD, home, archive, etc.
Removed SSD and put the SATA drive in the notebook.
Booted O.K.
The SSD is in the USB case if I want to access any more files.
Just installed tahr on the now internal SATA hard drive....running like it is supposed to at this stage....

BTW, I've been running a USB SSD on my netbook with saucy, tahr, etc.  No problems yet...

---

### Post by cariboo on 2013-11-18
The manufacturer of your SSD should have diagnostic software available to test the drive. Of course in order for the software to work, you will need to  install the drive in your notebook.

---

### Post by sudodus on 2013-11-19
Have you checked the partitions in the SSD with ***e2fsck -f***

And have you checked the  S.M.A.R.T. information for example with ***smartctl***

---

### Post by Bucky Ball on 2013-11-19
Note: SSD=Solid State Drive. Your thread title says it twice. ;)

---

### Post by powder on 2013-11-19
Since you've got your data backed up, I would Secure Erase the drive and reinstall.  You'll need to reconnect the SSD to the drive bay in the notebook, boot up a live CD/USB, and use hdparm to [Secure Erase]("http://tinyapps.org/docs/wipe_drives_hdparm.html").  Then power cycle and reinstall.

---

### Post by ventrical on 2013-11-21
> **cariboo907 said:**
> The manufacturer of your SSD should have diagnostic software available to test the drive. Of course in order for the software to work, you will need to  install the drive in your notebook.


Although The Agility 3 , SATA 3, SSD that I use runs fine in Ubuntu, The tools  (iso) to format/maintain have to be boot created using a Windows Operating System, and ,also the .iso is zipped and the common executables are .exe and .com

No CD came with the SSD.

 The literature says it is Linux compatible (which it is) so if one is using linux (ubuntu only) they would have to depend on those tools unless they wanted to crossover to Windows for maintanence or use Wine. I am not sure if this case scenario applies to the OP.

So far .. no problems here as of yet and even the disk benchmarker works using Ubuntu's 'disk' utility.

Regards..

---

### Post by jerrylamos on 2013-11-21
> **ventrical said:**
> So far .. no problems here as of yet .....

Besides the one that failed in my notebook, I have an SSD on an IBM desktop running fine.  It's got USB attached backup drives however I'm lax on backing things up....

And another USB SSD on a netbook with tahr, running pretty well, an occasional fsck.  Better back up that one too....real soon now.

The failing SSD is in a USB case.  Let me try the e2fsck -f on its partitions.  Right now I don't trust it.

Thanks for everyone's comments.

---

### Post by ventrical on 2013-11-21
> **jerrylamos said:**
> Besides the one that failed in my notebook, I have an SSD on an IBM desktop running fine.  It's got USB attached backup drives however I'm lax on backing things up....

And another USB SSD on a netbook with tahr, running pretty well, an occasional fsck.  Better back up that one too....real soon now.

The failing SSD is in a USB case.  Let me try the e2fsck -f on its partitions.  Right now I don't trust it.

Thanks for everyone's comments.

  I have an Asus Eee PC Series netbook with the  SSD built on board (4GBs)+4GBSDHC. It runs Trusty iso from standard USB flashdrive  just swell but I have not run a USB SSD on that.

 Hmmm.. I am interested to see what your results are because perhaps it can help me set up this little netbook with trusty install.

---

