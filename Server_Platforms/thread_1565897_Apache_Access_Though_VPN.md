---
title: "Apache Access Though VPN"
date: 2010-09-01
forum: Server Platforms
---

### Post by thegaffney on 2010-09-01
Hey there, just switched our company from windows server to linux and everything is going good except we have 4 vpn connections though out the country coming to our server. All giving the client machines ip addresses of 192.168.x.x based on where they are located 192.168.1.x for the main location 192.168.2.x for a second location etc, and IIS could see the clients ip instead of the wan ip and was setup to block all ips except 192.168.x.x ip's and this worked great.

So i set up apache the same way, to allow only 192.168 ip's but i guess it doesn't work that way in apache for connections coming though vpn?

My error.log shows (WAN IP) denied by server configuration
So apache is seeing the wan ip and not the clients ip which is 192.168.3.x

By also if i look in access.log the 192.168.3.x IP is logged not the WAN IP? So i know its seeing it somewhere?

2 out of our 4 VPN connections are not static IP's, so the 2 that are I just add that ip to the allow list and that worked
But i don't think we should HAVE to get static ips for the other 2, that's one of the benefits of using VPN, especially if our old windows server didnt need it

Is there any way for apache to see the clients ip address for access
or is there something somewhere else that needs changed for this?

Thanks for the help

---

### Post by deoren on 2010-09-01
Can you post the relevant section of your Apache configuration? It sounds like it's already seeing the right IPs, but there is some sort of misconfiguration.

---

### Post by thegaffney on 2010-09-02
Yeah you bet, here is the listing for the virtual host they are trying to get to

```
<VirtualHost *:80>
        ServerAdmin mike@midfifty.com
        ServerName midfifty.com
        DocumentRoot /www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order deny,allow
                Allow from 192.168
                Deny from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorDocument 403 https://midfifty.com/notallow.php
        ErrorLog /var/log/apache2/***.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```And here is the line in the error log when they try to view it

```
[Wed Sep 01 22:21:26 2010] [error] [client 74.47.104.206] client denied by server configuration: /www/

```But the computer's LAN IP that is trying to connect (using VPN) is 192.168.0.x
But this was never an issue with IIS and Windows, all the windows server had in its restrictions was "Deny all connections except from 192.168.x.x" So even the people in a different state with a different internet IP connecting though the VPN could view it because i knew the LAN IP

Computers in the same building as the server can access it just fine of coarse, there IP range is 192.168.1.x


If it helps , from the linux server i can successfully ping the VPN clients LAN IP, example 192.168.0.3 and of coarse i can ping the VPN routers IP 192.1668.0.1 even though the server is on a 192.168.1.1 gateway, so the VPN is working correctly, and the VPN users can browse our network files.

---

### Post by thegaffney on 2010-09-02
Oh, and like I said, to get around it for now, i added "Allow {WAN IP ADDRESS}" to the virtual hosts config, an that of coarse allows them to connect, 

And only AFTER they have access, then in the access.log file you can now see the LAN IP when that client makes a request, so obviously apache knows the LAN IP

```
**192.168.0.4 **- - [01/Sep/2010:13:05:21 -0700] "GET /img/tab_bg_h.gif HTTP/1.1" 200 441 "http://servername/style.css" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1$
```

---

### Post by deoren on 2010-09-02
Bummer. I don't see anything that would be blocking their LAN IP in your config file. It doesn't look like I'll be of much help as I'm unfamiliar with how most VPN setups work on the back end.

---

### Post by thegaffney on 2010-09-02
Its ok, thanks for taking a look at least,

for now ill just use the wan ip's and change it when they change, until someone comes across this and might know whats going on

---

### Post by de0xyrib0se on 2010-09-02
Make sure the remote locations use the private ip of the server and not the public one, if they use the public one their connections would go out through the internet and not the VPN tunnel...since the server public ip is not part of their tunnels.

---

### Post by de0xyrib0se on 2010-09-02
Make sure that whatever IP you want the server to answer apache requests on is part of the routes advertised by the VPN to the clients.

---

### Post by thegaffney on 2010-09-02
> **de0xyrib0se said:**
> Make sure the remote locations use the private ip of the server and not the public one, if they use the public one their connections would go out through the internet and not the VPN tunnel...since the server public ip is not part of their tunnels.

Ah good idea, ill have them check that to see whether its going though our dns server or a internet one.

---

