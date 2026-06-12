---
title: "[firehol] Errors on start"
date: 2014-10-11
forum: Security
---

### Post by will-pimblett on 2014-10-11
Hi, I'm running firehol (a iptables config generator) and it's throwing the following on startup

```

FireHOL: Saving your old firewall to a temporary file: OK
FireHOL: Processing file /etc/firehol/firehol.conf: OK
FireHOL: Activating new firewall (47 rules):


--------------------------------------------------------------------------------
ERROR   : # 1.
WHAT    : A runtime command failed to execute (returned error 1).
SOURCE  : line 28 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_internet_ftp_c3 -m state --state ESTABLISHED\,RELATED -m helper --helper ftp -j ACCEPT 
OUTPUT  : 


iptables: No chain/target/match by that name.






--------------------------------------------------------------------------------
ERROR   : # 2.
WHAT    : A runtime command failed to execute (returned error 1).
SOURCE  : line 28 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_internet_ftp_c3 -m state --state ESTABLISHED\,RELATED -m helper --helper ftp -j ACCEPT 
OUTPUT  : 


iptables: No chain/target/match by that name.






--------------------------------------------------------------------------------
ERROR   : # 3.
WHAT    : A runtime command failed to execute (returned error 1).
SOURCE  : line 28 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_internet_irc_c4 -m state --state ESTABLISHED\,RELATED -m helper --helper irc -j ACCEPT 
OUTPUT  : 


iptables: No chain/target/match by that name.






--------------------------------------------------------------------------------
ERROR   : # 4.
WHAT    : A runtime command failed to execute (returned error 1).
SOURCE  : line 28 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_internet_irc_c4 -m state --state ESTABLISHED\,RELATED -m helper --helper irc -j ACCEPT 
OUTPUT  : 


iptables: No chain/target/match by that name.






--------------------------------------------------------------------------------
WARNING : This might or might not affect the operation of your firewall.
WHAT    : A runtime command failed to execute (returned error 1).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/modprobe nf_conntrack_ftp -q 
OUTPUT  : 








--------------------------------------------------------------------------------
WARNING : This might or might not affect the operation of your firewall.
WHAT    : A runtime command failed to execute (returned error 1).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/modprobe nf_conntrack_irc -q 
OUTPUT  : 




 FAILED



```

I'm running a VPS on an OpenVZ host, however the config I'm using worked on 12.04 on the same hardware/environment, I'm now on 14.04.

The line in question on my /etc/firehol/firehol.conf causing this is `client all accept`, which I can't really leave out!

/etc/firehol/firehol.conf for reference

```

version 5

interface venet0 internet
    protection strong 10/sec 10

    # Some servers on the Internet try to ident back the client to find
    # information about the user requesting the service. With our current
    # firewall, such servers will have to timeout before accepting our request.

    server ident reject with tcp-reset

    server ssh accept
    server ftp accept
    server http accept
    server icmp accept [COLOR=#000000]       
    
    client all accept
[/COLOR]
```

---

### Post by will-pimblett on 2014-10-11
This seems related: [http://blog.kylemanna.com/linux/2013/04/26/ufw-vps/](http://blog.kylemanna.com/linux/2013/04/26/ufw-vps/)

---

### Post by Phil_Whineray on 2014-10-13
Hi [br]1[/br] The warnings describe the source of your problems I think: the conntrack modules for ftp and irc are not getting loaded. [br]1[/br] The errors happen because the client all line creates rules which make use of helpers which these modules are needed to provide. [br]1[/br] Are you using a stock kernel? Perhaps a separate package is needed? [br]1[/br]  You can try running the modprobe manually without the -q to see if anything is reported, also check out the contents of dmesg for module load problems: [br]1[/br]  ```
 /sbin/modprobe nf_conntrack_ftp 
``` ```
 dmesg | tail 
``` [br]1[/br] Cheers [br]1[/br] Phil

---

