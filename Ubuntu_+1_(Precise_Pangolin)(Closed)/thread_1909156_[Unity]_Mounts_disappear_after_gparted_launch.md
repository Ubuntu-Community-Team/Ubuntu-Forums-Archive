---
title: "[Unity] Mounts disappear after gparted launch"
date: 2012-01-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by t1497f35 on 2012-01-14
Hi,
Is it addressed anywhere?

The mount points disappear (despite not being unmounted) after doing "sudo gparted" and don't come back even after closing gparted, so I have to logout and back in to get them to show up again.

Screenshots attached.

---

### Post by fabricator4 on 2012-01-14
> **t1497f35 said:**
> Hi,
Is it addressed anywhere?

Not that I'm aware off.  Confirmed for both Natty and Oneiric.  (Edit: I meant Oneiric and Precise.  Must have got caught in a timewarp there...)


> The mount points disappear (despite not being unmounted) after doing "sudo gparted" and don't come back even after closing gparted, so I have to logout and back in to get them to show up again.

Screenshots attached.

You should be able to get them back by opening file manager and clicking on them in the sidebar (worked here).

I noticed that USB drives are not affected.

You might be able to prevent the icons disappearing from the launcher by putting entries for the partitions in fstab.

Chris

---

### Post by t1497f35 on 2012-01-14
Thanks, my /etc/fstab file already contains them, so they're mounted right from the start.

> 
... usual stuff, then:
/dev/sda5    /media/movies        btrfs rw,nosuid,nodev,relatime 0 0
/dev/sda6    /media/music        btrfs rw,nosuid,nodev,relatime 0 0
/dev/sda7    /media/docs        btrfs rw,nosuid,nodev,relatime 0 0
/dev/sda8    /media/torrents        btrfs rw,nosuid,nodev,relatime 0 0
/dev/sda10    /media/movies2        btrfs rw,nosuid,nodev,relatime 0 0

The solution with the file manager doesn't work for me. They've not been in unmounted state so it's unclear why clicking on them in the filemanager would bring them back in the unity panel.

---

### Post by mc4man on 2012-01-14
See the same with gparted - once they're gone from unity launcher they will not return, whether mounted at boot (fstab) or thru nautilus doesn't matter.

Additionally there seems to be some inconsistent behavior in general - when unmounting internal drives from nautilus sometimes they leave the launcher, (expected behavior here with my settings), & sometimes they don't.

So there is at least 2 bugs here - ~/.xsession.errors shows some curious lines when using gparted

Also am surprised slightly by the new quicklist option to format - doesn't seem in line with the ongoing design philosophy of protecting users from themselves

---

### Post by effenberg0x0 on 2012-01-14
In your opinion, could a possible description be: 

- When the partitions are mounted during login, they are mounted by root.
- When you start gparted as root and with no arguments, you can see it scanning for a while. Maybe, during this scan, it sees the need to umount not-primary partitions to analise the structure of /dev/sd[a-z]. However, it is not set to remember previous state and remount the previously mounted partitions on exit.
- Then mounting fstab partitions would need root, which is why clicking the file-manager wouldn't be enough? So, you'd be stuck with sudo mount -a (or, of course, mounting specific units as root) or restarting.

---

### Post by t1497f35 on 2012-01-14
> **effenberg0x0 said:**
> In your opinion, could a possible description be: 

- When the partitions are mounted during login, they are mounted by root.
- When you start gparted as root and with no arguments, you can see it scanning for a while. Maybe, during this scan, it sees the need to umount not-primary partitions to analise the structure of /dev/sd[a-z]. However, it is not set to remember previous state and remount the previously mounted partitions on exit.
- Then mounting fstab partitions would need root, which is why clicking the file-manager wouldn't be enough? So, you'd be stuck with sudo mount -a (or, of course, mounting specific units as root) or restarting.
gparted doesn't unmount partitions on startup, it only does so when it needs to - like when formatting a partition - and even in this case it only unmounts the given partition. Check for yourself. It would be absurd (for gparted) to unmount a bunch of partitions only to be able to scan and list them.

As a proof, after I start gparted I check the state of those partitions in a few different file managers and they show up as mounted.

---

### Post by fabricator4 on 2012-01-14
> **t1497f35 said:**
> gparted doesn't unmount partitions on startup, it only does so when it needs to - like when formatting a partition - and even in this case it only unmounts the given partition. Check for yourself. It would be absurd (for gparted) to unmount a bunch of partitions only to be able to scan and list them.

As a proof, after I start gparted I check the state of those partitions in a few different file managers and they show up as mounted.

Agreed - gparted does not unmount the partitions, but as soon as it starts up and scans them they disappear from the launcher.

As an experiment, try unmounting them in Disk Utility. Re-mounting them in either disk Utility or Nautilus then causes them to be put back on the launcher. (unmounting in Gparted may also work)

Odd behaviour.  Something Gparted is doing is having an unexpected affect on the Unity Launcher.

Chris

---

