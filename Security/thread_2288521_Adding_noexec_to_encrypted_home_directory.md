---
title: "Adding noexec to encrypted home directory"
date: 2015-07-28
forum: Security
---

### Post by drm200 on 2015-07-28
When I setup Ubuntu initially, I encrypted my home directories.

If I run the "mount" command I can see (as shown below) that the user home directory is allowed to execute files.  I'd like to mount the user home directory with the noexec flag.
Does anyone know how to do this?   There is no reference to the encrypted directory in fstab.


Mount output for user1:

/home/dan/.Private on /home/user1 type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=038df6b2ec5da738,ecryptfs_fnek_sig=5b277702372fac00)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=user1)

---

### Post by CharlesA on 2015-07-30
Found this, but I doubt it is any help: 
[http://askubuntu.com/questions/591708/change-ecryptfs-mount-options-remove-nosuid](http://askubuntu.com/questions/591708/change-ecryptfs-mount-options-remove-nosuid)
[http://unix.stackexchange.com/questions/39395/mount-options-with-ecryptfs-encrypted-home](http://unix.stackexchange.com/questions/39395/mount-options-with-ecryptfs-encrypted-home)

---

### Post by drm200 on 2015-08-01
thanks for the links ... unfortunately they did not lead to any insight in how to mount an encrypted directory with noexec flag.

I've spent about 10 hours searching for help on this .... but have not found any ideas .... it seems strange that an encrypted directory should be left open to file execution ...  My home directory was encrypted for security reasons and contains the standard subdirectories (downloads, music, documents, etc) .. and all of these directories can not be protected with the noexec flag.

This would seem to be a security hole.

---

