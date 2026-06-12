---
title: "Lost my RAID 5 array following esx disc cloning can anyone help?"
date: 2015-01-13
forum: Virtualisation
---

### Post by cheechy on 2015-01-13
Ok feeling ill at this right now (I'm not kidding!) as I suspect I've lost a great deal of data. Feel a bit of a chump for not backing up before it but my mindset was focused on cloning the boot disc to avoid issues!

Anyhow to build the picture I wanted to move my ESX4.1 boot disc to another disc using clonezilla. After a couple of hours the clone was complete so I moved my boot disc out and put the new one in. Everything appeared to come up ok but then I discovered that the only VM  I had configured came up as unrecognised. I did a couple of disc scans to see if anything could be picked up as datastore 1 (the boot disc) wasn't coming up as a datastore at all. I decided to abort and put my original boot disc back in and reinstate.

Again everything came back up and the VM was there so I started it.

The pain starts with then realising my RAID 5 array didn't come back with it - I suspect the cloned vm has altered the boot blocks on the 4 raid discs!! I didn't even think about this.

Anyhow Ubuntu 14.04 LTS can see the discs ok but on checking for superblocks none of the discs has one - they are gone :-( so mdadm wont entertain the idea of reassembling.

Can anyone provide hope that I can get my data back? Last backup I did was over a year ago (I know).

Thanks

---

