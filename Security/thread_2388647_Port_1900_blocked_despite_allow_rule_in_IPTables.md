---
title: "Port 1900 blocked despite allow rule in IPTables"
date: 2018-04-05
forum: Security
---

### Post by rlongfield on 2018-04-05
I have an IPtables.sh file that allows me to quickly modify my IPtables and use variables.

Everything was going well until I noticed that I have a lot of connections to my Ubuntu server from my private network at home (mix of Nix and Win boxes, plus Android devices) on port 1900 that are being blocked. 

In my IPtables I have the following variables set.

    ```
THIS_HOST="192.168.1.116"
    WORK="XX.XX.XX.XX"
    HOME_NETWORK="192.168.1.0/24"
```

Then I have an entry to allow my Home_Network to connect to port 1900

    ```
#Accept Some UPN Discovery Connections
    $IPTABLES -A INPUT -m state --state NEW -p UDP -s $HOME_NETWORK -d $THIS_HOST --dport 1900 -j ACCEPT
```

This entry does not work as I get the following in my syslog:

** Apr  4 15:54:39 zues kernel: [331454.549383] Firewalled packet:IN=eth0  OUT= MAC=01:00:5e:7f:ff:fa:cc:52:af:41:64:68:08:00 SRC=192.168.1.248  DST=239.255.255.250 LEN=188 TOS=0x00 PREC=0x00 TTL=2 ID=22168 PROTO=UDP SPT=1823 DPT=1900 LEN=168**

I know the variables work as this entry is working properly:

    ```
#accept some ssh connections
    $IPTABLES -A INPUT -m state --state NEW -p TCP -s $WORK -d $THIS_HOST --dport 22 -j ACCEPT
    $IPTABLES -A INPUT -m state --state NEW -p TCP -s $HOME_NETWORK -d $THIS_HOST --dport 22 -j ACCEPT
```

When I do a 

**_sudo iptables -L_** 

I get this:

    **ACCEPT     udp  --  192.168.1.0/24       Zeus *(My Server)*                 state NEW udp dpt:1900**


