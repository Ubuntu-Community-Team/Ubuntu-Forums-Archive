---
title: "Does anyone else have problems with stability under ext4?"
date: 2010-11-07
forum: The Cafe
---

### Post by Dustin2128 on 2010-11-07
I recently completed an otherwise wonderful maverick install process to find that the install was extremely unstable. I went back to see what could've possibly gone wrong, and the thing's perfectly stable on the disc; so I figured it's a filesystem problem. I reformatted the ext4 partition to ext3, and lo, stability issues gone! Its not an isolated problem either; I had the exact same one with slackware on my laptop. But it works just fine with ext3. Desktop's fine with ext4. Anyone else having these problems?

---

### Post by _outlawed_ on 2010-11-07
Working fine here

---

### Post by MooPi on 2010-11-07
Can you elaborate on the stability issues ? I haven't had a problem but am curious.

---

### Post by NCLI on 2010-11-07
Fine here too, on all of my machines, including my 5-disk 8 TB RAID5-array.

But I agree with MooPi, please elaborate.

---

### Post by Dustin2128 on 2010-11-07
> **MooPi said:**
> Can you elaborate on the stability issues ? I haven't had a problem but am curious.
After starting up, you could use it for maybe 5 minutes before everything just froze; total non-responsiveness. After I swapped to ext3 it was fine.

---

### Post by NightwishFan on 2010-11-07
I recently switched back to ext3, though my data partition has extents and everything so I am unsure if I am able to migrate back on it. I reinstalled my system partition on ext3 and it seems to work well. There is not much difference and some things are obviously slower however a few problems I had with dpkg and banshee are fixed (known problems).

If anyone knows a way I could migrate back that would be great, though I think once you have extents it is not possible.

---

### Post by NCLI on 2010-11-07
> **NightwishFan said:**
> I recently switched back to ext3, though my data partition has extents and everything so I am unsure if I am able to migrate back on it. I reinstalled my system partition on ext3 and it seems to work well. There is not much difference and some things are obviously slower however a few problems I had with dpkg and banshee are fixed (known problems).

If anyone knows a way I could migrate back that would be great, though I think once you have extents it is not possible.
Maybe you should try going forwards instead of backwards? I hear that it's very easy and safe to do an in-place upgrade to BTRFS.

---

### Post by NightwishFan on 2010-11-07
I like to use one solution, also, I do not want to risk my data on something as new as btrfs. Is the disk format even final?

---

### Post by juancarlospaco on 2010-11-07
badblocks, fsck, memtest

---

### Post by Dustin2128 on 2010-11-07
out of curiosity, what's the big deal about BTRFS? Why is everyone saying that its the future, is it really that much better than ext?

---

### Post by FuturePilot on 2010-11-07
> **Dustin2128 said:**
> out of curiosity, what's the big deal about BTRFS? Why is everyone saying that its the future, is it really that much better than ext?

Yes. It's basically a Linux equivalent to ZFS.

---

### Post by Dustin2128 on 2010-11-07
> **FuturePilot said:**
> Yes. It's basically a Linux equivalent to ZFS.
ZFS? Sorry, I don't look into file systems much.

---

### Post by FuturePilot on 2010-11-07
> **Dustin2128 said:**
> ZFS? Sorry, I don't look into file systems much.

It's a file system that was designed by Sun for Solaris
[http://en.wikipedia.org/wiki/ZFS]("http://en.wikipedia.org/wiki/ZFS")

---

### Post by Khakilang on 2010-11-07
No issue here on Lucid Lynx.

---

### Post by zer010 on 2010-11-07
I've had no issues with ext4 and I have been using it since 9.04. *thumbs up*:)

---

### Post by ssam on 2010-11-08
> **juancarlospaco said:**
> badblocks, fsck, memtest

+1

then suspect graphcis drivers

also have a look in /var/log/syslog and see if there are any messages when it crashes.

---

### Post by Spice Weasel on 2010-11-08
I used to have issues, but then I discovered XFS and JFS.

All problems gone. :)

---

### Post by NightwishFan on 2010-11-08
Do you think XFS would be better for my laptop than ext3?

---

### Post by Spice Weasel on 2010-11-08
The best way is to try it out and see what you think yourself.

---

### Post by TBABill on 2010-11-08
> **NightwishFan said:**
> I like to use one solution, also, I do not want to risk my data on something as new as btrfs. Is the disk format even final?
 
BTRFS is the default on PCLinuxOS, although you can choose others at install, and it works beautifully. I had it on 3 different machines for quite some time. The only reason I came back to Ubuntu was lack of 3D video support for the GPU integrated in my CPU (Intel Core i3-330m). If you are willing to experiment perhaps some questions about the file systems specifically to their experts would help you decide whether to try it or not? Great folks in their forums and most of the frequent users are incredibly knowledgeable.

---

### Post by NightwishFan on 2010-11-08
Thanks for the answer. I might look at XFS instead as I have no use for advanced features of btrfs.

---

