---
title: "ssh works from windows laptop but not from other ubuntu desktop"
date: 2008-06-20
forum: Server Platforms
---

### Post by SimbaSpirit on 2008-06-20
ok here's my setup.

I have 2 computers running the most up to date ubuntu (hardy, all updates intact), and a laptop running vista.

I follow the tutorials on the internet about how to ssh from terminal.

ssh username@servername:24 (have it on port 24 because other computer uses 22)

ssh username@192.168.1.99
ssh username@<external ip>

My router is using dd-wrt, and has ports 22 and 24 properly forwarded.

Server 1 can't ssh Server2, or the other way around.
My vista laptop using PuTTY can access both of them.

Am I using the command incorrectly?
To change the ports I edited the "port:" in ssh_config and sshd_config

Thanks,
-SS

---

### Post by Sef on 2008-06-21
Moved to Server Platforms.

---

### Post by windependence on 2008-06-21
To ssh on a different port:

```
ssh -p 24 name@server_or_ip
```

To start the ssh server on a different port:

```
sudo /usr/sbin/sshd -p 24
```

The above will not survive a reboot, you will need to put it in your startup script.

HTH

-Tim

---

