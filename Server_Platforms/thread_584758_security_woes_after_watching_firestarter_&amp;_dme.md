---
title: "security woes after watching firestarter &amp; dmesq logs"
date: 2007-10-21
forum: Server Platforms
---

### Post by django_sr on 2007-10-21
Hi folks,

I'm currently experiencing some issues with regard to firestarter and some open ports I have and I don't know how to asses them.

I had ubuntu 7.04 installed and had opened port 4662, 4672 for using amule. Then a few days ago I completely installed the new gutsy gibbon and now when I look into firestarter, I get the following info under blocked connections:

Time: Oct 21 12:37:37 Source: 83.113.14.169 Destination: 192.168.1.104 In IF: eth0 Out IF:  Port: 4662 Length: 48 ToS: 0x00 Protocol: TCP Service: eDonkey

It is strange because I havent installed amule yet and I have bloked all ports in the firewall on the gutsy machine.

In dmesg I'm seeing this:
 dmesg | grep 83.113.14.169
[80713.812000] Inbound IN=eth0 OUT= MAC=00:04:76:21:89:43:00:13:49:89:d6:1e:08:00 SRC=83.113.14.169 DST=192.168.1.104 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=28155 DF PROTO=TCP SPT=2030 DPT=4662 WINDOW=65535 RES=0x00 SYN URGP=0 
[80716.792000] Inbound IN=eth0 OUT= MAC=00:04:76:21:89:43:00:13:49:89:d6:1e:08:00 SRC=83.113.14.169 DST=192.168.1.104 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=28393 DF PROTO=TCP SPT=2030 DPT=4662 WINDOW=65535 RES=0x00 SYN URGP=0 
[80722.824000] Inbound IN=eth0 OUT= MAC=00:04:76:21:89:43:00:13:49:89:d6:1e:08:00 SRC=83.113.14.169 DST=192.168.1.104 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=28839 DF PROTO=TCP SPT=2030 DPT=4662 WINDOW=65535 RES=0x00 SYN URGP=0 
[84277.936000] Inbound IN=eth0 OUT= MAC=00:04:76:21:89:43:00:13:49:89:d6:1e:08:00 SRC=83.113.14.169 DST=192.168.1.104 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=54982 DF PROTO=TCP SPT=1104 DPT=4662 WINDOW=65535 RES=0x00 SYN URGP=0 
[84280.916000] Inbound IN=eth0 OUT= MAC=00:04:76:21:89:43:00:13:49:89:d6:1e:08:00 SRC=83.113.14.169 DST=192.168.1.104 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=55331 DF PROTO=TCP SPT=1104 DPT=4662 WINDOW=65535 RES=0x00 SYN URGP=0 
[84286.852000] Inbound IN=eth0 OUT= MAC=00:04:76:21:89:43:00:13:49:89:d6:1e:08:00 SRC=83.113.14.169 DST=192.168.1.104 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=55954 DF PROTO=TCP SPT=1104 DPT=4662 WINDOW=65535 RES=0x00 SYN URGP=0 

