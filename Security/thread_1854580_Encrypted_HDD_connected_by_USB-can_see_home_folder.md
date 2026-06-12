---
title: "Encrypted HDD connected by USB-can see home folder, unable to access data"
date: 2011-10-04
forum: Security
---

### Post by jaguare22 on 2011-10-04
I am working on an HDD that came from my laptop which was damaged beyond repair.  I have the HDD connected via USB adapter.  I have mounted the drive using Disk Utility in Natty.  When I access the home folder and username, I see two files, Access-your-private-data.desktop and readme.txt.  Clicking the .desktop brings up a terminal window that immediately disappears.  The readme says either click or use the terminal.  When I use the terminal and I am prompted to enter my passphrase and then returned to the prompt.  I am sure the passphrase is correct.  I need to access the data graphically to scan for and recover important data.  It seems that clicking access-your-private-data.desktop should bring up a passphrase prompt but it doesn't.  All help appreciated.

J

---

### Post by jaguare22 on 2011-10-05
Still working on this.  Really would appreciate some help.  Hard drive from damaged laptop connect to my old laptop with usb adapter.  Drive is mounted and I can browse all but Home folder (encrypted) have two files in folder.  Access-your-data.desktop and readme.txt.  Have tried both terminal and graphical methods for access.  Terminal method is ~ecryptfs-mount-private, just returns to prompt.  No surprise drive is mounted.  Clicking access-your-private-data.desktop brings up terminal window which closes immediately. 

Thanks and all help/suggestions appreciated.

---

### Post by dave01945 on 2011-10-05
while it is mounted if you type in terminal

```
sudo ecryptfs-recover-private --fnek /media/home/.ecryptfs/user/.private
```

that should work let us know how it goes also i have presumed that the drive is mounted under /media/home you may have to change it if it is mounted somewhere else and you need to change user to your user name

--EDIT--

wrote down the path slightly wrong i have changed it now

---

### Post by OpSecShellshock on 2011-10-05
Have you tried booting from the external drive? I am assuming here that it was the main drive in the damaged laptop and therefore was the one that booted that device before it was broken. If successful, and as long as you know your user password for that system, it should perform the decryption. From there you should be able to mount the internal drive of the functioning laptop and hopefully copy the unencrypted files that way. Not sure if that would work, as I've never tried, but mechanically it doesn't strike me as much different than booting from a USB stick.

There is also the warranty annihilation route of opening the functioning laptop, switching out the drives, and booting up that way, then transferring to external storage. It's a bit of a desperation move, though, and is ultimately just an inversion of what I suggested above.

If you don't know the password or the key that was generated when the encryption was first implemented (which I believe is the "passphrase" that the prompt was referring to), then you may as well just let it go.

---

### Post by OpSecShellshock on 2011-10-05
> **dave01945 said:**
> while it is mounted if you type in terminal

```
sudo ecryptfs-recover-private --fnek /media/home/.ecryptfs/user/.private
```that should work let us know how it goes also i have presumed that the drive is mounted under /media/home you may have to change it if it is mounted somewhere else and you need to change user to your user name

--EDIT--

wrote down the path slightly wrong i have changed it now

Or that.

---

### Post by jaguare22 on 2011-10-05
Ubuntu forums comes through again!  Thanks for all the help.  Dave your help worked as it should have by letting me enter my passphrase.  Sadly, my passphrase didn't work, though my password did, to some degree.  It said success and my data was in a read-only directory but I couldn't access it graphically.  Permissions issue.  

Anyway, I got to thinking about connecting the drive to another machine.  I hooked it up to my old Pentium 5 3GB dual core.  Completely different hardware, can you believe it...it booted!  Ubuntu rocks!  Seriously doubt Windows could have done that.  Data transfer in progress.  Mark this one solved!  Thanks.

---

