---
title: "permission Denied event with root user"
date: 2015-03-31
forum: Virtualisation
---

### Post by tiencruise on 2015-03-31
Dear all,

I am facing with the problem when trying to install the application. Here is the command i type in terminal

> Directory: /home/tiencruise/Desktop/HDB_CLIENT_LINUX_X86_64
Tue Mar 31 17:09:39 ICT 2015
tiencruise@tiencruise:~/Desktop/HDB_CLIENT_LINUX_X86_64> su root
Password: 
tiencruise:/home/tiencruise/Desktop/HDB_CLIENT_LINUX_X86_64 # ls
client               hdbinst   hdbuninst    LABEL.ASC  SIGNATURE.SMF
filelist.clientinst  hdbsetup  instruntime  PRODLABEL
tiencruise:/home/tiencruise/Desktop/HDB_CLIENT_LINUX_X86_64 # ./hdbinst
cannot exec /home/tiencruise/Desktop/HDB_CLIENT_LINUX_X86_64/instruntime/sdbrun: Permission denied

Can you help me!

Thanks

---

### Post by TheFu on 2015-03-31
Only a guess, but fix the permissions on sdbrun to have execute.

---

