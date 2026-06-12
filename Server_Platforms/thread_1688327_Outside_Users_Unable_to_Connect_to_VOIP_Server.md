---
title: "Outside Users Unable to Connect to VOIP Server"
date: 2011-02-15
forum: Server Platforms
---

### Post by buler on 2011-02-15
I am trying to setup a mumble server ([http://mumble.sourceforge.net/](http://mumble.sourceforge.net/)) on Ubuntu Server 10.10.  I have downloaded/installed all of the necessary files and configured my router to open up the necessary port (64738 ).  However users outside of my network are unable to connect to the server (get Timeout error).  Also to add, I am fairly new to using linux/ubuntu.


I made a post on reddit where you will find more information regarding my problem: [http://www.reddit.com/r/linuxquestions/comments/fggu9/ubuntu_server_1010_portforwarding_not_working/](http://www.reddit.com/r/linuxquestions/comments/fggu9/ubuntu_server_1010_portforwarding_not_working/)

Thank you!

---

### Post by Foeburner on 2011-02-15
Two things: 1. have you tried placing the server on the DMZ to allow all connections to go to the server without the firewall blocking ports and 2. Do you have a static external IP address? For these IP addresses, you'll need a business grade account. If you dont have a static address from your ISP, your users may connect today if configured right but not tomorrow or whenever the lease is up.

---

### Post by arrrghhh on 2011-02-15
Static IP is good, if not dyndns can get around that...

Are the ports open to the WAN?  Specifically 64738.  Do you have a firewall running on the Ubuntu Server?

---

### Post by elico on 2011-02-16
first send us the output of the command
netstat -ntlp
to see the murmur server listening ports.
also.
what about the murmur server ip permissions ?
does it have any restrictions?
if you are trying to run the command
telnet local-server-ip 64738
what do you get?

what is the device?router? that is doing the port-forwarding?
if you can use telnet to the local machine it means not likely problem on the murmur machine but on the routing\port-forwarding.
also to make sure the murmur server configured correctly try to check the settings for the server restrictions.

---

### Post by buler on 2011-02-16
> **Foeburner said:**
> Two things: 1. have you tried placing the server on the DMZ to allow all connections to go to the server without the firewall blocking ports and 2. Do you have a static external IP address? For these IP addresses, you'll need a business grade account. If you dont have a static address from your ISP, your users may connect today if configured right but not tomorrow or whenever the lease is up.

1.  I have tried placing the server on the DMZ, outside users are still unable to connect.
2.  I do not have an external static ip, I however have setup an dydns account

> **arrrghhh said:**
> Static IP is good, if not dyndns can get around that...

Are the ports open to the WAN?  Specifically 64738.  Do you have a firewall running on the Ubuntu Server?

I have opened up the ports necessary for mumble from within the router.  I do have a firewall running on the Ubuntu server.  I used this guide ([http://ubuntuforums.org/showthread.php?t=159661&highlight=firewall]("http://ubuntuforums.org/showthread.php?t=159661&highlight=firewall")), starting at Part 3 "The Scripts".

Here is the output from the command "iptables-save":
```

*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [111:13089]
:FIREWALL - [0:0]
:TRUSTED - [0:0]
-A INPUT -j FIREWALL
-A INPUT -p tcp -m tcp --dport 64738 -j ACCEPT
-A INPUT -p udp -m udp --dport 64738 -j ACCEPT
-A FORWARD -j DROP
-A FIREWALL -i eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FIREWALL -i lo -j ACCEPT
-A FIREWALL -j TRUSTED
-A FIREWALL -j DROP
-A TRUSTED -i eth0 -p tcp -m tcp --dport 25565 -j ACCEPT
-A TRUSTED -i eth0 -p udp -m udp --dport 25565 -j ACCEPT
-A TRUSTED -i eth0 -p tcp -m tcp --dport 64738 -j ACCEPT
-A TRUSTED -i eth0 -p udp -m udp --dport 64738 -j ACCEPT
-A TRUSTED -i eth0 -p tcp -m tcp --dport 6502 -j ACCEPT
-A TRUSTED -i eth0 -p udp -m udp --dport 6502 -j ACCEPT
-A TRUSTED -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT
-A TRUSTED -i eth0 -p udp -m udp --dport 22 -j ACCEPT
COMMIT

```

(you can find more output logs inside the reddit link I posted earlier, I am the user "MagicianNamdGOB")


> **elico said:**
> first send us the output of the command
netstat -ntlp
to see the murmur server listening ports.
also.
what about the murmur server ip permissions ?
does it have any restrictions?
if you are trying to run the command
telnet local-server-ip 64738
what do you get?

what is the device?router? that is doing the port-forwarding?
if you can use telnet to the local machine it means not likely problem on the murmur machine but on the routing\port-forwarding.
also to make sure the murmur server configured correctly try to check the settings for the server restrictions.

- Output from "netstat -ntlp":
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:6502          0.0.0.0:*               LISTEN      766/murmurd
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      841/sshd
tcp6       0      0 :::64738                :::*                    LISTEN      766/murmurd
tcp6       0      0 :::22                   :::*                    LISTEN      841/sshd

```

- I am not sure if there are any IP restrictions.

- Output from "telnet local-server-ip 64738" (using actual ip and then dyndns hostname)

```
telnet: Unable to connect to remote host: Connection refused

```
(for both external ip and hostname)

However, I can connect to the internal server ip.

- The router I am using is: Belkin F5D7234-4v4
Here is a screenshot of the portforward screen [http://i.imgur.com/0QVbT.png]("http://i.imgur.com/0QVbT.png")

Like I said above there are more output logs in the reddit post from in the OP, (I am user: MagicianNamdGOB).  Let me know if you all need more info.  Thanks for the help.

---

### Post by arrrghhh on 2011-02-16
> **buler said:**
> - Output from "netstat -ntlp":
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:6502          0.0.0.0:*               LISTEN      766/murmurd
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      841/sshd
tcp6       0      0 :::64738                :::*                    LISTEN      766/murmurd
tcp6       0      0 :::22                   :::*                    LISTEN      841/sshd

```

- I am not sure if there are any IP restrictions.

- Output from "telnet local-server-ip 64738" (using actual ip and then dyndns hostname)

```
telnet: Unable to connect to remote host: Connection refused

```
(for both external ip and hostname)

However, I can connect to the internal server ip.

Well the telnet test is telling.

I'm also pretty sure you should see 64738 open on IPV4.  Looks like you only have it on V6... I'm definitely venturing into unknown water - I'm not sure how you could enable that only for V6, but that appears to be what's going on.

I've also never used murmurd, do you have to bind it to an IP or interface...?  Perhaps it's not configured correctly.

---

