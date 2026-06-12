---
title: "no gksu/sudo for network-admin"
date: 2008-02-13
forum: Security Discussions
---

### Post by kordosky on 2008-02-13
Hi,

I run 7.04 on a laptop, essentially as a single user.  I move around from wireless at home, to wired at work, to wireless in an airport, etc.  I'd like to modify my system so that network-admin can be run without having to gksu and type the password.  I thought this sort of thing was controlled by /etc/group, but I don't know which group (if any) I should add my user to.  I am currently in:

kordosky$ groups
kordosky adm dialout cdrom floppy audio dip video plugdev scanner netdev lpadmin powerdev admin

Can anyone help?  Is /etc/group the right way to make my modification?

---

### Post by p_quarles on 2008-02-13
Well, I really don't recommend doing that. The better solution, in my view, would be to set up certain common functions to run without password authentication. That's not really endorsed either, but strikes me as better than getting rid of authentication altogether.

Anyway, here's what you would do:
```
sudo visudo
```
This will bring up the /etc/sudoers file in the default text editor (Nano). Find the line that says:
```
%admin ALL=(ALL) ALL
```
and change it to:
```
%admin ALL=NOPASSWD: ALL
```
The procedure for granting no-password access to specific applications is virtually the same. Let us know if you'd rather go that route.

---

