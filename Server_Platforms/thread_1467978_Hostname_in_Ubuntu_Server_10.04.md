---
title: "Hostname in Ubuntu Server 10.04"
date: 2010-05-01
forum: Server Platforms
---

### Post by Black_Prince on 2010-05-01
First, hello everyone. I'm new to this forum, so if I posted this thread in wrong one, please forgive me.

I've noticed in Ubuntu Lucid (10.04) when I try to change hostname, it won't change.

This is how I done it:

echo server.example.com > /etc/hostname

nano /etc/hosts

Then I put this line:

127.0.1.1       server.example.com

after 

127.0.0.1       localhost

Then I rebooted my system. When I tried to run hostname command, I got this:

root@server:~# hostname
server.example.com
root@server:~# hostname -f
hostname: Name or service not known

So, if anyone knows how to solve this, I would be very thankful. And sorry for my English, I'm from Bosnia & Herzegovina.

---

### Post by hannon on 2010-05-04
The same thing happened to me after I installed a gui(xfce). Being as unskilled as I am I couldn't figure out how to fix it so I just did a clean install but never put the desktop enviorment on and it worked fine.

Sorry I wish I could be of more help.

---

### Post by ghost_ryder35 on 2010-05-04
> **Black_Prince said:**
> First, hello everyone. I'm new to this forum, so if I posted this thread in wrong one, please forgive me.

I've noticed in Ubuntu Lucid (10.04) when I try to change hostname, it won't change.

This is how I done it:

echo server.example.com > /etc/hostname

nano /etc/hosts

Then I put this line:

127.0.1.1       server.example.com

after 

127.0.0.1       localhost

Then I rebooted my system. When I tried to run hostname command, I got this:

root@server:~# hostname
server.example.com
root@server:~# hostname -f
hostname: Name or service not known

So, if anyone knows how to solve this, I would be very thankful. And sorry for my English, I'm from Bosnia & Herzegovina.

```

npope@ubuntu:~$ sudo vi /etc/hosts

```
Replace your current hostname with your new hostname ( i just commented the old one out )
```

#127.0.1.1      ubuntu      ubuntu
127.0.1.1       foo     foo

```
Change /etc/hostname to new hostname
```

npope@ubuntu:~$ sudo vi /etc/hostname

```
```

foo

```
Change hostname
```

npope@ubuntu:~$ sudo hostname foo

```
Log out and back in
```

npope@foo:~$

```

---

### Post by Black_Prince on 2010-05-05
> **ghost_ryder35 said:**
> ```

npope@ubuntu:~$ sudo vi /etc/hosts

```Replace your current hostname with your new hostname ( i just commented the old one out )
```

#127.0.1.1      ubuntu      ubuntu
127.0.1.1       foo     foo

```Change /etc/hostname to new hostname
```

npope@ubuntu:~$ sudo vi /etc/hostname

``````

foo

```Change hostname
```

npope@ubuntu:~$ sudo hostname foo

```Log out and back in
```

npope@foo:~$

```

Well, that was first how I tried it ... As you see in my post, hostname is changed, but when I run command **hostname -f** it says "hostname: Name or service not known". Command **hostname** works fine, and I see right hostname after my username, but I still don't get it why I got **hostname: Name or service not known** even with right entry in /etc/hosts
Anyways, thanks for your help, I switched back to Ubuntu Server 9.10 for some reasons.

---

### Post by capscrew on 2010-05-05
> **Black_Prince said:**
> Well, that was first how I tried it ... As you see in my post, hostname is changed, but when I run command **hostname -f** it says "hostname: Name or service not known". Command **hostname** works fine, and I see right hostname after my username, but I still don't get it why I got **hostname: Name or service not known** even with right entry in /etc/hosts
Anyways, thanks for your help, I switched back to Ubuntu Server 9.10 for some reasons.

The host name is NOT the FQDN (fully qualified domain name).  It is only the *host *part.   So we have a FQDN of: *[I]**server.example.com***[/I] -- the host name is: **[COLOR="Blue"]server[/COLOR]**.

Using this example the correct hostname command should be: ```
sudo echo [COLOR="blue"]server [/COLOR]> /etc/hostname
```

I believe this will also work:```
sudo hostname [COLOR="Blue"]server[/COLOR]
```

---

### Post by Black_Prince on 2010-05-05
> **capscrew said:**
> The host name is NOT the FQDN (fully qualified domain name).  It is only the *host *part.   So we have a FQDN of: *[I]**server.example.com***[/I] -- the host name is: **[COLOR=Blue]server[/COLOR]**.

Using this example the correct hostname command should be: ```
sudo echo [COLOR=blue]server [/COLOR]> /etc/hostname
```I believe this will also work:```
sudo hostname [COLOR=Blue]server[/COLOR]
```

Oh, now I got it... Don't know why I didn't think about it earlier, but in an example that I viewed on howtoforge web site entry for /etc/hosts on Ubuntu Server 10.04 was shown as

```
127.0.1.1 server1.example.com server1
```So that gave correct hostname resolved. Thanks, you finaly made me understand that example, because it wasn't like in 9.xx or 8.xx versions. Maybe after all I do switch to Ubuntu Server 10.04

---

### Post by Black_Prince on 2010-05-05
> **capscrew said:**
> The host name is NOT the FQDN (fully qualified domain name).  It is only the *host *part.   So we have a FQDN of: *[I]**server.example.com***[/I] -- the host name is: **[COLOR=Blue]server[/COLOR]**.

