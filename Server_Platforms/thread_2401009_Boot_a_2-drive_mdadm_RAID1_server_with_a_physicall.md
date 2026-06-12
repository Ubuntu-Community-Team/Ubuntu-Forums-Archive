---
title: "Boot a 2-drive mdadm RAID1 server with a physically disconnected drive"
date: 2018-09-12
forum: Server Platforms
---

### Post by florianjakubina14 on 2018-09-12
Hello everyone,

coming from AskUbuntu and having not received an answer so far, I'm giving a try here.

Here is the context: a friend and I have a project for which we would like to create a server based on old components. First of all, I spent some time reading what solution would be the best including OS (Ubuntu, Nas4Free and so on), RAID and partitioning (which partitions, LVM, ...). I choose Ubuntu for flexibility/possibilities, support and concept understanding.

So far, after following few tutorials describing command lines and GUI solution, I succeeded to obtain some good results. Here are the two main tutos that I followed:

    [https://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04](https://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04)
    [https://www.youtube.com/watch?v=4KiWxMDKu94](https://www.youtube.com/watch?v=4KiWxMDKu94)

So, my Ubuntu server consists of 2 drives in RAID1 created from mdadm. I have 3 RAID1 partitions mounted on boot, swap & root (/). GRUB being installed on both drives, I can successfully boot from each. Also, I tried to boot from a single drive by making the other one "fail" (command lines) and disconnecting it (physically). Then I can reconnect it, add to respective RAID1 again and things are running...

However, something is disturbing me: if a drive is physically disconnected without having set flag "fail" then my server does not boot. I could imagine this a software raid limitation but after googling a lot, I cannot find such an info to be sure about that. But in practice, it means my server cannot handle a power cycle issue for instance. Am I right? Or is there a problem in the configuration leading to that result?

In addition, I have another question (I haven't look for info yet and this one could seem stupid...) about LVM: is there any requirement about the physical volume that would be set in a volume group, divided in two logical volumes mounted on root (/) and home? In particular, my idea was to define as physical volume my current RAID1 partition used for root (/) and the subsequent logical volume would replace it.

Best regards,

Florian

---

### Post by darkod on 2018-09-12
Booting degraded raid1 array (with a member missing) is a mistery for me too. I have done some tests that didn't work as expected and had no time to investigate deeper.

The question about LVM I do not understand. Are you asking whether you can create only one LV in a VG (only root LV)? If that is the question then the answer is yes. You take your raid1 array (/dev/mdX) and you assign it as PV for LVM. After that you create a VG on that PV. Once you have the VG you can create as many as you want/need LVs in it. If you need only one, it can be only one. One hint: do not assign all VG space to the LV right away. The benefit of LVM is that you can expand as needed. If you assign all space to one LV in the future you will not have an easy way to create another one (because you will have no free space in the VG). Assign only what is necessary to the LVs and later as they grow you can expand.

---

### Post by florianjakubina14 on 2018-09-12
Good evening darkod and thank you for your answer.

Actually, by disconnecting my drive without explicitly making it fail, the raid1 is not degraded from a mdadm point of view. That's probably the reason why my system does not boot (mdadm does not see it as degraded so it expects two drives).
When the drive is set to "fail" then the degraded state is known by mdadm and everything goes fine when disconnected. That would also be the case if the drive dies while the server is running.
Therefore I'm worried because depending on its consumption (still need to measure it), I plan to not let it run 24h/24 and it would be a pity if a drive dies during a power cycle...

Regarding LVM, my concern was to initially have a raid1 partition mounted as root then use it as PV to be finally turned into 2 VG for root and home. I was a little bit confused by the moving role of the RAID1 partition but after all, there is no big deal with that and when configuring my partitions, I don't have to mount the raid1 array and I can immediately assign it to a VG. 

Anyway, thank you for you piece of advice about VG space. I'm still wandering what I will exactly do about "space allocation": I often read on internet that a good practice is to allocate 15 to 20 Gb for root and the remaining for home but in my case, I mainly need shared documents/files and sources codes (versioning) so I don't think the home directory is relevant for that (/opt or /srv seem to suit better).

Florian

---

