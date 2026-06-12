---
title: "User Settings locked in HH"
date: 2008-04-24
forum: Security
---

### Post by Martym on 2008-04-24
So I wanted to backup my home directory and I had the idea of creating a new user so none of the files in /home/<<other user>> would be locked.  When I go into User Settings I am prompted for a password when the window opens everything is greyed out.  

I managed to create a user using adduser but it does not, I am sure, have the necessary permissions.

My main concern is why I cannot create users through the GUI.  I want to make a backup of /home so I can do a fresh install of HH.  

I just wiped out XP on here and have 75GB of space I want to allocate between /home and /

Any ideas why User Settings would be unusable?

---

### Post by bikeboy on 2008-04-24
Have you clicked the button with a picture of a set of keys, labeled 'Unlock'?

---

### Post by Martym on 2008-04-25
No, the unlock button is greyed out too, I get a window before the panel opens asking for my password which I enter then I get the window but I cannot modify any account and only view my own.

---

### Post by Martym on 2008-04-25
Two things, first I tried running the users-admin from a terminal using sudo gksu users-admin and received this message :

```

** (users-admin:30449): CRITICAL **: Unable to lookup session information for process '30449'

```


But more important is this... I am going to save what I can from /home to a network drive and do a clean install, there are just too many odd things happening on here

---

