---
title: "Securely Delete Files off Journaling File-system"
date: 2010-02-19
forum: Security
---

### Post by MontelEdwards on 2010-02-19
I have some very confidental files on my computer that I store such as credit reports, and other things. I always encrypt them with GPG, but there still is that original non-encrypted file left that needs to be deleted. I looked into tools like wipe, and shred but they all say that it really doesn't help on journaling filesystems directly on their man page.

I am not asking how to wipe the whole drive with dd or anything, but I am simply asking if there is a tool that'll delete a single file securely.



Thanks
- Montel

---

### Post by doas777 on 2010-02-19
I'm interested in the answer to that one as well.

---

### Post by bodhi.zazen on 2010-02-19
I believe the "theory" that data could be recovered has been debunked:

[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

The information on the wipe man page is based on unproven theory and paranoia.

All you need to do is overwrite the data a single time. wipe and similar utilities over write the data more then once you should be good to go.

You can also look up the "great Zero Challenge"

[http://www.root777.com/unix-linux/the-great-zero-challenge/](http://www.root777.com/unix-linux/the-great-zero-challenge/)

The challenge was never accepted nor was it cracked.

Note: Over writing the data is not the same as deleting the file. Simply deleting the file is insufficient as the space will be marked as empty space. At some point the data wil be over written.

As an alternate to wipe you can simply run a cron script to write all 0 to your free space once a day, you can then simply delete files and they will be over written by your script.

---

### Post by doas777 on 2010-02-19
i am amused by 'man wipe'. I am often thought to be a little paranoid, but apparently I'm not paranoid enough.

with most transactional logging systems (databases by my experience) you can usually truncate or clear the translog after synching everything. i wonder if there is such a mechanism for ext3\4 in journaling mode.

i have been able to recover partially overwritten files in ntfs using spinrite or some other data recovery tools, but they are often a bit damaged.

---

### Post by FuturePilot on 2010-02-19
They only don't work as expected on journaling filesystems under certain conditions. From the shred manpage:
>  In  the  case  of  ext3 file systems, the above disclaimer applies (and shred is thus of limited  effectiveness)  **only  in  data=journal ** mode, which  journals  file  data  in addition to just metadata.  In both the data=ordered (default) and data=writeback modes, shred works as  usual.

Ubuntu uses data=ordered by default, so unless you changed this yourself, shred will work as expected.

---

### Post by doas777 on 2010-02-19
> **FuturePilot said:**
> They only don't work as expected on journaling filesystems under certain conditions. From the shred manpage:


Ubuntu uses data=ordered by default, so unless you changed this yourself, shred will work as expected.I knew that that was the case for ext3, but I heard that it was in journaling mode for ext4. can you confirm?

---

### Post by FuturePilot on 2010-02-19
> **doas777 said:**
> I knew that that was the case for ext3, but I heard that it was in journaling mode for ext4. can you confirm?

From my dmesg log
```
EXT4-fs (sda2): mounted filesystem with ordered data mode
```

---

### Post by doas777 on 2010-02-19
> **FuturePilot said:**
> From my dmesg log
```
EXT4-fs (sda2): mounted filesystem with ordered data mode
```


you sir, are a model human being. 
thank you kindly.

---

### Post by HermanAB on 2010-02-19
Hmm, if you have confidential information on your machine, then you really should use LUKS and encrypt the whole disk.  

Here are some wizards for LUKS: 
[http://www.aeronetworks.ca/luks-usb-howto.html](http://www.aeronetworks.ca/luks-usb-howto.html)
[http://www.aeronetworks.ca/LUKS-Mount-FreeOTFE.pdf](http://www.aeronetworks.ca/LUKS-Mount-FreeOTFE.pdf)

---

### Post by bhuvi on 2010-02-19
instead of placing the unencrypted files in your hard disk and worrying whether it could be recovered,you could just create a ramdisk and place your unencrypted files there, encrypt it and place the encypted version on your disk,this way there's no chance that your unencrypted files can be recovered after you reboot your system.

---

### Post by doas777 on 2010-02-19
good points, but there are many usecases for which full disk encryption is less desirable than a solution like an encrypted file-volume (truecrypt\pgp classic style).
[http://www.eff.org/deeplinks/2008/05/protecting-yourself-suspicionless-searches-while-t](http://www.eff.org/deeplinks/2008/05/protecting-yourself-suspicionless-searches-while-t)

---

### Post by MontelEdwards on 2010-02-22
I forgot about this thread LOL and I didn't know it was getting any posts.

What I ended up doing is 1) Gutmann wiping my HDD 2) Installing Ubuntu through the alternate installing and setting up an encrypted LVM 3) Encrypted my home directory.

I also [URL="https://answers.launchpad.net/ubuntu/+question/101681"]asked this question on Launchpad 
[/URL] 

And according to the EXT4 Wiki Page it [sates that files cannot be undeleted]("http://ext4.wiki.kernel.org/index.php/Frequently_Asked_Questions#Can_I_undelete_files_in_Ext4.3F")

So what I do now, is just use 'wipe' for all my files. Mainly because it does I think 30 passes, and renames the file to random characters, then delete. ( It has directory and symbolic link support).

---

### Post by MontelEdwards on 2010-02-22
Also, there is a package in Ubuntu called [secure-delete]("http://packages.ubuntu.com/karmic/secure-delete")
This has four tools:

srm - securely delete an existing file
smem - securely delete traces of a file from ram
sfill - wipe all the space marked as empty on your hard drive
sswap - wipe all the data from you swap space.


And according to the srm man page;
>        srm is designed to delete data on mediums in a secure manner which can not be recovered by thiefs, law enforcement or other threats.
       The wipe algorythm is based on the paper "Secure Deletion of Data from Magnetic and Solid-State Memory" presented at the 6th  Usenix
       Security Symposium by Peter Gutmann, one of the leading civilian cryptographers.

       The secure data deletion process of srm goes like this:

       *      1 pass with 0xff

       *      5 random passes. /dev/urandom is used for a secure RNG if available.

       *      27 passes with special values defined by Peter Gutmann.

       *      5 random passes. /dev/urandom is used for a secure RNG if available.

       *      Rename the file to a random value

       *      Truncate the file


So I believe for now, that srm is the best tool to use.

---

### Post by mkvnmtr on 2010-02-22
The four tools in secure-delete should handle all of your wiping needs. It looks like as was stated earlier in the thread wiping will delete files .

---

### Post by jrandolph on 2010-03-02
> **bodhi.zazen said:**
> 

Note: Over writing the data is not the same as deleting the file. Simply deleting the file is insufficient as the space will be marked as empty space. At some point the data wil be over written.

As an alternate to wipe you can simply run a cron script to write all 0 to your free space once a day, you can then simply delete files and they will be over written by your script.

How would you write this script?
I am really interested in something like that.
I make and delete so many files each day, and it would be nice to know that they are truly "gone".

I would assume that this would lessen the life span of my drive though - am I correct?

---

### Post by bodhi.zazen on 2010-03-02
> **jrandolph said:**
> How would you write this script?
I am really interested in something like that.
I make and delete so many files each day, and it would be nice to know that they are truly "gone".

I would assume that this would lessen the life span of my drive though - am I correct?

It is very easy, see if this thread helps you (several suggestion on the thread)

[http://ubuntuforums.org/showthread.php?t=898033](http://ubuntuforums.org/showthread.php?t=898033)

---

