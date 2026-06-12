---
title: "help! i think someone is hacking me!"
date: 2009-10-09
forum: Security
---

### Post by blueson on 2009-10-09
ubuntu 8.04 on an acer travelmate (reposted from network/wireless section)

for the past few weeks i noticed i haven't been able to access google.com without getting a time-out. i thought it was my router. when i checked the log i found two interesting entries.

10/06/2009  04:04:45 **Smurf** 0.0.0.0->> 10.25.160.1, Type:5, Code:1 (from WAN Outbound)
10/06/2009  04:04:45 DHCP Client: Send Discover

10/06/2009  23:06:22 **SYN Flood to Host** 192.168.2.101, 53341->> 66.249.90.104, 80 (from WAN Outbound)

the IP above happens to be google. i read up on syn flood attacks and i think someone's using my computer to trigger syn flood/dos attacks.

i ran chkrootkit and this is what i found (scroll to the end). when i was on wireless it reported packet sniffer on eth1. when on wired internet it reported it on eth0. is this a positive result for a packet sniffer?

in my "network tools" i can't access the configuration for eth0 or eth1. also, i can't see the bottom left entries (hardware address, multicast, mtu etc.) so i can't see my own mac address. 

i ran ports scan and everytime i click different random ports appear open. (34728, 39742, 48763 etc.) this seems to go with the syn flood attack.

most of the time i browse using my wired network (eth0) but my wireless always stays open and it's an apartment so there's lots of other networks around. i don't know too much about hacking but is it possible someone got into my computer through my wireless network? OR was it a sketchy website? OR a bad repository? which of the 3 is most likely?

also, if i completely wipe and reinstall my system, what are the chances of this happening again knowing someone could have my mac address?

thanks for the help.

---------------------------------------------------------------------------------

*****@*****:~$ sudo chkrootkit
ROOTDIR is `/'
Checking `amd'... not found
Checking `basename'... not infected
Checking `biff'... not found
Checking `chfn'... not infected
Checking `chsh'... not infected
Checking `cron'... not infected
Checking `crontab'... not infected
Checking `date'... not infected
Checking `du'... not infected
Checking `dirname'... not infected
Checking `echo'... not infected
Checking `egrep'... not infected
Checking `env'... not infected
Checking `find'... not infected
Checking `fingerd'... not found
Checking `gpm'... not found
Checking `grep'... not infected
Checking `hdparm'... not infected
Checking `su'... not infected
Checking `ifconfig'... not infected
Checking `inetd'... not infected
Checking `inetdconf'... not infected
Checking `identd'... not found
Checking `init'... not infected
Checking `killall'... not infected
Checking `ldsopreload'... not infected
Checking `login'... not infected
Checking `ls'... not infected
Checking `lsof'... not infected
Checking `mail'... not found
Checking `mingetty'... not found
Checking `netstat'... not infected
Checking `named'... not found
Checking `passwd'... not infected
Checking `pidof'... not infected
Checking `pop2'... not found
Checking `pop3'... not found
Checking `ps'... not infected
Checking `pstree'... not infected
Checking `rpcinfo'... not infected
Checking `rlogind'... not found
Checking `rshd'... not found
Checking `slogin'... not infected
Checking `sendmail'... not found
Checking `sshd'... not found
Checking `syslogd'... not infected
Checking `tar'... not infected
Checking `tcpd'... not infected
Checking `tcpdump'... not infected
Checking `top'... not infected
Checking `telnetd'... not found
Checking `timed'... not found
Checking `traceroute'... not found
Checking `vdir'... not infected
Checking `w'... not infected
Checking `write'... not infected
Checking `aliens'... no suspect files
Searching for sniffer's logs, it may take a while... nothing found
Searching for HiDrootkit's default dir... nothing found
Searching for t0rn's default files and dirs... nothing found
Searching for t0rn's v8 defaults... nothing found
Searching for Lion Worm default files and dirs... nothing found
Searching for RSHA's default files and dir... nothing found
Searching for RH-Sharpe's default files... nothing found
Searching for Ambient's rootkit (ark) default files and dirs... nothing found
Searching for suspicious files and dirs, it may take a while... 
/usr/lib/firefox/.autoreg
/usr/lib/xulrunner-1.9.0.14/.autoreg
/usr/lib/firefox-3.0.14/.autoreg
/usr/lib/jvm/.java-6-openjdk.jinfo
/usr/lib/jvm/.java-gcj.jinfo
/lib/modules/2.6.24-24-generic/volatile/.mounted

