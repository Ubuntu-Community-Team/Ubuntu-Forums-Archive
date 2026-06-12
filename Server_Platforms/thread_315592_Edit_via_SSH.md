---
title: "Edit via SSH"
date: 2006-12-09
forum: Server Platforms
---

### Post by vr.crawler on 2006-12-09
i can`t edit anything on a server, conected with ssh!
it returns me this on everything i try to edit: 

bsd@ubuntu-server-http:~$ sudo edit /etc/apache2/apache2.conf
Password:
Warning: unknown mime-type for "/etc/apache2/apache2.conf" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"
bsd@ubuntu-server-http:~$

what is this?](*,)

---

### Post by keithweddell on 2006-12-09
Try sudo gedit if the server has a desktop.  Otherwise try sudo nano or sudo vi.

Keith

---

### Post by vr.crawler on 2006-12-09
yes it works now.
thanks.

---

### Post by tturrisi on 2006-12-09
or sudo editor

---

