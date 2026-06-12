---
title: "Unable to connect FTP using FTP client"
date: 2013-08-01
forum: Server Platforms
---

### Post by sububtu on 2013-08-01
Hi all ...
happy to see the forum- live again...

Iam having a squid proxy configured as transperant proxy with dansguardian.
the proxy is serving connections and working smoothly for the http requests and ftp requests from web browser.
But i wonder why !! iam unable to connect using any ftp clients !!!
At the same time iam able to connect using the ftp client from the proxy server.
So i guess there is some problem with my squid.conf. Here is the squid .conf details . .. 



acl manager proto cache_object
acl localhost src 127.0.0.1/32 ::1
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32 ::1
acl localnet src 192.168.1.0/24    # RFC1918 possible internal network
acl SSL_ports port 443
acl Safe_ports port 80        # http
acl Safe_ports port 21        # ftp
acl Safe_ports port 443        # https
acl Safe_ports port 70        # gopher
acl Safe_ports port 210        # wais
acl Safe_ports port 1025-65535    # unregistered ports
acl Safe_ports port 280        # http-mgmt
acl Safe_ports port 488        # gss-http
acl Safe_ports port 591        # filemaker
acl Safe_ports port 777        # multiling http
acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access deny all
http_port 4239 transparent
coredump_dir /var/spool/squid3
refresh_pattern ^ftp:        1440    20%    10080
refresh_pattern ^gopher:    1440    0%    1440
refresh_pattern -i (/cgi-bin/|\?) 0    0%    0
refresh_pattern (Release|Packages(.gz)*)$      0       20%     2880
refresh_pattern .        0    20%    4320
visible_hostname proxyserver1

Squid running on ubuntu server 12.04
Please help me . ..

---

### Post by TheFu on 2013-08-01
Is your FTP client running in active or passive modes?

Of course, for distributing things to the entire world, FTP is fine, but for any sort of limited distribution of files, sftp would be much preferred: [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)

---

### Post by sububtu on 2013-08-02
@TheFu 
Thanks for your valuable reply.
Im running the FileZilla FTP client in recommended passive mode.
 iam unable to connect using neither Filezilla nor WINscp .
But ,,,as i already mentioned im able to connect ftp from the browser easily  why this happens ??!!!!

---

### Post by CharlesA on 2013-08-02
> **sububtu said:**
> @TheFu 
Thanks for your valuable reply.
Im running the FileZilla FTP client in recommended passive mode.
 iam unable to connect using neither Filezilla nor WINscp .
But ,,,as i already mentioned im able to connect ftp from the browser easily  why this happens ??!!!!

Are you sure port 20 and 21 are open? I don't know why a browser would be any different from a ftp client, but it's worth a shot.

I pretty much echo TheFu's opinion on sftp. I use it all the time and it is a lot easier to configure/deal with than plain ftp.

---

### Post by sububtu on 2013-08-02
> **CharlesA said:**
> Are you sure port 20 and 21 are open? I don't know why a browser would be any different from a ftp client, but it's worth a shot.

I pretty much echo TheFu's opinion on sftp. I use it all the time and it is a lot easier to configure/deal with than plain ftp.

Yes port 21 is Open .
Iam able to use FTP clent from the Proxy server itself!!.
But unable to connect from clent machines which uses the proxyserver@port: 8080

---

### Post by TheFu on 2013-08-02
FTP is either Active or Passive. I don't recall which is which, but 1 needs 2 ports and the other 1.  That means the firewall needs to allow both ports and if a proxy is involved, then it needs to allow inbound connections - which would be extremely unusual.  I think the 2nd port, the data one, is dynamic, so you'll have a hard time with most firewall to get that working. The wikipedia article on FTP should explain everything about both methods.

The web browser knows about the proxy, since you configured it for the web already.  Did you also tell the FTP client(s) about the proxy?

With sftp, only 1 port is needed. Firewalls are easy to configure.  sftp uses the ssh port and that single port can support ssh, scp, sftp, rsync, NX, and a host of other, lesser known, things.  sftp is not as fast as ftp since it has encrypted connections.  

Of course, if you don't control the other side, sftp is not an option. Sniff, sniff.   If the other side is a webhost, ask for sftp from them. If they don't have it - I'd switch to another webhost provider.  FTP should have died in the 1990s for any non-world-wide distribution uses.

---

### Post by CharlesA on 2013-08-02
> **TheFu said:**
> Of course, if you don't control the other side, sftp is not an option. Sniff, sniff.   If the other side is a webhost, ask for sftp from them. If they don't have it - I'd switch to another webhost provider.  FTP should have died in the 1990s for any non-world-wide distribution uses.

When I was using a shared host, SSH access was a requirement for me cuz shell access is a good thing to have and I prefer rsync over ssh and sftp over plain FTP.

Now that I've moved to a VPS, I haven't looked back.

---

