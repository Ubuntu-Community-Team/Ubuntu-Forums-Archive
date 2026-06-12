---
title: "URL-traffic redirect to multiple internal IPs"
date: 2012-08-27
forum: Server Platforms
---

### Post by aaron.kyle on 2012-08-27
THE SETUP:

I have an Ubuntu server on Amazon's EC2 with public IP of (ex.) 123.45.67.89

I have set up OpenVPN so that all incoming traffic passes from my public IP through the EC2 server to a local server hosted at an internal IP address of: 10.8.0.1.  This local server ALWAYS connects to OpenVPN with the same internal IP.

I also connect a second local server to OpenVPN with a static internal IP of 10.8.0.2.

THE CHALLENGE

With the current configuration, all internet traffic coming to the public IP is re-directed only to the internal IP 10.8.0.1.  However, I have 2 URL domain names (ex. myname1.com and myname2.com) and would like to re-direct traffic based on domain name to one or the other internal IP, as follows:

myname1.com > 10.8.0.1
myname2.com > 10.8.0.2


I have tried things like adding both internal IPs to an OpenVPN up.sh script so that (theoretically) port 80 traffic could be sent to each internal IP, then setting up VirtualHosts under Apache.  I can't get the URL routing to work though.  

The apache config that I tried is:

[HTML]
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ProxyRequests off 
        <Proxy *> 
          Order deny,allow 
          Allow from all 
        </Proxy> 
        <Location /> 
          Order allow,deny 
          Allow from all 
        </Location> 
</VirtualHost>
<VirtualHost *:80>
        ServerName myname1.com
        ProxyRequests off 
        <Proxy *> 
          Order deny,allow 
          Allow from all 
        </Proxy> 
        <Location /> 
          Order allow,deny 
          Allow from all 
        </Location> 
        ProxyPreserveHost on
        ProxyPass / http://10.8.0.1/
        ProxyPassReverse / http://10.8.0.1/
</VirtualHost>
<VirtualHost *:80>
        ServerName www.myname1.com
        ProxyRequests off 
        <Proxy *> 
          Order deny,allow 
          Allow from all 
        </Proxy> 
        <Location /> 
          Order allow,deny 
          Allow from all 
        </Location> 
        ProxyPreserveHost on
        ProxyPass / http://10.8.0.1/
        ProxyPassReverse / http://10.8.0.1/
</VirtualHost>
<VirtualHost *:80>
        ServerName myname2.com
        ProxyRequests off 
        <Proxy *> 
          Order deny,allow 
          Allow from all 
        </Proxy> 
        <Location /> 
          Order allow,deny 
          Allow from all 
        </Location> 
        ProxyPreserveHost on
        ProxyPass / http://10.8.0.2/
        ProxyPassReverse / http://10.8.0.2/
</VirtualHost>
<VirtualHost *:80>
        ServerName www.myname2.com
        ProxyRequests off 
        <Proxy *> 
          Order deny,allow 
          Allow from all 
        </Proxy> 
        <Location /> 
          Order allow,deny 
          Allow from all 
        </Location> 
        ProxyPreserveHost on
        ProxyPass / http://10.8.0.2/
        ProxyPassReverse / http://10.8.0.2/
</VirtualHost>

[/HTML]

Does anyone have suggestions for what I should be doing to get this working, or where my errors might be?  Thanks in advance for your help!

---

### Post by sandyd on 2012-08-27
I dont know about apache, but this has worked for me in nginx.

make sure /etc/nginx/sites-enabled is clean (no files inside, if there are, delete them)

```

sudo service apache2 stop
sudo apt-get install nginx
sudo rm /etc/nginx/sites-enabled/*
sudo nano /etc/nginx/sites-enabled/default.conf

```

copy and paste this
```

server {
        listen *:80;
        server_name myname1.com www.myname1.com;
        port_in_redirect off;
        error_log off;
        real_ip_header X-Forwarded-For;

	location / {
		proxy_pass        http://10.8.0.1;
		proxy_set_header  X-Real-IP  $remote_addr;
		proxy_redirect off;
		proxy_buffering off;
		proxy_set_header Host $host;
		proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
	}
}
server {
        listen *:80;
        server_name myname2.com www.myname2.com;
        port_in_redirect off;
        error_log off;
        real_ip_header X-Forwarded-For;

	location / {
		proxy_pass        http://10.8.0.2;
		proxy_set_header  X-Real-IP  $remote_addr;
		proxy_redirect off;
		proxy_buffering off;
		proxy_set_header Host $host;
		proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
	}
}

```

