---
title: "How to get sudo/root access while on non-admin logins?"
date: 2008-08-14
forum: Security
---

### Post by adasiak on 2008-08-14
I'm having no luck performing any sudo functions when I'm not logged into the default account (that created at installation).

Let's say there are three accounts on my home machine: I'll call them "sysadmin" (the default account, supposedly with sudo privileges), "common" (for my family and our guests), and "yourstruly" (my sandbox).

I find that while in "common" and "yourstruly", I cannot access any programs or edit any files that require the sudo password: no installing files, no changing privileges, no system configuration at all.  It seems I must open up a second desktop -- for "sysadmin" only -- and perform the changes there.  It seems to defeat part of the purpose of being the superuser.

Now, I've seen it mentioned that all I have to do is add those other desktops to the admin group.  I tried this (from "sysadmin", natch) and discovered (in "common") that the sudo password required to perform administrative functions is not the original "sysadmin" password, but the "common" password.

(This probably comes as no surprise to regular Ubuntu users, but I'm just coming over from MEPIS, which uses the conventional root login protocol.)

The obvious problem with putting every single user in the admin group is that I don't _want_ everybody to have administrative privileges.  What I've come to expect -- and this is coming from the root login model -- is that I, the administrator, can have a single password that gives me the access I need, no matter whose login I happen to be working in at the moment.

With my current knowledge, it seems I have to choose between inconvenience (always going back to the "sysadmin" desktop) and poor security (giving every user an administrative password).  But that can't be right.  I have a feeling I don't understand the Ubuntu way yet.

Would someone be so kind as to point the way, please?

(Incidentally, I'm running Kubuntu 8.04, with KDE 3.5# (3.59?).)

---

### Post by Stemp on 2008-08-14
```
su sysadmin
```
?

---

### Post by DGortze380 on 2008-08-14
use the command in the last post to change user to one with sufficient privileges to run what you are trying to do. Of course, only works in a terminal. 

Or edit sudoers to give sudo access for the commands/applications you need to the user you need to have them. 

CAUTION: use visudo -f to edit the sudoers file. If you mess up sudoers you will lock yourself out of your own system. There are a number of ways to fix this but as per forums rules I won't post *my* solution.

---

### Post by adasiak on 2008-08-14
Hmmm.

The scenario I envision is something like: I'm writing an OpenOffice.org Writer document in the "common" account, when I realize I need the hyphenization patterns for Slovenian.  I open up KPackage, select openoffice.org-hyphenation-sl, and click on "Install Marked".  I am prompted for a password.

Or...

My daughter, logged in under the "daughter" account, is misusing the computer, so I decide it's time to take away some privileges.  I go to K Menu > Settings > System Administration > User Management, intending to remove her from the games, video, and audio groups.  To make the changes, I click on "Administrator Mode" and am prompted for a password.

Is there any way to set it up so I can provide some password that will let me in?  Or must I choose between (a) using the console to accomplish my administrative tasks and (b) opening up a "sysadmin" desktop to use graphical tools?  That is, is there any way I can use the graphical administration tools in whatever account I find myself in?

---

### Post by Stemp on 2008-08-15
In fact it's PolicyKit, but it's for gnome.
I guess there must be something similar for KDE .
[http://www.ubuntu.com/testing/hardy/beta#head-0c2fe70fd977aeeb919226213631737226fde756](http://www.ubuntu.com/testing/hardy/beta#head-0c2fe70fd977aeeb919226213631737226fde756)

---

