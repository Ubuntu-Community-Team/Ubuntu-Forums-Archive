---
title: "Mac OS X mounting Samba Partition"
date: 2009-04-14
forum: The Cafe
---

### Post by glug101 on 2009-04-14
Hello all!

I guese this is not exactly the best place to post this, but I couldn't think of a better place since this is not directly a linux issue.  I've setup a Ubuntu 8.04 based firewall/router at my small church and I'm turning on functionality slowely.  I am adding network shares so that files can be shared across mac os x and windows pcs.  Samba seems to be the natural choice, but I'm having trouble mounting it with the mac.  

I can get the mac to mount the samba share, but I can't get it to remember the mounting.  Reboot the computer and you need to reconnect manually.  The silly thing doesn't even remember the loginid and passwd even though I clicked the option to remember it on the keychain.  

Any ideas?  I'll bet that somebody here has experience with this and I would like to thank them heartily beforehand.

Have a happy day!

---

### Post by bashveank on 2009-04-14
[AutoMountMaker?]("http://jm.marino.free.fr/index.php?switch=sw_&title=AutomountMaker")
edit: or just put the mount commands into a script and put the script in your login items...
edit 2: if you drag the icon for the net drive into login items then it'll mount on login...
edit 3: or you could always make an automator action, save it as an application, and put it in your login items....

---

### Post by Keith Hedger on 2009-04-14
> **bashveank said:**
> ...
edit 2: if you drag the icon for the net drive into login items then it'll mount on login...
...


Didn't know you could do that! well live and learn :)

---

### Post by glug101 on 2009-04-14
Wow, this is what I love about this community.  What was that, less than 15 minutes?  

I'll check out AutoMountMaker and I might try the first 2 edits you put in, but Automater is right out.  The computer is running OS 10.2.  Having used OSS for as long as I have, my skin crawls a bit when having to leverage a 5 year old operating system.  But, there it is.  

Thank you very much Bashveank!

---

### Post by stchman on 2009-04-14
> **glug101 said:**
> Hello all!

I guese this is not exactly the best place to post this, but I couldn't think of a better place since this is not directly a linux issue.  I've setup a Ubuntu 8.04 based firewall/router at my small church and I'm turning on functionality slowely.  I am adding network shares so that files can be shared across mac os x and windows pcs.  Samba seems to be the natural choice, but I'm having trouble mounting it with the mac.  

I can get the mac to mount the samba share, but I can't get it to remember the mounting.  Reboot the computer and you need to reconnect manually.  The silly thing doesn't even remember the loginid and passwd even though I clicked the option to remember it on the keychain.  

Any ideas?  I'll bet that somebody here has experience with this and I would like to thank them heartily beforehand.

Have a happy day!

I personally have had problems getting Ubuntu to deal with Samba shares.

Since OS X is a *ix based OS it probably has the same quirks as Ubuntu.

I personally use NFS on my Linux machines.  It works far better and the mount stays put.  Problem is that XP does not support NFS natively.

---

### Post by glug101 on 2009-04-14
> **stchman said:**
> I personally have had problems getting Ubuntu to deal with Samba shares.

Since OS X is a *ix based OS it probably has the same quirks as Ubuntu.

I personally use NFS on my Linux machines.  It works far better and the mount stays put.  Problem is that XP does not support NFS natively.

Exactly why I can't use NFS.  WinXP box is on the network and the two need to be the same.  At home (OSX and Linux only) I use NFS.  Works great.  However, in my meager experience, I've found that connecting to a linux samba server to be less flakey than a windows server.  (admittedly been a few years since I tried it last though)

---

