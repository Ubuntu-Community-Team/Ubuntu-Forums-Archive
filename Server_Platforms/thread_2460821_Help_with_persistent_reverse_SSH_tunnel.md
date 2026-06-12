---
title: "Help with persistent reverse SSH tunnel"
date: 2021-04-19
forum: Server Platforms
---

### Post by xpl01t on 2021-04-19
Hi everyone. 
I'm having some issues with reverse SSH tunnel on Ubuntu server. 
The situation is as follows:
1) I have two computers running Ubuntu: one is a dedicated server w/ static IP, and another one is a RaspberryPi behind NAT, which I'm going to use to talk to some equipment. Let's call them "*server*" and "*pi*"
2) Due to some bureaucratic constraints I cannot use *autossh* on *pi*, so my only option to run a persistent tunnel is a *systemd* service. It looks something like this:

**reverse_tunnel.service**
```

[Unit]
Description="Reverse SSH tunnel"
After=network.target


[Service]
ExecStart=ssh -fN -o ServerAliveInterval=60 -R 1111:localhost:22 serveruser@server
RestartSec=15
Restart=always


[Install]
WantedBy=multi-user.target

```

3) On the server side I've enabled *GatewayPorts*, configured passwordless login for *serveruser *and tested it on Pi's side. Everything works so far.
4) Tested a reverse tunnel by connecting to *tunneluser@server* -p *1111* - also works. 
5) An hour or so later I'm no longer able to connect to my tunnel. I've checked *server* status and it seems that my tunnel is listed as "ESTABLISHED" , but I can't login. If I restart *sshd* on *server* - tunnel gets re-establised again but I get the "wrong password" upon login, which is a good indicator that I'm not connecting to *pi. *On Pi's side reverse_tunnel service is still active and no errors have been reported....
6) My tunnel only gets re-established if I reboot Pi or restart tunnel service manually. Some time later it hangs again.

Not too long ago I did the exact same setup on 2 remote computers and unless I've missed something - everything worked without a hitch for a few months, including re-establishing a failed tunnel.

---

### Post by scorp123 on 2021-04-19
> **xpl01t said:**
>  2) Due to some bureaucratic constraints I cannot use *autossh* on *pi*, so my only option to run a persistent tunnel is a *systemd* service. It looks something like this: 

Welcome to the club, I have to do that too and I picked the same approach :lolflag:


> **xpl01t said:**
>  5) An hour or so later I'm no longer able to connect to my tunnel. I've checked *server* status and it seems that my tunnel is listed as "ESTABLISHED" , but I can't login. If I restart *sshd* on *server* - tunnel gets re-establised again but I get the "wrong password" upon login, which is a good indicator that I'm not connecting to *pi. *On Pi's side reverse_tunnel service is still active and no errors have been reported....
6) My tunnel only gets re-established if I reboot Pi or restart tunnel service manually. Some time later it hangs again. 

DHCP issue maybe? I'm assuming your Pi is in a client network? Did you check what the lease times in that network are? Also: Let's not forget Corporate Firewalls. Depending on make, model and setting it could be that a Firewall will actively kill what it perceives to be "stale" connections (e.g. to preserve bandwidth).

I had similar issues once and the only way I could solve it is to add more "auto-reconnect" features into my script.

My service file for "systemd" looks like this:

```

[Unit]
Description=ReverseSSH
Requires=network.target
After=systemd-user-sessions.service

[Service]
Type=simple
Restart=always
ExecStart=/opt/reversessh/revs.sh
# Don't run this as root!
User=sshuser

[Install]
WantedBy=multi-user.target

```

But that proved to be not enough for some reasons, e.g. it could happen that my network guys would work on the local LAN during off-hours, take routers or switches offline and what not, so I needed to add more "auto-reconnect" features directly in the script that my service file above is calling. So the file "/opt/reversessh/revs.sh" thus looks like this:

```

#! /bin/bash

while true
do
  LIVECHECK=`netstat -tan | grep INSERT-TARGET-HOST-HERE | grep ESTABLISHED`

  if [ -z "$LIVECHECK" ]
          then
                  ssh -N -c aes128-ctr -C -o ServerAliveInterval=60 -R 24999:localhost:22 ssh-jump-server.my.network.local
          else
                  sleep 1m
  fi
done

```

This setup works for me, 24 x 7. And it will always reconnect even if my LAN people do things to the network .. the connection will always go back up as soon as the LAN is available again. Also I'd suggest you use SSH keys for authentication.

---

### Post by xpl01t on 2021-04-20
Thx, @Scorp123
I think I've figured it out, and it's only partially my fault... :p 
Our partners, who's housing the equipment (and the ones that imposed all limitations), told us beforehand that they've removed all external connectivity from said equipment except Pi. 
Today I've discovered that I'm still getting backups from the old server (rsync from old machine), which means that the old tunnel that goes to the same port as Pi tunnel is also running. 
I've decided to keep the same port, so our guys won't have to change scripts and connection settings.

Decided to check SHA256 signatures and compare to auth logs, and here's where the dog was burried ))))
Between connection attempts from Pi I also get connections from an old host and neither is able to establish the tunnel.
Gotta bring the Pi back and change some settings for my tunnel, so I can connect to the old server and disable old tunnel...
Just in case I'll try your method as well. I think our old-old implementation was similar (ran as cronjob)

---

### Post by scorp123 on 2021-06-01
**_Edit:_**  What I wrote above in **Post #2** does not (any longer?) seem to work correctly.

When for some reasons one of the firewalls on either side quickly drops the connection (e.g. small glitch? A software update? Someone accidentally tripped over the cable and quickly reinserted it before the network monitoring picked up the interface being down? ... etc.) then the SSH connection gets killed. It should re-establish itself as per the code used ... but it doesn't :-s

Funny part is that due to how the whole thing was written ("systemd" service vs. infinite loop in the shell script that gets executed) the daemon still thinks that it is "up" even though it clearly is not (e.g. there's no SSH tunnel and no port being forwarded ...)  ](*,)

I just had this happen to me and my construct in post #2 does NOT automatically reconnect.

So I am now experimenting with this new approach:

```

[Unit]
Description=ReverseSSH
Requires=network.target
After=systemd-user-sessions.service

[Service]
Type=simple
Restart=always
RestartSec=20
ExecStart=/usr/bin/ssh -N -c aes128-ctr -C -o ServerAliveInterval=60 -o ExitOnForwardFailure=yes -R 24999:localhost:22 remote-user@ssh-jump-server.my.network.local
User=sshuser

[Install]
WantedBy=multi-user.target

```

---

