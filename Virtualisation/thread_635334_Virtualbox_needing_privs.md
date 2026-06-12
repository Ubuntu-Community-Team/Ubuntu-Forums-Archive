---
title: "Virtualbox needing privs"
date: 2007-12-08
forum: Virtualisation
---

### Post by snick512 on 2007-12-08
```


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
```

What would be the easiest way going about this? Never had any problems with write privs before..

---

### Post by ubukool on 2007-12-08
Hi,

go to system -->Administration---->Users and Groups

click on 'manage groups'

Scan down the list, there should be a group called 'vboxusers'. If there is, double click on it and make sure that your username is ticked so that you are a member of the group. If there is no group, create one by clicking on 'Add Group', typing vboxusers in the group name field and making sure that your user name is ticked so that you are a member. Then, log out and log back in again. When you a start your virtual machine, everything should work!

Good luck! :)

---

### Post by snick512 on 2007-12-08
thank you.

Now i can run XP for those simple needs lol

---

### Post by vandorjw on 2008-06-11
How could I do this on Xubuntu?
-------------------
Found it,

Applications---> System --->Users and Groups ---> then Manage Groups.
I had to "unlock" the application before it became useful...


Thanks + Cheers

---

### Post by Victormd on 2008-06-11
You can do this from the terminal, just type
```
sudo adduser $USER vboxusers
```
and you should be good to go. Don't worry about the user name becase $USER will automatically output your user name.
You should get something like this:
> Adding user cc7gir to group vboxusers
Done.
Or whatever your user name is in xubuntu...

---

