---
title: "I have SSH running, but would like to create a new login with limited access"
date: 2011-06-07
forum: Server Platforms
---

### Post by diablo75 on 2011-06-07
I have SSH running on a computer I use as a server at home and login to it for my own purposes but am needing to share access to this server with someone else, and I'd like to do it in a way so that when they sign in all they see is the contents of one folder and nothing outside of it.  So I'd like them to have full access to this folder and do anything they want with it, but not be able to browse outside of it at all via something like WinSCP (they're using Windows).  I'm thinking I need to create a new account for them to sign in with but beyond that I'm not sure what I need to do.  The only other special thing is that the folder I'd like them to be presented with is actually on an external hard drive.  We're going to be doing a lot of online music collaboration and I need to give him lots of free space to drop files and the internal hard drive doesn't have a lot to spare right now.

---

### Post by Dry Lips on 2011-06-07
**1.** First of all... Why did you post this under Absolute beginner? 
You're no beginner, and this topic would be more suitable under
 &#8220;Server Platforms&#8221;. ;)

 

 **2.** I think your external HDD would be mounted under /media.
 See this reference for how to mount your  external HDD.
 [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
 [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
  

 **3.** How to create a locked user:
 ```
cd /media/yourHDD
mkdir userdirectory
useradd user1 -d /media/yourHDD/userdirectory1
chown -hR user1 /media/yourHDD/userdirectory1 
passwd user1

``` **4.** In addition I would disable their opportunity to SSH into your machine if I were you.

---

### Post by lisati on 2011-06-07
*Thread moved to **Server Platforms**.*

---

### Post by diablo75 on 2011-06-07
> **Dry Lips said:**
> **1.** First of all... Why did you post this under Absolute beginner? 
You're no beginner, and this topic would be more suitable under
 &#8220;Server Platforms&#8221;. ;)

 

 **2.** I think your external HDD would be mounted under /media.
 See this reference for how to mount your  external HDD.
 [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
 [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
  

 **3.** How to create a locked user:
 ```
cd /media/yourHDD
mkdir userdirectory
useradd user1 -d /media/yourHDD/userdirectory1
chown -hR user1 /media/yourHDD/userdirectory1 
passwd user1

``` **4.** In addition I would disable their opportunity to SSH into your machine if I were you.

I did all the above and tested it out and it sort of works.  When I login to the server via ssh using their username, it defaults to their new folder so they have immediate access to it.  However, they can still back out of the folder up the file tree and into the rest of the system without restriction.  I would rather it treat their folder as if it's the only folder in the entire computer, so to speak.  Perhaps this has to do with the way SSH works.  Perhaps FTP would be better?  I don't know.  What's the best way to do what I'm trying to do?

On a related note I would like to do this with an entire hard drive (share it out via a new account) but restrict it so that they can upload new files (perhaps into a specific folder) but not delete anything.

---

### Post by Dry Lips on 2011-06-08
> **diablo75 said:**
> I did all the above and tested it out and it sort of works.  When I login to the server via ssh using their username, it defaults to their new folder so they have immediate access to it.  However, they can still back out of the folder up the file tree and into the rest of the system without restriction.  

Yes, because you need to do what I said in point **4.**, (disable their opportunity to SSH into your machine.) I didn't provide a link for this, (sorry, it was late at night) but here you go:

[http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#SFTP-only_Accounts](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#SFTP-only_Accounts)

[http://www.openbsd.org/cgi-bin/man.cgi?query=sshd_config&sektion=5&arch=i386&apropos=0&manpath=OpenBSD+Current](http://www.openbsd.org/cgi-bin/man.cgi?query=sshd_config&sektion=5&arch=i386&apropos=0&manpath=OpenBSD+Current)

> On a related note I would like to do this with an entire hard drive  (share it out via a new account) but restrict it so that they can upload  new files (perhaps into a specific folder) but not delete  anything.You'll need to automatically mount your hdd, as described in the link under point **2.** above. Since the HDD is mounted under /media it should be no different than giving access to a normal folder.

About not deleting files, you'll need to look into setting file permissions:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Clear as mud? ;) Let us know if you get stuck!

---

### Post by diablo75 on 2011-06-08
Awesome. Looks like I should be able to figure the rest out with the link you provided.  Thanks for the help!

---

### Post by Dry Lips on 2011-06-08
> **diablo75 said:**
> Awesome. Looks like I should be able to figure the rest out with the link you provided.  Thanks for the help!

Well, use caution... This is advanced stuff. Back up all configuration files that
you tamper with, and don't attempt this without physical access to your server,
in case you lock yourself out.

And if you're stuck, give us an update!

--

Another excellent tutorial:
[http://www.howtoforge.net/chrooted-ssh-sftp-tutorial-debian-lenny](http://www.howtoforge.net/chrooted-ssh-sftp-tutorial-debian-lenny)

---

