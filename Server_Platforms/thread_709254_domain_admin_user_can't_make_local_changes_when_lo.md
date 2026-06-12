---
title: "domain admin user can't make local changes when logged in"
date: 2008-02-27
forum: Server Platforms
---

### Post by beaker15 on 2008-02-27
Hi

I need the administrators group on my samba domain to be able to make local changes on my Windows XP clients. At the moment, if i want to install something or make changes i have to log out of the domain and log on as a local user. Any ideas how to solve this?

---

### Post by astrotech226 on 2008-02-27
If the domain is set up correctly, anyone in the "Domain Admins" group should be able to make local changes to the computer.  *UNLESS*, there has been some restrictions put in the local security policy.

Here's a few things to check.  If you fire up usrmgr.exe on the Windows computer, check the the "Domain Admins" group and make sure the user you are logging in as is in fact in that group.

Then, on the XP computer, right click My Computer and click Manage.  Under System Tools, open up Local Users and Groups.  Click Groups below that.  Double click Administrators in the right pane.

You should see a member of the local Administrators group for YOURDOMAIN\Domain Admins.  If you don't, that's the problem.  If you add that group to the local Administrators group, you should be all set!

---

### Post by beaker15 on 2008-02-28
great stuff,  thanks for all the help!
:guitar:

---

