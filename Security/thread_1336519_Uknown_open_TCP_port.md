---
title: "Uknown open TCP port"
date: 2009-11-24
forum: Security
---

### Post by mikelj on 2009-11-24
[FONT=Arial][SIZE=2]After entering [/SIZE][/FONT][SIZE=2]**netstat -lp -t** I recognize all connections except for** localhost:29754**.  No PID is shown for this service.

Does anyone know how I might determine what program is opening this port?

Thanks[/SIZE]

---

### Post by dca on 2009-11-24
You can see if using nmap gives more info by running port-scan on yourself (localhost)...
 
*sudo nmap -sS -O 127.0.0.1*
 
I don't know if it's installed by default...

---

### Post by dca on 2009-11-24
Doesn't avahi or something open ports to discover add'l services running on your network?
 
Oh, here's something else on nmap and other port discoveries
 
[http://www.go2linux.org/which_service_or_program_is_listening_on_port](http://www.go2linux.org/which_service_or_program_is_listening_on_port)

---

### Post by scorp123 on 2009-11-24
> **mikelj said:**
> [FONT=Arial][SIZE=2]After entering [/SIZE][/FONT][SIZE=2]**netstat -lp -t** I recognize all connections except for** localhost:29754**.  No PID is shown for this service. What does this command say?
```
sudo lsof -n -i -P
```

Example output:
```

COMMAND   PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
sshd     1644 root    3u  IPv4   6172      0t0  TCP *:22 (LISTEN)
sshd     1644 root    4u  IPv6   6175      0t0  TCP *:22 (LISTEN)
cupsd    2189 root    6u  IPv6   7352      0t0  TCP [::1]:631 (LISTEN)
cupsd    2189 root    7u  IPv4   7353      0t0  TCP 127.0.0.1:631 (LISTEN)
dropbox  3685  joe   11u  IPv4  40175      0t0  TCP 192.168.1.210:36208->174.36.30.67:443 (CLOSE_WAIT)
dropbox  3685  joe   21u  IPv4  40274      0t0  TCP 192.168.1.210:39225->174.36.30.66:443 (CLOSE_WAIT)
dropbox  3685  joe   23u  IPv4  65778      0t0  TCP 192.168.1.210:55122->208.43.202.26:80 (ESTABLISHED)
dropbox  3685  joe   25u  IPv4  40280      0t0  TCP 192.168.1.210:52657->75.101.135.243:443 (CLOSE_WAIT)
dropbox  3685  joe   27u  IPv4  40286      0t0  TCP 192.168.1.210:39228->174.36.30.66:443 (CLOSE_WAIT)
dhclient 4625 root    5w  IPv4  65395      0t0  UDP *:68 
dhclient 4702 root    5w  IPv4  65634      0t0  UDP *:68

```


EDIT:

I just tried your command "**netstat -lp -t**" and I don't see half of what "**sudo lsof -n -i -P**" spits out. So I'd strongly suggest you give "**sudo lsof -n -i -P**" a try.

---

### Post by cdenley on 2009-11-24
You need to run netstat as root to get the PID and process name. That might be helpful.
```

sudo netstat -tlnp

```
Then, once you get the PID, if you don't recognize the command:
```

sudo lsof -p [PID]

```

---

### Post by mikelj on 2009-11-25
nmap Doesn't detect it.

Both scorp123 and cdenley solutions gave me the PID I was looking for.  

```
tcp        0      0 127.0.0.1:29754         0.0.0.0:*               LISTEN      1850/vpnagentd
```With the info from: **sudo lsof -p 1850 **I could determine that this was some kind of agent relating to the Cisco AnyConnect software.

Thanks to all who replied.

---

### Post by mikelj on 2009-11-25
Credit goes to dca too.  If I had initially read past the nmap section in your link I would have found the same solutions.

---

