---
title: "Cannot access my self-hosted website"
date: 2022-01-27
forum: Server Platforms
---

### Post by digitalis492 on 2022-01-27
**Really need some help here PLEASE. **[B]==============================
**Fi**rst off - I am NOT an experienced Linus person but I can follow clear instructions.
[/B]
I have a dedicated home/office PC running Ubuntu 20.04 + LAMP + Joomla.

 Have not, as yes, installed Letsencrypt SSL - but will do so asap.

I have a registered domain with Godaddy.com - Let's call it "myweb.com".

 
I have a static public IP address - used in Godaddy's DNS A & CNAME records - IP address provided by my ISP.

 
Ubuntu network settings are IPv4 Auto DHCP & auto Routes. No IPv6.

 --------------------------------------------------------
/etc/hostname = myweb

 ---------------------------------------------------------
/etc/hosts = 
192.168.0.137   myweb.com myweb 
127.0.0.1         localhost localhost.localdomain

 ------------------------------------------------------------
/etc/apache2/sites-enabled = 
VirtualHost *:80> 
ServerName myweb.com 
ServerAlias [www.myweb.com]("http://www.myweb.com") 
ServerAdmin [email]admin@myweb.com[/email] 
DocumentRoot /var/www/html/joomla

 ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined

<Directory /var/www/html/joomla>
     Options FollowSymlinks
     Allowoverride all
     Require all granted
---------------------------------
      [h=1]ISSUE:[/h] I can only access my Joomla website using my local IP address or localhost. 
Using a computer external to my network to access my site gives me a timeout or connection refused message.

 
I have searched the net for likely causes for several weeks but have not resolved this issue.

 
PLEASE, I would really appreciate some advice from this very learned community.

 Am happy to provide more info as needed - naturally!

Thank you.
Andreas.

---

### Post by raja.genupula on 2022-01-27
Are you able to ping your static IP ?

---

### Post by SeijiSensei on 2022-01-27
If the server is behind a router, outside access is being blocked. You need to look into "port forwarding" so that ports 80/443 on the router and forwarded back to the corresponding ports on the server. You'll need to read the documentation for your router to learn how to do this.

Another option to consider is spending $5/month and renting a virtual server at linode.com. Then your website would be publicly visible, but this option probably requires more system administration skills than you currently have.  See if you can configure port forwarding.

---

### Post by TheFu on 2022-01-27
Work through each device between the server and the internet.  Ensure the DNS and firewall settings allow the access required.

BTW, the post above has this error:
```
VirtualHost *:80> 
```
it should be 
```
[COLOR="#FF0000"]<[/COLOR]VirtualHost *:80>
```

LE certs needs both 80/tcp and 443/tcp to be open and not just open, but open to the entire world.

Also, the server running the website and LE termination needs to have a static LAN address with 1-to-1 port forwards for 80 and 443/tcp ports from the static public IP. That is configured in the router.

For systems running services that are available over the internet, it is important those are on different LAN segments with firewalling between other LAN servers and desktops and other devices.  The goal is to limit damage to the other systems on the LAN when a cracker gets into apache.

---

### Post by digitalis492 on 2022-01-27
These are the ports forwarded in my Router:

PORT   PROTOCOL    EXTERNAL HOST    INTERNAL HOST  EXTERNAL PORT   INTERNAL PORT
--------   ----------------     -------------------------    ------------------------  -------------------------   ------------------------
80          tcp/udp       "my  static ip addr"          192.168.0.137           80                                80
SSH       tcp/udp                same                            same                   22                                22
DNS       tcp/udp                same                            same                   53                                53
SMTP     tcp/udp                same                            same                   25                                25
Other      tcp/udp                same                            same                  443                              443

Anything wrong with these please ?

---

### Post by TheFu on 2022-01-27
> **digitalis492 said:**
> These are the ports forwarded in my Router:

```
PORT   PROTOCOL    EXTERNAL HOST    INTERNAL HOST  EXTERNAL PORT   INTERNAL PORT
--------   ----------------     -------------------------    ------------------------  -------------------------   ------------------------
80          tcp/udp       "my  static ip addr"          192.168.0.137           80                                80
SSH       tcp/udp                same                            same                   22                                22
DNS       tcp/udp                same                            same                   53                                53
SMTP     tcp/udp                same                            same                   25                                25
Other      tcp/udp                same                            same                  443                              443
```

