---
title: "apache works locally but not globally"
date: 2010-05-21
forum: Server Platforms
---

### Post by evaristegalois on 2010-05-21
I set up apache (apache2) to create a moodle server, but I can't get it to work globally. I don't know much about setting up a server. Here is the rub:

[http://192.168.0.150](http://192.168.0.150) works beautifully (locally of course), showing me the index page at /var/www

[http://mysite.homelinux.org](http://mysite.homelinux.org) (my dyndns) or [http://96.49.75.14](http://96.49.75.14) (my current IP address) doesn't work (either locally or globally).

ssh works well globally, i.e. ssh -l myname mysite.homelinux.org works.

pinging mysite.homelinux.org works without a problem.

Ports 22, 80 and 443 are open on my router (checked my router's settings), and are set up this way:

Virtual Server HTTP	192.168.0.150	TCP 80/80	always
Virtual Server HTTPS	192.168.0.150	TCP 443/443	always
Virtual Server SSH	192.168.0.150	TCP 22/22       always

Any suggestions?

---

### Post by lisati on 2010-05-21
Some ISPs block port 80, even if you open it up on your router and your server.

To check if port 80 can be seen from outside your network, you can visit the [Shields Up]("https://www.grc.com/x/ne.dll?bh0bkyd2") web site.

---

### Post by evaristegalois on 2010-05-21
Thanks. That's the problem. I guess I have to talk my ISP provider.

---

### Post by evaristegalois on 2010-05-21
All right. I went through ShieldsUP and you were right, they can ping me, but they can't get through at port 80. So I talked to my internet service provider, Shaw, and they said:

> there is nothing we can assist you with - we do not block ports and this is strictly router related - 
let me confirm -
we are not blocking port 80- 
if it is not working it may be router related - this is not supported by shaw.


So, my Virtual Servers List on my router points port 80 to 192.168.0.150, the filter for port 80 on the router is disabled, my ISP doesn't block port 80. I am wondering if there is a firewall on ubuntu 10.4 (that I certainly didn't install) that may be blocking port 80. How would I find out?

Someone recommended to run "netstat -nap" and look for apache in the output. There was nothing---is that a problem?

---

### Post by arrrghhh on 2010-05-21
By default, UFW is installed but not enabled.  So if UFW is disabled, then no (you can check by running "sudo ufw status") - there should be no firewall blocking on the Ubuntu side of things.

Can you try to skip your router as a test?  Plug the server straight to the internet connection to see if then port 80 is available to the outside world?

---

### Post by evaristegalois on 2010-05-21
Thanks for the hint, but sudo ufw status yields `inactive'.

I want to summarize this problem, because above I am giving a lot of unnecessary details (I believe). I am on my work computer now and I can ping my home computer at [http://ping.eu/](http://ping.eu/) simply pinging

myname.homelinux.org

However, when I do the port check on the same website for port 80 it tells me that port 80 is closed.

I did not mess with the apache2 conf files except for adding 

# added servername to avoid the could not determine fqdn error
ServerName myname.homelinux.org

to /etc/apache2/apache2.conf to avoid apache2 complaining about not finding a fqdn.

After doing this,

apache2ctl start

works without an error message, but 

# netstat -l | grep http

doesn't yield anything, and apparently it should give me something like

tcp 0 0 *:http *:* LISTEN

ports.conf has

NameVirtualHost *:80
Listen 80

in it, so apache2 should be listening to port 80. As mentioned above, my router does not filter port 80 and the port is forwarded to 192.168.0.150 (which, locally, takes me to the apache website telling me that apache is working).

My hunch is that I still haven't set up apache correctly to listen to port 80, but I don't know what to do next. I am also confused about hostnames, servernames, domainnames etc. My hostname (in /etc/hostname) is not the same as the `myname' in myname.homelinux.org, but does it need to be?

---

### Post by arrrghhh on 2010-05-21
OK a couple of things.  If you're running the test again from your work PC - then it's testing the port connectivity to your work PC, not your server @ home.

However, that netstat command should definitely yeild *something* - I get 2 results, http-alt and https.  However, I didn't do any of your configuration changes.  The hostname certainly doesn't have to match the domain name, I didn't even configure a ServerName in the apache2.conf, but it probably does complain when I restart apache.

So if you run

# ps -A |grep apache

Do you get anything?  Is apache even running is what I'm trying to get at.  If the netstat command came back empty handed, it probably isn't.

This doesn't make sense as to why you can access apache thru your LAN however... the IP on your server is configured as static not dynamic, yes?  Also, how are you pointing your outside domain name to your server at home?  Do you have a static WAN IP as well, or do you use a dynamic DNS service?  Are there other services you have facing the WAN that are working?

---

### Post by tgalati4 on 2010-05-21
I presume that you rebooted your router after port-forwarding.

---

### Post by evaristegalois on 2010-05-22
I restarted my computer, to no effect.

When I checked my port from work, I checked my home computer's port, not my work computer's port. It's easy to do at [http://ping.eu/port-chk/](http://ping.eu/port-chk/), I just entered myname.homelinux.org (which by dyndns gets forwarded to my temporary home computer IP address) and port 80. It checked and the port is closed. When I ping myname.homelinux.org at [http://ping.eu/ping/](http://ping.eu/ping/), all goes well.

Someone suggested I should plug my ethernet cable into the modem instead of the router. That didn't work, as it totally cut off my internet connection.

netstat -l outputs quite a bit of stuff, but nothing relating to http or apache (I was ambiguous on this point). Here is the first part of the output:

> Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:www                   *:*                     LISTEN     
tcp        0      0 *:58355                 *:*                     LISTEN     
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 localhost:postgresql    *:*                     LISTEN     
tcp        0      0 *:smtp                  *:*                     LISTEN     
tcp        0      0 *:nfs                   *:*                     LISTEN     
tcp        0      0 *:33825                 *:*                     LISTEN     
tcp        0      0 *:41002                 *:*                     LISTEN     
tcp        0      0 localhost:mysql         *:*                     LISTEN     
tcp        0      0 *:sunrpc                *:*                     LISTEN     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN     
tcp6       0      0 localhost:postgresql    [::]:*                  LISTEN     
tcp6       0      0 [::]:microsoft-ds       [::]:*                  LISTEN     
tcp6       0      0 [::]:netbios-ssn        [::]:*                  LISTEN     
udp        0      0 *:39102                 *:*                                
udp        0      0 *:42955                 *:*                                
udp        0      0 *:39768                 *:*                                
udp        0      0 *:mdns                  *:*                                
udp        0      0 *:sunrpc                *:*                                
udp        0      0 *:882                   *:*                                
udp        0      0 *:nfs                   *:*                                
udp        0      0 *:33282                 *:*                                
udp        0      0 gustav.local:netbios-ns *:*                                
udp        0      0 *:netbios-ns            *:*                                
udp        0      0 gustav.loca:netbios-dgm *:*                                
udp        0      0 *:netbios-dgm           *:*                                
                               

Here is the output for ps -A | grep apache

> 2434 ?        00:00:00 apache2
 2436 ?        00:00:00 apache2
 2437 ?        00:00:00 apache2
 2438 ?        00:00:00 apache2
 2439 ?        00:00:00 apache2
 2440 ?        00:00:00 apache2


---

### Post by evaristegalois on 2010-05-23
I just found out that there is a tiny button I needed to enable on the router, which I failed to do. Problem solved. Many thanks!

---

