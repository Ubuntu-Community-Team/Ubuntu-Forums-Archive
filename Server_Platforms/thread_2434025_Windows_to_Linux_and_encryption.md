---
title: "Windows to Linux and encryption"
date: 2019-12-29
forum: Server Platforms
---

### Post by aljames2 on 2019-12-29
Moving approx 1TB of data from windows storage drive (NTFS) to new Ubuntu 18.04 storage server, which has mounted on it, 2 separate 4 TB spinning drives (LVM + ext4) for storage.  My server OS is not encrypted (perhaps should be?).  Once this data is on my Linux partitions it will no longer be used by Windows clients.  Therefore, I do not believe shares between Windows & Linux are the best way to move the data one-way, so I plan to push the data over with WinSCP.  Not sure if this plan is best.

As for encryption of the storage data... The data on the Windows machine is currently not encrypted, But I would like to implement encryption on the new storage drives under LVM.  I feel I need a lesson on encryption...the pros and cons and difficulties my Linux client machines may experience when trying to use that data.  Add to that, the Linux client machines are unencrypted desktop installations.

The more I think about it the more I believe I should reinstall the server OS using encryption, as I believe it will then be easier to manage encryption on the storage drives?  

I feel my back up scheme is ok in a non-encrypted environment, using various tools such as ReaR (Relax & recover) to create encrypted OS recovery ISOs, Rsync to make backups between drives, and Rdiff on various OS directories for versioning.  Not sure how all this blows up if I start encrypting stuff?

Sorry for the incoherent brainstorming here but hopefully there’s a question, or at least a desire to organize my thinking better.

---

### Post by darkod on 2019-12-29
First of all, you should sit down and make the decision before you start moving the data. I hope you know that. When establishing the encryption it will delete any data already on the disks/partitions.

1. Copy/migrate using WinSCP once you have everything ready. Agree. Good plan.

2. Leave the OS unencrypted. I agree. I have my home server like that too. I don't see any major risk in it, plus it allows the OS to boot even in cases something gets messed up with the encryption. Much easier to manage the machine. The OS encryption doesn't make it easier or harder to manage the data encryption. But no OS encryption does allow you uninterrupted OS boot, which in my opinion is better.

3. Pros and cons of unencrypted Linux desktop installation accessing the data? I didn't understand this part. Depends how you plan to share it to them. If over nfs (recommended), then the data encryption has no role. The server OS has the data decrypted and mounted, and it offers the nfs to clients. From client side they see the data and no encryption at all. Do you need the client-server link to be encrypted too in your local network???

4. About the backup part, if the backups are done on the server itself, then again the mount of the data already happened and whether it was encrypted or not plays no role. The SW will simply see the data as if it was unencrypted.

---

### Post by aljames2 on 2019-12-29
#3, most client laptops are on a separate subnet behind the router, and they connect to the internet via wireless AP.  I would think use a VPN to access the nfs.  I am not sure that encryption of the storage data is necessary other than to protect the data from a risk like a lost or stolen drive?  Only users are trusted users.

---

### Post by TheFu on 2019-12-29
+1 for everything Darkod wrote.

I would add that NFSv4 protocol supports strong encryption with Kerberos authentication between the client and server.  If you are more comfortable setting up a full VPN, that's fine.  Clients over wifi isn't ideal.  You'll want safer NFS options to prevent data corruption at the cost of lower performance.  That is unfortunate.

Encrypted data is good when/if a drive has issues and needs to be sent in for warranty.  If the disk doesn't spin, you can't attempt to delete it, so the manufacturer has complete access.  For some people, having a vendor access to their data doesn't matter.  Servers should be in physically locked locations. Same for storage. Of course, each location is different and has challenges.  Physical security can be very difficult in an office with dropped ceilings. The rooms on 3 sides probably can't be secured, so a desk near a wall and hopping over the wall isn't too hard.  I've done that during security audits at clients just to make a point.  Plus, most internal door locks are easily defeated, also a nice party trick for clients to watch. Most doors are 30 seconds.  If we know the smartcard vendor in advance, it can be 2 seconds to entry. This is all under signed contracts, of course.  The locks on my own house front door are about 45 sec and 90 sec without any damage or traces.

