---
title: "need help setting up web host on home server"
date: 2012-01-02
forum: Server Platforms
---

### Post by Fitseries3 on 2012-01-02
First off, im new here but im no noob to computers by any means so please be respectful and i will treat you the same. if you want some background on me google my username.

**I am moving my business website to my own server here at home. **

**things i have setup so far:**
ubuntu 11.10 
apache2
phpmyadmin
mysql
vsftpd installed(but not sure if setup correctly)
wordpress 3
router is forwarding necessary ports
dns is setup properly and site is viewable from web

**problems im having:**
cannot get ftp to work from remote computers
all links on the site link to "localhost/" 
if you type the sites address, browser immediately changes to the ip addy instead of the name



i have iptables turned off for now to attempt to get ftp working but will enable it once issues are sorted out.

any help would be great. THANKS in advance

---

### Post by lisati on 2012-01-02
*Thread moved to **Server Platforms**.*

I was going to ask about port forwarding, but see that you've already looked at that.

---

### Post by Fitseries3 on 2012-01-02
> **lisati said:**
> *Thread moved to **Server Platforms**.*

I was going to ask about port forwarding, but see that you've already looked at that.

well to double check....

i have forwarded:
20
21
22
80
1023

---

### Post by azmyth on 2012-01-02
I suspect that when you setup wordpress you set it up locally thus it still has your paths as localhost. You probably need to change your wordpress paths.

---

### Post by Fitseries3 on 2012-01-02
> **azmyth said:**
> I suspect that when you setup wordpress you set it up locally thus it still has your paths as localhost. You probably need to change your wordpress paths.

what should it be set to?

WP is in /var/www/ 
i have "wordpress address (URL)" set to [http://ip.ad.dre.ss/wordpress](http://ip.ad.dre.ss/wordpress)
and "site address (URL)" set to [http://localhost/wordpress](http://localhost/wordpress)


**EDIT:**

i changed both to [http://www.mywebsiteaddres.com](http://www.mywebsiteaddres.com) and now the localhost problem is fixed. thank you azmyth

---

### Post by fdrake on 2012-01-02
> problems im having:
cannot get ftp to work from remote computers

are you sure your ftpserver is listening?
```
nmap localhost
```

---

### Post by Fitseries3 on 2012-01-02
> **fdrake said:**
> are you sure your ftpserver is listening?
```
nmap localhost
```

```

Starting Nmap 5.21 ( http://nmap.org ) at 2012-01-02 19:16 CST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000023s latency).
Not shown: 994 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
3306/tcp open  mysql

Nmap done: 1 IP address (1 host up) scanned in 0.14 seconds
```

---

### Post by volkswagner on 2012-01-02
> **Fitseries3 said:**
> 
dns is setup properly and site is viewable from web

**problems im having:**
cannot get ftp to work from remote computers
all links on the site link to "localhost/" 
if you type the sites address, browser immediately changes to the ip addy instead of the name




I'm not sure what this means.  Please clarify how you are attempting to connect to your ftp server.  What client and OS are you using to try and connect from?  Are you trying from outside your LAN?  Are you entering "ftp://123.456.789.xxx"  in a web browser?

---

### Post by azmyth on 2012-01-02
You can ftp connect between two computers on your LAN? On the WAN, you say it can't connect what error does it give? Is it a password issue or a not found issue?

---

### Post by Fitseries3 on 2012-01-02
> **volkswagner said:**
> I'm not sure what this means.  Please clarify how you are attempting to connect to your ftp server.  What client and OS are you using to try and connect from?  Are you trying from outside your LAN?  Are you entering "ftp://123.456.789.xxx"  in a web browser?

i cannot connect using filezilla in win7 on any of my laptops, same network.

i've tried [www.mysiteaddress.com](www.mysiteaddress.com) and 12.34.45.67 in filezilla as well as [ftp://12.34.45.67](ftp://12.34.45.67) and [ftp://www.mysiteaddress.com](ftp://www.mysiteaddress.com) in firefox

---

### Post by Fitseries3 on 2012-01-02
> **azmyth said:**
> You can ftp connect between two computers on your LAN? On the WAN, you say it can't connect what error does it give? Is it a password issue or a not found issue?

firefox throws "problem loading page, can't establish a connection to the server"

and filezilla says "Connection attempt failed with "ECONNREFUSED - Connection refused by server".

**EDIT**

i CAN connect via local net address of [ftp://192.168.1.135](ftp://192.168.1.135)

---

### Post by volkswagner on 2012-01-02
I have not used vsftp.

According to the man page
>     listen_address
              If vsftpd is in standalone mode, the default listen address  (of
              all local interfaces) may be overridden by this setting. Provide
              a numeric IP address.

              Default: (none)


What do you have for listen_adress?

The way I interpret this is default is setup for local only.  Perhaps you need to specify your eth0 or eth1 device here?

I say this because it appears to be working locally.

You may first need to verify the port is listening and is not blocked by your isp or router.

Go to canyouseeme.org and check port 21 from inside your LAN.

---

### Post by Fitseries3 on 2012-01-02
> **volkswagner said:**
> I have not used vsftp.

According to the man page


What do you have for listen_adress?

The way I interpret this is default is setup for local only.  Perhaps you need to specify your eth0 or eth1 device here?

I say this because it appears to be working locally.

You may first need to verify the port is listening and is not blocked by your isp or router.

Go to canyouseeme.org and check port 21 from inside your LAN.

```
[COLOR=red]Error:[/COLOR] I could **not** see your service on **24.94.182.147** on port (**21**)
Reason: Connection timed out
```

in /etc/vsftpd.conf       listen_address=24.94.182.147

---

### Post by volkswagner on 2012-01-03
I assume that is not your real ip, since I was not able to view your site.  You should not have your external ip listed.  I think you should list your interface as eth0 or eth1 (which ever is tied to your router).

The following command will list your interface name.
```
ifconfig
```

The error from canyouseeme.org is critical error.  since your sever appears to be correctly listening on port 21, the issue is either with your port forward or your isp is blocking port 21.

---

### Post by Fitseries3 on 2012-01-03
something happened and out of the blue i cant see the site remotely any more. this is really frustrating

---

### Post by volkswagner on 2012-01-03
> **Fitseries3 said:**
> something happened and out of the blue i cant see the site remotely any more. this is really frustrating


Does your isp provide you a static or dynamic ip address?  If it is the later perhaps your ip changed?  When you navigate to canyouseeme.org, does it show the address you expect?

---

### Post by Fitseries3 on 2012-01-03
dynamic. its still the same for now.

i cant even view the site locally any more, not even from the server. somethings botched up locally

---

