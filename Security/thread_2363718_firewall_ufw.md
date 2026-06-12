---
title: "firewall ufw"
date: 2017-06-13
forum: Security
---

### Post by arnauldd on 2017-06-13
Hello,

I am using the ubuntu ufw firewall. I ran a firewall test and the results showed this :

GRC Port Authority Report created on UTC: 2017-06-13 at 15:08:14


Results from scan of ports: 0-1055


   18 Ports Open
 1035 Ports Closed
    3 Ports Stealth
---------------------
 1056 Ports Tested


Ports found to be OPEN were: 22, 53, 80, 110, 443, 500, 501, 
                             502, 600, 601, 602, 603, 604, 605, 
                             606, 607, 608, 609


Ports found to be STEALTH were: 137, 139, 445


Other than what is listed above, all ports are CLOSED.


TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - A PING REPLY (ICMP Echo) WAS RECEIVED.

should I worry of anything ? close the open ports ? How ?

Thank you,

Arnauld

---

### Post by KenUBF on 2017-06-14
Hi arnauldd. Do you have any programs running in the background that might be responding to the website's pings? Have you checked the status of your firewall? To do that find the Terminal program and type the following. Copy/paste if you want: ```
sudo ufw status verbose
```

Then enter your password when it asks. 

If your firewall is on it should have an output like this:
```

Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip
```

Finally, when running these tests are you behind a router?

Once you do that we can go from there.

---

### Post by Habitual on 2017-06-14
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW) discusses the subject and particularly [https://help.ubuntu.com/community/UFW#Services](https://help.ubuntu.com/community/UFW#Services).
Hope that helps

---

### Post by arnauldd on 2017-06-15
thanks KenUBF,

I ran ```
sudo ufw status verbose
```

and got :

```
$sudo ufw status verbose [sudo] password for arnauld:    Status: active Logging: on (low) Default: deny (incoming), allow (outgoing), deny (routed) New profiles
```

I am behin a router.

---

### Post by arnauldd on 2017-06-15
thanks Habitual[COLOR=#000000][/COLOR]
.

---

### Post by KenUBF on 2017-06-15
Hi arnauldd,

OK. Thanks for that output. So I see your firewall is on with default settings. That's good. To figure out why there are open ports I'd like to check a few more things. First, I'd like to see what programs are listening for incoming connections. So if you would, please open  the Terminal again and type:

```

sudo netstat -lp 

```

Then please paste the output here, just for the top section that says 'Active Internet connections'. I don't believe I need the other section which would be called 'Active UNIX domain sockets'.

After that, I'd you to run the Shield's Up again. I was wondering if perhaps it tested another IP address that wasn't your machine. 

To see what IP address you have, in the Terminal type:

```

ifconfig

