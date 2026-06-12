---
title: "Starting Samba4 as DC daemon at boot"
date: 2013-09-01
forum: Tutorials
---

### Post by Toxic64 on 2013-09-01
If you installed Samba 4 from git using my previous tutorial ( [http://ubuntuforums.org/showthread.php?t=2146198](http://ubuntuforums.org/showthread.php?t=2146198) ),
you might have noticed that it doesn't contain a self starting script so you have to start it manually everytime you reboot your server.

Here is how to do to have it starting automatically:

First create a **samba4.conf** file in **/etc/init**:

```
sudo nano /etc/init/samba4.conf 
```

Add this Upstart script inside:

```
description "SMB/CIFS File and Active Directory Server"
author      "Jelmer Vernooij "
start on (local-filesystems and net-device-up)
stop on runlevel [!2345]
expect fork
normal exit 0
pre-start script
	[ -r /etc/default/samba4 ] && . /etc/default/samba4
	install -o root -g root -m 755 -d /var/run/samba
	install -o root -g root -m 755 -d /var/log/samba
end script
exec /usr/local/samba/sbin/samba -D
```

Save and exit

then execute those commands:

```
chmod 755 /etc/init/samba4.conf
chmod +x /etc/init/samba4.conf
```

Restart

Now your samba server should start automatically at reboot.

---

### Post by JnPson on 2013-09-01
Thank you. I needed this short tutorial.

---

