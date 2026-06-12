---
title: "vnc/ssh server behind nat - detecting real ip"
date: 2010-05-29
forum: Security
---

### Post by dmafcoi on 2010-05-29
broadband cable -> Linksys RTP300 router -> Firestarter -> Ubuntu 10.04 Desktop

sshd and vnc installed and working fine when enabled but the only way is to add my routers ip as a trusted address or add individual port entries for 192.168.15.1... on the linksys i, of course, have the appropriate ports forwarded to the Ubuntu static ip, so basically anyone can try to connect... how can i make the router forward the internet ip of the person trying to connect, so I can lock it down better?

Yes, I'm a newbie, and I think I've done well up to this point, figuring things out... just need a little help for this last bit

Thanks

---

### Post by CharlesA on 2010-05-30
Just go to whatismyip.com from whatever network you are going to be connecting from and add that address as allowed in the firewall, then block everything else.

---

### Post by dmafcoi on 2010-05-30
I appreciate you responding, but it's not that simple, apparently.

let's say i'm using port 2222 for ssh, so I forward port 2222 to my local ip, say 192.168.15.100.
let's say I work for HP and the real ip there is 15.100.217.1.
I can add 15.100.217.1 as a trusted ip address, and I still can't get through.
The firewall is saying the connection is coming from my router (192.168.15.1), so to get it to work, i have to add my router as trusted, which allows anyone to try to connect...

I need to be able to have the router send the correct internet ip address of the person trying to connect.

---

### Post by CharlesA on 2010-05-30
Interesting. What is the rule that you have in place?

Mine looks like this:

```
charles@thor:~$ sudo iptables -L
target     prot opt source               destination
ACCEPT     tcp  --  xxx-xxx-xxx-xxx.static.twtelecom.net  anywhere            tcp dpt:22
```

```
charles@thor:~$ sudo iptables -A INPUT -p tcp -m tcp -s xxx.xxx.xxx.xxx --dport 22 -j ACCEPT
```

Basically it is set to accept any packets on port 22 from the external IP address that I designate. It has worked fine for me.

---

### Post by Bachstelze on 2010-05-30
> **dmafcoi said:**
> 
I need to be able to have the router send the correct internet ip address of the person trying to connect.

The correct internet IP address is the IP of the router. There is no way to achieve what you want to do*, because seen from the outside, the router and the whole network behind it are a single entity.

* That is, before IPv6 becomes commonplace, so what you can do is send an angry letter to your ISP telling them you want IPv6 right now. ;)

---

### Post by mituw16 on 2010-05-30
Personally what I do for my setup is this...

DSL modem ---> ubuntu iptables script i wrote ---> ubuntu with ssh running on a custom port.

Bascially in my modem, I set my ubuntu server as the DMZ host, therefore my ubuntu's firewall blocks everything, and I dont have to worry about port forwarding from the modem to my server. 

I would suggest you take a look at fail2ban if you running ssh.

Personally, I never like firestarter, but if it works for you go for it! When I need a gui for my firewall applications, I usually use GUFW. Although usually i just write my own iptables script :D

Cheers

---

### Post by dmafcoi on 2010-05-30
Mituw16, I'll definitely check out fail2ban and I've never really considered ufw and the gui but will look at them, thanks.

Bachsteilze and CharlesA, thanks, all very helpful.

---

### Post by dmafcoi on 2010-05-30
also i noticed, after testing from several remote machines, that even though i have 192.168.15.1 listed, I still have to add the ip address of the remote machine for the connection to work, so it's all good... i really need to read up on iptables... i also installed fail2ban and i'm using very good passwords, so it's secure enough for a home machine... if someone wants in bad enough, they'll get in no matter wht I do lol, and the most they'll find is my secret recipe for homemade cat treats :P  thanks again

---

### Post by CharlesA on 2010-05-30
Keys would be a better option from a security standpoint, but since you have fail2ban running and are using a strong password, you should be ok. :-)

---