Restart nginx
```

sudo service nginx restart

```

IF it works, and you want to disable apache permantly,
```
sudo apt-get isntall chkconfig
sudo chkconfig apache2 off
```

Turn apache back on (if needed)
```
sudo chkconfig apache2 on
```

---

### Post by aaron.kyle on 2012-08-27
Thanks Sandyd!  Your quick response is well appreciated.

From what I can gather from your reply and and some basic web browsing, in order to use nginx I would have to run it as an apache replacement?  That is, I would have to migrate all programmes using apache to run with nginx?  Seems that if I have a site running multiple programmes all configured to Apache, that would take a lot more technical know-how that I have.  Or am I just overly-fearful?

UPDATE:

Apparently the nginx config also was not able to pass URL domain name traffic to my different internal IPs.  I no matter which URL domain name I enter, traffic still goes to 10.8.0.1.  Thus, the issue may not be with Apache, but instead with how OpenVPN is configured.  I'd still love any further guesses on how to achieve my objective of name-based IP redirects.   I'll keep looking into the question and will report what I find.

Thanks again!

---

### Post by aaron.kyle on 2012-08-27
Here's a person who was attempting something similar:

[http://serverfault.com/questions/282869/multiple-internal-ips-running-on-one-external-ip?rq=1](http://serverfault.com/questions/282869/multiple-internal-ips-running-on-one-external-ip?rq=1)

So my failed re-direction must an incorrect configurations somewhere other than apache2 or nginx.. otherwise this would be working.  I now suspect the issue is either in my OpenVPN config (bridged connection) or with iptables .. something.  Unless I am missing something very simple.


Any further help and insight would be appreciated!

UPDATE:

I am cataloging a few similar thread that seem to address the same issue.  I have yet tried to implement these solutions:

1) [http://serverfault.com/questions/215113/forward-differing-hostnames-to-different-internal-ips-through-nat-router?rq=1](http://serverfault.com/questions/215113/forward-differing-hostnames-to-different-internal-ips-through-nat-router?rq=1)

... have Nginx running on this server with the following configuration file:

```

server {
    listen *:80;
    location / {
        proxy_pass    http://$host;
    }
}

```

What this appears to do is proxy the request to the same host. But here's the trick, in my /etc/hosts file I will map all of the domains to their internal IPs.


```
182.168.0.110 example1.com
182.168.0.120 example2.com
182.168.0.130 foo.example2.com
182.168.0.140 bar.example2.com
```

So the Reverse Proxy server will route the requested host to the same host, but at this point it should look up the local hosts file, and map that to the internal IP address. It also means I can "set and forget" the Nginx configuration file.

A potential problem is if a local hostname has not been configured, then the Reverse Proxy will send the request back out to the Internet. However, I think NAT will stop this from getting stuck in an infinite loop.


2) [http://serverfault.com/questions/324808/how-to-properly-use-virtualhost-and-mod-proxy-together-for-different-incoming-do?rq=1](http://serverfault.com/questions/324808/how-to-properly-use-virtualhost-and-mod-proxy-together-for-different-incoming-do?rq=1)


... add all of your domain names to your /etc/hosts file with the IP address they resolve to - I have seen that problem before as well... - not necessarily the subdomains - but the root domains at least



3) [http://serverfault.com/questions/253830/port-forwarding-with-iptables-is-not-working?rq=1](http://serverfault.com/questions/253830/port-forwarding-with-iptables-is-not-working?rq=1)

... tell internal clients to access the server via its internal IP address. Alternatively, you can configure a "hairpin NAT" by adding a couple more iptables rules, as follows:

```
iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -d 192.168.1.254 -p tcp \
    --dport 80 -j SNAT --to-source $INT_IP

iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -d 192.168.1.254 -p tcp \
    --dport 22 -j SNAT --to-source $INT_IP
```

where $INT_IP is the router's internal IP address (e.g. 192.168.1.1). With these rules, connections from internal clients to the external IP address will flow through the router. It is best to avoid doing hairpin NAT whenever possible, since it is a rather inefficient use of network and router system resources.

---

### Post by SeijiSensei on 2012-08-28
How are the <VirtualHost> containers set up on the destination servers?  They should have ServerName directives that match the URL server names you use from the outside.  You might also want to include entries in each server's /etc/hosts that link the local IP address to the ServerName.

What do you see in /var/log/apache2/access.log and error.log on the hosts with the websites?  Do you see the requests arrive from the proxy?  Any errors?

---

### Post by aaron.kyle on 2012-08-29
Thanks, SeijiSensei, for helping me to think through this one.

In regard to the <VirtualHost> containers; are you referring to the  client.conf files? They read as follows:

```

# Specify that we are a client and
# will be pulling certain config file directives
# from the server.
client

# Use the same setting as you are using on
# the server.
;dev tap
dev tun

# Windows needs the TAP-Win32 adapter name
# from the Network Connections panel
# if you have more than one.  On XP SP2,
# you may need to disable the firewall
# for the TAP adapter.
;dev-node MyTap

# Are we connecting to a TCP or
# UDP server?  Use the same setting as
# on the server.
;proto tcp
proto udp

# The hostname/IP and port of the server.
remote 12.34.56.78 1194
;remote my-server-2 1194

## NOTE: I changed the IP numbers here for security, but my public IP was given correctly.

# Choose a random host from the remote
# list for load-balancing.  Otherwise
# try hosts in the order specified.
;remote-random

# Keep trying indefinitely to resolve the
# host name of the OpenVPN server.  Very useful
# on machines which are not permanently connected
# to the internet such as laptops.
resolv-retry infinite

# Most clients don't need to bind to
# a specific local port number.
nobind

# Downgrade privileges after initialization (non-Windows only)
;user nobody
;group nobody

# Try to preserve some state across restarts.
persist-key
persist-tun

# If you are connecting through an
# HTTP proxy to reach the actual OpenVPN
# server, put the proxy server/IP and
# port number here.  See the man page
# if your proxy server requires
# authentication.
;http-proxy-retry # retry on connection failures
;http-proxy [proxy server] [proxy port #]

# Wireless networks often produce a lot
# of duplicate packets.  Set this flag
# to silence duplicate packet warnings.
;mute-replay-warnings

# SSL/TLS parms.
# See the server config file for more
# description.  It's best to use
# a separate .crt/.key file pair
# for each client.  A single ca
# file can be used for all clients.
#remote-cert-tls server
ca /etc/openvpn/folder/ca.crt
cert /etc/openvpn/folder/clientX.crt
key /etc/openvpn/folder/clientX.key

##NOTE: I use client1 for server1 and client2 for server2; i.e. different dh certs/keys.

# Verify server certificate by checking
# that the certicate has the nsCertType
# field set to "server".  This is an
# important precaution to protect against
# a potential attack discussed here:
#  http://openvpn.net/howto.html#mitm
#
# To use this feature, you will need to generate
# your server certificates with the nsCertType
# field set to "server".  The build-key-server
# script in the easy-rsa folder will do this.
ns-cert-type server

# If a tls-auth key is used on the server
# then every client must also have the key.
#tls-auth ta.key 1

# Select a cryptographic cipher.
# If the cipher option is used on the server
# then you must also specify it here.
;cipher x

# Enable compression on the VPN link.
# Don't enable this unless it is also
# enabled in the server config file.
comp-lzo

# Set log file verbosity.
verb 3

# Silence repeating messages
;mute 20

# Use this for windows PC
;route-method exe
;route-delay 2
```

When you say that my client servers should have have ServerName directives that match the URL server names you use from the outside, is that accomplished with the line:

```
# The hostname/IP and port of the server.
remote 12.34.56.78 1194
```

Also, when you write: "You might also want to include entries in each server's /etc/hosts that link the local IP address to the ServerName."  Could you please give an example entry for how to create such linkages?

In /var/log/apache2/access.log on server 2,  I see no entries being created when I try to access the site from [http://site2.com](http://site2.com).  (server 1 is a mac mini, and I haven't done my homework on if it is using apache or how to check this log, but it is certainly receiving traffic (it's getting traffic for both of my two URL domain names).  I do, however, see entries being created when I navigate directly to the internal ip ([http://10.8.0.2](http://10.8.0.2)).

In error.log, it's the same story.  My output when connecting using the internal IP is:

```
[Wed Aug 29 08:07:07 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.2 with Suhosin-Patch configured -- resuming normal operations
[Wed Aug 29 08:44:06 2012] [error] [client 10.8.0.2] File does not exist: /var/www/favicon.ico
```

Any ideas?

Thanks again!! I really appreciate all the help to figure this out!

---

### Post by SeijiSensei on 2012-08-29
I thought you were using Apache mod_proxy on the externally-visible server to funnel requests back to Apache servers behind it.  If you have switched to nginx, then I can't help with that. 

In the all-apache scenario, the outside-facing box would have <VirtualHost> containers for each ServerName configured to pass requests back to the actual servers.  On the back end servers, you'd need a <VirtualHost> container with an identical ServerName to the one sent to the external facing host.

---

### Post by aaron.kyle on 2012-08-29
Thank you SeijiSensei.

To clarify - I am not using nginx.  I tried out the solution that Sandyd proposed, but the resulting behavior was the same as with Apache.  Since I am very new to working with servers, and since all of my web software is configured to work with Apache, I decided not to open a new can of worms by switching to nginx.

I am still not very clear about what you mean in terms of <VirtualHost> containers for the outside facing box.  I thought that you were referring to the client.conf files where I tell each of the servers how to connect to the EC2 openvpn server.   I'll do my homework and report back soon.

Thanks again for all your help!

---

### Post by SeijiSensei on 2012-08-29
I'm talking about the <VirtualHost> containers that you describe in your original post.  

On the externally facing server you'd have something like:
```

<VirtualHost *:80>
     ServerName  server1.example.com
     ProxyPass / http://10.8.0.1/
     ProxyPassReverse / http://10.8.0.1/
</VirtualHost>

```

On 10.8.0.1, you'd have
```

<VirtualHost *:80>
     ServerName server1.example.com
     DocumentRoot /path/to/the/website
     [etc.]
</VirtualHost>

```

---

### Post by aaron.kyle on 2012-08-30
Dear SeijiSensei,

Thank you once again for your time and your help.

As you suggested, I edited the httpd.conf file on my ubuntu home server on internal IP 10.8.0.2.  Unfortunately, my attempts did not result in allowing external traffic to reach my internal server.  My attempts were as follows: 

```
Listen 10.8.0.2:80 
NameVirtualHost 10.8.0.2:80 

<VirtualHost *:80> 
     ServerName site2.com 
     DocumentRoot /var/www/ 
</VirtualHost> 
<VirtualHost *:80> 
     ServerName www.site 2.com 
     DocumentRoot /var/www/ 
</VirtualHost> 
```

I then executed the command

```
apachectl -k graceful 
```

With the following output:

```
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName 
[Wed Aug 29 21:17:02 2012] [warn] _default_ VirtualHost overlap on port 80, the first has precedence 
[Wed Aug 29 21:17:02 2012] [warn] _default_ VirtualHost overlap on port 80, the first has precedence 
[Wed Aug 29 21:17:02 2012] [warn] NameVirtualHost 10.8.0.2:80 has no VirtualHosts 
```

Seeing the “port overlap” warning, I tried removing the 'Listen *:80 parameter, as follows

```
NameVirtualHost 10.8.0.2:80 

<VirtualHost *:80> 
     ServerName site2.com 
     DocumentRoot /var/www/ 
</VirtualHost> 
<VirtualHost *:80> 
     ServerName www.site2.com 
     DocumentRoot /var/www/ 
</VirtualHost> 
```

Again:

```
apachectl -k graceful 
```

My errors were generally the same:

```
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName 
[Wed Aug 29 21:17:58 2012] [warn] _default_ VirtualHost overlap on port 80, the first has precedence 
[Wed Aug 29 21:17:58 2012] [warn] _default_ VirtualHost overlap on port 80, the first has precedence 
[Wed Aug 29 21:17:58 2012] [warn] NameVirtualHost 10.8.0.2:80 has no VirtualHosts 
httpd not running, trying to start 
no listening sockets available, shutting down 
Unable to open logs 
Action '-k graceful' failed. 
The Apache error log may have more information. 

```

Not knowing much about these things, I decided to try adding 'http://'  in from of the VirtualHosts name:

NameVirtualHost [http://10.8.0.10:80](http://10.8.0.10:80) 

```
<VirtualHost *:80> 
     ServerName site2.com 
     DocumentRoot /var/www/ 
</VirtualHost> 
<VirtualHost *:80> 
     ServerName www.site2.com 
     DocumentRoot /var/www/ 
</VirtualHost> 
```

Once more

```
apachectl -k graceful 
```

Errors as follows:

```
[Wed Aug 29 21:18:52 2012] [error] (EAI 5)No address associated with hostname: Could not resolve host name http://10.8.0.2 -- ignoring! 
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName 
[Wed Aug 29 21:18:52 2012] [warn] _default_ VirtualHost overlap on port 80, the first has precedence 
[Wed Aug 29 21:18:52 2012] [warn] _default_ VirtualHost overlap on port 80, the first has precedence 
httpd not running, trying to start 
no listening sockets available, shutting down 
Unable to open logs 
Action '-k graceful' failed. 
The Apache error log may have more information. 
```

Another individual has suggested that I may be trying something that is not likely to work:

> When a user comes to either of your domains, it is Apache that decides which page to display by looking at browser domain header (the IP is the same). So normally multiple domain websites can be hosted on a single machine.

This is not a feasible solution with your current setup. Unfortunately, layer 3 applications (OpenVPN, iptables) know nothing about browser headers, so they can not decide where to redirect traffic.

Should I be looking somewhere other than Apache to find a solution?  Is a solution even possible?

Thank you once again for your time and your help!!

---

### Post by SeijiSensei on 2012-08-30
First, you should have an entry in each server's /etc/hosts file with the IP address and hostname like this:

```
10.8.0.2     www.example.com   example.com
```

Next, try replacing "*:80" with "10.8.0.2:80" in the <VirtualHost> definitions.  The entry in that definition must match exactly with the entry in NameVirtualHost.

Have you read this:  [http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html)?

You should read it very carefully, as it will explain everything you need to know about name-based virtual hosting.

---

### Post by aaron.kyle on 2012-08-31
Thanks again SeijiSensei.

I have been reading the materials at apache.org, but I appreciate that you linked me to this one in particular.

I'll continue trying.  For the moment, I have opted to use alternate ports for each server, which I am configuring with the OpenVPN up.sh script.

More soon.

---

### Post by areamike on 2012-09-07
It must be something wrong with something else in your Apache config or your niginx config. I am unfamiliar with nginix.

I have it setup simple on my local network.

Example:

[www.domain1.com](www.domain1.com) and [www.domain2.com](www.domain2.com) both point to my WAN IP.

I then have my router Port forwarding all requests on port 80 to my main internal server on:
192.168.0.10

I then have my main server using the VirtualHosts directive as follows:

<VirtualHost *:80>
ServerName [www.domain2.com](www.domain2.com)
ProxyRequests Off
<Proxy *>
Order deny,allow
Allow from all
</Proxy>
ProxyPreserveHost On
ProxyPass / [http://192.168.0.11/](http://192.168.0.11/)
ProxyPassReverse / [http://192.168.0.11/](http://192.168.0.11/)
</VirtualHost>

This works perfectly for me.

domain1.com brings up the website on my main server running on 192.168.0.10.
While domain2.com brings up my website on my secondary server running on 192.168.0.11.

This however does not work with SSH and FTP and email etc., but those can be easily accomplished using port forwarding, iptables and changing the appropriate listening ports for each service on each server.

---

### Post by aaron.kyle on 2012-09-18
Thanks for your insights, areamike!

In the end, I opted to set non-standard ports for my different websites and to use port forwarding.  I think the trouble was with the OpenVPN layer.

---