Searching for LPD Worm files and dirs... nothing found
Searching for Ramen Worm files and dirs... nothing found
Searching for Maniac files and dirs... nothing found
Searching for RK17 files and dirs... nothing found
Searching for Ducoci rootkit... nothing found
Searching for Adore Worm... nothing found
Searching for ShitC Worm... nothing found
Searching for Omega Worm... nothing found
Searching for Sadmind/IIS Worm... nothing found
Searching for MonKit... nothing found
Searching for Showtee... nothing found
Searching for OpticKit... nothing found
Searching for T.R.K... nothing found
Searching for Mithra... nothing found
Searching for OBSD rk v1... /usr/lib/security
/usr/lib/security/classpath.security
Searching for LOC rootkit... nothing found
Searching for Romanian rootkit... nothing found
Searching for Suckit rootkit... nothing found
Searching for Volc rootkit... nothing found
Searching for Gold2 rootkit... nothing found
Searching for TC2 Worm default files and dirs... nothing found
Searching for Anonoying rootkit default files and dirs... nothing found
Searching for ZK rootkit default files and dirs... nothing found
Searching for ShKit rootkit default files and dirs... nothing found
Searching for AjaKit rootkit default files and dirs... nothing found
Searching for zaRwT rootkit default files and dirs... nothing found
Searching for Madalin rootkit default files... nothing found
Searching for Fu rootkit default files... nothing found
Searching for ESRK rootkit default files... nothing found
Searching for rootedoor... nothing found
Searching for ENYELKM rootkit default files... nothing found
Searching for anomalies in shell history files... /usr/bin/find: //home/*****/.gvfs: Permission denied
/usr/bin/find: //home/*****/.gvfs: Permission denied
nothing found
Checking `asp'... not infected
Checking `bindshell'... not infected
Checking `lkm'... chkproc: nothing detected
Checking `rexedcs'... not found
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient3[13609])
Checking `w55808'... not infected
Checking `wted'... chkwtmp: nothing deleted
Checking `scalper'... not infected
Checking `slapper'... not infected
Checking `z2'... user ***** deleted or never logged from lastlog!
*****@******:~$ 

--------------------------------------------------------------------------------

---

### Post by update_manager on 2009-10-09
> **blueson said:**
> ubuntu 8.04 on an acer travelmate (reposted from network/wireless section)

10/06/2009  04:04:45 **Smurf** 0.0.0.0->> 10.25.160.1, Type:5, Code:1 (from WAN Outbound)
10/06/2009  04:04:45 DHCP Client: Send Discover

10/06/2009  23:06:22 **SYN Flood to Host** 192.168.2.101, 53341->> 66.249.90.104, 80 (from WAN Outbound)


most of the time i browse using my wired network (eth0) but my wireless always stays open and it's an apartment so there's lots of other networks around. i don't know too much about hacking but is it possible someone got into my computer through my wireless network? OR was it a sketchy website? OR a bad repository? which of the 3 is most likely?

A website would be the most likely option. It won't matter if anyone knows your MAC address or not.

A good test is to install wireshark, close your web browser and start collecting packets. If you don't want to install a sniffer the below iptables commands will log all web requests on port 80.


sudo iptables -P OUTPUT ACCEPT
sudo iptables -A OUTPUT -p tcp --dport -j LOG --log-prefix "port 80"
sudo iptables -A OUTPUT -p tcp --sport -j LOG --log-prefix "port 80"

You can view the logs with this command.

sudo tail -f /var/log/syslog | grep "port 80"

---

