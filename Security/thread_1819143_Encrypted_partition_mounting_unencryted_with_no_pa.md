---
title: "Encrypted partition mounting unencryted with no password needed."
date: 2011-08-05
forum: Security
---

### Post by MechaMechanism on 2011-08-05
EDIT:  This pass-wordless mounting of an encrypted partition was true even across reboots.

My thumb drive has an encrypted partition.  It used to be that I would need to enter a password to mount it.  Then today it started mounting with out the password.  Big honking uh oh!!!  Do you think I got hacked?

I wonder where the password is on the desktop is cached.

Disk Utility produces the following error when trying to lock the partition:> Error locking device: cryptsetup exited with exit code 240: Device udisks-luks-uuid-bb3e7f23-e8e8-4665-8b57-82451a0241ce-uid1000 is busy.Please help me as this has me really really worried.  I might be forced to delete the sensitive data if I have no other choice.

EDIT:  On my netbook the computer ask for the password and fails to mount partition if incorrect password or no password is entered.

EDIT 2:  Weird, in disk utility there is a button that says forget passphrase.  I clicked and unmounted the partition.  Voila! it now ask for the password.

---

### Post by requeth on 2011-08-10
You just found one of the many useless features of drive encryption. I've played extensively with windows, linux, and mac drive encryption and the built in encryption suites are completely useless.

I was a Vista beta tester and if you encrypt a drive in windows, pull the drive, plug it into a machine with the admin account named the same, and try to open the slave drive, a pop up box will pop up saying your not the owner and would you like to take ownership. You click yes and the drive is "de-encrypted".

A few months ago I received an OSX box that had been in a fire, encrypted drive. I threw the drive in a USB enclosure and slaved it to my Ubuntu box. I couldn't read, it, so I changed over to root and did an ls. I revceived a message roughly saying "you are not the owner of these files". I chown'd the master file and was able to CD into it with no trouble and no password. A file ended up corrupting and I had taken a backup of the drive.

I plugged the untouched drive into a mac box and it asked for a password in the GUI and let me in once the correct password was known. Which is the way your supposed to recover an OSX drive.

The FBI doesn't care about most drive encryptions, and there's a reason the built in encryption isn't allowed to be used for government computers.

When I need files secured, I use PGP. I've never found a way around it, and I got paid to try for a while.

---

### Post by mujahied on 2011-08-11
> **requeth said:**
> You just found one of the many useless features of drive encryption. I've played extensively with windows, linux, and mac drive encryption and the built in encryption suites are completely useless.

I was a Vista beta tester and if you encrypt a drive in windows, pull the drive, plug it into a machine with the admin account named the same, and try to open the slave drive, a pop up box will pop up saying your not the owner and would you like to take ownership. You click yes and the drive is "de-encrypted".

A few months ago I received an OSX box that had been in a fire, encrypted drive. I threw the drive in a USB enclosure and slaved it to my Ubuntu box. I couldn't read, it, so I changed over to root and did an ls. I revceived a message roughly saying "you are not the owner of these files". I chown'd the master file and was able to CD into it with no trouble and no password. A file ended up corrupting and I had taken a backup of the drive.

I plugged the untouched drive into a mac box and it asked for a password in the GUI and let me in once the correct password was known. Which is the way your supposed to recover an OSX drive.

The FBI doesn't care about most drive encryptions, and there's a reason the built in encryption isn't allowed to be used for government computers.

When I need files secured, I use PGP. I've never found a way around it, and I got paid to try for a while.

if you have the pw for pgp i can provide you the tools to decrypt that i have some pgp tools as i work for a company that has pgp server i got hold of these tools at work 
is a live bootable cd and you type in the command pgpwde --decrypt --disk 0 -p "pgp password

---

