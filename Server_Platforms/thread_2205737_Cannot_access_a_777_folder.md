---
title: "Cannot access a 777 folder"
date: 2014-02-15
forum: Server Platforms
---

### Post by Pragmateek on 2014-02-15
Hi,

I'm facing a really strange issue: a user, "jenkins", cannot access a folder in another user's home, though, in despair, I've changed its rights to 777. (I know this is bad, really bad)

I'm not a Linux guru but I've used it for years, and this ugly trick has always worked, so seems like things are changing.

So I have two questions:
1) How such a thing is possible: 777 is no more synonym of "open-bar"?
2) What's the right way to give my "jenkins" user read access to the mentioned folder?

Some additional information:
- "jenkins" is a special user created by the Jenkins integration server
- the folder is the folder used by Dropbox 
- there is a symlink owned by root to the folder

To check if any of the above points could be significant I've created a folder near to the other and symlinked it the same way, and the "jenkins" user can access it.
So there is something special with the Dropbox folder that I'm missing. :/

I'm using Ubuntu Server 13.10.

Thanks in advance for any help.

---

### Post by CharlesA on 2014-02-15
Check the parent folder's permissions.

---

### Post by Pragmateek on 2014-02-15
Thanks for your answer Charles.

The "jenkins" user can access the home folder of the other user.
It can even access a folder in the home if the correct rights are set, this is what I've tested to ensure the issue is with the Dropbox folder only.

I guess there is more to rights management than the goold old "rwx" system but I have no idea what.

I've read that Ubuntu supports **ACL** so I've tried to play with "**setfacl**" without any success so far, but maybe I'm not using it correctly.

---

### Post by CharlesA on 2014-02-15
I've never messed with acl lists before, but maybe this will help.
[https://help.ubuntu.com/community/FilePermissionsACLs](https://help.ubuntu.com/community/FilePermissionsACLs)

---

### Post by SeijiSensei on 2014-02-16
In order for one user to see files in another's home directory you must have the following permissions:

/home = 755 (root read/write/exec, group/other read execute)
/home/user = 755 unless both users belong to a common group in which case 750 would work

Ubuntu by default comes with a /home that meets these requirements, but other distributions enforce stronger privacy and make all home directories 700, letting only the user access the folder.  (This is the only acceptable security model for shared servers.  On desktops, 755 might be acceptable.)

---

### Post by Pragmateek on 2014-02-16
I modified the ACLs using "**setfacl**" though it seems useless as 777 is equivalent to "**other::rwx**".
When I displayed the ACLs with "**getfacl**" I had "**user:jenkins:rwx**" meaning that "jenkins" should have full access to the folder, if I understand well.
It didn't change anything.

But good news this morning, after restarting the box, I can now access the folder with the "jenkins" user!
This is kind of crazy as in 6 years of Linux usage I've never had to restart the OS to fix things, whereas restarting is the de-facto best-practice on Windows. :/

Don't know if this is an issue with Ubuntu Server itself or Dropbox, or both, but as of now it works...

I'll let this thread open and if in 3 days all is still correctly up I'll close it.

Thanks Charles for your help.

---

### Post by Pragmateek on 2014-02-16
Thanks SeijiSensei for the info.

All is OK:
- /home is 755
- /home/user is even 775 (don't know why as I don't remember having changed it myself)

As the problem fade away this morning seems like this may not be a "normal" rights issue that can be solved by tweaking the good old "rwx" rights or the ACLs, unless Ubuntu has been changed in such a way that some changes only take effect when rebooting (ala Windows) :/

---

### Post by thnewguy on 2014-02-16
You mentioned doing a reboot to fix the problem. Is it possible the jenkins user was logged in while you were tinkering with permissions/ownership, either at your console or somewhere else? I have found that new permissions are not always granted at the time, but will be delayed until the user is fully logged out and logs in again. It's frustrating, but seems the user needs to reload their permissions to be able to access new files/folders. A reboot would effectively log them out and back in again.

---

### Post by Pragmateek on 2014-02-16
Hum very interesting thnewguy.

I've not myself started any graphical or console session with the "jenkins" user, but maybe the Jenkins server uses some tricks that prevent the immediate enforcement of rights.

---

### Post by SeijiSensei on 2014-02-17
When you login and start the GUI, the session will have the permissions granted to the user and group at that time.  Changing permissions after that will not take effect until you log in again.  You don't need to reboot, just log out and log back in again.

---

