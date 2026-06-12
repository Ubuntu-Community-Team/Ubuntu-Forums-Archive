---
title: "Permissions in network drive"
date: 2010-09-19
forum: Security
---

### Post by skamarla on 2010-09-19
Hi everyone,

I have a router with a USB port. If you connect a mass storage device into that USB port, you get a network disk (FTP-based, single-user).

I would like to use this feature to have a central repository of important data for the three PC's in my home. I'm thinking of having Unison synchronize the local disks with the network.

Can I keep the users and permissions for the local PC's on the network drive? UID's are the same.

The disk is NTFS right now, but I may reformat it to ext3, if necessary (although I'm not sure if the router will detect the ext3 format).

Also, if I dual-boot into Windows, is there a way to map the Windows users into Linux?

---

### Post by uselpa on 2010-09-19
I don't think that your UID and GID will get copied over to NTFS. Generally speaking there's no easy way to map Windows and Linux users.

---

### Post by serverfarm on 2010-09-19
What router?  Some are fancy enough to allow things like permissions, some aren't.

---

### Post by bodhi.zazen on 2010-09-19
> **skamarla said:**
> Hi everyone,

I have a router with a USB port. If you connect a mass storage device into that USB port, you get a network disk (FTP-based, single-user).

I would like to use this feature to have a central repository of important data for the three PC's in my home. I'm thinking of having Unison synchronize the local disks with the network.

Can I keep the users and permissions for the local PC's on the network drive? UID's are the same.

The disk is NTFS right now, but I may reformat it to ext3, if necessary (although I'm not sure if the router will detect the ext3 format).

Also, if I dual-boot into Windows, is there a way to map the Windows users into Linux?

Depends on the capabilities of the router, but you would need to try with ext3 as ntfs does not support Linux permissions.

---

### Post by skamarla on 2010-09-19
> **serverfarm said:**
> What router?  Some are fancy enough to allow things like permissions, some aren't.

It's a Huawei HG553, but I don't think it's got much in the way of permissions. All it does is give FTP access to the USB drive, and only one FTP user is allowed.

If I format it as ext3, do you think permissions will work, though?

---

