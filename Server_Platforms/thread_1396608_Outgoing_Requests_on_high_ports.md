---
title: "Outgoing Requests on high ports"
date: 2010-02-02
forum: Server Platforms
---

### Post by mistypotato on 2010-02-02
Can someone tell me a way to figure out what program or script is generating outbound requests on high ports approximately every half hour?

thx

---

### Post by Vegan on 2010-02-02
Kinda hard to see the software stack, my crystal ball is on strike today.

---

### Post by cdenley on 2010-02-02
To determine what process is attempting to establish a connection, use this command while the process is running.
```

sudo lsof -i -n

```
That should get you the PID, which can get you more information about the process.
```

sudo ps -f -p [PID]
sudo lsof -p [PID]

```

If the process doesn't run for long, that might be difficult. It may help to log the UID of new outgoing connections in order to track down how the process is started.
```

sudo iptables -A OUTPUT -m state --state NEW -j LOG --log-uid

```

---

### Post by Rhubarb on 2010-02-02
If you know exactly what ports are in use, you could do a quick internet search for them and see what applications are commonly used for those ports.

Alternatively you could setup a packet sniffer such as wireshark to capture those packets, and have a look at them to see what they may be / may be from.

---

### Post by cdenley on 2010-02-02
I believe in his other thread (which was closed before I could reply) he said it was traffic going to port 443, so encrypted web traffic. I couldn't get a reply from the web server, though I could establish a TCP connection.

---

