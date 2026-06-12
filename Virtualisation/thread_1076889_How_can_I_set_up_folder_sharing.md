---
title: "How can I set up folder sharing?"
date: 2009-02-21
forum: Virtualisation
---

### Post by ElevenWarrior on 2009-02-21
I've already went through the manual, I followed the directions, for host/guest folder sharing, but I still can't get it to work.
 I go to My network places>entire network.
and my shared folder isn't there.
any ideas?
thanks in advance

---

### Post by Syngensmyth on 2009-02-22
Subscribed to view answers. I am having problems with this also. VirtualBox Host is Vista64, client is Mint Linux. What is your host/client config?

---

### Post by HawkST on 2009-02-23
I don't know if you have tried this particular set of instructions yet, but [this is what worked for me.]("http://ubuntuforums.org/showthread.php?t=627847#7") Once done, it will appear in My Computer, at the bottom.

Edit* this assumes you have XP as your virtual drive (as appears to be commonplace here).

Syngensmyth, you will need modify the last step, mount using
```
mount -t vboxsf share mount_point
```

I haven't tried it with Linux as the virtual drive, so let us know how you get on.

---

### Post by HermanAB on 2009-02-23
Hmm, since I always have problems with folder sharing, I simply use FTP.  Filezilla server and client or vsftpd on the Linux host.  Nothing simpler than that and it always works.

Then at a later date, once the system is stable, I may configure NFS:
[http://aeronetworks.ca/nfs-howto.html](http://aeronetworks.ca/nfs-howto.html)

Cheers,

Herman

---

### Post by Syngensmyth on 2009-02-24
vboxsf not found error

I did set up a share in guest so not sure whats up. Share in Mint Guest is odd. I can't point to the subfolder in home so it designates all of home. But in VB the share is a folder within home. 

I'll try Herman's ftp idea also. Sorry to hijack ... seems same subject. Thanks Eleven.

OK Herman ... ftp works wonders, many thanks. Maybe someday I'll get VB share to work but for now I can at least write files somewhere.

VB forum is worthless by the way. "Read the manual." If one wishes to give that answer, why bother answering?

---

