---
title: "Administrative questions"
date: 2010-10-14
forum: Security
---

### Post by robdashu on 2010-10-14
I might like to do a fresh install of ubuntu;  Is there a simple way of doing a disk image copy to an external hard drive, and then restoring?  Or any kind of simple copying of files, say, from root with all subdirectories to the external drive?  Isn't there a /prefs directory somewhere that I could use to bring a fresh install up to date with all of the preferences I've set over the course of a year?

A possibly related subject - when logging in, several requests are made by the system for keyring passwords, which I don't know, so I close the dialog box and go on.  It seems as if nothing is lost on my part for not supplying these keyring passwords.  Can you refer me to a clear explanation of their functioning?  Also password management  in general.  Is password management best done from shell script, i.e., interactively in a terminal window with ubuntu line commands, or is there a good GUI tool?

These forums have so many threads that are related to very specific software units, and I have some questions on a conceptual level.  Any suggestions for learning and reference [besides reading manuals!]?

---

### Post by cariboo on 2010-10-14
> **robdashu said:**
> I might like to do a fresh install of ubuntu;  Is there a simple way of doing a disk image copy to an external hard drive, and then restoring?  Or any kind of simple copying of files, say, from root with all subdirectories to the external drive?  Isn't there a /prefs directory somewhere that I could use to bring a fresh install up to date with all of the preferences I've set over the course of a year?

There are several backup utilities in the repositories, my preferences are clonezilla for hard drive imaging, and rsync for daily backups. Clonezilla is a Live CD, that creates a partition, or full disk image, that can be updated without having to create a new image every time you run it. Rsync does differential backups, after the first time it is run, it only backs up files that have changed.

> A possibly related subject - when logging in, several requests are made by the system for keyring passwords, which I don't know, so I close the dialog box and go on.  It seems as if nothing is lost on my part for not supplying these keyring passwords.  Can you refer me to a clear explanation of their functioning?  Also password management  in general.  Is password management best done from shell script, i.e., interactively in a terminal window with ubuntu line commands, or is there a good GUI tool?

The keyring should only ask you for a password if you have auto login set, otherwise it uses your login password. The keyring stores your passwords and keys for such things as wireless, ssh keys and gpg keys. You can access the keyring by going to System->Preferences And Encryption Keys

> These forums have so many threads that are related to very specific software units, and I have some questions on a conceptual level.  Any suggestions for learning and reference [besides reading manuals!]?

It depends on what you want to know. There are many help resources available. A good place to start is the [Linux Documentation Project]("http://tldp.org/")

---

### Post by HermanAB on 2010-10-15
Howdy,

You could use netcat:
[http://www.aeronetworks.ca/netcat-howto.html](http://www.aeronetworks.ca/netcat-howto.html)

---

