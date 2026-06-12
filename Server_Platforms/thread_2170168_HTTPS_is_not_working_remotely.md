---
title: "HTTPS is not working remotely"
date: 2013-08-25
forum: Server Platforms
---

### Post by owena1337 on 2013-08-25
Hi,

I setup my server using the "Perfect Server Ubuntu 12.04" guide. Everything went well and everything is working as far as I know of except SSL remotely. I can access [https://192.168.0.100](https://192.168.0.100) - which is my homeserver's LAN IP address coincidently with the guide, however I do receive 403 for that, but SSL doesn't seem to work if I try and access it through it's domain name or external IP address. The setting in ISPConfig for SSL does not work either when setting up a website. As of now I've hit rock bottom.

Any ideas?

---

### Post by TheFu on 2013-08-25
Did you purchase an SSL cert?
Do you own a domain?
Did you setup DNS for the domain to point to your home public IP address?
Did you open port 443 on the edge router to your house?
Are you positive the ISP doesn't block inbound connections on port 25, 80, 443?

---

### Post by 2Stoned on 2013-08-25
TheFu has some good points there.
Imo, i think this can be fixed with just port forwarding to 443. Thats it.

---

### Post by owena1337 on 2013-08-25
> **TheFu said:**
> Did you purchase an SSL cert?
Do you own a domain?
Did you setup DNS for the domain to point to your home public IP address?
Did you open port 443 on the edge router to your house?
Are you positive the ISP doesn't block inbound connections on port 25, 80, 443?

1&2.) I own a domain, and it points towards my home's external IP Address.
3.) My homeserver is in the DMZ. It's sitting outside the firewall open to everything.
4.) 100% positive

---

### Post by CharlesA on 2013-08-25
If you are getting a 403 error, you should fix that first, before trying to figure out why HTTPS isn't working externally.

If you couldn't connect via https, it would either timeout or give you an error, what errors are you getting?

I don't use ISPConfig, so I configure my web servers manually, have you checked the configuration and verified that port 80, 443, and 25 are open to the internet and not blocked by your ISP?

---

### Post by owena1337 on 2013-08-25
I host websites via the webserver, it's got nothing to do with the ports (ports check also confirm) It works on Windows Server 2008 also. PLUS I can use HTTPS via webmin from another location outside my home network.

---

### Post by sandyd on 2013-08-25
> **owena1337 said:**
> I host websites via the webserver, it's got nothing to do with the ports (ports check also confirm) It works on Windows Server 2008 also. PLUS I can use HTTPS via webmin from another location outside my home network.

What do you mean by "can use HTTPS via webmin from another location outside my home network"

---

### Post by owena1337 on 2013-08-25
By accessing my home server's external IP address either by it's IP OR domain name with ":1000" on the end via HTTPS. E.g...

