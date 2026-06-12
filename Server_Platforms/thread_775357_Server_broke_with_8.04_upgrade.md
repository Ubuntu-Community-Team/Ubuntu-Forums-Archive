---
title: "Server broke with 8.04 upgrade"
date: 2008-04-30
forum: Server Platforms
---

### Post by R.Bucky on 2008-04-30
I am running an apache web server (Drupal). I upgraded to 8.04. When I try and visit my domain, Firefox comes back with nothing. I can view my pages on localhost no problem. I have checked my root at .htaccess, ports onmy router and other conf files (#80), and double checked everything that I can think of. What gives?

I checked /var/log/apache2 and saw this in the error.log:
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5 with Suhosin-Patch configured -- resuming normal operations
[Tue Apr 29 22:08:31 2008] [notice] caught SIGWINCH, shutting down gracefully


I also noticed my terminal header is also displaying my FQDN, long and short. 

Any ideas?

Mark
[http://buckyspalace.net](http://buckyspalace.net)

---

### Post by windependence on 2008-04-30
> **R.Bucky said:**
> I am running an apache web server (Drupal). I upgraded to 8.04. When I try and visit my domain, Firefox comes back with nothing. I can view my pages on localhost no problem. I have checked my root at .htaccess, ports onmy router and other conf files (#80), and double checked everything that I can think of. What gives?

I checked /var/log/apache2 and saw this in the error.log:
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5 with Suhosin-Patch configured -- resuming normal operations
[Tue Apr 29 22:08:31 2008] [notice] caught SIGWINCH, shutting down gracefully


I also noticed my terminal header is also displaying my FQDN, long and short. 

Any ideas?

Mark
[http://buckyspalace.net](http://buckyspalace.net)

Sounds like the firewall has been activated after your upgrade. Check to make sure the port is open.

-Tim

---

### Post by gtdaqua on 2008-04-30
telnet to your webserver on port 80. if not, then its a firewall issue.

```

telnet webserver-ip 80

```

---

### Post by R.Bucky on 2008-04-30
After applying the telnet command in terminal, here is what I received: 
"telnet: could not resolve webserver-ip/80: Name or service not known
"
Now what? I am searching for information on a default firewall install or something like that. But, y router is ok and configured as well as opening up the corresponding port in the ports.conf.

---

### Post by R.Bucky on 2008-04-30
I can access my website using my port number after the address. but, not without the port. I never had to do that before. What is the scoop on that? [http://buckyspalace.net:10259](http://buckyspalace.net:10259)

---

### Post by windependence on 2008-04-30
> **R.Bucky said:**
> After applying the telnet command in terminal, here is what I received: 
"telnet: could not resolve webserver-ip/80: Name or service not known
"
Now what? I am searching for information on a default firewall install or something like that. But, y router is ok and configured as well as opening up the corresponding port in the ports.conf.

Try one thing yet just to be sure. Go to [www.canyouseeme.org](www.canyouseeme.org) and test your port 80 to see if it's open. If not, you either have your firewall up or your ISP is blocking it.

-Tim

---

### Post by x-unknown on 2008-04-30
You were supposed to substitute the IP address of your webserver for webserver-ip. Try that and see if the webserver is responding.

---

### Post by R.Bucky on 2008-04-30
Duh! Trying that when I get home. Well, I found out that port 80 was blocked. so, I changed ports to another non-used port in the higher range and configured my system for that port. But, no dice. I may end up going back to 7.10 if this keeps up. I should have known.

---

### Post by R.Bucky on 2008-04-30
Well, I replaced the apache2.conf with my backup file. The server functions now, but the mailserver is dead. I no longer receive email from my site, but Drupal is telling me that a mail was sent. Back to square one of figuring out the FQDN entries. 

I am still unclear what is the proper syntax for my FQDN. I think that it goes [ip address] [long name] [short name]. The problem is that I do not know what my long name would be. When I type in "hostname" to terminal, it provides me with two line: 127.0.0.1 localhost and mark.buckyspalace.net. Huh?

Can anyone help with the mailserver issue or recommend another post???

---

### Post by sp00n on 2008-05-02
I am having the same problem - what firewall will have been installed and configured during the upgrade, and how do i open the ports?

---

### Post by sp00n on 2008-05-02
I have enabled ufw and opened the ports i need to serve pages through with the following:

```
sudo ufw enable
sudo ufw allow 80
```

but i still can neither serve pages nor telnet to port 80, i get the following from telnet:

```
telnet: Unable to connect to remote host: Connection refused
```

---

### Post by sp00n on 2008-05-02
i upgraded to hardy via update-manager, and when prompted, kept all my config files for apache / mysql etc. So all my ports.conf, 000-default, httpd.conf files are as before, but my server does not respond to any connection attempts to any of the ports i am connecting through. this is seriously affecting my business. HELP!

---

### Post by sp00n on 2008-05-02
i have no access as localhost either, unlike the previous poster.

---

### Post by windependence on 2008-05-02
> **sp00n said:**
> i have no access as localhost either, unlike the previous poster.

This is gonna sound funky but is Apache running? If you start top in a terminal can you see httpd processes?

-Tim

---

### Post by windependence on 2008-05-02
> **sp00n said:**
> I have enabled ufw and opened the ports i need to serve pages through with the following:

```
sudo ufw enable
sudo ufw allow 80
```

but i still can neither serve pages nor telnet to port 80, i get the following from telnet:

```
telnet: Unable to connect to remote host: Connection refused
```

What happens when you paste 127.0.0.1:80 in your browser on the server machine?

-Tim

---

### Post by andguent on 2008-05-03
Just another troubleshooting option to try:
```
netstat -ntlp
```
That should list all programs listening to TCP ports. Apache should be listed there with a line that looks something like:
**tcp        0      0 192.168.1.2:80       0.0.0.0:*               LISTEN     14717/apache2**

If this does NOT show, then no one will get to your website. Also, if the IP address listed there in column 4 is "127.0.0.1" or similar, that is no good either. It shouldn't be, but something else to check. It MUST have that :80 on the end of it.

If that is all fine, then do the telnet test from another computer on the same LAN. This is important that it is not done from outside the router, as we want to test the server's personal firewall. If telnet gives you ANY garbage at all or a 'connected' message, you are good. It will say "connection refused" if a firewall is enabled incorrectly.

If all is still good, then confirm your port forward settings on your router. Verify that the IP address it points to is the same that your server thinks it is. Make sure the server hasn't changed IPs on you.

If everything still looks good, then I would second the motion above: Using [http://www.canyouseeme.org/](http://www.canyouseeme.org/) or another more powerful scanner Shields Up from grc.com. Verify either/both of them can see your port 80 open.

Please post back as to how far you got through the tests.

---

### Post by LordCrank on 2008-05-12
I am having similar issues, however it is with a server that I do not have direct access to.  The server responds to pings, but gives a "connection refused" message when trying to access it through ssh or when trying to get to the web pages it is supposed to serve.  I am going to be paying for a kvm for 24 hours, but I don't know what would have caused it to stop responding like it has.

Would upgrading to 8.04 have turned on any sort of software firewall?
If not, would it have disabled apache and sshd from starting when the computer boots?
I don't recall having set up xinetd, but I'm not entirely certain it's not there.  Would the update have somehow disabled xinetd?

I chose for all options to keep any modified configuration files, so unless the location that the files are stored in changed or the syntax needed in files has changed it shouldn't be an issue of them being configured incorrectly.

---

### Post by andguent on 2008-05-12
Hardy introduced the [ufw]("https://wiki.ubuntu.com/UbuntuFirewall") to the basic setup. Type 'ufw disable' to test if that is causing your problems. Test with my connectivity checking steps above too. 

Either way, you need to get physically to the box, or find another way of connecting to it.

---