```

And post the output here. That will provide all of your network interfaces. ***For privacy reasons you can erase maybe the last set of numbers if you don't feel comfortable posting your entire IP address here.*** Personally, I would make sure you do that. But check to make sure your IP address listed and the one being scanned by Shield's Up are the same. Finally, could you post a screenshot of the Shield's Up results so I can see exactly which ports are open and whatnot so I can compare with the output of netstat? 

Thanks!

---

### Post by KenUBF on 2017-06-15
I forgot that you mentioned you were behind a router, which when scanning with Shield's Up, it will scan the IP address given to you by your ISP, not your computer's IP. So if they are different in Shield's Up and what appears in ifconfig that will be why. So that means it is the ports on your router that are being scanned, not your Linux firewall. Do you have a firewall built into your router?

---

### Post by arnauldd on 2017-06-16
Hello KenUBF,

so, after > sudo netstat -lp I get :

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 0.0.0.0:12326           0.0.0.0:*               LISTEN      13527/skype         
tcp        0      0 0.0.0.0:hostmon         0.0.0.0:*               LISTEN      5380/systemd-resolv 
tcp        0      0 0.0.0.0:4242            0.0.0.0:*               LISTEN      7390/java           
tcp        0      0 localhost:4243          0.0.0.0:*               LISTEN      7390/java           
tcp        0      0 0.0.0.0:46484           0.0.0.0:*               LISTEN      5994/rslsync        
tcp        0      0 arnauld-Alienwar:domain 0.0.0.0:*               LISTEN      6960/dnsmasq        
tcp        0      0 localhost:domain        0.0.0.0:*               LISTEN      5380/systemd-resolv 
tcp        0      0 localhost:12534         0.0.0.0:*               LISTEN      16930/mono          
tcp        0      0 0.0.0.0:19511           0.0.0.0:*               LISTEN      7983/rslsync        
tcp        0      0 localhost:ipp           0.0.0.0:*               LISTEN      2226/cupsd          
tcp        0      0 localhost:8888          0.0.0.0:*               LISTEN      5994/rslsync        
tcp        0      0 localhost:36601         0.0.0.0:*               LISTEN      14001/Cryptomator   
tcp        0      0 0.0.0.0:smtp            0.0.0.0:*               LISTEN      5617/master         
tcp        0      0 localhost:9050          0.0.0.0:*               LISTEN      5957/tor            
tcp        0      0 0.0.0.0:42427           0.0.0.0:*               LISTEN      14001/Cryptomator   
tcp        0      0 0.0.0.0:db-lsp          0.0.0.0:*               LISTEN      6238/dropbox        
tcp        0      0 localhost:31742         0.0.0.0:*               LISTEN      6287/ruby           
tcp        0      0 localhost:40511         0.0.0.0:*               LISTEN      16930/mono          
tcp        0      0 localhost:31743         0.0.0.0:*               LISTEN      6287/ruby           
tcp        0      0 localhost:17600         0.0.0.0:*               LISTEN      6238/dropbox        
tcp        0      0 localhost:17603         0.0.0.0:*               LISTEN      6238/dropbox        
tcp        0      0 localhost:31749         0.0.0.0:*               LISTEN      7452/openvpn        
tcp6       0      0 [::]:hostmon            [::]:*                  LISTEN      5380/systemd-resolv 
tcp6       0      0 [::]:46484              [::]:*                  LISTEN      5994/rslsync        
tcp6       0      0 ip6-localhost:ipp       [::]:*                  LISTEN      2226/cupsd          
tcp6       0      0 [::]:19511              [::]:*                  LISTEN      7983/rslsync        
tcp6       0      0 [::]:smtp               [::]:*                  LISTEN      5617/master         
tcp6       0      0 [::]:db-lsp             [::]:*                  LISTEN      6238/dropbox        
udp        0      0 arnauld-Alienware:41434 0.0.0.0:*                           5994/rslsync        
udp        0      0 0.0.0.0:ipp             0.0.0.0:*                           2249/cups-browsed   
udp        0      0 arnauld-Alienware:41746 0.0.0.0:*                           7983/rslsync        
udp        0      0 arnauld-Alienware:33565 0.0.0.0:*                           7983/rslsync        
udp        0      0 0.0.0.0:17500           0.0.0.0:*                           6238/dropbox        
udp        0      0 arnauld-Alienware:42678 0.0.0.0:*                           7983/rslsync        
udp        0      0 0.0.0.0:1900            0.0.0.0:*                           5994/rslsync        
udp        0      0 0.0.0.0:1900            0.0.0.0:*                           7983/rslsync        
udp        0      0 0.0.0.0:19511           0.0.0.0:*                           7983/rslsync        
udp        0      0 0.0.0.0:44700           0.0.0.0:*                           2147/avahi-daemon:  
udp        0      0 arnauld-Alienware-:3838 0.0.0.0:*                           7983/rslsync        
udp        0      0 arnauld-Alienware-:3838 0.0.0.0:*                           7983/rslsync        
udp        0      0 localhost:3838          0.0.0.0:*                           7983/rslsync        
udp        0      0 arnauld-Alienware-:3838 0.0.0.0:*                           7983/rslsync        
udp        0      0 0.0.0.0:3838            0.0.0.0:*                           7983/rslsync        
udp        0      0 arnauld-Alienware-:3838 0.0.0.0:*                           5994/rslsync        
udp        0      0 arnauld-Alienware-:3838 0.0.0.0:*                           5994/rslsync        
udp        0      0 localhost:3838          0.0.0.0:*                           5994/rslsync        
udp        0      0 arnauld-Alienware-:3838 0.0.0.0:*                           5994/rslsync        
udp        0      0 0.0.0.0:3838            0.0.0.0:*                           5994/rslsync        
udp        0      0 0.0.0.0:36663           0.0.0.0:*                           7452/openvpn        
udp        0      0 0.0.0.0:4000            0.0.0.0:*                           13614/QQ.exe        
udp        0      0 0.0.0.0:4001            0.0.0.0:*                           13614/QQ.exe        
udp        0      0 0.0.0.0:4002            0.0.0.0:*                           13614/QQ.exe        
udp        0      0 0.0.0.0:12326           0.0.0.0:*                           13527/skype         
udp        0      0 0.0.0.0:37517           0.0.0.0:*                           6960/dnsmasq        
udp        0      0 localhost:54153         0.0.0.0:*                           5994/rslsync        
udp        0      0 0.0.0.0:mdns            0.0.0.0:*                           22810/libpepflashpl 
udp        0      0 0.0.0.0:mdns            0.0.0.0:*                           6781/pia_nw         
udp        0      0 0.0.0.0:mdns            0.0.0.0:*                           2147/avahi-daemon:  
udp        0      0 0.0.0.0:hostmon         0.0.0.0:*                           5380/systemd-resolv 
udp        0      0 0.0.0.0:46484           0.0.0.0:*                           5994/rslsync        
udp        0      0 arnauld-Alienware:38920 0.0.0.0:*                           5994/rslsync        
udp        0      0 localhost:48394         0.0.0.0:*                           13527/skype         
udp        0      0 arnauld-Alienware:48955 0.0.0.0:*                           5994/rslsync        
udp        0      0 arnauld-Alienwar:domain 0.0.0.0:*                           6960/dnsmasq        
udp        0      0 localhost:domain        0.0.0.0:*                           5380/systemd-resolv 
udp        0      0 0.0.0.0:bootpc          0.0.0.0:*                           6946/dhclient       
udp        0      0 arnauld-Alienware-1:ntp 0.0.0.0:*                           7335/ntpd           
udp        0      0 arnauld-Alienware-1:ntp 0.0.0.0:*                           7335/ntpd           
udp        0      0 localhost:ntp           0.0.0.0:*                           7335/ntpd           
udp        0      0 0.0.0.0:ntp             0.0.0.0:*                           7335/ntpd           
udp        0      0 localhost:49280         0.0.0.0:*                           7983/rslsync        
udp6       0      0 [::]:19511              [::]:*                              7983/rslsync        
udp6       0      0 [::]:36478              [::]:*                              2147/avahi-daemon:  
udp6       0      0 [::]:mdns               [::]:*                              2147/avahi-daemon:  
udp6       0      0 [::]:hostmon            [::]:*                              5380/systemd-resolv 
udp6       0      0 [::]:46484              [::]:*                              5994/rslsync        
udp6       0      0 [::]:ntp                [::]:*                              7335/ntpd           
raw6       0      0 [::]:ipv6-icmp          [::]:*                  7           2199/NetworkManager 
Active UNIX domain sockets (only servers)
...

```

I didn't run the Shield's Up again, because, as you said, I am behind a router. I didn't realize that Shield's Up was scanning my router and not my computer. So I guess that if ufw is on with the default settings ```
Default: deny (incoming), allow (outgoing)
``` 
I am safe, don't you think ?

I have no idea if my router has a built in firewall, will check it this week-end.

---

### Post by ChuangTzu on 2017-06-16
this is a good standard ufw setting:

```
sudo ufw enable
sudo ufw default deny
sudo ufw deny ssh
```

---

### Post by arnauldd on 2017-06-26
thank you @ChuangTzu.

---

