---
title: "Parania or am i being hacked?"
date: 2010-08-23
forum: Security
---

### Post by triunenature on 2010-08-23
Ubuntu Server 10.04

First i want to show you some auth.log entrys:

```

Aug 22 17:06:33 server sshd[1915]: Failed password for root from xxx.xxx.x.10 port 49813 ssh2
Aug 22 17:07:13 server sshd[1915]: last message repeated 2 times

```
(no computer on the network is assigned to xxx.xxx.x.10)

```

Aug 22 17:40:43 server sshd[2303]: Did not receive identification string from 68.44.48.229
Aug 22 17:43:02 server sshd[2305]: Did not receive identification string from 68.37.135.185
Aug 22 17:45:25 server sshd[2307]: Did not receive identification string from 68.112.138.15
Aug 22 17:47:42 server sshd[2309]: Did not receive identification string from 68.12.243.40

```

Not sure what that is, but does that mean someone is trying to access my server?  I'm new to auth.log and exploring it has made me a bit paranoid...

So am i paranoid, or is this a legitimate concern?

If this is legit, what methods should i impose to secure my server?

I have already changed the default port for ssh, and only allowed certain users to connect via ssh.

Any other ideas?

Thanks for the advice!

---

### Post by FuturePilot on 2010-08-23
Use DenyHosts or Fail2Ban. It will ban the IP after a specified number of failed login attempts. Also, disable password authentication completely and only use key auth.

---

### Post by cdenley on 2010-08-24
Authentication attempts such as that are very common. Bots will check random IP's to see if it is hosting a SSH server, and if they are, it will attempt to authenticate using weak passwords and common usernames (usually root). You can get a few attacks like that a day, each attack consisting of possibly hundreds of authentication attempts (if they don't get banned first). This is why you must use strong passwords (or better yet, disable password authentication and use keys) and never set a root password. DenyHosts or Fail2Ban may help as well, as already suggested.

---

### Post by msandoy on 2010-08-24
Just to maintain a healty paranoia level, you could install logwatch to assist you in reading your logfiles. I use logwatch and Denyhosts. I have seen attacks by poorly made bots, mounting up to 1500 login attempts after the specified IP was banned.
Reading logfiles will give you an initial scare. :-)

---

### Post by maikel.b on 2010-08-25
> **triunenature said:**
> Ubuntu Server 10.04
 
First i want to show you some auth.log entrys:
 
```

Aug 22 17:06:33 server sshd[1915]: Failed password for root from xxx.xxx.x.10 port 49813 ssh2
Aug 22 17:07:13 server sshd[1915]: last message repeated 2 times

```
(no computer on the network is assigned to xxx.xxx.x.10)
 
```

Aug 22 17:40:43 server sshd[2303]: Did not receive identification string from 68.44.48.229
Aug 22 17:43:02 server sshd[2305]: Did not receive identification string from 68.37.135.185
Aug 22 17:45:25 server sshd[2307]: Did not receive identification string from 68.112.138.15
Aug 22 17:47:42 server sshd[2309]: Did not receive identification string from 68.12.243.40

```
 
Not sure what that is, but does that mean someone is trying to access my server? I'm new to auth.log and exploring it has made me a bit paranoid...
 
So am i paranoid, or is this a legitimate concern?
 
If this is legit, what methods should i impose to secure my server?
 
I have already changed the default port for ssh, and only allowed certain users to connect via ssh.
 
Any other ideas?
 
Thanks for the advice!
 
[FONT=Calibri][SIZE=3]Oke changing the port for default ssh is a option.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I didn’t change my ssh port, I use iptables to protect my ssh against brute force attack.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Before using ip tables more than 1000 hacks a day, with ip tables 1 or 2 bud they can’t login.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]You can try to login for 8 times in 60 seconds, a script gives up and go to find a other ssh server..[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3][SIZE=2]Vi[/SIZE] [/SIZE][/FONT][COLOR=black][FONT=Verdana]/etc/rc.local and add the next 2 lines above exit [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH[/FONT][/COLOR]
[FONT=Verdana][COLOR=black]iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 8 --rttl --name SSH -j DROP[/COLOR][/FONT]
 
[COLOR=black][FONT=Verdana]this wil start iptables when you reboot the server..[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]for now no boot required copy and paste these in the shell as root[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH[/FONT][/COLOR]
[FONT=Verdana][COLOR=black]iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 8 --rttl --name SSH -j DROP[/COLOR][/FONT]
 
[COLOR=black][FONT=Verdana]this only works when you have ssh working on port 22 if you want to use the port you use at this moment for ssh change this port also with iptables.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Success!! Greetz Maikel.[/FONT][/COLOR]

---

### Post by Nick_Jinn on 2010-08-25
I know for certain I have been hacked before. I even have the IPs of a few people who have done it, though I never did anything about it.

---

### Post by wacky_sung on 2010-08-25
I have been a victim of several hacks such as using my system as zombies(from botnet), RAT and keylogger down the decade using Window OS.As for Linux ,yet for me find out down the road.:guitar:

---

