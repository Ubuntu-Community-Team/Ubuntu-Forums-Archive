---
title: "shred and ext4 filing system"
date: 2011-01-08
forum: The Cafe
---

### Post by t0p on 2011-01-08
I am aware that the shred command (and, similarly, srm) can be of limited use when used with a journalling file system.  To quote the shred manpage:

> 
CAUTION: Note that shred relies on a very  important  assumption:  that the  file system overwrites data in place.  This is the traditional way to do things, but many modern file system designs do not  satisfy  this assumption.   The following are examples of file systems on which shred is not effective, or is not guaranteed to be effective in all file system modes:

       * log-structured or journaled file systems, such as those supplied with AIX and Solaris (and JFS, ReiserFS, XFS, Ext3, etc.)

       * file systems that write redundant data and  carry  on  even  if  some writes fail, such as RAID-based file systems

       *  file  systems  that  make snapshots, such as Network Appliance's NFS server

       * file systems that cache in temporary locations, such as NFS version 3 clients

* compressed file systems

       ***In  the  case  of  ext3 file systems, the above disclaimer applies (and shred is thus of limited  effectiveness)  only  in  data=journal  mode, which  journals  file  data  in addition to just metadata.  In both the data=ordered (default) and data=writeback modes, shred works as  usual.* Ext3  journaling  modes  can  be  changed  by adding the data=something option to the mount  options  for  a  particular  file  system  in  the /etc/fstab file, as documented in the mount man page (man mount).[/I]**



