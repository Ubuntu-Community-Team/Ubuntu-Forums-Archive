---
title: "Can't access to cups web config UI"
date: 2014-09-28
forum: Server Platforms
---

### Post by NarsilAnduril on 2014-09-28
Hi,

First time I install cups on a 14.04 server, doesn't work the same way as on 12.04 ! :-(

Facts :
- Cups is up on the server
- locally, curl localhost:631 returns the web interface
```
diego@kiwi:/var/www/html$ curl localhost:631
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<HTML>
<HEAD>
	<META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8">
	<TITLE>Accueil - CUPS 1.7.2</TITLE>
	<LINK REL="STYLESHEET" TYPE="text/css" HREF="/cups.css">
	<LINK REL="SHORTCUT ICON" HREF="/images/cups-icon.png" TYPE="image/png">
</HEAD>
<BODY>
<TABLE CLASS="page" SUMMARY="{title}">
<TR><TD CLASS="body">
<TABLE BORDER="0" CELLPADDING="0" CELLSPACING="0" SUMMARY="">
<TR HEIGHT="36">
<TD><A HREF="http://www.cups.org/" TARGET="_blank"><IMG
SRC="/images/left.gif" WIDTH="64" HEIGHT="36" BORDER="0" ALT=""></A></TD>
<TD CLASS="sel"><A HREF="/">&nbsp;&nbsp;Accueil&nbsp;&nbsp;</A></TD>
<TD CLASS="unsel"><A HREF="/admin">&nbsp;&nbsp;Administration&nbsp;&nbsp;</A></TD>
<TD CLASS="unsel"><A HREF="/classes/">&nbsp;&nbsp;Classes&nbsp;&nbsp;</A></TD>
<TD CLASS="unsel"><A HREF="/help/">&nbsp;&nbsp;Aide&nbsp;En&nbsp;Ligne&nbsp;&nbsp;</A></TD>
<TD CLASS="unsel"><A HREF="/jobs/">&nbsp;&nbsp;T&acirc;ches&nbsp;&nbsp;</A></TD>
<TD CLASS="unsel"><A HREF="/printers/">&nbsp;&nbsp;Imprimantes&nbsp;&nbsp;</A></TD>
<TD CLASS="unsel" WIDTH="100%"><FORM ACTION="/help/" METHOD="GET"><INPUT
TYPE="SEARCH" NAME="QUERY" SIZE="20" PLACEHOLDER="Search Help"
AUTOSAVE="org.cups.help" RESULTS="20"></FORM></TD>
<TD><IMG SRC="/images/right.gif" WIDTH="4" HEIGHT="36" ALT=""></TD>
</TR>
</TABLE>

<TABLE CLASS="indent" SUMMARY="">
<TR><TD STYLE="padding-right: 20px;">

<H1>CUPS 1.7.2</H1>

<P>CUPS est le syst&egrave;me d'impression Open Source, bas&eacute; sur des standards, d&eacute;velopp&eacute; par
<A HREF="http://www.apple.com/">Apple Inc.</A> pour Mac OS<SUP>&reg;</SUP> X et
les autres OS UNIX<SUP>&reg;</SUP>-like.</P>

</TD>
<TD><A HREF="http://www.cups.org/"><IMG SRC="images/cups-icon.png" WIDTH="128"
HEIGHT="128" ALT="CUPS"></A></TD>
</TR>
</TABLE>

<TABLE CLASS="indent" SUMMARY="">
<TR><TD VALIGN="top" STYLE="border-right: dotted thin #cccccc; padding-right: 20px;">

<H2>CUPS pour les utilisateurs</H2>

<P><A HREF="help/overview.html">Pr&eacute;sentation de CUPS</A></P>

<P><A HREF="help/options.html">Impression en ligne de commande et options</A></P>

<P><A HREF="help/whatsnew.html">Quoi de neuf dans CUPS 1.6</A></P>

<P><A HREF="http://www.cups.org/newsgroups.php?gcups.general">Forum utilisateur</A></P>

</TD><TD VALIGN="top" STYLE="border-right: dotted thin #cccccc; padding-left: 20px; padding-right: 20px;">

<H2>CUPS pour les administrateurs</H2>

<P><A HREF="admin">Ajout d'imprimantes et de classes</A></P>

<P><A HREF="help/policies.html">G&eacute;rer les politiques</A></P>

<P><A HREF="help/accounting.html">Printer Accounting Basics</A></P>

<P><A HREF="help/security.html">S&eacute;curit&eacute; du serveur</A></P>

<P><A HREF="help/kerberos.html">Utiliser l'authentification Kerberos</A></P>

<P><A HREF="help/network.html">Utiliser des imprimantes r&eacute;seaux</A></P>

<P><A HREF="help/ref-cupsd-conf.html">R&eacute;f&eacute;rences sur cupsd.conf</A></P>

<P><A HREF="http://www.cups.org/ppd.php">Trouver des pilotes d'imprimantes</A></P>

</TD><TD VALIGN="top" STYLE="padding-left: 20px;">

<H2>CUPS pour les d&eacute;veloppeurs</H2>

<P><A HREF="help/api-overview.html">Introduction &agrave; la programmation CUPS</A></P>

<P><A HREF="help/api-cups.html">L'API CUPS</A></P>

<P><A HREF="help/api-filter.html">Programmation de filtres et de backends</A></P>

<P><A HREF="help/api-httpipp.html">Les API HTTP et IPP</A></P>

<P><A HREF="help/api-ppd.html">L'API PPD</A></P>

<P><A HREF="help/api-raster.html">L'API Raster</A></P>

<P><A HREF="help/ref-ppdcfile.html">PPD Compiler Driver Information File Reference</A></P>

<P><A HREF="http://www.cups.org/newsgroups.php?gcups.development">Forum d&eacute;veloppeurs</A></P>

</TD></TR>
</TABLE>

</TD></TR>
<TR><TD>&nbsp;</TD></TR>
<TR><TD CLASS="trailer">CUPS et le logo CUPS sont des marques d&eacute;pos&eacute;es de
<A HREF="http://www.apple.com">Apple Inc.</A> CUPS est sous copyright 2007-2014 Apple
Inc. Tous droits r&eacute;serv&eacute;s.</TD></TR>
</TABLE>
</BODY>
</HTML>
```