### Post by cdenley on 2010-02-02
Do you by any chance use TOR?
[http://torstatus.blutmagie.de/router_detail.php?FP=7be683e65d48141321c5ed92f075c55364ac7123](http://torstatus.blutmagie.de/router_detail.php?FP=7be683e65d48141321c5ed92f075c55364ac7123)
(that was the IP/port given in the closed thread)

---

### Post by tgalati4 on 2010-02-02
If inbound port 443, then it's probably IMAP mail.

---

### Post by cdenley on 2010-02-02
> **tgalati4 said:**
> If inbound port 443, then it's probably IMAP mail.

No, imap uses TCP 143 (or 993 with SSL). 443 is generally HTTP with SSL. However, the server in question appears to be running a TOR router on that port.

---

### Post by BkkBonanza on 2010-02-02
I haven't seen anyone mention the obvious,

sudo netstat -ntp

As long as you do it just after the event occurs it will still show connections finishing up and with process info.

For more detail you can use tcpdump with a filter expression selecting a port range,
see man tcpdump, eg.

tcpdump 'tcp port > 1024'

---

### Post by cdenley on 2010-02-02
Same thing as
```

sudo lsof -i -n

```
which I already posted. Analyzing traffic with tcpdump probably won't get you anywhere since it must be encrypted tor traffic.

---

### Post by mistypotato on 2010-02-02
From the command lsof -i -n
it appears www-data is the only process utilizing the ports in the suspect range

Could that indicate a hack of mysql?

---

### Post by mistypotato on 2010-02-02
**Does anything here look odd?**

vsftpd    13112       root    0u  IPv4  45741       TCP *:ftp (LISTEN)
apache2   15022   www-data    3u  IPv4 424615       TCP *:www (LISTEN)
apache2   15022   www-data    4u  IPv4 424617       TCP *:https (LISTEN)
apache2   15022   www-data   56u  IPv4 764740       TCP 127.0.0.1:45435->127.0.0.1:6800 (CLOSE_WAIT)
apache2   15123   www-data    3u  IPv4 424615       TCP *:www (LISTEN)
apache2   15123   www-data    4u  IPv4 424617       TCP *:https (LISTEN)
apache2   15123   www-data   56u  IPv4 764738       TCP 127.0.0.1:45434->127.0.0.1:6800 (CLOSE_WAIT)
apache2   15281   www-data    3u  IPv4 424615       TCP *:www (LISTEN)
apache2   15281   www-data    4u  IPv4 424617       TCP *:https (LISTEN)
apache2   15281   www-data   56u  IPv4 764712       TCP 127.0.0.1:45429->127.0.0.1:6800 (CLOSE_WAIT)
apache2   15282   www-data    3u  IPv4 424615       TCP *:www (LISTEN)
apache2   15282   www-data    4u  IPv4 424617       TCP *:https (LISTEN)
apache2   15282   www-data   56u  IPv4 764719       TCP 127.0.0.1:45430->127.0.0.1:6800 (CLOSE_WAIT)
apache2   15284   www-data    3u  IPv4 424615       TCP *:www (LISTEN)
apache2   15284   www-data    4u  IPv4 424617       TCP *:https (LISTEN)
apache2   15284   www-data   56u  IPv4 764726       TCP 127.0.0.1:45432->127.0.0.1:6800 (CLOSE_WAIT)
apache2   15285   www-data    3u  IPv4 424615       TCP *:www (LISTEN)
apache2   15285   www-data    4u  IPv4 424617       TCP *:https (LISTEN)
apache2   15285   www-data   56u  IPv4 764750       TCP 127.0.0.1:45438->127.0.0.1:6800 (CLOSE_WAIT)
apache2   15286   www-data    3u  IPv4 424615       TCP *:www (LISTEN)
apache2   15286   www-data    4u  IPv4 424617       TCP *:https (LISTEN)
apache2   15286   www-data   56u  IPv4 764732       TCP 127.0.0.1:45433->127.0.0.1:6800 (CLOSE_WAIT)
apache2   15287   www-data    3u  IPv4 424615       TCP *:www (LISTEN)
apache2   15287   www-data    4u  IPv4 424617       TCP *:https (LISTEN)
apache2   15287   www-data   56u  IPv4 764742       TCP 127.0.0.1:45436->127.0.0.1:6800 (CLOSE_WAIT)
apache2   26048       root    3u  IPv4 424615       TCP *:www (LISTEN)
apache2   26048       root    4u  IPv4 424617       TCP *:https (LISTEN)
privoxy   27514    privoxy    1u  IPv4 321123       TCP 127.0.0.1:8118 (LISTEN)

---

### Post by BkkBonanza on 2010-02-02
Your data above indicates that apache is talking to port 6800. This is happening on localhost, which means it's just a local communication between two programs running on your system. What do you have on port 6800? It doesn't appear to be anything malicious though.

---

### Post by cdenley on 2010-02-02
The destination port is a lot more relevant for outbound connection than the source port. Since you said it was connecting on port 443, it appears the connection wasn't active when you ran the command. I do see you have privoxy running, so once again DO YOU USE TOR? The traffic you were concerned about must be tor traffic.

The local connection by apache to port 6800 looks odd since you don't have anything listening on that port, but it probably isn't related to the tor traffic.

---

### Post by mistypotato on 2010-02-02
port 6800  runs Railo Coldfusion Server Engine

Here is some additional output

firefox-b 32050  myusername   31u  IPv4 769747       TCP 192.168.4.12:36200->74.125.47.113:www (ESTABLISHED)
me@myServer:~$ vsftpd    13112       root    0u  IPv4  45741       TCP *:ftp (LISTEN)
bash: syntax error near unexpected token `('
me@myServer:~$ apache2   15022   www-data    3u  IPv4 424615

---

### Post by mistypotato on 2010-02-02
> **cdenley said:**
> The destination port is a lot more relevant for outbound connection than the source port. Since you said it was connecting on port 443, it appears the connection wasn't active when you ran the command. I do see you have privoxy running, so once again DO YOU USE TOR? The traffic you were concerned about must be tor traffic.

The local connection by apache to port 6800 looks odd since you don't have anything listening on that port, but it probably isn't related to the tor traffic.

I wasnt aware that I use or installed Tor.  I do not know what it is or does. But I do see Debian-Tor server in the list.

The other day I attempted to install Bothunter on my system.

---

### Post by cdenley on 2010-02-02
[http://www.bothunter.net/docs.html](http://www.bothunter.net/docs.html)
> 
4. Optional: You are prompted to install Tor if it has not been installed previously. BotHunter may be configured to use Tor to interact
anonymously with the BotHunter repository services.

[https://www.torproject.org/](https://www.torproject.org/)

---

### Post by mistypotato on 2010-02-02
Thanks.

Still cant understand why my server is trying to connect with numersous computers that are on IPBLOCK's list of "bad" sites?

---

### Post by cdenley on 2010-02-02
If IPBLOCK blacklists TOR routers, then I would reconsider using it.

---

### Post by mistypotato on 2010-02-02
Ok,
It's official as far as I'm concerned.
My server apparently has been compromised.

The convincing evidence...
A Drastic increase in the number of OUTBOUND connections on high ports going to multiple sites listed at MXtoolbox.com and other blacklisting services.  My guess is a script has been installed.

Additional evidence, hundreds of new inbound connection attempts from IP addresses in foreign countries, representing a sudden and significant increase in such connection attempts that were not occurring last week.  While this could simply represent a global increase in such traffic, I have not been able to find any evidence of that.

The only software installed was Bothunter Unix version.  I cannot say for sure I got a poisoned copy but it would be my guess.  However, now that the server is down, I'll try to investigate further to see if the logs can give me a clue otherwise.

rkhunter is not finding anything definitive.  /usr/sbin/unhide and /usr/sbin/unhide-Linux26 are the only warnings.

I have shutdown all external connections both inbound and outbound to the server.

At this point it looks as though I'm in for the long and difficult job of rebuilding my server from a freshly low-level formatted hard drive.

---

### Post by cdenley on 2010-02-03
I think what is more likely is Bothunter or something you installed is connecting to TOR routers. I only know about one specific connection that was concerning you, and that could not have been anything but TOR traffic. I wouldn't be surprised if all the traffic that is concerning you was to TOR routers. How about posting some IP's and ports so we can see what servers it is connecting to? It seems very unlikely that a malicious script would bother using TOR to hide the source IP. Also, an increase in inbound connection attempts wouldn't indicate your system has been compromised. If they already gained access to your system, there would be no reason to attempt more remote connections.

---

### Post by mistypotato on 2010-02-03
Thanks for the encouragement :)

I'm checking that possibility.

---

