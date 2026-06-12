---
title: "I want to remove gnome from my server. What will happen?"
date: 2010-07-09
forum: Server Platforms
---

### Post by tsash on 2010-07-09
It's my first experience with *nix OS.
I needed server for following purposes:
Fileserver on samba
Internet gateway
VPN gateway
DNS
I installed ubuntu 10.04 server edition, but wasn't able to work without graphical environment. So I installed gnome. I installed and tweaked samba and bind9 and network manager and all works fine for now. 
So I have a question. What will happen if I remove gnome? Especially with network manager? 
And what will I gain in performance. It's important because I have only an old Dell Optiplex 150 (933/512/10) serving as a server.

---

### Post by CharlesA on 2010-07-09
The iffy part is network manager, but you can always reconfigure the ip address manually. IIRC that's the only problem area. You can remove gnome and go from there.

I suppose you could make it not start gnome automatically but not remove it completely, which would save some resources (minus disk space).

---

### Post by The Real Dave on 2010-07-09
Most of the stuff you would have configured anyway through the terminal. None of that would change. NetworkManager is the only thing you'll have to fix. [This]("http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/") will help you configure your IP address.

You'll also want to make sure you have ssh installed so you can access the server's terminal remotely.

```
sudo apt-get install ssh
```

[Here]("http://linuxexpresso.wordpress.com/2010/05/29/completely-remove-ubuntu-desktop/")'s a nice way to getting rid of Gnome completely by the way. This will uninstall everything installed by the ubuntu-desktop package.

---

### Post by spynappels on 2010-07-09
Are you using Network Manager to administer your VPN endpoint functionality, and are you running the server as a router? You say it is an Internet gateway. These may make it a little tricky if you have no confidence in CLI, but there is plenty of help here on the forums if you do want to take the plunge.

---

### Post by tsash on 2010-07-12
Thank you all for replies. I'll probably try not to start gnome automatically.

---

