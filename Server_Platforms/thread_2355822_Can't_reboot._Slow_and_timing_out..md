---
title: "Can't reboot. Slow and timing out."
date: 2017-03-17
forum: Server Platforms
---

### Post by Gottier on 2017-03-17
I ssh into the server. Install sqlite3 and php7.0-sqlite3, then standard apt upgrade.

```
sudo apt update
sudo apt install sqlite3 php7.0-sqlite3
sudo apt upgrade
sudo reboot
```

I get a message like this:

```
sudo reboot
Failed to start reboot.target: Connection timed out
See system logs and 'systemctl status reboot.target' for details.
```

So, I do as it recommends:

```
sudo systemctl status apache.service
Failed to get properties: Connection timed out
```

Or if I try to restart apache:

```
sudo service apache2 restart
Failed to retrieve unit: Connection timed out
Failed to restart apache.service: Connection timed out
See system logs and 'systemctl status apache.service' for details.
```

All of this very slow to respond. I'm not at the physical location, and nobody is actually there. If I try to restart the server but it won't restart then that is very bad. What can I do? I need help.

Edit: This is my recent stuff in apt install log:

```
Start-Date: 2017-03-14  03:19:09
Commandline: /usr/bin/unattended-upgrade
Upgrade: libicu55:amd64 (55.1-7, 55.1-7ubuntu0.1), libevent-2.0-5:amd64 (2.0.21-stable-2, 2.0.21-stable-2ubuntu0.16.04.1)
End-Date: 2017-03-14  03:19:11

Start-Date: 2017-03-15  12:40:51
Commandline: /usr/bin/unattended-upgrade
Remove: linux-headers-4.4.0-31-generic:amd64 (4.4.0-31.50), linux-image-4.4.0-62-generic:amd64 (4.4.0-62.83), linux-image-extra-4.4.0-62-generic:amd64 (4.4.0-62.83), linux-headers-4.4.0-31:amd64 (4.4.0-31.50), linux-headers-4.4.0-62:amd64 (4.4.0-62.83), linux-headers-4.4.0-64:amd64 (4.4.0-64.85), linux-image-4.4.0-64-generic:amd64 (4.4.0-64.85), linux-image-extra-4.4.0-64-generic:amd64 (4.4.0-64.85), linux-headers-4.4.0-62-generic:amd64 (4.4.0-62.83), linux-image-4.4.0-31-generic:amd64 (4.4.0-31.50), linux-headers-4.4.0-64-generic:amd64 (4.4.0-64.85), linux-image-extra-4.4.0-31-generic:amd64 (4.4.0-31.50)
End-Date: 2017-03-15  12:41:50

Start-Date: 2017-03-16  21:32:05
Commandline: apt install sqlite3 php7.0-sqlite3
Requested-By: gottier (1000)
Install: php7.0-sqlite3:amd64 (7.0.15-0ubuntu0.16.04.4), sqlite3:amd64 (3.11.0-1ubuntu1)
End-Date: 2017-03-16  21:32:09

Start-Date: 2017-03-16  21:32:50
Commandline: apt upgrade
Requested-By: gottier (1000)
Upgrade: grub-legacy-ec2:amd64 (0.7.9-0ubuntu1~16.04.2, 0.7.9-48-g1c795b9-0ubuntu1~16.04.1), libxml2:amd64 (2.9.3+dfsg1-1ubuntu0.1, 2.9.3+dfsg1-1ubuntu0.2)
End-Date: 2017-03-16  21:32:53
```

---

### Post by Gottier on 2017-03-17
Looking around the internet, it seems that if a dbus service is restarted, it may not automatically restart the login service. I had to do this to get back to normal:

```
sudo systemctl --force --force reboot
```

---

