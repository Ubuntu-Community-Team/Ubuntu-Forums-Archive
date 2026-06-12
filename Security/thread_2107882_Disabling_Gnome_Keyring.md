---
title: "Disabling Gnome Keyring"
date: 2013-01-23
forum: Security
---

### Post by Lunestic on 2013-01-23
Whenever I do svn commands, an annoying prompt asking for gnome keyrings comes up.  Another thing, I can just put random entries and after two tries it will let me pass.  This is annoying and I want to disable it.  Here is the terminal result:

```
tim@ubuntu:~/cs225/hw0$ svn blah
WARNING: gnome-keyring:: couldn't connect to: /run/user/myName/keyring-Hmbiuz/pkcs11: No such file or directory
Password for 'Default' GNOME keyring: 
Password for 'Default' GNOME keyring:
<normal results>

```

I have disabled SSH Key Agent and GPG Password Agent in my Desktop Session Preferences.  Any ideas on how to disable it?  Thanks

---

### Post by hectorh302 on 2013-11-13
Same problem here.

---

### Post by houstonbofh on 2013-11-15
[https://wiki.archlinux.org/index.php/GNOME_Keyring#Manage_using_GUI](https://wiki.archlinux.org/index.php/GNOME_Keyring#Manage_using_GUI)

Just change it to blank.

---

### Post by rousseau09 on 2013-11-19
Similar, might help 
[How to fix WARNING: gnome-keyring:: couldn't connect to: /root/.cache/keyring-yNzNuC/pkcs11: No such file or directory?]("http://www.blackmoreops.com/?p=425")

---

