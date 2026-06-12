---
title: "Linux filesystems (ext3, ext4, etc...) healthier for a harddrive than NTFS filesystem"
date: 2010-04-26
forum: The Cafe
---

### Post by wpLOL on 2010-04-26
I was just wondering, are Linux filesystems healthier on a hard drive than a Windows filesystem? I was thinking because Ext3/4 don't suffer from disk fragmentation nearly as bad as NTFS does, also file transfers/Unpacking files are much, much faster than on Windows.

---

### Post by MasterNetra on 2010-04-26
> **wpLOL said:**
> I was just wondering, are Linux filesystems healthier on a hard drive than a Windows filesystem? I was thinking because Ext3/4 don't suffer from disk fragmentation nearly as bad as NTFS does, also file transfers/Unpacking files are much, much faster than on Windows.

Well its healthier for your system as fragmenting occurs much more slowly. As for physically I would say ext2 and just about any file system that doesn't do file journaling would be better as there would be less writing, but then again constantly using (moving, creating, copying, and pasting files) a drive occupied with ext2 would wear down the hard drive faster then a barely used ntfs one.

My $0.04

---

### Post by renkinjutsu on 2010-04-26
yes, the linux filesystems don't fragment nearly as much as ntfs but both ext3 and ext4 write to disk everytime a file is access to change its atime. A lot of disk writes can wear down your harddrive. There are ways around it though (noatime mount option)

---

### Post by wpLOL on 2010-04-26
> **MasterNetra said:**
> Well its healthier for your system as fragmenting occurs much more slowly. As for physically I would say ext2 and just about any file system that doesn't do file journaling would be better as there would be less writing, but then again constantly using (moving, creating, copying, and pasting files) a drive occupied with ext2 would wear down the hard drive faster then a barely used ntfs one.

My $0.04

Yeah, my parents use Windows Vista on their computers, their hard drives are constantly doing something, as you can hear it working, yet, you're not actually do anything, no file transfers, programs running, etc... but on Ubuntu, my hard drive is completely quiet, I only hear it when I'm running programs, watching movies, etc...

> **renkinjutsu said:**
> yes, the linux filesystems don't fragment nearly as much as ntfs but both ext3 and ext4 write to disk everytime a file is access to change its atime. A lot of disk writes can wear down your harddrive. There are ways around it though (noatime mount option)

That's what I was thinking too

---

### Post by speedwell68 on 2010-04-26
Off on a slight tangent of curiosity.  Are there any defrag programs available for Linux?  It is something I have largely forgotten about doing since I started using Ubuntu exclusively about 4 years ago.

---

### Post by MasterNetra on 2010-04-26
> **wpLOL said:**
> Yeah, my parents use Windows Vista on their computers, their hard drives are constantly doing something, as you can hear it working, yet, you're not actually do anything, no file transfers, programs running, etc... but on Ubuntu, my hard drive is completely quiet, I only hear it when I'm running programs, watching movies, etc...



That's what I was thinking too

Background Intelligent Transfer Service, it does things automatically without you knowing what its doin.

---

### Post by chriswyatt on 2010-04-26
There's one still in development for EXT4 I believe:

[http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/](http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/)

---

### Post by renkinjutsu on 2010-04-26
> **speedwell68 said:**
> Off on a slight tangent of curiosity.  Are there any defrag programs available for Linux?  It is something I have largely forgotten about doing since I started using Ubuntu exclusively about 4 years ago.

Not really... you can make a tarball of all your files onto another drive, then untar it back into your filesystem.

If you're using btrfs, it comes with an online defrag program.. pretty neat!

---

### Post by chriswyatt on 2010-04-26
> **MasterNetra said:**
> Background Intelligent Transfer Service, it does things automatically without you knowing what its doin.

Oh, is that what it's called?  I would've called it Annoying Doing Things Behind Your Back Service myself.

---

### Post by MasterNetra on 2010-04-26
> **speedwell68 said:**
> Off on a slight tangent of curiosity.  Are there any defrag programs available for Linux?  It is something I have largely forgotten about doing since I started using Ubuntu exclusively about 4 years ago.

[http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/](http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/)

Haven't tested myself though if your using ext4 you most likely won't need this. As ext4 is suppose to be extremely resistant to fragmentation.

> **chriswyatt said:**
> Oh, is that what it's called?  I would've called it Annoying Doing Things Behind Your Back Service myself.

Too long, besides you can disable it, though it might need to be enabled for updates otherwise its fodder.

---

### Post by wpLOL on 2010-04-26
> **MasterNetra said:**
> Background Intelligent Transfer Service, it does things automatically without you knowing what its doin.

What's its actually purpose? lol

---

### Post by szymon_g on 2010-04-26
> **renkinjutsu said:**
> yes, the linux filesystems don't fragment nearly as much as ntfs

i wouldn't say that, let say, ext2 doesn't fragment as much as ntfs.

> **renkinjutsu said:**
> but both ext3 and ext4 write to disk everytime a file is access to change its atime. A lot of disk writes can wear down your harddrive. There are ways around it though (noatime mount option)

thats why devs invented 'relatime' mount option

---

### Post by MasterNetra on 2010-04-26
> **wpLOL said:**
> What's its actually purpose? lol

There is a explanation on wiki:
[http://en.wikipedia.org/wiki/Background_Intelligent_Transfer_Service](http://en.wikipedia.org/wiki/Background_Intelligent_Transfer_Service)

---

