---
title: "copying files from root to VM"
date: 2012-05-25
forum: Server Platforms
---

### Post by batb on 2012-05-25
[COLOR=#1F497D][FONT=&quot][/FONT][/COLOR][COLOR=#1F497D][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#1F497D][FONT=&quot]1) I am trying to copy files into a user's shell directory that I have created on my Virtual Machine, but it doesn't allow me to do a copy/paste into the user's directory.[/FONT][/COLOR]
[COLOR=#1F497D][FONT=&quot]2)  What is the correct way for a root user to create a directory for data  and document files that multiple users can access as the need arises?[/FONT][/COLOR]

---

### Post by darkod on 2012-05-25
If you are talking about a folder with R/W permissions for all, I usually do:

sudo chmod a+rw /path/folder

That gives read/write to all.

---

### Post by batb on 2012-05-25
> **darkod said:**
> If you are talking about a folder with R/W permissions for all, I usually do:

sudo chmod a+rw /path/folder

That gives read/write to all.

thanks Darko, that worked

---

