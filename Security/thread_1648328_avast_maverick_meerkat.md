---
title: "avast maverick meerkat"
date: 2010-12-18
forum: Security
---

### Post by me12345 on 2010-12-18
Hi,
 
I have put avast on my ubuntu laptop from a TAR GZ file but when I try to run it, it says, 
 
./avast:178: /home/william/Desktop/avast4workstation1.3.0/lib/avast4workstation/bin/avast: not found
 
I thought this might be because I didn't install ia32-libs, so i did
 
sudo apt-get install ia32-libs
 
but that didn't work. It said
 
E: uable to locate package ia32-libs
 
So I tried sudo apt-get update, which gave me a huge long list of errors, including:
 
An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release: The following signatures were invalid: NODATA 1 NODATA 2
 
 
Note that I don't really know the deep reasons why I have been trying to install ia32-libs, I just read somewhere on the internet that it would help with avast. I had internet enabled when I ran these commands. I had ufw active and blocking all incoming connections, before I enabled the internet.
 
Does anyone know how I can fix avast so it will work? and also fix ia32-libs and update?

---

### Post by me12345 on 2010-12-19
For some reason, sudo apt-get update suddenly worked. Then sudo apt-get install ia32-libs worked. Then avast worked. However, now I am getting a strange problem with the user account I made - the administrator account works fine. It says unable to update ICEauthority file. Then it says sanity check failed. Then it prompts me for a passphrase to unencrypt my home directory. I enter the correct passphrase but it won't work. It then hangs and won't load. Does anyone know what may be causing this?

---

