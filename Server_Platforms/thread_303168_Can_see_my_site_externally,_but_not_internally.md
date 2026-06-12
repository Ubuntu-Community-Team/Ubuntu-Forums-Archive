---
title: "Can see my site externally, but not internally"
date: 2006-11-19
forum: Server Platforms
---

### Post by dbqp on 2006-11-19
Hi all,

I setup a server using the perfect server guide for 6.10 and all is great! After assistance from this community I learned vi/vim and so much along the way! I am serving up web pages, ftp to my server from another PC on my internal network, can SSH from a PC on my internal network.  I have also confirmed that pages are being served outside of my internal network. That is all working.

What I can't do is actually see the pages being served. I upload, I SSH, I FTP, but my URL takes me to my router login or [http://.....com/.../userfail.html](http://.....com/.../userfail.html)

Looking for any help as I have searched the forums for this problem. I only see posts where people can see it internally, but not externally. My problem is just the opposite!

:-k

---

### Post by DaveBorealis on 2006-11-19
If you're using the same machine as what apache's running on, then point your browser to 127.0.0.1.

Best regards,
Dave

---

### Post by dbqp on 2006-11-19
> **DaveBorealis said:**
> If you're using the same machine as what apache's running on, then point your browser to 127.0.0.1.

Best regards,
Dave

Thanks for the reply, but I am on another PC within my network. My server is running without a GUI (X) so I connect to it from another PC.  I tried 127.0.0.1, but no luck.

FYI - I can access my ISPConfig control panel as well from this other workstation...for what it's worth...but not the actual served pages.

Dave

---

### Post by PilotJLR on 2006-11-19
Probably the only issue here is that your router does not support loopback, which means using your WAN IP address and/or domain name internally will redirect to the lan interface, which would normally be the router config page.

Try browsing to the private IP address you assigned your server... this should work from inside your own network only.

If you also verified it works externally (ie the port forward is okay), then you're all set...

---

### Post by dbqp on 2006-11-19
> **PilotJLR said:**
> Probably the only issue here is that your router does not support loopback, which means using your WAN IP address and/or domain name internally will redirect to the lan interface, which would normally be the router config page.

Try browsing to the private IP address you assigned your server... this should work from inside your own network only.

If you also verified it works externally (ie the port forward is okay), then you're all set...

Thank you.  I try my internal IP such as 192.168.2.11, but this takes me to this page:

 This IP address is shared. For access to the web site which you look for, enter its address instead of its IP.

For questions or problems please contact the server administrator.
powered by ISPConfig 

Title of this page is: Shared IP

I go to the URL, but again as I said above, it takes me to my router...when it goes to this URL it seems like it is confused and constantly refreshes without actually displaying a page - it just "blinks" on the refresh icon in FireFox until I click "Stop"

---

### Post by DaveBorealis on 2006-11-19
> **dbqp said:**
> I try my internal IP such as 192.168.2.11, but this takes me to this page:

 This IP address is shared. For access to the web site which you look for, enter its address instead of its IP.
<SNIP>

