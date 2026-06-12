---
title: "what stops linux from writing to NTFS"
date: 2005-10-12
forum: The Cafe
---

### Post by phrozen on 2005-10-12
one of the first thing i learnt when i started playing around with linux was that you couldnt write to NTFS(and because when i started, and i still am, i only used live CDs)so as you can imagaine i couldt save anything on my harddrives. i was wondering about why linux can read but not write to NTFS and if anyone could fill me in on the technical details of the whole Linux NTFS thing it would be awesum

---

### Post by nocturn on 2005-10-12
[QUOTE=phrozen]one of the first thing i learnt when i started playing around with linux was that you couldnt write to NTFS(and because when i started, and i still am, i only used live CDs)so as you can imagaine i couldt save anything on my harddrives. i was wondering about why linux can read but not write to NTFS and if anyone could fill me in on the technical details of the whole Linux NTFS thing it would be awesum[/QUOTE]

NTFS write support does exist, but is disabled in most kernels because it is dangerous.   NTFS is an MS filesystems, it has to be reverse engineered to work on Linux.  Now, this works, but not flawless.  Any bug in the writing code could cause loss of files or even corrupt the partition, so it is not recommended.

---

### Post by drogoh on 2005-10-12
[deleted because an identical answer was given while I was typing this out]

---

### Post by GeneralZod on 2005-10-12
[QUOTE=nocturn]NTFS write support does exist, but is disabled in most kernels because it is dangerous.   NTFS is an MS filesystems, it has to be reverse engineered to work on Linux.  Now, this works, but not flawless.  Any bug in the writing code could cause loss of files or even corrupt the partition, so it is not recommended.[/QUOTE]

In fact, writing support is so poor as to not be worth using - one is limited to overwriting the contents of an already existing file, and I'm not sure even if that file is allowed to be non-contiguous.

There are hacks to write to NTFS, but I can't recommend them in good conscience.  If you're truly willing to risk loss of data, google for "captive ntfs".  Note that while I haven't personally heard of any data loss resulting from the use of this software (which actually commandeers Microsoft's own NTFS driver and makes it work under Linux), you should approach the use of this as if it will definitely destroy stuff - better safe than sorry, after all!

The real question, of course, is why, for all their boasting of "interoperability" with other systems, Windows is incapable of writing to ext2/3, which are not only well-documented but which have freely available and hugely well-tested reference implementations?

Edit:

Actually, I just remembered that there is a third-party ext2 reader/writer avaailble for Windows, but the name of the project escapes me for the time being :)

---

### Post by asimon on 2005-10-12
And other issue is that Microsoft has NTFS potentially covered by some patents. That is the reason why for example Red Hat doesn't even ship read support for NTFS. (I don't know if the patent issue is true, but at least you can read on redhat mailing lists and fedora faqs that Red Hat has patent concerns regarding NTFS) And it's also a reason which prevents Red Hat developers to improve the NTFS write support of Linux. I fancy that reverse engineering NTFS is not very exciting and something you would want to do in you precious spare time, thus probably a job you need to pay someone to get it done. And this is problematic when patent concerns come into play.

---

### Post by drogoh on 2005-10-12
[QUOTE=GeneralZod]
Actually, I just remembered that there is a third-party ext2 reader/writer avaailble for Windows, but the name of the project escapes me for the time being :)[/QUOTE]

