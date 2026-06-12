---
title: "Problem loading encrypted volume on boot (16.04.01)"
date: 2016-07-21
forum: Security
---

### Post by hiramabif2 on 2016-07-21
I'm a serial distro-hopper and I'm finally trying out Ubuntu 16.04.01.

I keep the same /home partition no matter what distro I use.

Typically, what I do when I try out a new distribution is the following:

1. Find the UUID of the device (/dev/sdb1)
2. Add a line to /etc/crypttab:

data UUID=(UUID of /dev/sdb1) none luks

3. Add a line to /etc/fstab:

/dev/mapper/data /home ext4 auto 0 2

--

Now, the weird thing is, I'm never prompted for a password for dev/sdb1!

I've checked and doublechecked to ensure that I'm using the correct UUID -- that is, of the block device and not the mapper.

Can anyone help?

---

### Post by DuckHook on 2016-07-21
> **hiramabif2 said:**
> I'm a serial distro-hopper and&#8230;I keep the same /home partition no matter what distro I use&#8230;&#8230;which is probably not a good idea. /home is where a lot of user-specific config files are kept, including some that are peculiar to each distro. Each distro does things slightly differently and it only takes a slight difference to break decryption. After all, that's the whole point in encryption: the decryption method must be absolutely exact, because any attempt that isn't could be from a malicious attack.

For this and other reasons, the usual advice is to keep your /home directories matched to each specific distro, create a shared data directory/partition and link the data back to each /home. You can encrypt the data directory/partition as strongly as you like.

I can't help you with your issue because I have no idea what distro created your original directories, or how they've customized their encryption schemes. Other users may be able to help you if you post your original distro details to this thead.

---

### Post by hiramabif2 on 2016-07-21
LUKS is not distro-specific, so that should not be an issue. This was originally created in, I believe, Debian 7. 

For diagnostic purposes, I have created a /new/ LUKS-encrypted partition within Ubuntu and the same problem seems to exist.

---

### Post by DuckHook on 2016-07-21
*Thread moved to **Security** as the more appropriate forum.*

You are more likely to find the expertise that you need here.

---

