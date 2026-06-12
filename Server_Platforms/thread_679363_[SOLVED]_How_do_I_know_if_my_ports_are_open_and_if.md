---
title: "[SOLVED] How do I know if my ports are open and if I'm at risk?"
date: 2008-01-26
forum: Server Platforms
---

### Post by the8thstar on 2008-01-26
Hello,

I would like to get your enlightened opinion about my system. I believe I have a pretty secure system, but when I run rkhunter and iptables, I get disturbing results.

To spare you an unpleasant read, I have highlighted them in **BOLD**.

> root@Ubuntu:/home/the8thstar# sudo rkhunter --update && sudo rkhunter -c -sk
[ Rootkit Hunter version 1.3.0 ]

Checking rkhunter data files...
  Checking file mirrors.dat                                  [ No update ]
  Checking file programs_bad.dat                             [ No update ]
  Checking file backdoorports.dat                            [ No update ]
  Checking file suspscan.dat                                 [ No update ]
  Checking file i18n/cn                                      [ No update ]
  Checking file i18n/en                                      [ No update ]
  Checking file i18n/zh                                      [ No update ]
  Checking file i18n/zhutf                                   [ No update ]
[ Rootkit Hunter version 1.3.0 ]

Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preload file                                [ Not found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]

  Performing file properties checks
    Checking for prerequisites                               [ OK ]
    [B]/bin/bash                                                [ Warning ]
    /bin/cat                                                 [ Warning ]
    /bin/chmod                                               [ Warning ]
    /bin/chown                                               [ Warning ]
    /bin/cp                                                  [ Warning ]
    /bin/date                                                [ Warning ]
    /bin/df                                                  [ Warning ]
    /bin/dmesg                                               [ Warning ]
    /bin/echo                                                [ Warning ]
    /bin/ed                                                  [ Warning ]
    /bin/egrep                                               [ Warning ]
    /bin/fgrep                                               [ Warning ]
    /bin/grep                                                [ Warning ]
    /bin/ip                                                  [ Warning ]
    /bin/kill                                                [ Warning ]
    /bin/login                                               [ Warning ]
    /bin/ls                                                  [ Warning ]
    /bin/lsmod                                               [ Warning ]
    /bin/mktemp                                              [ Warning ]
    /bin/more                                                [ Warning ]
    /bin/mount                                               [ Warning ]
    /bin/mv                                                  [ Warning ]
    /bin/netstat                                             [ Warning ]
    /bin/ps                                                  [ Warning ]
    /bin/pwd                                                 [ Warning ]
    /bin/readlink                                            [ Warning ]
    /bin/sed                                                 [ Warning ]
    /bin/sh                                                  [ Warning ]
    /bin/su                                                  [ Warning ]
    /bin/touch                                               [ Warning ]
    /bin/uname                                               [ Warning ]
    /bin/which                                               [ Warning ]
    /bin/dash                                                [ Warning ]
    /usr/bin/awk                                             [ Warning ]
    /usr/bin/basename                                        [ Warning ]
    /usr/bin/chattr                                          [ Warning ]
    /usr/bin/cut                                             [ Warning ]
    /usr/bin/diff                                            [ Warning ]
    /usr/bin/dirname                                         [ Warning ]
    /usr/bin/dpkg                                            [ Warning ]
    /usr/bin/dpkg-query                                      [ Warning ]
    /usr/bin/du                                              [ Warning ]
    /usr/bin/env                                             [ Warning ]
    /usr/bin/file                                            [ Warning ]
    /usr/bin/find                                            [ Warning ]
    /usr/bin/GET                                             [ Warning ]
    /usr/bin/groups                                          [ Warning ]
    /usr/bin/head                                            [ Warning ]
    /usr/bin/id                                              [ Warning ]
    /usr/bin/killall                                         [ Warning ]
    /usr/bin/last                                            [ Warning ]
    /usr/bin/lastlog                                         [ Warning ]
    /usr/bin/ldd                                             [ Warning ]
    /usr/bin/less                                            [ Warning ]
    /usr/bin/locate                                          [ Warning ]
    /usr/bin/logger                                          [ Warning ]
    /usr/bin/lsattr                                          [ Warning ]
    /usr/bin/lsof                                            [ Warning ]
    /usr/bin/md5sum                                          [ Warning ]
    /usr/bin/newgrp                                          [ Warning ]
    /usr/bin/passwd                                          [ Warning ]
    /usr/bin/perl                                            [ Warning ]
    /usr/bin/pstree                                          [ Warning ]
    /usr/bin/rkhunter                                        [ Warning ]
    /usr/bin/rpm                                             [ Warning ]
    /usr/bin/runcon                                          [ Warning ]
    /usr/bin/sha1sum                                         [ Warning ]
    /usr/bin/size                                            [ Warning ]
    /usr/bin/slocate                                         [ Warning ]
    /usr/bin/sort                                            [ Warning ]
    /usr/bin/stat                                            [ Warning ]
    /usr/bin/strace                                          [ Warning ]
    /usr/bin/strings                                         [ Warning ]
    /usr/bin/sudo                                            [ Warning ]
    /usr/bin/tail                                            [ Warning ]
    /usr/bin/test                                            [ Warning ]
    /usr/bin/top                                             [ Warning ]
    /usr/bin/touch                                           [ Warning ]
    /usr/bin/tr                                              [ Warning ]
    /usr/bin/uniq                                            [ Warning ]
    /usr/bin/users                                           [ Warning ]
    /usr/bin/vmstat                                          [ Warning ]
    /usr/bin/w                                               [ Warning ]
    /usr/bin/watch                                           [ Warning ]
    /usr/bin/wc                                              [ Warning ]
    /usr/bin/wget                                            [ Warning ]
    /usr/bin/whatis                                          [ Warning ]
    /usr/bin/whereis                                         [ Warning ]
    /usr/bin/which                                           [ Warning ]
    /usr/bin/who                                             [ Warning ]
    /usr/bin/whoami                                          [ Warning ]
    /usr/bin/gawk                                            [ Warning ]
    /usr/bin/lwp-request                                     [ Warning ]
    /usr/bin/w.procps                                        [ Warning ]
    /sbin/depmod                                             [ Warning ]
    /sbin/ifconfig                                           [ Warning ]
    /sbin/ifdown                                             [ Warning ]
    /sbin/ifup                                               [ Warning ]
    /sbin/init                                               [ Warning ]
    /sbin/insmod                                             [ Warning ]
    /sbin/ip                                                 [ Warning ]
    /sbin/lsmod                                              [ Warning ]
    /sbin/modinfo                                            [ Warning ]
    /sbin/modprobe                                           [ Warning ]
    /sbin/rmmod                                              [ Warning ]
    /sbin/runlevel                                           [ Warning ]
    /sbin/sulogin                                            [ Warning ]
    /sbin/sysctl                                             [ Warning ]
    /sbin/syslogd                                            [ Warning ]
    /usr/sbin/adduser                                        [ Warning ]
    /usr/sbin/chroot                                         [ Warning ]
    /usr/sbin/cron                                           [ Warning ]
    /usr/sbin/groupadd                                       [ Warning ]
    /usr/sbin/groupdel                                       [ Warning ]
    /usr/sbin/groupmod                                       [ Warning ]
    /usr/sbin/grpck                                          [ Warning ]
    /usr/sbin/nologin                                        [ Warning ]
    /usr/sbin/pwck                                           [ Warning ]
    /usr/sbin/tcpd                                           [ Warning ]
    /usr/sbin/useradd                                        [ Warning ]
    /usr/sbin/userdel                                        [ Warning ]
    /usr/sbin/usermod                                        [ Warning ]
    /usr/sbin/vipw                                           [ Warning ][/B]

