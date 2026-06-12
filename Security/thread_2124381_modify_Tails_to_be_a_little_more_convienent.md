---
title: "modify Tails to be a little more convienent"
date: 2013-03-10
forum: Security
---

### Post by goodbye-windows(tm) on 2013-03-10
Hi All,

I tried Tails for the first time last evening. It will probably never be soft and cushy/convienent, but it does a great job of keeping my real ip address hidden and allowing me to surf anonymously. For special purpose internet activity needing security and online banking/ebay/paypal use, I don't think anything can be more secure.

I have the iso file burned onto a mini DVD-R. But, every time I boot, I have to manually load my printer driver and my wireless (WPA2) password. I'd like to have Tails load with an encrypted text file on the desktop for miscellaneous info (so I can access it after Tails starts running). 

I'd like to modify Tails, so that it knows some of my settings when it forst boots.  But, how do I do this??? As long as the process of adding new settings doesn't access the internet, I shouldn't compromise my security and anonymity. 

Any suggestions regarding how to modify the stock iso to include some minor settings changes?

YIA

Art

 

 .

---

### Post by Stonecold1995 on 2013-03-10
Tails is designed to secure your hardware as well, so it doesn't save settings to your drive, or read your drive, etc.  Tor is what Tails uses to connect anonymously to the internet, it is like a proxy.  All Tails does is provide extra protection from things like web exploits (e.g. if you visit a fake website with a malicious script, Tails will block it from running), malware (even if it is somehow infected, your hard drive isn't mounted and the malware can't mount it, so it can't read/modify your personal files), physical attackers (e.g. when you shut down Tails, it deletes everything in its RAM so no "evidence" of whatever you were doing is left over), etc.

