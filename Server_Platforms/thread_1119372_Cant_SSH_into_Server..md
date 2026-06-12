---
title: "Cant SSH into Server."
date: 2009-04-07
forum: Server Platforms
---

### Post by redonwhite on 2009-04-07
](*,)  I have a server with a fresh install of ubuntu 8.10 LAMP/SSH installed.  When i type

```
ssh servername@ipaddress
```

I get

```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
**----I DELETED THIS PART NOT SURE IT MATTERS----.**
Please contact your system administrator.
Add correct host key in /home/bob/.ssh/known_hosts to get rid of this message.
Offending key in /home/bob/.ssh/known_hosts:1
RSA host key for **---IPADDRESS---** has changed and you have requested strict checking.
Host key verification failed.
 
```

---

### Post by Iowan on 2009-04-07
I usually enter ```
ssh username@servername
```or (since my local DNS is offline) ```
ssh username@server-ip-address
```

---

### Post by Stupendoussteve on 2009-04-07
> **redonwhite said:**
> ](*,)  I have a server with a fresh install of ubuntu 8.10 LAMP/SSH installed.  When i type

```
ssh servername@ipaddress
```

I get

```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
**----I DELETED THIS PART NOT SURE IT MATTERS----.**
Please contact your system administrator.
Add correct host key in /home/bob/.ssh/known_hosts to get rid of this message.
Offending key in /home/bob/.ssh/known_hosts:1
RSA host key for **---IPADDRESS---** has changed and you have requested strict checking.
Host key verification failed.
 
```

I'm guessing that the previous install at this IP address was also running ssh...

Your system is protecting you from an attack. You need to remove the key from ~/.ssh/known_hosts and it will save the new one when you connect again.

---

### Post by redonwhite on 2009-04-07
> **Stupendoussteve said:**
> I'm guessing that the previous install at this IP address was also running ssh...

Your system is protecting you from an attack. You need to remove the key from ~/.ssh/known_hosts and it will save the new one when you connect again.

How exactly would go about deleting that key out of that folder.  I couldn't seem to find the folder. :oops:

Also another dump question.  Did this occur because I didn't set up a static IP address to the server yet?  

Thanks for your replies.

---

### Post by Stupendoussteve on 2009-04-07
The folder is a hidden folder. If you are using gnome you would go to the home folder and then View > Show Hidden Files (or hit Ctrl + H). You should be able to find .ssh after that.

It happens because the system stores a key for the IP address that it is at. If another computer uses that IP address the system sees that the key is changed, and warns you that it may be faking the machine you expect it to be.

---

### Post by redonwhite on 2009-04-07
> **Stupendoussteve said:**
> The folder is a hidden folder. If you are using gnome you would go to the home folder and then View > Show Hidden Files (or hit Ctrl + H). You should be able to find .ssh after that.

It happens because the system stores a key for the IP address that it is at. If another computer uses that IP address the system sees that the key is changed, and warns you that it may be faking the machine you expect it to be.

Awesome response thank you very much.  I most definitely have to figure out how to get a static IP address on my server now.  :p . Ive been holding out while I experiment with the server, but I think now is the time.  =).

Thanks again!

---