So. I've opened everything in cupsd.conf to be reachable from my LAN (Port 631 and Allow all everywhere)
```
#
#
# Sample configuration file for the CUPS scheduler.  See "man cupsd.conf" for a
# complete description of this file.
#

# Log general information in error_log - change "warn" to "debug"
# for troubleshooting...
LogLevel warn

# Deactivate CUPS' internal logrotating, as we provide a better one, especially
# LogLevel debug2 gets usable now
MaxLogSize 0

# Only listen for connections from the local machine.
# Listen localhost:631
Port 631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing On
BrowseLocalProtocols dnssd

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Web interface setting...
WebInterface Yes

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow all
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow all
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
  Allow all
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default

  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    Order deny,allow
  </Limit>

  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

# Set the authenticated printer/job policies...
<Policy authenticated>
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default

  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    AuthType Default
    Order deny,allow
  </Limit>

  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

#
#

```

But, now way to reach the web interface from another machine on the LAN.

Could someone explain me what's wrong ?

Thx

Diego

---

### Post by NarsilAnduril on 2014-09-30
Bump : no ? really nobody ?

---

### Post by ian-weisser on 2014-09-30
I don't know why it doesn't work for you.
It works just fine for me in 14.04.

Back to basics:
Does the cups server have the correct IP address?
Is cups is really running?
Can you access localhost:631 on that machine to verify that the webserver is running?
Is port 631 blocked by a firewall on either machine?

---

### Post by NarsilAnduril on 2014-10-01
> **ian-weisser said:**
> I don't know why it doesn't work for you.
It works just fine for me in 14.04.

Back to basics:
Does the cups server have the correct IP address?
Is cups is really running?
Can you access localhost:631 on that machine to verify that the webserver is running?
Is port 631 blocked by a firewall on either machine?

Yes, the cups server has the correct IP, webmin on the same machine is answering on port 10000.

sudo service cups restart says [ok].

curl localhost:631 returns the html code of the cups web interface (as shown in my first post)

I don't know how to check if  port 631is blocked somewhere ...

Thx

Diego

---

### Post by nerdtron on 2014-10-01
From another machine open a command prompt and try:
```
telnet 192.x.x.x 631
```
 Be sure to put the IP address of the CUPs server. If it is successful, then the port is open on the server.

---

