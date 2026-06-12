---
title: "VSFTPD Running on Custom Port - 425 Connection Refused - Remote Connections Only"
date: 2016-01-31
forum: Server Platforms
---

### Post by own3mall on 2016-01-31
Hi All,

I cannot get VSFTPD to work properly when using a custom port on Ubuntu 14.04.  I can connect to the FTP server running on a custom port from the local server itself, but remote connections using my properly port-forwarded IP address or via another computer on the same LAN will appear to work, but then the connection is refused by the server. 

Here is my configuration stored in /etc/vsftpd.conf

```

listen_port=10001
pasv_min_port=45000
pasv_max_port=45050
pasv_address={SERV_REAL_IP_ADDRESS}
pasv_addr_resolve=YES
pasv_enable=YES
log_ftp_protocol=YES
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
local_umask=0002
file_open_mode=0775
dirmessage_enable=YES
xferlog_enable=YES
nopriv_user=ftp
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
guest_enable=YES
guest_username=ftp
local_root=/var/www/vhosts/$USER
user_sub_token=$USER
virtual_use_local_privs=YES
user_config_dir=/etc/vsftpd_user_conf
local_max_rate=2000000 # bytes per sec, 2Mbytes per sec
max_clients=50 # to avoid DOS attack, if you have a huge server, increase this..
ftpd_banner=Welcome to vsFTPd Server, managed by Yo Mama

allow_writeable_chroot=YES
seccomp_sandbox=NO
anon_root=/var/public_ftp
anon_mkdir_write_enable=NO
anon_upload_enable=NO

```

 I enabled some additional logging, and here is what I'm getting.

> 
Sun Jan 31 19:18:46 2016 [pid 8190] [ftp] FTP response: Client "192.168.1.100", "230 Login successful."
Sun Jan 31 19:18:46 2016 [pid 8190] [ftp] FTP command: Client "192.168.1.100", "OPTS UTF8 ON"
Sun Jan 31 19:18:46 2016 [pid 8190] [ftp] FTP response: Client "192.168.1.100", "200 Always in UTF8 mode."
Sun Jan 31 19:18:46 2016 [pid 8190] [ftp] FTP command: Client "192.168.1.100", "PWD"
Sun Jan 31 19:18:46 2016 [pid 8190] [ftp] FTP response: Client "192.168.1.100", "257 "/""
Sun Jan 31 19:18:46 2016 [pid 8190] [ftp] FTP command: Client "192.168.1.100", "TYPE I"
Sun Jan 31 19:18:46 2016 [pid 8190] [ftp] FTP response: Client "192.168.1.100", "200 Switching to Binary mode."
Sun Jan 31 19:18:46 2016 [pid 8190] [ftp] FTP command: Client "192.168.1.100", "PASV"
Sun Jan 31 19:18:46 2016 [pid 8190] [ftp] FTP response: Client "192.168.1.100", "227 Entering Passive Mode (ip_removed,218,192)."
Sun Jan 31 19:18:46 2016 [pid 8190] [ftp] FTP command: Client "192.168.1.100", "LIST"
Sun Jan 31 19:18:57 2016 [pid 8142] [ftp] FTP response: Client "192.168.1.100", "425 Failed to establish connection."


Anyone know why this is happening?  I've seen several guides online for various Linux distributions that say that changing the port is easy.  However, once I change the port to anything other than 21, FTP will not work via a remote connection.  It's not a firewall issue, as I have ports 45000-45050 forwarded along with the listen port of 10001.  I've verified the ports are open, and the initial connection is made just fine by the client.  However, after trying to send any command, it will timeout with a connection refused error. 

To make sure I wasn't crazy, I tried the same thing on another server running Ubuntu 12.04.  I got the same result.  The client established the connection, but when sending any command, the connection eventually goes into a timeout state and the server throws a 425 error saying that it failed to establish the connection.  Yet, once I set the listen port back to 21, everything is fine again.

Has anyone ever been able to configure VSFTPD to use a custom port successfully?  If so, how?  I'd like to use a custom port for security purposes, but after trying this multiple times, it seems that it is not possible with VSFTPD?

---

### Post by darkod on 2016-02-01
Do you have port 10000 forwarded and open too? FTP communicates also on "main port - 1" port. For example, for the standard port 21, FTP communicates also on 20 and you need both of them forwarded and opened.

As for security, you need to look more into how are you protecting your FTP server and not into which port you are using. Changing a default port these days means nothing because they are scanning opened and listened-to ports. They don't depend on whether you will leave ftp on port 21 or change it. Changing the port does not bring you any advanced security against anything.

FTP is known to be very unsecure, so pay more attention to using TLS (not even SSL is enough these days it seems). And make the TLS compulsory, not optional. No connections without TLS!!!

Depending how you need to use your ftp think about other more secure solutions like SCP or SFTP (unlike FTP/FTPS it goes over ssh port 22). Further more you can make scp of sftp require ssh keys only, not accepting passwords. That way only users whos keys are accepted will be able to connect.

