---
title: "New to LAMP can't find ip address"
date: 2014-06-08
forum: Server Platforms
---

### Post by jessica14 on 2014-06-08
Just started more detailed web development. and am learning php after a fun romp with css, but I can't get lamp to work. I just used [this ]("https://www.digitalocean.com/community/articles/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu")tutorial to install, another a week ago but errored out. but today everything seemed to go okay with that tutorial except I have no ip for eth0 I thought it was because I use wifi and when I typed 
 ```
[COLOR=#2D2D2D][FONT=monospace]ifconfig eth0 | grep inet | awk '{ print $2 }'[/FONT][/COLOR]
```
but replaced eth0 with wlan0 I got an ip. but that ip doesn't work, neither does lo, in the address bar looking for the info.php.

When I just typed ifconfig this is what I got. 
```
eth0      Link encap:Ethernet  HWaddr 00:24:21:1a:30:cb            UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2452 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:399911 (399.9 KB)  TX bytes:399911 (399.9 KB)


wlan0     Link encap:Ethernet  HWaddr 00:21:6a:bd:79:54  
          inet addr:192.168.1.51  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6aff:febd:7954/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43768 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45858 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20517662 (20.5 MB)  TX bytes:11217728 (11.2 MB)



```

I'm running google-chrome on an intel atom with ubuntu 14.04 I also tested firefox. and read that there is a know issue with skype and apache, but the port was already not 80.

---

### Post by steeldriver on 2014-06-08
Hello and welcome to the forums

What version of Ubuntu are you running? The tutorial you followed  appears to be for 12.04, but I *think* the default DocumentRoot  directory may have changed for 14.04

What actually happens when you type 192.168.1.51 (or localhost) into your browser address bar?

---

### Post by jessica14 on 2014-06-08
I get a 404
[COLOR=#000000][FONT=Times New Roman]The requested URL /info.php was not found on this server. How do I find it via localhost.[/FONT][/COLOR]

---

### Post by SeijiSensei on 2014-06-09
Make sure your web site is in /var/www/html not /var/www.  As steeldriver said, the default directory changed in 14.04.  So you should have a /var/www/html/info.php file rather than /var/www/info.php.

As for the eth0 issue, most web servers are connected over Ethernet not wifi and have a static IP address.  In your case wlan0 is the functional equivalent of eth0. If you are getting an address using DHCP, you should either "reserve" that address on your router, or [set up a static address in Ubuntu]("https://help.ubuntu.com/14.04/serverguide/network-configuration.html#static-ip-addressing").

---

### Post by jessica14 on 2014-06-09
/var/www$ sudo mv ./info.php ./html/ thanks. [http://10.0.0.8/info.php](http://10.0.0.8/info.php) found it. Thanks, I will assign a static ip tonight.

---