Here is my iptables.sh file

    ```
#!/bin/bash
    
    ################################################################
    #Insert modules- should be done automatically if needed
    dmesg -n 1 #Kill copyright display on module load
    #/sbin/modprobe ip_tables
    #/sbin/modprobe iptable_filter
    /sbin/modprobe ip_conntrack
    /sbin/modprobe ip_conntrack_ftp
    #/sbin/modprobe ip_nat_ftp #for PASV ftp
    
    IPTABLES="/sbin/iptables"
    THIS_HOST="192.168.1.116"
    LOCAL_HOST="127.0.0.1"
    WORK="XX.XX.XXX.18"
    HOME_NETWORK="192.168.1.0/24"
    #EXTRA_IP_FOR_SSH="$Work"
    #EXTRA_IP_FOR_SSH=""
    #EXTRA_IP_FOR_MYSQL=""
    
    $IPTABLES -F
    
    #Kill ANY stupid packets, including
    #-Packets that are too short to have a full ICMP/UDP/TCP header
    #- TCP and UDP packets with zero (illegal) source and destination ports
    #-Illegal combinations of TCP flags
    #-Zero-length (illegal) or over-length TCP and IP options,
    # or options after the END-OF-OPTIONS option
    #-Fragments of illegal length or offset (e.g., Ping of Death).
    #Above list ripped from
    #[http://www.linux-mag.com/2000-01/bestdefense_02.html](http://www.linux-mag.com/2000-01/bestdefense_02.html)
    #$IPTABLES -A INPUT -m unclean -j DROP
    #$IPTABLES -A FORWARD -m unclean -j DROP
    
    #Allow Loopback
    iptables -A INPUT -i lo -j ACCEPT
    iptables -A OUTPUT -o lo -j ACCEPT
    
    #Allow Outgoing DNS
    iptables -A OUTPUT -p udp -o eth0 --dport 53 -j ACCEPT
    iptables -A INPUT -p udp -i eth0 --sport 53 -j ACCEPT
    
    #Kill invalid packets (illegal combinations of flags)
    $IPTABLES -A INPUT -m state --state INVALID -j DROP
    $IPTABLES -A FORWARD -m state --state INVALID -j DROP
    
    #block enemies
    $IPTABLES -A INPUT -s "91.65.221.109" -j DROP
    
    #Block Port Hammers
    $IPTABLES -A INPUT -s "58.218.201.189" -j DROP
    $IPTABLES -A INPUT -s "185.222.211.44" -j DROP
    #$IPTABLES -A INPUT -s "61.78.245.0/24" -j DROP
    #$IPTABLES -A INPUT -s "218.146.209.182" -j DROP
    #$IPTABLES -A INPUT -s "220.77.44.229" -j DROP
    #$IPTABLES -A INPUT -s "61.75.224.41" -j DROP
    
    #Accept Some UPN Discovery Connections
    $IPTABLES -A INPUT -m state --state NEW -p UDP -s $HOME_NETWORK -d $THIS_HOST --dport 1900 -j ACCEPT
    
    #ICMP
    #ping flood protection
    $IPTABLES -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -j ACCEPT
    $IPTABLES -A INPUT -p icmp --icmp-type echo-request -j DROP
    #Allow all other icmp
    $IPTABLES -A INPUT -p icmp -j ACCEPT
    
    #allow established and related connections to continue
    $IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -d 127.0.0.1 -j ACCEPT
    $IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -d $THIS_HOST -j ACCEPT
    
    #this is "bif"
    #procmail sends a biff/comsat message via udp on port 512 every time it deliveres a message to a users mailbox
    #$IPTABLES -A INPUT -p UDP -s 127.0.0.1 -d 127.0.0.1 --dport 512 -j REJECT
    
    #allow spamassassin to talk to spamd
    #$IPTABLES -A INPUT -p TCP -s 127.0.0.1 -d 127.0.0.1 --dport 783 -j ACCEPT
    #$IPTABLES -A INPUT -p TCP -s 127.0.0.1 -d 127.0.0.1 --sport 783 -j ACCEPT
    
    #accept some httpd connections
    $IPTABLES -A INPUT -p TCP -d $THIS_HOST --dport 80 -m limit --limit 25/minute --limit-burst 100 -j ACCEPT
    
    #accept some httpsd connections
    $IPTABLES -A INPUT -p TCP -d $THIS_HOST --dport 443 -j ACCEPT
    
    #accept some ssh connections
    $IPTABLES -A INPUT -m state --state NEW -p TCP -s $WORK -d $THIS_HOST --dport 22 -j ACCEPT
    $IPTABLES -A INPUT -m state --state NEW -p TCP -s $HOME_NETWORK -d $THIS_HOST --dport 22 -j ACCEPT
    $IPTABLES -A INPUT -m state --state NEW -p TCP -s $HOME -d $THIS_HOST --dport 22 -j ACCEPT
    $IPTABLES -A OUTPUT -o eth0 -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
    #if [ "$EXTRA_IP_FOR_SSH" != "" ]; then
    #        $IPTABLES -A INPUT -m state --state NEW -p TCP -s $EXTRA_IP_FOR_SSH -d $THIS_HOST --dport 22 -j ACCEPT
    #fi
    
    #accept some ftp connections
    #$IPTABLES -A INPUT -m state --state NEW -p TCP -s $HOME_NETWORK -d $THIS_HOST --dport 21 -j ACCEPT
    #$IPTABLES -A INPUT -m state --state NEW -p TCP -s $WORK -d $THIS_HOST --dport 21 -j ACCEPT
    
    #Accept Some Vino/VNC Connections
    $IPTABLES -A INPUT -m state --state NEW -p TCP -s $HOME_NETWORK -d $THIS_HOST --dport 5900 -j ACCEPT
    $IPTABLES -A INPUT -m state --state NEW -p UDP -s $HOME_NETWORK -d $THIS_HOST --dport 5900 -j ACCEPT
    $IPTABLES -A INPUT -m state --state NEW -p TCP -s $WORK -d $THIS_HOST --dport 5900 -j ACCEPT
    $IPTABLES -A INPUT -m state --state NEW -p UDP -s $WORK -d $THIS_HOST --dport 5900 -j ACCEPT
    
    #Accept Some Samba Connections
    $IPTABLES -A INPUT -m state --state NEW -p TCP -s $HOME_NETWORK -d $THIS_HOST --dport 139 -j ACCEPT
    $IPTABLES -A INPUT -m state --state NEW -p TCP -s $HOME_NETWORK -d $THIS_HOST --dport 445 -j ACCEPT
    $IPTABLES -A INPUT -m state --state NEW -p UDP -s $HOME_NETWORK -d $THIS_HOST --dport 137 -j ACCEPT
    $IPTABLES -A INPUT -m state --state NEW -p UDP -s $HOME_NETWORK -d $THIS_HOST --dport 138 -j ACCEPT
    
    #Accept Some MYTHTV Connections
    $IPTABLES -A INPUT -m state --state NEW -p TCP -s $HOME_NETWORK -d $THIS_HOST --dport 6543 -j ACCEPT
    $IPTABLES -A INPUT -m state --state NEW -p TCP -s $HOME_NETWORK -d $THIS_HOST --dport 6544 -j ACCEPT
    $IPTABLES -A INPUT -m state --state NEW -p TCP -s $HOME_NETWORK -d $THIS_HOST --dport 3306 -j ACCEPT
    #$IPTABLES -A INPUT -m state --state NEW -p TCP -s $LOCAL_HOST -d $THIS_HOST --dport 6543 -j ACCEPT
    #$IPTABLES -A INPUT -m state --state NEW -p TCP -s $LOCAL_HOST -d $THIS_HOST --dport 6544 -j ACCEPT
    #$IPTABLES -A INPUT -m state --state NEW -p TCP -s $LOCAL_HOST -d $THIS_HOST --dport 3306 -j ACCEPT
    
    #Accept Some UPN Discovery Connections
    #$IPTABLES -A INPUT -m state --state NEW -p UDP -s $HOME_NETWORK -d $THIS_HOST --dport 1900 -j ACCEPT
    #$IPTABLES -A INPUT -m state --state NEW -p UDP -s $HOME_NETWORK -d $THIS_HOST --dport 1900 -j ACCEPT
    
    #Accept Some Mosquitto Connections
    $IPTABLES -A INPUT -p TCP -d $THIS_HOST --dport 1883 -j ACCEPT
    $IPTABLES -A INPUT -p UDP -d $THIS_HOST --dport 1883 -j ACCEPT
    $IPTABLES -A INPUT -p TCP -d $THIS_HOST --dport 8883 -j ACCEPT
    $IPTABLES -A INPUT -p UDP -d $THIS_HOST --dport 8883 -j ACCEPT
    $IPTABLES -A INPUT -p TCP -d $THIS_HOST --dport 8083 -j ACCEPT
    $IPTABLES -A INPUT -p UDP -d $THIS_HOST --dport 8083 -j ACCEPT
    
    #Accept Some Test Connections
    $IPTABLES -A INPUT -p TCP -d $THIS_HOST --dport 56665 -j ACCEPT
    $IPTABLES -A INPUT -m state --state NEW -p TCP -s $HOME_NETWORK -d $THIS_HOST --dport 1823 -j ACCEPT
    $IPTABLES -A INPUT -m state --state NEW -p UDP -s $HOME_NETWORK -d $THIS_HOST --dport 1823 -j ACCEPT
    
    #Accept Some Minecraft Connections
    
    
    #Accept Some UT2K4 Connections
    
    
    
    
    #accept some mysql connections
    $IPTABLES -A INPUT -m state --state NEW -p TCP -s $THIS_HOST -d $THIS_HOST --dport 3306 -j ACCEPT
    $IPTABLES -A INPUT -m state --state NEW -p TCP -s $HOME_NETWORK -d $THIS_HOST --dport 3306 -j ACCEPT
    #$IPTABLES -A INPUT -m state --state NEW -p TCP -s $OFFICE2 -d $THIS_HOST --dport 3306 -j ACCEPT
    #if [ "$EXTRA_IP_FOR_MYSQL" != "" ]; then
    #        $IPTABLES -A INPUT -m state --state NEW -p TCP -s $EXTRA_IP_FOR_MYSQL -d $THIS_HOST --dport 3306 -j ACCEPT
    #fi
    
    #SMTP server
    #accept connections from the world
    #smtp  One per second limt -burst rate of ten
    #$IPTABLES -A INPUT -p tcp --dport 25 --syn -m limit --limit 1/s --limit-burst 10 -j ACCEPT
    #$IPTABLES -A INPUT -p tcp --dport 25 --syn -j DROP
    #$IPTABLES -A INPUT -p tcp --dport 25 -j ACCEPT
    
    #pop server
    #$IPTABLES -A INPUT -p tcp --dport 110 -j ACCEPT
    #$IPTABLES -A INPUT -p tcp -d 127.0.0.1 --dport 110 -j ACCEPT
    
    #snmp
    #$IPTABLES -A INPUT -p udp -s 205.189.48.232 --dport 161 -j ACCEPT
    
    
    ####################################################################3
    # that's it for specific port opennings
    # now we just log everythign and drop it
    ####################################################################3
    
    #Drop all packets from Private IP Address space
    ## Class A Reserved
    $IPTABLES -A OUTPUT -d 10.0.0.0/8 -j DROP
    
    ## Class B Reserved
    $IPTABLES -A OUTPUT -d 172.16.0.0/12 -j DROP
    
    ## Class C Reserved
    $IPTABLES -A OUTPUT -d 192.168.1.0/24 -j ACCEPT
    
    ## Class D Reserved
    $IPTABLES -A OUTPUT -d 224.0.0.0/4 -j DROP
    
    ## Class E Reserved
    $IPTABLES -A OUTPUT -d 240.0.0.0/5 -j DROP
    
    
    ##Some ports should be denied and logged.
    $IPTABLES -A INPUT -p tcp --dport 515 -m limit -j LOG \
                                           --log-prefix "L1on attack"
    $IPTABLES -A INPUT -p tcp --dport 515 -j DROP
    $IPTABLES -A INPUT -p tcp --dport 6670 -m limit -j LOG \
                                           --log-prefix "Deepthroat scan"
    $IPTABLES -A INPUT -p tcp --dport 6670 -j DROP
    $IPTABLES -A INPUT -p tcp --dport 6711 -m limit -j LOG \
                                           --log-prefix "Subseven scan"
    $IPTABLES -A INPUT -p tcp --dport 6711 -j DROP
    $IPTABLES -A INPUT -p tcp --dport 6712 -m limit -j LOG \
                                           --log-prefix "Subseven scan"
    $IPTABLES -A INPUT -p tcp --dport 6712 -j DROP
    $IPTABLES -A INPUT -p tcp --dport 6713 -m limit -j LOG \
                                           --log-prefix "Subseven scan"
    $IPTABLES -A INPUT -p tcp --dport 6713 -j DROP
    
    $IPTABLES -A INPUT -p tcp --dport 12345 -m limit -j LOG \
                                           --log-prefix "Netbus scan"
    $IPTABLES -A INPUT -p tcp --dport 12345 -j DROP
    $IPTABLES -A INPUT -p tcp --dport 12346 -m limit -j LOG \
                                           --log-prefix "Netbus scan"
    $IPTABLES -A INPUT -p tcp --dport 12346 -j DROP
    $IPTABLES -A INPUT -p tcp --dport 20034 -m limit -j LOG \
                                           --log-prefix "Netbus scan"
    $IPTABLES -A INPUT -p tcp --dport 20034 -j DROP
    $IPTABLES -A INPUT -p tcp --dport 31337 -m limit -j LOG \
                                           --log-prefix "Back orifice scan"
    $IPTABLES -A INPUT -p tcp --dport 31337 -j DROP
    
    $IPTABLES -A INPUT -p tcp --dport 6000  -m limit -j LOG \
                                           --log-prefix "X-Windows Port"
    $IPTABLES -A INPUT -p tcp --dport 6000  -j DROP
    
    
    $IPTABLES -A INPUT -p tcp --dport 9704 -m limit --limit 5/minute \
            -j LOG --log-level 6 --log-prefix "rpc.statd(9704) Shell:"
    $IPTABLES -A INPUT -p tcp --dport 9704 -j DROP
    
    $IPTABLES -A INPUT -p tcp --sport 9704 -m limit --limit 5/minute \
            -j LOG --log-level 6 --log-prefix "rpc.statd(9704) Shell:"
    $IPTABLES -A INPUT -p tcp --sport 9704 -j DROP
      ## NetBus and NetBus Pro
    
    $IPTABLES -A INPUT -p tcp --dport 20034 -m limit --limit 5/minute \
            -j LOG --log-level 6 --log-prefix "NetBus Pro:"
    $IPTABLES -A INPUT -p tcp --dport 20034 -j DROP
    $IPTABLES -A INPUT -p tcp --dport 12345:12346 -j DROP
    $IPTABLES -A INPUT -p tcp --dport 12345:12346 -m limit --limit 5/minute \
            -j LOG --log-level 6 --log-prefix "NetBus:"
    
      ## Trinoo
    $IPTABLES -A INPUT -p tcp --sport 27665 -m limit --limit 5/minute \
            -j LOG --log-level 6 --log-prefix "Trinoo:"
    $IPTABLES -A INPUT -p tcp --dport 27665 -m limit --limit 5/minute \
            -j LOG --log-level 6 --log-prefix "Trinoo:"
    $IPTABLES -A INPUT -p tcp --sport 27665 -j DROP
    $IPTABLES -A INPUT -p tcp --dport 27665 -j DROP
    
    $IPTABLES -A INPUT -p udp --sport 27444 -m limit --limit 5/minute \
            -j LOG --log-level 6 --log-prefix "Trinoo:"
    $IPTABLES -A INPUT -p udp --dport 27444 -m limit --limit 5/minute \
            -j LOG --log-level 6 --log-prefix "Trinoo:"
    $IPTABLES -A INPUT -p udp --sport 27444 -j DROP
    $IPTABLES -A INPUT -p udp --dport 27444 -j DROP
    
    $IPTABLES -A INPUT -p udp --sport 31335 -m limit --limit 5/minute \
            -j LOG --log-level 6 --log-prefix "Trinoo:"
    $IPTABLES -A INPUT -p udp --dport 31335 -m limit --limit 5/minute \
            -j LOG --log-level 6 --log-prefix "Trinoo:"
    $IPTABLES -A INPUT -p udp --sport 31335 -j DROP
    $IPTABLES -A INPUT -p udp --dport 31335 -j DROP
    
    
    
      ## Back Orifice
    $IPTABLES -A INPUT -p tcp --dport 31337 -m limit --limit 5/minute \
            -j LOG --log-level 6 --log-prefix "BackOrifice-TCP:"
    $IPTABLES -A INPUT -p udp --dport 31337 -m limit --limit 5/minute \
            -j LOG --log-level 6 --log-prefix "BackOrifice-UDP:"
    $IPTABLES -A INPUT -p tcp --dport 31337 -j DROP
    $IPTABLES -A INPUT -p udp --dport 31337 -j DROP
    
    $IPTABLES -A INPUT -p tcp --sport 31337 -m limit --limit 5/minute \
            -j LOG --log-level 6 --log-prefix "BackOrifice-TCP:"
    $IPTABLES -A INPUT -p udp --sport 31337 -m limit --limit 5/minute \
            -j LOG --log-level 6 --log-prefix "BackOrifice-UDP:"
    $IPTABLES -A INPUT -p tcp --sport 31337 -j DROP
    $IPTABLES -A INPUT -p udp --sport 31337 -j DROP
    
    #Traceroutes depend on finding a rejected port.  DROP the ones it uses
    $IPTABLES -A INPUT -p udp --dport 33434:33523 -j DROP
    
    #Don't log ident because it gets hit all the time eg connecting to an irc server
    $IPTABLES -A INPUT -p tcp --dport 113 -j REJECT
    
    
    #drop netbios lookups
    #don't bother logging them, since they're innocent and frequent
    $IPTABLES -A INPUT -p tcp --dport 137 -j DROP
    $IPTABLES -A INPUT -p udp --dport 137 -j DROP
    
    
    ##i don't want these logged - there's just too many of them
    $IPTABLES -A INPUT -p UDP --dport 67  -j DROP
    $IPTABLES -A INPUT -p UDP --dport 138  -j DROP
    
    ##Catch all rules.
    #iptables reverts to these if it hasn't matched any of the previous rules.
    $IPTABLES -A INPUT -m limit --limit 5/minute -j LOG  \
            --log-prefix "Firewalled packet:"
    $IPTABLES -A FORWARD -m limit --limit 5/minute -j LOG \
            --log-prefix "Firewalled packet:"
    #Reject
    $IPTABLES -A INPUT -p all -j DROP
    $IPTABLES -A FORWARD -p all -j REJECT
    
    #Accept it anyway if it's only output
    $IPTABLES -A OUTPUT -j ACCEPT
```

---

### Post by SeijiSensei on 2018-04-05
Is there a reason why you are limiting this to new connections? I'd get rid of the state module entries.

---

### Post by rlongfield on 2018-04-05
> **SeijiSensei said:**
> Is there a reason why you are limiting this to new connections? I'd get rid of the state module entries.

Copy and paste error really.
I removed the ```
-m state --state NEW
``` and I am left with this: ```
$IPTABLES -A INPUT -p UDP -s $HOME_NETWORK -d $THIS_HOST --dport 1900 -j ACCEPT
```

Unfortunately it didn't change anything. I also noticed traffic on 5353 so I tried to open that port as well and it's not working.
$IPTABLES -I INPUT -p UDP -s $HOME_NETWORK -d $THIS_HOST --dport 5353 -j ACCEPT

---

