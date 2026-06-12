---
title: "Way to make all downloads lose executable permission?"
date: 2011-06-16
forum: Security
---

### Post by nrundy on 2011-06-16
Is there any way to make all downloads (perhaps to a specific folder) automatically adopt a specific Permissions format: rw-------?

This way nothing can execute unless I specifically change the permission setting on the downloaded item?

This would also be desirable if it applied to USB thumb drives. This way malicious software on a drive would lose executable permissions upon mount.

I wish this sort of security setup was default in ubuntu.

---

### Post by jerome1232 on 2011-06-16
If you have a separate /home you could mount it with the noexec option, nothing could be executed from /home ever that way.

alternativly... and my knowledge on this is a bit fuzzy in this area but I believe you can use ACL's (access control lists) to achieve what you desire.

---

### Post by nrundy on 2011-06-16
Well, sometimes I need to execute something. For example, if I download a .deb and want to execute it to install something.

So taking away the ability to execute completely would be too severe. I just want to prevent a program from having exe capabilities unless I specifically allow it.

---

### Post by cpmman on 2011-06-16
Folder Properties - Permissions - Apply permissions to enclosed files.

(move file to another folder if exec permissions to be added)

---

### Post by nrundy on 2011-06-16
> **cpmman said:**
> Folder Properties - Permissions - Apply permissions to enclosed files.

(move file to another folder if exec permissions to be added)

Yes, but files landing in the folder don't automatically gain the permissions. It leaves the user having to remember to run the permissions every time a file is added. So the file will land on the drive with exe permissions, damage could be done if hostile.

---

### Post by bodhi.zazen on 2011-06-16
Are you downloading to a FAT or NTFS partition ? Or a linux partition ?

---

### Post by nrundy on 2011-06-16
Linux partition. downloads from surfing the net while using ubuntu.

---

### Post by bodhi.zazen on 2011-06-16
That is not the default behavior. If this happens on all partitions, then I would ask what your umask is.

If it happens only on a few partitions , what is unique about the partition you are downloading to ? Is it a samba share ?

---

### Post by nrundy on 2011-06-17
> **bodhi.zazen said:**
> That is not the default behavior. If this happens on all partitions, then I would ask what your umask is.

If it happens only on a few partitions , what is unique about the partition you are downloading to ? Is it a samba share ?

What?

What do you mean bodhi? I'm asking if there is a way to make the file lose exe permissions. What do you mean "is not the default behavior. If this happens on all partition, . .."

Nothing is happening. I'm asking if there is a way to improve security.

---

### Post by Lars Noodén on 2011-06-17
> **nrundy said:**
> I'm asking if there is a way to make the file lose exe permissions.

Then jerome1232's suggestion of mounting a separate /home partition as noexec is the way to  go.  It will not affect .deb's that you download  because that is data.

---

### Post by bodhi.zazen on 2011-06-17
> **nrundy said:**
> What?

What do you mean bodhi? I'm asking if there is a way to make the file lose exe permissions. What do you mean "is not the default behavior. If this happens on all partition, . .."

Nothing is happening. I'm asking if there is a way to improve security.

When I download a file it is not given execution permissions. So your "problem" is not the standard, default behavior.

I am suggesting we try to understand what setting you changed, did you change your umask ? custom .bashrc ?

---

### Post by jerome1232 on 2011-06-17
> **bodhi.zazen said:**
> When I download a file it is not given execution permissions.

I was under the impression that this was a what-if that the op is trying to avoid.

I have never seen a download arrive with executable permissions, is that due to te umask? If so then it is a non-issue and nothing needs to be setup

---

### Post by bodhi.zazen on 2011-06-17
> **jerome1232 said:**
> I was under the impression that this was a what-if that the op is trying to avoid.

I have never seen a download arrive with executable permissions, is that due to te umask? If so then it is a non-issue and nothing needs to be setup

Well, there are several potential variables.

umask value - this is applied to new files / directories

File system. Permissions on FAT/NTFS are not the same as linux.

mount options - noexec

apparmor - where is a user allowed to down load to ? $HOME ? /tmp ?

network files systems - permissions will vary with samba and nfs mounts.

Reading - Perhaps I misunderstood the problem / question - I though the user was experiencing downloaded files arriving as executable.

Linux != windows, so if you run a file you can only affect files in $HOME unless you run it as root, or find a way of elevating privileges.

If you are asking about running arbitrary code, well such hypothetical code can do whatever you hypothisize.

Apparmor would be the next step in security. For example, I use apparmor to lock down security in $HOME, no reason firefox should have access to anything in $HOME but Downloads and ~/.mozilla (config files).

You can confine users with apparmor, or go to Fedora and use selinux. In Fedora selinux confines users further (user_u) and there is also xguest .

---

### Post by nrundy on 2011-06-19
> **bodhi.zazen said:**
> When I download a file it is not given execution permissions. So your "problem" is not the standard, default behavior.

