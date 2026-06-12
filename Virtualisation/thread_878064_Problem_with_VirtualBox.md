---
title: "Problem with VirtualBox"
date: 2008-08-02
forum: Virtualisation
---

### Post by MasterNetra on 2008-08-02
NVM solved

---

### Post by johns747 on 2008-08-02
I just saw your note, and had a similar issue when I installed virtualbox on a new 8.04 installation.  

You need to be sure the vboxdrv file has proper permissions.  First, change to your dev directory  (cd /dev).  Second, as a host user (ie, as sudo), change the file permissions on vboxdrv as follows (at prompt, enter the following:  sudo chmod 777 vboxdrv   ) This will change the permissions on the vboxdrv file to allow read, write and execute privileges for all users.  After you hit enter, you will be prompted for your password.  Then give vb a try.  

This assumes you have a standard installation, and that vboxdrv is in your dev directory.  I also assume you are using 8.04, although the file permission issue is true for 7.10, in my experience.  Finally, I am a 64 bit user (both under 7.10 and, now, under 8.04), although this should not affect the file permission issue.

---

### Post by tuxxy on 2008-08-02
You can change your thread prefix to solved, this shows people before clicking on the message that its solved.

---

### Post by MasterNetra on 2008-08-02
When i looked into the users section of the group i had saw my user name there and thought i was in but i forgot with ubuntu you gotta make sure its checked..

---

