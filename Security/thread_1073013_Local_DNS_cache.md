---
title: "Local DNS cache"
date: 2009-02-17
forum: Security
---

### Post by gecko3940 on 2009-02-17
I've just performed these actions on my computer as firefox is rather slow:

> [http://www.ubuntugeek.com/local-dns-cache-for-faster-browsing-on-ubuntu-machine.html](http://www.ubuntugeek.com/local-dns-cache-for-faster-browsing-on-ubuntu-machine.html)

 I was wondering if I have made my computer vulnerable to attack. I have a netgear voip/firewall and use firestarter (default settings). The last feedback comment suggests I have opened a port. here are my scans:

>  nmap [my ip address] -p 53 -A

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2009-02-18 13:46 EST
SCRIPT ENGINE: rpcinfo.nse is not a file.
SCRIPT ENGINE: Aborting script scan.
Interesting ports on [my ip address]:
PORT   STATE SERVICE    VERSION
53/tcp open  tcpwrapped

Service detection performed. Please report any incorrect results at [http://insecure.org/nmap/submit/](http://insecure.org/nmap/submit/) .
Nmap done: 1 IP address (1 host up) scanned in 0.167 seconds


> netstat -ant | grep :53
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN     
tcp6       0      0 :::53                   :::*                    LISTEN     

> sudo lsof | grep dnsmasq | grep :
[sudo] password for everyone: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/everyone/.gvfs
      Output information may be incomplete.
dnsmasq   7786    dnsmasq    4u     IPv4      30172                 UDP *:domain 
dnsmasq   7786    dnsmasq    5u     IPv4      30173                 TCP *:domain (LISTEN)
dnsmasq   7786    dnsmasq    6u     IPv6      30174                 UDP *:domain 
dnsmasq   7786    dnsmasq    7u     IPv6      30175                 TCP *:domain (LISTEN)

gmc.com says my ports are stealthed.

Thanks for any help. I'm a relative newbie here.

---

### Post by cdenley on 2009-02-18
You have installed a service which listens for external connections. However, neither of your firewalls should allow such connections. If you uncommented this line
```

listen-address=127.0.0.1

```
then I don't think it would be listening for external connections. Did you miss that step?

---

### Post by gecko3940 on 2009-02-19
Thanks for the reply. By uncomment, I think you mean remove the # at the start of the line??

Here is what I have done with the relevant part of the file /etc/dnsmasq.conf:
> 
# If you want dnsmasq to listen for DHCP and DNS requests only on
# specified interfaces (and the loopback) give the name of the
# interface (eg eth0) here.
# Repeat the line for more than one interface.
# interface=lo 
# Or you can specify which interface _not_ to listen on
# except-interface=
# Or which to listen on by address (remember to include 127.0.0.1 if
# you use this.)
listen-address=127.0.0.1
# If you want dnsmasq to provide only DNS service on an interface,
# configure it as shown above, and then use the following line to
# disable DHCP on it.
#no-dhcp-interface=

# On systems which support it, dnsmasq binds the wildcard address,
# even when it is listening on only some interfaces. It then discards
# requests that it shouldn't reply to. This has the advantage of
# working even when interfaces come and go and change address. If you
# want dnsmasq to really bind only the interfaces it is listening on,
# uncomment this option. About the only time you may need this is when
# running another nameserver on the same machine.
#bind-interfaces

The line "listen-address=127.0.0.1" used to read "# listen-address=" until I changed it.
The line "# interface=lo" used to read "# interface=" but I changed it after reading the last post on the page (post 16). 
The line "#bind-interfaces" was already there; post 16 recommended it also.

With the file as above, I get the readings I posted at the start of this thread.

Thanks for any help you can offer.

---

### Post by cdenley on 2009-02-19
With listen-address set to 127.0.0.1, I would expect it to bind to the interface with that IP, but the netstat output you posted indicated it was binding to 0.0.0.0, which means any network interface. You can try the "interface=lo" line, but according to the comments, that should give you the same result. Are you sure the output hasn't changed? Are you sure you restarted dnsmasq to use the new configuration?
```

sudo /etc/init.d/dnsmasq restart
sudo netstat -tlnp

```

---

### Post by cariboo on 2009-02-19
Just out of curiosity, do you really need to run iptables as well as the firewall in your router? I've been running with only my router firewall for the last 7 years, and never had a problem.

Jim

---

### Post by cdenley on 2009-02-19
> **cariboo907 said:**
> Just out of curiosity, do you really need to run iptables as well as the firewall in your router? I've been running with only my router firewall for the last 7 years, and never had a problem.

Jim

It all depends if you can trust the other computers on your network. If there were other users connected to the router who can have their computer hijacked or something, then you might want a software firewall to protect you from threats on your LAN.

---

### Post by gecko3940 on 2009-02-19
I ran 
> sudo /etc/init.d/dnsmasq restart
sudo netstat -tlnp

> * Restarting DNS forwarder and DHCP server dnsmasq 

> Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:55555         0.0.0.0:*               LISTEN      5003/avgscan    
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN      6197/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5036/cupsd      
tcp6       0      0 :::53                   :::*                    LISTEN      6197/dnsmasq    


I re-ran 
>   nmap [my ip] -p 53 -A

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2009-02-20 07:32 EST
SCRIPT ENGINE: rpcinfo.nse is not a file.
SCRIPT ENGINE: Aborting script scan.
Interesting ports on [my ip]:
PORT   STATE SERVICE    VERSION
53/tcp open  tcpwrapped

Service detection performed. Please report any incorrect results at [http://insecure.org/nmap/submit/](http://insecure.org/nmap/submit/) .
Nmap done: 1 IP address (1 host up) scanned in 0.173 seconds
everyone@Everyone:~$ netstat -ant | grep :53
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN     
tcp        0      0 [my ip]:53         [my ip]:43686                TIME_WAIT  
tcp6       0      0 :::53                   :::*                    LISTEN     
everyone@Everyone:~$ sudo lsof | grep dnsmasq | grep :
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/everyone/.gvfs
      Output information may be incomplete.
dnsmasq   6197    dnsmasq    4u     IPv4      21833                 UDP *:domain 
dnsmasq   6197    dnsmasq    5u     IPv4      21834                 TCP *:domain (LISTEN)
dnsmasq   6197    dnsmasq    6u     IPv6      21835                 UDP *:domain 
dnsmasq   6197    dnsmasq    7u     IPv6      21836                 TCP *:domain (LISTEN)

---

### Post by cdenley on 2009-02-19
After installing dnsmasq and seeing the configuration file in it's entirety, the comments in the portion were rather misleading. The "listen-address" line causes dnsmasq to instantly close connections coming from a different interface, but still binds on the wildcard interface and listens for any connections.

Since the server doesn't actually interact with any remote clients and immediately closes any external connections, this isn't really necessary for security, but uncommenting the "bind-interfaces" line in addition to setting "listen-address" will cause dnsmasq to only listen on 127.0.0.1, which should be expected.
```

$ grep -v ^# /etc/dnsmasq.conf|grep -v '^$'
interface=lo
bind-interfaces
$ sudo lsof -n -i :53
COMMAND   PID    USER   FD   TYPE DEVICE SIZE NODE NAME
dnsmasq 12350 dnsmasq    4u  IPv6 541840       TCP [::1]:domain (LISTEN)
dnsmasq 12350 dnsmasq    5u  IPv6 541841       UDP [::1]:domain 
dnsmasq 12350 dnsmasq    6u  IPv4 541842       TCP 127.0.0.1:domain (LISTEN)
dnsmasq 12350 dnsmasq    7u  IPv4 541843       UDP 127.0.0.1:domain

```

---

### Post by gecko3940 on 2009-02-20
Thanks. I removed # from the "# bind-interfaces" line, restarted dnsmasq and here are my new results:

> 
sudo netstat -tlnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:55555         0.0.0.0:*               LISTEN      5008/avgscan    
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      15126/dnsmasq   
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5041/cupsd      

nmap [my ip] -p 53 -A

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2009-02-21 05:11 EST
SCRIPT ENGINE: rpcinfo.nse is not a file.
SCRIPT ENGINE: Aborting script scan.
Interesting ports on [my ip]:
PORT   STATE  SERVICE VERSION
53/tcp closed domain

Service detection performed. Please report any incorrect results at [http://insecure.org/nmap/submit/](http://insecure.org/nmap/submit/) .
Nmap done: 1 IP address (1 host up) scanned in 0.343 seconds

netstat -ant | grep :53
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN     

sudo lsof | grep dnsmasq | grep :
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/everyone/.gvfs
      Output information may be incomplete.
dnsmasq   15126    dnsmasq    4u     IPv4      46262                 TCP localhost:domain (LISTEN)
dnsmasq   15126    dnsmasq    5u     IPv4      46263                 UDP localhost:domain 

grep -v ^# /etc/dnsmasq.conf|grep -v '^$'
listen-address=127.0.0.1
bind-interfaces

sudo lsof -n -i :53
COMMAND   PID    USER   FD   TYPE DEVICE SIZE NODE NAME
dnsmasq 15126 dnsmasq    4u  IPv4  46262       TCP 127.0.0.1:domain (LISTEN)
dnsmasq 15126 dnsmasq    5u  IPv4  46263       UDP 127.0.0.1:domain 

I seem to now have the 127.0.0.1:53 address on the dnsmasq line and 53/tcp is now closed, which I believe is good. 
But my IPv6 lines are missing and the grep -v ^# /etc/dnsmasq.conf|grep -v '^$' lines don't match your's. 
The netstat -ant | grep :53 results are much shorter.

Is everything ok now?

---

### Post by cdenley on 2009-02-20
> **gecko3940 said:**
> Thanks. I removed # from the "# bind-interfaces" line, restarted dnsmasq and here are my new results:

 

I seem to now have the 127.0.0.1:53 address on the dnsmasq line and 53/tcp is now closed, which I believe is good. 
But my IPv6 lines are missing and the grep -v ^# /etc/dnsmasq.conf|grep -v '^$' lines don't match your's. 
The netstat -ant | grep :53 results are much shorter.

Is everything ok now?

Your configuration seems safe, since your only TCP listener isn't listening for remote connections.

---

### Post by gecko3940 on 2009-02-20
Thanks for your help. This Ubuntu community rocks.

---

