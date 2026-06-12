---
title: "Cannot configure NUT UPS client"
date: 2010-05-16
forum: Server Platforms
---

### Post by MikeEagling on 2010-05-16
Hi,

I am running Ubuntu Server Lucid 64bit on an AMD-based system and Ubuntu Server Lucid x86 on a dual P4 HP Netserver. I have a Trust PW-4120M UPS plugged into the AMD box via a serial cable.

I have installed nut on both systems from the repositories (with "apt-get instal nut") and configured the AMD system as follows:

#nut.conf
MODE=netserver

#ups.conf
[trustups]
        driver = megatec
        port = /dev/ttyS0
        desc = "Primary system UPS"

# upsd.conf
ACL localhost 127.0.0.1/32
ACL lan 192.168.2.0/24
ACL all 0.0.0.0/0
ACCEPT localhost
ACCEPT lan
REJECT all

# upsd.users
[local_mon]
        password = <password>
        upsmon master

[remote_mon]
        password = <remote_passwd>
        allowfrom = 192.168.2.3
        upsmon slave

# Network UPS Tools: example upsmon configuration
#
# This file contains passwords, so keep it secure.
MONITOR trustups@localhost 1 local_mon <password> master
MINSUPPLIES 1
SHUTDOWNCMD "/sbin/shutdown -h now"
POLLFREQ 5
POLLFREQALERT 5
HOSTSYNC 15
DEADTIME 15
POWERDOWNFLAG /etc/killpower
RBWARNTIME 43200
NOCOMMWARNTIME 300
FINALDELAY 5

Nut works as expected on this machine: if I pull the plug the server shuts down gracefully.

However, I am unable to configure the Netserver to monitor the upsd running on the AMD box. It has the following config files:

#nut.conf
MODE=netclient

# Network UPS Tools: example upsmon configuration
#
# This file contains passwords, so keep it secure.
MONITOR trustups@192.168.2.2 1 remote_mon <remote_passwd> slave
MINSUPPLIES 1
SHUTDOWNCMD "/sbin/shutdown -h now"
POLLFREQ 5
POLLFREQALERT 5
HOSTSYNC 15
DEADTIME 15
POWERDOWNFLAG /etc/killpower
RBWARNTIME 43200
NOCOMMWARNTIME 300
FINALDELAY 5

upsmon starts ok on this machine but, no matter what I try, it cannot connect to the remote server. Every few minutes upsmon issues the following message:

Broadcast Message from nut@netcom                                              
        (somewhere) at 2:30 ...                                                
                                                                               
UPS trustups@192.168.2.2 is unavailable

I've tried every adjustment to the config files I can think of but without success. I'm guessing this is a permissions issue but I've been unable to find any info on this after extensive searching of Google. As far as I can tell (ie. I've not installed one!) there's no firewall operating on either machine.

I'm hoping I've just missed something obvious... Can anyone make any suggestions?

Thanks in advance,

Mike

---

### Post by tgalati4 on 2010-05-16
If you have a software firewall running then it's possible that you need to poke a hole in the appropriate port to allow upsd communication.

I use apcupsd on several machines on my network and I can remotely monitor my ups boxes.

apcupsd uses port 6544 to communicate.  I don't know what nut uses.

---

### Post by MikeEagling on 2010-05-17
Thanks for the reply.

Yeah, I think I need to expose port 3493 somehow. Unfortunately there seems to be zero content online regarding this specific issue so it will require some experimentation to resolve...

---

