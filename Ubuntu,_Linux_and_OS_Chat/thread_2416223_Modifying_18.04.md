---
title: "Modifying 18.04"
date: 2019-04-07
forum: Ubuntu, Linux and OS Chat
---

### Post by natchezjohn on 2019-04-07
Because of my own peculiar desires I have installed the standard 18.4 installation on my desktop pc and added the Mate desktop. Now I have the system I REALLY want. 
I have a 64gig  Laptop dual booting Windows 10 and would like to install the same on it. My question is: If I delete the ubuntu default desktop (to reclaim disk space) will it have any undesirable effect on the remaining Mate desktop? If no, how do I uninstall the default desktop?
I will appreciate any help you can give me.

---

### Post by ajgreeny on 2019-04-07
The simple answer is that you can't easily remove the default desktop from an install.

Often users imagine that removing the **ubuntu-desktop** package will remove all the packages that are included with that DE but unfortunately that is not the case; ubuntu-desktop is simply a metapackage, ie a list of all the packages that are required to be installed to make the default ubuntu DE, and removing it does just that, it removes that single package only.
A few more packages may also be removed if you then run ```
sudo apt autoremove
``` but the full list will certainly not go.

This is always one of the problems of adding a second DE to an existing one; you end up with duplicate applications for file-manager, text-editor, terminal, etc etc, and whilst that should not use too much disk space unless you are really low in available space, it can make for confusing menus and could potentially cause changes to some system files that might be a problem.

If your 64G laptop with Windows 10 does not yet have any *ubuntu OS installed alongside Windows I suggest you download the iso file of [Ubuntu-mate]("https://ubuntu-mate.org/download/") and install that rather than the ubuntu install with added mate DE.

---

### Post by natchezjohn on 2019-04-07
OR - is UbuntuMate equal in all ways to default 18.04 with Mate desktop? IGNORE THIS POST - I HAD NOT SEEN ajgreeny's RESOnse

---

### Post by natchezjohn on 2019-04-07
Thank you I suspected Ubuntu-Mate was the way to go

---

### Post by natchezjohn on 2019-04-07
EXCELLENT! Just what I wanted. Thank you ajgreeny

---

### Post by ajgreeny on 2019-04-07
Great news! Glad you like it.

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

