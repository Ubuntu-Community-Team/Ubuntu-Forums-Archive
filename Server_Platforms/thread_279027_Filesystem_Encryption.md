---
title: "Filesystem Encryption"
date: 2006-10-17
forum: Server Platforms
---

### Post by ivoencarnacao on 2006-10-17
I was planning to setup an encrypted filesystem for my Ubuntu, but i dont really know what are the best choices... anyone with some ideas?


Thanks for the help!
Ivo.

---

### Post by tomBorgia on 2006-10-17
truecrypt is pretty good... have to use the command line tho :-?  -
[http://www.truecrypt.org/]("http://www.truecrypt.org/")

---

### Post by ivoencarnacao on 2006-10-17
I was looking at this tutorial of LUKS to go ([https://wiki.ubuntu.com/EncryptedFilesystemHowto4)](https://wiki.ubuntu.com/EncryptedFilesystemHowto4)), what would be the diferences between them?

Thanks for your answer!
Ivo.

---

### Post by tomBorgia on 2006-10-18
trucrypt would be easier! 

Here's how to install [http://ubuntuforums.org/showthread.php?t=199367]("http://ubuntuforums.org/showthread.php?t=199367")
Basically you create a file of a certain size as opposed to a entire filesystem - something like 
truecrypt -c filename 
and then specify the size and the encryption method, passcode etc. this then generates a file which you then mount to another directory with truecrypt.

e.g.
truecypt -c encryptedfile.tc        //create the file - you'll be promted fo                             
                                    //the required info... 
mkdir /home/user/encrypted          //the mount directory
truecrypt encryptedfile.tc /home/user/encrypted
                                    //mounts the file on the directory - you can then use the directory as a normal directory, when finished -
truecrypt -d                        //dismounts the directory - the dir will then be empty but your data will be encrypted in the encrypted.tc file
Hope this is helpful.

---

### Post by Chayak on 2006-10-18
Just a note for you to take into consideration.  You'll be creating a bottleneck in your filesystem and a cpu load whenever you write or read to the encrypted area.  This can sometimes create problems with multimedia files being read from the drive unless you have a newer cpu.  Your speed for the drive access will probably be in the 50MB/s range depending on which encryption scheme you use.

---

### Post by etienne.navarro on 2006-10-19
encfs is an option and similar to truecrypt

---

### Post by etienne.navarro on 2006-10-19
> **Chayak said:**
> Just a note for you to take into consideration.  You'll be creating a bottleneck in your filesystem and a cpu load whenever you write or read to the encrypted area.  This can sometimes create problems with multimedia files being read from the drive unless you have a newer cpu.  Your speed for the drive access will probably be in the 50MB/s range depending on which encryption scheme you use.

Is this for all encryption schemes? I'm using LUKS on a P3 and doesn't seem to create any bottleneck.

---

### Post by etienne.navarro on 2006-10-19
FWIW here are some tests I ran using [dbench]("http://samba.org/ftp/tridge/dbench/").

Encryption used is LUKS: SHA256, AES cipher with 256 keysize (followed [EncryptedFilesystemHowto3]("https://help.ubuntu.com/community/EncryptedFilesystemHowto3"))
File system is XFS, no special parameters and journal on same disk. No special hdparm settings in place either.

**Machine 1:** Pentium III (Coppermine), 866MHz, cache size 256KB, 512MB SDRAM[LIST]
[*]Regular: Throughput 67.802 MB/sec 10 procs[/LIST][LIST]
[*]LUKS: Throughput 57.2743 MB/sec 10 procs[/LIST][LIST]
[*]hdparm -tT /dev/hdX:[LIST]
[*]Timing cached reads: 460 MB in 2.00 seconds = 230.00 MB/sec[/LIST][LIST]
[*]Timing buffered disk reads: 110 MB in 3.02 seconds = 36.42 MB/sec[/LIST] [/LIST]**Machine 2:** Pentium 4 1.60GHz, 2133 MHz, cache size 512KB, 1024MB DDR RAM[LIST]
[*]Regular:Throughput 146.437 MB/sec 10 procs[/LIST][LIST]
[*]LUKS: Throughput 129.104 MB/sec 10 procs[/LIST][LIST]
[*]hdparm -tT /dev/hdX:[LIST]
[*]Timing cached reads: 1680 MB in 2.00 seconds = 840.00 MB/sec[/LIST][LIST]
[*]Timing buffered disk reads: 146 MB in 3.03 seconds = 48.18 MB/sec[/LIST] [/LIST]So there is a drop in performance by about 10-15% (in my case), but doesn't necessary limit the drive access speed to 50MB/s (for LUKS).

*Note: if you run these tests, make sure dbench is on the same hard disk you are running the tests on.*

---

### Post by Chayak on 2006-10-19
It will vary but I was speaking more from previous benchmarks with TrueCrypt.  Like everything it can vary greatly with different configurations but there is a potential bottleneck for some systems.  Thats where hardware ran encryption picks up.

---

### Post by ivoencarnacao on 2006-10-20
So we have TrueCrypt, LUKS, EncFS with the FUSE thing and, what else is there?

Which one could be considered the most secure? Can we choose one with security / performance balance?


I was planning to use LUKS on a XFS partition in my "stylish" Ubuntu Edgy laptop (1,5Ghz Centrino, 512 RAM, 60GB 4200RPM HDD) but at this point i really dont know where to go!

Not even if XFS would be my best choice...


So, all the help would be just GREAT! :P

---

### Post by etienne.navarro on 2006-10-21
> **ivoencarnacao said:**
> So we have TrueCrypt, LUKS, EncFS with the FUSE thing and, what else is there?

Here is a list, [http://en.wikipedia.org/wiki/Encryption_on_Linux](http://en.wikipedia.org/wiki/Encryption_on_Linux), depends on your needs.

I really like LUKS and in your case recommend it. It's easy to use and setup, secure, and performance hit is almost negligible for me (your machine should have no problem). You can also encrypt your whole hard drive (home partition, swap, and root) with it (look on the ubuntu wiki for guides how to do this) which is nice especially for a laptop. Only problem is that if you're using Edgy it doesn't automatically start, but this should be sorted out soon - no problems with Dapper though.

---

### Post by gnomeza on 2006-11-10
Disclaimer: I've used LUKS/dmcrypt, not EncFS or Truecrypt.

I ruled out EncFS because it seemed "locate" would still leak your filenames (would anyone using EncFS like to confirm this?). To prevent that you'd need an encrypted root. So, hell, you may as well go for full disk encryption.

Truecrypt provides plausible deniability, LUKS/dmcrypt does not. If deniability is important to you (do you live in the UK or any other country in which it's illegal to withhold encryption keys?), rule LUKS out.

Truecrypt also uses LRW block-cipher mode which is more secure than the CBC-ESSIV mode used by dmcrypt. dmcrypt LRW mode will probably be stable soon though...
See [http://clemens.endorphin.org/LinuxHDEncSettings](http://clemens.endorphin.org/LinuxHDEncSettings) for a comparison of LRW and CBC-ESSIV.

Bruce Schneier uses TrueCrypt  - [http://www.schneier.com/blog/archives/2006/05/truecrypt.html](http://www.schneier.com/blog/archives/2006/05/truecrypt.html).
(If it's good enough for Mr Schneier, it's probably good enough for anyone.)

OTOH, LUKS is the Linux standard.

As for filesystems: Be wary of the difficulty of resizing XFS.
On a laptop with full disk encryption with LUKS and LVM, I chose ext3 instead of complicating things further...

---

### Post by etienne.navarro on 2006-11-26
> **gnomeza said:**
> Bruce Schneier uses TrueCrypt  - [http://www.schneier.com/blog/archives/2006/05/truecrypt.html](http://www.schneier.com/blog/archives/2006/05/truecrypt.html).
(If it's good enough for Mr Schneier, it's probably good enough for anyone.)

[SIZE=3]*[FONT=Trebuchet MS] "Most people use passwords. Some people use passphrases. Bruce Schneier uses an epic passpoem, detailing the life and works of seven mythical Norse heroes."[/FONT]*[/SIZE] ([http://geekz.co.uk/schneierfacts/](http://geekz.co.uk/schneierfacts/))

---

