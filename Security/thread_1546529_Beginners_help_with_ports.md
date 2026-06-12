---
title: "Beginners help with ports"
date: 2010-08-05
forum: Security
---

### Post by spillage2 on 2010-08-05
Hello all.

Very new to linux and have been trying to set up file sharing, vnc trying to understand doing this through ssh :icon_frown: I am worried I may have ports opened that I shouldn't.

have run netstat -tupl and have this output

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:33030         *:*                     LISTEN      2211/ssl_esock  
tcp        0      0 localhost:ipp           *:*                     LISTEN      1233/cupsd      
tcp        0      0 localhost:41821         *:*                     LISTEN      2158/beam.smp   
tcp6       0      0 [::]:netbios-ssn        [::]:*                  LISTEN      854/smbd        
tcp6       0      0 [::]:5900               [::]:*                  LISTEN      1643/vino-server
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN      1233/cupsd      
tcp6       0      0 [::]:microsoft-ds       [::]:*                  LISTEN      854/smbd        
udp        0      0 *:mdns                  *:*                                 911/avahi-daemon: r
udp        0      0 192.168.0.2:netbios-ns  *:*                                 1961/nmbd       
udp        0      0 *:netbios-ns            *:*                                 1961/nmbd       
udp        0      0 192.168.0.2:netbios-dgm *:*                                 1961/nmbd       
udp        0      0 *:netbios-dgm           *:*                                 1961/nmbd       
udp        0      0 *:54453                 *:*                                 911/avahi-daemon: r
udp        0      0 *:bootpc                *:*                                 1369/dhclient
```  

I have firestarter running but can any tell me if there is anything here I need to worry about as my old windows set up using outpost kinda made me feel that all was safe.

Thanks 

Spill.

---

### Post by Rubi1200 on 2010-08-05
**[SIZE=4][COLOR=#8b0000][B][COLOR=#8b0000][SIZE=2]> [B][SIZE=4][COLOR=#8b0000][B][COLOR=#8b0000][SIZE=2]The two most common cracks posted on these forums are ssh and vnc, both running with password authentication[/SIZE][/COLOR]**[/COLOR][/SIZE][/B][/SIZE][/COLOR][/B][/COLOR][/SIZE][/B]
 
[COLOR=#8b0000][SIZE=4]**[B][COLOR=#8b0000][SIZE=2]> [COLOR=#8b0000][SIZE=4][B][B][COLOR=#8b0000][SIZE=2]If you wish to run these services, please secure them[/SIZE][/COLOR]**[/B][/SIZE][/COLOR][/SIZE][/COLOR][/B][/B][/SIZE][/COLOR]
 
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
 
[[COLOR=#444444]Ubuntu wiki, Community - SSH guide[/COLOR]]("https://help.ubuntu.com/community/SSH")
 
[[COLOR=#444444]Ubuntu Security Guide - UFW[/COLOR]]("https://help.ubuntu.com/10.04/serverguide/C/firewall.html")
 
[[COLOR=#444444]Ubuntu wiki community - UFW (Configure your firewall [iptables] )[/COLOR]]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw")
 
Very useful command:
 
```
 
sudo lsof -i -n -P

```

---

### Post by spillage2 on 2010-08-05
thanks for the useful links. I have blocked port 80 as not yet running any web servers but even though i have two comps on my network and have set ufw to block port 80 on both nmap still shows them as open.

---

### Post by espressobeanie on 2010-08-05
Spillage, 

What does the output of this command show you on your server and two clients?

> ufw status

Also, check to see that your ufw default for incoming connections is set to deny.

---

### Post by rookcifer on 2010-08-06
> **spillage2 said:**
> thanks for the useful links. I have blocked port 80 as not yet running any web servers but even though i have two comps on my network and have set ufw to block port 80 on both nmap still shows them as open.

Are you scanning the machine from the same machine?  That is

```
nmap 127.0.0.1
```

??  If so, that isn't going to give an accurate "reading."  You're going to need to scan the machines from outside.

---

### Post by spillage2 on 2010-08-07
yes i was scanning from with the same network. after using putty on a mobile the results showed only one port which was closed so it should all be good. 

thanks for all the advice.

---

