---
title: "SSH non-default port"
date: 2010-01-25
forum: Server Platforms
---

### Post by munky99999 on 2010-01-25
Currently I'm all patched up and such. If I use a port for ssh for anything other then the default port. It just doesnt work.

Anyone else having this problem?

---

### Post by doas777 on 2010-01-25
just a stab in the dark, did you restart the sshd after changing the port?

---

### Post by munky99999 on 2010-01-25
> **doas777 said:**
> just a stab in the dark, did you restart the sshd after changing the port?

yes :)

changing the port makes 22 not accessible also. im about to check with nmap. just to see. its odd that suddenly all my comps are having this problem.

---

### Post by CharlesA on 2010-01-25
If you change the ssh listening port to something other then 22, port 22 will appear "not accessible." Are you trying to connect when you are on the internal network, or when you are connected remotely?

---

### Post by munky99999 on 2010-01-25
ok nmap comes back with it open.

So i try using the switch.

ssh -p 2222 munky@192.168.0.149

works just fine. Yet

ssh munky@192.169.0.149:2222

just wont work at all. Which seems to be my problem.I'm fairly certain the above worked before something changed?

Am I losing my mind?

---

### Post by CharlesA on 2010-01-25
I believe you need to use the -p switch if ssh is running on a different port.

---

### Post by BkkBonanza on 2010-01-25
SSH uses the first syntax (-p 2222) not the second (:2222). You're probably thinking of browser url syntax or maybe Nautilus based ssh/sftp access.

Note you can tell it to listen on more than one port if you need both open for testing. Just add two directives, one for each port. This is very useful for when you don't have physical access and you want to verify the new one before dropping the old.

---

### Post by 2hot6ft2 on 2010-01-25
Both host and client files will need to be changed so edit both to the same port # along with the hosts firewall.

sshd_config is the configuration file for the OpenSSH server (/etc/ssh/sshd_config).
ssh_config is the configuration file for the OpenSSH client (/etc/ssh/ssh_config).
Make sure not to get them mixed up.
Uncomment the port line in ssh_config and change the port #

I wouldn't use port 2222 or 8888 like is in the guides either.
Find another port to use.

---

### Post by pricetech on 2010-01-25
> **2hot6ft2 said:**
> I wouldn't use port 2222 or 8888 like is in the guides either.
Find another port to use.

49152 to 65535 are designated by IANA as Dynamic / Private ports.

---

### Post by 2hot6ft2 on 2010-01-25
> **pricetech said:**
> 49152 to 65535 are designated by IANA as Dynamic / Private ports.
Right, and for the others this may help [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#Listen on a Non-Standard Port](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#Listen on a Non-Standard Port)
and
[http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)

This is a nice list
[http://www.neohapsis.com/neolabs/neo-ports/neo-ports.html](http://www.neohapsis.com/neolabs/neo-ports/neo-ports.html)

---

### Post by Kemon on 2010-01-25
This may help?

Edit: /etc/ssh/sshd_config
```
sudo vim /etc/ssh/sshd_config
```

Add or edit the port.
Port 22
Port <new port>

```
sudo /etc/init.d/ssh restart
```

I use Port 22 and Port 443.
Port 22 for local and Port 443 from work ^^

---

### Post by pricetech on 2010-01-26
If you want the list directly from the source:

[http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)

---

### Post by doas777 on 2010-01-26
> **pricetech said:**
> If you want the list directly from the source:

[http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)

I miss Jon Postle. but then again, he would hate our model for internet governance. RIP.

---

### Post by bodhi.zazen on 2010-01-26
Why are you changing the port ?

I have found if you secure your ssh server it does not add much to change the port.

Personally I advise you :

1. Use keys and disable passwords.

2. Block ip with multiple log in attempts. You can do this with iptables, denyhosts, fail2ban ...

You then do not really need to change the port and keeping the port at 22 just makes it easier for everyone.

---

### Post by pricetech on 2010-01-26
> **bodhi.zazen said:**
> Why are you changing the port ?

I have found if you secure your ssh server it does not add much to change the port.

While I agree with your advise on securing, he may have another reason for changing the port.

I have mine running on a different port because I only have one external IP which I need to forward to 2 internal IPs.

---

