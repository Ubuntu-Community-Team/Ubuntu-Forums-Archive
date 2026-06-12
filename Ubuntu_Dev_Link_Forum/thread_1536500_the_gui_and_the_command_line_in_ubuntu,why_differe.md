---
title: "the gui and the command line in ubuntu,why different?"
date: 2010-07-22
forum: Ubuntu Dev Link Forum
---

### Post by zonelight on 2010-07-22
As we know that there are various syscalls in linux kernel,the sys_mkdir(),sys_open(),sys_fchmodat(),sys_fchownat().Then,we can intercept it .
Today i do a work about it,catch the chown syscall.
The file is "myfile",the owner is "my".We can use the command "chown root myfile",then,"myfile"'s owner will change to root.After i used strace for a look,i found the syscall in this situation is sys_fchownat.I catch it,every time i use the chown command to change the owner of "myfile",then a printk will into log.
But,when i use the gui environment,right-click "myfile"->properties->permissions,then change the own by mouse.Nothing happened....
So,the gui of gnome do not invoke the syscall?

---

