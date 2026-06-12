---
title: "cobbler check problem"
date: 2012-02-18
forum: Ubuntu Cloud and Juju
---

### Post by datalay on 2012-02-18
it is ubuntu-server 11.10

1) cobbler check: how can i  fix 1?


2) i enabled DNS&DHCP property of orchestra, but i think orchestra DHCP is not running, because i cant boot node 1 with network property,, how can i check DHCP property of orchestra, how can fix it? 




root@ubuntuserver:~# cat komut.sh 
sudo cobbler system add \
        --name="oneiric01.ubuntu.lan" \
        --mac-address="00:0F:EA:C8:A7:1E" \
        --ip-address="192.168.77.33" \
        --dns-name="oneiric01.ubuntu.lan" \
        --hostname="oneiric01.ubuntu.lan" \
        --profile="oneiric-i386-juju" \
        --mgmt-classes="orchestra-juju-available" \
        --kopts=" DEBCONF_DEBUG=developer netcfg/dhcp_timeout=120 netcfg/choose_interface=eth0"

root@ubuntuserver:~# cobbler system list
   oneiric01.ubuntu.lan

oracle@ubuntuserver:~$ sudo cobbler check
[sudo] password for oracle: 
The following are potential configuration items that you may want to fix:

1 : One or more repos need to be processed by cobbler reposync for the first time before kickstarting against them: natty-x86_64-security, precise-i386, precise-x86_64-security, lucid-x86_64, precise-i386-security, hardy-x86_64, oneiric-x86_64-security, lucid-i386, oneiric-i386, natty-x86_64, lucid-x86_64-security, natty-i386, hardy-i386, oneiric-i386-security, hardy-i386-security, precise-x86_64, maverick-x86_64-security, lucid-i386-security, maverick-i386-security, maverick-x86_64, maverick-i386, natty-i386-security, hardy-x86_64-security, oneiric-x86_64

Restart cobblerd and then run 'cobbler sync' to apply changes.
oracle@ubuntuserver:~$ nmap localhost

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2012-02-18 10:12 EET
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00066s latency).
Not shown: 994 closed ports
PORT STATE SERVICE
22/tcp open ssh
25/tcp open smtp
53/tcp open domain
80/tcp open http
3128/tcp open squid-http
5666/tcp open nrpe

Nmap done: 1 IP address (1 host up) scanned in 0.18 seconds


oracle@ubuntuserver:~$ sudo cobbler list
[sudo] password for oracle: 
distros:
hardy-i386
hardy-x86_64
lucid-i386
lucid-x86_64
maverick-i386
maverick-x86_64
natty-i386
natty-x86_64
oneiric-i386
oneiric-x86_64
precise-i386
precise-x86_64

profiles:
hardy-i386
hardy-i386-juju
hardy-x86_64
hardy-x86_64-juju
lucid-i386
lucid-i386-juju
lucid-x86_64
lucid-x86_64-juju
maverick-i386
maverick-i386-juju
maverick-x86_64
maverick-x86_64-juju
natty-i386
natty-i386-juju
natty-x86_64
natty-x86_64-juju
oneiric-i386
oneiric-i386-juju
oneiric-x86_64
oneiric-x86_64-juju
precise-i386
precise-i386-juju
precise-x86_64
precise-x86_64-juju

systems:
oneiric01.ubuntu.lan

repos:
hardy-i386
hardy-i386-security
hardy-x86_64
hardy-x86_64-security
lucid-i386
lucid-i386-security
lucid-x86_64
lucid-x86_64-security
maverick-i386
maverick-i386-security
maverick-x86_64
maverick-x86_64-security
natty-i386
natty-i386-security
natty-x86_64
natty-x86_64-security
oneiric-i386
oneiric-i386-security
oneiric-x86_64
oneiric-x86_64-security
precise-i386
precise-i386-security
precise-x86_64
precise-x86_64-security

images:

mgmtclasses:
orchestra-juju-acquired
orchestra-juju-available

packages:

files:

---

