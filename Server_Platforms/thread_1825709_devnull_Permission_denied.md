---
title: "/dev/null: Permission denied"
date: 2011-08-15
forum: Server Platforms
---

### Post by orlandodawn on 2011-08-15
Hi - I am running Ubuntu Linux 11.04 server on a headless server and recently ran some updates. 

Since then whenever I ssh in I am getting "/dev/null: Permission denied" (unless I ssh as root)

From a bit of googling the permissions on the null folder are being changed by something. I can remedy the issue by running: 

sudo chmod ugo+rw /dev/null

However every time I reboot it comes back. 

How can I find out what is changing it and how can I resolve this on a permanent basis. 

(The updates I were running were to try to sort a different problem with Virtualbox)

and I thank the community for any help here. 

M[URL="https://10.0.1.254:10000/cron/edit_cron.cgi?idx=9"]
[/URL]

---

### Post by disabledaccount on 2011-08-16
The simplest solution is to put chmod in some startup script. There are many ways to do it, f.e. using system V init scripts:
- copy <devnull_fix.sh> to /etc/init.d (don't forget to make it executable)
- run: update-rc.d <devnull_fix.sh> defaults

For details look to >man update-rc.d

---

### Post by dinu90 on 2011-08-16
the /dev/ dir is recreated each time your OS boots so most probably something changed after the upgrade which creates the /dev/null file with the wrong permissions

Can you provide a full list of upgraded packages?

[**java tutorials**]("http://www.java-forums.org/java-tutorial/")

---

