---
title: "samba on lubuntu 14 working better than ever"
date: 2014-05-28
forum: Server Platforms
---

### Post by sturmey2 on 2014-05-28
Ok, not really. it's currently sharing using parameters that aren't in smb.conf, and there doesn't appear to be a way to reset it.

I ran **sudo cp /usr/share/samba/smb.conf /etc/samba/** to reset everything, but it's still sharing under the computer name I gave it in the previous conf file even though it's not in the replacement.

I set a folder to 777 permissions and shared it in smb.conf manually with guest = yes and I get asked for a user/pass to see the share.
If I use the samba configuration tool, it says I have everyone allowed, but the same request for user/pass

This worked in Lubuntu 12 on a different computer last time I set it up. I'm thinking that someone broke something in how samba is set up in the latest update.

Does Samba work at this point, or should I look for an alternative?:cry:

---

### Post by bab1 on 2014-05-28
> **sturmey2 said:**
> Ok, not really. it's currently sharing using parameters that aren't in smb.conf, and there doesn't appear to be a way to reset it.

I ran **sudo cp /usr/share/samba/smb.conf /etc/samba/** to reset everything, but it's still sharing under the computer name I gave it in the previous conf file even though it's not in the replacement.

I set a folder to 777 permissions and shared it in smb.conf manually with guest = yes and I get asked for a user/pass to see the share.
If I use the samba configuration tool, it says I have everyone allowed, but the same request for user/pass

This worked in Lubuntu 12 on a different computer last time I set it up. I'm thinking that someone broke something in how samba is set up in the latest update.

Does Samba work at this point, or should I look for an alternative?:cry:

Samba file sharing (smbd/nmbd) works in 14.04, just like it always has.  The parameter *guest = ok * is not valid however.  In never has been valid.  The correct term is *guest ok = yes*.  This may not be all of your problems but I would start with that and see what happens.

---

### Post by sturmey2 on 2014-05-28
It was late, and I didn't copy and paste, so I probably made an error posting, but I'll check. I'm wondering if purging and reinstalling will help. I guess it can't hurt. This install has been nothing but trouble, so maybe I need to wipe and reinstall.

---

### Post by bab1 on 2014-05-28
> **sturmey2 said:**
> It was late, and I didn't copy and paste, so I probably made an error posting, but I'll check. I'm wondering if purging and reinstalling will help. I guess it can't hurt. This install has been nothing but trouble, so maybe I need to wipe and reinstall.
Unless you have other problems, reinstalling Samba won't really help much.  Everything related to sharing (smbd) is configured in the smb.conf file.  If the smbd daemon is running then is has read the smb.conf file and configured itself.

---

### Post by sturmey2 on 2014-06-06
ok, so I found out how to reset Samba on the workstation and now I've tracked the errors back to how mounting happens in the latest versions of Lubuntu.
It seems when I plug in a USB drive I can't change any permissions on the mount point and that is what's limiting my access.

---

### Post by bab1 on 2014-06-06
> **sturmey2 said:**
> ok, so I found out how to reset Samba on the workstation and now I've tracked the errors back to how mounting happens in the latest versions of Lubuntu.
It seems when I plug in a USB drive I can't change any permissions on the mount point and that is what's limiting my access.

Most likely this is because the USB drive is formatted as FAT32 or NTFS.  Neither of these formats have provisions for Linux type ownership and permissions.  The module (driver) for the formatted drive allows you to set ownership and permissions if the partition is mounted via the ***mount*** command (via CLI, script or a line in /etc/fstab).  If, on the other hand, the partition formatted ext4 then the ownership permissions are that of the parent directory.

UDEV handles the actual auto-mount and you may be able to set the mount parameters in a  udev 70-persistent-storage.rule.  I've never never done that.  I mount all my partitions tvia fstab.

---

### Post by sturmey2 on 2014-06-06
Yes I have tracked the issue down to the "upgraded" mount system. In the last computer I set this up on, I plugged in the usb drive, opened the samba sharing, selected "share" and pointed at the usb drive and it just worked. 

The new mount only mounts the drive with 700 permissions which I can't change to save my life. Even when i specify that it should be mounted with umask=000 it still only mounts as700. I am not the only person that is having this issue. I think I'm going to install Windows since the permissions there for sharing will work with the drive I have.

I'm disappointed that I have to do this, but since the improvements have broken the way this works I guess I'm out.

---

