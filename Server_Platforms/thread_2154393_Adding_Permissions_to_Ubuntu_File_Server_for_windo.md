---
title: "Adding Permissions to Ubuntu File Server for windows users"
date: 2013-06-14
forum: Server Platforms
---

### Post by Ready2DropWin on 2013-06-14
I have a ubuntu 10.4 file server, on a windows domain/network. As it stands now, when users navigate to the server \\servername they have full access to any or all files. I was wondering if there was a way to add permissions, or ask for credentials for folders or files? I have found this example on the forums, but I am not sure if it will work the way that I want. Thanks in advance for the help.

Example I found:

```

gksu geany /etc/samba/smb.conf

```

```


[sharedfolder] path = /home/your_username/sharedfolder available = yes valid users = your_username read only = no browsable = yes public = yes writable = yes Save and close. Then restart Samba:

```

```


sudo restart smbd

```

---

### Post by SeijiSensei on 2013-06-14
[http://www.samba.org/samba/docs/using_samba/ch09.html](http://www.samba.org/samba/docs/using_samba/ch09.html)

---