While you can LUKS encrypt storage at almost any level, I do it at the partition, then put LVM PVs inside the encrypted container.  The nitty details about the plan to dencrypt at boot is something you might want to test in advance. A key file on a flash drive? A 1FA setup with a yubikey or smartcard or should the OS just stop until a passphrase or 2FA device is used?  LUKS has 8 slots to unlock, so having 3+ methods isn't hard.
[https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987](https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987) has an lsblk output you might find interesting. LUKS, LVM, good stuff.

I'd suggest whatever the plan should be tested ASAP, probably on a virtual machine.

WinSCP is kinda slow. You'll see.  Wouldn't hurt to look up performance settings to make it faster. pscp might be faster, but I haven't used either for anything except trivial stuff in many years.

Setting up samba for the transfer isn't too hard, but it depends on the clients. Win10 and Samba default changes broke old configs, so some different settings are needed.  Samba can achieve good write speed over a wired GigE network with a solid NIC. I see 65MBps+ consistently with multiple, multi-Gigabyte files.

---

### Post by aljames2 on 2019-12-31
Thanks for the help Darkod & TheFu.  Good stuff indeed.  I’m going to play around with a couple scenarios on a VM.  A side chance to practice using KVM Virsh.

TheFu, I reviewed your link lsblk and the OS is volume group is encrypted. Is that done from installation.  Is LUKS the encryption method that the Ubuntu installation uses when encryption is chosen from the beginning?  Thanks again

---

### Post by TheFu on 2019-12-31
> **aljames2 said:**
>  TheFu, I reviewed your link lsblk and the OS appears to be on the encryption layer.  Did you do that post-installation using LUKS.  I guess my real question, is LUKS the encryption method that the Ubuntu installation uses when encryption is chosen?  Thanks again

No.  I selected whole drive encryption + lvm during the install, but for **only data directories**, that isn't needed.  It can easily be manually added later to an empty partition.  For boot/OS stuff, doing it later, manually, isn't possible because **encrypting is a destructive process**.  Paddy wrote up a way to manually do all that, but it just seemed way to complex for my needs.

---

### Post by darkod on 2020-01-01
To add, I have my setup little different and I really don't know which is "best". Never even looked into it honestly.

TheFu said that he has encryption and then LVM if I understand correctly.

My setup is:
mdadm raid1 to create the md devices -> the data md devices used as physical volumes in LVM (the OS md array is out of the LVM fully) -> the data logical volumes encrypted with LUKS -> the encrypted mapper device formatted with ext4 and mounted to be used

I hope that made some sense. :)

---

### Post by TheFu on 2020-01-01
There are lots of possible different setups.  Just depends on the goals.  My goals were to have as much storage encrypted withing 1 encryption container (requiring unlocking just once).  Someone else might want each LV encrypted separately and see the need to unlock each separately as a feature.

Regardless, whenever using encryption, be aware that almost any storage issue will require restoring from backups.  Data recovery or forensic tools only see random bits.

Outside the installer, on Ubuntu I've only used **cryptsetup** to create, manage, encrypted containers. Just a few days ago, I added a challenge-response setup using a Yubikey 5C to a slot in the LUKS container.  I left 2 other slots unmodified.  One has a 88 character, no way I can type it, passphrase for emergency use.  The other uses a different Yubikey with a static output and a 20 character manually entered passphrase (something I have + something I know).  I'll probably remove that static yubikey method - while it is slightly more secure than just typing everything due to the length, someone familiar could easily get the static output if they ever had access and knew how to get it replayed rather than the ever-changing outputs.  Completely OT, sorry.

I didn't answer the question about LUKS being used during the install.  Yes, it does.  The limited reading I've done about encryption on Linux says to always use LUKS if you aren't an expert.  I've followed that.  I have played with some flash and portable SSD drives using LUKS encryption too.  When all the tools are installed, caja, the mate file manager seems to know how to open the encryption, then activate any LVM VGs, and access LVs.  I found this surprising when it all just worked.  The only issue I had was that VG names couldn't be already used on the system. This is an issue if we 100% clone some storage onto new storage, but want to access the older storage too.  In the end, I wiped the original SSD and started over.

---

