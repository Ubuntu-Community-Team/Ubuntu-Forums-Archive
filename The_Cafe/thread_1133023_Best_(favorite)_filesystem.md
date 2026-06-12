---
title: "Best (favorite) filesystem?"
date: 2009-04-22
forum: The Cafe
---

### Post by inxygnuu on 2009-04-22
I have been looking at some different filesystems lately, and decided to ask the Ubuntu Forums "what is the best (/your favorite) filesystem? Please explain why it is too, please.

Thanks,
3v4n

---

### Post by SuperSonic4 on 2009-04-22
ext3 at the moment although ext4 is a strong contender and will overtake ext3 when it is more mature

---

### Post by pimz on 2009-04-22
For the best check out the many benchmark tests (google), the rest is just a matter of opinion

---

### Post by will1911a1 on 2009-04-22
Ext3

---

### Post by SpriteSODA on 2009-04-22
[http://up53.siz.co.il/up2/qyztw1yyu3mz.png](http://up53.siz.co.il/up2/qyztw1yyu3mz.png)

poll fail :P

---

### Post by Eisenwinter on 2009-04-22
Ext2|3|4, with Ext4 being the most favourite.

I have an ext3 /boot partition, and ext4 / and /home.

---

### Post by RiceMonster on 2009-04-22
Currently using ext3. I plan on trying out ext4 in the near future

---

### Post by steeleyuk on 2009-04-22
> **RiceMonster said:**
> Currently using ext3. I plan on trying out ext4 in the near future


Same, pretty much.

For 9.04 I'll most likely put ext4 on my root drive and the data drives will stay as ext3 until 9.10.

---

### Post by hatten on 2009-04-22
what about jfs and xfs?

---

### Post by Simian Man on 2009-04-22
> **SpriteSODA said:**
> [http://up53.siz.co.il/up2/qyztw1yyu3mz.png](http://up53.siz.co.il/up2/qyztw1yyu3mz.png)

poll fail :P

Umm, how is that a poll fail?

---

### Post by steeleyuk on 2009-04-22
> **Simian Man said:**
> Umm, how is that a poll fail?

100% and 50%... its the way the forum displays the percentages that makes it look odd.

---

### Post by Simian Man on 2009-04-22
> **steeleyuk said:**
> 100% and 50%... its the way the forum displays the percentages that makes it look odd.

Oh I see.  If it's multiple choice, they could all theoretically be at 100% though :).

---

### Post by piousp on 2009-04-22
JFS is really good, and currently most of mount options are formated with JFS. The others are in EXT3 for the moment, but i expect to "upgrade" them to ext4.
XFS looks good too.

But, BTRFS will just rock :P

Also, i'm interested in seeing this 3 in action as they do look good enough:

SQUASHFS
NILFS
Tux3FS

---

### Post by Tibuda on 2009-04-22
I have only used ext3 (because is the ubuntu default fs), so I can't say if it is the best.

---

### Post by gnomeuser on 2009-04-22
Currently I am using ext4, it performs decently and it's very stable. The time I have spend with btrfs as well as looking at the design makes me vote for it as my second choice. Heavy duty testing of btrfs should be posible in the Karmic Koala timeframe and I know one of the Ubuntu Server developers has expressed interest in getting that going.. so hopefully.

Already today for a filesystem of a totally new design and being fairly young it is quite stable and featureful. I especially enjoy it's builtin compression which is a nice touch that I enjoyed in the zfs design as well.

---

### Post by kk0sse54 on 2009-04-22
HAMMER has been holding my interest for quite some time but for linux I use ext4

---

### Post by gnomeuser on 2009-04-22
Linux Magazine tests and benchmarks [btrfs](http://www.linux-mag.com/id/7308/).

---

### Post by cb951303 on 2009-04-22
BTRFS will probably become the standard among linux distros.
There is also this with similar design goals but not yet complete: [http://www.tux3.org/](http://www.tux3.org/)

---

### Post by oomingmak on 2009-04-23
From the choices given I'd choose NTFS (I hate EXT)

But BTRFS is the one that I am really excited about.

---

### Post by adamlau on 2009-04-23
Other = XFS.

---

### Post by Firestem4 on 2009-04-23
HAMMER is probably my favorite FS. But I don't use BSD (yet, anyways. specifically DragonFly BSD, obviously). But I use Linux and Windows primarily. ext3/4 are the best. I can't stand NTFS anymore.

---

### Post by Twitch6000 on 2009-04-23
ext3 is my favorite due to it being so stable.

I will use ext4 when it gets a bit more stable... and less buggy...

I have tried others like ntfs,fat,and jfs.

ext3 is about as stable as it gets :).

---

### Post by caveman59330 on 2009-04-23
well for Ubuntu i like to use Reiser FS with Journaling but for Mandriva or anything else I usually go with Ext3 but I cant wait to try Ext4 and some others to see how the do as well.

---

### Post by gnomeuser on 2009-04-23
> **cb951303 said:**
> BTRFS will probably become the standard among linux distros.
There is also this with similar design goals but not yet complete: [http://www.tux3.org/](http://www.tux3.org/)

TUX3 is an interesting idea, the only problem it really has is that there is no buy in from any of the big distributions. You don't have them jumping up and down to add support as well as work.

T'so in his recent talk on ext4 told the story of why jfs while technically superior at the time it arrived in Linux to our current solutions utterly failed to gain ground. It was solely down to the distributors not buying in, and when no engineers sit down and get to know the code it is hard to get supported. You need people to fix the code when it breaks within your own ranks to do that kind of commitment.

This is one thing btrfs has been very good at doing, all the major distros basically have people doing work or interested in supporting it.

---

### Post by medic2000 on 2009-04-23
Reiserfs. Really fast and stable fs. Recommended.

---

### Post by anaconda on 2009-04-23
jfs

It is ligter and faster than ext3. Noticeable on slower machines.

ext2-3-4 have the good? feature that windows can read/write to those.

---

