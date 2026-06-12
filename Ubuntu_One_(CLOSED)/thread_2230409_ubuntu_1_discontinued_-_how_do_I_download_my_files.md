---
title: "ubuntu 1 discontinued - how do I download my files (like it say through July 31)"
date: 2014-06-19
forum: Ubuntu One (CLOSED)
---

### Post by squakie on 2014-06-19
I think we all saw the post a while back, of which I extract the following:

> As of today, it will no longer be possible to purchase storage or music  from the Ubuntu One store. The Ubuntu One file services will not be  included in the upcoming Ubuntu 14.04 LTS release, and the Ubuntu One  apps in older versions of Ubuntu and in the Ubuntu, Google, and Apple  stores will be updated appropriately. The current services will be  unavailable from 1 June 2014; user content will remain available for  download until 31 July, at which time it will be deleted.

So, with xubuntu 14.04, just exactly how do I:

- find the files I have 
- download them (until July 31)

Help!

Thanks ;)

---

### Post by bapoumba on 2014-06-19
Thread moved to Ubuntu One.

Do not you have a download link or at least access to the files from the web interface ?

---

### Post by squakie on 2014-06-19
My PC that I had everything on went belly-up thanks to something stupid on my part, and that isn't covered on the warranty on the laptop.  So, I'm using an old acer laptop with xubuntu to try to do things.  I would have no idea at this time what a download link would have been - is there any way to retrieve that?  I also don't know how to access from a web interface since ubuntu one isn't included or in the repositories for 14.04.  I'm trying to figure out just how exactly I'm supposed to be able to those downloads that are supposedly available until July 31.  If you can find ANY way for me to do this, it would be so greatly appreciated!

Thanks!
Dave ;)

---

### Post by slickymaster on 2014-06-19
You could ping someone on the irc channel #ubuntuone or use the contact details at [https://one.ubuntu.com/help/contact/](https://one.ubuntu.com/help/contact/)

---

### Post by squakie on 2014-06-19
I downloaded, unpacked and tried to run u1_downloaded and it gives me an error:```

me@oldlap:~/Downloads/u1-downloader$ ./u1_downloader
bash: ./u1_downloader: cannot execute binary file: Exec format error
me@oldlap:~/Downloads/u1-downloader$ 
```

The folder contents are:```
me@oldlap:~/Downloads/u1-downloader$ ls -al
total 5192
drwxrwxr-x 2 me me    4096 Jun 12 14:07 .
drwxr-xr-x 8 me me    4096 Jun 19 04:52 ..
-rw-rw-r-- 1 me me  214211 Jun 10 10:58 cacert.pem
-rwxr-xr-x 1 me me 5089973 Jun 12 14:06 u1_downloader
```

I've tried with sudo and get the same error message as in [this]("http://ubuntuforums.org/showthread.php?t=2230312") post - the expected " message.

The blog entry that announced all of this has a link to 3 tools to try - but they are all cloud-to-cloud tools.  I don't have another cloud.  I just want to get my files back off of UbuntuOne as it says I should be able to through July 31.

If you have been getting this same error message, here's the trick:  this message appears when you are running 32-bit version of ubuntu/lubuntu/xubuntu, etc., but have downloaded the default as it turns out the default u1_downloader is 64-bit.  Finding that wasn't easy - there is really no mention of it on the initial download page.  To actually download your files from UbuntuOne - if you are using a 32-bit version of ubuntu:

go to [this]("https://help.ubuntu.com/community/U1/Downloader/All/Architectures") link and download the 32-bit version, use the archive manager to decompress it, then in terminal go to the folder everything decompressed to and simply:

./u1_downloader

if will prompt for your ubuntone email address and then for your ubuntuone password, and then it will start downloading.  I have a C source code out there that it just doesn't seem to want to download for whatever reason.  The FAQ says to just retry.  I've done that 3 times so far with the same failure - it did download the rest of my files from ubuntuone.

---

### Post by Pazit on 2014-06-20
> **squakie said:**
> If you have been getting this same error message, here's the trick:  this message appears when you are running 32-bit version of ubuntu/lubuntu/xubuntu, etc., but have downloaded the default as it turns out the default u1_downloader is 64-bit.  Finding that wasn't easy - there is really no mention of it on the initial download page.  To actually download your files from UbuntuOne - if you are using a 32-bit version of ubuntu:

go to [this]("https://help.ubuntu.com/community/U1/Downloader/All/Architectures") link and download the 32-bit version, use the archive manager to decompress it, then in terminal go to the folder everything decompressed to and simply:

./u1_downloader

if will prompt for your ubuntone email address and then for your ubuntuone password, and then it will start downloading.  I have a C source code out there that it just doesn't seem to want to download for whatever reason.  The FAQ says to just retry.  I've done that 3 times so far with the same failure - it did download the rest of my files from ubuntuone.
That was helpful, Thank you very much!

---

### Post by squakie on 2014-06-20
I also found out that when I *thought* I copied my C source code up there I really only created an empty file - and that's why it's not transferring it.  Unfortunately for me, it also means I've lost the source code I worked several months on!!  Oh well, that's what I get for not keeping another copy and then breaking my old laptop! ;)

---

### Post by susanabra on 2014-07-19
Thank you!!

---

