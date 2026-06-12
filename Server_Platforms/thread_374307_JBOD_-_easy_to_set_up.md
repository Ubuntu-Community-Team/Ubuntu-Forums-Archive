---
title: "JBOD - easy to set up?"
date: 2007-03-02
forum: Server Platforms
---

### Post by gurgle on 2007-03-02
I am looking to set up my Ubuntu server with JBOD - basically I just want to have 1 logical volume to share out to my clients. Is there a howto on this?

---

### Post by Enki on 2007-03-02
You could use [LVM]("http://www.suse.com/en/whitepapers/lvm/lvm1.html") to span any number of disks, which can be different sizes. It's available on the alternative install cd.

However: if you lose one disk, you lose all data, or at least the time you need to replace the disk and restore your backup. If your clients need high availabilty, invest in a raid controller and setup raid5.

---

### Post by gurgle on 2007-03-03
so if i use lvm and one disk goes down, i lose all the data on the jbod arrary? how much is a good raid5 controller?

---

### Post by Enki on 2007-03-05
As far as I know, yes, or you'd have a very hard time restoring it without a proper backup. Consumer-grade RAID controllers are about 130 EUR I believe. Professional stuff is a lot more. Google is your friend.

Note: RAID 5 is not a replacement for backups. If two disks fail before you replace the first and rebuild, you're still toast.

---

### Post by gurgle on 2007-03-05
thanks. I know RAID 5 isnt for backups, but it will just be media, so if 2 disks die then oh well. is it pretty easy to install ubuntu onto a hardware raid5 setup?

---

### Post by Enki on 2007-03-06
Should be. After you've built your array, I believe the OS will just see it as a single disk. Good luck, and let us know how it goes.

---

