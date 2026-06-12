---
title: "Host: WinXP / Guest: Kubuntu / BackupPC &amp; USB Drive via samba"
date: 2008-04-29
forum: Virtualisation
---

### Post by sunspots on 2008-04-29
The title is a bit of a mouth full on what my set up is, which is
- Host OS: Windows XP Pro
- Guest OS: Kubuntu 8.04 Hardy Heron
- Guest OS Appl: BackupPC
- Virtual Appl: vmWare on Windows
- USB Drive on Windows XP and with shares for Kubuntu

I have a 320G USB drive that is recognized in XP. I have set up the shares, samba, and mounted the USB drive in Kubuntu.

I have also got BackupPC working and cataloguing the files from my  XP shares. However, they are being saved on the guest OS, Kubuntu. Which isn't the preferred option, a) system crash then backup lost, B) virtual system is not large, it's only 8Gig and backups of music files, etc is over 40Gig.

Unfortunately, BackupPC to work efficiently by using hard links to cut down on disk space cannot write to NTFS windows share (since NTFS does not recognize hard links).

Question. Can I somehow from the guest OS of Kubuntu format the Windows share drive into a Linux drive? 

I know I could go and dual boot (which I have got), but I have found that support for my machine to be missing in some areas. Plus, I'm still entrenched to using Windows. Using Kubuntu via vmWare gives me the best of both worlds and allows me to play and learn Kubuntu. With the ability to continually switching back and forth.

Any suggestions/pointers would be greatly appreciated.
Thanks

---

### Post by fjgaude on 2008-04-29
Seems to me you could boot up using the LiveCD for Kubuntu, if it has Gparted on it, and from there you could re-format, place an ext3 filesystem on the drive you wish to have as backup, or whatever.

---

### Post by sunspots on 2008-04-29
> **fjgaude said:**
> Seems to me you could boot up using the LiveCD for Kubuntu, if it has Gparted on it, and from there you could re-format, place an ext3 filesystem on the drive you wish to have as backup, or whatever.

Ok, sounds like the logical thing to do. 

But what about mounting? Will it still need to be mounted with samba & CIFS since it is connected to  XP (host OS)?

---

### Post by sunspots on 2008-04-30
I posted the same question on the vmWare forum. I was told, that I could create a new virtual drive that is to be housed on the USB drive. Then when in Kubuntu I can create a mount point and mount that virtual drive.

Just tested that and it worked fine.

Oh, I had to format the drive before doing the mounting. (In case someone comes across this message)

---

### Post by Alex Quinn on 2008-06-11
> **sunspots said:**
> Unfortunately, BackupPC to work efficiently by using hard links to cut down on disk space cannot write to NTFS windows share (since NTFS does not recognize hard links).

I saw this claim in the BackupPC documentation, too, but it's not true.  **NTFS most certainly does support hard links** (2 logical files pointing to the same inode).  However, you need either Cygwin or a downloadable tool from Microsoft to create them.  See my Cygwin session below for evidence.


```
Alex@conniekay ~
$ touch file1.txt

Alex@conniekay ~
$ ln file1.txt file2.txt

Alex@conniekay ~
$ echo Apples > file1.txt

Alex@conniekay ~
$ cat file1.txt
Apples

Alex@conniekay ~
$ cat file2.txt
Apples

Alex@conniekay ~
$ echo Oranges > file2.txt

Alex@conniekay ~
$ cat file2.txt
Oranges

Alex@conniekay ~
$ cat file1.txt
Oranges

Alex@conniekay ~
$ ls -l file?.txt
-rw-r--r-- 2 Alex None 8 Jun 11 12:02 file1.txt
-rw-r--r-- 2 Alex None 8 Jun 11 12:02 file2.txt

Alex@conniekay ~
$ stat file1.txt
  File: `file1.txt'
  Size: 8               Blocks: 1          IO Block: 65536  regular file
Device: d43f28aeh/3560908974d   Inode: 6473924464600201  Links: 2
Access: (0644/-rw-r--r--)  Uid: ( 1003/    Alex)   Gid: (  513/    None)
Access: 2008-06-11 12:02:37.765625000 -0400
Modify: 2008-06-11 12:02:31.671875000 -0400
Change: 2008-06-11 12:02:31.671875000 -0400

Alex@conniekay ~
$ stat file2.txt
  File: `file2.txt'
  Size: 8               Blocks: 1          IO Block: 65536  regular file
Device: d43f28aeh/3560908974d   Inode: 6473924464600201  Links: 2
Access: (0644/-rw-r--r--)  Uid: ( 1003/    Alex)   Gid: (  513/    None)
Access: 2008-06-11 12:02:37.765625000 -0400
Modify: 2008-06-11 12:02:31.671875000 -0400
Change: 2008-06-11 12:02:31.671875000 -0400

Alex@conniekay ~
$ cmd /c ver

Microsoft Windows XP [Version 5.1.2600]

Alex@conniekay ~
$
```



I wouldn't be surprised if there's some limitation or bug in the NTFS implementation of hard links that causes problems, but I'm not aware of anything specifically.  As far as I've seen, they work fine.  For example, the [finddupe]("http://www.sentex.net/~mwandel/finddupe/") tool uses WinXP hard links to reduce the space occupied by duplicate files.

---

### Post by sunspots on 2008-06-11
Hi Alex,
Thanks for the information and the test scenario. Recently, I have seen mention in the BackupPC mailing list mention of NTFS supporting hardlinks.

I wasn't aware that you still needed to download tools from MS or cygwin to make it work.

I'll have a look into this for future reference.
Thanks

---

