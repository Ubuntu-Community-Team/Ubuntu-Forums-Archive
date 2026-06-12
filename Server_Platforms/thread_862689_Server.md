---
title: "Server"
date: 2008-07-17
forum: Server Platforms
---

### Post by Tux.Ice on 2008-07-17
Ok, i already have 4 computers on a Windows workgroup at a small company and i am going to set up a printer and file server that will only have access to a ethernet connection and a power plug. do i want to use ubuntu, or ubuntu server. i want to be able to remotly access apache, and do backups on it, and of course store files, ALL FROM A WINDOWS COMPUTER. is this possible? and how do i do it?

---

### Post by Sef on 2008-07-17
Moved to server platforms.

---

### Post by TSS on 2008-07-17
> **Tux.Ice said:**
> Ok, i already have 4 computers on a Windows workgroup at a small company and i am going to set up a printer and file server that will only have access to a ethernet connection and a power plug. do i want to use ubuntu, or ubuntu server. i want to be able to remotly access apache, and do backups on it, and of course store files, ALL FROM A WINDOWS COMPUTER. is this possible? and how do i do it?

You are going to want to use Ubuntu Server.  Here is a general guide that should be helpful: [http://doc.ubuntu.com/ubuntu/serverguide/C/](http://doc.ubuntu.com/ubuntu/serverguide/C/)

In terms of access, ssh and sftp should serve you well.  You can just use PuTTY and PSFTP for your needs ([http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)).

---

### Post by cozmicharlie on 2008-07-17
Yes you can do it in Ubuntu.  From your description I would say all you need is Ubuntu server as long as you are comfortable using a command line rather than a gui (headless server).  You can set up a lamp server during the set process for Apache and ssh for file sharing.  If you choose ssh for file sharing (I perfer it over Samba) then you can set up Tunneleir in Windows (it's free) and open ssh in Ubuntu.  I am sure others will have good suggestions for you also.

Good luck!

---

### Post by windependence on 2008-07-17
Sure, an Ubuntu box with SAMBA, CUPS, and Apache loaded would work great. Probably more stable than the rest of your network. 

I will warn you, there is no GUI installed on the server version by default. You should have no problem administering this from PuTTY on a windows box though. If you need a crutch, you could use WebMin, accessible from the outside.

-Tim

---

### Post by richiewrt on 2008-07-18
You may also want to look at webmin to administer the server once you have it up and running. It gives you a nice web frontend for administering your server.

---

### Post by Tux.Ice on 2008-07-18
it wont be a web server though, the Apache is for a PHP script on file management. ok, i will be installing a gui, in the end i would like to go through windows My network places and access the server's Home, and drag files into the server, can this be done.

---

### Post by Tux.Ice on 2008-07-18
also, in a web browser i want to be able to type in the servers static IP, 192.168.0.198 (were behind a router) and have the router forward that to the servers 127.0.0.1, so i can see the apache.

---

### Post by cozmicharlie on 2008-07-18
> **Tux.Ice said:**
> also, in a web browser i want to be able to type in the servers static IP, 192.168.0.198 (were behind a router) and have the router forward that to the servers 127.0.0.1, so i can see the apache.

No problem - you can set up a Dynamic DNS [http://www.dyndns.com/](http://www.dyndns.com/).

---

### Post by Tux.Ice on 2008-07-19
well i dont think we need DynDNS because the server wont be accesable outside of our workgroup.

---

### Post by cozmicharlie on 2008-07-19
> **Tux.Ice said:**
> well i dont think we need DynDNS because the server wont be accesable outside of our workgroup.

You are correct - all you need to do is bind it to that address and you are good to go.

---

### Post by Tux.Ice on 2008-07-19
what packages are included in the server edition, that arent in the normal ubuntu, and to install GNOME i would do an 

```
aptitude install gnome
```

as root right?

---

### Post by cariboo on 2008-07-19
If you are going to install a gui any how why not install xbuntu and then add the server packages after install. To do this once you have things set up the way you want open up a terminal and type:

```
tasksel
```

Choose Lamp and hit OK.

This is just my personal opinion, but it is kind of useless to install a gui on a headless server, unless you are going to use remote desktop software to access it.

To use apache I would just add the name of the server to my hosts file eg:


```
127.0.0.1	localhost
127.0.1.1	intrepid
192.168.1.200	willy
192.168.1.1	router
```

That way you don't have to enter the ip address everytime you want to access the server web page or even if you install webmin all you have to do for example to access webmin type:

```
https://servername:10000
```

JIm

---

