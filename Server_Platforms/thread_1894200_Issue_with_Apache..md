---
title: "Issue with Apache."
date: 2011-12-12
forum: Server Platforms
---

### Post by ZettaGeek on 2011-12-12
Greetings,

 I am having some difficulty with Apache Web Server on my Ubuntu Server installation.

When I try to access pages on this server from my web-browser, it will not display any pages, but rather sit on a white screen with the browser saying "Connecting" at the bottom. I can connect to the MySQL Server as well as the OpenSSH server without issues, but Apache will not display pages.

I might add, this was working fine before AT&T added the static IPs to our U-verse service. Before they made that change, I had this server outside of the DMZ (Which I believe it still is) and used a DynamicDNS service to link a domain to that IP. This setup worked quite nicely.

On the code below, I masked the IPs for security reasons. My real IP was replaced with this: "108.XX.XXX.XXX:XXXX" I didn't change the ones that say "0.0.0.0."

Here is the output of "netstat -tulpn"

```

tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      2751/apache2
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -
tcp        0      0 108.XX.XXX.XXX:XXXX    0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:9834            0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:48053           0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:44798           0.0.0.0:*               LISTEN      -
tcp6       0      0 :::22                   :::*                    LISTEN      -
udp        0      0 0.0.0.0:617             0.0.0.0:*                           -
udp        0      0 0.0.0.0:111             0.0.0.0:*                           -
udp        0      0 108.XX.XXX.XXX:XXXX    0.0.0.0:*                           -
udp        0      0 108.XX.XXX.XXX:XXXX   0.0.0.0:*                           -
udp        0      0 0.0.0.0:137             0.0.0.0:*                           -
udp        0      0 108.XX.XXX.XXX:XXXX     0.0.0.0:*                           -
udp        0      0 108.XX.XXX.XXX:XXXX     0.0.0.0:*                           -
udp        0      0 0.0.0.0:138             0.0.0.0:*                           -
udp        0      0 0.0.0.0:43454           0.0.0.0:*                           -
udp        0      0 0.0.0.0:35266           0.0.0.0:*                           -
udp        0      0 0.0.0.0:36828           0.0.0.0:*                           -
udp        0      0 0.0.0.0:2049            0.0.0.0:*                           -
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -
```

Output of "ifconfig"

```
eth0      Link encap:Ethernet  HWaddr 00:c0:4f:53:04:bb
          inet addr:108.XX.XXX.XXX:XXXX  Bcast:108.XX.XXX.XXX:XXXX  Mask:255.255.252.0
          inet6 addr: fe80::2c0:4fff:fe53:4bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1289432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6019 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1730232503 (1.7 GB)  TX bytes:982008 (982.0 KB)
          Interrupt:11 Base address:0xc000
```

If it helps, I also get this error when starting/stopping Apache:
```
 apache2: Could not reliably determine the server's fully qualified domain name, using 108.XX.XXX.XXX for ServerName
```

I'm really not sure how to debug this, so if you need more info, just tell me what to get.

Thank you so much!
- ZettaGeek

---

### Post by Dangertux on 2011-12-12
> **ZettaGeek said:**
> Greetings,

 I am having some difficulty with Apache Web Server on my Ubuntu Server installation.

When I try to access pages on this server from my web-browser, it will not display any pages, but rather sit on a white screen with the browser saying "Connecting" at the bottom. I can connect to the MySQL Server as well as the OpenSSH server without issues, but Apache will not display pages.

I might add, this was working fine before AT&T added the static IPs to our U-verse service. Before they made that change, I had this server outside of the DMZ (Which I believe it still is) and used a DynamicDNS service to link a domain to that IP. This setup worked quite nicely.

On the code below, I masked the IPs for security reasons. My real IP was replaced with this: "108.XX.XXX.XXX:XXXX" I didn't change the ones that say "0.0.0.0."

Here is the output of "netstat -tulpn"