Checking for rootkits...

  Performing check of known rootkit files and directories
    55808 Trojan - Variant A                                 [ Not found ]
    ADM Worm                                                 [ Not found ]
    AjaKit Rootkit                                           [ Not found ]
    aPa Kit                                                  [ Not found ]
    Apache Worm                                              [ Not found ]
    Ambient (ark) Rootkit                                    [ Not found ]
    Balaur Rootkit                                           [ Not found ]
    BeastKit Rootkit                                         [ Not found ]
    beX2 Rootkit                                             [ Not found ]
    BOBKit Rootkit                                           [ Not found ]
    CiNIK Worm (Slapper.B variant)                           [ Not found ]
    Danny-Boy's Abuse Kit                                    [ Not found ]
    Devil RootKit                                            [ Not found ]
    Dica-Kit Rootkit                                         [ Not found ]
    Dreams Rootkit                                           [ Not found ]
    Duarawkz Rootkit                                         [ Not found ]
    Enye LKM                                                 [ Not found ]
    Flea Linux Rootkit                                       [ Not found ]
    FreeBSD Rootkit                                          [ Not found ]
    ****`it Rootkit                                          [ Not found ]
    GasKit Rootkit                                           [ Not found ]
    Heroin LKM                                               [ Not found ]
    HjC Kit                                                  [ Not found ]
    ignoKit Rootkit                                          [ Not found ]
    ImperalsS-FBRK Rootkit                                   [ Not found ]
    Irix Rootkit                                             [ Not found ]
    Kitko Rootkit                                            [ Not found ]
    Knark Rootkit                                            [ Not found ]
    Li0n Worm                                                [ Not found ]
    Lockit / LJK2 Rootkit                                    [ Not found ]
    Mood-NT Rootkit                                          [ Not found ]
    MRK Rootkit                                              [ Not found ]
    Ni0 Rootkit                                              [ Not found ]
    Ohhara Rootkit                                           [ Not found ]
    Optic Kit (Tux) Worm                                     [ Not found ]
    Oz Rootkit                                               [ Not found ]
    Phalanx Rootkit                                          [ Not found ]
    Phalanx Rootkit (strings)                                [ Not found ]
    Portacelo Rootkit                                        [ Not found ]
    R3dstorm Toolkit                                         [ Not found ]
    RH-Sharpe's Rootkit                                      [ Not found ]
    RSHA's Rootkit                                           [ Not found ]
    Scalper Worm                                             [ Not found ]
    Sebek LKM                                                [ Not found ]
    Shutdown Rootkit                                         [ Not found ]
    SHV4 Rootkit                                             [ Not found ]
    SHV5 Rootkit                                             [ Not found ]
    Sin Rootkit                                              [ Not found ]
    Slapper Worm                                             [ Not found ]
    Sneakin Rootkit                                          [ Not found ]
    Suckit Rootkit                                           [ Not found ]
    SunOS Rootkit                                            [ Not found ]
    SunOS / NSDAP Rootkit                                    [ Not found ]
    Superkit Rootkit                                         [ Not found ]
    TBD (Telnet BackDoor)                                    [ Not found ]
    TeLeKiT Rootkit                                          [ Not found ]
    T0rn Rootkit                                             [ Not found ]
    Trojanit Kit                                             [ Not found ]
    Tuxtendo Rootkit                                         [ Not found ]
    URK Rootkit                                              [ Not found ]
    VcKit Rootkit                                            [ Not found ]
    Volc Rootkit                                             [ Not found ]
    X-Org SunOS Rootkit                                      [ Not found ]
    zaRwT.KiT Rootkit                                        [ Not found ]

  Performing additional rootkit checks
    Suckit Rookit additional checks                          [ OK ]
    Checking for possible rootkit files and directories      [ None found ]
    Checking for possible rootkit strings                    [ None found ]

  Performing malware checks
    Checking running processes for suspicious files          [ None found ]
    Checking for login backdoors                             [ None found ]
    Checking for suspicious directories                      [ None found ]
    Checking for sniffer log files                           [ None found ]

  Performing trojan specific checks
    Checking for enabled inetd services                      [ OK ]

  Performing Linux specific checks
    Checking kernel module commands                          [ OK ]
    Checking kernel module names                             [ OK ]

Checking the network...

  Performing check for backdoor ports
    Checking for UDP port 2001                               [ Not found ]
    Checking for TCP port 2006                               [ Not found ]
    Checking for TCP port 2128                               [ Not found ]
    Checking for TCP port 14856                              [ Not found ]
    Checking for TCP port 47107                              [ Not found ]
    Checking for TCP port 60922                              [ Not found ]

  Performing checks on the network interfaces
    Checking for promiscuous interfaces                      [ None found ]

Checking the local host...

  Performing system boot checks
    Checking for local host name                             [ Found ]
    Checking for local startup files                         [ Found ]
    Checking local startup files for malware                 [ None found ]
    Checking system startup files for malware                [ None found ]

  Performing group and account checks
    Checking for passwd file                                 [ Found ]
    Checking for root equivalent (UID 0) accounts            [ None found ]
    Checking for passwordless accounts                       [ None found ]
    Checking for passwd file changes                         [ None found ]
    Checking for group file changes                          [ None found ]
    Checking root account shell history files                [ OK ]

  Performing system configuration file checks
    Checking for SSH configuration file                      [ Not found ]
    Checking for running syslog daemon                       [ Found ]
    Checking for syslog configuration file                   [ Found ]
    Checking if syslog remote logging is allowed             [ Not allowed ]

  Performing filesystem checks
    Checking /dev for suspicious file types                  [ None found ]
    Checking for hidden files and directories                [ Warning ]

Checking application versions...

    Checking version of Exim MTA                             [ OK ]
    Checking version of GnuPG                                [ OK ]
    Checking version of OpenSSL                              [ OK ]


System checks summary
=====================

File properties checks...
    Files checked: 123
    Suspect files: 123

Rootkit checks...
    Rootkits checked : 110
    Possible rootkits: 0

Applications checks...
    Applications checked: 3
    Suspect applications: 0

The system checks took: 1 minute and 21 seconds

All results have been written to the logfile (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)

Next, I ran iptables... and I don't understand what I'm reading. Does the following config look normal to you? Am being hacked? Are there ports open on my system? If so, how do I close them?

> root@Ubuntu:/home/the8thstar# sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.2.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.2.1          anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       0    --  anywhere             255.255.255.255     
DROP       0    --  anywhere             192.168.2.255       
DROP       0    --  base-address.mcast.net/8  anywhere            
DROP       0    --  anywhere             base-address.mcast.net/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
LSI        0    -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.2.2          192.168.2.1         tcp dpt:53 
ACCEPT     udp  --  192.168.2.2          192.168.2.1         udp dpt:53 
ACCEPT     0    --  anywhere             anywhere            
DROP       0    --  base-address.mcast.net/8  anywhere            
DROP       0    --  anywhere             base-address.mcast.net/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
OUTBOUND   0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSI        0    --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       0    --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  anywhere             anywhere

Just to get a little more in-depth, here are the contents of my Hosts file:

> 127.0.0.1	localhost
127.0.1.1	Ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts     

I use Firefox with the following security addons: Adblock, NoScript, RefControl, SafeHistory and Shazou. I also have VirtualBox running a virtual XP Home Edition (which is set to be able to R/W my /Home partition) and I dual boot with Vista Home Premium.

I apologize for the long post. I hope that it can be useful to someone  in a similar situation.

Your comments will be welcome and your help appreciated! 

Regards,

The8thStar

---

### Post by AnonCat on 2008-01-26
A quick way to scan for open ports is to go the website I linked to at the bottom and use their online utility (Shields Up) for scanning your system.  The only change I had to do the default Ubuntu settings to fully shore my firewall was to disable smtp.  I don't think you really have to worry though as most of the information you bolded mostly consists of linux commands/programs which are harmless but have the potential to do harm if used wrong.  The scan results you provided mentioned that no malware was found so I'd rest easy.

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by Vinno on 2008-01-27
the8thstar have you issued the -propupd command with rk hunter? Thats maybe why your getting all those warnings on the file property's.

> --propupd                     Update the file properties database 

---

### Post by the8thstar on 2008-01-27
**AnonCat**

> [https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2")

Thanks for the link! I'm at work right now, but I'll check it out later.

**Vinno**

> -propupd command with rk hunter

Good idea. I'll include it in my next run and will publish the results.

Thanks guys!

---

