---
title: "vsftpd and passive ftp behind hardware router?"
date: 2005-05-19
forum: Server Platforms
---

### Post by mwnovak on 2005-05-19
I'm trying to run vsftpd 2.0.3 on Ubuntu 5.04.  The server is behind a Netgear WGR614 wireless router/firewall, but it also runs its own iptables ruleset.  The problem is simply that, after successfully logging in and establishing a control connection, the FTP session chokes while trying to establish a passive data connection (e.g. listing a directory, downloading a file, etc).  

For example, the Captain FTP client shows the following (I get similar results with SmartFTP and plain-vanilla *nix command-line clients):

```

PASV

227 Entering Passive Mode (63,199,226,113,244,27)
LIST

425 Failed to establish connection.

```

Note that everything works fine for active transfers if the client's firewall allows active ftp (i.e. accepts new connections to "high" ports).  However, most users don't have/want their "high" ports open ... which leaves me trying to make passive transfers work correctly.

So...

I'm mostly convinced this is a firewall issue because, if I forward ports 20-21 and 49152-65535 on the router while setting iptables on the server to allow NEW connections to those ports, passive FTP works just fine.  Of course, I don't want to leave the ephemeral port range sitting wide open to new connections (seems like an awfully big hole, no?).  It's my understanding that the [ip_conntrack_ftp module](http://www.sns.ias.edu/~jns/security/iptables/iptables_conntrack.html) should help me out by noting control connections to port 21 and allowing RELATED inbound connections to 49152-65535... but it doesn't seem to work.  If anyone wants to take a crack at this, my config details are listed below.

In vsftpd.conf, I have the following relevant lines:

```

pasv_enable=YES
pasv_promiscuous=NO
port_enable=NO
port_promiscuous=NO
pasv_max_port=65534
pasv_min_port=49152
pasv_address=63.199.xx.xx  # my external ip address

```

I'm forcing passive mode here for testing, but active transfers work just fine when I set "port_enable=YES".  I've tried running in the promiscuous modes, with the default pasv_min/max port range, and/or without specifying a "pasv_address" ip.  In every event, the client can't establish a passive data connection.

On the Netgear router, I have ports 20-21 and 49152-65534 forwarded to the server's local/internal ip (192.168.1.10).  For the sake of testing, I've tried assigning the server as an un-firewalled DMZ host, and I've also tried disabling SPI on the router... no joy.

So, now for the server's iptables script... I won't post the entire script unless someone asks for it, but it's based on [an example by James C. Stephens](http://www.sns.ias.edu/~jns/security/iptables/rules.html).  The integral bits are as follows:

```

# modules
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_conntrack
modprobe ip_conntrack_ftp

# drop by default
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP

# loopback
iptables -A INPUT  -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

# SSH
iptables -A OUTPUT  -o $IFACE -p tcp --sport 22 -m state --state ESTABLISHED -j ACCEPT
iptables -A INPUT -i $IFACE -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT

# ftp
UP_PORTS="49152:65534"

# control 
iptables -A INPUT  -i $IFACE -p tcp --dport 21 -m state --state NEW,ESTABLISHED -j LOG --log-prefix "1: FTP Control IN "
iptables -A INPUT  -i $IFACE -p tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o $IFACE -p tcp --sport 21 -m state --state ESTABLISHED -j LOG --log-prefix "2: FTP Control OUT "
iptables -A OUTPUT -o $IFACE -p tcp --sport 21 -m state --state ESTABLISHED -j ACCEPT

# active data (used with "port_enable=YES" in vsftpd.conf; commented out for the moment)
#iptables -A OUTPUT -o $IFACE -p tcp --sport 20 -m state --state NEW,ESTABLISHED -j LOG --log-prefix "3a: Active FTP Data OUT "
#iptables -A OUTPUT -o $IFACE -p tcp --sport 20 -m state --state NEW,ESTABLISHED -j ACCEPT
#iptables -A INPUT  -i $IFACE -p tcp --dport 20 -m state --state ESTABLISHED -j LOG --log-prefix "4a: Active FTP Data IN "
#iptables -A INPUT  -i $IFACE -p tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT

# passive data
iptables -A INPUT  -i $IFACE -p tcp --dport $UP_PORTS -m state --state ESTABLISHED,RELATED -j LOG --log-prefix "3b: Pasv FTP Data IN "
iptables -A INPUT  -i $IFACE -p tcp --dport $UP_PORTS -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -o $IFACE -p tcp --sport $UP_PORTS -m state --state ESTABLISHED -j LOG --log-prefix "4b: Pasv FTP Data OUT "
iptables -A OUTPUT -o $IFACE -p tcp --sport $UP_PORTS -m state --state ESTABLISHED -j ACCEPT

# Any tcp not already allowed is logged and then dropped.
iptables -A INPUT  -i $IFACE -p tcp -j LOG --log-prefix "IPTABLES TCP-IN: "
iptables -A INPUT  -i $IFACE -p tcp -j DROP
iptables -A OUTPUT -o $IFACE -p tcp -j LOG --log-prefix "IPTABLES TCP-OUT: "
iptables -A OUTPUT -o $IFACE -p tcp -j DROP

```      

