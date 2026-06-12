---
title: "FTP not responsive unless server logged in?"
date: 2011-02-01
forum: Server Platforms
---

### Post by Narkboy on 2011-02-01
Hi all - I'm a total Linux noob, but I've needed a working development server for a while so I've put together an old celeron box running Ubuntu Server 10.10.

The box runs fine, as does the Apache and MySQL servers, even if they did take a little while to fine tune!

The problem I have is that vsftpd doesn't respond unless I'm logged on locally or via putty. As long as a local user is logged in, it's fine. If I try to connect when noone is logged in, then the connection times out waiting for the server message, and thereafter I have to login and stop / restart the vsftpd to make it work again.

I'm not sure if the vsftpd is set to run on boot or on login and I have no idea how to check. Vsftpd is set to allow only local users, of which there is only one - so I can't check if it would work with any user logged in.

Any thoughts?

---

### Post by rudelgurke on 2011-02-01
Did you took a look in the logfiles ?

Also a small overview over your configuration would be nice to see what might be wrong.

---

### Post by Narkboy on 2011-02-02
Ok - vsftpd conf:

```

local_enable=YES
anonymous_enable=NO
write_enable=YES
listen=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES

```

Everything else is commented out.

I've looked through the vsftpd log and it lists connections and file actions, but nothing else. I'm assuming that vsftpd works but isn't actually loaded at boot, but at login - is that possible and how would I check that?

Thanks for your help! :)

---

### Post by rudelgurke on 2011-02-02
Do you maybe start it through Xinetd ? If so, enable it to run in standalone mode and directly run it through init (/etc/init.d/vsftpd start) or by service vsftpd start

---

