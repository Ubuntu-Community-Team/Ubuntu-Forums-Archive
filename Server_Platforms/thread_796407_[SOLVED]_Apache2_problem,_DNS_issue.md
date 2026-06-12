---
title: "[SOLVED] Apache2 problem, DNS issue?"
date: 2008-05-16
forum: Server Platforms
---

### Post by Titan8990 on 2008-05-16
I am trying to set up webmail on my server using apache2. I having some form of DNS problem that I believe might be related to my /etc/hosts file. What is happening is I can only view my webmail page by inputting my local ip or the 127.0.0.1 loopback in the browser. If I try to use the name domain name or if I try to use local host firefox prompts me if I want to open or save a PHTML file. The PHTML file has what appears to be a randomly generated name because if a run find for the file name of the PHTML file it comes up with nothing. Also, the name of the file is never the same but the contents are the same. is a redirect that has the following contents:

```
<?php

/**
 * index.php
 *
 * Redirects to the login page.
 *
 * @copyright &copy; 1999-2007 The SquirrelMail Project Team
 * @license http://opensource.org/licenses/gpl-license.php GNU Public License
 * @version $Id: index.php 12127 2007-01-13 20:07:24Z kink $
 * @package squirrelmail
 */

// Are we configured yet?
if( ! file_exists ( 'config/config.php' ) ) {
    echo '<html><body><p><strong>ERROR:</strong> Config file ' .
        '&quot;<tt>config/config.php</tt>&quot; not found. You need to ' .
        'configure SquirrelMail before you can use it.</p></body></html>';
    exit;
}

// If we are, go ahead to the login page.
header('Location: src/login.php');

?>
```

I created php test file that works correctly as long as I use my local IP. I find it odd that localhost does not even work. I had to play around with my hosts file in order to get my mail server to work correctly. Anyways here is what my /etc/hosts file looks like:

192.168.26.1 MYDOMAIN.com
127.0.0.1 localhost MYDOMAIN.com
192.168.26.25 MYDOMAIN.com

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I am always appreciative of any help I can get.

---

### Post by dmizer on 2008-05-17
you have set up three locations for MYDOMAIN.com.  dns has no idea where to look for it.

here's my working hosts on a client (named tsubasa) in my network:
```
127.0.0.1 localhost
127.0.1.1 tsubasa
192.168.0.7 MYDOMAIN.net MYDOMAIN.com

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

here's a working hosts file on the server:
```
127.0.0.1       localhost
127.0.1.1       MYDOMAIN.net MYDOMAIN.com servername

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by Titan8990 on 2008-05-18
I will make the changes on Monday and see if it changes anything. I gave it a shot from my home machine and it doesn't have the issue that the local machine has. 


Thanks for the reply.

---

### Post by Titan8990 on 2008-05-19
Alright, i made the changes to my /etc/hosts/ and it now looks like the following:

127.0.1.1        einstein
127.0.0.1        localhost
192.168.26.25    MYDOMAIN.com

Now I can only view my page by going to my local address of 192.168.26.25 but not by typing in localhost or MYDOMAIN.com. This isn't a big issue since it seems that machines other than this one can get to the webmail via MYDOMAIN.com but I am interest in what could cause this issue.

---

