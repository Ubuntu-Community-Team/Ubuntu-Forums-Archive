---
title: "How do I stop a standard user from using an admin password in Gnome to do admin tasks"
date: 2024-04-29
forum: Security
---

### Post by vbgf3 on 2024-04-29
Hi,

This is regarding Ubuntu 24.04, but should apply also to 22.04. 

Currently user2 - a standard user, can edit a file owned by root using gnome-text-editor, and then save it successfully by typing in the admin account's password into the Gnome dialog 

I have checked, this is not sudo capability. I have voided user2 of all rights to use sudo in the sudoers file. 

Where can I add a rule to deny user2 of ever (using the admin password) accomplishing anything admin-nish in Gnome ?  A standard user should Forever remain a standard user, regardless of what password she 
possesses. 

I will add 2FA later to restrict user2 from logging to the admin account even if she has the correct password. 

Thanks

---

### Post by TheFu on 2024-04-30
user2 needs to NOT be a member of sudo/admin groups.

BTW, there isn't any "admin account" password.  There's a username, usually with a uid of 1000, that was created during installation that is placed into the sudo group.  That's the only difference between a user who can perform sudo and one that cannot.

However, there are lots of ways someone could screw with this.  Setting a password for the 'root' account is one.  Setting a password for the sudo group is another.  Default ubuntu installs don't have a password set for root, which effectively prevents anyone direct access.  But if I wanted admin privileges on a system and I already had an account there, it wouldn't be hard to quickly add myself to the sudo group, if I could trick the main admin into looking away for a bit (say 10 seconds).  For local accounts, membership in the sudo group is clearly listed in the /etc/group file.  There should be just 1 username there, at the end of the line. This is the first username created during install time.  If someone isn't that user or a member of that group, then they cannot know just a password and gain elevated privileges without someone screwing up as described.

---

### Post by vbgf3 on 2024-05-02
Hi

I found my answer. It requies 2 steps.

A. Use visudo and add this line to deny user2 from doing anything using sudo  

user2 ALL=(ALL) !ALL


B. Add a deny all user2 actions rule file in this directory (using any file name) : /usr/share/polkit-1/rules.d/ 

polkit.addRule(function(action, subject) {
  if (  subject.user == "user2") {
    return polkit.Result.NO; // Deny all actions for user user2
  }
});

Note: This will slow down Gnome, but it will stop user2 from doing anything that needs additional permissions.

To Improve this: First run the action you want to forbid and then run jounalctl to find the error message string.
Then do a locate 'polkit' and you will see the rules.d directory and action directory. The rules.d directory is where you code your rule and place it, 
as shown above. 
The action directory holds the policy files, which contains the error message string you are interested in. Use grep to find the policy file with your string.
Then inside that policy file you will find "action.id == "... " This is the action you want to control.
Now go to the rules.d directory and read the existing rules files to see the syntax of how to construct a rule file specifying the action you want to control.

Once you narrow down the action.id's that you want to deny, Gnome will run fast again.

---

