---
title: "Oh, Partitioning! You pain in the neck!"
date: 2009-09-24
forum: The Cafe
---

### Post by dragos240 on 2009-09-24
It takes so long even for a 500GB hd. I want to know if having a SSHD will make partitioning faster. That would rock! The only downside is you don't get to hear the beautiful sound of heads clicking!

---

### Post by Bachstelze on 2009-09-24
What are you doing that is taking so long?

---

### Post by dragos240 on 2009-09-24
Shrinking my /home partition and growing my / partition. EST. 6 hrs. :(

---

### Post by aldld on 2009-09-24
I was also thinking of shrinking /home and increasing the size of /. Using a 500gb hard drive.

Can it really take 6 hours? It didn't take 6 hours to create partitions when installing the OS. Is creating new partitions faster than resizing existing ones?

---

### Post by dragos240 on 2009-09-24
> **aldld said:**
> I was also thinking of shrinking /home and increasing the size of /. Using a 500gb hard drive.

Can it really take 6 hours? I didn't take 6 hours to create partitions when installing the OS. Is creating new partitions faster than resizing existing ones?

No idea, but shrinking the partition is going to be about 3 hrs. So growing the / partition may take a bit.

---

### Post by Bachstelze on 2009-09-24
The reason it's taking so long is that you're probably changing the start sector of one of the partitions. Therefore, the partition is not only shrunk, it is also *moved*. And it's the moving part that is taking so long, since te system has to move pretty much all the data in the partition.

---

### Post by magmon on 2009-09-24
> **dragos240 said:**
> No idea, but shrinking the partition is going to be about 3 hrs. So growing the / partition may take a bit.

Wow. My little laptop hard drive edits partitions very quickly (30ish minutes). I feel your pain though, it took me nearly 3 days to get my armada m300 running x.x

---

### Post by MasterNetra on 2009-09-25
> **aldld said:**
> I was also thinking of shrinking /home and increasing the size of /. Using a 500gb hard drive.

Can it really take 6 hours? It didn't take 6 hours to create partitions when installing the OS. Is creating new partitions faster than resizing existing ones?

Create new partitions are faster because it doesn't shift data around. When it resizes it has to shift data from one spot to another so that it stays within the designated partition...well if you create a new partition it will have to move the others that would come after to make room for the new designated area. Also resizing is risky because of it moving data. If something makes it screw up during it. It could accidently corrupt some of the data. Which is the reason why if you start a resizing don't cancel it.

---

### Post by aldld on 2009-09-25
> **MasterNetra said:**
> Create new partitions are faster because it doesn't shift data around. When it resizes it has to shift data from one spot to another so that it stays within the designated partition...well if you create a new partition it will have to move the others that would come after to make room for the new designated area.

That makes sense. Thanks! ;)

---

### Post by dragos240 on 2009-09-25
Good news! The partitioning was successful!

---

### Post by MasterNetra on 2009-09-25
> **dragos240 said:**
> Good news! The partitioning was successful!

Congratz!

---

### Post by ChrT on 2009-09-25
I moved 10 TB of partitions from ext2 to ZFS last weekend...suffice it to say I'm lucky offsite backups were kept.

---

### Post by dragos240 on 2009-09-25
A 10 TB hd? Must have!

---

### Post by ChrT on 2009-09-25
> **dragos240 said:**
> A 10 TB hd? Must have!

I said 10 TB of partitions. I don't remember over precisely how many physical drives that was, but none of them was above 1TB. And I didn't own any of them.

(In fact, I don't think there are any commercial HD's over 1TB being sold right now)

---

### Post by dragos240 on 2009-09-25
I thought I saw some 2 TB hds at my local electronics store.

---

