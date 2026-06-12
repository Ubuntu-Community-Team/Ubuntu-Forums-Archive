---
title: "New server install partitioning for KVM host."
date: 2012-11-01
forum: Server Platforms
---

### Post by Slug71 on 2012-11-01
Hey guys,

Im installing both Ubuntu Sever and CentOS on one of the drives in my test rig. Both will be set-up the same as hosts running VMs. Just want to get a feel of the differences of each and see which I like better.

I have 70GB spare on the drive which I will be dividing between the two. Thats after allocating space to the Swap area. I know its not much space but like I said, it's only to mess around with.

These are my first Linux server installs i've ever done and have no idea how the partitioning should go. I know for Desktop use it's usually just / and /home along with Swap but here i have no idea what the 'standard' is if there even is a standard. Or how much space is generally allocated to various partitions like /var etc... if those others are required.

So give I have 35GB for each install, how would I partition them?

Thanks in advance.

---

### Post by chadk5utc on 2012-11-02
From my own experience the biggest difference you'll notice right away is that CentOs(.rpm-RedHat based) has a GUI where Ubuntu(.deb-Debian Based) does not. Heres a link for KVM that should give you more than I could explain
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

### Post by sandyd on 2012-11-02
> **Slug71 said:**
> Hey guys,

Im installing both Ubuntu Sever and CentOS on one of the drives in my test rig. Both will be set-up the same as hosts running VMs. Just want to get a feel of the differences of each and see which I like better.

I have 70GB spare on the drive which I will be dividing between the two. Thats after allocating space to the Swap area. I know its not much space but like I said, it's only to mess around with.

These are my first Linux server installs i've ever done and have no idea how the partitioning should go. I know for Desktop use it's usually just / and /home along with Swap but here i have no idea what the 'standard' is if there even is a standard. Or how much space is generally allocated to various partitions like /var etc... if those others are required.

So give I have 35GB for each install, how would I partition them?

Thanks in advance.
I just did a standard root partition, then have  /var/lib/vz (where my qemu/kvm disk images are stored) on a on a LVM partition, so I could extend it later if I needed.

Really, there isn't any 'standard' to partitioning. Its more about your needs, and your plans for future growth.

---

### Post by LHammonds on 2012-11-02
Figuring out a design of the partition system is a major step for setting up a server.  I also have found that you need to design your system to be flexible so you don't pigeon-hole yourself when the server starts taking on different roles as it goes.

Take a look in my sig for how I setup my Ubuntu Servers which has a large section that covers partitioning, LVM and long-term maintenance of space over time.

LHammonds

---

### Post by Slug71 on 2012-11-03
> **chadk5utc said:**
> From my own experience the biggest difference you'll notice right away is that CentOs(.rpm-RedHat based) has a GUI where Ubuntu(.deb-Debian Based) does not. Heres a link for KVM that should give you more than I could explain
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

Yeh thats really why I'd like to try the difference between them. Thanks for the link. :)

---

### Post by Slug71 on 2012-11-03
> **sandyd said:**
> 
Really, there isn't any 'standard' to partitioning. Its more about your needs, and your plans for future growth.

> **LHammonds said:**
> Figuring out a design of the partition system is a major step for setting up a server.  I also have found that you need to design your system to be flexible so you don't pigeon-hole yourself when the server starts taking on different roles as it goes.

Take a look in my sig for how I setup my Ubuntu Servers which has a large section that covers partitioning, LVM and long-term maintenance of space over time.

LHammonds

Yeh thats pretty much what I've concluded.

Busy looking at your sig. now thanks. :)

---

### Post by Slug71 on 2012-11-03
> **sandyd said:**
> I just did a standard root partition, then have  /var/lib/vz (where my qemu/kvm disk images are stored) on a on a LVM partition, so I could extend it later if I needed.


So just / and /var/lib/vz will do? no /home?

---

### Post by sandyd on 2012-11-04
> **Slug71 said:**
> So just / and /var/lib/vz will do? no /home?

it depends on where your VMs reside - /var/lib/vz is a directory specific to Proxmox on Debian.

However, back to the question, there is no reason to create a seperate /home partition because /home is generally not used.

---

### Post by Slug71 on 2012-11-05
> **sandyd said:**
> it depends on where your VMs reside - /var/lib/vz is a directory specific to Proxmox on Debian.

However, back to the question, there is no reason to create a seperate /home partition because /home is generally not used.

Thanks sandyd.

I already did the CentOS installation. I just made a /(10gb) and the rest of the space(26gb) a LVM partition. I haven't been able to boot it though as tge Grub menu doesn't seem to be loading. Does that seem to be good though?

---

### Post by sandyd on 2012-11-06
> **Slug71 said:**
> Thanks sandyd.

I already did the CentOS installation. I just made a /(10gb) and the rest of the space(26gb) a LVM partition. I haven't been able to boot it though as tge Grub menu doesn't seem to be loading. Does that seem to be good though?

The setup seems to be good - you can grow the LVM onto more HDDs as more space is needed.

---

### Post by Slug71 on 2012-11-06
> **sandyd said:**
> The setup seems to be good - you can grow the LVM onto more HDDs as more space is needed.
Thanks! :)

---

