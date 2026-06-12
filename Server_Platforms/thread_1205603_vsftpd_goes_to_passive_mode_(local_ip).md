---
title: "vsftpd goes to passive mode (local ip)"
date: 2009-07-06
forum: Server Platforms
---

### Post by artheus on 2009-07-06
Hi!

When I'm trying to connect to my ubuntu-server using an FTP client on an external computer (external from the servers lan), the ftp client can't connect..

I've done a little research on it.. and I've come to the conclusion that there is no problem with the router, port forwarding. It's when the server turns to passive mode. It starts using the server lan-ip instead of the wan-ip.

```

Connecting to 123.456.789.10:21...
227 Entering Passive Mode (192,168,0,100,125,175)

```

How can I config the vsftp to keep the wan-ip for the passive mode?

Cheers,
Artheus

---

### Post by John Cheng on 2009-07-06
> **artheus said:**
> Hi!

When I'm trying to connect to my ubuntu-server using an FTP client on an external computer (external from the servers lan), the ftp client can't connect..

I've done a little research on it.. and I've come to the conclusion that there is no problem with the router, port forwarding. It's when the server turns to passive mode. It starts using the server lan-ip instead of the wan-ip.

```

Connecting to 123.456.789.10:21...
227 Entering Passive Mode (192,168,0,100,125,175)

```

How can I config the vsftp to keep the wan-ip for the passive mode?

Cheers,
Artheus

According to the man page for vsfptd ([http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html)), you can set the pasv_address explicityly (as an IP address) or as a hostname. Do these settings work?

---

