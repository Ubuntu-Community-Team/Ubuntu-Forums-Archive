---
title: "Secure backup recommendations?"
date: 2007-06-02
forum: Server Platforms
---

### Post by cryogen on 2007-06-02
Hi all,

I'm wondering if anyone here would have some recommendations for a way to securely backup a server to a semi-dedicated backup system?

A little background on the network setup would probably be in order.  What I'm working with is a physics research lab with all the machines on the campus network and hence open to attack.  As such, I installed openvpn and firewalls on all the boxes (ubuntu, XP, OSX) to encrypt and filter all traffic between them.  The the main server is an ubuntu box running samba over openvpn and serving files to all the other boxes.  I'm setting up another ubuntu box to be used almost exclusively as a backup repository in a separate room.   The primary goal of all this is data integrity and loss prevention all while being as automated as possible.

What I'm trying to decide is what's the best way to backup the main ubuntu server to the backup server?  After some research I've concluded I want to use rsnapshot to do the actual backups since it seems to do what I need.  The question is, would it be safer to have rsnapshot ssh into the file server and backup that way, or to mount the samba share on the backup machine and have rsnapshot copy locally?  

Encryption-wise I know the ssh solution is better, but I'm also looking for failsafe options and total automation.  If I go with the ssh option I probably (?) want to chroot it with chrootssh so the rsnapshot system can only see the directory to be backed up.  However I don't want to recompile openssh every time a new version comes out, thus making the local samba share look attractive.

If anyone has any comments, things I haven't thought of, relevant links or tricks they would be greatly appreciated.

--cryogen

---

### Post by Chayak on 2007-06-03
Well the easiest way I know of is using truecrypt on your backup machine and using a script to mount the remote truecrypt volume and then copy the data over and unmount it.

Then there are command line tricks using AES pipe.

Though now that I think of it you can use a simple script to .tar your files and then use GPG to encrypt them to your public key before they are copied over to the remote server.

---

### Post by kidders on 2007-06-03
Hi there,

It seems to me that your reason for creating a VPN was to handle security/privacy issues at the packet level. If that's true (ie you trust it to meet your security requirements), then there should be no need to wrap network communications in further encryption ... provided, of course, the data being backed up never leaves the VPN. I suppose it's all about trading performance & implementation complexity off against safety. What do you think of the following statements? Imo, what your best choices are depends on how reasonable you you find them...[LIST]
[*]You trust your VPN to make it impractically time-consuming for malicious users to interfere with your research. If you didn't, you wouldn't be using one.
[*]Although ugly, Windows filesharing works easily with all major OSs, so it's the ideal way to exchange files between computers on your network.[/LIST]Two other things come to mind, that might be worth thinking about...

**- I -**
Whether you would prefer to have your backup server connect periodically to your clients and copy files, or have the client machines drop backups onto the server. It looks like you've already decided on the former, but tbh I would prefer the latter. (Just an opinion.) [SIZE=1]**Edit:** I suspect Chayak agrees hehe.[/SIZE]

**- II -**
Depending on how sensitive your research is, you might like to consider on-disk encryption on the backup server. [SIZE=1]**Edit:** Already mentioned by Chayak :-) [/SIZE]It could be, for instance, that while theft of any hard drive on your network would be very bad, the loss of one from the *backup* server (which could contain years worth of data) would be disastrous.


One final thing that I'm not so sure about it what you would say the primary purpose of your backups is. For instance, it could be...[LIST]
[*]Restoration of a damaged machine ... ie copying back the most recent versions of your files.
[*]Recovery of lost data ... ie copying back old data that had been deleted.[/LIST]I suppose what I'm wondering about is how paranoid you want to be about the accuracy of your backups.

[SIZE="1"][COLOR="Silver"][UAResolved][/COLOR][/SIZE]

---

### Post by Chayak on 2007-06-03
Well if you really want to be paranoid you can go the route of full disk encryption.

[http://www.linux.com/howtos/Disk-Encryption-HOWTO/index.shtml]("http://www.linux.com/howtos/Disk-Encryption-HOWTO/index.shtml")

Though I would prefer something like pointsec myself if your data is that valuble.  The first thing to do it find a secure room and lock the server in there with a battery backup then you start scripting...

All network interfaces are down until the time of backup then it brings it up and connects to the remote machine to be backed up.  It mounts a truecrypt volume using a keyfile on the remote computer.  It then creates a tar file and does a hash of that file before copying.  It checks the copied file against the hash and uses a remote GPG key to encrypt the archive marking it with date and time and then drops the interface offline again until it's next 'check in'.  The truecrypt volume unmounts and the volume file is backed up to tape.  There is all kinds of crazy stuff you can do if you really put your mind to it and use a little imagination.

Great... now I want to play around with that myself ;)

---

### Post by Brazen on 2007-06-03
> **Chayak said:**
> 
Though now that I think of it you can use a simple script to .tar your files and then use GPG to encrypt them to your public key before they are copied over to the remote server.

I like the sound of that.  How would you go about encrypting it with GPG?

---

### Post by Chayak on 2007-06-04
```
gpg -e *file*
```

