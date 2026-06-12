---
title: "/var/log/syslog......Permission Denied?"
date: 2011-03-01
forum: Server Platforms
---

### Post by auzzie2112 on 2011-03-01
im trying to access /var/log/syslog but keep getting the error permission denied.

i need this file for troubleshooting.

thanks

---

### Post by headvampyre@hotmail.co.uk on 2011-03-01
Hi, ive just messaged you on this, sorry for not getting back so quick. Just run:

sudo gedit /var/log/syslog

from terminal :)

---

### Post by trundlenut on 2011-03-01
how are you trying to access it?

---

### Post by headvampyre@hotmail.co.uk on 2011-03-01
Through terminal using gedit. You need root privelages to access the file, which is why you use sudo.

---

### Post by matt_symes on 2011-03-01
Hi

Try adding yourself to the [syslog] *(as pointed out below i should have typed adm. Brain and fingers not connected tonight)* group then you will not require sudo.

From the menu: Applications->Accessories->Terminal

Enter into the terminal

```
sudo useradd -a -G adm <your user name>
```

where <your user name> is, obviously, your user name.

Kind regards

---

### Post by nerdy_kid on 2011-03-01
just please DONT use sudo for gui apps, it can cause your .ICEauthority file to become owned by root, which means you won't be able to log in without fixing it from the commandline.  Use gksu instead, i.e. 
```

gksu gedit /var/log/syslog

```

---

### Post by hawkmage on 2011-03-01
The /var/log/syslog file has group ownership by adm and is readable by group so you should be able to read it as long as you are member of the adm group.  If I remember correctly the Administrative account you create when you install Ubuntu is part of the adm group .

---

### Post by auzzie2112 on 2011-03-03
thanks everyone but just a little more info on my problem....
 
OS: Ubuntu Linux _Server_ 10.10 (so no gui)
 
also i am using the admin account i created when i installed the system.

---

### Post by hawkmage on 2011-03-03
What do you get when run the commands "groups" and "ls -l /var/log/syslog"

---

### Post by trundlenut on 2011-03-04
What happens if you do:

```
cat /var/log/syslog
```
and
```
nano /var/log/syslog
```

---

