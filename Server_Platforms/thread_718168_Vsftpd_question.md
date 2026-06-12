---
title: "Vsftpd question"
date: 2008-03-07
forum: Server Platforms
---

### Post by blx_286 on 2008-03-07
I need some help with a vsftpd problem. I have vsftpd setup using ssl and I have moved it from my local network to the DMZ. I can connect to it from my network to the DMZ without a problem, but when I connect from the Internet I get the following error:

```
Status:	Connecting to x.x.x.x:990 ...
Status:	Connected with x.x.x.x:990, negotiating SSL connection...
Response:	220 (vsFTPd 2.0.4)
Command:	AUTH SSL
Response:	234 Proceed with negotiation.
Status:	SSL connection established. Waiting for welcome message...
Command:	PBSZ 0
Response:	200 PBSZ set to 0.
Command:	PROT P
Response:	200 PROT now Private.
Command:	USER me
Response:	331 Please specify the password.
Command:	PASS *********
Response:	230 Login successful.
Command:	FEAT
Response:	211-Features:
Response:	 AUTH SSL
Response:	 AUTH TLS
Response:	 EPRT
Response:	 EPSV
Response:	 MDTM
Response:	 PASV
Response:	 PBSZ
Response:	 PROT
Response:	 REST STREAM
Response:	 SIZE
Response:	 TVFS
Response:	211 End
Command:	SYST
Response:	215 UNIX Type: L8
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/"
Command:	PASV
Response:	227 Entering Passive Mode (192,168,0,39,47,39)
Command:	TYPE A
Response:	200 Switching to ASCII mode.
Command:	LIST
Error:	Transfer channel can't be opened. Reason: A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond.
Error:	Could not retrieve directory listing
Command:	PWD
```

If I add a passive address to my config file it works from the Internet, but then I get the following error from my network to the DMZ.

```
Status:	Connecting to x.x.x.x:990 ...
Status:	Connected with x.x.x.x:990, negotiating SSL connection...
Response:	220 (vsFTPd 2.0.4)
Command:	AUTH SSL
Response:	234 Proceed with negotiation.
Status:	SSL connection established. Waiting for welcome message...
Command:	PBSZ 0
Response:	200 PBSZ set to 0.
Command:	PROT P
Response:	200 PROT now Private.
Command:	USER me
Response:	331 Please specify the password.
Command:	PASS *********
Response:	230 Login successful.
Command:	FEAT
Response:	211-Features:
Response:	 AUTH SSL
Response:	 AUTH TLS
Response:	 EPRT
Response:	 EPSV
Response:	 MDTM
Response:	 PASV
Response:	 PBSZ
Response:	 PROT
Response:	 REST STREAM
Response:	 SIZE
Response:	 TVFS
Response:	211 End
Command:	SYST
Response:	215 UNIX Type: L8
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/"
Command:	PORT 10,0,0,59,17,108
Response:	200 PORT command successful. Consider using PASV.
Command:	TYPE A
Response:	200 Switching to ASCII mode.
Command:	LIST
Response:	150 Here comes the directory listing.
Error:	Unknown error in SSL layer
Error:	Disconnected from server
Error:	Could not retrieve directory listing
Error:	Timeout detected!
```

Is there a config setting I can make to allow me to connect from inside or outside of the company? Here is my config:

