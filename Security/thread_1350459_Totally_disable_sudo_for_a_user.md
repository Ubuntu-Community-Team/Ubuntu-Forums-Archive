---
title: "Totally disable sudo for a user"
date: 2009-12-09
forum: Security
---

### Post by needhelppeeps on 2009-12-09
The first user I created has sudo access and of course I want to leave it that way. The second user I specifically left sysadmin unchecked on. This user cannot use sudo through the terminal but when I click on software or user management, I can still enter the original user's password and make changes. I see no useful purpose for this as I created the second user specifically so he cannot do crap other than browse the web and created files in his homedir. How can I remove the second user's ability to use sudo through the first user's password?

---

### Post by memilanuk on 2009-12-09
Try the Ubuntu Community Docs...

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by needhelppeeps on 2009-12-09
Ya I looked at that before, unfortunately it doesn't answer the question as to why ubuntu behaves unexpectadly with regard to allowing software to be added by a non-sudo user.

---

### Post by memilanuk on 2009-12-09
Did you check to see if they were somehow added to the /etc/sudoers file?

Did you check to see what groups they are a member of?  If you have 'su' installed they may be able to 'su' to root using the original users password and then do what ever they want from there (as they are effectively 'root' at that point).

Monte

---

### Post by aysiu on 2009-12-09
The behavior you describe should not work.

If it does, it should be reported as a bug:
[https://bugs.launchpad.net](https://bugs.launchpad.net)

---

### Post by sisco311 on 2009-12-09
> **aysiu said:**
> The behavior you describe should not work.

If it does, it should be reported as a bug:
[https://bugs.launchpad.net](https://bugs.launchpad.net)

It's not a BUG, it's policykit feature.

---

### Post by aysiu on 2009-12-09
> **sisco311 said:**
> It's not a BUG, it's policykit "feature".
I can't tell if you're being sincere or sarcastic.

---

### Post by SuperSonic4 on 2009-12-09
Perhaps your second user is specified in /etc/sudoers. Find out with ```
sudo visudo
``` as someone with root access or root

---

### Post by sisco311 on 2009-12-09
> **aysiu said:**
> I can't tell if you're being sincere or sarcastic.

Sorry.

The OP is talking about the authentication window that pops up when you press the *unlock* button in Users and Groups or Network Manager.

This applications are using policykit to authenticate you as an admin user.

policykit allows you to authenticate yourself as an admin by entering the admin user's password even if you are logged in as non-admin user.

This is not a security risk since you have to know the admin user's password, which means that you can login as the admin user or simply su to the admin account and use sudo to run applications as root.

---

### Post by jeremyswalker on 2009-12-09
From what I am understanding of the issue, he is able to gain administrative privileges using the first user's password while logged in as another user. If this is the case, aysiu is right. It's a bug.

EDIT: I retract this statement, if the OP is referring to the scenario offered by sisco311. I can't say as I entirely agree with the logic behind this "feature", though.

---

### Post by needhelppeeps on 2009-12-09
Yes, that is what happens. As the second user I cannot type sudo and run a command with the first user's password. However, through the graphical interface of user manager, software center, etc I can type in the first user's password. I didn't see any usefulness here as I don't ever want the second user to add or del anything. Is there a way to turn that off for the specific user?

 I was also a little irked that the home directories were not secured. I totally didn't expect that a default would allow everyone to access my files (although at least it didn't seem as though they could delete anything, I'd just assume no one saw that salaries xls!). Fortunately, that was easy to fix. Overall, I do want to say ubuntu has been very impressive with regards to performance, finding hardware, and ease of use, despite a few defaults I'd like to see changed with regards to privacy.

---

### Post by bodhi.zazen on 2009-12-09
I do not think that is a bug or a security flaw, it is a "feature" in that the admin application has been written for convenience, allowing user 1 to run an app as an administrator (root) without having to either log the second user off or log the first user on.

You may not like it, but the second user can not run an application as an administrator without knowing the password, and if they know the password they can either su to the admin user in a terminal or log in as an admin, either way it is not really a security hole, IMO.

---

### Post by sisco311 on 2009-12-09
Don't tell the admin password to the second user. :)

To prevent the authentication window from popping up remove *PolicyKit Authentication Agent* from the startup applications (System -> Preferences -> Startup Applications).

To force users to be member of the admin group before they can use *su*, edit the  /etc/pam.d/su file, uncomment the **auth       required   pam_wheel.so** line and append it with **group=admin**:
```
auth    required    pam_wheel.so    group=admin
```

To force users to be member of the admin group before they can use *policykit*, add the above mentioned line to the /etc/pam.d/polkit-1 file.

Backup the files before editing!

---

### Post by aysiu on 2009-12-09
> **bodhi.zazen said:**
> I do not think that is a bug or a security flaw, it is a "feature" in that the admin application has been written for convenience, allowing user 1 to run an app as an administrator (root) without having to either log the second user off or log the first user on.

You may not like it, but the second user can not run an application as an administrator without knowing the password, and if they know the password they can either su to the admin user in a terminal or log in as an admin, either way it is not really a security hole, IMO.
So have they also made it so that if you drag a file from your home directory to a system folder and can password-authenticate as a sudoer, you can actually drag it there without being told you don't have permission and aren't the owner of the folder?

---

### Post by ibuclaw on 2009-12-09
To provide some closure for the OP (and a solution).

You can use PAM as a security shield to prevent it from working successfully - even using your own password.

```
sudo nano /etc/pam.d/polkit-1
```
And put at the bottom of the file:
```
auth required pam_succeed_if.so user ingroup admin
```
Now authentication via PolicyKit will only work if you are **logged in** as a user from the **admin** group. Even if you use the correct password - it will still deny access.

Regards
Iain

edit: looks like sisco311 beat me to it - blasts and drats to leaving for lunch. :D

But - I agree with Bodhi, if a user knows the password, they can just su into your account and do stuff from there. PolicyKit or no PolicyKit...

---

### Post by bodhi.zazen on 2009-12-09
> **aysiu said:**
> So have they also made it so that if you drag a file from your home directory to a system folder and can password-authenticate as a sudoer, you can actually drag it there without being told you don't have permission and aren't the owner of the folder?

I have not seen that, but, honestly I almost never use Gnome, and whey I sys admin I prefer a terminal :twisted:

I will try it later tonight.

---

### Post by ibuclaw on 2009-12-09
> **aysiu said:**
> So have they also made it so that if you drag a file from your home directory to a system folder and can password-authenticate as a sudoer, you can actually drag it there without being told you don't have permission and aren't the owner of the folder?

No - at least. That wasn't the behaviour I received dragging from /home/iain to /opt.

If I were to 'gksu nautilus /opt' though... that allows it without problems.

---

