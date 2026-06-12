---
title: "what happened to ubuntu-sparc desktop"
date: 2006-09-06
forum: Sun Sparc Users
---

### Post by recupero on 2006-09-06
It used to be at [http://cdimages.ubuntu.com/ports/daily](http://cdimages.ubuntu.com/ports/daily)

Have you lost your hope for a desktop and totally friendly install for your workstation?

---

### Post by joshuapurcell on 2006-09-06
Although I haven't followed this version of Ubuntu closely, I have never heard of a desktop version for Sun processors. Here is the link to the server version though:
[http://cdimage.ubuntu.com/ports/daily-live/current/](http://cdimage.ubuntu.com/ports/daily-live/current/)

Is that what you are looking for?

---

### Post by netztier on 2006-09-07
> **recupero said:**
> Have you lost your hope for a desktop and totally friendly install for your workstation?

When I reinstalled my Ultra 2 a few days ago, I did a server install (without LAMP etc) and added **xubuntu-desktop** afterwards. I don't see a problem with doing this with **ubuntu-desktop**, too.

To me, this is an extremely friendly setup process - just a little beyond touch-and-go, but hey, let's leave that to the owners of commodity hardware ;-)

regards

Marc

---

### Post by bhuvan72 on 2006-10-27
Hi,

I have installed sparc server 6.10 on a Ultra 5 but I get an error when i try..

sudo apt-get install ubuntu-desktop

Reading package lists... done
Building dependency tree
Reading state information ... done
E: Couldn't find package ubuntu-desktop

The error is the same for xu/ku buntu...

I had also disabled both DNS server and LAMP during install...

Could you help me out on this as you have done this before..

Thanks,
Bhuvan.

---

### Post by christhemonkey on 2006-10-27
Try doing a:
```
sudo apt-get update
```
First!

---

### Post by bhuvan72 on 2006-10-27
I get

Ign cdrom://ubuntu server 6.10...
Errhttp://security.ubuntu.com edgy-security Release.gpg
Could not connect to security.ubuntu.com:80 , connection timed out...

Its the same with another security site as well..

:(

Bhuvan.

---

### Post by Delta_Farce on 2006-10-29
Edit your sources.list file (/etc/apt) I think.

Comment out the CD repository and open up the http respositories in the file (you can also open Universe and Multiverse).

That should force apt to look at the online repositories rather than the CD, and then it should find the desktop installers.

If apt still refuses to work, try pinging an internet site to make sure you have a working internet connection.

---

