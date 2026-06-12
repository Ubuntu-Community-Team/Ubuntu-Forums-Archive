---
title: "Dropbox"
date: 2008-07-14
forum: The Cafe
---

### Post by sefs on 2008-07-14
Hi all, have you ever heard of Dropbox (getdropbox.com)?  Would you use it?  Is it trustworthy?

---

### Post by fatality_uk on 2008-07-14
Obviously, I wouldn't store anything with personal details, name address, bank etc. Usually these sites have a nice clause seomthing along the lines of:

"We have the right to pull the service anytime we want. Any data that is on our servers, could be lost, sorry!"

---

### Post by Mazza558 on 2008-07-14
I use it - it's very fast indeed, and the developers seem friendly enough.

---

### Post by kool_kat_os on 2008-07-14
what is it?

---

### Post by sefs on 2008-07-14
Kool kat think of it as an online thumbdrive.

---

### Post by Vitamin-Carrot on 2008-07-15
???

Buy a USB flash drive

---

### Post by red_Marvin on 2008-07-15
Encrypt your data and you should be fine.

---

### Post by chopeen on 2008-08-07
> **Mazza558 said:**
> I use it - it's very fast indeed, and the developers seem friendly enough.

Is there any way to make their software work with Ubuntu?

---

### Post by Mazza558 on 2008-08-07
> **chopeen said:**
> Is there any way to make their software work with Ubuntu?

They're very near to releasing a Linux version (gnome/nautilus only for now) in the form of a deb file. Check the forums for more info.

---

### Post by stimpack on 2008-08-07
I use drop.io which does not have the pretty sweet syncing of dropbox, however I like to encrypt things first before dumping them online.

---

### Post by billgoldberg on 2008-08-07
I would never, I mean never store data online.

--

I have harddrives enough laying around.

---

### Post by asdir on 2008-09-16
> **red_Marvin said:**
> Encrypt your data and you should be fine.

Would you mind telling me how I encrypt data (preferably only the Dropbox folder) so that it will still be encrypted once it is uploaded to the Dropbox server?

Afaik it is only possible to encrypt whole disks, but even the data on there would be deciphered once files are copied (uploaded) to somewhere else. But then again, I am not an expert in these matters...

---

### Post by meho_r on 2008-09-16
Maybe with [[COLOR="Blue"]this[/COLOR]]("http://www.truecrypt.org/") ;)

---

### Post by Canis familiaris on 2008-09-16
I'm using it. :)

---

### Post by Biochem on 2008-09-16
> **asdir said:**
> Would you mind telling me how I encrypt data (preferably only the Dropbox folder) so that it will still be encrypted once it is uploaded to the Dropbox server?

Afaik it is only possible to encrypt whole disks, but even the data on there would be deciphered once files are copied (uploaded) to somewhere else. But then again, I am not an expert in these matters...

Have a look at encfs. It encrypts the files in a folder, since each files are individually encrypted you won't have to send your whole truecrypt volume each time. Just sync the encrypted folder not the clear mounted one. It won't work with windows though

---

### Post by niglet101 on 2008-09-16
[http://sikh.myminicity.com/ind](http://sikh.myminicity.com/ind)

---

### Post by meho_r on 2008-10-08
> **Biochem said:**
> Have a look at encfs. It encrypts the files in a folder, since each files are individually encrypted you won't have to send your whole truecrypt volume each time. Just sync the encrypted folder not the clear mounted one. It won't work with windows though

After using this method for some time now, just want to say thank you :D More convenient that TrueCrypt indeed.

---

### Post by UbuWu on 2008-10-08
It is really nice, but don't use it on your laptop, it will drain the battery. according to powertop it causes wakeups around 30 times per second.

---

### Post by borobudur on 2008-12-25
Is there something like dropbox but for your local intra net which works with nautilus?

---

### Post by Prefix100 on 2008-12-25
It is a great tool, I use it for submitting work to college, image hosting, and sharing files with friends.

---

### Post by billgoldberg on 2008-12-25
> **borobudur said:**
> Is there something like dropbox but for your local intra net which works with nautilus?

An ftp server.

And there you have your storage, available in the entire world from any pc.

---

### Post by borobudur on 2008-12-26
> **billgoldberg said:**
> An ftp server.
And there you have your storage, available in the entire world from any pc.
But I'm asking for my own LAN! 
I'd like to have the same as Dropbox but with my own storage server (client is open source but the Dropbox server is not). Advantage:
- no bandwidth problems
- nobody else sees my files
- no encryption necessary

I like the integration of Dropbox into Nautilus and it's great to have on all machines the same synchronized data.

---

### Post by Biochem on 2008-12-28
You mean like nfs or samba but where you can unplug your laptop and still access your data?

if so have a look a unison (I use it over samba, but that's because i'm not an admin on the other end to install it)

---

### Post by borobudur on 2008-12-29
> **Biochem said:**
> You mean like nfs or samba but where you can unplug your laptop and still access your data?

if so have a look a unison (I use it over samba, but that's because i'm not an admin on the other end to install it)
With NFS and Samba you have *just* a mount. With Unison you have to do the synchronization yourself from time to time. 

I had a look at the iFolder ([ifolder.com]("http://www.ifolder.com/")). It looks like it's the same idea like DropBox, and you could have it even peer to peer. 
Has anyone an idea why nobody continues with this project? That's a wonderful thing for your LAN.

Have a look at this article in linuxjournal: 
[linuxjournal.com/content/synchronizing-your-life]("http://www.linuxjournal.com/content/synchronizing-your-life")

---

