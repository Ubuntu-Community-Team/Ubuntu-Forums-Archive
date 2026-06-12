---
title: "Lastlog and faillog."
date: 2009-12-15
forum: Security
---

### Post by zozza on 2009-12-15
I have been learning about the log files.

For some reason the lastlog command does not seem to work.  My last log in is listed like this:

zozza           tty1                      Mon Nov 16 14:16:08 +0000 2009

Also, when I log in as another user it appears like this:

zozza2                                     **Never logged in**

And when I deliberately mess up the passwords and run faillog no information is generated.

Any ideas why?

Thanks.

---

### Post by kiranmurari on 2010-01-04
[SIZE=2]There is a bug **"lastlog shows 'Never logged in' (in last/wtmp my logins visable)"** filed in launchpad for this. [https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/271049](https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/271049)[/SIZE]
[SIZE=2]
Instead of lastlog and faillog, you can use last and lastb.
last - displays list of last logged in users from /var/log/wtmp file
lastb - displays list of bad login attempts from /var/log/btmp file[/SIZE]  [SIZE=2]
[/SIZE]
       ```
[SIZE=2]user@desktop:~$ last
user    pts/1        10.10.43.16      Mon Jan  4 14:25   still logged in
user    pts/0        :0.0             Mon Jan  4 14:24   still logged in
user    tty7         :0               Mon Jan  4 14:23   still logged in
user    pts/0        :0.0             Mon Jan  4 11:04 - 14:22  (03:18)[/SIZE]
[SIZE=2]wtmp begins Mon Jan  4 11:04:17 2010[/SIZE]
       [SIZE=2]
[/SIZE]
[SIZE=2]user@desktop:~$ sudo lastb
user    tty7         :0               Mon Jan  4 14:23 - 14:23  (00:00)[/SIZE]
[SIZE=2]btmp begins Mon Jan  4 14:23:46 2010[/SIZE]
```[SIZE=2]

[/SIZE][SIZE=2]Hope this helps.[/SIZE]

[SIZE=2]Regards,
Kiran[/SIZE]

---

