---
title: "NAS Server Solution..."
date: 2008-09-18
forum: Server Platforms
---

### Post by ksudbury on 2008-09-18
I need a NAS hardware solution that I can stick on the network and rsync backups to each day using rsnapshot, I can do this via mounting a smb share if need be.  

It needs to have RAID obviously & the ability to remove discs easily would be an advantage, also if it could ping an email if a disc fails it would be good! 

The only thing I have looked at so far is a drobo... with the roboshare add on, although this seems great it is pricey for what it does & it wont send an email out directly! It needs a MAC or Windows PC that has droboshare software installed on it.. 

Any ideas welcome... this is for business use so please no one say "buy an old pc and bang some HD's in it" :)  


Cheers

---

### Post by warchief_ryan on 2008-09-18
So its for a business... so what.  An older pc would be a great option, though the 'drobo' is a cool looking little thing, an old pc would be much more flexible IMHO.  I don't see why an old pc(not that it has to be old) is not an option...

And I didn't say "buy and old pc and bang some HD's in it", well... with those words anyway.

---

### Post by ksudbury on 2008-09-19
...

---

### Post by Apocrathia on 2008-09-19
I am currently trying to do somewhat of the same thing. I am setting up a home media server.

What kind of systems will be interacting with the server?
Are you wanting to do a hot-swappable raid?
(I was looking into the drobo pretty seriously, still am somewhat. I really want the ability to just pop in new drives when I need them and add the storage space to the data pool)
Web interface?

As far as the email notification system goes. That is a really keen idea, but I'm not really sure how you could do this. Probably setup an email account on gmail, company imap server, whatever. set it to an email client on the server box, then write a simple script to continuously test our drives and when a test fails, send out an email.

---

### Post by Krupski on 2008-09-19
> **ksudbury said:**
> I need a NAS hardware solution that I can stick on the network and rsync backups to each day using rsnapshot, I can do this via mounting a smb share if need be.  

It needs to have RAID obviously & the ability to remove discs easily would be an advantage, also if it could ping an email if a disc fails it would be good! 

The only thing I have looked at so far is a drobo... with the roboshare add on, although this seems great it is pricey for what it does & it wont send an email out directly! It needs a MAC or Windows PC that has droboshare software installed on it.. 

Any ideas welcome... this is for business use so please no one say "buy an old pc and bang some HD's in it" :)  


Cheers

I have built several NAS boxes using Intel DG33BU motherboards, Core 2 Duo or Quad CPUs, 8 GB of ram and a pair of Western Digital WD1002FBYS or a quad of WD1001FALS hard drives as RAID-1 or RAID 0+1 respectively.

The boxes are administered remotely using SSH and available on my home Intranet as Samba shares.

The RAID arrays are run and managed with MDADM and it works flawlessly.

Or, said another way... "Get a *new* PC and stick some hard drives into it" :lolflag:

-- Roger

---

### Post by TheGameAh on 2008-09-19
A little OT, but was wondering.

For people who build their own boxes like this, do you RAID everything?  As in, the root file system as well?  Or do you have a single harddrive for the OS?

---

### Post by Krupski on 2008-09-20
> **TheGameAh said:**
> A little OT, but was wondering.

For people who build their own boxes like this, do you RAID everything?  As in, the root file system as well?  Or do you have a single harddrive for the OS?

My NAS boxes have the entire OS on a compact flash card. The storage hard drives are setup as RAID (minimum RAID-1) and they are SOLELY for data... the OS runs from the solid state drive (which is not RAID).

---

