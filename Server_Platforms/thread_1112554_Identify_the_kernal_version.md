---
title: "Identify the kernal version"
date: 2009-03-31
forum: Server Platforms
---

### Post by Vegan on 2009-03-31
Is there any way from a terminal window to show the version of the kernel that is use at the moment?

It wound be handy to see and help to determine if any problems are cited, which kernel version is at fault.

---

### Post by Cheesemill on 2009-03-31
In a Terminal window, type:
```
sudo uname -r
```
and type your password.

Cheesemill

---

### Post by cariboo on 2009-03-31
You don't have to use sudo, just type the command as a normal user.

Jim

---

### Post by Vegan on 2009-04-04
Thanks that is what I needed, to check that my kernel is up to date.

When I log on I see the Ubuntu version, not the kernel version.

EDIT:

On using the command I see my kernel is not the latest release.

I have 2.6.27-11-server while linix.org sayd 2.6.29 is in production.

---

### Post by Yashiro on 2009-04-05
Don't worry about it. Unless you have a crippling issue just use the kernel from your chosen  distribution.

---

### Post by Bucky Ball on 2009-04-05
You can also check from the desktop with System Monitor->General. Shows what kernel you are currently running at least. :)

---

### Post by Vegan on 2009-04-19
The reason I prefer to check my kernel version is simply to see if a problematic defect has been fixed.

I had to move from 8.04 to 8.10 to fix a conflict between mono and php5.

---

### Post by Wiebelhaus on 2009-04-19
I love sysinfo , not as fast as your asking for but it can't be beat for it's informational output.

just apt-get sysinfo.

---

