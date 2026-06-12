---
title: "Print Server"
date: 2010-04-22
forum: Server Platforms
---

### Post by Cyphor on 2010-04-22
Hi there. Before I start, id just like to let you know that im still quite new to Linux, but am liking it so far :)

I have Ubuntu 9.10 server installed as a VMware client, and I'm planning to replace our Windows print server with a linux one. I have managed to get the server joined to our Windows domain and Active Directory through Likewise-open by following the guide on the Ubuntu website.

I have installed Samba and CUPS to manage the printer sharing. Ive managed to add a network printer in CUPS and share it. When I connect to the server through Windows, it doesn't appear?

We have nearly 1500 users on site along with 35 network printers currently connected to our windows print server. Can someone point me in the right direction and possibly give me some guidance on the best way to move from windows to linux on this issue?

Many thanks!

Cyphor

---

### Post by ICEB3AR on 2010-04-22
There is an Option in Samba:
(/etc/samba/)smb.conf
```
...
browseable = yes
...
```
And also in Cups there is an Option
(/etc/cups/)cupsd.conf
```
...
Browsing On
BrowseOrder ...

``` 

Have you set up this? Are the Browse-Rules in Cups right?

---