```
# ----------------------------------------------------------------------
# base configuration
# ----------------------------------------------------------------------
anon_world_readable_only=NO
anonymous_enable=NO
# chroot will jail all users, with no exceptions
chroot_local_user=YES
chroot_list_enable=NO
# all users are virtual (guest) users there are no system user logins
guest_enable=YES
guest_username=ftp
hide_ids=YES
listen=YES
# commented out the next line from the tutorial
#listen_address=192.168.0.1
local_enable=YES
max_clients=20
max_per_ip=2
nopriv_user=ftp
pam_service_name=ftp
pasv_address=x.x.x.x
pasv_min_port=12000
pasv_max_port=12100
session_support=NO
use_localtime=YES
user_config_dir=/etc/vsftpd/vusers
#userlist commented out from original tutorial
#userlist_enable=NO
#userlist_file=/etc/vsftpd/denied_users
xferlog_enable=YES
#ftpd_banner=Welcome to the FTP service

# ----------------------------------------------------------------------
# ftp settings
# ----------------------------------------------------------------------
anon_umask=0027
async_abor_enable=YES
connect_from_port_20=YES
dirlist_enable=NO
download_enable=NO

# ----------------------------------------------------------------------
# ssl settings
# ----------------------------------------------------------------------
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
listen_port=990
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

```

Thanks in advance,
Tim

---

### Post by netlogic on 2008-03-07
You need your passive port 12000 through 12100 open on your router or firewall.

---

### Post by blx_286 on 2008-03-08
Thanks for the quick reply. I do have those passive ports added to the firewall, but I still can't get it work from inside and outside the company correctly. I should have used some IP addresses in my previous post to better explain.

I have assigned a public IP and it NAT's to a local IP in the DMZ. If I have the passive address set to my public IP I can connect to it from the Internet. But I cannot connect to it from inside the company using the public or local IP.

If I comment out the passive public address, I can connect to if from inside the company using the local IP, but I cannot connect to it from the Internet using the public IP. I hope that makes more sense.

Thanks,
Tim

---

### Post by netlogic on 2008-03-08
By quickly glancing at your config, there is nothing wrong with it. Also, if it worked from the lan, it should also work from outside. It seems like you are getting stuck at the data port. 

[B][I]Error:	Transfer channel can't be opened. Reason: A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond.
Error:	Could not retrieve directory listing
[/I][/B]

You are having a routing or firewall issue. Vsftpd works very well in a NAT environment. Long as passive ports are OPEN both ways, it wouldn't matter it is NAT. It has be allowed in and out. If it is set to only out, it wouldnt' work. Also, what client app are you using to use FTP over TLS?

> I have assigned a public IP and it NAT's to a local IP in the DMZ. If I have the passive address set to my public IP I can connect to it from the Internet. But I cannot connect to it from inside the company using the public or local IP.

It is a routing issue. If you can get to the machine from the outside, but you can't from inside, something is blocking it. I know it sounds simple. Most of the time, it is a simple problem. You can always run nmap to see if you can see the port from your workstation.

---

### Post by blx_286 on 2008-03-08
> **netlogic said:**
> Also, what client app are you using to use FTP over TLS?

We are a Windows shop and I use Filezilla and it is set to FTP over SSL explicit encryption.

> It is a routing issue. If you can get to the machine from the outside, but you can't from inside, something is blocking it. I know it sounds simple. Most of the time, it is a simple problem.

Yeah, for some reason with this hardware firewall any public IP's I have that NAT back in don't work from the inside. It's like they won't go out and route back in. But they work from the outside coming in.

What bugs me is that this server only has SSH and Vsftpd installed. From outside the company I can SSH into the public IP and from inside the company I can SSH into the private IP. I can only do the same with Vsftpd if I toggle the pasv_address off and on.

> You can always run nmap to see if you can see the port from your workstation.

I haven't used nmap before, but I was thinking about making my workstation dual boot and I will have to look into that.

Thanks,
Tim

---

### Post by Mr. C. on 2008-03-09
> **blx_286 said:**
> Yeah, for some reason with this hardware firewall any public IP's I have that NAT back in don't work from the inside. It's like they won't go out and route back in. But they work from the outside coming in.

What bugs me is that this server only has SSH and Vsftpd installed. From outside the company I can SSH into the public IP and from inside the company I can SSH into the private IP. I can only do the same with Vsftpd if I toggle the pasv_address off and on.
Thanks,
Tim