### Post by NarsilAnduril on 2014-10-01
diego@cerise:~$ telnet 172.26.155.13 631
Trying 172.26.155.13...
telnet: Unable to connect to remote host: Connection refused

But I'll have to check if telnet is running...  I think (and hope) it's not !

---

### Post by nerdtron on 2014-10-01
> **NarsilAnduril said:**
> diego@cerise:~$ telnet 172.26.155.13 631
Trying 172.26.155.13...
telnet: Unable to connect to remote host: Connection refused

But I'll have to check if telnet is running...  I think (and hope) it's not !

No, that command will check port 631 on the server and not the telnet service.
On the server do you have firewall? Please post the output of the following:
```
sudo netstat -tulpn
sudo ufw status
sudo iptables --list
```

---

### Post by NarsilAnduril on 2014-10-01
```
diego@kiwi:~$ sudo netstat -tulpn
[sudo] password for diego: 
Connexions Internet actives (seulement serveurs)
Proto Recv-Q Send-Q Adresse locale          Adresse distante        Etat       PID/Program name
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      823/smbd        
tcp        0      0 0.0.0.0:55022           0.0.0.0:*               LISTEN      21963/rtorrent  
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      520/rpcbind     
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      1574/perl       
tcp        0      0 0.0.0.0:45904           0.0.0.0:*               LISTEN      592/rpc.statd   
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      997/sshd        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5725/cupsd      
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      823/smbd        
tcp        0      0 127.0.0.1:5000          0.0.0.0:*               LISTEN      21963/rtorrent  
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      1148/mysqld     
tcp6       0      0 :::139                  :::*                    LISTEN      823/smbd        
tcp6       0      0 :::111                  :::*                    LISTEN      520/rpcbind     
tcp6       0      0 :::80                   :::*                    LISTEN      5445/apache2    
tcp6       0      0 :::22                   :::*                    LISTEN      997/sshd        
tcp6       0      0 ::1:631                 :::*                    LISTEN      5725/cupsd      
tcp6       0      0 :::445                  :::*                    LISTEN      823/smbd        
tcp6       0      0 :::60162                :::*                    LISTEN      592/rpc.statd   
udp        0      0 0.0.0.0:43494           0.0.0.0:*                           5409/avahi-daemon: 
udp        0      0 0.0.0.0:617             0.0.0.0:*                           520/rpcbind     
udp        0      0 0.0.0.0:631             0.0.0.0:*                           5684/cups-browsed
udp        0      0 127.0.0.1:768           0.0.0.0:*                           592/rpc.statd   
udp        0      0 0.0.0.0:56386           0.0.0.0:*                           592/rpc.statd   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           5409/avahi-daemon: 
udp        0      0 0.0.0.0:10000           0.0.0.0:*                           1574/perl       
udp        0      0 0.0.0.0:111             0.0.0.0:*                           520/rpcbind     
udp        0      0 172.26.155.13:123       0.0.0.0:*                           1700/ntpd       
udp        0      0 127.0.0.1:123           0.0.0.0:*                           1700/ntpd       
udp        0      0 0.0.0.0:123             0.0.0.0:*                           1700/ntpd       
udp        0      0 172.26.155.63:137       0.0.0.0:*                           1140/nmbd       
udp        0      0 172.26.155.13:137       0.0.0.0:*                           1140/nmbd       
udp        0      0 0.0.0.0:137             0.0.0.0:*                           1140/nmbd       
udp        0      0 172.26.155.63:138       0.0.0.0:*                           1140/nmbd       
udp        0      0 172.26.155.13:138       0.0.0.0:*                           1140/nmbd       
udp        0      0 0.0.0.0:138             0.0.0.0:*                           1140/nmbd       
udp6       0      0 :::617                  :::*                                520/rpcbind     
udp6       0      0 :::42167                :::*                                592/rpc.statd   
udp6       0      0 :::5353                 :::*                                5409/avahi-daemon: 
udp6       0      0 :::40807                :::*                                5409/avahi-daemon: 
udp6       0      0 :::111                  :::*                                520/rpcbind     
udp6       0      0 fe80::222:15ff:fe0f:123 :::*                                1700/ntpd       
udp6       0      0 ::1:123                 :::*                                1700/ntpd       
udp6       0      0 :::123                  :::*                                1700/ntpd       

```

```
diego@kiwi:~$ sudo ufw status
État*: inactif
```

```
diego@kiwi:~$ sudo iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    
```

---

