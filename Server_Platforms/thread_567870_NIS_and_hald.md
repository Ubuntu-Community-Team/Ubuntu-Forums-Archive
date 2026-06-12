---
title: "NIS and hald"
date: 2007-10-05
forum: Server Platforms
---

### Post by anthonyf38 on 2007-10-05
Hi, 

We are responsible of a linux room for an engineering school, and this room must be installed automatically and simply (because it is a large lack of time)

An automatic install has been realised with all the possibility offered by ubuntu, but we have a last problem : NIS and HALD.

So, these computer must be used very simply (to discover linux) so the users will not mount their pendrive with a command... 
When the users are logged in with NIS, these users on the computer does not belong to the group plugdev, cdrom and so on... So their pendrives are not mounted automatically.

If I manage the password file as this :
+user1:::::
+user2::::: ...
and add these users to the right groups, it works fine.
I can script it to be up to date of the users (by downloading a list of users) and update it at every start of the computer.

But is there another solution ? A solution that allow me to add only a line +:::::: to my passwd file and make it simplier ? (because if I script it I have also to script something to keep the list of users up to date, download it, update the computers when they starts... It's a little bit complicated for a network that is not connected to the internet and so we have no problem of "hacking".

Thanks a lot.

Anthony Fleury

---

### Post by Arne_M on 2008-05-08
take a look at nsswitch, there you can specify which information you want to get from nis.
You can also add such a +:::: line to group

Look at the man page for nsswitch to see how to use it.

you can test the functionality with 

```
getent group
```

---

