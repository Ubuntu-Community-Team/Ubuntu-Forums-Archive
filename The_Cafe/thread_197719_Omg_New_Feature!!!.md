---
title: "Omg New Feature!!!"
date: 2006-06-16
forum: The Cafe
---

### Post by Engnome on 2006-06-16
Well I noticed that when the enter your password dialog comes up you now have several choices. Like: Save password for this session and save in keyring (what is that?) 

Oh boy I gotta calm down :rolleyes: New stuff that just appears gets me kinda excited.

---

### Post by beercz on 2006-06-16
[QUOTE=Engnome]Save password for this session and save in keyring (what is that?)[/QUOTE]
Keyring is a repository for all your saved passwords to access network servers etc....  You can save multiple passwords for multiple services in your keyring.  When you revisit a service with a previously saved password in your keyring, you just need to enter your keyring password.

Makes remembering passwords easier - you only need remember one - your keyring password.

btw this is not a new feature, is has been around for a while now.

---

### Post by Engnome on 2006-06-16
[QUOTE=beercz]
btw this is not a new feature, is has been around for a while now.[/QUOTE]

Really? just saw it today.

Btw my password doesnt work with that new password dialog:confused: :mad: :( 

Fortunately it doesnt come up all the time, sometimes the old one appears and then my password works.

Think I'm gonna reinstall dapper today. Gotten like 3 big problems in less than 12 hours.:sad:

---

### Post by woedend on 2006-06-16
thats not a new feature, it's a "different" feature.  I personally like it(debian uses it).  It's the difference between gksu and gksudo.  Basically, if you use sudo account like is default with ubuntu, you get the cheezy "Grant Authorization" box and type the user account password in whenever you need to run an app with root permissions.  However, if you instead use a root account, you get the dialogue you described, where you may save the password for the session. 
In ubuntu, gksu is linked to gksudo, the the gksu command is worthless by default. There is a setting that affects this.  Open gconf-editor and look at apps->gksu
There is a checkbox that says sudo-mode
by default it's checked, which means gksu uses gksudo basically.  If you uncheck it, you get the option to save the password(but you also need to have enabled a root password).  I'm betting yours isn't checked?
 So why your password doesn't work - because it needs the root password, not the user password.

---

### Post by Engnome on 2006-06-16
Hmmm I dont have a checkbox there. The value is 0 though. Chaning it to 1 doesnt help either.

Btw my user passsword and root password is the same. (I'm the only one using this laptop)

Oh well I can alwas do gksudo synaptic and it works. When trying gksu I get the new dialog and it doesnt work, getting sh: /usr/X11R6/bin/xauth: No such file or directory after the command. Is that my problem?

Should I file a bug report or is this my fault? havent used gconf bfore this.

---