I am suggesting we try to understand what setting you changed, did you change your umask ? custom .bashrc ?

ah, now I understand. thanks for clarifying, bodhi.

I looked at this again and realized I made a mistake in my initial post/s.  files are landing on my drive without exe permission. the problem is that some are landing as compressed files (eg, tar.gz). When I extract then the file lands with executable, Group, and Other permissions allowed. Plus when I copy from a USB then files land with exe and Group Other permissions allowed.

Is there a way to get files to basically never have Executable, Group, Other permissions unless I manually give it to them?

---

### Post by bodhi.zazen on 2011-06-19
> **nrundy said:**
> ah, now I understand. thanks for clarifying, bodhi.

I looked at this again and realized I made a mistake in my initial post/s.  files are landing on my drive without exe permission. the problem is that some are landing as compressed files (eg, tar.gz). When I extract then the file lands with executable, Group, and Other permissions allowed. Plus when I copy from a USB then files land with exe and Group Other permissions allowed.

Is there a way to get files to basically never have Executable, Group, Other permissions unless I manually give it to them?

'never' is a long time, and the solution varies with your use.

Your first step should be to have separate partitions for /home and /tmp and mount them noexec.

The problem when copying from a flash drive is that the flash is typically FAT or NTFS, so, set your permissions properly when you mount the flash drive.

Similarly you would need to configure your network mounts as well.

---

### Post by Lars Noodén on 2011-06-19
> **bodhi.zazen said:**
> ... the flash is typically FAT or NTFS, so...

I'd like to see a campaign to update camera and other firmware to support EXT2 instead.

---

### Post by bodhi.zazen on 2011-06-19
> **Lars Noodén said:**
> I'd like to see a campaign to update camera and other firmware to support EXT2 instead.

Good luck with that =)

---

### Post by nrundy on 2011-06-19
> **bodhi.zazen said:**
> 'never' is a long time, and the solution varies with your use.

Your first step should be to have separate partitions for /home and /tmp and mount them noexec.

The problem when copying from a flash drive is that the flash is typically FAT or NTFS, so, set your permissions properly when you mount the flash drive.

Similarly you would need to configure your network mounts as well.

/tmp is a subdirectory of /home right? wouldn't it be enough to just make /home its own partition?

Assuming I make /home its own partition and set it to noexec, this would just default all aps to noexec but still allow me to manually enable exe capabilities on select apps, right?

Does setting noexec have to be done when creating the parition or can it be set after creation?

---

### Post by bodhi.zazen on 2011-06-19
> **nrundy said:**
> /tmp is a subdirectory of /home right? wouldn't it be enough to just make /home its own partition?

No, /tmp is a subdirectory of /

> assuming I make /home its own partition and set it to noexec, this would just default all aps to noexec but still allow me to manually enable exe capabilities on select apps, right?

No, noexec means noexec, you can not pick and choose if you set this option on the partition.

You have to decide what you want, you first said "never" , now you want some to be exec, lol.

> Does setting noexec have to be done when creating the parition or can it be set after creation?

You set options in fstab.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by nrundy on 2011-06-19
> **bodhi.zazen said:**
> No, /tmp is a subdirectory of /



No, noexec means noexec, you can not pick and choose if you set this option on the partition.

You have to decide what you want, you first said "never" , now you want some to be exec, lol.



You set options in fstab.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

Well when I said never I meant that they never default to exe. But they would still be able to be set manually to have this capability. I thought I made this clear, sorry about that misunderstanding.

---

### Post by bodhi.zazen on 2011-06-19
> **nrundy said:**
> Well when I said never I meant that they never default to exe. But they would still be able to be set manually to have this capability. I thought I made this clear, sorry about that misunderstanding.

Well, in general they will not be exec, you identified the two most common exceptions.

The third would be (some) network shares, such as samba.

---

### Post by nrundy on 2011-06-19
> **bodhi.zazen said:**
> Well, in general they will not be exec, you identified the two most common exceptions.

The third would be (some) network shares, such as samba.

These "exceptions" though are two of the most common ways to get exploited though. That's what concerns me. It seems to me these exceptions should be eliminated by the developers, if possible.

---

### Post by CharlesA on 2011-06-19
> **nrundy said:**
> /tmp is a subdirectory of /home right? wouldn't it be enough to just make /home its own partition?

Assuming I make /home its own partition and set it to noexec, this would just default all aps to noexec but still allow me to manually enable exe capabilities on select apps, right?

Does setting noexec have to be done when creating the parition or can it be set after creation?

/tmp is off of the root (/)

/home is off of the root as well.

You'd be able to just make /home it's own partition and set it as noexec in fstab and be done with it.

As far as I know that doesn't allow you to execute scripts and whatnot, but I'm not sure how it does that.

---

