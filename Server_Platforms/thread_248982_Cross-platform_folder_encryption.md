---
title: "Cross-platform folder encryption"
date: 2006-09-01
forum: Server Platforms
---

### Post by Hikaru79 on 2006-09-01
I'm going to be moving away to University in two days, and I imagine that there is going to be lots of file-swapping going on in residence. For that (and other) purposes, I have a 250 GB hard drive with one giant FAT32 partition. I would like to be able to lend this out to people to up/down from it. However, there is also a fair deal of sensitive personal information there that I do not want anyone to be able to get at. I know that there are a variety of easy-to-use per-folder encryption options for Linux, but here's the catch. I'm bringing with me to University a Macbook Pro running OS X, and a desktop dual-booting Ubuntu and WinXP, and I want it to be accessible from all three -- and God knows what platforms my residence-mates will be running (it's a computer science program ;)). So I need a per-folder encryption solution that will work on a FAT32 partition, is very easy to access, and will work on WinXP, OS X, and various flavours of Linux.

That's a very tall order, I know, but I'm sure something is out there, and the community can help me find it :)

Thanks in advance!

---

### Post by skymt on 2006-09-02
The closest thing I know is [TrueCrypt](http://www.truecrypt.org/). Unfortunately the Mac OS X version is still in development. Otherwise it's exactly what you need.

Another possibility is keeping your personal stuff in a GnuPG'd .tbz. That's probably less convenient than you'd like.

---

### Post by sysops on 2006-09-05
FAT32 AFAIK doesn't support any tight permissions and encryption. IS there a real need to use FAT32? I suppose you aer using FAT32 for dualboot access to the parition. Why not upgrade it to NTFS? You get the advantage of being able to use the parition from either OS and get to implement permissions and encryption.

Frankly, if you were sharing out stuff on your harddrive. It'd be best to seperate your personal data from shared data and implement different network shares depending on the level of access you wish to give to different people.

If you asked me what i'd do, I'd upgrade the parititions to EXT/ReiserFS (running ENCFS or something similar), run linux as the primary OS with Windows within it via vmware. Setup network shares via samba and have windows access data off of those shares. a wee bit slower for the windows setup than accessing data off of disk normally, but this setup provides the overall requirements you need.

---

### Post by beowulf62381 on 2006-09-08
Have you tried SimpleCrypt I'm not sure if it will crypt a folder but you could always tar/zip the folder then run SimpleCrypt.

It Features

    * Blowfish or AES algorithm at 128 bits in CBC mode
    * SHA-1 at 65000 iterations, with salt, to generate keys
    * Random IV
    * Password and algorithm checking before decryption
    * Comes in .app, .jar, and .exe forms 

[http://www.insanityflows.net/archive/index.php?title=SimpleCrypt](http://www.insanityflows.net/archive/index.php?title=SimpleCrypt)

---

### Post by dimeotane on 2007-02-11
One  option that is easy to use and cross compatible with different systems is password protected archives.  You can archive a folder containing your files, and set a password.  You can then copy (or backup) the archive as needed to any computer, even a windows OS and you can extract your files.   You want to use something that is secure, ideally AES encryption. 

However, watch out what the file names in the archive are.. because even though  someone can't extract the files, they may be viewable. 

This is a method people often use to protect their files on a USB memory stick... just in case they lose it, and someone else looks through it. 

Most archive formats don't hide the names of files in the archive... so a filename like "my-favourite-prostitutes-list.txt"  might give away more info than you'd prefer. 
:lolflag: 

From what i can tell the rar 3.6 package (I installed with automatix) supports passwords and 128 bit secure passwords.   This currently is the best option for an easy to use file encryption standard which is cross compatible with different OS.

---

