---
title: "[SOLVED] Samba file size issues after installing 8.04"
date: 2008-06-24
forum: Server Platforms
---

### Post by 40.8utnubu on 2008-06-24
After 4 hours of googling and reading I give up..

I have a Ubunu server with my media on. My HTPC access this data using Samba. I just upgraded (with a clean install) from 6.10 to 8.04. The problem is that when I set up Samba again suddenly there seems to be a 4 GB file size limit when using the share. If a file is bigger than that the size is reported as smaller and I'm unable to use the file from any of the other computers in the network.

The file system on the disk is ext3 and the Samba version is Version 3.0.28a .

Any ideas?

---

### Post by windependence on 2008-06-24
Did you have several posts on this before? Or am I thinking of someone else?

-Tim

---

### Post by dca on 2008-06-24
I've only seen this on FAT32 file systems...
 
[http://osdir.com/ml/linux.colinux.general/2005-09/msg00038.html](http://osdir.com/ml/linux.colinux.general/2005-09/msg00038.html)
[http://ubuntuforums.org/archive/index.php/t-504166.html](http://ubuntuforums.org/archive/index.php/t-504166.html)
 
Here suggests using NFS versus Samba or there abouts...
 
[http://forums.macrumors.com/showthread.php?t=465712](http://forums.macrumors.com/showthread.php?t=465712)

---

### Post by 40.8utnubu on 2008-06-24
> **windependence said:**
> Did you have several posts on this before? Or am I thinking of someone else?

My first post ever regarding Linux. I'm one of them finding my answers using search engines and other ppl's problems. :)

..though I wish I found the posts you're thinking of.. Of course there are many posts regarding the 2 GB limit and file systems limits and when mounting shares on Ubuntu..

---

### Post by 40.8utnubu on 2008-06-24
> **dca said:**
> I've only seen this on FAT32 file systems...
Yes, I know.. I had that issue a couple of years ago when I first tried a setup like that.

Thanks for the suggestions..just doesn't seem to be what I'm looking for.. Can't understand what can be so different from yesterday when I ran on 6.10. It's like *"Didn't I use samba? Have I forgot about some problems I had the last time I set it up? Why didn't I keep the old data as reference?"* .. :|

---

### Post by cdenley on 2008-06-24
Seems to work fine for me.
samba 3.0.28a-1ubuntu4.2
I created a 4.2 GB file
```

dd if=/dev/zero of=test.dat bs=1024 count=4404020

```
copied it with a Windows XP client. I had a 4.2 GB copy. What kind of clients have you tried? Is the file the correct size locally, but the incorrect size when accessed remotely through samba?

---

### Post by 40.8utnubu on 2008-06-24
> **cdenley said:**
> Seems to work fine for me.
samba 3.0.28a-1ubuntu4.2
I created a 4.2 GB file
```

dd if=/dev/zero of=test.dat bs=1024 count=4404020

```
copied it with a Windows XP client. I had a 4.2 GB copy. What kind of clients have you tried? Is the file the correct size locally, but the incorrect size when accessed remotely through samba?

I did as you did, and the sizes (in bytes) are:
[LIST]
[*]According to ls:     4,509,716,480
[*]Seen from Vista:       214,749,184
[*]After copied to Vista: 216,006,656
[/LIST]

The only 'client' I have tried is Explorer in both Vista and XP. And I know for a fact that this is not how it used to be.

As far as I can see after having looked at files ranging from 0 bytes to past 8 GB is that the size I get is modulus 4 GB of the real size.

---

### Post by windependence on 2008-06-25
> **40.8utnubu said:**
> My first post ever regarding Linux. I'm one of them finding my answers using search engines and other ppl's problems. :)

..though I wish I found the posts you're thinking of.. Of course there are many posts regarding the 2 GB limit and file systems limits and when mounting shares on Ubuntu..

Seems like we had this question a few times in the last few weeks. I'll see if I can locate the threads.

-Tim

---

### Post by 40.8utnubu on 2008-06-25
Seems like there's a problem with the partition table of the disk in question. I'll get back to you when I've checked it out.

---

### Post by 40.8utnubu on 2008-06-25
OMG...I've used countless hours on this one.. and I finally found out what was wrong.. there was indeed something wrong with the partition table of the disk, but that wasn't the reason! The reason was that when I set up samba this time I used this one:
```
protocol = LANMAN2
```

The moment I remove it the filesizes are correct.. :( I haven't found the docs that describes LANMAN2, but then again I don't care that much any longer.. At least I hope that someone else can have use of this thread.. :)

---

