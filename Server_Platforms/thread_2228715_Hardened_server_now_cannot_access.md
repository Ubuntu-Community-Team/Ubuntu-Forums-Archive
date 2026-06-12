---
title: "Hardened server now cannot access"
date: 2014-06-09
forum: Server Platforms
---

### Post by adam-kimber on 2014-06-09
I wanted to put my ubuntu server on the internet and wanted to make sure it was safe, so I thought I would follow this hardening guide, [http://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics](http://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics). All was fine until I rebooted. Now I cannot access my Samba shares or SSH into the machine. 

I have used Ubuntu desktop for a while but am a complete noob to servers. I have a 14.04 running with my data on a software raid. I have obviously followed something on that guide wrong but for the life of me I have no idea. Any pointers? The box has completely disappeared, which I think is probably part of the hardening! 

----

The server is on a local network behind a NAT that I was going to forward ports to the server. I have not undertaken item 6 (NAT does DHCP, server has specific internal address reserved), item 9 (couldn't find the file in question), items 10 and 11 (they are separate guides), only part of 12 (as the denyhosts package couldn't be found) and not done 13-18. I have also not done 3 as I was not sure how to generate the keys on a windows machine (I will post seperately about that if I cannot find any info). 

----

Thank you for your time!

---

### Post by TheFu on 2014-06-09
Whoa!  You put a server running Samba on the internet?

**fail2ban** can be a replacement for denyhosts.

I did NOT click on that unknown link to read anything.  Ubuntu has a few security guides. Links are in my signature.

---

### Post by adam-kimber on 2014-06-09
> **TheFu said:**
> Whoa!  You put a server running Samba on the internet?

Is this a bad thing? I need Samba for sharing files within my network to Windows machines. I then would like to access these files by FTP from remote locations. Are you suggesting this is not a wise setup?

---

### Post by TheFu on 2014-06-09
> **adam-kimber said:**
> Is this a bad thing? I need Samba for sharing files within my network to Windows machines. I then would like to access these files by FTP from remote locations. Are you suggesting this is not a wise setup?

Yes, that is my suggestion.

[FTP is also a bad idea.]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp")  Use sftp instead.  There are very few reasons to still run an FTP server these days - most of them are bad, IMHO.

The basis of remote access to your network should be either a strong VPN or ssh.
With ssh, you get scp, sftp for free. They run on the same port.
Secure ssh with key-only logins. NEVER passwords, and use fail2ban to block repeated hack attempts with dynamic firewall control.

Only 1 port needs to be opened on the internet this way - the port for ssh.  That reduces the attack vectors, which is basic security 101.

Within your network, running samba is fine provided the availability over the internet is highly restricted and only encrypted channels are available - IMHO.  Running a web server or FTP server or IM server or email/DNS servers on the same hardware opens the possible attacks to an unacceptable risk level. These services are hacked all the time, best not to risk important data on that same hardware.  OTOH, lots of people don't get hacked doing this ... I've been hacked ... back in 2002. My attitude has changed completely since then.

---

### Post by adam-kimber on 2014-06-09
Thank you for your advice. I will swap to SFTP. How would I go about making sure the samba is restricted. Just don't port forward this to the internet? I also like the idea of only using one port that is exposed.

---

### Post by TheFu on 2014-06-09
Securing ssh/scp/sftp:  [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

Restricting which IPs can access Samba-shares (v3 samba, unknown for v4 samba). Put this in the relevent stanzas inside the /etc/samba/smb.conf file:
```
[homes]
  hosts allow = 127.0.0.1 172.22.22.0/24 192.168.1.27
  hosts deny = 0.0.0.0/0
 .
 .
 .

``` If you use a GUI for setting up samba - I haven't a clue what should be done. If the GUIs create an smb.conf file, adding those lines should work, I'd guess.

Oh - and if you need a remote desktop, not just ssh when you are traveling around the world, running a FreeNX server on the machine for 13.10 and earlier Ubuntu versions is an option. I don't have personal experience with 14.04, but understand that FreeNX is dead there and something like x2go is recommended now.  The rdp and VNC solutions are much slower, and require VPN or ssh-tunnel be manually configured unless you don't care at all about security. In my book, using NX is just easier, since the remote desktop protocol is highly efficient AND goes over ssh already. It uses the same ssh-port already used, so nothing more needs to be configured on the router/firewall.

Besides the links in my signature above, there are lots and lots of security-related discussions here worth reviewing.  In short
* limit public facing services
* always use encryption
* avoid using passwords, use key-based authentication
* Each public facing service needs a dedicated machine, so that everything else can be locked down. Be wary of all-in-one distros that provide email, web server, backup server, VoIP, DNS, Samba, NFS, .... kitchen sink and claim to be "secure" from the start.

Oh ... and almost no router firmware shipped with a router is secure. Most have been found to have back doors, so the only way to trust them is to load after-market firmware like tomato, dd-wrt, openwrt, or pfsense.  These after-market solutions will also have issues, but at least a back-door isn't one of them. ;)

---

### Post by CharlesA on 2014-06-09
I don't think I can add much that TheFu hasn't already mentioned, but I have gotten in the habit of running one or two services per box if they are public facing. My mail server runs postfix and dovecot, my web server runs nginx and varnish, and my znc server runs znc and mumble (cuz I'm insane).

This limits attack surface. If this machine is a local machine (which is seems like it is due to Samba), you should only allow sftp access via keys instead of password in the even you actually need remote access to files.

Also: I use [CSF]("http://www.configserver.com/cp/csf.html") on my servers for integrity checks and blacklisting among other things, and I have found it quite handy. I'd considering it as a drop-in replacement for denyhosts or fail2ban, but every environment is different.

---

