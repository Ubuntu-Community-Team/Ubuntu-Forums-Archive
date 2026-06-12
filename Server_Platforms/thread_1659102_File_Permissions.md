---
title: "File Permissions"
date: 2011-01-03
forum: Server Platforms
---

### Post by idny on 2011-01-03
Hi, 
I've been reading to help a question i have but need further assistance.

I have a server (10.10) running a samba share.
The server uses ssh for remote connection where i configure it from.
I want to be able to lock down certain folders and files.

The is a directory in my samba share that i only want 1 user to see in the windows side of things.
So basically when a user connects to the share via windows, they can only see certain files in the share, whereas another user can connect and see everything depending on the user name

How can this be done,

Thanks

---

### Post by woodman231 on 2011-01-03
Managing those things are usually made easier with a program called [Webmin]("http://www.webmin.com/download.html").

You may also want to look in to using this [PDC Turnkey solution]("http://www.turnkeylinux.org/domain-controller").  I have used this and been able to do exactly what you are proposing to do.

Thanks,
Sean W.

---

### Post by idny on 2011-01-06
Well i managed to fix it in a slightly different way.

I have simply allowed all users to be able to see all the directorys (windows side) but when connecting to the server it prompts for a login. The login it then checked against the server, and the samba/users config. If they are not the owner then they cannot open the directorys on either windows or linux side :)

Files for set to **# sudo chmod 700** (given owner full control and nothing for others)
To assign the owner i did: **#sudo chown [username]:[group] [directory]**

in case anyone needs those :)

---