If you insist on using ftp instead of scp or sftp, forget about playing with the ports and look in depth into how to secure it. The port means nothing...

---

### Post by own3mall on 2016-02-01
Yes, port 10000 is forwarded and open too.  I'm running a public FTP server, so yes, in my case, changing the port will do wonders, as I am not giving out the FTP links until Recaptcha V2 I'm Not a Robot is passed.  Most people scanning ports will be looking at port 21.  You change the port, and I guarantee that makes it harder to scan and guess.  

FTP is relatively secure for my needs.  No need for anything else.  I just wish I could get it to work with a custom port.

---

### Post by darkod on 2016-02-02
I just re-read it, and you say it doesn't work from the local network too if you change to custom port, right? In such case it looks more like config issue than firewall. If the config is good, local LAN clients should be able to access it correctly because they are not passing through the firewall. That is, if you have possibility to try as local LAN client.

If it's a VPS stuck in a datacentre you can only try from the outside. In such case it could be firewall's fault too. I would double check the firewall again, even if you think all is good. It works on the standard port so compare firewall settings for 20:21 and 10000:10001.

Also on the server confirm running services and ports with:
```
sudo netstat -plunt
```

That will show you whether services are running where you expect them to.

---

### Post by own3mall on 2016-02-07
Yes, it shows VSFTPD listening on port 10001.  I can only access FTP locally on the server.  If I connect to FTP via port 10001 FROM THE SERVER itself, it works, but from any other machine on the LAN or a remote connection, it doesn't work.  I really don't get it.  I think there is a bug in VSFTPD because I have tried this on a VPS and on my home network, and I get the same result on each.  Each firewall is configured correctly to allow it.  The ports 10001 and 10000 are open.  I've tried other port combinations too, and I can't get it to work.  Only port 21 works.

Have you tried getting VSFTPD to run on a different port?  If you haven't, please do.  You may get the same result?

---

### Post by darkod on 2016-02-07
On the server, can you post the output of:
```
sudo iptables -L -n -v
```

Just to confirm iptables rules in case you have firewall active on the server itself.

As for it being a bug, I have no idea. I haven't used it almost at all (or very long time ago). I might have time tomorrow to try and test, but not right now.

---

### Post by own3mall on 2016-02-08
> **darkod said:**
> On the server, can you post the output of:
```
sudo iptables -L -n -v
```

Just to confirm iptables rules in case you have firewall active on the server itself.

As for it being a bug, I have no idea. I haven't used it almost at all (or very long time ago). I might have time tomorrow to try and test, but not right now.

I don't have anything blocked with iptables on the VPS server, and on my test home server, I only have fail2ban entries and Peerguardian entries blocked.  I've done iptables -F as well.  No dice.  I use the default policy.  Yeah, if you could test it and see if you can get VSFTPD running on a custom port, that would be really helpful.  As far as it stands, I'd say it is a bug.  Someone reported here:

