---
title: "Slow ping and ssh from ubuntu; fast from windows"
date: 2012-04-16
forum: Server Platforms
---

### Post by kedomingo on 2012-04-16
I have googled the issue and most suggest that this is a problem with ping's reverse DNS lookup and an -n option will solve this. However, ping is not the only problem but ssh as well.

To illustrate, I have 2 clients on the same network: let's call them UBU(10.0.0.106) and WIN(10.0.0.103) -- Ubuntu 11 and Windows 7 respectively. The following settings are the same for both machines:

[FONT="Courier New"]
Gateway: 10.0.0.1
DNS: 10.0.0.1, 10.0.0.50
[/FONT]

Pinging a FQDN from WIN is fast as expected but from UBU, it is verrry slow. This can be sped-up by disabling reverse DNS lookup of ping:

[FONT="Courier New"]
**vgm@sandbox ~ $** ping -n example.com -c 4
64 bytes from x.x.x.x: icmp_req=1 ttl=49 time=210 ms
64 bytes from x.x.x.x: icmp_req=2 ttl=49 time=206 ms
64 bytes from x.x.x.x: icmp_req=3 ttl=49 time=208 ms
64 bytes from x.x.x.x: icmp_req=4 ttl=49 time=220 ms
[/FONT]

An ssh connection from WIN to the same FQDN is also fast, but from UBU, it is painfully slow (the server responds after about 10-60 seconds). I also already turned reverse dns lookup from the server i'm ssh-ing to (using UseDNS). Note that this server i'm connecting to is not on the local network but somewhere in the UK and assumed to be properly set up.

[FONT="Courier New"]
**vgm@sandbox ~ $** time ssh [email]example@example.com[/email]
[email]example@example.com[/email]'s password:


real    0m**43.788**s
user    0m0.012s
sys     0m0.004s
[/FONT]

*From the remote machine:*
[FONT="Courier New"]
# cat /etc/ssh/sshd_config | grep DNS
UseDNS no
[/FONT]

Although hostname lookup is fast from UBU:

[FONT="Courier New"]
**vgm@sandbox ~ $** time host example.com
example.com has address x.x.x.x
example.com mail is handled by 0 mail4.atlanticbt.com.

real    0m0.481s
user    0m0.000s
sys     0m0.012s
[/FONT]

Firewall is also disabled on both machines.

Could you guys give me some insights why this is happening?

[COLOR="DimGray"]*(*I have replaced my FQDN with example.com)*[/COLOR]

---

### Post by sj1410 on 2012-04-17
there are 2 tweaks which helped me for slow ssh connection,

[Fix for slow SSH connection]("http://www.techpage3.com/2012/04/fix-for-slow-ssh-connection.html")

---