Explore2fs -- [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

It's just as bad as Linux NTFS write support, or at least it was when I tried it (2001 or so).

---

### Post by Lovechild on 2005-10-12
one very very simple answer - the lack on Microsoft's part of opening the specification and the patents. 

There's no good technical reasons why we couldn't do it, likewise why Windows couldn't support ext3/etc. out of the box, except they don't feel like playing ball with a competitor - which on the whole is understandable.

---

### Post by jnoreiko on 2005-10-12
[QUOTE=drogoh]Explore2fs -- [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

It's just as bad as Linux NTFS write support, or at least it was when I tried it (2001 or so).[/QUOTE]

I managed to get excellent ext2/3 support on Windows2000.
My system's died since then so I can't tell you what I used for definite, but it wasn't Explore2fs, it was a driver that made linux partitions show up just like normal drives in My Computer. easy to install, easy to use, didn't have any problems at all with it.

It was possibly EXT2IFS [http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm)

EDIT: no it wasn't. I could write files as well as read.

I think it's this one: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by super on 2005-10-12
a question that is a little of topic:

what makes ntfs better than fat32? (which works perfectly with linux)

---

### Post by az on 2005-10-12
[QUOTE=super]a question that is a little of topic:

what makes ntfs better than fat32? (which works perfectly with linux)[/QUOTE]

I think NTFS is a journaled filesystem and vfat is just a bunch of free space with an index.

There are some really detailed articles on the differences between filesystems, but I am not that much of a geek to read they all the way through.  I am not smart enough, either.




How many days do you think it would take for a GPL driver for the kernel to read and write to NTFS to be made once the spaces are released?  Would it be a matter of hours, do you think?

---

### Post by poofyhairguy on 2005-10-12
[QUOTE=super]a question that is a little of topic:

what makes ntfs better than fat32? (which works perfectly with linux)[/QUOTE]


Even after years of trying, Microsoft cannot protect FAT with patents. Thats why they are trying to phase it out!

---

### Post by Takis on 2005-10-12
[QUOTE=super]a question that is a little of topic:

what makes ntfs better than fat32? (which works perfectly with linux)[/QUOTE]
There are a couple of things. Like azz said, it's journalled which helps with stability. It also supports file permissions, which FAT32 never did. It's actually a very good filing system, save the fact that it's a closed source. The major advantage I would say NTFS has over EXT2/3 is support for Access Control Lists, which allows for complex management of group permissions. The drawback to ACLs is the extra disk space and processing time needed to save permissions and calculate them when loading the files, but IMHO this is a relatively small drawback considering the gains. This is debatable but irrelevant to the original post.

There is a very cool plugin for Windows Explorer called ext2fsd ([http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)) which allows you to mount your root partition as a Windows logical drive (i.e. F:, G:, etc), but in my experience this program is still relatively unstable and should be used with extreme caution.

Using the common FAT32 partition is currently the most stable method of sharing files between these OSs.

[QUOTE=poofyhairguy]Even after years of trying, Microsoft cannot protect FAT with patents. Thats why they are trying to phase it out![/QUOTE]
That and the fact that it's quite possibly the worst file system ever. No permissions? What's the point?

---

### Post by MikeRussell on 2005-10-12
How would one go about installing ubuntu with shared disk space?  Any help would be apprecitaed

Mike

---

### Post by Jeff Hunter on 2005-10-12
[QUOTE=Takis]That and the fact that it's quite possibly the worst file system ever. No permissions? What's the point?[/QUOTE]


Well, I will say this from the perspective of a geek too lazy to make the switch...I still use FAT 32 on my XP partition, in large part due to the fact that I have no real need for NTFS permissions, don't have extra storage capacity to back up in case everything goes nuts when I try it, nor the desire to rebuild if it crashes.  I ahve not had to rebuild in too long, and I am one who neither likes to, nor believes it should ever be nessisary to rebuild.

Also because I still keep a Win 98 partition on my computer and want it to be compatable with XP.

How many here Tripple boot?

Oh well, I was even thinking of using the tiny bit of free space to install a second Linux partition and try out my third distro.  Was thinking about trying out Gentoo.  Quad boot, anyone?

Sorry, that got a tad off subject.

Anywho, my experiance has been that NTFS is indeed a better FS than FAT, but I could not say much about why other than what has already been listed.  I would say it is probably about as good as ext3 or ReiserFS (which is what I use for Linux), but that might be giving it more kudos than it is worth.  I really don't have the expertiese to say.

My two cents (1.83 cents after taxes taken out)

Jeff Hutner

"I am NOT a Nerd!  I am a GEEK!  Get it right!"

---

### Post by agntsmyth on 2007-10-21
> **super said:**
> a question that is a little of topic:

what makes ntfs better than fat32? (which works perfectly with linux)

i could be wrong but isnt fat32 limited to smaller file sizes, so large .iso files wont work in it. correct me if im wrong. I also believe that ntfs is suposed to use smaller blocks on the physical drive or something so that drive space is used more efficiently (*note- the previous explanation is a generalization, of a very likely misunderstood generalization, that i heard quite some time ago; do not go telling people that and then get mad at me when you are completely and totally wrong, especially if i am wrong.)

---

### Post by jdong on 2007-10-21
NTFS is a very advanced filesystem compared to FAT32 and is designed from the ground-up to be robust and reliable with data. 

This is an old revived thread, and shows how Linux makes progress over time. With Gutsy, NTFS volumes are indeed read-write by default.

---

### Post by saulgoode on 2007-10-21
> **MikeRussell said:**
> How would one go about installing ubuntu with shared disk space?  Any help would be apprecitaed

I would recommend having an additional partition, formatted as VFAT. This partition would be accessible from Windows (as a D:\ drive, for example) and also could be mounted from Linux.

---

### Post by jdong on 2007-10-21
> **saulgoode said:**
> I would recommend having an additional partition, formatted as VFAT. This partition would be accessible from Windows (as a D:\ drive, for example) and also could be mounted from Linux.

If you are sharing with Windows, at this point I'd actually recommend using NTFS with ntfs-3g to do it. FAT32 is a very old filesystem that's simply unreliable and limited for modern purposes.

---

### Post by gn2 on 2007-10-21
Fat32 file size limit is 4gb I think.

Fat32 also prone to serious defragmentation.

I've used ntfs-3g for a while without any problems at all.

---

