---
title: "Code after installing ubuntu-desktop"
date: 2008-03-16
forum: Server Platforms
---

### Post by RandomUsr on 2008-03-16
```
xauth: creating new authority file /home/CurrentUser/.serverauth.4850
xauth: /home/CurrentUser/.Xauthority not wrietable, changes will be ignored
xauth: error in locking Authority file /home/CurrentUser/.Xauthority
cannot read from /etc/X11/X Symbolic Link [invalid argument], aborting 
xinit connection refused [errno 111]: unable to connect to xserver
xinit no such process [errno 3]: Server Error
xauth: error in locking authority file /home/CurrentUser/.Xauthority 
```

This is the code i get when running startx
I've added the ubuntu repo's to /etc/apt/sources.list

---

### Post by dmizer on 2008-03-17
just delete the old .Xauthority file.

```
sudo rm /home/[COLOR="Red"]ubuntu-username[/COLOR]/.Xauthority
```
where "ubuntu-username" should be replaced with your actual ubuntu user name.  then retry starting x.

however, you are likely to run into many problems.  the server kernel is not tuned to supporting a gui environment.  if you want a gui on your server, you would be better off to install regular ubuntu and then install the necessary server packages on that.  further, most server configuration is handled at the command line anyway, so there's not much advantage in ease of use to be gained by installing a gui on a pure server.

---

