---
title: "Securely erase files"
date: 2007-08-14
forum: Server Platforms
---

### Post by climbjm on 2007-08-14
I used to use Secure Eraser for Windows to wipe my files and my unused hard drive space from my system.
[http://www.heidi.ie/eraser/](http://www.heidi.ie/eraser/) << found here

Are there any other programs that you know of that will do this in Linux (Not just Ubuntu, however that is what I am primarily running)?

For example, I want it to use the Guttmann and US DoD 5220-22.M  methods to erase my files.
Something different than /usr/bin/shred

---

### Post by bodhi.zazen on 2007-08-14
I hope you find this link of interest :

[http://www.cyberciti.biz/tips/linux-how-to-delete-file-securely.html](http://www.cyberciti.biz/tips/linux-how-to-delete-file-securely.html)

---

### Post by climbjm on 2007-08-14
Thanks!  I didn't know about srm.

---

### Post by koenn on 2007-08-14
You might also want to look at DBAN (Darik's Boot and Nuke)
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

It's intended to wipe entire partitions/disks using the methods you mention.

---

### Post by HermanAB on 2007-08-14
Uhmmm, Ubuntu uses Ext3 file system by default.  This file system is journaled.  The file system is log structured and never overwrites anything.  If you try to overwrite multiple times, then all you have done is waste your time.  In short, you cannot erase a file, even if you try really hard.

The only way to erase data on Ext3 is to encrypt the whole file system.  Then to erase it, you forget the key and create a new encrypted file system.

---

### Post by koenn on 2007-08-15
uhmm ... what you say may be correct for tools that erase individual files, but after dban, there isn't even a filesystem left on the partition/disk. 

Also, if you 'forget' the key to an encrypted fs, wouldn't you loose access to the entire fs , i.e. **all** files.

---

### Post by HermanAB on 2007-08-15
See this:
[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

What it amounts to is that it is not possible to securely erase files on a HDD, unless you invoke a very low level routine built into the HDD firmware.  That of course wipes the whole HDD.

The other way is to encrypt a file system and then if you 'forget' the key, all files on the file system are erased, but a file system can be much smaller than a HDD - it can be partitioned, or you can use loopback systems with a file system inside a file.

For military use, you can erase media and re-use it only if the media will be re-used at the same or higher classification level. The only secure erase method certified for military use is a big sledge hammer or a propane torch.  Usually, the military destroy HDDs by taking a whole bunch of them to a steel mill and chucking them into a reduction smelter.

Cheers,

Herman

---

### Post by koenn on 2007-08-15
I believe that would depend on how you define "secure" - and that definition may be a tradeoff between cost/effort involved in recovering the erased data, and the sensitivity / required level of confidentiality of the data in question. 
dban would erase to the point that recovery using software tools is impossible, but specialised machinery would still be able to recover data / contents from files / ...
fysical destruction of the disks would then be the ultimate sollution (provided you can organise it so that the disks can not be diverted or read at some point between your office and the destruction site :) )

The " secure erase the key to an encrypted fs" method takes an other approach : it renders the data unaccessible unless the encryption can be cracked.

---

