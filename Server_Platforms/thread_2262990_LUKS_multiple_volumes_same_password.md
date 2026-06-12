---
title: "LUKS multiple volumes same password"
date: 2015-01-28
forum: Server Platforms
---

### Post by xen3 on 2015-01-28
Hi,

perhaps this is covered elsewhere more extensively but.... I found it hard to get real information on LUKS.

I decided to give it a show and install Server using a single unencrypted /boot partition as primary on this disk drive.

Then I created a LVM volume group on the entire rest of the drive. In the volume group I created a number of volumes, two for root filesystems, two for swap, and one for data.

Then I encrypted all of them, using the installer. I gave "data" a different password, but the other 4 volumes have the same passwords.

Now this means all the volumes are encrypted separatedly, but inside the LVM. Now when I boot the system (using a display, this is actually just a laptop, nothing fancy server-wise yet) I am asked for 5 different passwords, 4 of which I need to retype as they are all the same. I would have expected some kind of automation as I know it happens with TrueCrypt.

Now after a while it dawned on me that different setups would also have been possible. E.g.... you could have:

- three physical logical partitions, one for the main system, one for the secondary system, one for data, then encrypt that partition, in the encrypted partition create LVM volume group, within that create volumes for root and swap.

Then, if that works, you only need 3 passwords, one for the main group, one for the second group, and one for data.

However the annoying part at this point is that it won't even allow me to boot without giving ALL of the passwords. Even if it doesn't even need 3 of those volumes, it still won't boot unless I give all of them.

I don't even know if I need that unencrypted /boot partition, it just seemed to be something that was mentioned in pretty much every guide.

I could use it to select between two operating systems (both linux) and then only need to type the password for the one I choose.

But currently it just wants everything.

I guess I may have found a solution in:

[http://ubuntu.aspcode.net/view/635400140124705175187072/full-disk-encryption-with-luks-auto-mount-second-volume](http://ubuntu.aspcode.net/view/635400140124705175187072/full-disk-encryption-with-luks-auto-mount-second-volume)

---

### Post by MAFoElffen on 2015-01-28
Note- I'm not real familiar with LUKS encrption, but I know some in the server section are. Let me message a Mod to see if they would move this to the Server Section to try to get this appropriate attention.

---

