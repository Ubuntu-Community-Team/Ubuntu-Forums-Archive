---
title: "How do I  make a limited account?"
date: 2012-05-19
forum: Security
---

### Post by natgab on 2012-05-19
I would like to set up a **limited permission user account**, similar to what a guest account has on a normal installation.  

My friend has a slim Compaq PC, with only 512MB RAM, so I am hoping to move him over from Windows XP to Lubuntu.  Since its only for Internet / Music, I think he would be fine without Windows.  Since its older, Winodws XP + Virus scanner slows it down.  Lubuntu on the other hand flies :P

I set up the PC with the Administrator account and then made a user account for him to use.  But I don't know how to put more limits on the user account.  I have done this on my Mac, but it has a control panel that lets you tick off individual applications to block.  I just want to know if there is a way to allow my friend to install applications but not change system settings and have it automatically install updates.

I have always used my own Ubuntu computer as a single user, so I have no experience setting up users in Linux.

---

### Post by Lisiano on 2012-05-19
You can do auto updates and the "Install software" part but I'm not exactly sure on the last one.

For auto updates see here [https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

For permissions to use apt and dpkg [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

But if you want my opinion, I wouldn't give him the permissions to install software. This way he can't mess up by deleting something system important or installing something wicked. It would be better to sit down with him and talk through all the uses he will have and install all the software he will need, then use SSH (If possible) to install stuff or TeamViewer/VNC.

Note, the default standard user is equivalent to a guest user but unlike guest, can save files and can try to run admin stuff, by try I mean the user will receive a prompt to enter a password from a local admin, while guest won't see one and silently fail.

---

### Post by natgab on 2012-05-19
I will check and see if I did it right.  Because I think I might have made his user account as Administrator too.  So a normal user cannot install any applications?  I will try and make another normal user on the PC and see if they are both the same.  And see if they can install applications or not.

It might be a good thing to not let him install apps, since it only has a 40GB HD, so it might fill up if he accidently add more than one music player or something like that.

---

### Post by Lisiano on 2012-05-19
Indeed. A standard account will prompt the user to enter the password from an admin account, meaning unless he knows your password, he won't be able to install anything.

---

### Post by natgab on 2012-05-22
> **Lisiano said:**
> Indeed. A standard account will prompt the user to enter the password from an admin account, meaning unless he knows your password, he won't be able to install anything.

Yeah, setting up the standard account will work.  He is fine not having to worry about updates.  I went and added GIMP and full Libre Office instead of the Abiword / Gnumeric and he should be fine.

I will just go and add in any apps if he needs them manually, don't want to fuss with the remote log-in stuff.

---

### Post by Lisiano on 2012-05-23
If you are satisfied with the end result, please mark the thread as solved in the thread tools above.

---

