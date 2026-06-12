---
title: "remove credentials in Remote Desktop Viewer"
date: 2009-12-14
forum: Security
---

### Post by danielsender on 2009-12-14
Hi,

I would like to remove the credentials (passwords) of some previous connections. I tried removing the history (~/.local/share/vinagre/history), but it didn't do it. Since this machine is used by other people I wouldn't like to have them logging into these hosts. Thanks.

Daniel

---

### Post by RedSingularity on 2009-12-14
Is there a folder hidden called vinagre?

---

### Post by danielsender on 2009-12-14
I only found the one I mentioned before. I don't know if there any app within gnome that takes care of that or is something hidden within the Remote Desktop Viewer stuff.

Daniel

---

### Post by RedSingularity on 2009-12-14
Well you can look for files with the find command..........

find /home -name vinagre*

---

### Post by danielsender on 2009-12-14
I found .gconf/apps/vinagre/%gconf.xml, so what should I do now?

Daniel

---

### Post by RedSingularity on 2009-12-14
Remove that file too.  (Along with any others that come up in that list.)

---

### Post by danielsender on 2009-12-14
No avail. The program still knows the passwords.

Daniel

---

### Post by RedSingularity on 2009-12-14
If you delete all the config files it shouldnt remember it.  If you want you can remove it from your system then do a search through the whole root directory like this.......

sudo find / -name vinagre*

When you delete files do this search again and again till it returns no results.

---

### Post by danielsender on 2009-12-14
I found the way to do it. The application is seahorse and can be accessed as Applications->Accessories->Passwords and Encription Keys . Then you can delete those entries or deny acces to selected programmes. Anyway, thanks for your time.

Daniel

---

