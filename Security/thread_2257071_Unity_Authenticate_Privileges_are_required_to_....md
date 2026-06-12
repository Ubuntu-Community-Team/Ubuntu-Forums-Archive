---
title: "Unity Authenticate: Privileges are required to ..."
date: 2014-12-16
forum: Security
---

### Post by charlieott on 2014-12-16
Hi.  When I installed Ubuntu i created a user called 'ccri' which is the 'admin' account with sudo access.

I have enabled LDAP authentication using pam modules via sssd and now my users can log in on any machine which is intended.

I have also given sudo to some of the LDAP accounts by just adding the account name/group to the sudoers file in etc.  So these users can install software with apt, etc...

However, even though I am logged in with my ldap account (cott) and I am able to perform sudo, whenever using the gnome/unity applications like Printers or the Ubuntu Software Center, i am prompted for the password for the original user during install.  See attached screenshot.

My question is...

How do I change the username used in the authenticate dialog so that other users can authenticate w/ their own credentials??

---

### Post by charlieott on 2014-12-16
so i'm wondering if 'polkit' is related? [https://www.google.com/search?q=polkit-gnome-authorization+ubuntu&espv=2&biw=1339&bih=667&source=lnms&tbm=isch&sa=X&ei=8dWQVMCfMdWOsQTHqIHQBA&ved=0CAcQ_AUoAg](https://www.google.com/search?q=polkit-gnome-authorization+ubuntu&espv=2&biw=1339&bih=667&source=lnms&tbm=isch&sa=X&ei=8dWQVMCfMdWOsQTHqIHQBA&ved=0CAcQ_AUoAg)

---

### Post by charlieott on 2015-01-07
Still havent found the solution to this.  Admittedly I havent been looking that hard.  Wondering if the 'sudo' group in /etc/group is parsed? since the username prompting is the only user in the sudo group.

---

### Post by charlieott on 2015-01-27
still an issue for me.

---

