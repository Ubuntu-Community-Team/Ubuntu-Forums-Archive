---
title: "jaunty: suspecting firewall problems"
date: 2009-07-20
forum: Security
---

### Post by beugeneb on 2009-07-20
Hello, i recently migrated to jaunty from debian lenny. After setting up my static network in /etc/network/interfaces including nameservers in /etc/resolv.conf I installed all my favorite packages. Everything was fine for a few hours. Then for no apprarant reason I could not get any web pages.. I could not even ping my router. Kept getting host unreachable. I did the normal trouble shooting;

ethernet cable loopback checked out fine
I had sync on my router

Then I booted into the ubuntu live DVD and was still not able to access the internet but could ping my router, I logged into my router web page  noticed my username and password were not configured. As soon as i retyped these settings ( authentication issue ) I resumed access to the internet.

When I rebooted back to the jaunty on my hard drive I noticed I still could not ping anything.


This time I booted into windows, again on same system on a second hard drive, again managed to access the internet successfully.

I am currently using the same system on third hard drive using Centos.

So, I am thinking this must be some Ubuntu specific software problem more than likely a firewall.

In windows I would also reset TCP/IP but don't know how to do it in Linux

I have tried

ufw --version


and get command not recognized.

Also tried 

sudo iptables -L


siawash@ubuntu:~$ sudo iptables -L
[sudo] password for siawash: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

*************]


siawash@ubuntu:~$ man utf
No manual entry for utf



I ping my gateway

siawash@ubuntu:~$ ping 192.168.0.1
connect: Network is unreachable
siawash@ubuntu:~$ 






Can anyone help?

---

### Post by cariboo on 2009-07-20
Do your ip address and dns address stay the same after you reboot Jaunty?

---

### Post by utnubuuser on 2009-07-20
Is ufw enabled? By default it isn't.

---

### Post by The Cog on 2009-07-21
It's not a firewall issue. You appear not to have ufw installed, and iptables says there are no filtering rules.

The fact that your gateway is unreachable suggests to me that maybe your internet connection is being de-configured. I have read that gnome-network-manager sometimes does this, although I have not seen it myself (I always replace it with wicd immediately after install anyway). 

I suggest that you use the command ifconfig to see if your interface still has an IP address when the problem occurs, and also check that it still says RUNNING, which means the cable is still plugged in.

But my first suspect would be gnome-network-manager.

---

### Post by cariboo on 2009-07-21
You have to use network manager to set static ip and dns addresses. If you enter them manually in /etc/network/interfaces and /etc/resolv.conf they will revert to dhcp and auto dns after a reboot.

---

### Post by beugeneb on 2009-07-22
First of all, thanks to all for the feedback.

I am not a 100% on how to run the NetworkManager. I tried typing NetworkManager at a prompt using sudo, nothing happened.

gnome's System >> administration >> network tools >> under devices tab

I notice interface has reverted back to lo instead of eth0. Still, I cannot ping my gateway.

Under system >> Preferences >> Network connections >> under wired connections and IP4 addresses keep reverting to blank after several manual entries.

Here are some additional details.
*********************************************************************************************************

#!/bin/sh -e
# Script to dispatch NetworkManager events
#
# Runs ifupdown scripts when NetworkManager fiddles with interfaces.

if [ -z "$1" ]; then
    echo "$0: called with no interface" 1>&2
    exit 1;
fi

# Fake ifupdown environment
export IFACE="$1"
export LOGICAL="$1"
export ADDRFAM="NetworkManager"
export METHOD="NetworkManager"
export VERBOSITY="0"

# Run the right scripts
case "$2" in
    up)
        export MODE="start"
        export PHASE="up"

"01ifupdown" [readonly] 61L, 1299C                            16,1          Top

******************************************************************************************************

system-settings

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false
*******************************************************************************************************

/etc/network/interfaces

siawash@ubuntu:/etc/network$ cat interfaces

iface eth0 inet static
address 192.168.0.5
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.255.255
gateway 192.168.0.1

******************************************************************************************************
ifconfig: does not show my gateway, host or MAC


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4600 (4.6 KB)  TX bytes:4600 (4.6 KB)

---

### Post by The Cog on 2009-07-22
There should be a wireless strength indicator in your taskbar. Right-click this to get at the gnome-network-manager configuration.

---

### Post by beugeneb on 2009-07-23
I don't use wireless at all. What I use is ethernet on eth0 interface

---

### Post by beugeneb on 2009-07-24
I solved this by doing a rebuild. Fortunately my /home partition is mounted to an external drive which has all my personal data.

This issue must be new to ubuntu. I am assuming static networking should be configured during installation. There was an advanced button at disk partitioning which allowed static addressing.

But there has to be an option to do this post installation...

Guess I have to read the ubuntu pocket book...

---