Using this example the correct hostname command should be: ```
sudo echo [COLOR=blue]server [/COLOR]> /etc/hostname
```I believe this will also work:```
sudo hostname [COLOR=Blue]server[/COLOR]
```

Oh, now I got it... Don't know why I didn't think about it earlier, but in an example that I viewed on howtoforge web site entry for /etc/hosts on Ubuntu Server 10.04 was shown as

```
127.0.1.1 server1.example.com server1
```So that gave correct hostname resolved. Thanks, you finaly made me understand that example. Maybe after all I do switch to Ubuntu Server 10.04

---

### Post by capscrew on 2010-05-05
> **Black_Prince said:**
> Oh, now I got it... Don't know why I didn't think about it earlier, but in an example that I viewed on howtoforge web site entry for /etc/hosts on Ubuntu Server 10.04 was shown as

```
127.0.1.1 server1.example.com server1
```So that gave correct hostname resolved. Thanks, you finaly made me understand that example, because it wasn't like in 9.xx or 8.xx versions. Maybe after all I do switch to Ubuntu Server 10.04

Well almost...

The /etc/hosts file is where you map the IP address to the hostname.  It is **_NOT _**where you **define the hostname for the OS**.

---

### Post by Black_Prince on 2010-05-05
> **capscrew said:**
> Well almost...

The /etc/hosts file is where you map the IP address to the hostname.  It is **_NOT _**where you **define the hostname for the OS**.

Well, I said in my first post that my English is bad ... Anyways I got it, thanks.

---

### Post by Medraq on 2010-10-05
Just an FYI for the semi-literate:

I encountered this exact error today & wondered what caused it.  A more thorough re-reading of my [FONT="Fixedsys"]/etc/hosts[/FONT] file resolved the issue.  I had typed "[FONT="Fixedsys"]268[/FONT]" instead of "[FONT="Fixedsys"]168[/FONT]" as one of the octets in my IP address.  Doh!  :redface:

---

### Post by rainofkayos on 2010-11-25
I use local DNS hosted from my router and all my hosts are on .lan

in my hosts file I always move my hostname away from localhost as ubuntu sets that up by default for some reason.

/etc/hosts
127.0.0.1 localhost.localdomain localhost
192.168.6.5 karma.lan karma

/etc/hostname
karma.lan

and granted that your resolv.conf us using files first that should give you the hostname karma when you type hostname (or whatever your hostname would be)

---

### Post by capscrew on 2010-11-25
> **rainofkayos said:**
> I use local DNS hosted from my router and all my hosts are on .lan

So what you are saying here is that the TLD (top level domain for you LAN is: **.lan** and that DNS names (FQDN) are served from the DNS server in your network edge device (the router).> 

in my hosts file I always move my hostname away from localhost as ubuntu sets that up by default for some reason.

That is a good idea.  The hostname *localhost* is the name that should be associated only with the virtual interface.  This is always on the network 127.0.0.0/8.> 

/etc/hosts
127.0.0.1 localhost.localdomain localhost[COLOR="Red"]**<- the hostname goes first: localhost localhost.localdomain**[/COLOR]
192.168.6.5 karma.lan karma [COLOR="red"]**<-The same here. The hostname is karma**[/COLOR]

/etc/hostname
karma.lan [COLOR="red"]**<- This should only have the hostname  (no TLD needed)**[/COLOR]

The above is not correct. See my comments in red.  
The /etc/hostname file should **only **have the hostname.  No .lan is needed.

Note that the /etc/hosts file is a mapping config file primarily for ***hostnames and aliases ***.  The format is important.  This is what the format looks like
```
IP Address <hostname> <alias> 
```
> 

and granted that your resolv.conf us using files first that should give you the hostname karma when you type hostname (or whatever your hostname would be)

Absolutely.  Thats why it is important to have them configured correctly.  Some examples from my host *malibu* below: 

**Commands:**
  
```
$hostname

malibu
```


```

$cat /etc/resolv.conf

# Local LAN DNS
nameserver 192.168.1.1

# Local domain name 
# the suffix (domain.tld)
beachbees.home

# Search list for hostname lookup
# By default this contains only the local domain name.

```

```

$cat /etc/hosts

127.0.0.1 localhost localhost.beachbees.home
192.168.1.12 malibu malibu.beachbees.home
192.168.1.200 printer hp2200

```
Note that the hostname *printer *is still referred to when using the alias *hp2200* in the following:

```

$ ping [COLOR="Blue"]**hp2200**[/COLOR]


PING [COLOR="red"]printer [/COLOR](192.168.1.200) 56(84) bytes of data.
64 bytes from [COLOR="Red"]printer [/COLOR](192.168.1.200): icmp_seq=1 ttl=64 time=8.83 ms
64 bytes from [COLOR="red"]printer [/COLOR](192.168.1.200): icmp_seq=2 ttl=64 time=6.06 ms
64 bytes from [COLOR="red"]printer [/COLOR](192.168.1.200): icmp_seq=3 ttl=64 time=6.06 ms
64 bytes from [COLOR="red"]printer [/COLOR](192.168.1.200): icmp_seq=4 ttl=64 time=6.05 ms

--- printer ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 6.058/6.755/8.832/1.201 ms

```

---