Hm...I just fired up apache on another machine within my home net (although it's running Mac OS X), and I reached the webserver by typing in '192.168.1.112'.

Could it be something in your host file?  Do you have the domain name assigned to the internal IP of the apache server on the client trying to access it?  On this client I have 192.168.1.112 assigned to the server's host name, and I can reach it by either the IP or the name.  Also on the server I have its host name assigned to 192.168.1.112.  

Dave

---

### Post by dbqp on 2006-11-19
> **DaveBorealis said:**
> Hm...I just fired up apache on another machine within my home net (although it's running Mac OS X), and I reached the webserver by typing in '192.168.1.112'.

Could it be something in your host file?  Do you have the domain name assigned to the internal IP of the apache server on the client trying to access it?  On this client I have 192.168.1.112 assigned to the server's host name, and I can reach it by either the IP or the name.  Also on the server I have its host name assigned to 192.168.1.112.  

Dave

How can I do this?  The client I am working from is IP 198.168.2.14 and the server is 192.168.2.11 on my internal network. Please explain.

My hosts file (on the server) domain is assigned to 198.168.2.11



Thank you!

---

### Post by DaveBorealis on 2006-11-19
> **dbqp said:**
> How can I do this?  The client I am working from is IP 198.168.2.14 and the server is 192.168.2.11 on my internal network.

On both client and server machines add to '/etc/hosts'```

'198.168.2.11     <internal server name>.<internal net name>      <internal server name>'

```

Then use 'http://<internal server name>/' as the URL.

---

### Post by dbqp on 2006-11-19
> **DaveBorealis said:**
> On both client and server machines add to '/etc/hosts'```

'198.168.2.11     <internal server name>.<internal net name>      <internal server name>'

```

Then use 'http://<internal server name>/' as the URL.

So in my /etc/hosts file I have:

127.0.0.1      localhost.localdomain   localhot
192.168.2.11   xxxx.xxxxxxxxxx.com     xxxx

and add:

192.168.2.14   xxxx.xxxxxxxxxx.com    xxxx

under the existing IP's and domain?

---

### Post by DaveBorealis on 2006-11-19
> **dbqp said:**
> So in my /etc/hosts file I have:

127.0.0.1      localhost.localdomain   localhot
192.168.2.11   xxxx.xxxxxxxxxx.com     xxxx

and add:

192.168.2.14   xxxx.xxxxxxxxxx.com    xxxx

under the existing IP's and domain?

No, on both machines there should be an entry for the apache server's internal IP and internal host name:
```

client:
192.168.2.11    xxxx    xxxx
server
192.168.2.11    xxxx.localhost     xxxx

```
Unless the dot-com name is also the alias for your 192.168.2.0 network, just use localhost on the server and I believe nothing on the client, like above.  And on the apache's server use the command 'hostname' to get its internal host name.  (It's also in the '/etc/hostname' file.)

---

### Post by dbqp on 2006-11-19
> **DaveBorealis said:**
> No, on both machines there should be an entry for the apache server's internal IP and internal host name:
```

client:
192.168.2.11    xxxx    xxxx
server
192.168.2.11    xxxx.localhost     xxxx

```
Unless the dot-com name is also the alias for your 192.168.2.0 network, just use localhost on the server and I believe nothing on the client, like above.  And on the apache's server use the command 'hostname' to get its internal host name.  (It's also in the '/etc/hostname' file.)

I do have a DynDNS set up directing it to a dot com. I am not really sure what you mean from your response.  I changed my servers hosts file to xxxx.localhost but that did not work....I have since changed it back...

My localhost and hostname are the same and everything is lined up correctly in that regard...

???

---

### Post by jjross on 2006-11-19
take a look at etc/resolv.conf on your server and post what it says , I had a similar problem and changed this to 127.0.0.1 and that made it work,

---

### Post by dbqp on 2006-11-19
> **jjross said:**
> take a look at etc/resolv.conf on your server and post what it says , I had a similar problem and changed this to 127.0.0.1 and that made it work,

I have the server hostname: xxxx.xxxxxxxxx.com
and the name servers: 192.168.2.11 on both

I changed these both to 127.0.0.1  but still no luck - will I need t shutdown and restart?

---

### Post by meyrd on 2006-11-19
I tried the same thing and it did not work for me either. I also have a dyndns account that points to my server. I cannot view from within unless I just type in the local lan address. If I type in the whole address with the www I get my router setup page on the router wan address (not the internet wan address).
I also found that if your router is set to auto update the dyndns account settings for your dynamic ip you need to check and make sure it doesn't change it to the router wan address, (this has happened to me).

---

### Post by jjross on 2006-11-19
you definitely need to restart apache everytime you make a change in a config file

---

### Post by jjross on 2006-11-19
for what its worth, my etc/resolv.conf has only 1 line
nameserver 127.0.0.1

---

### Post by dbqp on 2006-11-19
> **meyrd said:**
> I tried the same thing and it did not work for me either. I also have a dyndns account that points to my server. I cannot view from within unless I just type in the local lan address. If I type in the whole address with the www I get my router setup page on the router wan address (not the internet wan address).
I also found that if your router is set to auto update the dyndns account settings for your dynamic ip you need to check and make sure it doesn't change it to the router wan address, (this has happened to me).

I just experienced that same scenario with my router/DynDNS service.  I was getting a MySQL error when trying to log in to ISPConfig and modified my IP at DynDNS and tried again with success.

Stil can't see my site internally after changing my resolv.conf file to one name  server with the IP 127.0.0.1..(and restarted!)hmmm....

