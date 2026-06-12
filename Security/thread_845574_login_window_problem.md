---
title: "login window problem"
date: 2008-06-30
forum: Security
---

### Post by g1rnz on 2008-06-30
I have hardy heron which was set to auto login but it has stopped working. it now defaults to HUMAN and if I change to another theme it does not save settings. any help will be apprieated

---

### Post by djacidjac on 2008-09-24
Make sure the little radio button is actually selected in the themes window as opposed to your choice just being hi-lighted.

If that's not the problem, maybe this will help;

I had a similar problem; no changes to "Login Window" would save. I deleted /etc/gdm/gdm.conf-custom and then made a copy of /etc/gdm/gdm.conf named gdm.conf-custom. Everything works in "Login Window" now. Just remember that any changes you made in the past will be gone and you'll be left with the default settings.

This took me a while to figure out. I hope this helps.

---

### Post by esmailgad on 2008-09-24
I have the same problem. the login window does not save changes. in the folder etc/gdm i did not find the gdm.config-custom. I can not copy the file in the folder due to permission error. what can I do

---

### Post by cariboo on 2008-09-24
You are getting permission errors because you can not save file in /etc as a regular user. Use:

```
gksu gedit /etc/name_of_file
```

to edit the file as root. To create a file to edit:

```
sudo touch /etc/name_of_file
```

Jim

---

### Post by chemical0815 on 2008-09-26
:-*

---

