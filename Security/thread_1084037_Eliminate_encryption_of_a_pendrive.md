---
title: "Eliminate encryption of a pendrive"
date: 2009-03-01
forum: Security
---

### Post by Sadd on 2009-03-01
Hi, this is the first time i write here, i think i´m at the right place..for asking this.

i have a 2Gb pendrive and its encrypted with truecrypt  a long time ago,,,but now i dont need that encryption enymore..i searched the main page of truecrypt ,,,but i dont seem to understand the steps for eliminating the encryption XD sorry
please help me ...someone that have already done this
i upgraded to the last version of truecrypt and i use hardy distribution
thanks

---

### Post by bgates on 2009-03-01
I think you should be able to just blow everything on it away using gparted, and create a new partition and format it in whatever filesystem you like with no encryption.

Exercise great care that it is truly the usb drive that you have selected in gparted when doing this.  :)

---

### Post by radar2020 on 2009-03-02
First of all you will need gparted.  Start Synaptic Package Manager and install gparted.

If the whole pendrive is encrypted do the following:

	Put the pendrive into a USB slot of your computer
	Go to SYSTEM > ADMINISTRATION > PARTITION EDITOR > enter your password
		
		A new window comes up called Gparted

	You want  the partition of the pendrive not the harddrive.  Click on the downward pointing arrow in the top right hand corner of the Gparted window.  In this drop down menu, choose your pendrive.  ( Very important!)

	In Gparted click inside the pendrive partition.
	Go to the menu > PARTITION > UNMOUNT
	Click in the pendrive partition again
	Go back to the menu > PARTITION > FORMAT      (Choose the format  that you want. fat16 or fat32 are good choices)
	click APPLY
        
        The pendrive will now be ready to use as normal.

---

### Post by Sadd on 2009-03-02
Thanks radar, but when i go to "partition" the "unmount" and "format" options are unavailable =( , maybe because it is ecrypted....also i mounted the drive using truecrypt and the same happens,,,

there´s no other way restoring the drive  just using truecrypt¡¡¡??????

---

### Post by HermanAB on 2009-03-02
If you are only going to use it on Linux, then you don't need to partition a USB drive and can simply format it:
$ sudo mkfs.ext3 /dev/sdX

Where sdX is the name of the device, which you can get from dmesg:
$ dmesg
Just to see where you are in the log, 
then plug it in and look at dmesg again:
$ dmesg

You can format it with FAT or many others:
$ ls /sbin/mkfs*

Cheers,

Herman

---

### Post by Sadd on 2009-03-05
Thank you very much HermanAB
formatting from terminal worked perfect
now, i just have a last question....to use this drive in windows...i have to format in FAT right?

thanks again.... you already solved my problem =)

---

### Post by HermanAB on 2009-03-05
If you wish to use the device with Windows, then you need FAT or NTFS (better).  On Linux however, you can use any file system you like. I normally use JFS, because it is very efficient in terms of storage space use.

Cheers,

Herman

---