### Post by jklm988 on 2008-05-19
You write very well, support you![neoprene computer bags](http://www.cnprince.com/en/oem.html) [neoprene Laptop computer bags](http://www.cnprince.com/en/oem.html) [memory foam computer bags](http://www.cnprince.com/en/oem.html) [memory foam Laptop computer bags](http://www.cnprince.com/en/oem.html)

---

### Post by dmizer on 2008-05-20
what is einstein's ip address? (post the results of ifconfig)

also, post the contents of /etc/nsswitch

---

### Post by Titan8990 on 2008-05-20
eth0      Link encap:Ethernet  HWaddr 00:1D:7D: D3:2D:97  
          inet addr:192.168.26.25  Bcast:192.168.26.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fed3:2d97/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:143839 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38917 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33496994 (31.9 MB)  TX bytes:3700910 (3.5 MB)
          Interrupt:21 Base address:0xe000 

It is set statically. And:

root@einstein:~# cat /etc/nsswitch
cat: /etc/nsswitch: No such file or directory

---

### Post by dmizer on 2008-05-20
okay, since einstein is your server, your /etc/hosts file should look like the "server" example i gave above, not the "client" example.

like so:
```
127.0.1.1 einstein MYDOMAIN.com
127.0.0.1 localhost
```

any computer on your network other than einstein, should look like this:
```
127.0.1.1 einstein
127.0.0.1 localhost
192.168.26.25 MYDOMAIN.com
```

---

### Post by Titan8990 on 2008-05-20
This is not the domain server though it is only the E-mail server. The domain server is 192.168.26.1. It is using ISA to forward the address to the local machine. There is actually three domains hosted from the one server. 


Also, there are no other computers to configure hosts lists on as it is network of MS workstations.

---

### Post by dmizer on 2008-05-21
hosts file performs the same function in Windows NT/2000/XP/2003/Vista: %SystemRoot%\system32\drivers\etc\hosts
more information here: [http://support.microsoft.com/kb/172218](http://support.microsoft.com/kb/172218)

your eamil server is not resolving itself.  you have two choices.  you can point your email server to itself via hosts, or you can point it to your domain server.  either way, it only effects how einstein handels MYDOMAIN.com

point your email server to the domain server:
```
127.0.1.1 einstein
127.0.0.1 localhost
192.168.26.1 MYDOMAIN.com
```

if that doesn't work, point your email server to itself:
```
127.0.1.1 einstein MYDOMAIN.com
127.0.0.1 localhost
```

but perhaps a bigger question is ... why does your isa server not resolve the domain for your email server.  what happens if you completely remove MYDOMAIN.com from the hosts file on the email server?

---

### Post by Titan8990 on 2008-05-21
> but perhaps a bigger question is ... why does your isa server not resolve the domain for your email server. what happens if you completely remove MYDOMAIN.com from the hosts file on the email server?

Seems that removing that has no effect on the web server. The local machine can still only view the page by typing in my local address. It seems that changes to /etc/hosts/ does not change this as I have had MYDOMAIN.com point at just about everything. 

I'm not sure if this has an effect on the E-mail aspect of the server yet. We are still having issues getting SMTP connections to the box. The rule is set in ISA to foreward SMTP traffic to einstein but I set up a packet sniffer on einstein and that traffic is not making it to me. IMAP follows the same port forewarding rule and works flawlessly. We are going to work on it today and I will let you know how it goes.

---

### Post by Titan8990 on 2008-05-22
Alright, your input ended up helping in a somewhat unrelated issue and for this I thank you. If you are interested the correct end result was this:

root@einstein:~# cat /etc/hosts
127.0.1.1        einstein
127.0.0.1        localhost
192.168.25.24    MYDOMAIN.COM
192.168.25.1     MY.ISA.SERVER

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

We now have a fully functioning Email server w/ webmail and it's secured with TLS!

---

### Post by dmizer on 2008-05-22
i'm very glad to hear it's working for you!

but, that /etc/hosts configuration looks very strange to me, since einstein's ip address is 192.168.25.24 ... but maybe i just do not have a complete understanding of how hosts works in tandem with a local dns server.

---

### Post by Titan8990 on 2008-05-22
Who knows, it might not be completely right but as long as nothing is broken I am not going to try and fix it.

---

### Post by windependence on 2008-05-23
> **Titan8990 said:**
> Alright, your input ended up helping in a somewhat unrelated issue and for this I thank you. If you are interested the correct end result was this:

root@einstein:~# cat /etc/hosts
127.0.1.1        einstein
127.0.0.1        localhost
192.168.25.24    MYDOMAIN.COM
192.168.25.1     MY.ISA.SERVER

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

We now have a fully functioning Email server w/ webmail and it's secured with TLS!

You are behind a Micro$shaft ISA server?

-Tim

---

### Post by atvar on 2008-05-23
This post really helped! Thanks guys!

---

