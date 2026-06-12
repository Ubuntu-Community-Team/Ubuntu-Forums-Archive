---
title: "Finally, Windows has seen the Light"
date: 2008-04-01
forum: Windows
---

### Post by Jammy4041 on 2008-04-01
Finally, I can read AND write to my ubuntu partition from my windows partiton, without having to reboot into linux everytime.

The answer was to use a piece of software called Ext2 IFS for Windows. (It also supports read/write to Ext3 as well.)

And I can assign my Linux, Swap partitions drive letters.

Thankyou Ext2 IS For Windows.

([PS- you can download it here]("http://www.fs-driver.org/download.html"))

---

### Post by PmDematagoda on 2008-04-01
Just so you know, that software you are talking about is not made by Microsoft and it is not affiliated to Microsoft in anyway, so your title is made invalid by that.

---

### Post by ashvee on 2008-04-01
thts cool 

but our aim is to avoid windows forever

---

### Post by ukripper on 2008-04-01
In my opinion, possible corruption could occur during journal index, when you save files from windows to ext3 may confuse the ext3 file system and would eventually cause conflicts with other files in use. 

Therefore, I would save it within linux itself unless you want to use ext2(doesn't comes with journal indexing feature).

---

### Post by Jammy4041 on 2008-04-01
It picks up my Ubuntu partition as ext2, but I was sure it was ext3.

---

### Post by r76 on 2008-04-01
> **Jammy4041 said:**
> It picks up my Ubuntu partition as ext2, but I was sure it was ext3.

Look, it's called Ext[COLOR="Red"]**2**[/COLOR]IFS, what more do you expect, it to be included as a default app in Windows? Oh wait....

---

### Post by qamelian on 2008-04-01
> **Jammy4041 said:**
> It picks up my Ubuntu partition as ext2, but I was sure it was ext3.
It only supports the ext2 filesystem without the jouranling features the differentiate 2 from 3.

---

### Post by tango_ninja on 2008-04-01
Dunno if this means that *Windows* has seen the light...maybe the windows development community :)

but it's definitely a useful tool

---

### Post by tubasoldier on 2008-04-01
> **ukripper said:**
> In my opinion, possible corruption could occur during journal index, when you save files from windows to ext3 may confuse the ext3 file system and would eventually cause conflicts with other files in use. 

Therefore, I would save it within linux itself unless you want to use ext2(doesn't comes with journal indexing feature).

You are absolutely correct. The major difference between ext2 and ext3 is journaling. I tried Ext2Fs before and as you speculated, my partition became corrupted. 

I highly recommend not using it unless you specifically use ext2

---

### Post by jimoz on 2008-04-02
I had it installed briefly... Windows crashed and started screwing with the ext3 partition.

I uninstalled it so Windows cant access it - solved that problem - and now use the NTFS partition only for documents that need to be shared between OSes.

---

### Post by kpkeerthi on 2008-04-02
> **Jammy4041 said:**
> Finally, I can read AND write to my ubuntu partition from my windows partiton, without having to reboot into linux everytime.

The answer was to use a piece of software called Ext2 IFS for Windows. (It also supports read/write to Ext3 as well.)

And I can assign my Linux, Swap partitions drive letters.

Thankyou Ext2 IS For Windows.

([PS- you can download it here]("http://www.fs-driver.org/download.html"))

I used it back in the days (in 2006) I dual booted. It was quite useful.

---

### Post by regbsn on 2008-04-03
I was planning to install ext2IFS to allow access to A/V media on my Ubuntu partitions from WinXP. I plan on mostly using Linux, so most of my media files will reside there. That is why most of y hard drive space is allocated to ext3 / home partition.
Should I only read from  Linux partition and not write to it? 
Can I safely drag and drop to NTFS WinXP sda1 mounted drive fro Linux.
I have been able to copy pictures to Linux (for DE background).

---

### Post by sayakb on 2008-04-03
I never attempted to write anything on the ext3 thru Windows since I remember an older version of ext2 IFS once screwed my partition in a way that it was lost. I had to format my whole hard drive to recover that area..

---

### Post by ukripper on 2008-04-03
> **regbsn said:**
> I was planning to install ext2IFS to allow access to A/V media on my Ubuntu partitions from WinXP. I plan on mostly using Linux, so most of my media files will reside there. That is why most of y hard drive space is allocated to ext3 / home partition.
Should I only read from  Linux partition and not write to it? 
Can I safely drag and drop to NTFS WinXP sda1 mounted drive fro Linux.
I have been able to copy pictures to Linux (for DE background).

I would still be careful on reading from ext3 from within windows, as ext3 uses journaling and would still cache some data (file in use) where  possible file Locking problem may occur.

---

### Post by vanadium on 2008-04-03
Reading certainly won't do any harm. Writing to an ext3 as an ext2, i.e. without using the journal, is OK. You are just using your ext3 system with the vulnerability of an ext2 system, and to be safe, you would need to regularly check the file system fully. In other words, you loose the advantage of journaling (no need for  regular lengthy checks to be safe), but you are just as safe as an ext2 system can be.

Be sure to immediately do a file system check (I am not sure if you can also do that in Windows) if the disk was not cleanly unmounted, for example because of a crash.

---

