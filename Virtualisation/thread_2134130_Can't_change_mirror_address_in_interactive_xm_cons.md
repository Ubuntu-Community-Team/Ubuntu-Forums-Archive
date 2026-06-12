---
title: "Can't change mirror address in interactive xm console screen"
date: 2013-04-10
forum: Virtualisation
---

### Post by redmage123 on 2013-04-10
Hello all, 

I am having some trouble installing an Ubuntu VM with Xen.  I start by  using the xen-create-image command with the appropriate
parameters. 

I then run  xm create  <configfile>.  After that, it shows up in the output from xm list. 

When i then try and do an xm console <domain>, it gives me an Ubuntu installation screen (using the ncurses
text graphics tool, I imagine).  Unfortunately, when I go to change the URL of the mirror, I can't edit the highlighted field.
For example, if I select Ireland as the county, it automatically places ie.archive.ubuntu.com in the field.  the process
then fails because it can't connect to the mirror.  i expect this as the field value is  incorrect. 
I want it to point to ftp.heanet.ie/mirrors/ubuntu/ but I can't edit the field at all.  
Anybody know what's going on and how I can fix this? 

Thanks 

 -- redmage123

---

