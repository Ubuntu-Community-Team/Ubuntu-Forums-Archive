---
title: "Server not booting after messing with root file permissions"
date: 2019-12-09
forum: Server Platforms
---

### Post by mangonels on 2019-12-09
Hi. I was messing with the permissions for the root folders on my system (removed all "other" user permissions setting them to -, and later set permissions for others to r-x, if not higher, for all of the mentioned root folders). After that, I also happened to delete a user, which I later created again... The user in question should have been non-consequential to the accessibility of the system, but, probably due to the previous permission modifications on the root folders, the ssh connection froze and I lost control over it. 
The root account (and one other access account) where unaltered . So I'd presume the permission modifications over the root folders are more likely to have caused the problem. That's all I did (no more).

Folder's current permissions (as seen from kimsufi's rescue mode):
[IMG]https://imgur.com/B4CH9EH[/IMG]
[IMG]https://i.imgur.com/B4CH9EH.png[/IMG]

After the mentioned changes, the system won't boot (restart on the kimsufi pannel) if set to start from hard drive, and I have no idea which change exactly over the file permissions may have caused the problem, or if it was the apparently inconsequential user deletion I did after.

The OS is remotely hosted in a dedicated Kimsufi server (ovh), so luckily I can start the system in rescue mode.

I obviously don't seem to know what I'm doing. I can use ubuntu fairly decently, but when I get into more complicated stuff I seem to mess up things easily. I must also mention I got into this situation since I didn't follow instructions propperly on the last post I made, so now it's costing me more time than I wanted to dedicate, just in the attempt to fix this.

Solutions I see would be to either fix the boot problem (with your help), or backup and reinstall ubuntu (which I really would like to avoid). In any case, all I have access to is rescue mode in order to achieve any of both.

Ubuntu version: 18.04
Terminal only.

---

### Post by slickymaster on 2019-12-09
*Thread moved to **Server Platforms**.*

---

### Post by SeijiSensei on 2019-12-09
I vote for reinstalling. Trying to go back and fix permissions changes could take a very long time.

Promise me you won't do this again.  The permissions structure is carefully laid out and doesn't need "fixing."

---

### Post by mangonels on 2019-12-09
Allright then... Thanks.

---

### Post by mangonels on 2019-12-09
Still clueless as to how I'm going to get those files out of there. I do have access to them.

---

### Post by mangonels on 2019-12-09
Oh my god, all I wanted was a limited access account, this is a nightmare.

---

### Post by SeijiSensei on 2019-12-09
> **mangonels said:**
> Oh my god, all I wanted was a limited access account, this is a nightmare.
Every account other than the initial one created that has sudo privileges has limited access. Ordinary users can write files to their home directories and to /tmp. That's it.

Now there are other types of limited accounts like ones that are created with chroot.  But honestly I don't see much reason for accounts like these.  Unix and its offspring like Linux have been multi-user from the outset with a lot of thought given to how to protect users from each other and from endangering the overall system.

One aspect of Ubuntu that you might want to change is its use of 755 permissions on home directories. That enables users to list and view the files in others accounts. Linux distributions with more of an "enterprise" orientation like RedHat and its free clone CentOS assign 700 permissions to home directories. This grants the owner full permissions in her home directory but blocks other users from seeing the files therein.  If you want to adopt this model, before creating other users, log in then run
```

cd ~
chmod 700 . -R

```
To make these limited permissions the default for new users, edit the file /etc/login.defs ("sudo nano /etc/login.defs") and change the value for the UMASK parameter from its default value of 022 to 077.  This value is the eight-bit "complement" of the permission mask, so a umask of 077 means that files and directories with be created with 700 permissions.

---

### Post by mangonels on 2019-12-09
Thanks for the info. It seems to be very diferent to what I was suggested here, allthough I was much more precise with what I REALLY needed: [https://ubuntuforums.org/showthread.php?t=2432733&p=13914876#post13914876](https://ubuntuforums.org/showthread.php?t=2432733&p=13914876#post13914876)

I'll get back to this once I solve the mess I've made.

---