Logging of the FTP control/data bits is to help debug the problem.  Note that I've used information presented in the [Linux Home Networking tutorial on FTP Server Setup](http://www.siliconvalleyccie.com/linux-hn/ftp-server.htm) to guide my construction of rules for FTP control and active/passive data connections.  Someone double-check me, but I think I've got it right.

Now for the logs...

A passive FTP session gives the following (edited for brevity; 67.161.xx.xx is the client's external ip, 63.199.xx.xx is the server's external ip, 192.168.1.10 is the server's internal/non-public ip):

```

May 19 12:52:29 localhost kernel: 1: FTP Control IN IN=eth0 OUT= MAC=00:30:65:c1:8d:72:00:09:5b:d6:06:0c:08:00 SRC=67.161.xx.xx DST=192.168.1.10 LEN=60 TOS=0x00 PREC=0x00 TTL=50 ID=2641 PROTO=TCP SPT=32775 DPT=21 WINDOW=65535 RES=0x00 SYN URGP=0 
May 19 12:52:29 localhost kernel: 2: FTP Control OUT IN= OUT=eth0 SRC=192.168.1.10 DST=67.161.xx.xx LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=21 DPT=32775 WINDOW=5760 RES=0x00 ACK SYN URGP=0 
May 19 12:52:29 localhost kernel: 1: FTP Control IN IN=eth0 OUT= MAC=00:30:65:c1:8d:72:00:09:5b:d6:06:0c:08:00 SRC=67.161.xx.xx DST=192.168.1.10 LEN=52 TOS=0x00 PREC=0x00 TTL=50 ID=2642 PROTO=TCP SPT=32775 DPT=21 WINDOW=65535 RES=0x00 ACK URGP=0 
May 19 12:52:29 localhost vsftpd: Thu May 19 12:52:29 2005 [pid 7445] CONNECT: Client "67.161.xx.xx"
May 19 12:52:29 localhost vsftpd: Thu May 19 12:52:29 2005 [pid 7445] FTP response: Client "67.161.xx.xx", "220 -- welcome to [hostname].org -- explicit SSL is required -- play nice --"

## the client and server proceed to negotiate a login, eventually resulting in:

May 19 12:52:29 localhost vsftpd: Thu May 19 12:52:29 2005 [pid 7444] [cjjohnston] OK LOGIN: Client "67.161.xx.xx"
May 19 12:52:29 localhost vsftpd: Thu May 19 12:52:29 2005 [pid 7446] [cjjohnston] FTP response: Client "67.161.xx.xx", "230 Login successful."

## after a bit more negotiation (SYST, etc), we get:

May 19 12:52:31 localhost kernel: 2: FTP Control OUT IN= OUT=eth0 SRC=192.168.1.10 DST=67.161.xx.xx LEN=105 TOS=0x00 PREC=0x00 TTL=64 ID=54560 DF PROTO=TCP SPT=21 DPT=32775 WINDOW=1708 RES=0x00 ACK PSH URGP=0 
May 19 12:52:31 localhost vsftpd: Thu May 19 12:52:31 2005 [pid 7446] [cjjohnston] FTP command: Client "67.161.xx.xx", "PWD"
May 19 12:52:31 localhost vsftpd: Thu May 19 12:52:31 2005 [pid 7446] [cjjohnston] FTP response: Client "67.161.xx.xx", "257 "/cjjohnston""
May 19 12:52:31 localhost kernel: 1: FTP Control IN IN=eth0 OUT= MAC=00:30:65:c1:8d:72:00:09:5b:d6:06:0c:08:00 SRC=67.161.xx.xx DST=192.168.1.10 LEN=89 TOS=0x00 PREC=0x00 TTL=50 ID=2655 PROTO=TCP SPT=32775 DPT=21 WINDOW=65535 RES=0x00 ACK PSH URGP=0 
May 19 12:52:31 localhost kernel: 2: FTP Control OUT IN= OUT=eth0 SRC=192.168.1.10 DST=67.161.xx.xx LEN=97 TOS=0x00 PREC=0x00 TTL=64 ID=54562 DF PROTO=TCP SPT=21 DPT=32775 WINDOW=1708 RES=0x00 ACK PSH URGP=0 
May 19 12:52:31 localhost kernel: 1: FTP Control IN IN=eth0 OUT= MAC=00:30:65:c1:8d:72:00:09:5b:d6:06:0c:08:00 SRC=67.161.xx.xx DST=192.168.1.10 LEN=89 TOS=0x00 PREC=0x00 TTL=50 ID=2656 PROTO=TCP SPT=32775 DPT=21 WINDOW=65535 RES=0x00 ACK PSH URGP=0 
May 19 12:52:31 localhost vsftpd: Thu May 19 12:52:31 2005 [pid 7446] [cjjohnston] FTP command: Client "67.161.xx.xx", "PASV"
May 19 12:52:31 localhost vsftpd: Thu May 19 12:52:31 2005 [pid 7446] [cjjohnston] FTP response: Client "67.161.xx.xx", "227 Entering Passive Mode (63,199,xx,xx,217,2)"
May 19 12:52:31 localhost kernel: 2: FTP Control OUT IN= OUT=eth0 SRC=192.168.1.10 DST=67.161.xx.xx LEN=129 TOS=0x00 PREC=0x00 TTL=64 ID=54564 DF PROTO=TCP SPT=21 DPT=32775 WINDOW=1708 RES=0x00 ACK PSH URGP=0 
May 19 12:52:31 localhost kernel: 1: FTP Control IN IN=eth0 OUT= MAC=00:30:65:c1:8d:72:00:09:5b:d6:06:0c:08:00 SRC=67.161.xx.xx DST=192.168.1.10 LEN=52 TOS=0x00 PREC=0x00 TTL=50 ID=2658 PROTO=TCP SPT=32775 DPT=21 WINDOW=65535 RES=0x00 ACK URGP=0 
[COLOR=DarkOrange]May 19 12:52:34 localhost kernel: IPTABLES TCP-IN: IN=eth0 OUT= MAC=00:30:65:c1:8d:72:00:09:5b:d6:06:0c:08:00 SRC=67.161.xx.xx DST=192.168.1.10 LEN=60 TOS=0x00 PREC=0x00 TTL=50 ID=2659 PROTO=TCP SPT=32776 DPT=55554 WINDOW=65535 RES=0x00 SYN URGP=0 
May 19 12:52:37 localhost kernel: IPTABLES TCP-IN: IN=eth0 OUT= MAC=00:30:65:c1:8d:72:00:09:5b:d6:06:0c:08:00 SRC=67.161.xx.xx DST=192.168.1.10 LEN=60 TOS=0x00 PREC=0x00 TTL=50 ID=2660 PROTO=TCP SPT=32776 DPT=55554 WINDOW=65535 RES=0x00 SYN URGP=0 
[/COLOR]
## after several lines like the last two listed above (dropped SYN packets, 
## labeled with "IPTABLES TCP-IN"), we get:

May 19 12:53:46 localhost kernel: 1: FTP Control IN IN=eth0 OUT= MAC=00:30:65:c1:8d:72:00:09:5b:d6:06:0c:08:00 SRC=67.161.xx.xx DST=192.168.1.10 LEN=89 TOS=0x00 PREC=0x00 TTL=50 ID=2675 PROTO=TCP SPT=32775 DPT=21 WINDOW=65535 RES=0x00 ACK PSH URGP=0 
May 19 12:53:46 localhost vsftpd: Thu May 19 12:53:46 2005 [pid 7446] [cjjohnston] FTP command: Client "67.161.xx.xx", "LIST"
May 19 12:53:46 localhost kernel: 2: FTP Control OUT IN= OUT=eth0 SRC=192.168.1.10 DST=67.161.xx.xx LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=54566 DF PROTO=TCP SPT=21 DPT=32775 WINDOW=1708 RES=0x00 ACK URGP=0 
[COLOR=DarkOrange]May 19 12:54:17 localhost kernel: IPTABLES TCP-IN: IN=eth0 OUT= MAC=00:30:65:c1:8d:72:00:09:5b:d6:06:0c:08:00 SRC=63.199.xx.xx DST=192.168.1.10 LEN=52 TOS=0x10 PREC=0x00 TTL=64 ID=42294 PROTO=TCP SPT=22 DPT=63521 WINDOW=2352 RES=0x00 ACK RST URGP=0 [/COLOR]
May 19 12:54:46 localhost vsftpd: Thu May 19 12:54:46 2005 [pid 7446] [cjjohnston] FTP response: Client "67.161.xx.xx", "425 Failed to establish connection."
May 19 12:54:46 localhost kernel: 2: FTP Control OUT IN= OUT=eth0 SRC=192.168.1.10 DST=67.161.xx.xx LEN=121 TOS=0x00 PREC=0x00 TTL=64 ID=54568 DF PROTO=TCP SPT=21 DPT=32775 WINDOW=1708 RES=0x00 ACK PSH URGP=0 
May 19 12:54:46 localhost kernel: 1: FTP Control IN IN=eth0 OUT= MAC=00:30:65:c1:8d:72:00:09:5b:d6:06:0c:08:00 SRC=67.161.xx.xx DST=192.168.1.10 LEN=52 TOS=0x00 PREC=0x00 TTL=50 ID=2688 PROTO=TCP SPT=32775 DPT=21 WINDOW=65535 RES=0x00 ACK URGP=0 

```

Note that it steps through the control connection ("1: FTP Control IN" and "2: FTP Control OUT") without a hitch.  However, what _should_ be the first part of the passive data connection gets dropped ("IPTABLES TCP-IN") as not matching any ACCEPT rules in the firewall script.  My assumption is that the ruleset doesn't see that incoming SYN packet ("SPT=32776 DPT=55554") as RELATED to the previous control connection.  But, isn't that what ip_conntrack_ftp is for?  If not, is there any way to get that incoming packet seen as related to the FTP session without simply opening the ephemeral range to all NEW connections?  

I'd thought this might be impossible until I started reading about the ip_conntrack_ftp module... unless I've misunderstood and it's only designed for client (not server) firewalls, everything I've found suggests that module should be exactly what I need to get passive connections working.  But, again, no joy.  One thought: is it possible that the Netgear router is somehow mangling the incoming data packets such that ip_conntrack_ftp can't see them as related to the extant control connection on port 21?  I dunno.

Suggestions?  Comments?  Reading material?

--MW

---

### Post by LordHunter317 on 2005-05-19
To make a long story short: ip_conntrack_ftp can't help you here.

If the linux box was the firewall/router, it could.  But it can't create redirect entries on your NETGEAR, can it?

It should be able to help with limiting the ports required to be open on the FTP Server proper. But you'll still have to redirect that entire port range on the netgear, or whatever range you want to use for passive FTP.

Anyway, to make it work, you need to pass RELATED states as well as ESTABLISHED ones.  You should be doing this anyway.

I didn't look at your firewall rules more in detail, but mght later.

---

### Post by mwnovak on 2005-05-19
> It should be able to help with limiting the ports required to be open on the FTP Server proper. But you'll still have to redirect that entire port range on the netgear, or whatever range you want to use for passive FTP.

Got that ... as mentioned, the Netgear router is already forwarding 20-21 and 49152-65535 to the server's local ip.

The objective, as you note, is limiting the range of ports that accept NEW conncetions on the server itself.  ip_conntrack_ftp can help with this, correct?

> Anyway, to make it work, you need to pass RELATED states as well as ESTABLISHED ones. You should be doing this anyway.

For which elements of the passive FTP process (control in, control out, passive data in, passive data out)?  I'll go through and add RELATED to each iptables rule dealing with FTP and see what happens ... but the "passive data in" rule (client high port > server high port) is the only one that should require it, no? 

--MW

---

### Post by mwnovak on 2005-05-19
Okay, I added RELATED to each of the iptables dealing with FTP:

```

# control
iptables -A INPUT  -i $IFACE -p tcp --dport 21 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -o $IFACE -p tcp --sport 21 -m state --state ESTABLISHED,RELATED -j ACCEPT

# ftp passive data
iptables -A INPUT  -i $IFACE -p tcp --dport 49152:65534 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -o $IFACE -p tcp --sport 49152:65534 -m state --state ESTABLISHED,RELATED -j ACCEPT

```

There was no change in behavior: passive ftp still chokes when it attempts to do anything with the data channel.  Other ideas?

Just out of curiosity, is RELATED really necessary in that first iptables line?

--MW

---

### Post by LordHunter317 on 2005-05-19
Haha.  I figured out why it isn't working.

ftp_conntrack cannot help you, and here's why:
When the client makes a passive FTP connection to your server, it sends out the IP address of your router, plus the port to connection. ftp_conntrack is seeing this and adding a RELATED state entry for that, not for the IP address of your server on the LAN (192.168.whatever). 

However, your router is obviously translating all the packets to have 192.168.whatever as their destination address. So, the RELATED state entries aren't matching.

Whoops. I'm not sure if there are any easy fixes for this. I suppose you could do some PREROUTING NAT tricks to re-write the packet, but I'm not sure I see the value in that. So, I think you'll just goign to have to allow NEW traffic on those ports.

Anyway, lemme give you some advice on your rules:

[list]
[*]Have your first INPUT chain rule be:```
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```This allows all connections that get created by the rules following it. This allows you to write rules that match only initial traffic (i.e., TCP SYN) and makes your ruleset more compact. It also means you won't miss any oddball ICMP traffic that gets marked RELATED, like you might now. There's no security loss in having a generic rule matching against solely these two states
[*]Wherever possible, use port names instead of numbers. ssh instead of 22, for example. iptables understands any name in /etc/services. Some ports are easy to remember, but I for one can't be arsed to remember them all. That's why the file is there, take advantage of it.
[*]Whenever you match a new TCP connection, include the --syn flag. This stops all unusual TCP portscans cold (e.g., XMAS, stealth FIN), barring any bugs in the kernel, of course. It also makes it harder for an attacker to attempt to posion the state table, as they have to present legtimate traffic to get state table entries.
[*]Don't bother with egress filtering. At an invidivual machine level, it's rarely worth the hassle the extra rules create. It's only worth it generally when a box is isolated (i.e., by itself in a colo) and it only performs one task that uses a fixed set of mappable ports. Which isn't many machines. You get more value out of doing egress filtering at a network wide level with the aid of a NIDS or with your border router (your netgear in this case).
[*]Once you get everything working, kill the logging.
[/list]As a courteousy, I'll apply these tidbits to your rules:```
#!/bin/sh

# All the other modules will be loaded automagically
/sbin/modprobe ip_conntrack_ftp

# Default DROP Policy.
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

# Allow existing traffic
/sbin/iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# loopback
iptables -A INPUT  -i lo -j ACCEPT

iptables -A INPUT -i $IFACE -m state --state NEW -p tcp --syn --dport 22 -j ACCEPT

# FTP
UP_PORTS="49152:65534"

# control 
iptables -A INPUT  -i $IFACE --m state --state NEW -p tcp --syn --dport ftp -j LOG --log-prefix "1: FTP Control IN "
iptables -A INPUT  -i $IFACE -m state --state NEW  -p tcp --syn --dport ftp -j ACCEPT

# passive data
iptables -A INPUT  -i $IFACE -m state --state NEW -p tcp --syn --dport $UP_PORTS -j LOG --log-prefix "3b: Pasv FTP Data IN "
iptables -A INPUT  -i $IFACE -m state --state NEW -p tcp --syn --dport $UP_PORTS -j ACCEPT

# Any tcp not already allowed is logged and then dropped.
iptables -A INPUT  -i $IFACE -p tcp -j LOG --log-prefix "IPTABLES TCP-IN: "
iptables -A INPUT  -i $IFACE -p tcp -j DROP
iptables -A OUTPUT -o $IFACE -p tcp -j LOG --log-prefix "IPTABLES TCP-OUT: "
iptables -A OUTPUT -o $IFACE -p tcp -j DROP

```That should cover you, I think.

---

### Post by mwnovak on 2005-05-19
Thanks for the iptables tips: they were well explained and very helpful.  I appreciate it.

I don't mind filtering output for this particular machine, however... it actually does live in a closet serving out ssh, http, and ftp.  I just assume not use any blanket ACCEPT statements, regardless of the direction. :)

As for the original problem, I think I've actually earned your PEBKAC title for the day: did I forget to mention I've got vsftpd using SSL on both control and data channels?  Yeah.  ip_conntrack_ftp can't ... uh ... track what it can't read, can it?  

Hmm... I'm not feeling super bright at the moment.  Do you happen to know of an opensource FTP proxy that'll deal with (implicit or explicit) SSL?  This is a whole new can of worms...

Interestingly enough, I got passive transfers working with my original iptables after disabling SSL.  The only change I made in vsftpd.conf was commenting-out the "pasv_address=63.199.xx.xx" entry.  That gels with your explanation of why ip_conntrack_ftp wasn't working, right?  By not forcing vsftpd to broadcast the router/WAN ip, the conntrack module could add a RELATED marker for internal server address (192.168.xx.xx) ... which correctly matches against the subsequent inbound data packet.

Whew... this is a bit esoteric for me, but at least I understand why conntrack wasn't working (aside from my SSL cramp).  Thanks for helping me sort through this.

--MW

---

### Post by LordHunter317 on 2005-05-20
> **mwnovak]  I just assume not use any blanket ACCEPT statements, regardless of the direction. :)[/quote]That's your call, but think about the gain before you make your final decision.

> As for the original problem, I think I've actually earned your PEBKAC title for the day: did I forget to mention I've got vsftpd using SSL on both control and data channels? Yeah. ip_conntrack_ftp can't ... uh ... track what it can't read, can it? No, it cannot.  BTW, I commit about a thousand PEBKAC errors a day, so don't sweat it  said:**
> Hmm... I'm not feeling super bright at the moment. Do you happen to know of an opensource FTP proxy that'll deal with (implicit or explicit) SSL? This is a whole new can of worms...I think Squid *might* be able to do it, with some work.  Note that the Ubuntu supplied squid probably has SSL support off (as the Debian one does) so you may have to build from source to get it working.

> Interestingly enough, I got passive transfers working with my original iptables after disabling SSL. The only change I made in vsftpd.conf was commenting-out the "pasv_address=63.199.xx.xx" entry. That gels with your explanation of why ip_conntrack_ftp wasn't working, right?Yes it does. However, did you test this with an Internet client?  Unless something's rewritting the PASV commands, they should get a bad IP out on the Interent.

> Whew... this is a bit esoteric for me,That's being polite about FTP.
This is one of the reasons it's largely been abandoned as a transfer protocol.

---

### Post by mwnovak on 2005-05-20
> Yes it does. However, did you test this with an Internet client? Unless something's rewritting the PASV commands, they should get a bad IP out on the Interent.

An internet client, meaning from outside the LAN where the server lives?  Yep, it absolutely works: I successfully tested with *nix-style command-line ftp and the "fancier" Capt. FTP (Mac) and SmartFTP (Win) clients.  No problems.  I'm curious to see if it also works from within the LAN, but I'll have to wait until tomorrow when I can visit the box.

I agree, though ... the reading I've done on passive FTP (more than I ever wanted, at this point) suggests that vsftpd would need the "pasv_address=whatever" line to run passive transfers from behind the router.  So, I dunno.

I just spent an hour reading up on the SuSE ftp-proxy, but I don't think it can deal with SSL.  I'll look at squid and see if I can make heads or tails of it.  At this point, the only thing driving me to implement FTP with SSL is ... ahem ... the "principle" of the thing.  

Yeah, principles: woohoo. 

It'd involve finding new clients for both my Mac and Win machines, but--at this point--I really should just commit to sftp and be done with it.

At any rate, thanks again for your help, I do appreciate it. (maybe stay on the lookout for a squid-related post in the next week or so)       

--MW

---

### Post by 0001001 on 2005-11-18
Hi, 

I've found a solution for this problem but, since I'm not very familiar with Linux, I need some help.

Here's how you get vsftpd + ssl + passive to work:

add the following line to your vsftpd.conf:
 ```
pasv_address=writedownyourstaticiphere
``` 

The main problem is that most of you don't have a static IP, but use a dyndns service such as dyndns.org.
The problem is, that you can't do this:
```
pasv_address=mike123.dyndns.org
``` 
because vsftpd cannot resolve the dns name to an real IP.

There are two solutions:
1. Somebody makes vsftpd work with dns names, so that vsftpd can resolve the address. I have no clue how to do this, but maybe there are some linux gurus or programmers out there to change the vsftpd sources. I hope so, cause most Windows FTP Servers can resolve dns names.

2. That's the solution I'm working on:
Automatically resolve the dyndns name let's say every 15 minutes and write it down to the vsftpd.conf.
Here's how it works:
- type nslookup mike123.dyndns.org
- filter the IP address and send the commandline output to vsftpd.conf

But I'm not very familiar with Linux yet, so I need someone to write a script that does this.

Hope someone can work it out!

---

