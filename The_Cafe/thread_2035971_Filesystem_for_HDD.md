---
title: "Filesystem for HDD"
date: 2012-07-31
forum: The Cafe
---

### Post by 3Miro on 2012-07-31
Hi Everyone,

I have an external HDD that I share between several machines. The best way to protect your data on an external HDD is via encryption, which I have done. I also wanted to use a filesystem that has the nice properties of ext4 (speed, low fragmentation, universal support under Linux), so I have an encrypted external HDD with ext4 filesystem. 

Here is my problem: I am constantly running into issues with permissions. Files get written to the HDD with different usernames and different permissions, so often times I have to run chown or chmod commands to get access to my own files. On a regular system, permissions make sense, however, on an external HDD permissions are useless. Encryption is the only way to protect anything anyway.

Is there a filesystem that I can use on my external HDD that has the nice properties of ext4 and doesn't use any user:group permissions (i.e. the equivalent of 777/666 permissions).

This is either a DUH! response and the answer is already out there or this can be an interesting hacking/philosophical discussion. I am hoping for the former.

---

### Post by CharlesA on 2012-07-31
Are you sharing those files between *nix boxes? I assume so cuz of the use of ext4.

In my case, I haven't run into permissions problems since I made my user the same UID on both machines because the permissions are based off the uid, not the username.

---

### Post by ssam on 2012-08-01
on file systems without built in user support there are mount options to control which user the files appear to belong to. someone recently posted patch to add this to ext4
[https://lwn.net/Articles/496891/](https://lwn.net/Articles/496891/)

I am not sure if it was actually accepted.

alternatively you could try to solve this using groups, so the users on each computer all members of the same group.

or maybe you could use bindfs to make a view into the disk with different permissions. [https://code.google.com/p/bindfs/](https://code.google.com/p/bindfs/)

---

### Post by 3Miro on 2012-08-01
> **CharlesA said:**
> Are you sharing those files between *nix boxes? I assume so cuz of the use of ext4.

Yes, I am using all Linux.

> 
In my case, I haven't run into permissions problems since I made my user the same UID on both machines because the permissions are based off the uid, not the username.

I used to do that when I used my own personal machines, but now I have to use a workstation that belongs to my employer and the user ID are synced with a central server. I don't think I can overwrite this, but I will double-check.

---

### Post by 3Miro on 2012-08-01
> **ssam said:**
> on file systems without built in user support there are mount options to control which user the files appear to belong to. someone recently posted patch to add this to ext4
[https://lwn.net/Articles/496891/](https://lwn.net/Articles/496891/)

I am not sure if it was actually accepted.

Thanks for the link, I knew I wouldn't be the first to run into this problem. I will see if the gid option is available.

> 
alternatively you could try to solve this using groups, so the users on each computer all members of the same group.

Default group options are 644/755, in both cases the result is that group members cannot modify the files (only read). I can set umask, but this changes the behavior for all files, I want /home to still have 644/755 permissions and changing the files on the HDD to 666/777 or 664/775 is the same thing.

> 
or maybe you could use bindfs to make a view into the disk with different permissions. [https://code.google.com/p/bindfs/](https://code.google.com/p/bindfs/)

This looks interesting, although it may be a bit redundant as I would map the encrypted volume to a decrypted device, mount the decrypted device, "fuse" the folder to another folder. 

If it works I will use it, thanks for the link.

---

### Post by 3Miro on 2012-08-01
> **ssam said:**
> on file systems without built in user support there are mount options to control which user the files appear to belong to. someone recently posted patch to add this to ext4
[https://lwn.net/Articles/496891/](https://lwn.net/Articles/496891/)

I am not sure if it was actually accepted.

Ubuntu 12.04 doesn't have this feature, I don't think this was accepted upstream. It is a shame as it is an important feature.

> 
or maybe you could use bindfs to make a view into the disk with different permissions. [https://code.google.com/p/bindfs/](https://code.google.com/p/bindfs/)

bindfs works, it is a very clumsy approach as it requires the root password, but it works in the end. I hope they soon come up with a better solution.

---