---

### Post by dbqp on 2006-11-19
> I also found that if your router is set to auto update the dyndns account settings for your dynamic ip you need to check and make sure it doesn't change it to the router wan address, (this has happened to me).

How did you correct this problem?

---

### Post by jjross on 2006-11-19
Wish I could help more but that is about all I know, Your set up is different than mine, I am using VHCS, so some of the settings may be different in the system your using.
Dont give up, the answer is here on the forum somewhere.

---

### Post by meyrd on 2006-11-19
I have a belkin router and it gives me the ability to turn off auto update to dyndns. I unchecked the box and then had to update my settings by logging in at dyndns.com.
The router had sent the wan address settings instead of my dynamic ip from my isp.
Sometimes ya just gotta do it the manual way.
I realize you still can't see your site internally but...Hope this helps!

---

### Post by DaveBorealis on 2006-11-19
Say, you do have apache listening on port 80?  I mean, you don't have your router catching port 80 requests and forwarding them to something like 192.168.2.11:8080?  (This is a wild guess, but it's the best I can do!)

Dave

---

### Post by dbqp on 2006-11-19
> **DaveBorealis said:**
> Say, you do have apache listening on port 80?  I mean, you don't have your router catching port 80 requests and forwarding them to something like 192.168.2.11:8080?  (This is a wild guess, but it's the best I can do!)

Dave

My ports.conf file is listening to ports 80 and 443 as in the perfect setup guide.  On my router I have redirected port 80 (HTTP) to 192.168.2.11 (the server).  Could this be my problem?

EDIT: I tried disabling this port forward and no go....still the same result

---

### Post by DaveBorealis on 2006-11-20
> **dbqp said:**
> My ports.conf file is listening to ports 80 and 443 as in the perfect setup guide.  On my router I have redirected port 80 (HTTP) to 192.168.2.11 (the server).  Could this be my problem?

EDIT: I tried disabling this port forward and no go....still the same result

On my FreeBSD apache server the port is set in 'httpd.conf' with a slingle line: 'Port 80'.  On that machine it's found in '/usr/local/etc/apache/httpd.conf'.

Your could try pointing your browser to 'http://192.168.2.11:443/' and see what happens.

---

### Post by dbqp on 2006-11-20
> **DaveBorealis said:**
> On my FreeBSD apache server the port is set in 'httpd.conf' with a slingle line: 'Port 80'.  On that machine it's found in '/usr/local/etc/apache/httpd.conf'.

Your could try pointing your browser to 'http://192.168.2.11:443/' and see what happens.

BINGO!

YOU ROCK!

Thank you.  Although it takes me to the root directory, I can thn click on the wb folder to see how it serves!

Thank you, thank you, thank you! (can you tell this makes me happy?)

:D

---

### Post by DaveBorealis on 2006-11-20
> **dbqp said:**
> BINGO!
Hey, now I can go to bed feeling like I accomplished something today!

(And you're very welcome.  It was fun.)

Dave

---

### Post by dbqp on 2006-11-20
> **DaveBorealis said:**
> Hey, now I can go to bed feeling like I accomplished something today!

(And you're very welcome.  It was fun.)

Dave

You can definitely sleep sound, Superman. - THANK YOU!

---

### Post by MJN on 2006-11-21
The use of the *Port* directive has been deprecated in Apache (since v2.0) hence you would be advised not to use it (it may 'work' now, but this cannot be guaranteed for future versions).

Do you have a /etc/apache/ports.conf file? And is it referenced (and therefore parsed) by an **Include /etc/apache2/ports.conf** directive in /etc/apache/apache2.conf?

Also, do your <Virtualhost> directives in /etc/apache2/sites-available/* contain a port suffix (e.g. **<Virtualhost *:80>**) and, if you're using name-based virtual hosting do the **Servername **directives contain a port suffix (e.g. **Servername [www.newtonnet.co.uk:80]("http://www.newtonnet.co.uk:80")**) ?

If so, it should be working hence I suspect one of the above is missing.

I am intrigued about you saying '*Although it takes me to the root directory, I can thn click on the wb folder to see how it serves*' what is your **DocumentRoot** directive set to in your <Virtualhost> directive? It ought to be your web folder, and not the parent directory (which is how it sounds at the moment).

Mathew

---

