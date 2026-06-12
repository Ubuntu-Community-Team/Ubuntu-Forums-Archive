---
title: "Remotely restoring a server using an image, and the dd command"
date: 2010-04-18
forum: Server Platforms
---

### Post by jzimmerlin on 2010-04-18
Hi Everyone,
Ubuntu newbie here :)

I'm getting ready to deploy a Ubuntu server in a remote location.  I am deathly afraid of something going horribly wrong though, so what I'd like to do is be able to somehow image the system when it's working, and be able to restore that remotely via SSH if things go to hell.

My first thoughts were that I could partition the hard drive, and install two separate instances of Ubuntu.  One would be the server in it's working state, and the other one would be a separate instance of Ubuntu that I could boot into to restore an image (if that's possible).

So a few questions:
1.  If I had two separate instances of Ubuntu on two separate partitions, and I was currently booted into one of them, would it be possible to tell the Ubuntu server to reboot and boot into the other instance of Ubuntu on the other partition over SSH?  (SSH is the only form of access I will have to the server)
2.  Is there a better way to remotely restore a server than what I outlined above?
3.  Also, I've used the dd command to make backups before, but it copies an entire hard drive byte for byte.  Is there an argument I can tag on, or another command to use altogether that will only copy the bits that are being used?

Thank you in advance for your help!

---

### Post by utnubuuser on 2010-04-18
doesn't sync do incremental synchronizations?

---

### Post by jzimmerlin on 2010-04-18
Well I was really hoping to image the drive so that I could restore it later.  I don't think file syncing would work for that.

---

### Post by kewlrichie on 2010-04-18
Have u checked out clonezilla ? I usually keep a clonezilla partition image just incase each month then keep an up to date file backup so just incase I could restore to a new harddrive real quick to get things working again then restore data later

---

### Post by jflaker on 2010-04-18
I wouldn't do a partition...I would keep the image on a CD/DVD or other media.  Even a disconnected/un-powered drive installed in the server with color tagged cables so you can talk someone through connecting the drive.

If you have a partitioned drive and something goes south on the drive, you lose your "safe" partition too.

---

### Post by jzimmerlin on 2010-04-18
@kewlrichie - I've heard about Clonezilla, but hadn't actually checked it out.  Very cool that it can do backups that don't include un-used bytes.

@jflaker - good advice.

I'm starting to think this might be more difficult than I thought!

---

