---
title: "SCP over SSH help"
date: 2010-11-15
forum: Security
---

### Post by gr8day8 on 2010-11-15
I'm looking to do file transfers using SCP over SSH.
If I use a standard shell, users can browse the directory structure ... = BAD
 
When I use rssh as a shell, I can't ls any files. Users need to be able to see the names of the files I've placed in their directory. 
 
I've played with jailbreaking, but it creates an entire directory structure so the user sees a "virtual machine". I don't want that, too compliaced. 
 
What I'm looking for is to have a user log in, see only their files, and be chrooted to their home. No files below or above. Like when you give an fpt account /bin/false.
 
Is this possible? I want to use SCP, not SFTP.
 
thanks -BT

---

### Post by bodhi.zazen on 2010-11-15
> **gr8day8 said:**
> 

Is this possible? I want to use SCP, not SFTP.
 
thanks -BT

No. If users ssh (scp) in they need access to things outside of their home directory.

The closest thing to what you are describing is a chroot jail.

I suggest you look into ssh keys (with forced commands), sshfs, and tools such as apparmor to confine a user as much as possible.

---