Anything wrong with these please ?

You shouldn't forward DNS or ssh or smtp unless those services are actually being provided by your servers. Running a secure DNS is non-trivial, so if you are really new, best to pay the $40/yr for someone else to do your public DNS.  
Ssh really should never be put on 22/tcp on the WAN side. Make it some very high, non-standard port and protect it from brute force attacks.  I use ports over 60000/tcp for ssh connections and only allow key-based connections from the internet. Anyone using ssh will be more technical, so setting up a non-standard port in their ~/.ssh/config file should be trivial for them on any client used. You can use port-translation for ssh, so WAN is on 61022 and internal it is still on port 22.  Makes it easy to connect on the LAN or WAN by using a different host alias in the ~/.ssh/config file.

I've been running SMTP for enterprises and small companies since the mid-1990s. I don't allow external access to the real email server, just to an extremely hardened smtp gateway for all in and out email traffic.  Over 90% gets dropped for failing spam processing.  End-user access to email is not allowed without using a full VPN. The CEO of one client wasn't happy about that, so I showed her the login attempts to her account.  That ended that.  She never complained about using a VPN again.  We could always move the IMAPS and SMTP to non-standard ports, but that would complicate things for the non-technical people way too much.

Can you validate that all the ports are actually open by looking at both the router logs and at the application logs. Log files are your friend.  Apache logs show all connections and requests. If there aren't any entries from the WAN side, then something is in the way.

Lastly, see how the code tags make things line up and easier to read?  If they are in a proper column in a terminal, a copy/paste here, then wrapping in 'code -tags' for the forum (adv-reply # option). Then it will all line up perfect.

---

### Post by digitalis492 on 2022-01-27
Thank you THE-FU.
Greatly appreciate you help. Will check out your suggestions.

Andreas.

---

### Post by mIk3_08 on 2022-02-14
> **digitalis492 said:**
> **Really need some help here PLEASE. **[B]==============================
**Fi**rst off - I am NOT an experienced Linus person but I can follow clear instructions.
[/B]
I have a dedicated home/office PC running Ubuntu 20.04 + LAMP + Joomla.

 Have not, as yes, installed Letsencrypt SSL - but will do so asap.

I have a registered domain with Godaddy.com - Let's call it "myweb.com".

 
I have a static public IP address - used in Godaddy's DNS A & CNAME records - IP address provided by my ISP.

 
Ubuntu network settings are IPv4 Auto DHCP & auto Routes. No IPv6.

 --------------------------------------------------------
/etc/hostname = myweb

 ---------------------------------------------------------
/etc/hosts = 
192.168.0.137   myweb.com myweb 
127.0.0.1         localhost localhost.localdomain

 ------------------------------------------------------------
/etc/apache2/sites-enabled = 
VirtualHost *:80> 
ServerName myweb.com 
ServerAlias [www.myweb.com]("http://www.myweb.com") 
ServerAdmin [EMAIL="admin@myweb.com"]admin@myweb.com[/EMAIL] 
DocumentRoot /var/www/html/joomla

 ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined

<Directory /var/www/html/joomla>
     Options FollowSymlinks
     Allowoverride all
     Require all granted
---------------------------------
      **ISSUE:**

 I can only access my Joomla website using my local IP address or localhost. 
Using a computer external to my network to access my site gives me a timeout or connection refused message.

 
I have searched the net for likely causes for several weeks but have not resolved this issue.

 
PLEASE, I would really appreciate some advice from this very learned community.

 Am happy to provide more info as needed - naturally!

Thank you.
Andreas.

I agree with SeijiSensei and TheFu. Its all in the router configuration. The port forwarding configuration. 
This is usually the configuration of your router 21 - FTP 80 - HTTP 5900 - VNC TCP/UDP - 27015
TCP - 5800 - 5900 - ip.local.0.0 TCP/UDP - 21 - 21 - ip.local.0.0 HTTP - TCP - 80 - 80 - ip.local.0.0 TCP/UDP - 27015 - 27015 - ip.local.0.0
So good Luck and cheers.

---

