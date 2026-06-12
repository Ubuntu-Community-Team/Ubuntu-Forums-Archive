---
title: "Why is my port 25 open?"
date: 2010-10-26
forum: Security
---

### Post by Alexx86 on 2010-10-26
Hey,
I played around a little and found that out:
```

alexx@alexx-fett:/etc/init.d$ nmap localhost

Starting Nmap 5.00 ( http://nmap.org ) at 2010-10-26 18:19 CEST
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 998 closed ports
PORT    STATE SERVICE
25/tcp  open  smtp
631/tcp open  ipp

Nmap done: 1 IP address (1 host up) scanned in 0.10 seconds
alexx@alexx-fett:/etc/init.d$ telnet localhost 25
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 alexx-fett ESMTP Postfix (Ubuntu)
quit
221 2.0.0 Bye
Connection closed by foreign host.
alexx@alexx-fett:/etc/init.d$ 
```

Do you know why I have a postfix installed on my system? This is not default, or is it?
On my other laptop (Ubuntu Netbook Remix 10.04) the port 25 is closed.

Thanks in advance,
 Alex

---

### Post by cariboo on 2010-10-26
Postfix is installed as a dependency of some programs, if you choose the option to not configure it on install, it shouldn't be listening on any port.

To do this, open a terminal and type:

```
sudo dpkg-reconfigure postfix
```

and select no configuration from the dialog box.

---

### Post by uRock on 2010-10-26
> **cariboo907 said:**
> Postfix is installed as a dependency of some  programs, if you choose the option to not configure it on install, it  shouldn't be listening on any port.

To do this, open a terminal and type:

```
sudo dpkg-reconfigure postfix
```and select no configuration from the dialog box.
or deny the port via GUFW.

---

### Post by Alexx86 on 2010-10-26
> **cariboo907 said:**
> Postfix is installed as a dependency of some programs, if you choose the option to not configure it on install, it shouldn't be listening on any port.

To do this, open a terminal and type:

```
sudo dpkg-reconfigure postfix
```and select no configuration from the dialog box.

I do remember that screen. Apparently I installed postfix along with something else I installed a few days ago. I just can't remember what it was.
Thanks a lot :)

---

### Post by pqwoerituytrueiwoq on 2010-10-26
```
 * Stopping Postfix Mail Transport Agent postfix                         [ OK ] 

Postfix configuration was untouched.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Stopping Postfix Mail Transport Agent postfix                         [ OK ] 
 * Starting Postfix Mail Transport Agent postfix                         [ OK ]
```
Just tried reconfiguring it it started back up
i changed it from Internet site to no configuration

---

### Post by Alexx86 on 2010-10-26
> **pqwoerituytrueiwoq said:**
> 
i changed it from Internet site to no configuration

Yup, it did the same here.
I just uninstalled it (along with the dependend "trn", a news reader) and hope nothing important used it.

---

### Post by CharlesA on 2010-10-26
Note: If you run nmap from the same machine - scanning localhost, it'll throw off the reading.

---

### Post by Alexx86 on 2010-10-26
> **CharlesA said:**
> Note: If you run nmap from the same machine - scanning localhost, it'll throw off the reading.

I'm sorry, what means "throw off the reading"?

---

### Post by CharlesA on 2010-10-26
> **Alexx86 said:**
> I'm sorry, what means "throw off the reading"?

It will show ports as open when they aren't open to the outside world.

You'd have to run nmap from another machine to get a valid reading.

---

### Post by pqwoerituytrueiwoq on 2010-10-26
> **CharlesA said:**
> Note: If you run nmap from the same machine - scanning localhost, it'll throw off the reading.
what if you use your local ip assigned by your router
```
user@linux-laptop:~$ nmap 192.168.1.46

Starting Nmap 5.00 ( http://nmap.org ) at 2010-10-26 15:15 EDT
Interesting ports on 192.168.1.46:
Not shown: 999 closed ports
PORT   STATE SERVICE
25/tcp open  smtp

Nmap done: 1 IP address (1 host up) scanned in 0.23 seconds
```

---

### Post by CharlesA on 2010-10-26
> **pqwoerituytrueiwoq said:**
> what if you use your local ip assigned by your router
```
user@linux-laptop:~$ nmap 192.168.1.46

Starting Nmap 5.00 ( http://nmap.org ) at 2010-10-26 15:15 EDT
Interesting ports on 192.168.1.46:
Not shown: 999 closed ports
PORT   STATE SERVICE
25/tcp open  smtp

Nmap done: 1 IP address (1 host up) scanned in 0.23 seconds
```

Same thing will happen since you are running the scanner from that machine.

You'd need to scan it from another machine on the same network to get an accurate list of what ports are open.

---

### Post by Alexx86 on 2010-10-26
Blast. I would have liked to try that. I just scanned my local network address, and port 631 (cups?), which was open at `nmap localhost`, was closed.
Now as I purged postfix, I can't try it anymore.

---

### Post by CharlesA on 2010-10-26
In any case, you can always use netstat to see what is listening for external connections:

```
netstat -ln
```

That'll show all listening services, anything with a *:port is listening for external connections.

---

