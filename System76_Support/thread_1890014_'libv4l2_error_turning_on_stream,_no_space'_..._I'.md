---
title: "'libv4l2: error turning on stream, no space' ... I've got plenty!"
date: 2011-12-02
forum: System76 Support
---

### Post by wakajawaqa on 2011-12-02
Hi I just put a new 120 Gb SSD in my gazelle, everything was working beautifully for a couple weeks, now I'm having some weird issues.

Right clicking in Nautilus and going to properties shows some very odd things.

According to Nautilus, I have only 10.5 MB free in /dev and I have 140.7 TB total contents in /proc. Sadly, I can't afford a 140 TB SSD just now...

Does anybody have any idea what's going on here? It's not even causing any real problems, at the moment. I was having trouble running 'cheese,' because of an error saying ```
unable to open '/dev/video0': No space left on device
```I originally titled this thread to that effect, but it stopped happening after updating. I tried changing the title, but it doesn't appear to have taken effect yet.... sorry to mislead anyone

Anyway, installation of the SSD was pretty easy, took out two screws, replaced the HDD, screwed it back in, installed the OS, so I don't think I could have botched that.

This is /etc/fstab

```
#
# /etc/fstab: static file system information
#
# <file system> <dir>   <type>  <options>       <dump>  <pass>
tmpfs           /tmp    tmpfs   nodev,nosuid    0       0
/dev/sda5 / ext4 defaults,noatime,discard 0 1
/dev/sda6 /var ext4 defaults,noatime,discard 0 1
/dev/sda7 swap swap defaults,noatime,discard 0 0
/dev/sda8 /home ext4 defaults,noatime,discard 0 1
```Any input is appreciated. Should I just ignore it?

Thanks in advance

---

### Post by isantop on 2011-12-02
How big are those partitions? If one of them is particularly small, it could cause that.

By the way, any particular reason you don't go with a standard, single-partition set up? It's definitely less headaches down the road.

---

### Post by wakajawaqa on 2011-12-02
Hi, thanks a lot for the reply.

My partitions are 15 GB for root (its presently 45% full, according to system monitor. A big chunk of that is Doom 3 files) 2 GB for /var (48% full) 6 GB for SWAP. I'm sure that is overkill, but I've got 6 GB RAM and, from what I've read, it seems I should have at the same amount for SWAP to hibernate.... maybe that's bunk, everywhere you look someone says something different. I alloted the rest for /home.

I always do a seperate /home, It's really just force of habit now, but when I was first learning about Linux, I was advised to do so because it would make it easier to multi-boot and do backups and I do distro-hop / multi-boot quite a bit. I did a seperate /var because the 'SSD' article on the Arch wiki said: > If the SSD is the only storage device on the system (i.e. no HDDs),  consider allocating a separate partition for /var to allow for better  crash recovery for example in the event of a broken program wasting all  the space on / or if some run away log file maxes out the space, etc.  I don't know how common that is, but I went ahead and took their advice....

Do those look reasonable sizes, any recommendations?

---

### Post by isantop on 2011-12-02
> **wakajawaqa said:**
> Hi, thanks a lot for the reply.

My partitions are 15 GB for root (its presently 45% full, according to system monitor. A big chunk of that is Doom 3 files) 2 GB for /var (48% full) 6 GB for SWAP. I'm sure that is overkill, but I've got 6 GB RAM and, from what I've read, it seems I should have at the same amount for SWAP to hibernate.... maybe that's bunk, everywhere you look someone says something different. I alloted the rest for /home.

I always do a seperate /home, It's really just force of habit now, but when I was first learning about Linux, I was advised to do so because it would make it easier to multi-boot and do backups and I do distro-hop / multi-boot quite a bit. I did a seperate /var because the 'SSD' article on the Arch wiki said:  I don't know how common that is, but I went ahead and took their advice....

Do those look reasonable sizes, any recommendations?

That stuff from Arch really isn't relevant in Ubuntu. I've been using Ubuntu for about five years, solidly, and I've never once seen either of those two issues. I'd strongly recommend reinstalling, or setting up a single / partition.

Separate homes are still okay (they don't cause many problems), but I'd still recommend keeping an entire installation on a single partition. Booting multiple distros with the same home folder is a very bad idea and asking for a configuration file conflict to happen. A better way to do that is put the other distro on a separate partition, then use symlinks to link the folders in your Ubuntu home folder to the other distro.

---

### Post by wakajawaqa on 2011-12-02
I neglected to say I'm currently dual booting Arch w/ Openbox and I mimicked the partition scheme I used there. I haven't had any config problems because the Arch system is so minimal and has few (if any) of the same packages installed.

Anyway, thank you very much for your advice, I will go ahead and reinstall under a single partition as soon as this causes any other problems.

---

