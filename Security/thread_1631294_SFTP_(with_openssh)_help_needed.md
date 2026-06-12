---
title: "SFTP (with openssh) help needed"
date: 2010-11-26
forum: Security
---

### Post by Vectorferret on 2010-11-26
What I want to do is: allow sftp access to my Ubuntu system (happens to be desktop as it's also my main system) using accounts that are not able to login normally. (I have already managed to create such accounts.) These accounts need to be chrooted (also already accomplished with the openssh daemon settings.) Where I run into problems is that I want to give them (read only) access to files outside the chroot (on another partition in fact) and the matter if made more difficult because the directories to be shared are on NTFS-3G partitions (as they are a shared linux / windows storage drive). Is this possible and if so, what do I need to do?

Edit - Forgot to include versions
Ubuntu 10.10
openssh 1.5.5p1-4ubuntu4 (the one that comes with 10.10)

---

### Post by cariboo on 2010-11-26
Ssh users already have read only access to files not owned by the user, by default.

---

### Post by Vectorferret on 2010-11-29
> **cariboo907 said:**
> Ssh users already have read only access to files not owned by the user, by default.That isn't what is happening for me. I have this in my fstab:
/media/Cargo_Bay_1/Books /home/(the_user)/Books bind defaults,bind 0 0

They have full write privileges when they login with ssh. Is there a better way to give them access. (Even better is a shared home directory for ftp users and then giving them read only to the mappings but I don't know how to do that.)

---

### Post by cariboo on 2010-11-29
What type of file system does the disk have, if it is NTFS, you can only set permissions for the mount point. If it is something else (ext2/3/4} you can set ownership and permissions for the individual files/directories.

Oops, I just re-read your first post. Linux permissions don't work with NTFS file systems, and Windows permissions don't work with Linux.

---

### Post by CharlesA on 2010-11-29
What is the file system for that drive?

---

### Post by Vectorferret on 2010-11-29
> **cariboo907 said:**
> What type of file system does the disk have, if it is NTFS, you can only set permissions for the mount point. If it is something else (ext2/3/4} you can set ownership and permissions for the individual files/directories.

Oops, I just re-read your first post. Linux permissions don't work with NTFS file systems, and Windows permissions don't work with Linux.
Yes, it is NTFS. I need some other way of doing it then file permissions. This is why I am having so much trouble.

---

### Post by CharlesA on 2010-11-29
I don't think there is a way to "lock it down" if you are using NTFS, since it uses whatever global permissions you tell it to when it's mounted.

EXT2/3/4 have the advantage of being able to use linux permissions in that respect.

What exactly are you trying to accomplish?

---

### Post by Vectorferret on 2010-11-29
> **CharlesA said:**
> What exactly are you trying to accomplish?
Overall goal: I want to share access to certain directories to my friends in a simple, standard, cross platform way. (Which is why so far I have picked SFTP.) These directories are on an NTFS drive as I wish to use them in both linux and windows myself. I could change the file system given time if it is to something windows can also read/write effectively and safely (even if that means installing something extra). I do not want them to have any write access to these directories, or any access to the rest of the system outside of a chroot (some of them are online friends of varrying levels of trust). They do not need any ability to write their own files (but as far as I know Ubuntu requires a writeable home directory). The sharing method need to be done by a daemon so it is always available. It must work outside of the NAT (either with or without port forwarding). There is no problem or issue with installing software so long as it is easily available on an Ubuntu system (I have root access on the machine that physically houses the drives, I also have physical access and can open the case if that somehow becomes needed).

---

### Post by CharlesA on 2010-11-29
You could mount the drive as read only and go from there. It would make it a pain for you, since you wouldn't be able to write to anything on the drive.

---

### Post by Vectorferret on 2010-11-29
> **CharlesA said:**
> You could mount the drive as read only and go from there. It would make it a pain for you, since you wouldn't be able to write to anything on the drive.Not going to be able to do that. They are my only real storage drives and my best way of exchanging information between OS'.

---

### Post by CharlesA on 2010-11-29
Would it be possible to put the files they want to access on another drive and set it up like that?

---

### Post by Vectorferret on 2010-11-30
> **CharlesA said:**
> Would it be possible to put the files they want to access on another drive and set it up like that?They are too large to manage that unfortunately.

---

### Post by CharlesA on 2010-11-30
> **Vectorferret said:**
> They are too large to manage that unfortunately.
Not sure what you can do in that case, unfortunately.

Perhaps someone else has another suggestion. :)

---