### Post by mc4man on 2012-01-15
I think it's some interaction between nautilus & gparted that **can** cause unity an issue or 2 if the volumes are mounted.
Pretty easy to see if you have a nautilus window open while gparted is opening/scanning.
The Device section will 'refresh', if volumes are mounted then unity is affected.
small vid shows, in this case left the volumes unmounted so nothing 'bad' happened

---

### Post by effenberg0x0 on 2012-01-15
> **t1497f35 said:**
> gparted doesn't unmount partitions on startup, it only does so when it needs to - like when formatting a partition - and even in this case it only unmounts the given partition. Check for yourself. It would be absurd (for gparted) to unmount a bunch of partitions only to be able to scan and list them.

As a proof, after I start gparted I check the state of those partitions in a few different file managers and they show up as mounted.

It would be just as absurd as every other bug we see every day. It's a proposition, on a civil tone. I am dealing with other code now, which is why I haven't tested it myself. But I trust the judgement of others, there's no need to prove anything.

I agree to the others, It's a very curious finding. It doesn't seem risky, in terms of probable secondary effects, but please don't forget to report it.

Regards,
Effenberg

---

### Post by mc4man on 2012-01-15
Pretty simple here - any **mounted **volume(s) that are unmounted in nautilus when gparted has opened can't be re-mounted in nautilus until they are actually unmounted thru any means that does such things or a log out/in

The icon leaves the unity launcher because it's no longer 'mounted' in nautilus

---

### Post by fabricator4 on 2012-01-15
> **mc4man said:**
> Pretty simple here - any **mounted **volume(s) that are unmounted in nautilus when gparted has opened can't be re-mounted in nautilus until they are actually unmounted thru any means that does such things or a log out/in

The icon leaves the unity launcher because it's no longer 'mounted' in nautilus

So the problem is a Nautilus one, rather than the Launcher?

My latest test seems to confirm it.  If you are looking at one of the partitions in Nautilus (ie selected and viewing contents) then when you start Gparted it does not get "unmounted".

The main thing though is that the partitions are not being unmounted - if they were then I think you could almost say it was expected behaviour.  The Partitions only _appear_ to be unmounted - they are still accessible everywhere else such as CLI and Disk Utility.

Or should the bug be reported against Gparted?  It _might_ be reasonable to unmount unused partitions on startup, but why would USB drives be exempt, and why just make it inaccessible to Nautilus?  Here's a thought: I might boot up my Lubuntu partition and see if that behaves in the same way....

Chris

---

### Post by t1497f35 on 2012-01-15
TA DA!

It looks like Unity can't handle properly the "mount changed" event.

There are 3 types of mount events: mount removed, mount added and mount changed (though I don't know what "changed" means for a mount, it's not documented). There's also "pre unmount" but it doesn't matter for us.

I created a small app that monitors the mounts on the system and prints out those events.
After starting gparted ("sudo gparted") - it causes a "changed event" for the mounts of the system - which explains why they get rearranged in Nautilus - cause Nautilus treats this event properly and re-reads and rearranges the mount points (probably to make sure the info about the mount points is up to date), while Unity seems unprepared for this.

Gparted doesn't issue any "added" or "removed" events.
Notice, for some reason, gparted issues the "mount changed" signal (event) only once per user session, that is, if you close it and start it again it won't issue any "mount changed" anymore unless you log out and log in again.

---

### Post by fabricator4 on 2012-01-15
> **t1497f35 said:**
> TA DA!

It looks like Unity can't handle properly the "mount changed" event.


It's not just Unity.  I just got my Lubuntu partition going again and installed Gparted.  The file manager in Lubuntu is PCmanFM 0.9.9 and it is behaving exactly the same as Nautilus under Ubuntu.

The only common element here is Gparted.

Chris

---

### Post by t1497f35 on 2012-01-15
> **fabricator4 said:**
> 
The only common element here is Gparted.

In general it's about all the apps that are capable of firing a "mount changed" event (and about those which can't handle it properly), we know that gparted is one of them, but even if there's few such apps imo Unity should still learn to handle this event properly because it's a central part of Ubuntu, unlike the file manager you mentioned.

---

### Post by dino99 on 2012-01-15
> **t1497f35 said:**
> In general it's about all the apps that are capable of firing a "mount changed" event (and about those which can't handle it properly), we know that gparted is one of them, but even if there's few such apps imo Unity should still learn to handle this event properly because it's a central part of Ubuntu, unlike the file manager you mentioned.

As you have made deep testing, please report with your findings, before we get the next coming gparted release (still exist on Sid but waiting for sync in Precise)
[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/837213](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/837213)

---

### Post by t1497f35 on 2012-01-15
I'll report it as a Unity bug, since that's what it seems to be. Imo Gparted isn't guilty for issuing a mount changed signal.

EDIT: Actually I'm not filing any bug, according to [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) I must use ubuntu-bug and choose "other", which fails for me saying I didn't specify some parameter. So let anyone else file this bug for whom ubuntu-bug is working properly.

---

