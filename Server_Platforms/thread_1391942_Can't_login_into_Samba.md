---
title: "Can't login into Samba"
date: 2010-01-27
forum: Server Platforms
---

### Post by fabzzap on 2010-01-27
Ubuntu 9.10, Samba 3.4.0-3ubuntu5.3.

I explore a folder under my home, right click on a folder, select 'Sharing options', tick 'Share this folder', and leave unrticked 'Allow other to create and delete files' and 'Guest access'.

Places->Network->double-click on the local machine icon. A dialog appears. I use my username as username, my password as password, and WORKGROUP as domain. It doesn't let me in, the same dialog keeps appearing.

From a terminal

<username>@<hostname>:~$ smbclient //localhost/<sharename> -U <username>
Enter <username>'s password: <I type my password here>
session setup failed: NT_STATUS_LOGON_FAILURE
<username>@<hostname>:~$

<username>@<hostname>:~$ smbclient //localhost/<sharename> -U <username>
Enter <username>'s password: <nothing, just ENTER>
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.0]
tree connect failed: NT_STATUS_ACCESS_DENIED
<username>@<hostname>:~$

Excerpt from /etc/samba/smb.conf

   workgroup = WORKGROUP
   security = user

What's wrong here?

---

### Post by gobbledigook on 2010-01-27
please post your /etc/samba/smb.conf file :)

---

### Post by Morbius1 on 2010-01-27
> I explore a folder under my home, right click on a folder, select 'Sharing options', tick 'Share this folder', and leave unrticked 'Allow other to create and delete files' and 'Guest access'.
If you're creating a share from nautilus and you leave unselected "guest access" then the server will require a username and password from the client. But you have not created one.

Are you trying to access the server from the client using the servers username and password?

Or are you trying to access the server using the clients username and password?

---

### Post by kamaji792 on 2010-01-27
Have you created the samba password:

```
smbpasswd -a <username>
```

All the best

---

### Post by fabzzap on 2010-01-28
> **Morbius1 said:**
> 
Are you trying to access the server from the client using the servers username and password?

Or are you trying to access the server using the clients username and password?

As said, the server I was trying to access si localhost, that is, the client and the server are the same machine. And I was using my password, since I assumed that having an account also meant having a Samba account. Apparently, it's not like that, you have to add a Samba account by running smbpasswd -a <username> as root.

 smbpasswd -a worked, thank you!

This leads to another question: how to keep the regular /etc/passwd password and the the Samba /etc/smbpasswd in sync without having to change both?

---

### Post by Morbius1 on 2010-01-28
> **fabzzap said:**
> This leads to another question: how to keep the regular /etc/passwd password and the the Samba /etc/smbpasswd in sync without having to change both?

I personally don't know how one keeps them in sync but in a normal network you don't want them to be in sync. 

If the client is accessing the server share by using the server users login username and password then the client knows how to access the server machine itself. In that case you want to make the server user's samba password to be different from the server login password.

If the client is accessing the server share by using the clients username and login password then the server user knows how to access the clients machine itself. In that case you want the clients samba password to be different from the clients local login password.

---

