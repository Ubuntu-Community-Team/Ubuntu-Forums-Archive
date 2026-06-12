---
title: "SSH client issue connecting to multiple servers"
date: 2007-06-24
forum: Server Platforms
---

### Post by BluewookieJim on 2007-06-24
Hi all, first post here from a new ubuntu convert.

The problem I'm experiencing is that I have 2 SSH servers on my home network, each set to listen on a different port, and I connect via a dynamic dns address. I usually connect to them using a command like

ssh {username}@{hostname}.dnydns.net -p {port_number}

So what I basically have happening here is when the .ssh/known_hosts file is empty, I can connect to either server. But once I connect to one server, I cannot connect to the other until I clear the known_hosts file again. I get the following error message:

[INDENT]@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
----------------------------------------------
Please contact your system administrator.
Add correct host key in /home/jim/.ssh/known_hosts to get rid of this message.
Offending key in /home/jim/.ssh/known_hosts:2
RSA host key for ------------------------ has changed and you have requested strict checking.
Host key verification failed.

Does anyone happen to have any suggestions?
[/INDENT]
Thanks in advance.

---

### Post by Wardazo on 2007-06-24
Hi

I think you might be getting this because you are using **1** address (the dynamic dns one) for two differenet severs with different keys. Possible solutions

1. Use the the ip addresses of the computers on you *home* network to log in 

ssh 192.168.X.XXX

... forget about dynamic dns. The client can then differentiate between the two servers. There is also no need for different ports.

or

2.Never used dynamic dns, but if you're determined to use it, you could try copying the keys for one ssh server (found in /etc/ssh/) to the other one, so they then share the same key. I have never tried this, and suspect that it will not work.

---

### Post by BluewookieJim on 2007-06-24
I see what you are saying, but the reason I use the dyndns setup is that I use the SSH connection remotely when I am away from home. I have at&t yahoo dsl, so I can't count on my IP ever being the same. 

Also, both SSH servers are behind my router, with the only the specific high numbered port open via the the router interface. 

I guess I could just use separate logins on my Ubuntu system to avoid the problem, but that wouldn't really solve the problem.

---

### Post by Wardazo on 2007-06-24
> **BluewookieJim said:**
> I guess I could just use separate logins on my Ubuntu system to avoid the problem, but that wouldn't really solve the problem.

No I agree it wouldn't. 

Could you have two different dyndns addresses or can you make an extra sub domain. You need some ip address or dns item to distinguish them so the client doesn't get confused about the key.

You could try (2) but you might have to reinstall one of the ssh servers. It could mess things up.

Just seen a solution here:

