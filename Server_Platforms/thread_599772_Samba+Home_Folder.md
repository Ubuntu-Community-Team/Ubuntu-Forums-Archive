---
title: "Samba+Home Folder"
date: 2007-11-01
forum: Server Platforms
---

### Post by jdm2 on 2007-11-01
I'm setting up a samba sever for my school.  Two teachers there want one and they want to try linux so I said I would help them.  Right now I just using a test machine to figure out everything I need to do.  The only thing right now that I want to know is when the user access the samba sever, they see everybody folder, but they only can access their own.  That is how I want it.  The thing is that when they access it from xp they also see the config files and everything else that is hidden in the home folder.  I don't want them to be able to see that at all.  Any suggestion.  I can go any way with this as long as it is easy and deals with samba.  Thanks for the help.  
jdm2

---

### Post by prezbedard on 2007-11-01
This might be one answer from the windows side. If they have access to folder options that lets them view hidden files and folders you might have to disable that. However it may be that windows can't read what is hidden and what is not on a Linux file share. but you can try and see if that is the case but fiddling with hidden files and folders under folders options in XP.

---

### Post by jdm2 on 2007-11-01
I will try that and see if that works.  Thanks for the help.  
jdm2

I have been looking and I have this config file:

[homes]
comment = Home Directories
browseable = no
writable = yes
valid users = %S
read only = no
create mode = 0600
directory mode = 0700

logon home = \\rch01\%U // This tells where is the home directory for the user

hide files = /*.pst/

What does the Hide files do?  Thanks for the help.

---

### Post by prezbedard on 2007-11-06
I believe it is telling the system to mask files with a .pst extension (outlook personal folder) as hidden

---

### Post by Limpan on 2007-11-06
It seems to me that you should be able to use something like
```
hide files = /.*/
```
and if you then tell your XP clients to not show hidden files they might go away.

EDIT: Did a quick google and it seems that the right way to do it is to write this
```
hide files = /.*/*.pst/
```
Then all files that start with a dot and all files that end with .pst will be marked as hidden.

---

### Post by MJN on 2007-11-06
You likely want to use the **veto files** option instead - it functions the same as hide files but completely stops the viewing and accessing of files regardless of the client 'hidden file' setting. See the smb.conf man page for details and, in particular, the caveat about the deletion of directories containing veto'd files.

Mathew

---

### Post by jdm2 on 2007-12-11
Thanks for the help.  I got it to work.  The problem was that the user account on the windows pc that I was using had show hidden files enable.  
jdm2

---

### Post by MJN on 2007-12-11
The veto directive effectively sidesteps any client setting hence you may wish to use it if the users are able to enable/disable the client setting at will.

Mathew

---

### Post by jdm2 on 2007-12-11
Thanks for the suggestion MJN.  I will look into that.
jdm2

---

