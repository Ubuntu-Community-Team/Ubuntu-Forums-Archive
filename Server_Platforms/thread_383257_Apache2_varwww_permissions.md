---
title: "Apache2 /var/www permissions"
date: 2007-03-13
forum: Server Platforms
---

### Post by ujeezy on 2007-03-13
Hi all,

I'm setting up Apache2 on Dapper and I have two questions about basic permissions/organization: 

1.) I currently have the server's document root set to /var/www, under which I plan to have folders named something like: site1.com, site2.com, etc.

Who should the owner of these folders be? Right now they are owned by root, but I plan for each site to be maintained by a unique user.  What about the group setting, does it matter? 

2.) Do you forsee any problem with setting up these folders with symlinks? For example /var/www/site1.com might point to /home/site1/htdocs

Thanks in advance!

---

### Post by conjur3r on 2007-03-13
1. The user and group owners should be whoever will be managing the site contents.  You, as the administrative root user will always have access to those files/folders anyway.

2. No problems.  Alternatively, you could leave reconfigure the apache virtualhosts to point to the htdocs folder within their home directories.  This would make backing up a little easier as you know all of the content is under /home.  It will also make chrooting easier if you want to go down this path at a later state.

---

### Post by easytec on 2007-09-29
That is too easy.
The Ubuntu Server Edition from Dapper to Gutsy Gibbon support for permission, you do this.
If you are already are using the ROOT account, which can't be accessed directly for security.
Follow these steps:
[LIST=1]
[*]Make sure your an administrator / substitute (super) user.
[*]If you are not, log in to the main account your created when you set up Ubuntu Server Edition.
[*]If you now are, go to the Administration menu in the GNOME System menu.
[*]Setup groups, put yourself into the super user / root group.
[*]Try again, if that fails reboot.
[*]Try again, it should work. If not it is advised you upgrade to Feisty Fawn or Gutsy Gibbon.
[/LIST]
(Sorry if this post is out dated, only Ubuntu Forums stick for ages)!

---

