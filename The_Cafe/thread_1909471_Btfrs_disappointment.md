---
title: "Btfrs disappointment"
date: 2012-01-15
forum: The Cafe
---

### Post by BC59 on 2012-01-15
Yesterday I spent the day to reformat my Sony Vaio laptop and freshly install the 11.10 (I think it's the tenth time since it's beta release).
Last year I tested Btfrs the "new" Linux file system and it was very fast but extremely buggy.
So yesterday I decided to format my drive to Btfrs. Apart from the sense that everything was slow, the procedure was going ....well, until I started to update the system. After 3 hours of waiting to install the new packages, I gave up and reformatted the drive to ext4.
Finally Btfrs goes from bad to worst.
Any opinions of people tried to do the same?

---

### Post by nmaster on 2012-01-15
not sure why you sound so surpised by the bugs. according to wikipedia, a stable version has "yet to be released"
[http://en.wikipedia.org/wiki/Btrfs](http://en.wikipedia.org/wiki/Btrfs)

---

### Post by BC59 on 2012-01-15
> **nmaster said:**
> not sure why you sound so surpised by the bugs. according to wikipedia, a stable version has "yet to be released"
[http://en.wikipedia.org/wiki/Btrfs](http://en.wikipedia.org/wiki/Btrfs)

I'm surprised for 2 things. First as I said, last year Btrfs was faster than ext4 and now is very much slower and secondly I read that kernel 3 augmented it's support to this new file system
[http://kernelnewbies.org/Linux_3.0](http://kernelnewbies.org/Linux_3.0)
I don't see any improvement comparing to other kernels.

---

### Post by philinux on 2012-01-15
From what I've read I'd wait till 12.10.

---

### Post by BC59 on 2012-01-15
> **philinux said:**
> From what I've read I'd wait till 12.10.

I thought so. Looks like the progress is very slow and the results are not very promising. It was scheduled to be ready for the year 2010 and it's postponed now to the end of 2012.

---

### Post by sffvba[e0rt on 2012-01-15
*Thread moved to **The Community Cafe**.*

... seeing as it isn't really a testimonial or experience with Ubuntu...


404

---

### Post by FuturePilot on 2012-01-15
Btrfs isn't even finished yet....

---

### Post by Paqman on 2012-01-15
If you don't want to see bugs and regressions, don't install experimental stuff. The whole point of allowing you to install btrfs this early is precisely so that you do find the bugs.

---

### Post by BC59 on 2012-01-15
But in this case you don't deal with a bug! It's not a usual program, it's a file system. It's working or not and I have the feeling that is not working.
And don't forget this:
> In 2008, the principal developer of the ext3 and ext4 file systems, Theodore Ts'o, stated that although ext4 has improved features, it is not a major advance, it uses old technology, and is a stop-gap; Ts'o believes that Btrfs is the better direction because "it offers improvements in scalability, reliability, and ease of management".
So ext4 is kind of beta as well. But we use it and we expect it should be working.

---

### Post by Double.J on 2012-01-15
I did a default install of SUSE 12.1 with BTRFS. Not really had any desktop user affecting problems yet on my desktop, but the netbook is very slow to load programs such as firefox - around 12 Sec. Of course as it's disk read there's no performance issue once they're up and running - it's just getting them there. I don't have this on the desktop though - but that is a much faster drive?

Just my tuppence!

---

### Post by MadCow108 on 2012-01-15
> **BC59 said:**
> But in this case you don't deal with a bug! It's not a usual program, it's a file system. It's working or not and I have the feeling that is not working.


its not working due to bugs.
> 
So ext4 is kind of beta as well. But we use it and we expect it should be working.

nothing in that text says its beta, in contrary it says its stable due to it only being improvement to old proven technology.

if you want a next generation filesystem thats out of its experimental phase have a look at zfs.

---

### Post by Khakilang on 2012-01-15
I always use trial and tested filesystem. I like ext3 but end up with ext4. Prefer not to waste time re format and re install all those software.

---

### Post by Paqman on 2012-01-16
> **BC59 said:**
> But in this case you don't deal with a bug! It's not a usual program, it's a file system.

Filesystems are software just like anything else. Btrfs clearly still has some major bugs.

> 
So ext4 is kind of beta as well. But we use it and we expect it should be working.

Ext4 is stable, not beta. What Ts'o meant was that (like ext3 before it) it was merely an iterative upgrade of the previous version, and not a major new filesytem with lots of lovely new technology built it. All the funky new stuff would be going into btrfs (which is probably why it's taking a while to get right).

---

### Post by BrokenKingpin on 2012-01-17
I don't have much interest in it at this point... Ext4 works and performs just fine for me.

---

### Post by FuturePilot on 2012-01-17
> **BC59 said:**
> 
So ext4 is kind of beta as well. But we use it and we expect it should be working.

Ext4 is not beta. It's been considered stable for a while now.

---

