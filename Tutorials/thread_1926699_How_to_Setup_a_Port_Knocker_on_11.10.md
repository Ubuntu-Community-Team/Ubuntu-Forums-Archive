---
title: "How to Setup a Port Knocker on 11.10"
date: 2012-02-16
forum: Tutorials
---

### Post by kevdog on 2012-02-16
This guide is an extended updated to my original guide on how to set up FWKNOP as a portknocker: [**_http://ubuntuforums.org/showthread.php?t=812573_**]("http://ubuntuforums.org/showthread.php?t=812573"). 

This guide is applicable to **Ubuntu 11.10 and fwknop version 2.0**.

**[SIZE="5"]I. Overview of Port Knocking[/SIZE]**
An introduction to Port Knocking was covered in the original [guide]("http://ubuntuforums.org/showthread.php?t=812573"). In summary however, port knocking is a method to dynamically open or unmask a hidden port located behind a firewall. Although there are many port knocking implementations: [**_http://www.portknocking.org/view/implementations_**]("http://www.portknocking.org/view/implementations"), this guide covers the port knocking program known as [fwknop]("http://cipherdyne.org/fwknop/").  In this particular implementation, the port is unmasked by dynamic alteration of the server's iptables firewall.  This unmasking however is temporary, and the port is re-cloaked within a specified timeframe (usually 30 seconds). 

Fwknop is different than most port knocking implementations.
[LIST]
[*]The port knocking sequence is a single non-replayable packet -- meaning the server will only act once on the instructions contained in the packet.  If the same packet is re-sent (re-played), this packet is ignored. 
[*]The packet is either symmetrical AES/Rijndael encrypted with use of a password, or asymmetrically encrypted using [GnuPG]("http://www.gnupg.org/").
[*]The detection of packets on the server requires no open ports.  Passive packet sniffing is through libpcap that sniffs packets directly off the wire.
[/LIST]

Fwknop provides both client and server applications.  
[LIST]
[*]Server implementations - Linux (iptables firewalls), BSD/Mac OS X (ipfw firewalls)
[*]Client implementations - Linux, Mac OS, Windows, Android, Iphone/Ipad (coming soon).
[/LIST]

**[SIZE="5"]II. Installation of the FWKNOP Port Knocking Application[/SIZE]**

[SIZE="3"]**Server Installation of the FWKNOP Daemon (Server)**[/SIZE]

Pre-requisite packages:
```
sudo apt-get install build-essential linux-headers-$(uname -r) libpcap-dev libgpgme-dev libgpgme11 libpth-dev libpth20
```
Optional Packages:
```
sudo apt-get install gnupg
```

Fwknop source (Download, Compile and Install):
```
cd ~
[ -d ~/src/fwknop ] || mkdir -p ~/src/fwknop
cd ~/src/fwknop
wget http://cipherdyne.org/fwknop/download/fwknop-2.0.tar.bz2
tar jxf fwknop-2.0.tar.bz2
cd ~/src/fwknop/fwknop-2.0
./configure --with-gpgme
make
sudo make install
```

The fwknopd binary (fwknop daemon server) is located in /usr/local/bin/
The fwknopd configuration files are located in /usr/local/etc/fwknop/

**Verify correct installation of the fwknop daemon**

Included in the FWKNOP sources is a test installation script to verify the FWKNOP installation and server capabilities.

By default, this process assumes there is a mail server executable located at /bin/mail.  By default the fwknop server is designed to mail the server administrator notification everytime the fwknop process executes.

The test installation script produces many errors if an executable mail transfer agent (MTA) does not exist at /bin/mail.  
--If you have a MTA (mail transfer agent) and would like to utilize this notification feature, I would recommend creating a symbolic link from /bin/mail to your preferred mailing program.  This would be performed with the following code:
```
sudo ln -s <actual MTA/executable> /bin/mail
``` 

--If you do not have a MTA (mail transfer agent) and/or do not want to implement this notification feature, create a temporary link (this will be removed later) to allow the test program to complete
```
sudo ln -s /bin/echo /bin/mail
```

Run the Fwkop self installation test to verify the server was correctly installed:
```
sudo perl ~/src/fwknop/fwknop-2.0/test-fwknop.pl
```

Result of my test script appeared as the following:
```
[+] Starting the fwknop test suite...

    args: 

    Saved results from previous run to: output.last/

[build] [client] binary exists......................................pass (1)
[build security] [client] Position Independent Executable (PIE).....pass (2)
[build security] [client] stack protected binary....................pass (3)
[build security] [client] fortify source functions..................pass (4)
[build security] [client] read-only relocations.....................pass (5)
[build security] [client] immediate binding.........................pass (6)
[build] [server] binary exists......................................pass (7)
[build security] [server] Position Independent Executable (PIE).....pass (8)
[build security] [server] stack protected binary....................pass (9)
[build security] [server] fortify source functions..................pass (10)
[build security] [server] read-only relocations.....................pass (11)
[build security] [server] immediate binding.........................pass (12)
[build] [libfko] binary exists......................................pass (13)
[build security] [libfko] stack protected binary....................pass (14)
[build security] [libfko] fortify source functions..................pass (15)
[build security] [libfko] read-only relocations.....................pass (16)
[build security] [libfko] immediate binding.........................pass (17)
[preliminaries] [client] usage info.................................pass (18)
[preliminaries] [client] getopt() no such argument..................pass (19)
[preliminaries] [client] --test mode, packet not sent...............pass (20)
[preliminaries] [client] expected code version......................pass (21)
[preliminaries] [server] usage info.................................pass (22)
[preliminaries] [server] getopt() no such argument..................pass (23)
[preliminaries] [server] expected code version......................pass (24)
[preliminaries] collecting system specifics.........................pass (25)
[basic operations] dump config......................................pass (26)
[basic operations] override config..................................pass (27)
[basic operations] [client] --get-key path validation...............pass (28)
[basic operations] [client] require [-s|-R|-a]......................pass (29)
[basic operations] [client] --allow-ip <IP> valid IP................pass (30)
[basic operations] [client] -A <proto>/<port> specification.........pass (31)
[basic operations] [client] generate SPA packet.....................pass (32)
[basic operations] [server] list current fwknopd fw rules...........pass (33)
[basic operations] [server] list all current fw rules...............pass (34)
[basic operations] [server] flush current firewall rules............pass (35)
[basic operations] [server] start...................................pass (36)
[basic operations] [server] stop....................................pass (37)
[basic operations] [server] write PID...............................pass (38)
[basic operations] [server] --packet-limit 1 exit...................pass (39)
[basic operations] [server] ignore packets < min SPA len (140)......pass (40)
[basic operations] [server] -P bpf filter ignore packet.............pass (41)
[Rijndael SPA] [client+server] complete cycle (tcp/22 ssh)..........pass (42)
[Rijndael SPA] [client+server] packet aging (past) (tcp/22 ssh).....pass (43)
[Rijndael SPA] [client+server] packet aging (future) (tcp/22 ssh)...pass (44)
[Rijndael SPA] [client+server] expired stanza (tcp/22 ssh)..........pass (45)
[Rijndael SPA] [client+server] invalid expire date (tcp/22 ssh).....pass (46)
[Rijndael SPA] [client+server] expired epoch stanza (tcp/22 ssh)....pass (47)
[Rijndael SPA] [client+server] future expired stanza (tcp/22 ssh)...pass (48)
[Rijndael SPA] [client+server] OPEN_PORTS (tcp/22 ssh)..............pass (49)
[Rijndael SPA] [client+server] OPEN_PORTS mismatch..................pass (50)
[Rijndael SPA] [client+server] require user (tcp/22 ssh)............pass (51)
[Rijndael SPA] [client+server] user mismatch (tcp/22 ssh)...........pass (52)
[Rijndael SPA] [client+server] require src (tcp/22 ssh).............pass (53)
[Rijndael SPA] [client+server] mismatch require src (tcp/22 ssh)....pass (54)
[Rijndael SPA] [client+server] IP filtering (tcp/22 ssh)............pass (55)
[Rijndael SPA] [client+server] subnet filtering (tcp/22 ssh)........pass (56)
[Rijndael SPA] [client+server] IP+subnet filtering (tcp/22 ssh).....pass (57)
[Rijndael SPA] [client+server] IP match (tcp/22 ssh)................pass (58)
[Rijndael SPA] [client+server] subnet match (tcp/22 ssh)............pass (59)
[Rijndael SPA] [client+server] multi IP/net match (tcp/22 ssh)......pass (60)
[Rijndael SPA] [client+server] multi access stanzas (tcp/22 ssh)....pass (61)
[Rijndael SPA] [client+server] bad/good key stanzas (tcp/22 ssh)....pass (62)
[Rijndael SPA] [client+server] non-enabled NAT (tcp/22 ssh).........pass (63)
[Rijndael SPA] [client+server] NAT to 192.168.1.2 (tcp/22 ssh)......pass (64)
[Rijndael SPA] [client+server] force NAT 192.168.1.123 (tcp/22 ssh).pass (65)
[Rijndael SPA] [client+server] complete cycle (tcp/23 telnet).......pass (66)
[Rijndael SPA] [client+server] complete cycle (tcp/9418 git)........pass (67)
[Rijndael SPA] [client+server] complete cycle (udp/53 dns)..........pass (68)
[Rijndael SPA] [client+server] -P bpf SPA over port 12345...........pass (69)
[Rijndael SPA] [client+server] random SPA port (tcp/22 ssh).........pass (70)
[Rijndael SPA] [client+server] spoof username (tcp/22)..............pass (71)
[Rijndael SPA] [client+server] replay attack detection..............pass (72)
[Rijndael SPA] [server] digest cache structure......................pass (73)
[Rijndael SPA] [client+server] non-base64 altered SPA data..........pass (74)
[Rijndael SPA] [client+server] base64 altered SPA data..............pass (75)
[Rijndael SPA] [client+server] appended data to SPA pkt.............pass (76)
[Rijndael SPA] [client+server] prepended data to SPA pkt............pass (77)
[GnuPG (GPG) SPA] [client+server] complete cycle (tcp/22 ssh).......pass (78)
[GnuPG (GPG) SPA] [client+server] multi gpg-IDs (tcp/22 ssh)........pass (79)
[GnuPG (GPG) SPA] [client+server] complete cycle (tcp/23 telnet)....pass (80)
[GnuPG (GPG) SPA] [client+server] complete cycle (tcp/9418 git).....pass (81)
[GnuPG (GPG) SPA] [client+server] complete cycle (udp/53 dns).......pass (82)
[GnuPG (GPG) SPA] [client+server] replay attack detection...........pass (83)
[GnuPG (GPG) SPA] [client+server] non-base64 altered SPA data.......pass (84)
[GnuPG (GPG) SPA] [client+server] base64 altered SPA data...........pass (85)
[GnuPG (GPG) SPA] [client+server] appended data to SPA pkt..........pass (86)
[GnuPG (GPG) SPA] [client+server] prepended data to SPA pkt.........pass (87)
[GnuPG (GPG) SPA] [client+server] spoof username (tcp/22 ssh).......pass (88)
[GnuPG (GPG) SPA] [server] digest cache structure...................pass (89)

[+] passed/failed/executed: 89/0/89 tests
```

Any errors encountered with the self-test may be debugged by looking at the test result files located in: ~/src/fwknop/fwknop-2.0/test/output
If unable to correct the source of the error, please consult the [[B]_fwknop mailing list_[/B]("https://lists.sourceforge.net/lists/listinfo/fwknop-discuss")]

**[SIZE="5"]III. Configuration of the FWKNOP Port Knocking Daemon[/SIZE]**

There are two configuration files for FWKNOP:
[LIST]
[*]access.conf - /usr/local/etc/fwknop/access.conf
[*]fwknopd.conf - /usr/local/etc/fwknop/fwknopd.conf
[/LIST]
Each file must be edited as root. (ie gksu gedit ....)

***I. Modification of the /usr/local/etc/fwknop/fwknopd.conf file***
Directives to consider. Please remove any preceeding #'s on the lines being edited:

[I]PCAP_INTF -- Change this to your appropriate interface (eth0, wlan0, br0, etc)
MAX_SPA_PACKET_AGE - I chose 1000.  This seemed to work best when dealing with android clients
FLUSH_IPT_AT_INIT  Y
FLUSH_IPT_AT_EXIT  Y
FWKNOP_RUN_DIR		    /var/run/fwknop/;
FWKNOP_CONF_DIR             /usr/local/etc/fwknop;
ACCESS_FILE                 /usr/local/etc/fwknop/access.conf;
FWKNOP_PID_FILE             $FWKNOP_RUN_DIR/fwknopd.pid;
DIGEST_FILE                 $FWKNOP_RUN_DIR/digest.cache;
FIREWALL_EXE                /sbin/iptables;[/I]

***II. Modification of the /usr/local/etc/fwknop/access.conf file*** **(Mandatory)**
The access.conf file is the heart of the Port Knocking Daemon.  Options in this file control who can send packets, what incoming ports to open in the firewall after verification of the port knocking packet, the duration of time to keep the port open for incoming connections, the type of encryption method expected for the port knock (symmetric vs asymmetric), and commands are to be executed on the fwknop daemon server.  Example configurations are given in the file.

Configurations are usually done at the end of this file.  **There can be multiple configurations each set for a different user, IP source, encryption type, etc.**

A minimum edit to include symmetric AES encryption:

[I]SOURCE: ANY;
KEY: **<!!!!CHANGE ME TO YOUR SYMMETRIC ENCRYPTION PASSWORD!!>**;
FW_ACCESS_TIMEOUT: 30;[/I]

A minimum edit to include GPG-capable encryption/decryption:

[I]SOURCE: ANY;
GPG_HOME_DIR: /root/.gnupg;
GPG_DECRYPT_ID: <!! Server Master GnuPG Key Identifier *****See GnuPG section below** !!>;
GPG_DECRYPT_PW: <!!! Change to ROOT PASSWORD OF GPG PRIVATE KEY !!>;
GPG_REQUIRE_SIG: Y;
GPG_IGNORE_SIG_VERIFY_ERROR: N;
GPG_REMOTE_ID: <!! Client Master GnuPG Key Identifier [B]***See GnuPG section below[/B!!>;
FW_ACCESS_TIMEOUT: 30;[/I]

**[SIZE="5"]IV. Putting it All Together -- Illustrative Examples[/SIZE]**

Requirements for Testing Procedure:
1. Two separate computers - one acting as the fwknop/ssh client, and the other acting as the fwnkop/ssh daemon server.  The client must have a valid ssh account on the server.
2. A running OpenSSH daemon on the server
3. An active Iptables Firewall on the server.
4. A port scanner on the client machine to verify opening an closure of the incoming port on the server (Port 22).  Nmap will be our chosen port scanner.
5. Verification Steps to Ensure Everything is Working as Expected (Mostly applicable to server).

**[SIZE="3"]Client and Server Setup[/SIZE]**
(A Full explanation for the OpenSSH server setup may be found here: [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH))

**Client Machine**

*OpenSSH*Clients:
[INDENT]Ubuntu (Linux Machine) or Mac OS X - OpenSSH client installed by default at time of installation. [/INDENT]
[INDENT]Windows - OpenSSH client provided by installation of either **_[cygwin]("http://www.cygwin.com/")_** or **_[putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/")_**.[/INDENT]
[INDENT]Android SSH Clients[/INDENT] 
[INDENT][INDENT]ConnectBot - **_[https://market.android.com/details?id=org.connectbot&feature=search_result#?t=W251bGwsMSwxLDEsIm9yZy5jb25uZWN0Ym90Il0.]("https://market.android.com/details?id=org.connectbot&feature=search_result#?t=W251bGwsMSwxLDEsIm9yZy5jb25uZWN0Ym90Il0.")_**[/INDENT][/INDENT]
[INDENT][INDENT]AndFTP - **_[https://market.android.com/details?id=lysesoft.andftp&feature=search_result#?t=W251bGwsMSwxLDEsImx5c2Vzb2Z0LmFuZGZ0cCJd]("https://market.android.com/details?id=lysesoft.andftp&feature=search_result#?t=W251bGwsMSwxLDEsImx5c2Vzb2Z0LmFuZGZ0cCJd")_**[/INDENT][/INDENT]

*Fwknop*Clients:
[INDENT]Linux/MAC Fwknop Client- Compilation of the Server will automatically also compile the command line fwknop client.  The client executable is located in /usr/local/bin/fwknop[/INDENT]
[INDENT]Windows Fwknop Clients[/INDENT]
[INDENT][INDENT]Fwknop Client using _**[Cygwin]("http://www.cygwin.com/")**_ -- Compile only the fwknop client from source using: ./configure --disable-client --with-gpgme[/INDENT][/INDENT]
[INDENT][INDENT]Precompiled Fwknop Command Line client - **_[http://cipherdyne.org/fwknop/download/fwknop-static.exe]("http://cipherdyne.org/fwknop/download/fwknop-static.exe")_**[/INDENT][/INDENT]
[INDENT][INDENT]Windows GUI Client (Basic Functionality) - **_[http://cipherdyne.org/fwknop/download/fwknop-client-1.8.2-alpha-src.zip]("http://cipherdyne.org/fwknop/download/fwknop-client-1.8.2-alpha-src.zip")_**[/INDENT][/INDENT]
[INDENT]Android FWKNOP Client[/INDENT]
[INDENT][INDENT][/INDENT]Fwknop Client - **_[https://market.android.com/details?id=com.max2idea.android.fwknop&feature=search_result#?t=W251bGwsMSwxLDEsImNvbS5tYXgyaWRlYS5hbmRyb2lkLmZ3a25vcCJd]("https://market.android.com/details?id=com.max2idea.android.fwknop&feature=search_result#?t=W251bGwsMSwxLDEsImNvbS5tYXgyaWRlYS5hbmRyb2lkLmZ3a25vcCJd")_**[/INDENT]

**Server Machine: Platform Ubuntu Linux**

*OpenSSH Server Installation* 
[INDENT]Please consult Ubuntu documentation.  Although I would recommend making changes to the default ssh daemon configuration, the default settings will work in this setting[/INDENT]

*FWKNOP Server Installation*
Please see steps mentioned previously in this guide. Please ensure the test suite was run to confirm a proper installation

***!!IMPORTANT!!*** Prior to proceeding, please confirm that the OpenSSH server is appropriately installed, and that the client can connect to the server.

**[SIZE="3"]IPTables Firewall Setup on Server Machine[/SIZE]**

***If you already have an existing Iptables firewall established, please save the old configuration via:
```
sudo iptables-save -c > /etc/iptables-save 
```

Later the iptables can be restored if needed:
```
cat /etc/iptables-save | sudo iptables-restore -c
```
****

Below I've included my Iptables script file. Please use this file as a reference.  Portions of this script may be deleted if it doesn't meet the needs of an individual user.

```
#!/bin/bash

### Gloval Variables
IPTABLES=/sbin/iptables
IP6TABLES=/sbin/ip6tables
MODPROBE=/sbin/modprobe
INT_NET=<!!CHANGE TO INTERNAL NETWORK!!>  Examples: 192.168.1.0/24, 10.0.1.0/24
SSH_PORT=<!!CHANGE TO LISTENING SSH PORT!!> Default port number is 22
SERVER_INTERFACE=<!!Change to Listening Netork Interface!!> Examples: eth0,wlan0,br0

##Function to determine Local IP address of server
getaddr() {
  dev=$1
  name=$2
  L=`ip addr show dev $dev | grep inet | grep -v :`
  test -z "$L" && { 
    eval "$name=''"
    return
  }
  OIFS=$IFS
  IFS=" /"
  set $L
  eval "$name=$2"
  IFS=$OIFS
}

getaddr $SERVER_INTERFACE SERVER_IP


### flush existing rules and set chain policy setting to DROP
echo "[+] Flushing existing iptables rules..."
$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X
$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT DROP
$IPTABLES -P FORWARD DROP

### this policy does not handle IPv6 traffic except to drop it.
#
echo "[+] Disabling IPv6 traffic..."
$IP6TABLES -P INPUT DROP
$IP6TABLES -P OUTPUT DROP
$IP6TABLES -P FORWARD DROP

### load connection-tracking modules
#
$MODPROBE ip_conntrack
$MODPROBE iptable_nat
$MODPROBE ip_conntrack_ftp
$MODPROBE ip_nat_ftp

###### INPUT chain ######
#
echo "[+] Setting up INPUT chain..."

### state tracking rules
echo "         .....State Tracking Rules"
$IPTABLES -A INPUT -m state --state INVALID -j LOG --log-prefix "DROP IN INVALID " --log-ip-options --log-tcp-options
$IPTABLES -A INPUT -m state --state INVALID -j DROP
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

### ACCEPT rules
echo "         .....Common Ports"
$IPTABLES -A INPUT -p tcp -s $INT_NET --dport $SSH_PORT --syn -m state --state NEW -j DROP
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -j ACCEPT

# CIFS/SMB ACCEPT Rules
echo "         .....CIFS/SMB"
$IPTABLES -A INPUT -p tcp -s $INT_NET --sport 137:139 --dport 137:139 -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -p udp -s $INT_NET --sport 137:139 --dport 137:139 -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -p tcp -s $INT_NET --sport 137:139 --dport 1024:65535 -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -p udp -s $INT_NET --sport 137:139 --dport 1024:65535 -m state --state NEW -j ACCEPT

# MULTICAST
echo "         .....Multicast"
$IPTABLES -A INPUT -p udp --dport 5353 -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -p tcp --dport 5353 -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -s 0/0 -d 224.0.0.0/24 -m state --state NEW -j ACCEPT

### default INPUT LOG rule
echo "         .....Default INPUT LOG Rule"
$IPTABLES -A INPUT ! -i lo -j LOG --log-prefix "DROP IN- " --log-ip-options --log-tcp-options

### make sure that loopback traffic is accepted
$IPTABLES -A INPUT -i lo -j ACCEPT

###### OUTPUT chain ######
#
echo "[+] Setting up OUTPUT chain..."

### state tracking rules
echo "         .....State Tracking Rules"
$IPTABLES -A OUTPUT -m state --state INVALID -j LOG --log-prefix "DROP OUT INVALID " --log-ip-options --log-tcp-options
$IPTABLES -A OUTPUT -m state --state INVALID -j DROP
$IPTABLES -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

### ACCEPT rules for allowing connections out
echo "         .....Common Ports"
$IPTABLES -A OUTPUT -p tcp --dport 21 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 22 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 2222 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 25 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 43 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 4321 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 53 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p udp --dport 53 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT

## NoIP
echo "         .....NoIP"
$IPTABLES -A OUTPUT -p tcp --dport 8245 -m state --state NEW -j ACCEPT

# Multicast DNS
echo "         .....Multicast"
$IPTABLES -A OUTPUT -p tcp --dport 5353 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p udp --dport 5353 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -s $SERVER_IP -d 224.0.0.0/24 -m state --state NEW -j ACCEPT

# CIFS
echo "         .....CIFS"
$IPTABLES -A OUTPUT -p tcp --sport 137:139 -d $INT_NET --dport 137:139 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p udp --sport 137:139 -d $INT_NET --dport 137:139 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --sport 1024:65535 -d $INT_NET --dport 137:139 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p udp --sport 1024:65535 -d $INT_NET --dport 137:139 -m state --state NEW -j ACCEPT

# SMB
echo "         .....SMB"
$IPTABLES -A OUTPUT -p tcp -s $INT_NET --dport 445 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p udp -s $INT_NET --dport 445 -m state --state NEW -j ACCEPT 

## GMail SMTP
echo "         .....Gmail SMTP"
$IPTABLES -A OUTPUT -p tcp --dport 993 -m state --state NEW -j ACCEPT

### default OUTPUT LOG rule
echo "         .....Default OUTPUT LOG Rule"
$IPTABLES -A OUTPUT ! -o lo -j LOG --log-prefix "DROP OUT- " --log-ip-options --log-tcp-options

### make sure that loopback traffic is accepted
$IPTABLES -A OUTPUT -o lo -j ACCEPT

###### FORWARD chain ######
#
echo "[+] Setting up FORWARD chain..."

### state tracking rules
echo "         .....State Tracking Rules"
$IPTABLES -A FORWARD -m state --state INVALID -j LOG --log-prefix "DROP INVALID " --log-ip-options --log-tcp-options
$IPTABLES -A FORWARD -m state --state INVALID -j DROP
$IPTABLES -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

### ACCEPT rules
echo "         .....Common Ports"

# CIFS
echo "         .....CIFS"
$IPTABLES -A FORWARD -p udp -s $INT_NET --sport 137:139 -d $INT_NET --dport 137:139 -m state --state NEW -j ACCEPT

# MULTICAST
echo "         .....Multicast"
$IPTABLES -A FORWARD -p udp -s $INT_NET --sport 5353 -d 224.0.0.0/24 --dport 5353 -m state --state NEW -j ACCEPT

# Dynamic Device Discovery
echo "         .....Dynamic Device Discovery"
$IPTABLES -A FORWARD -p udp -s $INT_NET --sport 9131 --dport 9131 -m state --state NEW -j ACCEPT

### default LOG rule
echo "         .....Default FORWARD LOG Rule"
$IPTABLES -A FORWARD ! -i lo -j LOG --log-prefix "DROP F- " --log-ip-options --log-tcp-options

###### NAT rules ######
#
echo "[+] Setting up NAT rules..."

###### forwarding ######
#
echo "[+] Enabling IP forwarding..."
echo 1 > /proc/sys/net/ipv4/ip_forward

exit
### EOF ### 
```

Copy and paste this into your editor **as root** and make the appropriate changes within the Global Variables section, and then alter/delete/insert appropriate configurations within the remainder of the file. Save the file. Make the file executable -- ie sudo chmod +x <file_name>

For purposes of this guide I will refer to the file as ~/usr/local/sbin/iptables.sh
This script will first clear and setup firewall rules.  This script may be executed by:
```
sudo ~/usr/local/sbin/iptables.sh
```

**Verification of Firewall Rules -- Specifically SSH**

If the firewall rules are executed, nmap can be used to confirm or verify that the ssh listening port is filtered.  This can be done on the server itself using the nmap client. Assuming ssh is listening on port 22, this can be done similarly to:
```
nmap -p 22 <server IP address>

Starting Nmap 4.62 ( http://nmap.org )

Interesting ports on <server IP address>:
PORT   STATE    SERVICE
22/tcp filtered ssh
MAC Address: 00:40:96:AF:E3:0C (Cisco Systems)

Nmap done: 1 IP address (1 host up) scanned in 0.675 seconds
```

Despite filtering of the incoming port by the firewall, the server should be listening for connections:
```
$ sudo netstat -anlp | grep sshd
tcp6   0    0 :::22      :::*      LISTEN    4396/sshd
```

**[SIZE="3"]FWKNOP Daemon Setup on Server[/SIZE]**

**Configuration of the server's FWKNOP access.conf file (/usr/local/etc/fwknop/access.conf)**
For this example's purpose, we are going to consider the fwknop password = Ubuntu.  This password will act as the shared secret key for the Rijndael symmetric cipher.  When authenticating the password, the server will open port 22 for incoming connections for a maximum of 30 seconds to allow for an establishment of a ssh connection.

Editing the access.conf file as root (ie gksu gedit /usr/local/etc/fwknop/access.conf), add the following to the end of the file:

```
[I]SOURCE: ANY;
KEY: **<ACCESS_PASSWORD>**;
FW_ACCESS_TIMEOUT: 30;[/I]
```

**Starting FWKNOP Daemon as a service**
Rather than utilizing init.d scripts for services, Ubuntu utilizes Upstart to manage running services.  The fwknopd (fwknop daemon), may be manually started at the command line (sudo fwknopd -f -v), however in most cases, it would be preferable to start this service a boot time.  In order to utilize Upstart, an upstart script needs to be composed.

Create the upstart fwknopd script:
```
gksu gedit /etc/init/fwknopd.conf
```

Below is my current sample script I use for the fwknopd service:

[I]```
#FWKNOP Daemon

description "fwknop daemon- http://cipherdyne.org/fwknop/"

start on (starting network-interface
          or starting network-manager
          or starting networking)

stop on runlevel [!023456]

console output

respawn
respawn limit 10 5

pre-start script
    test -x /usr/local/sbin/fwknopd || { stop; exit 0; }
    test -x /usr/local/sbin/iptables.sh || { stop; exit 0; }
    /usr/local/sbin/iptables.sh
end script

pre-stop script
    /usr/local/sbin/fwknopd --fw-flush
end script

exec /usr/local/sbin/fwknopd -f
```[/I]

By adding the fwknop daemon to upstart, the fwknopd service will be automatically started at boot.  This service can also manually started,stopped or restarted by:
```
sudo service fwknopd <start|stop|restart>
```

******Please note with and manual modification of the iptables script (/usr/local/bin/iptables.sh), the fwknopd must be restarted. This could be implemented into the firewall script if the user desired!!!***

**[SIZE="3"]Utilizing the Client to send the Port Knock Sequence and open the Firewall[/SIZE]**

The client must send a fwknop encrypted packet to the server in order for the fwknop daemon to decrypt the packet, open a hole in the firewall, and unmask the listening process.

This guide will cover the command line client.  GUI clients require little explanation.

On the client machine, a port knocking packet -- specifically a SPA (Single Packet Authorization) packet as implemented by fwknop -- can be generated by:
fwknop -A <protocol/<port number> -s -D <serverIP>

The following would contruct a SPA packet to open port on the server firewall to allow access to port 22:
fwknop -A tcp/22 -s -D <serverIP ie xxx.xxx.xxx.xxx>

An illustrative example from the client's perspective
Prior to sending the SPA packet - check the status of the ssh listening port:
```
$ nmap -p 22 192.168.1.102

Starting Nmap 4.62 ( http://nmap.org )

Interesting ports on 192.168.1.102:
PORT   STATE    SERVICE
22/tcp filtered ssh
MAC Address: 00:40:96:AF:E3:0C (Cisco Systems)

Nmap done: 1 IP address (1 host up) scanned in 0.675 seconds
```

To dynamically open the servers port 22, construct and send the SPA packet (port knocking sequence) (In this example the packet is constructed with the -v (verbose flag) to demonstrate what is happening behind the scenes):
```

$: fwknop -D <server_ip.com> -A tcp/22 -s -v
Enter encryption password:

FKO Field Values:
=================

   Random Value: 8602308044321333
       Username: admin
      Timestamp: 1329413648
    FKO Version: 1.9.12
   Message Type: 1
 Message String: 0.0.0.0,tcp/22
     Nat Access: <NULL>
    Server Auth: <NULL>
 Client Timeout: 0
    Digest Type: 3

   Encoded Data: 8602308044321333:YWRtaW4:1329413648:1.9.12:1:MC4wLjAuMCx0Y3AvMj
IyMw

SPA Data Digest: /lGbZ270YryFWVno4dCjB6pGpzQ6JWbLhQ3IY38vKu4

Final Packed/Encrypted/Encoded Data:

/Q4QoYlnUofpWqYy8iZUkfPjixHogf/KHuikYzeNEp5pIW4SFMcECqbgYG4JPv5d6dltFLSpdCGD09wF
L6hjWST3T/gSgjjB25DEfUuWb1lPZalYGn502nMz4i6PBD6RZDvQ+BxRBtWb4d5b8/GiabAH70/dMAlb
w

Generating SPA packet:
    protocol: udp
        port: 62201
     IP/host: <server_ip.com>
send_spa_packet: bytes sent: 161

```

After the packet is sent, verify the status of the ssh listening port:
```
$ nmap -p 22 192.168.1.102

Starting Nmap 4.62 ( http://nmap.org )

Interesting ports on 192.168.1.102:
PORT   STATE SERVICE
22/tcp open  ssh
MAC Address: 00:40:96:AF:E3:0C (Cisco Systems)

Nmap done: 1 IP address (1 host up) scanned in 0.407 seconds
```

Server Response to incoming encrypted packet:
```
(stanza #1) SPA Packet from IP: **<client IP>** received with access source match
(stanza #1) No KEY for RIJNDAEL encrypted messages
(stanza #2) SPA Packet from IP: **<client IP>** received with access source match
process_spa_request() CMD: '/sbin/iptables -t filter -A FWKNOP_INPUT -p 6 -s <client IP>
 --dport 22 -m comment --comment _exp_1329413875 -j ACCEPT 2>&1' (re
s: 0, err: )
Added Rule to FWKNOP_INPUT for **<client IP>**, tcp/22 expires at 1329413875
check_firewall_rules() CMD: '/sbin/iptables -t filter -L FWKNOP_INPUT --line-num
bers -n 2>&1' (res: 0, err: )
check_firewall_rules() CMD: '/sbin/iptables -t filter -D FWKNOP_INPUT 1 2>&1' (r
es: 0, err: )
Removed rule 1 from FWKNOP_INPUT with expire time of 1329413875.

```


**[SIZE="5"]V. Implementing GnuPG encryption and authentication with the FWKNOP Port Knocking Daemon (Server)[/SIZE]**

To minimize security risks, I usually secure my SSH server to allow RSA key authentication, and configure my port knocker daemon to accept GnuPG-based key authentication. Limitations to this strategy include the paucity of mobile-platform turnkey GPG-based encryption programs -- translated to mean there a no known Android or Apple based FWKNOP clients that can utilize GPG keys to authenticate.  In addition there are no known Window's GUI clients that also utilize GPG for FWKNOP authentication. Due to this limitation, sending the GPG encrypted port knocking packet is usually done through the command line fwknop client on either linux or mac systems, or windows installation with the use of cygwin.  Compiling the fwknop client to be used via the command line was discussed above.

This portion of the guide will summarize how to implement GPG based FWKNOP authentication.  It will touch on the highlights of using GPG. For those users new to GnuPG, I would suggest possibly consulting these sources as a reference:
[http://ubuntuforums.org/showthread.php?t=687173]("http://ubuntuforums.org/showthread.php?t=687173")
[http://www.spywarewarrior.com/uiuc/gpg/gpg-com-4.htm]("http://www.spywarewarrior.com/uiuc/gpg/gpg-com-4.htm")


**[SIZE="3"]I. Creation of gpg keypairs for Server and Client[/SIZE]**
GPG Keys can usually be 1024, 2048, and 4096 bits in size, however due to the size limitation of an individual networking packet, GPG keys created specifically for this port knocking application can be no more than 2048 bits.  Even if you regularly use GPG keys with email, you may consider creating a new keypair since only these keys are to be specifically used for this application.  


Install GnuPG on the server (if not already installed):
```
sudo apt-get install gnupg
```


**Generate the GnuPG client keypair**

Depending on the client (ubuntu machine, windows, mac, android, iphone), the client keypairs may need to be created on the server and then distributed or created on the client. A client keypair could be created using:
```
$ gpg --gen-key
gpg (GnuPG) 1.4.12-git51c1e84; Copyright (C) 2012 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

gpg: keyring `/home/kevdog/.gnupg/secring.gpg' created
gpg: keyring `/home/kevdog/.gnupg/pubring.gpg' created
Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
Your selection? 1
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (2048) 
Requested keysize is 2048 bits   
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 0
Key does not expire at all
Is this correct? (y/N) y
                        
You need a user ID to identify your key; the software constructs the user ID
from the Real Name, Comment and Email Address in this form:
    "Heinrich Heine (Der Dichter) <heinrichh@duesseldorf.de>"

Real name: example
Email address: example@ubuntu.com
Comment:                         
You selected this USER-ID:
    "example <example@ubuntu.com>"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? o
You need a Passphrase to protect your secret key.    

We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
...................................
gpg: /home/kevdog/.gnupg/trustdb.gpg: trustdb created
gpg: key 82C75770 marked as ultimately trusted
public and secret key created and signed
```

**Generate the server GnuPG keypair**

The process would be similar on the server, however ensure that you create keys as the root user.  This is accomplished:
```
$ sudo su
[sudo] password for kevdog: 
/# gpg --gen-key
.....
```
Root keys are created and kept within the */root/.gnupg* directory.

At this point, two keypairs should be created -- a client keypair and server keypair (or root keypair located on the server).

**[SIZE="3"]II. Distribute and Sign the Keypairs[/SIZE]**
To maximize security, the server will import the client's public gnupg key and sign it.  Conversely the client will import the server's public gnupg key and sign it.  This process is known as key exchange.  Key exchange should be done with the utmost caution, ensuring that the key that you are excepting is originating from the correct source.  

**Exporting the Keys**

Keypairs are identified by numbers. 
```
$ gpg --list-keys
/home/kevdog/.gnupg/pubring.gpg
-------------------------------
pub   2048R/**CD3AD8FE** 2012-02-14
uid                  example <example@ubuntu.com>
sub   2048R/E89298CD 2012-02-14
```

Referencing the above:
[LIST]
[*]**CD3AD8FE** - The public signing key identifier  (**Master Key Identifier**)
[*]E89298CD - The public encryption key identifier
[/LIST]

By default - the keypair can be referenced by the Master Keypair Identifier -- in this example this would be **CD3AD8FE**.  With the client keys, I will refer to this value as the **<ClientMasterKeyIdentifier>**.  The server key pair created by root will be identified by the **<ServerMasterKeyIdentifier>**.  The server keys can be similarly identified by gpg --list-keys running as the root user (**Important -- you must log in as root (sudo su), rather than just doing this as a root process -- sudo**).

The command: *gpg --list-keys* can always be used on either the client or the server (as root) to list the key identifier


**Client -- GnuPG Public Key Export**
The client public key can be exported:
```
$ gpg --export -a <ClientMasterKeyIdentifier> > client_public.key
```

**Server -- GnuPG Public Key Export**
```
$ sudo su
/# gpg --export -a <ServerMasterKeyIdentifier> > server_public.key
```

The client_public.key is then distributed to the server.  Conversely the server_public.key is distributed to the client.  Both the client and server will import key.

**Client -- Import GnuPG public Key of Server**
```
$ gpg --import server_public.key
```


**Server -- Import GnuPG public Key of Client**
```
$ sudo su
/# gpg --import client_public.key
```

Once the keys are imported, sign the imported keys as following:

**Client -- Sign GnuPG public Key of Server**
```
$ gpg --sign-key <ServerMasterKeyIdentifier>
```

**Server -- Sign GnuPG public Key of Client**
```
$ sudo su
/# gpg --sign-key <ClientMasterKeyIdentifier>
```

**[SIZE="3"]III. Configure the FWKNOP Daemon to Recognize the Client's GnuPG Encrypted Port Knocking Packet[/SIZE]**

Now that the GnuPG keys are set up, its time to configure the port knocker daemon to use these keys.

Ensure within the **/usr/local/etc/fwknopd.conf** file that:
**GPG_HOME_DIR** points to the root user's directory where the server gnupg keys are located.  If using the setup as discussed above this would be **/root/.gnupg**.  

Edit the **/usr/local/etc/access.conf** file.  Although global variables can be set, I added a section at the bottom of the file, to specify my settings.  An example is provided below:

[I][INDENT]SOURCE: ANY;
GPG_HOME_DIR: /root/.gnupg;
GPG_DECRYPT_ID: <ServerMasterKeyIdentifier>;
GPG_DECRYPT_PW: <ServerGnuPGPrivateKeyPassword>;
GPG_REQUIRE_SIG: Y;
GPG_IGNORE_SIG_VERIFY_ERROR: N;
GPG_REMOTE_ID: <ClientMasterKeyIdentifier>;
FW_ACCESS_TIMEOUT: 30;[/INDENT][/I]

***Note that if wanting to work with multiple client keys, the GPG_REMOTE_ID variable can be a comma separated list of the ClientMasterKeyIdentifiers.  

Once saving any changes to *fwknopd.conf* and *access.conf*, restart the fwknop daemon:
```
$ sudo service fwknopd restart
```

**[SIZE="3"]IV. Utilize the Fwknop Command-Line Client to send the GnuPG Encrypted Port Knocking Packet[/SIZE]**

As of the time of this writing, only command line clients utilizing fwknop with GnuPG are available.  A variety of GUI, Mobile Applications were discussed above, however these clients utilized a symmetrically encrypted Port Knocking Packet that was encrypted/decrypted via use of a password.  GnuPG encrypted packets are asymmetrically encrypted and signed, requiring the use of pre-distributed keys on both the server and client.  The process for creating and distributing these keys was discussed above.

**Pre-requisites -- Please note that command line fwknop client must be installed on client machine in order to proceed.  Compiling the client from source on a variety of architectures was discussed above.  A precompiled windows client can also be found here: _[COLOR="Red"][http://cipherdyne.org/fwknop/download/binaries.html]("http://cipherdyne.org/fwknop/download/binaries.html")[/COLOR]_

Command Line options for the fwknop client are fully described **_[COLOR="Red"][here]("http://cipherdyne.org/fwknop/docs/manpages/fwknop.html")[/COLOR]_**

**[SIZE="2"]Example Usage with showing the constructed fwknop packet (port knocking packet) along with server response[/SIZE]**

**Client (used with the -v=verbose flag to show the contents of the port knocking packet):**
```
$ fwknop -D <source ip.com> -A tcp/22 -s --gpg-sign **<ClientMasterKeyIdentifier>** --gpg-recipient **<ServerMasterKeyIdentifier>** -v
Enter passphrase for signing:

FKO Field Values:
=================

   Random Value: 1397345259200062
       Username: admin
      Timestamp: 1329413706
    FKO Version: 1.9.12
   Message Type: 1
 Message String: 0.0.0.0,tcp/22
     Nat Access: <NULL>
    Server Auth: <NULL>
 Client Timeout: 0
    Digest Type: 3

   Encoded Data: 1397345259200062:YWRtaW4:1329413706:1.9.12:1:MC4wLjAuMCx0Y3AvMj
IyMw

SPA Data Digest: CsdxZk8R4DdnUNwUmLFNUV5T4ahpDkUwkaBtxmHNkq8

Final Packed/Encrypted/Encoded Data:

EMA1Nqc0b0VAdlAQf+JPQTCUiq3iRcdCVFWVlVw5qjvNa20oNhrch9Wn68+bi4r1m1VuyyuYfQwNX2HA
kYEBTxzsWmMo9GZHy+CMt9Kk+SaWyDm4Vfzp55vPf7hOF9i+B8BRuXx0DELxTeFHvETGb+A1+k1SDXM7
m8Cl+lgAf5sM4Du01kb3BMEiEspi8CEnHjluS++gvjaHvLsvNAl66VWToO5dk4WiOD4g+BJGZJIjvKuu
daQXAYGz8/ihw7EDDNN4zcAPrP9/nc9ra1S4oBALjGRXIw2kG3ehrRiWEv4zX4uM4Bm4fbSD9198zOAu
OfbBygp5CTMwLG5UuVpx/6TiuQmKotTTLDDA93V9LBHgFvuSd2csZKFaCnHE7rEtiytMKdOo1JxYnEN6
qX1FG1jIfV1J99TBdu0dLYLtRSARUh/e6iJAOz0+xWhDnhsMb4tGzTD+BZSCpndIDNrGohZKtprDY4dI
oBzVnQjpr0wQ+Si9rhHmbNFIpm9NTkIXCy3tI9ZMpUJcQqAYJ9CcNJC+E8an4Xp1Z3XnQiaOPxJJBNNw
rWwrdUADOavBJeCi8vw0WrkzroxqH44cGYUIZiYu0zi4Oa/gXIMo0V/7OyX3tfIjROfWVLE4Y1qjA6MM
xolQVfVdzWivka9vmRjFokx842M9fUVNAf4lWokJzcA/nNVBytCklVymkzB0Sw3JJhhb6A55twd48Njk
U0bWkXjoOeQwAKmp6ap7zuQB6SSKwHOedonqNSqGGr6bUZadEwnT9EEEBh3z+RMrbf+I+JkRpzKEUmlo
NEXMv2YID+lSnz80dZAYFHk4V943RuBb5GwuaRJV6fYUyL9dBKfANwfBBGDhylpnFqyTcxfaSu4FczuD
rGZ4U2pg1Z7/YOYVr5IqNj1vyvC0evAj4OX1IMVemegHHWO8lgTnJKjvN8364YIncIc2Hnd23iDJ3hxv
thLf7qbFBuS45k76GArEUo2uJmQzoHOfwLbc25x5A

Generating SPA packet:
    protocol: udp
        port: 62201
     IP/host: <source ip.com>
send_spa_packet: bytes sent: 1001
```

**Server Response (Initially):**
```
(stanza #1) SPA Packet from IP: <client IP> received with access source match
(stanza #1) Incoming SPA data signed by '**<ClientMasterKeyIdentifier>**'.
process_spa_request() CMD: '/sbin/iptables -t filter -A FWKNOP_INPUT -p 6 -s <client IP>
 --dport 22 -m comment --comment _exp_1329413971 -j ACCEPT 2>&1' (re
s: 0, err: )
Added Rule to FWKNOP_INPUT for <client IP>, tcp/22 expires at 1329413971
```

**Server Response (after 30 seconds):**
```
check_firewall_rules() CMD: '/sbin/iptables -t filter -L FWKNOP_INPUT --line-num
bers -n 2>&1' (res: 0, err: )
check_firewall_rules() CMD: '/sbin/iptables -t filter -D FWKNOP_INPUT 1 2>&1' (r
es: 0, err: )
Removed rule 1 from FWKNOP_INPUT with expire time of 1329413971.
```


**[SIZE="5"]VI. Real world Implementation[/SIZE]**
With an android phone, I often use **_[fwknop]("https://market.android.com/details?id=com.max2idea.android.fwknop&feature=search_result#?t=W251bGwsMSwxLDEsImNvbS5tYXgyaWRlYS5hbmRyb2lkLmZ3a25vcCJd")_** along with **_[rsync]("https://market.android.com/details?id=eu.kowalczuk.rsync4android&feature=search_result#?t=W251bGwsMSwyLDEsImV1Lmtvd2FsY3p1ay5yc3luYzRhbmRyb2lkIl0.")_** to remotely back up files and transfer photos to my server.  The happens securely and almost seemlessly. This implementation uses dropbear ssh keys rather than openssh keys, along with a symetrically based (password based) fwknop packet to dynamically alter the firewall.

---

### Post by AcePaus on 2012-04-13
Excellent tutorial! Thank you!!! 

I need help getting client working. 

[SIZE=4]**1.**[/SIZE] [SIZE=4]**How I got server working**[/SIZE]
I ran the excellent test script provided and it passed all tests:
```
[+] passed/failed/executed: 89/0/89 tests
```I followed all the steps up to the examples.

But I could not get the service to run. I made the /etc/init/fwknopd.conf script as in the tutorial. Attempting to start the service did not start it:
```
$ sudo service fwknopd start
fwknopd start/pre-start, process 2481
$ pgrep fwknop*
$

```fwknop was not running. I verified in several different ways. It would not start.

I also tried executing the commands manually in the terminal without the script, but fwknop would still not start/run.

```
$sudo /usr/local/sbin/fwknopd
/usr/local/sbin/fwknopd: error while loading shared libraries: libfko.so.0: cannot open shared object file: No such file or directory
```I checked all the paths and links:

```
$ sudo find / -name libfko.so
<path to source>/.libs/libfko.so
/usr/local/lib/libfko.so

``````
ls -la /usr/local/lib/libfko.so
lrwxrwxrwx 1 root root 15 Apr 12 01:42 /usr/local/lib/libfko.so -> libfko.so.0.0.3

/usr/local/lib# ls -la libfko.so.0.0.3
-rwxr-xr-x 1 root root 263618 Apr 12 01:42 libfko.so.0.0.3
```**Here's part 1 the solution:**
[http://blog.andrewbeacock.com/2007/10/how-to-add-shared-libraries-to-linuxs.html](http://blog.andrewbeacock.com/2007/10/how-to-add-shared-libraries-to-linuxs.html)

```
# vi /etc/ld.so.conf.d/.conf
```Add this one line to the (empty) file:
```
/usr/local/lib/
```run ```
sudo ldconfig
```Try again ```
$sudo /usr/local/sbin/fwknopd
``````

[*] KEY value is not properly set in stanza source 'ANY' in access file: '/usr/local/etc/fwknop/access.conf'
```The key is there! Trying some other values...

 ```
*Invalid access file entry in /usr/local/etc/fwknop/access.conf at line 57.
  - 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx;
 '
[*] No keys found for access stanza source: 'ANY'
 
[*] Data error in access file: '/usr/local/etc/fwknop/access.conf'

```**Here's part 2 the solution:**

There is a second stanza in the access.conf file way down at the bottom (easy to miss). You either need to comment out this 2nd "SOURCE: ANY;" line or provide a key for it. Maybe it has another purpose that I don't know? But I completed the first stanza and commented out the 2nd.

Also, a [COLOR=Magenta]space[/COLOR] is needed after each key of any key-value pair in the file:

[COLOR=Magenta]**No Good:**[/COLOR]
*KEY:*<!!!!CHANGE ME!!>;[I]
[COLOR=Lime]OK:[/COLOR]
[/I]*KEY: *<!!!!CHANGE ME!!>;


Now the server works. :popcorn:
[SIZE=4][B]
2.[/B][/SIZE] [COLOR=Red]**[SIZE=4]How do I get the client working?[/SIZE]**[/COLOR]

How do I install the client files on a Linux client? I do not want to install a MTA or build essentials and compile the source on the client. I built the code on the server. Which files should I copy to the client and where?

Great tutorial!!! I'm looking forward to using this. The features make it the best port knocker I found! Just need to get it working.

Any chance of a 2.0 package getting into the 12.04 repos? It is a lot of work to get this running, even with the great tutorial. (The older package in the repos would not run for me on 12.04. I tried that before building from source. I purged the package also before starting.)

---

### Post by kevdog on 2013-02-18
Sorry about not responding -- its obviously been awhile.  Thanks for the shared libraries tip -- that was great!!

---

### Post by &#3670;&#1763;&#1756;Storm &#3670;&#1763;&#1756;Shadow on 2013-03-12
Thank you for this share.
Take Care

---

