---
title: "mdadm RIAD issue on 2 controllers"
date: 2007-06-20
forum: Server Platforms
---

### Post by ACA:Sleeper on 2007-06-20
I have a GB-K8NXP-SLI motherboard with 2 onboard sata controllers  (nForce4 and sil 3114).  I have a 2 disk RAID0 mdadm array on one controller and a 3 disk mdadm RAID5 array on the other. The OS is running from a single IDE drive.

The arrays do not always work after booting, it seems to me that the drives /dev/ ID changes because sometimes the controllers are initiated in a different order. Sometimes the drive on the nForce4 controller are /dev/sda & /dev/sdb with the sli controlled drives following /sdc /sdd /sde, and sometimes it's the sli that come first... killing the makup of my arrays.

I can do a simple 'mdadm --assemble --force /dev/md0 /dev/sda1 /dev/sdb1' to recover, but that is not a long term solution to what is ment to be a stable server.

Can anyone provide some direction on this? (I am pretty new at all this)

---

### Post by ACA:Sleeper on 2007-06-21
8 hour bump

---

### Post by rickyjones on 2007-06-21
I'm not sure if this is correct, but I could have sworn that I read about this. What you can do is use the actual device identifier, or UID I think, which will never change. It's a long string of #s I think and I'm not sure how to get it.

Could someone with more experience chime in? I'm only going on theory and "if I recall correctly" right now...

-Richard

---

### Post by ACA:Sleeper on 2007-06-21
I thought that might be an option, but as of now, I've only seen the UID for the ARRAY, not the drive, how do I find it for the drive?

Would the format be the same?    mdadm --assemble /dev/md0 then_the_uids

---

### Post by rickyjones on 2007-06-21
That is the idea, but again, I'm not sure on the specifics. Hopefully that can point both of us in the right direction though.

---

### Post by ACA:Sleeper on 2007-06-23
Bumpage...

Any Ideas guys? I couldn't find out if/how to get the uid for the physical drives, not that I know if that will help anyways

---

### Post by moshuptrail on 2007-06-24
Try typing sudo blkid

or sudo fdisk -lu

---

### Post by ACA:Sleeper on 2007-06-25
Neither command has the drive UID, only the array (/dev/md0) UID.

Still looking for a solution.... :(

---