[emphasis is mine, to emphasise that shred is *not* useless when used with ext3.  For most users, who don't change from the default data=ordered mode, shred works just fine.]

Anyway, to the question I wish to pose: will shred work with ext4 in the same way as with ext3?  If not, is there a secure delete command that *will* work with ext4?

Cheers.

---

### Post by FuturePilot on 2011-01-08
> will shred work with ext4 in the same way as with ext3?
Yes.

---

### Post by wojox on 2011-01-08
I think encryption is the way to go.

---

### Post by t0p on 2011-01-10
> **FuturePilot said:**
> Yes.

Thanks.

> **wojox said:**
> I think encryption is the way to go.

Encryption certainly has its role to play in the secure handling of data; but a secure deletion tool can be just as important.

In England, the Regulation of Investigatory Powers act gives a judge the power to send you to prison for up to 2 years if you refuse to disclose a decryption key.  If you're not a criminal, there are other examples of where coercion might be used to force you to hand over the passphrase.  But if you have securely deleted the sensitive data, it's gone for good (if the file was too long for you to have memorized, of course).

Anyway, my query is answered.  Thanks to all.

---

### Post by Paqman on 2011-01-10
> **t0p said:**
> is there a secure delete command that *will* work with ext4?


TRIM, if you're on an SSD. That'll wipe anything, regardless of filesystem.

---

### Post by psusi on 2011-01-10
That warning is a little pedantic.  Even in data=journal mode, the original file data is only in the journal for a short period after it was written.  Before long the journal cycles around and overwrites the data, so the only time you might have a copy of the file data left in the journal after you shred it is if you JUST created the file, then immediately shred it, and then it might hang around in the journal for a few minutes or hours, but that's all.

For that matter, just the act of shreding the file is going to cause the journal copy to be overwritten, unless the file is very small.

---

### Post by YourSurrogateGod on 2012-08-01
> **t0p said:**
> I am aware that the shred command (and, similarly, srm) can be of limited use when used with a journalling file system.  To quote the shred manpage:



[emphasis is mine, to emphasise that shred is *not* useless when used with ext3.  For most users, who don't change from the default data=ordered mode, shred works just fine.]

Anyway, to the question I wish to pose: will shred work with ext4 in the same way as with ext3?  If not, is there a secure delete command that *will* work with ext4?

Cheers.

Hi, just curious, but which way did you do when it comes to securely deleting files with shred?  Did you modify the configuration of the file-system?  If so, how?

---

### Post by Bachstelze on 2012-08-01
> **YourSurrogateGod said:**
> Hi, just curious, but which way did you do when it comes to securely deleting files with shred?  Did you modify the configuration of the file-system?  If so, how?

As the quoted man page says, shred will work as expected on ext3/4 with the default settings. This means that if you did not add a special mount option to your fstab, you will be fine.

---

### Post by t0p on 2012-08-08
As this has reared its head again, I just thought I'd chip in and say I have been using the "secure-delete" utility **srm**.  It's easy to install, now it's available with **apt-get**, ie

```
sudo apt-get install secure-delete
```

and it's also easier on the fingers.  If you want to securely delete a file using shred, you have to use the **-u** flag, ie

```
shred -u sensitive.txt
```

because shred's default action is to just *overwrite* the file.  Not that that's a biggie for most of us,but there are always those who really truly want to wipe that data from the face of the earth.  That's what **srm** does - key in

```
srm sensitive.txt
```

and the result is the same as the above **shred-u** command.  Less letters.  No flags.  What's not to like?  ;)

---

### Post by Primefalcon on 2012-08-08
@t0p 

why not just alias it, like so
```
alias shred='shred -u'
```

or if yo really want to be secure
```
alias shred='shred -uz --iterations=10'
```

---

### Post by Paqman on 2012-08-08
> **t0p said:**
> No flags.  What's not to like?  ;)

You might want to use some flags anyway. By default both tools do too many writes (srm much moreso than shred). That's not a big deal on small files, but on larger ones it'll be slow and if you're on an SSD it'll be burning up your limited number of write cycles unnecessarily.

---

### Post by Primefalcon on 2012-08-08
> **Paqman said:**
> You might want to use some flags anyway. By default both tools do too many writes (srm much moreso than shred). That's not a big deal on small files, but on larger ones it'll be slow and if you're on an SSD it'll be burning up your limited number of write cycles unnecessarily.
again don't see much point to srm since you can just alias what flags you want

---

### Post by Paqman on 2012-08-10
> **Primefalcon said:**
> again don't see much point to srm since you can just alias what flags you want

Sure, but sometimes you might want different flags.

---

### Post by Bachstelze on 2012-08-10
> **Paqman said:**
> You might want to use some flags anyway. By default both tools do too many writes (srm much moreso than shred). That's not a big deal on small files, but on larger ones it'll be slow and if you're on an SSD it'll be burning up your limited number of write cycles unnecessarily.

If you are paranoid enough to use shred in the first place, having to replace your disk more frequently is probably the least of your worries.

---

### Post by Paqman on 2012-08-10
> **Bachstelze said:**
> If you are paranoid enough to use shred in the first place, having to replace your disk more frequently is probably the least of your worries.

True. A lot of those folk will quite happily drill dirty great holes through perfectly good disks to get rid of the data on them.

---

### Post by mips on 2012-08-10
Why go through all this hassle when you can do a secure erase (ata command set) from hdparm?

---

### Post by Primefalcon on 2012-08-10
> **Paqman said:**
> Sure, but sometimes you might want different flags.
sure then why not alias it with the flags to something like:

```
alias goaway='shred -uz --iterations=10'
```

and that way if you want to use other flags... nothing is stopping you from entering say shred with other flags

---

### Post by t0p on 2012-08-10
I've got an .iso of DBAN on an external drive..  I once had this crazed paranoid plan to somehow set things up so entering a particular key-combination in my usual Ubuntu sessions would automagically reboot to DBAN and overwrite my entire drive.  For use when *they* were trying force entry through my reinforced iron door.

Fortunately(?) I abandoned that plan (probably because I didn't know how to do it).  If someone were to tell me how to do it, I might still be interested.  Dunno, depends how much *they* have been following me, I guess.

---

### Post by Primefalcon on 2012-08-10
[SIZE="4"][COLOR="Red"]WARNING: NEVER DO THE FOLLOWING ON A COMPUTER WHICH HAS DATA YOU CARE ABOUT.... YOU'LL NEVER GET IT BACK FROM ANY MEANS[/COLOR][/SIZE]


I've heard good things about dban... you could also do something like this....

```

#!/bin/bash
x=1
dd if=/dev/zero of=/dev/sda bs=1M
while [ $x -le 5 ]
do
  dd if=/dev/urandom of=/dev/sda bs=1M
  x=$(( $x + 1 ))
done
dd if=/dev/zero of=/dev/sda bs=1M

```

and then let it run overnight, and if you wanted, you could add the script to sudoers and give it a hot key activation...

for the record no one has ever managed to recover data from even a single overwrite.... but running extra times just makes it more certain! the first 0 pass is for speed btw, but it'll still take a long time

---

### Post by Paqman on 2012-08-11
> **Primefalcon said:**
> sure then why not alias it with the flags to something like:

```
alias goaway='shred -uz --iterations=10'
```

and that way if you want to use other flags... nothing is stopping you from entering say shred with other flags

Sure, I wasn't suggesting otherwise.

Incidentally, shred's default is a much more sane 3 passes these days. Which is still three times more than you actually need.

---

### Post by Primefalcon on 2012-08-11
> **Paqman said:**
> Sure, I wasn't suggesting otherwise.

Incidentally, shred's default is a much more sane 3 passes these days. Which is still three times more than you actually need.
I agree entirely.... In there has bee a big challenge online for quite a while now... for a lot of money.... to recover data after a single rewrite.... and no one has been able to do.... regardless of what methods they use...

---

### Post by mips on 2012-08-11
The fastest method would be this,

[https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)
[http://tinyapps.org/docs/wipe_drives_hdparm.html](http://tinyapps.org/docs/wipe_drives_hdparm.html)

It's all I use to erase drives and it's way faster than any utility/tool out there.

---

### Post by daKoolaid on 2012-09-08
Cool, I saw that warning in shred's manpage and was wondering about it too since I'm using ext4.

I found a shred script to add as a right click option. I have yet to figure out how to make it work for folders and files with spaces in the names.
```
#!/bin/bash

shred -v -n 5 -z $@ -u

exit
```

---

