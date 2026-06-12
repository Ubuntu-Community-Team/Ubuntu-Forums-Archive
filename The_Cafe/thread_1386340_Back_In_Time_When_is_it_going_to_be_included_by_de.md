---
title: "Back In Time: When is it going to be included by default?"
date: 2010-01-20
forum: The Cafe
---

### Post by k64 on 2010-01-20
Back In Time is an open source app for Linux that works in much the same as Mac OS X's Time Machine, creating automated backups of your filesystem. When is it going to be included in Ubuntu by default?

You can find out more in a screenshot I have attached.

---

### Post by MaxIBoy on 2010-01-20
It will included by default the same day /home is symlinked to /dev/null by default.

EDIT: Seriously though, what does this have that Btrfs or Nilfs2 won't bring?

---

### Post by juancarlospaco on 2010-01-20
***And Gnome Journal the Time Machine of activities...***

---

### Post by k64 on 2010-01-20
> **MaxIBoy said:**
> It will included by default the same day /home is symlinked to /dev/null by default.

EDIT: Seriously though, what does this have that Btrfs or Nilfs2 won't bring?

***More like /dev/null mounted in /home.***

---

### Post by hessiess on 2010-01-20
> **MaxIBoy said:**
> Seriously though, what does this have that Btrfs or Nilfs2 won't bring?

Whenever they are actually finished, they will be good but as of now solutions like Back In Time actually exist and are stable. Any kind of revision control is EXTREMELY useful, once you have used a VCS of any sort, you will wonder how you managed without it.

Personally I store everything in a SVN repository because it allows for easy sync, and it works over plain HTTPS. But simpler solutions like Back in time would be perfectly adequate if you don't need synchronisation as well.

---

### Post by MaxIBoy on 2010-01-20
Now, a FUSE abstracted on top of Git, that I could go for. And I was thinking about writing one, until Phoronix started to mention Btrfs and Nilfs2. Actually, using Btrfs/Nilfs2 on-disk formats, but exposing their snapshots as a read-only Git repository, would be completely awesome and might be something I would try to create.



Anyway, the point I was trying to make is that by the time Ubuntu 10.10 is begun, Btrfs at least will probably be "ready for primetime," and I imagine Nilfs2 would be as well (Doesn't Nilfs2 even have a finalized on-disk format?) And 10.10 is the soonest possible release where a new program (such as Back in Time) could be included. So it's kind of moot.

---

### Post by beetleman64 on 2010-01-20
I can see why you'd want it. Having seen Time Machine in action I have to admit that it's a fantastically useful piece of software. I would like to see something like it on Ubuntu.

---

### Post by juancarlospaco on 2010-01-20
Theres etckeeper on Ubuntu server, kinda time machine but server oriented.

---

### Post by Warpnow on 2010-01-20
Couldn't you just use git on the root of your drive?

Never tried it.

---

### Post by sudoer541 on 2010-01-20
How is back in time?

if my pc doesint boot will back in time fix it?

---

### Post by k64 on 2010-01-20
[http://www.ubuntugeek.com/tag/install-back-in-time-ubuntu](http://www.ubuntugeek.com/tag/install-back-in-time-ubuntu)

The above link is to instructions on how to install Back In Time.

---

### Post by juancarlospaco on 2010-01-20
> **k64 said:**
> 
instructions on how to install Back In Time.

instructions?, 
you only need to[ click here for GTK]("apt:/backintime-gnome") or[ here for QTs]("apt:/backintime-kde")
:)

---

### Post by MaxIBoy on 2010-01-20
@sudoer, depends on what you define as "not booting." The Ubuntu-Geek website describes it as a GUI frontend for rsync, diff, and cp. So if you know the command line and you at least can get a working text-only mode, you can run the rsync, diff, and cp commands manually. An easier choice is to boot from a live CD, [chroot]("http://en.wikipedia.org/wiki/Chroot") into your broken installation, and then use the system recovery technique of your choice (Back in Time being one of your options if you had installed it and run backups with it before the system broke.)

> **Warpnow said:**
> Couldn't you just use git on the root of your drive?

Never tried it.I can only see that working if you dual-boot with an auxiliary OS and reboot every once and a while to run a git commit. Keeping a home directory under revision control is relatively easy. The root directory is something else entirely. That is what will be so great about Btrfs and Nilfs2: you can create snapshots of them while they are still mounted and being read/written to, even for the root directory. You can later mount those snapshots as separate, read-only filesystems.

---

### Post by k64 on 2010-01-20
> **juancarlospaco said:**
> instructions?, 
you only need to[ click here for GTK]("apt:/backintime-gnome") or[ here for QTs]("apt:/backintime-kde")
:)

I already posted a link to them, which you failed to look at.

---