GPG can do a lot check the help on it.

As for how I'll do all I mentioned before in a script I'll figure that out but I'm thinking the first thing I'll do is to rsync from the remote directory then tar that directory and run it through gpg before going to tape

```
#!/bin/bash
mkdir destdir
tar cf - mydir | gpg -c > destdir/myfile.tar.gpg

```

A possibility to build off of that I googled up

Though be careful when making one big .tar file and encrypting it.  If any part of it gets corrupted you've lost the entire .tar

the duplicity program looks promising as well.

---

### Post by cryogen on 2007-06-04
Wow!  Thanks for all the responses!

I guess to answer kidders' question, I'm looking to be paranoid with the backups, but mainly with making sure the file that gets copied to the backup server is **exactly** the same as the original.  The point of all this is data integrity. The os can be reinstalled and all the encryption keys can be regenerated, but the data cannot be reproduced.  We have about five years worth of experimental data to deal with so far.

As far as using the VPN goes, I realize that I'm probably being paranoid and that openvpn is pretty good, but what I've been trying to do is manage these machines as if the VPN isn't there.  That is, I'm treating everything as if it's totally open on the net.  The reason for doing that is mainly because I have XP boxes on the network, and as far as I'm concerned they're a giant gaping security hole, but I'm not allowed to get rid of them. :(  Furthermore, even if someone manages to crack the VPN they'll still have to get through all the other defenses which should be able to stand on their own without relying on the VPN at all.

> **kidders said:**
> 

**- I -**
Whether you would prefer to have your backup server connect periodically to your clients and copy files, or have the client machines drop backups onto the server. It looks like you've already decided on the former, but tbh I would prefer the latter. (Just an opinion.) [SIZE=1]**Edit:** I suspect Chayak agrees hehe.[/SIZE]

You're correct in your assessment.  Perhaps a little more background would be in order here:  right now, the windows clients are pulling live nightly backups to the local hard disks so if a machine dies we only lose a day's work.  Naturally, this involves samba and but has no provision for incremental backup.  The main server is doing a weekly backup to a local disk with daily incrementals.  The backup server would be also be doing remote incrementals with a weekly full backup, but preferably with a different method of doing them.   

I really want to avoid samba if I can because it creates a single point of failure in the backup system.  However, using ssh creates the hassle of chrooting it, (although I found a [_link_]("http://www.debian.org/doc/manuals/securing-debian-howto/ap-chroot-ssh-env.en.html") just now and it looks like I might be able to do that with pam instead of recompiling).

What exactly would be gained by having the server push the backups to the backup client as opposed to the other way around?

> **Chayak said:**
> Well if you really want to be paranoid you can go the route of full disk encryption.

[http://www.linux.com/howtos/Disk-Encryption-HOWTO/index.shtml]("http://www.linux.com/howtos/Disk-Encryption-HOWTO/index.shtml")


I've thought about using full disk encryption, but the main reason I haven't already done so is that I see it as a potential risk to the integrity of the data.  This is because I envision a scenario where I'm forced to reinstall the machine with the encrypted backups (due to a rootkit or such) but now the reinstalled system won't be able to read the encrypted drive with all our data in it (please enlighten me if I'm wrong :smile: ).  But if that happens, we may as well have not had the backup at all...  Hence the main goal of data integrity would be failed.  But I really like Chayak's GPG idea since that would include integrity checking!

By the way, the data isn't particularly sensitive by itself since someone would also need the physical component of our notebooks to get anything interesting, and both labs are locked with only known people having access.  Hence, I'm not overly concerned about physical theft but I'm **very** worried about hardware failure and keeping every last file exactly as it needs to be.

Again, probably the main reason for asking this question in the first place is the fact that I'm assuming the VPN isn't there.  Maybe I'm being overly paranoid or stupid...

Thanks again for all the responses!

--cryogen

---

### Post by Chayak on 2007-06-04
Well for data integrity you keep backups of your encryption keys in a safe place.  Though if you want to make sure your data is protected then I would suggest the tried and true tape drive.  Tape drives are a little expensive but they're designed for long term data storage.

---

### Post by elst on 2007-06-04
I haven't tried it, but Bacula is a fairly well-established network backup system that can use SSL to protect the transfer, and can optionally encrypt the backups. It also supports tape drives.

FWIW, you can apparently add permitted commands to SSH keys, so that they can't be used to perform other functions, which may make chroot less necessary.

---

### Post by cryogen on 2007-06-07
Just a follow up.

What I finally ended up doing was using rsnapshot to login over ssh and restricted the ssh key to executing only the relevant rsync command.

Thanks everyone for the responses!

--cryogen

---

### Post by chrisbain88 on 2007-08-10
Hey,
What about backing up using the dump command to backup the system.  The only problem that i currently see is that your will have to enter the root password for the command to commence.
Cheers
Chris

---

### Post by elst on 2007-08-11
Apparently, you have to be careful if you use dump with mounted filesystems:

[http://http://dump.sourceforge.net/isdumpdeprecated.html]("http://http://dump.sourceforge.net/isdumpdeprecated.html")

---

