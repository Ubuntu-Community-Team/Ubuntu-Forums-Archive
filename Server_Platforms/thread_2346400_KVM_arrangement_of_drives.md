---
title: "KVM arrangement of drives"
date: 2016-12-14
forum: Server Platforms
---

### Post by matthewmcwest on 2016-12-14
I have a server acting as a KVM host.  It does not perform any other tasks.  There is a HDD and an SSD of equal size.  When I first set it up I put the OS on the HDD and I use the SSD to store the images of guest VM's.  My thinking was that once the OS was loaded onto the RAM, there would be a limited amount of read/writes to the HDD.  Furthermore, I though that in the event of a hardware failure (anything but the SSD), I could mount the SSD on another server with ease.

After talking to someone, I realize that this may have not been the best arrangement.  I'm wondering if it is worth my time rebuilding the entire server so that most (OS and priority guest VM's) data is on the SSD.

Also, is there any tips on saving myself time and effort in doing this.  Thank you

---

### Post by TheFu on 2016-12-14
If the files "appear" to be where they need to be, then the OS doesn't care what the actual storage is.  Just update the fstab with the correct devices/UUIDs and locations to be mounted if you swap things around.  If you are using LVM (and you should), then things are a little more complicated, but still doable.

No need to "rebuild the entire server." If you have things setup, at a minimum, those settings can easily be retained. That with the data and list of all the packages installed will get you pretty far back to the same point.  A tool like [http://manpages.ubuntu.com/manpages/xenial/man8/apt-mark.8.html](http://manpages.ubuntu.com/manpages/xenial/man8/apt-mark.8.html) will let you capture the automatic and manually installed pkgs which can be used later to restore.  Backing up system/program settings and these lists of pkgs is a tiny amount of data to be stored.

But ... we always need backups.  This is a good chance to test the recovery method you've planned already for all this important data.  If you don't have solid, versioned, backups, this is the perfect time to get those in place.
There are few ways to save on backup storage, if you are interested.  The storage backend can really make this not-so-hard too.

As for whether having SSD for OS or VMs is faster. I don't know.  You'd have to look at the workload and monitor the disk I/O for a period to make an educated guess.  I don't trust SSDs at this point, but know lots of companies are deploying servers ONLY with SSDs in a RAID10 config for their VM hosts. They have lost a few SSDs due to failures, BTW.

---

### Post by matthewmcwest on 2016-12-14
Thank you. I'm interested in the idea of monitoring the disk I/O.  I would need some pointers on how to do this.  Rebuilding from backups would not take long, but would need to be done on a weekend.  It sounds like the choice for the setup is NOT a no-brainer.

---

### Post by TheFu on 2016-12-15
> **matthewmcwest said:**
> Thank you. I'm interested in the idea of monitoring the disk I/O.  I would need some pointers on how to do this.  Rebuilding from backups would not take long, but would need to be done on a weekend.  It sounds like the choice for the setup is NOT a no-brainer.

If it is a server, use the normal system monitoring tools (which should be there anyways) to monitor disk, network, cpu, ram, and 50 other things about a running system. Best to capture stats for at least a week before making decisions.  Cacti, sysusage, munin are some possibilities, but there are 20+ others.

Any work like this demands backups BEFORE starting. It is very easy for anyone to make a small mistake and loose everything.

---

