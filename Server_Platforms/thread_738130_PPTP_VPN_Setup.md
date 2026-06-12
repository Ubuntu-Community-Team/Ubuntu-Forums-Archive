---
title: "PPTP VPN Setup"
date: 2008-03-28
forum: Server Platforms
---

### Post by ryazkhan on 2008-03-28
Hello everyone. I am new to this forum and because I am playing with ubuntu server and doing some things write and having problem with some things so I decide to join this form so I can share what I have and can get help where I need. So I would like to start with getting help:

My current problem is with VPN server setup:
I setup PPTPD server and it is working but I am having problem with internet after I connect to my vpn server client loose internet connection but vpn remain alive not sure about server internet it will probably still be online. Here is my general config

I edited */etc/pptpd.conf *and I put two addresses like [COLOR="Blue"]localip[/COLOR] and [COLOR="blue"]remoteip  [/COLOR]

then I edited   */etc/ppp/options *file and added two dns in there

then I edited */etc/ppp/chap-secrets* to put user IDs and passwords.

and last I edit */etc/sysctrl.conf* to put this line in it.
*net.ipv4.conf.default.forwarding=1*. I am sorry if I am confusing

Any help would be appreciated 
Thanks in advance to all

---

### Post by farahbod on 2008-03-30
As i told you (in another thread) this is mostly because you send all your traffic through the vpn.
For example built-in vpn connection in windows xp route all your traffic through the tunnel.

If you use windows to connect run this:
```
route print
```

You only need to add new route and change default route back!

---

### Post by ryazkhan on 2008-03-31
Thanks for your help!
I understand that but not sure how to add route. I know it is missing default gateway or some thing and has to do with static route but....
please provide me the exact lines to put if possible

Any help would be appreciated!
just for info when I do *route* to see the gw etc I am just getting gateway for my eth0 which is vpn server itself but nothing for ppp0 which is actual tunnel.
Thanks

---

### Post by ryazkhan on 2008-04-01
I kind of solved my problem my self. While configuring VPN on client I just uncheck that option what says use gateway of server. It is working fine now without any problem. What I did is:
> After setting VPN connection in XP. I right click on it-->Went to properties--> Networking-->TCP/IP-->Properties-->Advance-->General-->Unchecked use default gateway on remote networkThat is it my connection and internet is stable, however I cannot expand my domain but I can brows all computer by name. I want to logon to domain from any where using VPN connection but some how I am not able to do that it say domain is not available but I am able to do all rest like mapping drives etc. Any help about that!!! This is not my requirement for any thing this is just learning since I am networking student

---

### Post by kafitz22 on 2008-04-01
I followed the advice presented here:
[http://ubuntuforums.org/showpost.php?p=4604824&postcount=11](http://ubuntuforums.org/showpost.php?p=4604824&postcount=11)

 which got my internet working without disabling the gateway like that. If I'm correct, what you did just disables the forwarding of internet traffic through the VPN so you're not actually using the VPN at all. After doing the steps presented here (I had to create a password for root and login as that instead of just sudo for the first step, but it seemed to fix internet browsing for me. Now to just get my Windows shares working through the VPN instead having to use the IP.

---

### Post by ryazkhan on 2008-04-02
I think u getting it wrong I just make my client to not to use remote gateway and use its current gateway for internet. I can successfully VPN in my ubuntu machine from any where in the world and can make a secure tunnel. I can do all this like access (browse) all of my PCs from my network using their name instead of IPs. I can map drives of my Network shares etc. My problem is I want to logon in that domain using VPN connections which is possible I did that when I was using windows server 2003 VPN.

---

### Post by Deathrend on 2008-04-02
You should move away from PPTP VPN, towards either an SSL vpn, or atleast an L2p, PPTP offers zero encryption, it's like Telnet Vs. SSH.

You should try something like sslexplorer, or OpenVPN, both very good products, and free.

---

### Post by farahbod on 2008-04-02
Here VPN itself works as a connection to the private network.
If you can reach (ping them for example) other servers in that network (specially DC, DNS, WINS) then probably you must define their addresses manully in the vpn connection advanced settings.

But if you cannot reach others, then you have to configure your ubuntu server properly(enable proxyarp and packet forwarding).


And about the routes, which you asked before, just type route and follow the instructions.
ex:
```
route add 192.168.10.0 mask 255.255.255.0 192.168.10.1 metric 5 if 1
```

---

### Post by djdavies75 on 2008-04-10
> **Deathrend said:**
> You should move away from PPTP VPN, towards either an SSL vpn, or atleast an L2p, PPTP offers zero encryption, it's like Telnet Vs. SSH.

You should try something like sslexplorer, or OpenVPN, both very good products, and free.

Your telnet versus SSH analogy is invalid for PPTP versus others; PPTP certainly offers encryption, and the resulting security is decent if strong password requirements are in place.

Now, whether it utilizes the best encryption technology is an entirely separate question. However, PPTP clients are built into nearly all operating systems nowadays, and the server piece is part of Windows server operating systems, so I do not expect PPTP to die any time soon.

---

### Post by farahbod on 2008-04-11
thanks djdavies75

---

