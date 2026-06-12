---
title: "Anyone installed Ubuntu Server 20.x on a Dell T640 successfully?"
date: 2020-05-05
forum: Server Platforms
---

### Post by cwxes652 on 2020-05-05
I just did.  But its not recognizing the RAID 1 that is configured.  Wondering if I should downgrade to 18 LTS since its certified?

Joe

---

### Post by oldfred on 2020-05-06
Moved to server sub-forum where those who know servers may be able to help.
Post this:
sudo parted -l

---

### Post by darkod on 2020-05-08
Do you have the option to use the disks in AHCI (plain disks, directly)?

If you do, I would consider that option as better and use mdadm raid1 instead to depend on server's HW raid.

That being said, if 18.04 recognizes the raid drivers I would expect 20.04 to do too.

---

### Post by LHammonds on 2020-05-08
Did you install 20.04 using the default "live" image or the [legacy]("http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04/release/") image?

LHammonds

---

