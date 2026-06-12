---
title: "Secure data removal"
date: 2008-02-25
forum: Security Discussions
---

### Post by Bunnykun on 2008-02-25
Hi guys, I have a question. 

Is there a linux equivalent to Eraser for windows?  I'm looking for a secure file removal tool, and my googling attempts have yielded nothing thus far.

[_Link to Eraser's Website_]("http://www.heidi.ie/eraser/default.php")

---

### Post by Rhubarb on 2008-02-25
If you're confident with the terminal, then you should try out secure-delete.
Grab secure-delete from the ubuntu repositories:
```
sudo aptitude secure-delete
```

Then you can use:
```
sudo srm file_to_delete
```

Depending on the sensitivity of the file you wish to delete, srm has a few different flags you can pass to it.

It's best to read up the man page for srm:
```
man srm
```

Also have a look at srm sfill sswap and smem.
Secure deleting may not be that secure on a journalled filesystem (like ext3, the default in ubuntu).
Also secure-delete may not be that effective on flash memory, as flash memory controllers often have level-wearing chips, which means the io address your computer wants to access on the flash drive is not always the same real io address that's actually access everytime.

I'm not sure if there's an easier more friendly way of securely deleting files.

---

### Post by HermanAB on 2008-02-25
Hmm, first you have to identify what your threat level is.  If you only want to protect yourself against your kid sister, then just delete the files the ordinary way.  

The problem with file erase utilities is that they don't really work (on both Linux and Windows!).  They put up a good show though and most people will likely be fooled by them.  However, in practice, the special file erase utilities are not much better than just deleting them the normal way.

If you really want to delete stuff so that even the government will have difficulty retrieving the data, then you need to wipe the whole disk: [http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

If you want to be sure that the government cannot recover the data, then you need to encrypt the disk and to delete the data - forget the key.  Which is fine if you live in a country that doesn't practise torture...

The other way to securely delete data is to use a very big hammer, a high power rifle, or a welding torch - your choice.

---

### Post by edm1 on 2008-02-25
> **Bunnykun said:**
> Hi guys, I have a question. 

Is there a linux equivalent to Eraser for windows?  I'm looking for a secure file removal tool, and my googling attempts have yielded nothing thus far.

[_Link to Eraser's Website_]("http://www.heidi.ie/eraser/default.php")

Ubuntu comes with one built in. Just use 'shred' instead of 'rm'. For more info type 'man shred' in the terminal.

---

### Post by bodhi.zazen on 2008-02-25
I was about to mention shred ...

There is also dban

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by HermanAB on 2008-02-25
Yup, shred, dban, except that they are not really any better than rm.

---

### Post by Bunnykun on 2008-02-25
All good info, thanks a lot guys!  :]

---

### Post by rapiscan on 2008-02-25
> **HermanAB said:**
> Yup, shred, dban, except that they are not really any better than rm.

Your comment really intrigued me.  Why are dban, srm, shred not more secure than rm?

---

### Post by ruy_lopez on 2008-02-26
Another tip is to create a file using /dev/zero, after you delete a file.

```
dd if=/dev/zero of=bigzero bs=4096
```

Find your block size using stat on a directory. Replace 'bs=4096' with the size of your blocks. 

Eventually 'dd' will run out of disk space. Delete the file 'bigzero'.

Now all your unallocated blocks will be filled with zeros.

EDIT: install 'dcfldd' and use the same as 'dd', if you want a progress readout (good idea).

---

### Post by ruy_lopez on 2008-02-26
This illustrates the problem with "srm". To follow you'll need "sleuthkit" and "secure-delete".

Create a file called data. "ls -Fhli" shows the inode numbers on the left.
```

private@host:~$ echo "this is data, data, data" > data
private@host:~$ cat data
this is data, data, data
private@host:~$ ls -Fhli
total 16K
802821 -rw-rw---- 1 private private   25 2008-02-26 11:54 data
802824 drwxrwx--- 2 private private 4.0K 2008-02-26 11:43 docs/
802827 drwxrwx--- 2 private private 4.0K 2008-02-26 11:43 etc/
802818 drwxrwx--- 2 private private 4.0K 2008-02-26 11:43 files/

```

Now, using Sleuthkit's "istat" command with the inode from "data". At the bottom, istat shows the allocated blocks. "/dev/hda6" is my /home partition, run "df" to find your own device.

```

private@host:~$ istat /dev/hda6 802821
inode: 802821
Allocated
Group: 49
Generation Id: 1770472290
uid / gid: 1001 / 1001
mode: -rw-rw----
size: 25
num of links: 1

Inode Times:
Accessed:       Tue Feb 26 11:54:47 2008
File Modified:  Tue Feb 26 11:54:38 2008
Inode Modified: Tue Feb 26 11:54:38 2008

Direct Blocks:
1619968 

```

Next, we run "dd". "bs=4096" refers to the block size. "skip=1619968" refers to the direct block (given by istat).

```

private@host:~$ dd if=/dev/hda6 bs=4096 skip=1619968 | xxd | less 

0000000: 7468 6973 2069 7320 6461 7461 2c20 6461  this is data, da
0000010: 7461 2c20 6461 7461 0a00 0000 0000 0000  ta, data........
0000020: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000030: 0000 0000 0000 0000 0000 0000 0000 0000  ................
...

```

We run "srm data" to "securely" delete the file 'data'. A subsequent call to 'istat' shows the file is unallocated. Is the file 'data' gone?

```

private@host:~$ srm data 
private@host:~$ istat /dev/hda6 802821
inode: 802821
Not Allocated
Group: 49
Generation Id: 1770472290
uid / gid: 1001 / 1001
mode: -rw-rw----
size: 0
num of links: 0

Inode Times:
Accessed:       Tue Feb 26 11:54:47 2008
File Modified:  Tue Feb 26 12:03:44 2008
Inode Modified: Tue Feb 26 12:03:44 2008
Deleted:        Tue Feb 26 12:03:44 2008

Direct Blocks:

```

Look below. The data was supposedly cleared. However, running 'dd' again, on the same block as before, shows the data still lingers. 'srm' hasn't cleared the block.

```

private@host:~$ dd if=/dev/hda6 bs=4096 skip=1619968 | xxd | less

0000000: 7468 6973 2069 7320 6461 7461 2c20 6461  this is data, da
0000010: 7461 2c20 6461 7461 0a00 0000 0000 0000  ta, data........
0000020: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000030: 0000 0000 0000 0000 0000 0000 0000 0000  ................
...

```

To clear the block you need to run 'sfill' or use 'dd' with if=/dev/zero or if=/dev/urandom to fill up the filesystem.

---

### Post by HermanAB on 2008-02-26
That is a really cool demo of non-deletion.

It actually goes even further than that.  On the microscopic level, successive overwrites on a disk platter creates 'layers' of data which can be retrieved with special equipment.  

This is further exagerated by today's enormous disk drives, which don't overwrite the same place even twice, unless the disk has been in use for many, many years.  The bigger the drives, the less overwriting occurs.

The result is that if your adversary has a few thousand dollars to waste, then your 'erased' and 'overwritten' data can be retrieved, by using special equipment.

Therefore the only effective way to prevent data retrieval, is by using encryption, since that ensures that the data on the disk is randomized.  Any  other file delete method is just smoke and mirrors.

---

### Post by rapiscan on 2008-02-26
HermanAB,

I would like to learn more on the subject, so if you don't mind humoring me whlie I play devil's advocate...

I read relevant portions of this paper, which confirms your assertion:
[http://www.cs.auckland.ac.nz/~pgut001/pubs/secure_del.html](http://www.cs.auckland.ac.nz/~pgut001/pubs/secure_del.html)

The paper notes that it's relatively easy and to read a couple of the previous levels with inexpensive equipment. It occured to me that programs like shred should really write many times in order to make it more difficult to recover data. 

Looking at the man page, I found "Overwrite the specified FILE(s) repeatedly, in order to make it harder for even very expensive hardware probing to recover the data.".

So this is pretty good news for those that use shred.  You've pretty much written off shred for being as useless as rm, but I would argue that using shred is a very good way to secure your data from most people.  Without shred, it's trivial to recover a deleted file.  I realize that it's not 100% effective, but at the same time it sounds like it takes rather expensive equipment and very knowledgeable people to recover data from a magnetic disc that has been written over many times.

EDIT: I just realized this paper is from 1996, so perhaps equipment to read from magnetic discs is cheaper and easier to use.  Is anyone aware of where to purchase this sort of thing?  (I don't want to buy one, but I'm really curious how expensive this type of equipment is.)

---

### Post by tubezninja on 2008-02-26
> **rapiscan said:**
> Your comment really intrigued me.  Why are dban, srm, shred not more secure than rm?

It looks like the shred man page answers why shred isn't too effective in some cases:

> CAUTION:  Note that shred relies on a very important assumption: that the file systemoverwrites data in place.  This is the traditional way to do things, but many  modern file  system  designs  do not satisfy this assumption.  The following are examples of file systems on which shred is not effective, or is not guaranteed to be effective in all file system modes:

       * log-structured or journaled file systems, such as those supplied with AIX and Solaris (and **JFS, ReiserFS, XFS, Ext3, etc**.)

       * file systems that write redundant data and carry on even if some writes fail, such as RAID-based file systems

       * file systems that make snapshots, such as Network Appliance&#8217;s NFS server

       * file systems that cache in temporary locations, such as NFSversion 3 clients

       * compressed file systems


Considering quite a few of us are using journaled ext3 or ReiserFS, it would seem shred is of limited usefulness.

However, I'm pretty sure dban is effective enough as it does a whole disk wipe and obliterates the file system, regardless of what it is.  It just takes a while to get an effecitve wipe.

---

### Post by ruy_lopez on 2008-02-26
(deleted)

---

### Post by HermanAB on 2008-02-26
The dban whole disk wipe is better, but awfully slow and if you really want to wipe the whole disk, then the routine built into the disk controller itself is much better and faster: [http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

---

