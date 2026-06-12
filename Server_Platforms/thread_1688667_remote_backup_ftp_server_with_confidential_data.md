---
title: "remote backup ftp server with confidential data"
date: 2011-02-15
forum: Server Platforms
---

### Post by Foeburner on 2011-02-15
I already have an ubuntu backup server in my location and need this one server to be backed up remotely in another state. this other location is a helpdesk so there's a danger that they can gain access to confidential data.

I'll be setting up this new server as an ftp server but need to set the ftp folder to only allow access to the backup server and me. Because its remote on the helpdesk side, they'll need some access to the file system but need to be completely blocked off from the ftp folder where all the data is at. 

How can I make sure I can keep them away from my data and still be able to retrieve or copy files over without permission issues between both servers?

---

### Post by pricetech on 2011-02-15
You have a much greater concern with moving confidential data via ftp.

Use SSH instead.

---

### Post by Foeburner on 2011-02-15
thats right! I'll do that. As for permissions? i need it to be almost like a locked folder that needs access via password. maybe set the folder to be visible by nautilus only?

---

### Post by Foeburner on 2011-02-17
Is there a way I can set a folder to not be visible unless my username is logged in and viewable by me only?

---

### Post by koenn on 2011-02-17
> **Foeburner said:**
> Is there a way I can set a folder to not be visible unless my username is logged in and viewable by me only?
samba can do that, but it'll only affect samba users, and you don't want samba for this. 
Also, "obscurity" is not the right way to secure things.
If you use ssh or rsync for your file transfer, you can set up filesystem permissions in such a way that only the account that executes the ssh (or rsync) command has access to them. That's all you need. Of course, anyone with root access on your backup server will have access to your data, but that's a given.

---

### Post by Foeburner on 2011-02-18
that sounds great! any special commands needed other than setting permissions as usual?

---

### Post by HermanAB on 2011-02-18
Howdy,

If you want your data to be secure, then you should encrypt it.

---

### Post by rudelgurke on 2011-02-18
Create an encrypted Partition (or file and mount that via loopback) with dm-crypt / cryptsetup and store the data there.
Of course use a long long (and good password) then even root can't decrypt your data. So you can even manually give access, once by logging in and mounting the crypted container, second time by sharing it over your local network - if you want.

---

### Post by Foeburner on 2011-02-22
Now, am I able to encrypt the partition that contains all the data and copy the encrypted data over to the remote site? Will I be able to copy files from network PCs onto this encrypted drive seemlessly or will i have to mount, decrypt, then copy files over, encrypt then move to remote site?

Appreciate all the help!! =D

---

### Post by mciverza on 2011-02-22
> **Foeburner said:**
> Now, am I able to encrypt the partition that contains all the data and copy the encrypted data over to the remote site? Will I be able to copy files from network PCs onto this encrypted drive seemlessly or will i have to mount, decrypt, then copy files over, encrypt then move to remote site?

Appreciate all the help!! =D

Either is possible. Probably for you the best scenario is to use the encrypted mount at the target computer (the helpdesk)

The SSH connection is encrypted, so no data can be intercepted whilst you're sending it across the network, so there is probably no need to further encrypt the data at the sending machine first.

---

### Post by Foeburner on 2011-02-24
Thank you all very much for steering me in the right direction! This is all the info I need. :)

I will mark this thread as solved now.

---

