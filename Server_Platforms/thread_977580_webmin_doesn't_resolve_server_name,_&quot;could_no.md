---
title: "webmin doesn't resolve server name, &quot;could not reliably determine the server's name&quot;"
date: 2008-11-10
forum: Server Platforms
---

### Post by jonny.milano on 2008-11-10
hey there,

i have googled and searched around but have not been able to find help for my exact issuse online. 

i recently installed ubuntu server to serve as a home file and print server (who knows maybe i will start using some of those other great features soon). i installed webmin via the command line along with samba, dns server, and lamp during my cd install. however, upon reboot the error message flashes by: "could not reliably determine the server's fully qualified domain. using 127.0.1.1"

i get no response (time out, i think) when i enter "https://myservername:10000/" into my desktop's web browser. however, webmin is working fine when i enter the server's ip address into my browser: "https://192.168.1.100:10000/". 127.0.1.1 does not work.

can someone please help?? how can i setup properly my server's domain name for use on my home network?

thanks in advance!

---

### Post by cariboo on 2008-11-10
Add your server name and ip address to /etc/host like this:

```
192.168.1.200	willy
```

on your computer

Jim

---

### Post by MJN on 2008-11-10
The error is produced by Apache and is telling you that despite it being configured to be using 'name based' virtual hosting it has not been told what one, or more, of its servers is actually called. Note that it is just a warning as it has now made an assumption but it needs an identity for various reasons related to loop detection, self-referrals etc.

The correct fix for this warning/error is to ensure you have specified a [ServerName]("http://httpd.apache.org/docs/2.0/mod/core.html#servername") directive in each of your <Virtualhost> containers.

I have never used Webmin to configure Apache however one assumes it provides you a way by which to set this directive.

(Jim's advice is correct regarding what then to do to enable 'willy' to resolve to the local IP address)

Mathew

---

### Post by jonny.milano on 2008-11-11
hello all, 

i tried doing what cariboo said however i do not have a /etc/host file, i have a etc/hosts file which i changed. if someone could tell me the file that i am to edit i could copy and paste the contents here on this form. now, whenever i try to start apache, i get this error:

```

 * Starting web server apache2
[Tue Nov 11 07:14:18 2008] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:10000
no listening sockets available, shutting down
Unable to open logs
   ...fail!

```

i tried to setup a virtual server on port 80 but (as you can see, i'm having difficulty..)

can someone please help???

---

### Post by jonny.milano on 2008-11-11
mjn,

can you tell me the location of the file i should be editing?

thank you.
j

---

### Post by MJN on 2008-11-11
As you're using Webmin then I won't be of much use as I don't know what files it configures in the backend in response to your frontend configuration changes.

I would assume it to work directly on the Apache site files in /etc/apache2/sites-available/ however given the inclusive modularisation of Apache its config files could be literally anywhere.

This is why I don't like abstract frontend configuration tools - sure they are the easiest way to get something up-and-running but you learn nothing along the way with the consequence being when it doesn't work you don't know how to fix it. This isn't a dig at you - I'm just highlighting why I can't help with the specifics as whilst I understand Apache I don't know how Webmin configures it.

Mathew

---

### Post by jonny.milano on 2008-11-11
Hey MJN,

No! Please, don't leave me now!! :) I am totally willing to edit any files directly with a command shell. In fact, with the command line I found two files at /etc/apache2/sites-available. One was called default and had this in it: 
```

NameVirtualHost *

```
And the other was entitled webmin.1226416358.conf and had this in it:
```

<VirtualHost *:80>
DocumentRoot "/var/www/torrentflux_2.4/html"
<Directory "/var/www/torrentflux_2.4/html">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

```

I would really like to learn more. But for the time being, can you help me setup to domain names? One for torrentflux on port 80 at the server's static IP of 192.168.1.57 and one for webmin (sorry, I know you probably hate this) on port 10000? I learn by doing so if you'll help me I'll learn from this.

-J

---

### Post by jonny.milano on 2008-11-11
Here is so more code that may be of use. I am trying to configure these file at /etc/apache2/sites-available now, with this in the file:
```

<VirtualHost tflux:80>
DocumentRoot "/var/www/torrentflux_2.4/html"
<Directory "/var/www/torrentflux_2.4/html">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

```

I get this error:
```

 * Starting web server apache2
(98)Address already in use: make_sock: could not bind to address 192.168.1.100:10000
no listening sockets available, shutting down
Unable to open logs
   ...fail!

```

Any help is greatly appreciated!

---

### Post by jonny.milano on 2008-11-11
also, my httpd.conf file has nothing in it. but i am thinking that it doesn't have to have anything in it(???) not sure...

---

### Post by jonny.milano on 2008-11-11
also (sorry for all the posts, just really want to get this solved) netstat gives me this:
```

> netstat
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 192.168.1.:microsoft-ds 192.168.1.106:4794      ESTABLISHED
tcp        0      0 localhost:webmin        192.168.1.101:60256     ESTABLISHED
tcp        0      0 192.168.1.5:netbios-ssn 192.168.1.101:49157     ESTABLISHED
tcp        0      0 localhost:webmin        192.168.1.101:60255     ESTABLISHED
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ]         DGRAM                    6090     @/com/ubuntu/upstart
unix  2      [ ]         DGRAM                    6236     @/org/kernel/udev/udevd
unix  9      [ ]         DGRAM                    11390    /dev/log
unix  2      [ ]         DGRAM                    34610    
unix  3      [ ]         STREAM     CONNECTED     30166    /var/run/samba/winbindd_privileged/pipe
unix  3      [ ]         STREAM     CONNECTED     30165    
unix  3      [ ]         STREAM     CONNECTED     14841    /var/run/samba/winbindd_privileged/pipe
unix  3      [ ]         STREAM     CONNECTED     14840    
unix  3      [ ]         STREAM     CONNECTED     13971    /var/run/samba/winbindd_privileged/pipe
unix  3      [ ]         STREAM     CONNECTED     13970    
unix  3      [ ]         STREAM     CONNECTED     13274    
unix  3      [ ]         STREAM     CONNECTED     13273    
unix  3      [ ]         STREAM     CONNECTED     13271    
unix  3      [ ]         STREAM     CONNECTED     13270    
unix  2      [ ]         STREAM     CONNECTED     13269    /var/run/samba/winbindd_privileged/pipe
unix  2      [ ]         DGRAM                    12109    
unix  2      [ ]         DGRAM                    11882    
unix  2      [ ]         DGRAM                    11876    
unix  3      [ ]         STREAM     CONNECTED     11808    
unix  3      [ ]         STREAM     CONNECTED     11807    
unix  2      [ ]         DGRAM                    11578    
unix  2      [ ]         DGRAM                    11460    
unix  2      [ ]         DGRAM                    11440    

```

I see nothing that is using port 80?? what gives?

---

### Post by Stolen Penguin on 2008-11-11
just a little note

its not /etc/host

the correct path is /etc/hosts

:) Good luck with the other stuff!

---

### Post by jonny.milano on 2010-09-21
So... After much adoodoo, I uninstalled WebAdmin and everything is working just fine with config files!

---