[https://test.com:1000](https://test.com:1000)

---

### Post by sandyd on 2013-08-25
Does running
```

lsof -i :443
```
on the server produce anything?

---

### Post by owena1337 on 2013-08-25
It does not, no.

---

### Post by TheFu on 2013-08-25
> **owena1337 said:**
> It does not, no.

Well, there is the issue. Apache (or whatever web server) isn't listening on port 443. That is the default port for HTTPS.

---

### Post by owena1337 on 2013-08-25
> **TheFu said:**
> Well, there is the issue. Apache (or whatever web server) isn't listening on port 443. That is the default port for HTTPS.

That's what I thought, but would that explain why I get 403 when accessing it via "192.168.0.100" (which is my home servers Lan address)?

---

### Post by TheFu on 2013-08-25
> **owena1337 said:**
> That's what I thought, but would that explain why I get 403 when accessing it via "192.168.0.100" (which is my home servers Lan address)?

I would draw a diagram showing all the points that packets traverse from A-Z to get where I think they should be going, then I'd double check each point in the real world to validate the packets actually follows the path I believe it does.

403 ... isn't that permission denied? I didn't look it up.  I return 403 on my websites for places or spiders that I don't like. If that's the case, your packets are getting to the server but the it is likely that simple file permissions are the issue.

---

### Post by CharlesA on 2013-08-25
> **TheFu said:**
> 403 ... isn't that permission denied? I didn't look it up.  I return 403 on my websites for places or spiders that I don't like. If that's the case, your packets are getting to the server but the it is likely that simple file permissions are the issue.

Indeed. Looking at the web server logs should tell you why that error is being thrown.

As far as webmin working, it runs it's own web server, so it doesn't touch Apache or Nginx or whatever you are using.

---

### Post by TheFu on 2013-08-26
> **CharlesA said:**
> Indeed. Looking at the web server logs should tell you why that error is being thrown.

As far as webmin working, it runs it's own web server, so it doesn't touch Apache or Nginx or whatever you are using.

It probably doesn't need to be said here, but just in case someone is lurking....
* webmin has been hacked into a few times providing the remote hacker with full admin access to servers.
* webmin is very capable, but allowing it to be accessed over the wider internet is **extremely poor security.**
* If you must use any web-min - SQL-min - whatever, please, please, please, please prevent access from everywhere, except the 1 or 2 specific IPs you'll come from.  This applies even on a LAN.

Be safe out there folks.

---

### Post by owena1337 on 2013-08-27
> **sandyd said:**
> Does running
```

lsof -i :443
```
on the server produce anything?

Sorry, my bad, I didn't run the command with root *le sigh*. The output of that command gives me;

```
COMMAND    PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME/usr/sbin 2371     root    5u  IPv4  12792      0t0  TCP *:https (LISTEN)
/usr/sbin 2375 www-data    5u  IPv4  12792      0t0  TCP *:https (LISTEN)
/usr/sbin 2382 www-data    5u  IPv4  12792      0t0  TCP *:https (LISTEN)
/usr/sbin 2395 www-data    5u  IPv4  12792      0t0  TCP *:https (LISTEN)
/usr/sbin 2396 www-data    5u  IPv4  12792      0t0  TCP *:https (LISTEN)
/usr/sbin 2397 www-data    5u  IPv4  12792      0t0  TCP *:https (LISTEN)
/usr/sbin 2398 www-data    5u  IPv4  12792      0t0  TCP *:https (LISTEN)
/usr/sbin 2399 www-data    5u  IPv4  12792      0t0  TCP *:https (LISTEN)
/usr/sbin 2509 www-data    5u  IPv4  12792      0t0  TCP *:https (LISTEN)
/usr/sbin 2510 www-data    5u  IPv4  12792      0t0  TCP *:https (LISTEN)
/usr/sbin 2511 www-data    5u  IPv4  12792      0t0  TCP *:https (LISTEN)
/usr/sbin 2598 www-data    5u  IPv4  12792      0t0  TCP *:https (LISTEN)



```

As for running this command (**sudo nano /etc/apache2/ports.conf**) to see what the file contains, It only has;

```
# If you just change the port or add more ports here, you will likely also# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz


Listen 80


<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
Listen 443
</IfModule>


<IfModule mod_gnutls.c>
Listen 443
</IfModule>



```

I have a feeling I need to put something into that file. 

Thanks.

---

### Post by CharlesA on 2013-08-27
Run these please:

```
ls /etc/apache/sites-*
```

---

### Post by owena1337 on 2013-08-27
> **CharlesA said:**
> Run these please:

```
ls /etc/apache/sites-*
```

This did not work;
```
ls: cannot access /etc/apache/sites-*: No such file or directory
```

---

### Post by CharlesA on 2013-08-27
> **owena1337 said:**
> This did not work;
```
ls: cannot access /etc/apache/sites-*: No such file or directory
```

Whoops, it should be /etc/apache2/sites*

---

### Post by sandyd on 2013-08-27
> **owena1337 said:**
> Sorry, my bad, I didn't run the command with root *le sigh*. The output of that command gives me;

```
COMMAND    PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME/usr/sbin 2371     root    5u  IPv4  12792      0t0  TCP *:https (LISTEN)
/usr/sbin 2375 www-data    5u  IPv4  12792      0t0  TCP *:https (LISTEN)
/usr/sbin 2382 www-data    5u  IPv4  12792      0t0  TCP *:https (LISTEN)
/usr/sbin 2395 www-data    5u  IPv4  12792      0t0  TCP *:https (LISTEN)
/usr/sbin 2396 www-data    5u  IPv4  12792      0t0  TCP *:https (LISTEN)
/usr/sbin 2397 www-data    5u  IPv4  12792      0t0  TCP *:https (LISTEN)
/usr/sbin 2398 www-data    5u  IPv4  12792      0t0  TCP *:https (LISTEN)
/usr/sbin 2399 www-data    5u  IPv4  12792      0t0  TCP *:https (LISTEN)
/usr/sbin 2509 www-data    5u  IPv4  12792      0t0  TCP *:https (LISTEN)
/usr/sbin 2510 www-data    5u  IPv4  12792      0t0  TCP *:https (LISTEN)
/usr/sbin 2511 www-data    5u  IPv4  12792      0t0  TCP *:https (LISTEN)
/usr/sbin 2598 www-data    5u  IPv4  12792      0t0  TCP *:https (LISTEN)



```

As for running this command (**sudo nano /etc/apache2/ports.conf**) to see what the file contains, It only has;

```
# If you just change the port or add more ports here, you will likely also# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz


Listen 80


<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
Listen 443
</IfModule>


<IfModule mod_gnutls.c>
Listen 443
</IfModule>



```

I have a feeling I need to put something into that file. 

Thanks.

looks fine
looks like port 443 isnt being forwarded properly or is being blocked if it cant be accessed outside of your network.

---

### Post by owena1337 on 2013-08-28
Hmmm. I've checked to see if my ISP (Virgin Media :roll:) blocked port 443, however it has been clear that people have reported them open. I ran a port check on port 443 and it appeared as closed. If it is indeed blocked, would it be possible to change the port, and what port would be ideal if I was to change it?

**EDIT:** Would Ubuntu Server block this port for any reason?

---

### Post by SeijiSensei on 2013-08-28
You need to configure your router to accept incoming traffic on port 443 that arrives on the Internet-facing side of the router and forward it to port 443 of the server.  See if you can find your router at [portforward.com]("http://portforward.com") for details on the appropriate method for your device.

---

### Post by owena1337 on 2013-08-28
> **SeijiSensei said:**
> You need to configure your router to accept incoming traffic on port 443 that arrives on the Internet-facing side of the router and forward it to port 443 of the server.  See if you can find your router at [portforward.com]("http://portforward.com") for details on the appropriate method for your device.

Would this be necessary since it is inside a DMZ?

---

### Post by SeijiSensei on 2013-08-28
I don't know.  I never use DMZs.  Is there a reason why you cannot just put the server behind the router and forward port 443 to it?

---

### Post by owena1337 on 2013-08-28
Not really, it just saves placing each port one by one into the table, and since there is limited room, it'll fill up easily. Game ports especially are filling that table up too. The server is fine.

---

### Post by CharlesA on 2013-08-28
> **owena1337 said:**
> Not really, it just saves placing each port one by one into the table, and since there is limited room, it'll fill up easily. Game ports especially are filling that table up too. The server is fine.

Try it and see if that makes a difference. I don't use the DMZ either, so I just forward ports as needed.

Other than that, if you can access the https site locally, the local firewall should be fine, but run this anyway:

```
sudo iptables -l
```

---

### Post by owena1337 on 2013-08-28
> **CharlesA said:**
> Try it and see if that makes a difference. I don't use the DMZ either, so I just forward ports as needed.

Other than that, if you can access the https site locally, the local firewall should be fine, but run this anyway:

```
sudo iptables -l
```

iptables v1.4.12: unknown option "-l"
Try `iptables -h' or 'iptables --help' for more information.

---

### Post by CharlesA on 2013-08-28
> **owena1337 said:**
> iptables v1.4.12: unknown option "-l"
Try `iptables -h' or 'iptables --help' for more information.

Must be -L then. -.-

I guess that shows how often I actually check my iptables rules after they have been written. :p

---

### Post by owena1337 on 2013-08-28
> **CharlesA said:**
> Must be -L then. -.-

I guess that shows how often I actually check my iptables rules after they have been written. :p

Haha, at least it worked!

Output;

```
crash@s2:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
fail2ban-dovecot-pop3imap  tcp  --  anywhere             anywhere             mu                                                                             ltiport dports pop3,pop3s,imap2,imaps
fail2ban-pureftpd  tcp  --  anywhere             anywhere             multiport                                                                              dports ftp
fail2ban-ssh  tcp  --  anywhere             anywhere             multiport dport                                                                             s ssh


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


Chain fail2ban-dovecot-pop3imap (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere


Chain fail2ban-pureftpd (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere


Chain fail2ban-ssh (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
```

---

### Post by CharlesA on 2013-08-28
Firewall looks fine. If port 443 is still showing closed even after you have set up a rule in port forwarding, it's likely the problem is your ISP.

---

### Post by owena1337 on 2013-08-28
Right. So I found something very interesting. In Webmin I enabled SSL and gave the path to the certificate file I generated using openssl. After restarting my webserver, the following addresses I found, work...

[https://test.com:80]("https://s2.owenashurst.com:80/owncloud/index.php/apps/files") - Notice the ":80" at the end of the address? It works with that on.

[https://]("https://s2.owenashurst.com:80/owncloud/index.php/apps/files")test.com - This just times out.

I ought to mention this, In webmin I enabled SSL on the following config "[COLOR=#393939][FONT=arial]Handles the name-based server [/FONT][/COLOR][COLOR=#393939][FONT=arial]on address [/FONT][/COLOR]*[COLOR=#393939][FONT=arial]." which is the default config which also means that if I try and direct to "test.com" it will say "Bad Request" and ask me to use "https://test.com:80".

Any ideas?[/FONT][/COLOR]

---

### Post by CharlesA on 2013-08-28
You shouldn't be able to use https over port 80 unless the configuration is set to listen for https connections on port 80.

That doesn't make any sense.

EDIT: If I try to access my site via SSL on port 80, I get a lovely error message:

> Secure Connection Failed

An error occurred during a connection to charlesa.net:80.

SSL received a record that exceeded the maximum permissible length.

(Error code: ssl_error_rx_record_too_long)

  The page you are trying to view cannot be shown because the authenticity of the received data could not be verified.
  Please contact the website owners to inform them of this problem. Alternatively, use the command found in the help menu to report this broken site.

Normal HTTP and HTTPS work fine for me.

---

### Post by owena1337 on 2013-08-28
Well for some reason, it seems to work like that. However, [https://test.com](https://test.com) doesn't work when it should.. this is getting beyond the joke...

---

### Post by CharlesA on 2013-08-28
Do you have another box you can try following the guide again and see if the same thing occurs? I've always configured my web servers from scratch (with a lot of help), but this is beyond ridiculous.

---

### Post by owena1337 on 2013-08-28
To right. I don't have another box however I could try a virtual machine, but the amount of times I've gone through "The Perfect Server" is over 20 from previous screw ups :/

---

### Post by CharlesA on 2013-08-28
> **owena1337 said:**
> To right. I don't have another box however I could try a virtual machine, but the amount of times I've gone through "The Perfect Server" is over 20 from previous screw ups :/

Which guide were you using? Based off the name, I'm guessing it's this one: [http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3)

I glanced thru it and it looks ok. I haven't used apache in a long time, though.

My suggestion is to set up Apache for http and https manually and see if you still have the problem.

---

### Post by owena1337 on 2013-08-28
> **CharlesA said:**
> Which guide were you using? Based off the name, I'm guessing it's this one: [http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3)

I glanced thru it and it looks ok. I haven't used apache in a long time, though.

My suggestion is to set up Apache for http and https manually and see if you still have the problem.

That's the correct tutorial. And I've tried doing so, but they are all from 2009, 2008 and I have a feeling that it'll work with an up to date tutorial since things would have been added/changed with Apache since then.

---

### Post by CharlesA on 2013-08-28
Check this out:
[https://help.ubuntu.com/lts/serverguide/httpd.html](https://help.ubuntu.com/lts/serverguide/httpd.html)

Maybe that will help?

---

### Post by owena1337 on 2013-08-28
In the "HTTPs configuration" section, I have executed every single one of those commands, but yet it doesn't work.. Even after a server reboot :/

**EDIT**: Is "[COLOR=#333333][FONT=monospace]/etc/apache2/sites-available/default-ssl" [/FONT][/COLOR]supposed to just have two lines?

> <IfModule mod_ssl.c>
</IfModule>

---

### Post by CharlesA on 2013-08-28
What does default-ssl look like?

---

### Post by owena1337 on 2013-08-28
> **CharlesA said:**
> What does default-ssl look like?

Sorry, just edited my post with your answer before you posted, haha.

---

### Post by CharlesA on 2013-08-28
> **owena1337 said:**
> Sorry, just edited my post with your answer before you posted, haha.

Heh, nope. Do you have any other configuration files you were using for ssl?

---

### Post by owena1337 on 2013-08-28
Only default ones I have right now. Was that nope for the fact that the default-ssl shouldn't just have two lines, or?

---

### Post by CharlesA on 2013-08-28
> **owena1337 said:**
> Was that nope for the fact that the default-ssl shouldn't just have two lines, or?

Correct.

[http://askubuntu.com/questions/157293/i-need-a-file-etc-apache2-sites-available-default-ssl](http://askubuntu.com/questions/157293/i-need-a-file-etc-apache2-sites-available-default-ssl)

---

### Post by TheFu on 2013-08-29
> **owena1337 said:**
> Well for some reason, it seems to work like that. However, [https://test.com](https://test.com) doesn't work when it should.. this is getting beyond the joke...

You are listening on port 80, but have HTTPS enabled. Configuration error.
Listen on port 443 instead.


HTTP defaults to port 80.
HTTPS defaults to port 443.

If you do anything other than that, then URLs need to specify the port ... HTTPS on port 80 demands a URL with [https://server:80](https://server:80) because is it NON-STANDARD.

BTW, using a DMZ is really poor security practice ... er .... especially on a machine with the firewall setup like this machine has.  Even if forward 500 ports are forwarded, you can't "fill up" the router firewall table. 

Also, the "perfect server" setups make a working config, but not a secure config.

---

### Post by owena1337 on 2013-08-29
Well after some tinkering I managed to get it to work via [https://192.168.0.100/](https://192.168.0.100/). This successfully loads the index.html file I made in my /var/www folder while using SSL. The problem is that I cant access it if I replace "192.168.0.100" with my domain name.

This is my config via Webmin - [https://www.dropbox.com/s/jipxxabu049d74x/webmin%20apache%20config.png](https://www.dropbox.com/s/jipxxabu049d74x/webmin%20apache%20config.png)

---

### Post by TheFu on 2013-08-29
> **owena1337 said:**
> Well after some tinkering I managed to get it to work via [https://192.168.0.100/](https://192.168.0.100/). This successfully loads the index.html file I made in my /var/www folder while using SSL. The problem is that I cant access it if I replace "192.168.0.100" with my domain name.

This is my config via Webmin - [https://www.dropbox.com/s/jipxxabu049d74x/webmin%20apache%20config.png](https://www.dropbox.com/s/jipxxabu049d74x/webmin%20apache%20config.png)

Did you setup an external DNS provider?
For local-only access, you have lots of options 
* router-based DNS (dd-wrt does this)
* /etc/hosts entry. This is really easy for a small network.
* internal DNS ---- running DNS is a very different topic than this. There are how-tos.
* external DNS - pay someone like DynDNS.com, No-IP.com, there are 50 others.

Running a secure DNS on the internet is hard. I have experience and will always elect to pay someone else, with DNS expertise, to do this for me and my companies.  DNS is the 2nd most-hacked service on the internet. Pay someone else, please.

---

### Post by owena1337 on 2013-08-29
Like I've said, I have a DNS. It's currently registered with GoDaddy but I'm moving it over to OVH sometime when I get a chance. the domain points to my external IP of my home. I can access ALL my sites/files on my homeserver fine WITHOUT SSL. Using SSL only works internally rather than externally.

---

### Post by TheFu on 2013-08-29
> **owena1337 said:**
> Like I've said, I have a DNS. It's currently registered with GoDaddy but I'm moving it over to OVH sometime when I get a chance. the domain points to my external IP of my home. I can access ALL my sites/files on my homeserver fine WITHOUT SSL. Using SSL only works internally rather than externally.

Sorry, I didn't re-read the thread before posting.

Can you telnet to port 443 on your public IP?
Can you telnet to port 443 on your public DNS name?

You'll see a connection, but no response, no text. Still, the connection will happen.

I'd draw a picture of the network and start verifying the packets traverse where I think they do all along the way.
* router pub interface
* router priv interface
* server input interface
* firewall on srv
* apache logs

There are logs for all those things. You might need to turn up the verbosity, but there are logs.

---

### Post by CharlesA on 2013-08-29
> **TheFu said:**
> 
* /etc/hosts entry. This is really easy for a small network.

Running a secure DNS on the internet is hard. I have experience and will always elect to pay someone else, with DNS expertise, to do this for me and my companies.  DNS is the 2nd most-hacked service on the internet. Pay someone else, please.

I use the hosts file when I am doing testing, otherwise internal DNS works wonders.

+1 to paying someone to deal with your DNS. I recently ran into hell trying to get DKIM working with my domain registrar and their (simple) web-based form. They do not support AAAA records either, so I'm trying to find a DNS provider that is cheap and has good features, which seems to be mutually exclusive.

> **TheFu said:**
> 
Can you telnet to port 443 on your public IP?
Can you telnet to port 443 on your public DNS name?

You'll see a connection, but no response, no text. Still, the connection will happen.

I'd draw a picture of the network and start verifying the packets traverse where I think they do all along the way.
* router pub interface
* router priv interface
* server input interface
* firewall on srv
* apache logs

There are logs for all those things. You might need to turn up the verbosity, but there are logs.

Good method. I've used telnet to troubleshoot mail servers but it works wonders for web servers too.

I still think the problem has something to do with port forwarding on the router. If your router has a web interface, is it accessed over port 80 or port 443?

---

### Post by owena1337 on 2013-08-29
> **TheFu said:**
> Sorry, I didn't re-read the thread before posting.

Can you telnet to port 443 on your public IP?
Can you telnet to port 443 on your public DNS name?

You'll see a connection, but no response, no text. Still, the connection will happen.

I'd draw a picture of the network and start verifying the packets traverse where I think they do all along the way.
* router pub interface
* router priv interface
* server input interface
* firewall on srv
* apache logs

There are logs for all those things. You might need to turn up the verbosity, but there are logs.

I see what you mean. I SSH'd into a Linux Server in France (hosted by OVH) and attempted the following command "telnet <my domain here> 443" (Obviously replacing with my domain). Unfortunately it timed out. Using the same command on my local computer running Windows 7, it seemed to have said "Connection to host lost" instead of timing out.

There is no indication in my Apache2 error/access logs for this connection.

---

### Post by CharlesA on 2013-08-29
That means the connection isn't even getting to the server. At this point it would be a good idea to diagram how this is supposed to work but, at this point, it really seems like your ISP is blocking port 443.

Have you tried forwarding port 443 to something like port 8080 and trying to connect via [https://somedomain:8080](https://somedomain:8080) ? That will tell you if the port forwarding rules are correct.

---

### Post by owena1337 on 2013-08-29
> **CharlesA said:**
> That means the connection isn't even getting to the server. At this point it would be a good idea to diagram how this is supposed to work but, at this point, it really seems like your ISP is blocking port 443.

Have you tried forwarding port 443 to something like port 8080 and trying to connect via [https://somedomain:8080](https://somedomain:8080) ? That will tell you if the port forwarding rules are correct.

How would I go about changing the port to something else? (I'd rather ask than screw everything up).

**EDIT:** Just tried telnet into my server from the server it self using the domain name. I don't know why but I was curious. Here are my results;

```
telnet> open test.com 443
Trying 192.168.0.100...
Connected to test.com.
Escape character is '^]'.
Connection closed by foreign host.
```

---

### Post by owena1337 on 2013-08-29
Derp. It was a router issue. Port 443 was forwarded to another IP which was my Raspberry Pi. I'm sorry for wasting your time... In einsight, at least this guide covered most of the steps to track down the issue for anyone else.

Thanks everyone for your continued support.

---

### Post by CharlesA on 2013-08-29
Glad you got it sorted. Don't forget to mark the thread as SOLVED from thread tools. :)

---

### Post by sandyd on 2013-08-29
> **CharlesA said:**
> I use the hosts file when I am doing testing, otherwise internal DNS works wonders.
+1 to paying someone to deal with your DNS. I recently ran into hell trying to get DKIM working with my domain registrar and their (simple) web-based form. They do not support AAAA records either, so I'm trying to find a DNS provider that is cheap and has good features, which seems to be mutually exclusive.
**Rage4 (includes geolocation!), dnsimple, dnsmadeeasy ($34/year), namecheap, zoneedit, dns.he.net. Pretty sure edgedirector is too expensive**


.

---

### Post by CharlesA on 2013-08-29
> **sandyd said:**
> .

Thank you!

---

### Post by 2Stoned on 2013-08-31
> **owena1337 said:**
> Derp. It was a router issue. Port 443 was forwarded to another IP which was my Raspberry Pi. I'm sorry for wasting your time... In einsight, at least this guide covered most of the steps to track down the issue for anyone else.

Thanks everyone for your continued support.

I knew it was a port issue :P

---