I'm following up from your other thread here also, just for completeness.  Your router may not support NAT loopback, which means you cannot access your LAN services on the LAN via a WAN IP address.  Use LAN addresses when on the LAN, and WAN when on the WAN.  Is there are reason you feel the need to use WAN addresses from on the LAN ?

---

### Post by blx_286 on 2008-03-09
> **Mr. C. said:**
>  Your router may not support NAT loopback, which means you cannot access your LAN services on the LAN via a WAN IP address. 

I inherited this router and I am still reading up on it, but that makes sense that it doesn't support NAT loopback.

>  Use LAN addresses when on the LAN, and WAN when on the WAN.

That was how I found my problem. Everything worked well when I was on the LAN connecting to the LAN IP. I then came home to test the WAN side and I could not connect. I then added that pasv_address (with the WAN IP) to the conf file and was able to connect from home to the WAN side.

From home, I then connected back into my office workstation, with a remote agent, and couldn't hit the LAN IP from the LAN side. I then commented out the pasv_address and I was able to hit the LAN IP from the LAN side again.

I think I read somewhere that vsftpd will send the server address back to the client in passive mode. But when using NAT it sends the LAN IP if you don't use the pasv_address option with a WAN IP. Does that sound right?

Or am I overlooking something on the router on the NAT side and I should be able to comment out the pasv_address and not use it at all?

Thanks,
Tim

---

### Post by Mr. C. on 2008-03-09
The firewall in your router needs to maintain a connection table, in order that it may allow *established* external client's to communicate with your LAN or DMZ servers. It does this by watching outbound initiated traffic, and sets up tables to allow the established client to connect.

For NAT'd or PAT'd port-fowarding to a LAN or DMZ server, the router also maintains a table of connections to forward.  The trouble is with services such as FTP that rely on the client making one connection (cmd), and the server making the other (data).  PASV changes this, by having the server send the IP/PORT combination where the client should make the data connection.  However... to the firewall, this looks like an unsolicited inbound attempt, so it blocks that connection.

(btw. Here are a few pictures that illustrate FTP if you're interested:
[http://cis68c2.mikecappella.com/files/cis68c2/10-lecture-ftp.pdf](http://cis68c2.mikecappella.com/files/cis68c2/10-lecture-ftp.pdf) )

This dilemma must be handled and supported by the firewall/router appliance: it must peek inside the payload (violating network packet encapsulation and layering rules) of the IP datagram and watch for that all important PORT or PASV command so that it can setup its internal tables to allow the incoming data connection from the client.  Many home/commodity/cheapo routers do not handle this properly!  Some give you a port range that you can open for PASV opens, and then you can configure the server appropriately.  This further wrinkle is when using FTP via SSL - since the datagram is encrypted, the router cannot see the commands being passed, and thus cannot associate a new inbound FTP data connection with the client's existing FTP cmd connection.

So, your router/firewall must properly support FTP, PORT or PASV, properly for this to work.  If it does not, you'll need a new router.

---

### Post by netlogic on 2008-03-10
Also, modifying these settings if you are stuck with the current router

also, pull out the 
**listen_port=990**
990 is default. I never had a success of having the default port behind the router or firewall.
you already have a range for your data port.
if you are using an old firewall or router, place this line.
It might force the passive port compatibility. 
# Make sure PORT transfer connections originate from port 20 (ftp-data).
**connect_from_port_20=YES**

Also, try this. It is a security risk, but it might get you further.
Set to YES if you want to disable the PASV security check that ensures the data connection originates from the same IP address as the control connection. Only enable if you know what you are doing! 
**pasv_promiscuous=YES**
also, for security... you want to LOCK users to their /home/$user
# You may restrict ALL local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
**chroot_local_user=YES**
# (default follows) 
# put the users who are allowed to browse through other directories here in 
# this userlist.
**chroot_list_file=/etc/vsftpd.chroot_list**
==================================
If I think of something else, I will let you know. 
These days, the memory chips in my brain seem to be burnt from overclocking.
There are few other things we can do in the passive mode if these don't help.

---