What does this all mean?
Does those logs mean that a computer is trying desperately to connect to port 4662?
Am I hackable (if there is a backdoor in amule and I have those ports open?
What is the best way to setup everything to be as secure as possible? Must I switch to a DMZ setup?

Thanks in advanced

---

### Post by kast on 2007-10-21
You would be hackable if any application you have installed has a back-door and you have an open port to it.

Not to  sure if what I'm seeing in your Log/dmesg is anything to worry about, but what I do is open the port in my Router when I need to use that application (Frostwire) and then close it after, instead of just leaving it open all the time. that is one way of making yourself a little  more secure, even if it does rely on the constant open/close of the port.

Also I run **OpenSSH** that I use when I'm at work to connect home, when I get home I close the port, but there is always logs of people trying to get in!  There is a good chance someone is scanning both are I.P's as I'm typing :)

---

### Post by robert_pectol on 2007-10-21
> **django_sr said:**
> Hi folks,

I'm currently experiencing some issues with regard to firestarter and some open ports I have and I don't know how to asses them.

What makes you think the ports are open?

> **django_sr said:**
> 
I had ubuntu 7.04 installed and had opened port 4662, 4672 for using amule. Then a few days ago I completely installed the new gutsy gibbon and now when I look into firestarter, I get the following info under blocked connections:

Time: Oct 21 12:37:37 Source: 83.113.14.169 Destination: 192.168.1.104 In IF: eth0 Out IF:  Port: 4662 Length: 48 ToS: 0x00 Protocol: TCP Service: eDonkey

Ok, so your firewall is blocking access attempts.  Nothing strange there.  Just because someone tries to access your ports does NOT mean that those port(s) are open.

> **django_sr said:**
> It is strange because I havent installed amule yet and I have bloked all ports in the firewall on the gutsy machine.

...Which is why your firewall logs are showing blocked connection attempts!  Whether or not you have installed amule on the new installation has no bearing.  The fact is, someone is trying to connect and they are being blocked.  Did you expect anything different?  Since you ran amule in the past (or any of the P2P networking softwares), your IP has been cached by other P2P clients as being part of the dynamic P2P network.  This is why you are seeing connection attempts, even though you aren't currently running amule.  Eventually your IP will become stale in their caches and will probably fall off of their lists.  Only then will the connection attempts stop.  That's just the way P2P networks operate.

> **django_sr said:**
> In dmesg I'm seeing this:
 dmesg | grep 83.113.14.169
[80713.812000] Inbound IN=eth0 OUT= MAC=00:04:76:21:89:43:00:13:49:89:d6:1e:08:00 SRC=83.113.14.169 DST=192.168.1.104 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=28155 DF PROTO=TCP SPT=2030 DPT=4662 WINDOW=65535 RES=0x00 SYN URGP=0 
[80716.792000] Inbound IN=eth0 OUT= MAC=00:04:76:21:89:43:00:13:49:89:d6:1e:08:00 SRC=83.113.14.169 DST=192.168.1.104 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=28393 DF PROTO=TCP SPT=2030 DPT=4662 WINDOW=65535 RES=0x00 SYN URGP=0 
[80722.824000] Inbound IN=eth0 OUT= MAC=00:04:76:21:89:43:00:13:49:89:d6:1e:08:00 SRC=83.113.14.169 DST=192.168.1.104 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=28839 DF PROTO=TCP SPT=2030 DPT=4662 WINDOW=65535 RES=0x00 SYN URGP=0 
[84277.936000] Inbound IN=eth0 OUT= MAC=00:04:76:21:89:43:00:13:49:89:d6:1e:08:00 SRC=83.113.14.169 DST=192.168.1.104 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=54982 DF PROTO=TCP SPT=1104 DPT=4662 WINDOW=65535 RES=0x00 SYN URGP=0 
[84280.916000] Inbound IN=eth0 OUT= MAC=00:04:76:21:89:43:00:13:49:89:d6:1e:08:00 SRC=83.113.14.169 DST=192.168.1.104 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=55331 DF PROTO=TCP SPT=1104 DPT=4662 WINDOW=65535 RES=0x00 SYN URGP=0 
[84286.852000] Inbound IN=eth0 OUT= MAC=00:04:76:21:89:43:00:13:49:89:d6:1e:08:00 SRC=83.113.14.169 DST=192.168.1.104 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=55954 DF PROTO=TCP SPT=1104 DPT=4662 WINDOW=65535 RES=0x00 SYN URGP=0 

What does this all mean?
Does those logs mean that a computer is trying desperately to connect to port 4662?

Well, I don't know about, "desperately" but yeah, it's showing that 6 TCP connection attempts were made to your port 4662.  They are just your standard connection attempts from an external client.  Nothing to be too concerned about.

> **django_sr said:**
> Am I hackable (if there is a backdoor in amule and I have those ports open?

If you were to install a compromised version of any software that contained a back door, then yes.  You would be, "hackable."  <--- I hate that term by the way!  :-)

> **django_sr said:**
> What is the best way to setup everything to be as secure as possible?

Only run trusted software.  Keep up on security updates.  Only run necessary software, especially if it opens any ports and binds to your external interface to offer services to the 'Net.  Understand exactly what services you are providing (and on what ports) to the external world and if necessary, use a firewall to give you tighter control over access to those services.  The list goes on but those are probably near the top.

> **django_sr said:**
> Must I switch to a DMZ setup?

No.  Although you can if you like.  Just be aware that by doing so, you're effectively putting yourself outside of the protection of your NAT router/firewall.  In some instances this may be exactly what you want but if you're not sure, then it probably isn't.

---