[http://www.cyberciti.biz/faq/change-vsftpd-ftp-server-port-21/](http://www.cyberciti.biz/faq/change-vsftpd-ftp-server-port-21/)

> 
After changing the default port number not able to use ftp service from outside network. From Lan it is working fine


Yeah, I'd agree with that statement.

---

### Post by darkod on 2016-02-09
It works, from home LAN. I can't test from outside.

Of course, I can't fully replicate your setup, but just installing vsftpd, then changing the listen_port to 10001 and activating SSL were the only changes I did in the conf file. I could connect by FTP with SSL/TLS.

What you quoted above from that article, that it is working fine from local LAN but not from outside, might have more to do with firewall/routing than vsftpd settings. If you have the settings wrong, it will not work for anyone, remote or local clients. If it doesn't work for remote clients only, you probably have issues with your firewall.

If in your case it doesn't work for local clients too, then look again at the settings because there might be some incompatibility or whatever...

---

### Post by darkod on 2016-02-09
Further on, I tried to configure passive mode like you have it, with port range 45000-45050 and it didn't work.

But commenting out the line pasv_address made it work again. However I wasn't sure if it uses passive or active mode.

Try commenting out the pasv_address and pasv_addr_resolve and see how it goes.

---

### Post by own3mall on 2016-02-10
> **darkod said:**
> Further on, I tried to configure passive mode like you have it, with port range 45000-45050 and it didn't work.

But commenting out the line pasv_address made it work again. However I wasn't sure if it uses passive or active mode.

Try commenting out the pasv_address and pasv_addr_resolve and see how it goes.

Tried that, but it still didn't work for me.  Here is what I've got now:

```

#pasv_enable=YES
listen_port=10001
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=002
file_open_mode=0777
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
nopriv_user=vsftpd
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
guest_enable=YES
guest_username=vsftpd
local_root=/var/www/vhosts/$USER
user_sub_token=$USER
virtual_use_local_privs=YES
user_config_dir=/etc/vsftpd_user_conf
local_max_rate=2000000 # bytes per sec, 2Mbytes per sec
max_clients=50 # to avoid DOS attack, if you have a huge server, increase this..
ftpd_banner=Welcome to vsFTPd Server
allow_writeable_chroot=YES

```

Still can't access the FTP server remotely.

 Did your setup work for remote connections?  What package version of Ubuntu are you running?  What's the output of the following command on your system?

```

dpkg -s vsftpd

```

Thanks for helping me test this!

---

### Post by darkod on 2016-02-10
First, lets clear out what you call remote and local connections. In one of your earlier posts I think you mentioned local as on the server itself, and remote for the private LAN and the internet. For me, that is confusing.

I don't see any point trying from the server itself (localhost), so I didn't even try that. For me, a local client is on the same private LAN subnet, and remote client is outside the local network, on the internet.

If by remote connection you consider from my home desktop to my home server, yes I tried it and it worked. But for me that's local connection, not remote.

I don't know if your server is in your home, or a VPS in a datacentre. So i don't know which type of remote and local connections you can try. If it's a VPS you can try only remote... If it's at home, you can try from another machine at home within your local LAN.

As for the ubuntu version, I actually installed in VBox the daily build of the upcoming 16.04 LTS because I wanted to play later with it. I know this is not identical to your situation, but it shouldn't matter much. The vsftpd version I can check later when at home.

Depending if this is a VPS or not, you can continue testing in few different ways. So is it a VPS or you have the physical (or virtual) server at home/work?

PS. If this server is behind a firewall and NAT (because you mentioned firewall and port forwarding before), and if you want clients outside the local network to use it, the passive mode is your only option. It's how ftp works... Behind firewalls and port forwarding it has to be in passive mode. So it's not too relevant testing with active mode... Just FYI...

---

### Post by own3mall on 2016-02-10
Remote being connecting to a public IP address from a different network.  

If you're testing this on your home server, try connecting from the outside (an IP address on another network). 

I have a VPS and home server.  Both are not working when using a custom port to connect from the outside.

---

### Post by darkod on 2016-02-10
And does the home server work on custom port from the inside?

---

### Post by own3mall on 2016-02-11
> **darkod said:**
> And does the home server work on custom port from the inside?

With the changes you suggested, I can now connect via FTP on the custom port from a LAN connection.  However, I still can't connect to it from the outside.  I have verified the ports are open, but maybe my router running DD-WRT has some security setting or iptables rule I need to adjust to get FTP to work on a different port than 21.  I'm investigating this.  

My VPS is running Ubuntu 12.04, and I cannot connect via FTP on a custom port from the outside.  The connection is established, but it returns a 425 error.

---

### Post by darkod on 2016-02-11
I think it's the firewall or port forwarding (or both). That's why it establishes the connection but as soon as it needs to continue it gets cut off. That's why it's working from the LAN because there is no firewall or port forwarding between the client and the server.

---

### Post by own3mall on 2016-02-11
> **darkod said:**
> I think it's the firewall or port forwarding (or both). That's why it establishes the connection but as soon as it needs to continue it gets cut off. That's why it's working from the LAN because there is no firewall or port forwarding between the client and the server.

On the home server, I'm thinking that is correct, but I'm not sure why.  On the VPS, I have no idea why it gives me a 425.  I don't even get a 425 on the home server because the remote connection to the server cannot even be established which is obviously probably something security wise in the router running DD-WRT despite the fact the ports are forwarded correctly.

---

### Post by darkod on 2016-02-11
Is it possible your VPS provider has some ports blocked? But that would be really stupid. They need to give you all ports available on the VPS because you have a right to select what and how you use on your server.

How are you running the firewall on the VPS? Basic iptables? How about port forwarding?

---

### Post by own3mall on 2016-02-11
Ok, this is really dumb.  I fixed it on both servers.  For the home server, I needed to add these settings specifically to vsftpd.conf:

```

listen_port=10001
pasv_min_port=43000
pasv_max_port=43050
pasv_address=dynamic_dns_domainname
pasv_addr_resolve=YES

```

I then needed to remove the /etc/hosts entry for the dynamic_dns_domainname from the server so that it wouldn't resolve to 127.0.0.1, which would be the address it would send to the remote FTP client as the address to use for the passive connection.

Then, I noticed that I was using DD-WRT incorrectly by trying to port forward the passive range under the "Port Forwarding" tab:

[[img]http://s17.postimg.org/c2yk81zh7/dd_wrt_wrong.jpg[/img]](http://postimg.org/image/c2yk81zh7/)

You have to forward a range under the "Port Range Forwarding" tab:

[[img]http://s17.postimg.org/lyv1tyfvf/dd_wrt_wrong2.jpg[/img]](http://postimg.org/image/lyv1tyfvf/)

Once that was all taken care of, it worked just fine.  The VPS was a firewall issue.  Once I disabled CSF so that it wouldn't block anything, it worked.  I would just need to port forward the range correctly on the VPS via the csf.conf file to get it to work.  Wow, thank you for helping me test, but this whole time it was totally my fault.  Sorry about that, but I really appreciate you helping me out.

---

### Post by darkod on 2016-02-12
No problem, glad you got it going... Please mark the thread as Solved, you can do that in Thread Tools above the first post (on any page of the thread).

---

