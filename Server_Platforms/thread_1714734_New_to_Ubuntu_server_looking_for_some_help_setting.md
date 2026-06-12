---
title: "New to Ubuntu server looking for some help setting it up (read for more info)"
date: 2011-03-25
forum: Server Platforms
---

### Post by CGfreak102 on 2011-03-25
So looking to fill up some spare time learning Ubuntu servers.

What I'm looking to do is setup a file server so i can access it from a remote location. 

I was working off the tuts that Ubuntu provides but i find that they lack a person explaining what the command does.  So i was wondering if someone could let me know what i would need to setup to reach that goal i said above.

now to tell you about the situation;
Basically i got a cable modem that leads to a router and then to the system i want to install the OS on. everything is DHCP, i can go static but i want to stay away from that unless its needed.
going to use Ubuntu 10.10
For file server i have installed Samba and got it to work on a local network only, looking to do the remote connection now.

I would try searching myself, but i have no clue what to search for to install or a phrase that describes what im trying to do.

Thanks,
-CGfreak102

---

### Post by a9k3d on 2011-03-26
Probably the first thing you should work on is getting remote console access via SSH.

You are going to need the test server at a fixed internal IP otherwise how is your router going to contact the server (known as port forwarding on most routers).

So try installing ssh-server on the server, get used to working with the console. Learn ssh port forwarding - you can do amazing things with port forwards and ssh socks proxy.

Now a warning - opening up your server to the world means within 20 minutes your server will be probed for easy cracks. SSH ports always get pounded on once discovered. Usuall a dictionary attack will start within days looking for username followed by password attempts on the discovered usernames. I recommend using a DSA key with SSH and forbidding password access in /etc/sshd_config. Also install fail2ban to block repeated crack attempts.

Have fun but check your /var/log/auth.log to see crack bots trying to get in.

---

### Post by Z.K. on 2011-03-26
If you use samba which you probably will you may find that it does not automatically startup when your server boots.  I just had this problem.  I have not had time to figure out the real problem yet, but if you put
```

restart nmbd
restart smbd

```
in the /etc/rc.local it will startup when your server boots.

Make sure your firewall is up and running too 
```
ufw status
```
from a terminal will tell you if the firewall is active.  It is not on the image I downloaded.

:)

---