```

tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      2751/apache2
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -
tcp        0      0 108.XX.XXX.XXX:XXXX    0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:9834            0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:48053           0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:44798           0.0.0.0:*               LISTEN      -
tcp6       0      0 :::22                   :::*                    LISTEN      -
udp        0      0 0.0.0.0:617             0.0.0.0:*                           -
udp        0      0 0.0.0.0:111             0.0.0.0:*                           -
udp        0      0 108.XX.XXX.XXX:XXXX    0.0.0.0:*                           -
udp        0      0 108.XX.XXX.XXX:XXXX   0.0.0.0:*                           -
udp        0      0 0.0.0.0:137             0.0.0.0:*                           -
udp        0      0 108.XX.XXX.XXX:XXXX     0.0.0.0:*                           -
udp        0      0 108.XX.XXX.XXX:XXXX     0.0.0.0:*                           -
udp        0      0 0.0.0.0:138             0.0.0.0:*                           -
udp        0      0 0.0.0.0:43454           0.0.0.0:*                           -
udp        0      0 0.0.0.0:35266           0.0.0.0:*                           -
udp        0      0 0.0.0.0:36828           0.0.0.0:*                           -
udp        0      0 0.0.0.0:2049            0.0.0.0:*                           -
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -
```Output of "ifconfig"

```
eth0      Link encap:Ethernet  HWaddr 00:c0:4f:53:04:bb
          inet addr:108.XX.XXX.XXX:XXXX  Bcast:108.XX.XXX.XXX:XXXX  Mask:255.255.252.0
          inet6 addr: fe80::2c0:4fff:fe53:4bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1289432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6019 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1730232503 (1.7 GB)  TX bytes:982008 (982.0 KB)
          Interrupt:11 Base address:0xc000
```If it helps, I also get this error when starting/stopping Apache:
```
 apache2: Could not reliably determine the server's fully qualified domain name, using 108.XX.XXX.XXX for ServerName
```I'm really not sure how to debug this, so if you need more info, just tell me what to get.

Thank you so much!
- ZettaGeek

Can you connect to the apache service locally?

Also for that last error you may need to declare the servers FQDN you can do this by updating your hosts file

108.xxx.xxx.xxx mydomain.com

Then setting your virtual host (site file) ServerName directive to the proper domain, though this shouldn't affect the issue at hand.

Also I'm assuming this is probably MySQL on port 3306, why is that bound externally? Unless you need to you should bind it to localhost only.

```

tcp        0      0 108.XX.XXX.XXX:XXXX    0.0.0.0:*               LISTEN      -

```

I suspect the error is likely in your site configuration, however the information about being able to connect locally will help clarify. Thanks and hope this helps.

---

### Post by ZettaGeek on 2011-12-13
Thanks for the fast response! :D

I would assume when you say local, you are referring to viewing the output of Apache on the server itself. Unfortunately, I don't have a Desktop Manager installed on this system so I have to do all of the administration from the command-line. After firing up w3m and accessing 127.0.0.1, I'm seeing what should be the output of the server prior to the issues with the network.

My suspicion is that the problem lies with Apache listening on the wrong IP, (since it said 0.0.0.0 in netstat.) Would I be correct in this assumption? If so, how would I check that?

Thanks,
ZettaGeek

---

### Post by ZettaGeek on 2011-12-13
> **Dangertux said:**
> Can you connect to the apache service locally?

Also for that last error you may need to declare the servers FQDN you can do this by updating your hosts file

108.xxx.xxx.xxx mydomain.com

Then setting your virtual host (site file) ServerName directive to the proper domain, though this shouldn't affect the issue at hand.

Also I'm assuming this is probably MySQL on port 3306, why is that bound externally? Unless you need to you should bind it to localhost only.

```

tcp        0      0 108.XX.XXX.XXX:XXXX    0.0.0.0:*               LISTEN      -

```

I suspect the error is likely in your site configuration, however the information about being able to connect locally will help clarify. Thanks and hope this helps.

Yes, you are correct, that is MySQL on port 3306. It is working fantastically! I will however repair the port binding as you suggest. Thanks for checking that.

---

### Post by Dangertux on 2011-12-13
> **ZettaGeek said:**
> Yes, you are correct, that is MySQL on port 3306. It is working fantastically! I will however repair the port binding as you suggest. Thanks for checking that.

Hey -- okay 0.0.0.0 isn't really the wrong IP for Apache it just means it's listening on all interfaces.

The port for MySQL is fine. I meant the ip address its listening on should be 127.0.0.1 (unless you need it remotely accessible).

So if you were able to view Apache's output from localhost but not from the designated domain do you have a virtual host set up that might be causing you problems?

It will either be in /etc/apache2/conf/httpd.conf (I think if not just do locate httpd.conf)

Or it will be in /etc/apache2/conf.d/sites-enabled/default (or some other site file)

Make sure the proper domain is listed by ServerName. Hopefully this helps.

---