I'm assuming you don't need to hide your IP address from banking sites, ebay, paypal, etc, because those are trustworthy companies.  Tor doesn't "secure" your web browsing so much as it prevents anyone (government, copyright groups, mafiaa etc) from tracking you down via your internet connection, because everyone you connect to will see a Tor IP, not yours.  Also be aware that, because of the way Tor is set up, if you connect to a site that DOESN'T use SSL/TLS (the URL doesn't start with [https://)](https://)), then a malicious Tor node may read/modify what is sent over your internet, even if they can't track it down to you.  So if you're browsing an unencrypted site and you put in sensitive information, a Tor node (which can be run by users, not just Tor Project itself) can view that sensitive information.

So, if all you want is to send banking information securely, you really don't even need Tor, much less Tails.

Anyways, to answer your actual question, you can read about persistent volumes for Tails at [https://tails.boum.org/doc/first_steps/persistence/index.en.html](https://tails.boum.org/doc/first_steps/persistence/index.en.html).  The persistent volume stores an encrypted text file (you choose the encryption key) where you can put things like settings, passwords (Wi-Fi, etc).  However, this only works with a USB installs, not Tails on a DVD.

---

### Post by goodbye-windows(tm) on 2013-03-10
> **Stonecold1995 said:**
> to answer your actual question, you can read about persistent volumes for Tails at [https://tails.boum.org/doc/first_ste.../index.en.html]("https://tails.boum.org/doc/first_steps/persistence/index.en.html").   The persistent volume stores an encrypted text file (you choose the  encryption key) where you can put things like settings, passwords  (Wi-Fi, etc).  However, this only works with a USB installs, not Tails  on a DVD.

TY Stone......

I should have been more specific.

I'm not asking about Tails support for USB drive implememtations. I've read about it and don't want it on a usb drive.

What I wanted to know was how to modify my Tails to include a few convienences, then store it back to another DVD-R. When the second DVD-R is started, Tails would come to life and would already know my wireless password, have a text file on the desktop for misc related info and a few other minor niceties.

Can it be done??

Art

---

### Post by Stonecold1995 on 2013-03-11
Unfortunately, not easily.  Not without modifying and re-packaging the ISO itself.  I suppose it wouldn't be *too* hard to modify it so there's an extra text file of your choice on the desktop at boot, but the changes wouldn't be saved at reboot.  Also, it would be viewable to anyone who has the disk.

You might be able to find a tutorial on that somewhere, but I don't remember how.

---

### Post by goodbye-windows(tm) on 2013-03-12
Yes, **"modifying and re-packaging the ISO"** is _**exactly**_**** what I want to do. I want to do the modifications without connecting to the internet at all, thus my repackaged iso won't become contaminated by carrying over tracking and flash cookies into the repackaged iso.

My desktop file would have reminders and a small set of bookmarks and passwords, and would be encrypted using open office 'save with password' option. All of my passwords are extremely strong and I can't remember them. So having the encrypted text file on the desktop is important.

I am aware that metadata must be removed before saving any file of any type.

I'll keep poking arouind the internet to see if I can find instructions for repackaging the ISO.

---

### Post by Stonecold1995 on 2013-03-12
> **goodbye-windows(tm) said:**
> Yes, **"modifying and re-packaging the ISO"** is _**exactly**_ what I want to do. I want to do the modifications without connecting to the internet at all, thus my repackaged iso won't become contaminated by carrying over tracking and flash cookies into the repackaged iso.

My desktop file would have reminders and a small set of bookmarks and passwords, and would be encrypted using open office 'save with password' option. All of my passwords are extremely strong and I can't remember them. So having the encrypted text file on the desktop is important.

I am aware that metadata must be removed before saving any file of any type.

I'll keep poking arouind the internet to see if I can find instructions for repackaging the ISO.

If you extract the Tails ISO, there's a file at live/filesystem.squashfs.  That file contains the Tails filesystem, e.g. /home, /bin, etc.  You could put an encrypted file in /home/clearnet!  However, when I extracted and mounted filesystem.squashfs, it was mounted read-only.  So, if you can find out how to mount squashfs with writing capability then you're good to go, just repackage the ISO (which is easy using something like 7zip, or various free ISO tools).

---

### Post by Stonecold1995 on 2013-03-12
OK, I haven't tested this but it might work:

Mount and copy the contents of the Tails ISO.  cd into the directory where the ISO contents were extracted.  There should be a >800 MB file under live/filesystem.squashfs.  Mount that file.
```
sudo mkdir /mnt/tails-iso
sudo mount Tails.iso /mnt/tails-iso
cp -r /mnt/tails-iso ~/tails-dir
cd ~/tails-dir
sudo mkdir /mnt/tails-squashfs
sudo mount live/filesystem.squashfs /mnt/tails-squashfs
```
You'll get an error saying it's only been mounted read-only.  That's OK.

Now you have to copy the contents to a new folder, put your encrypted file into it, and repackage the squashfs file.
```
sudo cp -r /mnt/tails-squashfs ~/tails-squashfs-copy
cp /path/to/your/encrypted/file ~/tails-squashfs-copy/home/clearnet
rm live/filesystem.squashfs
sudo mksquashfs ~/tails-squashfs-copy live/filesystem.squashfs -comp lzo -noappend
```

Now all you have to do is repackage the ISO, and you're good to go.
```
mkisofs -o tails-modified.iso ~/tails-dir
```

Time to clean up.
```
sudo umount /mnt/tails-squashfs /mnt/tails-iso
sudo rmdir /mnt/*
rm -r tails-squashfs-copy
```

Also, I highly suggest you don't encrypt your file with OpenOffice.  If it works like MS Word, it encrypts the file using the old and very weak RC4 algorighm, which any half-decent computer today can brute force in minutes, REGARDLESS of how long your password is.  If you want to encrypt your file *securely*, you should do it like this:
```
openssl aes-256-cbc -salt -in my_secrets.txt -out my_encrypted_secrets
```

And to decrypt,
```
openssl aes-256-cbc -salt -in my_encrypted_secrets -out my_secrets.txt -d
```

If you require the level of security Tails provides, then relying on application-specific encryption is very foolish, as it tends to be quite weak (e.g. MS Word, BitTorrent encryption, most SSL, WEP, all of which are very weak and all of which use RC4).

---

