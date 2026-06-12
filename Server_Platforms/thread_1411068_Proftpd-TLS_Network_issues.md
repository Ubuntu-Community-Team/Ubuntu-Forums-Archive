---
title: "Proftpd-TLS Network issues"
date: 2010-02-19
forum: Server Platforms
---

### Post by jeffshowalter7 on 2010-02-19
Taking first setups on setting up basic server functions.
Hope someone points out my stupidity. 

I setup Proftpd the other day with normal ftp and connected internally and external(currently just a test server so i didn't care about security) with no problems. Ftp is forwarded to server from the firewall etc and all worked fine.

I have since setup TLS on the server and verified that it worked internally. When I went out of my network and tried to connect using filezilla - FTPES I get the below log. This is right at the time when in filezilla you would normally get the popup to accept the cert.
###############################################
[HTML]Status:	Connecting to 70.16.166.139:21...
Status:	Connection established, waiting for welcome message...
Response:	220 ProFTPD 1.3.2 Server (Debian) [::ffff:192.168.3.10]
Command:	AUTH TLS
Response:	234 AUTH TLS successful
Status:	Initializing TLS...
Error:	Connection timed out
Error:	Could not connect to server[/HTML]
################################################

I checked in my /var/log/proftpd/proftpd.log is
::ffff(my ip) ftp session opened
::ffff(my ip) ftp session closed

in my /var/log/proftpd/tls.log 
Feb 19 12:38:44 mod_tls/2.2.1[3171]: unable to accept TLS connection: received EOF that violates protocol
Feb 19 12:38:44 mod_tls/2.2.1[3171]: TLS/TLS-C negotiation failed on control channel
################################################

I looked up those errors and it hasn't helped much.
Note sure if this should be in there, but I put it in while trying to figure this out. I put in my proftpd.conf file
PassivePorts 49152 49152

It looks like it is a firewall issue of some kind. I don't have anything blocked on outbound traffic and I have ftp(21) forwarded to the server and also i have setup forwarding for 49152 as well. 
(not sure I need that, as I tested that internally and found that it just chose a random socket anyway.)


So am I missing something with my firewall. I don't think it is the config as it works internally.(Can post if needed)
I had also tried this with vsftpd and gave up on it as it had the same issue. thought it was something crazy going on.

My firewall is untangle 7
running server 9.10

Anyway any help or shove in the right direction is helpful.
thanks,
jeff

---

### Post by jeffshowalter7 on 2010-02-20
Any thoughts on this? like I have stated, I have ftp forwarded on my firewall, and that should be all that is needed correct?

thanks, for any help

---

### Post by jeffshowalter7 on 2010-02-23
Well, after not getting any responses from this, I just scraped it and went with sftp and called it a day. Chrooted the users and it works.

---

### Post by WebWatch on 2011-01-12
Found this at [http://www.proftpd.org/docs/howto/TLS.html](http://www.proftpd.org/docs/howto/TLS.html)

--

Question: Using mod_tls, FTP sessions through my firewall now no longer work. What's going on?
Answer: The short answer is that FTPS and firewalls (and devices performing NAT) do not interact well. The control connection happens on a well-known port, and has no issues; it is the data connection that poses problems for FTP-aware firewalls. In a non-FTPS session, the firewall can inspect the FTP server's responses on the control connection to a client's PASV or PORT command, and thus know which on which ports/addresses the data connection will be established. In an FTPS session, though, those control connection messages are encrypted (that is the point of using FTPS, right?), and so the FTP-aware firewall cannot peek. Hence, it cannot know which on which ports the data connection will be established. For firewalls that are configured to always allow a certain range of ports (such as might be configured using the PassivePorts directive), FTPS should function without issue.

Unfortunately, this is a rather intractable--and known--issue. Earlier versions of the Draft defining FTPS used to allow something known as "implicit" FTPS, by which a client could contact a well-known port (akin to port 443 for HTTPS; FTPS used port 990) and the server, simply because the client contacted that certain port, would automatically encrypt the session. This approach has several drawbacks (the reason why it was removed from later versions of the Draft), but it did allow for simple TCP proxying.

To attempt to deal with the above issue, the RFC for FTP over SSL/TLS suggests using the CCC FTP command (Clear Command Channel). The CCC command makes an encrypted control channel revert back to an unencrypted channel. This helps to solve data connection problems in situations where network equipment (such as firewalls, routers, NAT) peek at the control channel in order to open ports. By sending the CCC command and unecrypting the control channel, the network equipment can once again peek at the commands (i.e. PORT and EPRT) in the control channel. Since the CCC command must come after the client has logged in, the USER and PASS commands on the control channel will still be protected by SSL/TLS.

Note that in order to configure the mod_tls module to allow use of the CCC command by clients, the following must appear in your proftpd.conf:

  TLSRequired auth+data

See the TLSRequired description for more details.

---

