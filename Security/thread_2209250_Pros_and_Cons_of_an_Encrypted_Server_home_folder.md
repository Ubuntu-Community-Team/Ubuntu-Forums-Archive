---
title: "Pros and Cons of an Encrypted Server /home folder"
date: 2014-03-04
forum: Security
---

### Post by Elastic_Potential on 2014-03-04
Recently, I set-up a server which can be managed remotely.  However, I encrypted the home folder without realizing that this causes some mishaps for a server.  For instance, some config files in my home folder cannot be accessed unless I either: log-in manually on the server, or log-in from SSH and run ecryptfs-mount-private.  This is somewhat annoying because I'd like to access my home folder on boot.

I like the idea of encryption for when my computer isn't running at all; but, this is hindering some basic system functionality.  As this is my first time managing a server PC in a few years, I was wondering if you guys have any thoughts on whether or not the security benefits from a server's encrypted home folder outweigh the cons of practical use.

In short, if I re-install [L]ubuntu and choose instead to have an unencrypted /home, would there be any noticeable or disconcerting security holes?

---

### Post by thnewguy on 2014-03-05
Security holes? Home folder encryption is really only there to protect against someone getting your data when they have physical access to your machine. For example, if someone steals your laptop you might want the drive to be encrypted so the thief cannot read your files. Someone physically stealing a server is slightly less likely, especially if it is in a locked room/house/apartment.

For servers I do not encrypt partitions, it is more work than benefit. If you really need to protect sensitive data, then create an encrypted container inside your home directory and store the sensitive data there. That will avoid the hassles of encrypted home directories and still offer protection.

---

### Post by ant2ne on 2014-03-05
Square peg round hole. The purpose to encrypting a directory is to prevent your data from being compromised, primarily, if the drive is removed and then loaded into another machine. Otherwise your OS security (firewall, proper permissions etc) is designed to protect the data. If you aren't afraid of the drive being stolen, then you shouldn't need to encrypt it. 

Also, I'd say it is bad security practice to have some service access your home directory at start up. I'd move whatever that is that needs your home to some other place and then you can encrypt your home if you wish. Or is this a shared home directory? Like one PC hosts the home directory for another PC. And then using NFS of CIFS you connect to that home directory.

---

### Post by Elastic_Potential on 2014-03-05
Thank you both for the insights.  I doubt it'll be stolen any time soon, so I'll just reinstall Linux, leave my home partition unencrypted, and put all my sensitive information in an encrypted partition.

[quote=ant2ne]Also, I'd say it is bad security practice to have some service access  your home directory at start up. I'd move whatever that is that needs  your home to some other place and then you can encrypt your home if you  wish.[/quote]
I would, but some programs, like rTorrent, require the config file to be in the home directory.  Also, I'm unsure how that would be bad practice; could you tell me more about that?

---

### Post by ant2ne on 2014-03-05
If you are running a torrent you are probably running it as a user and not as root so it probably isn't an issue. It depends I guess on how you are launching that torrent.

---

### Post by Elastic_Potential on 2014-03-05
> **ant2ne said:**
> If you are running a torrent you are probably running it as a user and not as root so it probably isn't an issue. It depends I guess on how you are launching that torrent. Using [this guide](http://www.karlrixon.co.uk/writing/start-rtorrent-automatically-at-boot-on-debian-ubuntu/), rTorrent boots in the background at startup; via SSH, I can toss the torrent files in a watch folder, so they'll be auto-loaded into the program.    As it stands, rTorrent can't access the rtorrent.rc file because it's in the encrypted home folder.  I'm sure there's a workaround for this, but a couple other programs suffer from this as well.

---

### Post by ant2ne on 2014-03-05
It would probably be best to create a separate user to run rTorrent with its own /home and keep your /home encrypted and secure. That is, unless the rTorrent user is the one who is creating or accessing the encrypted data. What other programs suffer from this?

---

### Post by bashiergui on 2014-03-05
Encrypting a drive is to protect it when it's not mounted. As soon as you mount it there is no benefit because it's decrypted upon mounting. If it's running all the time like a normal server and home is mounted all the time, then there are no benefits. If the idea is to protect sensitive data then just do encrypted containers like thnewguy suggested.

---

### Post by Elastic_Potential on 2014-03-05
> **ant2ne said:**
> It would probably be best to create a separate user to run rTorrent with its own /home and keep your /home encrypted and secure. That is, unless the rTorrent user is the one who is creating or accessing the encrypted data. That's a really good idea, hadn't thought of that.  I might just do this, at least until 14.04 is released.  > What other programs suffer from this? It's not a config file issue, but in terms of an encrypted home folder's interference, the other big one is scp.  The easiest way is to log-in and decrypt through SSH, then run scp; but it is a bit annoying, and it seems as if an unencrypted home would make things easier.

---

### Post by sh4d0w808 on 2014-03-07
If you want real secure storage then buy an FDE HDD/SSD - within this devices, encryption is hardware-supported. You can't solve a problem with software if it is not software-related.

---

