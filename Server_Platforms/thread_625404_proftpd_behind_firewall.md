---
title: "proftpd behind firewall"
date: 2007-11-27
forum: Server Platforms
---

### Post by Phulerock on 2007-11-27
my testing system is in the model:
proftpd(192.168.0.38) -- eth0 [firewall] eth1_pppoe_mode -- internet

proftpd with network configuration is below
Port            21
PassivePorts                 49152 65534
MasqueradeAddress             phulerock.no-ip.info

firewall using shorewall with NAT for FTP
DNAT net loc:192.168.0.38:21  tcp 21
DNAT net loc:192.168.0.38:20  tcp 20

trouble: connect from LAN is ok . But from internet, after entry user/pass, ftp client can not received the response from server,
bug here:
331 Password required for sauron.
Password:
230 welcome !!!
ftp> ls
200 PORT command successful
...
--> and nothing happen

is PassivePorts and MasqueradeAddress enough ? anyone help me to  configure passive mode behind firewall.

I follow the link [http://ubuntuforums.org/showthread.php?t=79588]("http://ubuntuforums.org/showthread.php?t=79588")
but proftpd still cant connect from internet

[SIZE="7"]**SOS**[/SIZE]

---

### Post by HermanAB on 2007-11-28
Hmm, let proftpd listen on all interfaces. You should not need passive mode.  Use Firestarter firewall and enable FTP.

If it is difficult to get to work, then you are doing something wrong...

Cheers,

Herman

---

### Post by chronographer on 2007-11-28
Oops, sorry wrong post...

---

### Post by smileypaul on 2007-11-28
I had the same problem... it got very frustrated.

I ended up compiling from source a newer version of ProFTP than what was in the repositories..

Try removing the masquerade address, and make sure the passive ports are open.

also, as stupid as it seems ... go download "Filezilla Client" .. its free ftp software available for all platforms, and for some reason, with that software only, i receieve no problems ...

---

### Post by Phulerock on 2007-11-29
Hello HermanAB,
I forgot to tell you that I use ubuntu-server distro for my proftpd, so I can user firestarter or gproftpd for configuration.

hello Smileypaul, I have just solved this problem, I'm sure this cause ROUTING problem on linux router box, so we could use this rule on shorewall

ACCEPT net $FW tcp 49152:65534
DNAT net loc:192.168.0.38 tcp 49152:65534

which 49152:65534 is range port in proftpd.conf.

I will write the fully document for proftpd behind shorewall very soon. Absolutely use ubuntu-server (not GUI).

Hope this help

---

