---
title: "Unable to open ports on Hardy !?"
date: 2008-04-28
forum: Security
---

### Post by skaboss on 2008-04-28
Hello,

I knwo that seems to be a total noob question, but i'm really stuck with this.
I have a dsl modem/router on which i opened the necessary ports (6881 tcp/udp) to run a torrent client. On my Hardy laptop, Azureus indicates this port as "firewalled", and so my dl speed is slow.
I then opened this port with ufw, but nmap still shows it closed...
```
Starting Nmap 4.53 ( http://insecure.org ) at 2008-04-28 12:17 CEST
Interesting ports on localhost (127.0.0.1):
PORT     STATE  SERVICE
6881/tcp closed bittorent-tracker

Nmap done: 1 IP address (1 host up) scanned in 0.094 seconds

```

It is not ans ISP issue, since it works well on my other computer.

Can you please help me ?

---

### Post by cdenley on 2008-04-28
Ubuntu does not filter any traffic by default. Post the output for this command.
```

sudo iptables -L INPUT

```

Unless you configured iptables to block the traffic, it must be a problem with your router's configuration.

---

### Post by skaboss on 2008-04-28
Hello,

Thank your for your answer. Here is the output :
```
target     prot opt source               destination         
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere  
```
My laptop has a dual boot with Vista, and i don't have this problem with Vista, that's why i can't imagine that would be caused by a messy router's config.

---

### Post by cdenley on 2008-04-28
You have ufw enabled. If iptables is filtering incoming traffic because of your ufw configuration, you either need to configure ufw to allow your traffic, or disable ufw.

To allow incoming traffic on that port (I think)
```

sudo ufw allow 6881

```

To show the rules for ufw
```

sudo ufw status

```

To disable ufw (you shouldn't need it for a desktop system)
```

sudo ufw disable

```

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

---

### Post by skaboss on 2008-04-28
Thanks for your answer. Actually, that is what i can't figure out.
Here is what ufw status displays :
```
Firewall loaded

To                         Action  From
--                         ------  ----
23687:tcp                  ALLOW   Anywhere
23687:udp                  ALLOW   Anywhere
6881:tcp                   ALLOW   Anywhere
6881:udp                   ALLOW   Anywhere

```

But these rules don't appear in nmap :

```
landry@albundy-mobile:~$ sudo nmap localhost

Starting Nmap 4.53 ( http://insecure.org ) at 2008-04-28 20:18 CEST
Interesting ports on localhost (127.0.0.1):
Not shown: 1711 closed ports
PORT     STATE SERVICE
25/tcp   open  smtp
631/tcp  open  ipp
3306/tcp open  mysql

```

It makes me think that the system doesn't care of the rules defined with ufw, am i wrong ?

---

### Post by cdenley on 2008-04-28
I think nmap by default will only scan common port numbers (22,80,3306,8080...). Also, if there isn't a service currently listening on that port, nmap can't tell whether the traffic is being filtered by iptables, or just ignored since there's no server on that port. When you scan "localhost", I don't think any firewall rules will have an effect, anyway. The local loopback device usually isn't filtered.

---

### Post by The Cog on 2008-04-28
It makes me think that Azureus is not listening on port 6881. I seem to rember that Azureus uses a random port number unless you configure a specific one.

You can double-check with the command:
```
netstat -lnt
```
ans see if port 6881 is listening.

---

### Post by skaboss on 2008-04-28
Ok, i edited Azureus config to use 23687 instead of 6881, and modified my rules accordingly (i disabled uwf, and used directly iptables).
Now i have :

```
 netstat -lnt
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     
tcp6       0      0 127.0.0.1:6880          :::*                    LISTEN     
tcp6       0      0 :::23687                :::*                    LISTEN     
tcp6       0      0 127.0.0.1:45100         :::*                    LISTEN     

```

```
sudo nmap -p23687 XX.XXX.XX.XXX

Starting Nmap 4.53 ( http://insecure.org ) at 2008-04-28 21:53 CEST
Interesting ports on -------------------------------:
PORT      STATE    SERVICE
23687/tcp filtered unknown

Nmap done: 1 IP address (1 host up) scanned in 0.448 seconds

```

---

### Post by The Cog on 2008-04-28
Are you trying to can your public address from inside a router? That cannot be done - the router won't NAT a connection that comes from the inside to the inside. You'll have to ue an external service like grc shields-up to scan your public address.

---

### Post by lemming465 on 2008-04-28
Do Windows and Ubuntu end up with the same IP address?  Typically your DSL router has firewall capabilities built in and you have to explicitly configure port forwarding for inbound connections.  Is that something that applies to your situation?

---

