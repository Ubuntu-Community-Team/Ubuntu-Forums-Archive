---
title: "Apache2 - Address already in use: make_sock: could not bind to address"
date: 2007-10-04
forum: Server Platforms
---

### Post by TheGoon on 2007-10-04
Hello,

I've been banging my head with this for 3 days - 

I am using Apache 2 and have un-installed Apache.

I've purged and reinstalled several times. I'm at a loss for any ideas.


[B] 
$sudo  /etc/rc3.d/S91apache2[/B] (does nothing)
[B]

**$ sudo ps -aux | grep apache** (nothing)[/B]



**$ sudo apache2ctl start**
[Thu Oct 04 09:45:17 2007] [warn] module authn_file_module is already loaded, skipping
[Thu Oct 04 09:45:17 2007] [warn] module authz_host_module is already loaded, skipping
[Thu Oct 04 09:45:17 2007] [warn] module authz_groupfile_module is already loaded, skipping
[Thu Oct 04 09:45:17 2007] [warn] module authz_user_module is already loaded, skipping
[Thu Oct 04 09:45:17 2007] [warn] module authz_default_module is already loaded, skipping
[Thu Oct 04 09:45:17 2007] [warn] module auth_basic_module is already loaded, skipping
[Thu Oct 04 09:45:17 2007] [warn] module env_module is already loaded, skipping
[Thu Oct 04 09:45:17 2007] [warn] module setenvif_module is already loaded, skipping
[Thu Oct 04 09:45:17 2007] [warn] module mime_module is already loaded, skipping
[Thu Oct 04 09:45:17 2007] [warn] module status_module is already loaded, skipping
[Thu Oct 04 09:45:17 2007] [warn] module autoindex_module is already loaded, skipping
[Thu Oct 04 09:45:17 2007] [warn] module cgi_module is already loaded, skipping
[Thu Oct 04 09:45:17 2007] [warn] module negotiation_module is already loaded, skipping
[Thu Oct 04 09:45:17 2007] [warn] module dir_module is already loaded, skipping
[Thu Oct 04 09:45:17 2007] [warn] module alias_module is already loaded, skipping
[B](98)Address already in use: make_sock: could not bind to address 1.1.1.1:80
no listening sockets available, shutting down
Unable to open logs[/B]

**$ sudo lsof | grep apache** (nothing)


eth0      Link encap:Ethernet  HWaddr 00:1A:4D:65:01:B1  
          inet addr:**1.1.1.1 ** Bcast:1.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe65:1b1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1486912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:915300 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1020421987 (973.1 MiB)  TX bytes:72401972 (69.0 MiB)
          Interrupt:16 

[B]$ more /etc/apache2/ports.conf 
Listen 1.1.1.1:80[/B]


**$ netstat -napt **
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     -                   
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     -                   
tcp        0      0 192.168.1.64:53         0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     -                   
tcp        0      0 1.1.1.1:53              0.0.0.0:*               LISTEN     -                   
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN     -                   
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     -                   
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     -                   
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN     -                   
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN     -                   
tcp        0      8 1.1.1.1:55221           1.1.1.2:24800           ESTABLISHED22523/synergyc      
tcp6       0      0 :::53                   :::*                    LISTEN     -                   
tcp6       0      0 ::1:953                 :::*                    LISTEN     -

---

### Post by conjur3r on 2007-10-04
Believe it or not, 1.1.1.1 is a publicly available IP address.  It would be wise of you to change your IP address to one of the reserved internal addresses: [http://en.wikipedia.org/wiki/Private_network](http://en.wikipedia.org/wiki/Private_network)

Edit your ports.conf file and change that Listen to 127.0.0.1:80 and try starting apache.

---

### Post by TheGoon on 2007-10-04
It's a crossover between my Linux and windows. 

Changing it to any IP - loopback or otherwise does not work.

---

### Post by TheGoon on 2007-10-07
Looks like I'm up the creek?

---

### Post by conjur3r on 2007-10-09
If you are certain your address of 1.1.1.1 is not affecting anything (I'm still positive it's causing something!), then try changing the port apache is configured to listen on to something unused and try to start it again.

---

### Post by Wim Sturkenboom on 2007-10-09
You can run *netstat* to check which program uses the address.

---

### Post by MJN on 2007-10-09
The netstat output is in the OP, however I would recommend ensuring it is run with sudo to ensure full output.
 
Also, it is worth trying **sudo lsof -i :80** to see exactly what is listening on port 80.
 
Mathew

---

### Post by dbrooke on 2007-10-24
I'm currently getting this... only with 443..

here is my error reporting:
-----------------------------
root@ubuntu:/etc/apache2/sites-available# /etc/init.d/apache2 start
 * Starting web server apache2
(98)Address already in use: make_sock: could not bind to address [::]:443
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:443
no listening sockets available, shutting down
Unable to open logs
   ...fail!
-----------------------------

Donovan

---

### Post by dbrooke on 2007-10-24
Solved:

Multi "ports.conf" files.

apache2>ports.conf
apache2>sites-enabled>porst.conf

Both had LISTEN entries!

(delete multi LISTEN entries to same ports)

Donovan

---

### Post by MJN on 2007-10-24
Ah - I don't think any of use expected that one!
 
(howcome the duplicate file, and in sites-enabled too?)
 
Mathew

---

### Post by dbrooke on 2007-10-28
Well, this was a couple days ago and a quite many headaches ago.. :-)  but I think it was because I followed a couple tutorials to set up the server... 

howtoforge: perfect server gutsy gibbon

Then a tutorial on installing ISPConfig...

Then a tutoria on reinstalling a self-assigned ssl cert.

Somewhere in there is where I'm sure it happened (I'm too new catch these potential errors!). :guitar:

Donovan

---

