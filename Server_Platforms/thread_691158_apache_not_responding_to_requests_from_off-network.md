---
title: "apache not responding to requests from off-network"
date: 2008-02-08
forum: Server Platforms
---

### Post by Ba66e77 on 2008-02-08
I'm having a similar problem to the one discussed here: [http://ubuntuforums.org/showthread.php?t=354205](http://ubuntuforums.org/showthread.php?t=354205)  Unfortunately, there was no solution included in that thread and it's been a year since the last post.

The difference is that, in my case, apache responds to requests from any machine on my network but any request coming from off network never gets a response.

All indications are that I have port forwarding correctly configured in my router.  Can someone please point me in the right direction?

The output of netstat is:
> $ sudo netstat -tlp |grep "apache2"
tcp        0      0 *:www                   *:*                     LISTEN     15449/apache2


My /etc/apache2/sites-available/default file has:
> 
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

---

### Post by cdenley on 2008-02-08
Are you actually accessing it from outside your network, or are you connecting to your WAN IP from inside your network?

Any iptables rules?
```

sudo iptables -L -n

```

Have you tried using another port? Sometimes ISP's block port 80 because they don't want you hosting a web server. This definitely sounds like a networking problem to me.

---

### Post by Ba66e77 on 2008-02-08
No iptable rules
> $ sudo iptables -L -n
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


I'll have to look further into the ISP blocking issue.  I thought it was kosher for me to  host my own site, but maybe not.

As far as > Are you actually accessing it from outside your network, or are you connecting to your WAN IP from inside your network?
I admit im a networking sped, but doesn't using the WAN IP cause the request to get routed up the WAN then back down to the LAN?

---

### Post by cdenley on 2008-02-08
> I admit im a networking sped, but doesn't using the WAN IP cause the request to get routed up the WAN then back down to the LAN?
It depends entirely on the router. Some routers ignore port forwarding for traffic coming from the LAN. Some routers have a setting for this.

---

