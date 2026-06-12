---
title: "Cacti problem with host_status"
date: 2006-07-11
forum: Server Platforms
---

### Post by Bjoeboo on 2006-07-11
Well Thanks to the help here I got Cacti installed :D and I'm trying to add my Linksys router to "Devices" but when I click "go" in the web ui after entering my device it complains:
[FONT="Courier New"][SIZE="3"]Undefined index: host_status in /usr/share/cacti/site/host.php on line 730[/FONT][/SIZE]

I checked that line of code it reads:  [FONT="Courier New"][SIZE="3"]if ($_SESSION["sess_host_status"] != $_REQUEST["host_status"]) { [/FONT][/SIZE]

What am I doing wrong?:confused:

---

### Post by Linus Torvalds on 2006-07-11
I have that same problem.  Usually this place is more helpful.  So much in fact that other distros come here for answers. Maybe its an SD thing.. sigh.

---

### Post by DSn0wMan on 2006-08-21
I don't understand why nobody wants to help Linus. After all, we owe him quite a bit for comming up with the kernel. =P

---

### Post by Linus Torvalds on 2006-08-23
no worries.

---

### Post by flickerfly on 2006-10-13
There is a solution at [http://forums.cacti.net/post-76194.html](http://forums.cacti.net/post-76194.html), but the fix is in the backports repository also so opening that up is a bit easier to fix the problem. ymmv

---

