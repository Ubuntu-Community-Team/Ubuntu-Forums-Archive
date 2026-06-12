---
title: "Change Repo's/ Install Gnome"
date: 2008-03-11
forum: Server Platforms
---

### Post by RandomUsr on 2008-03-11
Want to change my repos on Ubuntu Server 7.10 to include a repo for Ubuntu-Desktop. When I try to

apt-get install Ubuntu-Desktop

---

### Post by freebeer on 2008-03-11
I think your post got cut off or ended prematurely.

You should not need to change your repositories, as I'm pretty sure that the desktop is available in the standard repositories.  The correct command is:

```

sudo apt-get install ubuntu-desktop

```

Note that commands, filenames, etc. are case sensitive.  You had a capital U and capital D.

---

### Post by RandomUsr on 2008-03-12
Ok, couldn't Find Package ubuntu-desktop

---

### Post by Oldsoldier2003 on 2008-03-12
> **RandomUsr said:**
> Ok, couldn't Find Package ubuntu-desktop

post your /etc/apt/sources.list...  and comment out the cd source while you're at it, unless you have physical access to the server its more trouble than its worth.

---

### Post by RandomUsr on 2008-03-13
ok what's the command line from bash to pastebin the output

---