[http://people.uleth.ca/~daniel.odonnell/Blog/using-ssh-to-access-multiple-machines-at-a-single-domain](http://people.uleth.ca/~daniel.odonnell/Blog/using-ssh-to-access-multiple-machines-at-a-single-domain)

---

### Post by BluewookieJim on 2007-06-24
Thanks. That worked like a charm. Appreciate the help.

---

### Post by ricrac on 2007-06-24
SSH's known_hosts must have a unique host id to store and compare keyids.

Fixes:
1. Turn off hostid checking.  Lazy, insecure, do not do this! 
2. Assign another dyndns name to your dynamic ip, dyndns.org provides up to 5 hostnames
Both names will point to you, always use the same name for the same port.
i.e    ssh mydynamichostname       goes to standard port 22
       ssh myotherdynamichostname  goes to port 2222

Best Solution client config file, easier to maintain than [http://people.uleth.ca/~daniel.odonn...-single-domain](http://people.uleth.ca/~daniel.odonn...-single-domain)
If you want the "single-domain" solution why not just use -i and define a different identity file?
ssh -i  ~/.ssh/known_hosts remote1
ssh -i  ~/.ssh/known_hosts2 remote1:2222

3. Use a client configuration file. You should use config files especially for tunnels and complex auth's. Clearest SSH help pages. [http://www.openbsd.org/cgi-bin/man.cgi?query=ssh_config](http://www.openbsd.org/cgi-bin/man.cgi?query=ssh_config)
[http://www.rzg.mpg.de/networking/tunnelling.html](http://www.rzg.mpg.de/networking/tunnelling.html)

example /home/username/.ssh/config
```

#Start of /home/username/.ssh/config
Host remote1
    Hostname mydynamichost.dyndns.net
    Port 22
    ServerAliveInterval 60
Host remote2
    Hostname mydynamichost.dyndns.net
    Port 222
    ServerAliveInterval 60
#End of /home/username/.ssh/config

Use:	ssh username@remote1
	ssh username@remote2

```
-----------------------------------------------------------------------------------------------------------------
You could of course also tunnel ssh. Assume ssh server2's address is 192.168.1.1 on it's net.
```

#Start of /home/username/.ssh/config
Host remote1
    Hostname mydynamichost.dyndns.net
    Port 22
    User username
    Localforward 127.0.0.1:2222 192.168.1.1:22
    ServerAliveInterval 60
Host forwarded-remote2
    Hostname 127.0.0.1
    User username
    Port 2222
    ServerAliveInterval 60
#End of /home/username/.ssh/config

Use:
	ssh remote1
	ssh forwarded-remote2

```
Notice I used the ServerAliveInterval 60 to keep the connection alive and added the username to reduce typing when used. Adjust values as needed.

-----------------------------------------------------------------------------------------------------------------
I sometimes have as many as 12 tunnels defined for a single connection, much easier in the config than on the commandline.
```

#Start of /home/username/.ssh/config
Host remote1
    Hostname mydynamichost.dyndns.net
    Port 22
    User username
    Localforward 127.0.0.1:2222 192.168.1.1:22
    Localforward 127.0.0.1:110 192.168.1.2:110
    Localforward 127.0.0.1:25 192.168.1.3:25
    Localforward 127.0.0.1:3306 192.168.1.4:3306
    Localforward 127.0.0.1:10000 192.168.1.5:10000
    Localforward 127.0.0.1:80 192.168.1.6:80
    Localforward 127.0.0.1:443 192.168.1.7:443
    Compression yes
    CompressionLevel 9
    ServerAliveInterval 60
#End of /home/username/.ssh/config

```
This maps ports <1024 so you need to ssh as root, (will connect to remotes as username)
(root)#  ssh remote1
Then as a normal user you can,
Connect to remote web server in browser at [http://127.0.0.1](http://127.0.0.1)
Connect to remote secure web server in browser at [https://127.0.0.1](https://127.0.0.1)
Connect to remote pop server defined locally in email app as 127.0.0.1
Connect to remote smtp server defined locally in email app as 127.0.0.1
Connect to remote mysql server defined locally in sql app as 127.0.0.1
Connect to remote webmin server defined locally in email app as 127.0.0.1
Connect to remote ssh server locally, i.e.   ssh 127.0.0.1:2222

This assumes you're not running anything locally on ports 25,80,110,443,2222,3306 and 10000
Add "GatewayPorts yes" and any machines on your local net can connect using your local address.
i.e. your local ip running "ssh remote1" is 192.168.2.2, now all machines on 192.168.2 can access all services (web,pop,smtp,mysql,webmin) from remote 192.168.1.X  at(thru) 192.168.2.2
All local machines on 192.168.2
Connect to remote web server in browser at [http://192.168.2.2](http://192.168.2.2)
Connect to remote secure web server in browser at [https://192.168.2.2](https://192.168.2.2)
Connect to remote pop server defined locally in email app as 192.168.2.2
Connect to remote smtp server defined locally in email app as 192.168.2.2
Connect to remote mysql server defined locally in sql app as 192.168.2.2
Connect to remote webmin server defined locally in email app as 192.168.2.2
Connect to remote ssh server locally, i.e.   ssh 192.168.2.2:2222

---

### Post by BluewookieJim on 2007-06-24
wow, that is a lot to swallow.

I have something similar setup on my XP workstation at work. I have a batch file setup that handles all of my tunneling, I pass in a port #, and then map all the tunnels, and finally bring up the PuTTY interface for the login.

---

### Post by BluewookieJim on 2007-06-29
So there is definately some interestin tidbits there I would like to go through a bit more.

At work, on my winxp setup, I currently have putty setup, which I fire off through a dos batch job to map all my tunnels, and bring up the putty terminal window for me to login with. It also leaves the dos window up with a "key" to my various tunnels.

```
@Echo Off
cls

SET allLocal=

SET L01=-L 6001:192.168.1.163:80
SET allLocal=%allLocal% %L01%
@Echo TivoWebPlus - Downstairs         : Port 6001

SET L01=-L 6002:192.168.1.164:80
SET allLocal=%allLocal% %L01%
@Echo TivoWebPlus - Upstairs           : Port 6002

SET L01=-L 6003:192.168.1.1:80
SET allLocal=%allLocal% %L01%
@Echo Linksys Router Interface         : Port 6003

SET L01=-L 6004:192.168.1.181:9000
SET allLocal=%allLocal% %L01%
@Echo Slimserver on LS250_A            : Port 6004

SET L01=-L 6005:192.168.1.130:9000
SET allLocal=%allLocal% %L01%
@Echo Slimserver on Vader              : Port 6005

SET L01=-L 6006:192.168.1.130:5900
SET allLocal=%allLocal% %L01%
@Echo UltraVnc on Vader                : Port 6006

SET L01=-L 6007:192.168.1.120:5900
SET allLocal=%allLocal% %L01%
@Echo UltraVnc on Erin                 : Port 6007

SET L01=-L 6008:192.168.1.130:3389
SET allLocal=%allLocal% %L01%
@Echo Remote Desktop on Vader          : Port 6008

SET L01=-L 6009:192.168.1.120:3389
SET allLocal=%allLocal% %L01%
@Echo Remote Desktop on Erin           : Port 6009

SET L01=-L 6010:192.168.1.130:61022
SET allLocal=%allLocal% %L01%
@Echo SFTP on Vader                    : Port 6010

SET L01=-L 6011:192.168.1.163:23
SET allLocal=%allLocal% %L01%
@Echo Telnet on Downstairs TiVo        : Port 6011

SET L01=-L 6012:192.168.1.164:23
SET allLocal=%allLocal% %L01%
@Echo Telnet on Upstairs TiVo          : Port 6012

REM Echo %allLocal%

if "%1"=="vader"  Goto CONNECTVADER
if "%1"=="ls250a" Goto CONNECTLS250A
if "%1"=="" Goto NOHOST

:NOHOST
@Echo No Host specified. Use forward {vader/ls250a}
Goto END

:CONNECTVADER
@putty -ssh -C %2 %allLocal% {user}@{host}.dyndns.net 86422
goto END

:CONNECTLS250A
@putty -ssh -C %2 %allLocal% {user}@{host}.dyndns.net 89522
goto END

:END
Exit /B 0

```

I basically fire this code off by running the batch script, with the parameter for the SSH server I want to log in to, ie,  c:\remotetools\ssh_tunnels.bat vader

Ideally I'd like to be able to do something similar to this in ubuntu, and it looks like the examples you post above would facilitate some of that.

---

