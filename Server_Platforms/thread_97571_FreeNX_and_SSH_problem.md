---
title: "FreeNX and SSH problem"
date: 2005-12-01
forum: Server Platforms
---

### Post by maol62 on 2005-12-01
I have setup a FreeNX server according to this [page]("http://www.snakeoillabs.com/2005/10/27/freenx-on-ubuntu-breezy-howto/"). I can login from my laptop when I´m on the same LAN and loggin into my 192.168.xxx.xxx address but not from the WAN side when trying the 82.xxx.xxx.xxx address. I have forwarded port 22 from WAN side to my 192.168.xxx.xxx address in the router but i get the connection refused message when trying to connect. When testing the security at Sygates homepage it says that port 22 is open and that it also can see my openssh server running. Any ideas?

---

### Post by cactus on 2005-12-01
Can you connect with regular ssh?
If so..then it is probably the syntax in your ssh key (~/.ssh/authorized_keys). If the ip address is listed as a source..that could pose a problem during the auth of the key...
just a thought..

---

### Post by maol62 on 2005-12-01
No I can not connect with regular ssh. Im using [this]("http://www.oit.duke.edu/sa/security/ssh.html") service to check if I can login from WAN-side but I get Connection Refused. I have even tried to DMZ my 192.168.xxx.xxx address in the router but it doesnt help.

---

### Post by cactus on 2005-12-01
Do you have a firewall on your box..
oh wait..

try adding.. 
"sshd: ALL"
to your /etc/hosts.allow file...without the quotes of course.

---

### Post by maol62 on 2005-12-01
That was the fastest answer ever! Unfortunatly it didnt change anything. Its still connection refused.

---

### Post by maol62 on 2005-12-02
When looking in the file /var/log/auth.log after a successful login from LAN-side, I can se theese rows:

Accepted password for xxxxxxx from 192.168.1.2 port 51662
Accepted password for xxxxxxx from 192.168.1.2 port 51670
Accepted password for xxxxxxx from 192.168.1.2 port 44415

Why are the ports randomly different and why isnt it always port 22 as it should be? Have also tried with other software on my WinXP partition and it is the same problem there. When testing with sygate security test from web I get in the log, when using WinXp, that it has been a connection to port 22 in the server. So it shouldnt be any misconfiguration in the router I think. Sygate also tells me which type of server I run, SSH-2.0-OpenSSH_4.1p1 Debian-7ubuntu4.

---

### Post by cactus on 2005-12-02
it is showing the ephemeral src port, which is...ephemeral. 
With ssh, the destination port is 22. Src port is ephemeral.

things to check: 
your firewall device - make sure it is forwarding destination port 22, tcp. src port any.
your machine - make sure your ssh server allows connections from non-local-subnet ip addresses. make sure any firewall on the server itself...allows this as well.

---

### Post by maol62 on 2005-12-02
Ok, have done a clean install. Havent mentioned it but I also have problems with ipv6 so when I do a reinstall of Ubuntu I have to do the following things to get it to work (im just telling ju this because may be it has something to do with my ssh-problem):
First adding my ISPs DNS:

sudo gedit /etc/resolv.conf

nameserver xxx.xxx.xxx.xxx
nameserver yyy.yyy.yyy.yyy
nameserver 192.168.1.1

Then locking the file:
sudo chattr +i /etc/resolv.conf

Then replacing this row in /etc/modprobe.d/aliases:
alias net-pf-10 ipv6

with this row:
alias net-pf-10 off

Now when that is done, lets deal with the ssh-problem.:) 

> your firewall device - make sure it is forwarding destination port 22, tcp. src port any.
My router is configured to port forward as this:
src ip/mask: 0.0.0.0/0.0.0.0 
dst ip/mask: 192.168.1.2/255.255.255.255
dst port start: 22
dst port end: 22
dst port map: 22
It is enabled and I suppose that the sygate security check wouldnt see my openssh-server if this rule was missing in router.

> your machine - make sure your ssh server allows connections from non-local-subnet ip addresses.
I have added the line sshd: ALL in /etc/hosts.allow according to your suggestion.

> make sure any firewall on the server itself...allows this as well.
Eh, now its a little bit more tricky for a newbee like me. Firestarter is not installed on my system and neither is guarddog. Iptables is installed and this is what a get from it:

sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Any more ideas?

---

### Post by cactus on 2005-12-02
still no ssh? is the sshd daemon running after your fresh install?
/etc/init.d/ssh restart
just for giggles. see if it reports it as having stopped ok, and having started back up.

not sure about your firewall appliance. is the "map" section required? i am kinduv out of ideas at this point. If it works inside, and you have no firewall, and your default gateway is set appropriately, then it *should* work. You might have a funky firewall device..
/me scratches head

Try completely removing the inbound ssh rule, and recreate it...
also, put in the output from a 'route -a' command..see where your default route points to.

EDIT:
dst ip/mask: 192.168.1.2/255.255.255.255  ??
should be a mask of 255.255.255.0 most likely. It *shouldn't* matter, but it *could* cause a routing problem for the device, since it might see it as on another network, and it might not know where to forward it to. Shouldn't be a problem..but who knows how good their firmware is.. lol

Whatever the subnet mask your Lan port on the sygate is set to... use that same subnet mask there too...

---

### Post by maol62 on 2005-12-03
Ok, this is kind of embarassing. I was visiting my friend and from there it was no problems accessing the ssh-server at my computer. I thought the Mindterm Java  SSH client was accessing me from some internet address, but it seems to be just a Java client working on my computer. So, when I try to connect to my public address, 82.xxx.xxx.xxx, I go from my LAN side on port 22 and to my router and back on port 22, and I suppose that this is what the problem is all about, port 22 is already in use by my outgoing connection so therefore I get connection refused. So it doesnt matter if Im using the Java client or just the ssh command, it is the same thing. At least I think this is the problem.
Cactus, sorry for taking up your time with this issue, but thank you very much for the suggestions and for teaching me a lot!

---

### Post by LordHunter317 on 2005-12-03
[QUOTE=maol62]Then locking the file:
sudo chattr +i /etc/resolv.conf[/quote]Don't do this.  This file needs to be able to be edited.  And if you have LAN DNS, why doesn't it forward to your ISP?

[quuote]Then replacing this row in /etc/modprobe.d/aliases:
alias net-pf-10 ipv6

with this row:
alias net-pf-10 off[/quote]Don't do this either.  Out and out disabling IPv6 won't solve anything.

---

### Post by cactus on 2005-12-03
[QUOTE=maol62]Cactus, sorry for taking up your time with this issue, but thank you very much for the suggestions and for teaching me a lot![/QUOTE]

lol..no problem. ;)
Glad you are working, and figured it out.

---

