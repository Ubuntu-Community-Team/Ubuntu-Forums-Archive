---
title: "mod_proxy configuration -- big gaping hole"
date: 2010-11-05
forum: Security
---

### Post by yelvington on 2010-11-05
I enabled mod_proxy on my webserver the other day. I needed to proxy one specific virtual host to fetch a service from an alternate port. I followed the Apache documentation and configured the virtual host properly.

Not long after that found my access log flooded with requests indicating my webserver was being used as a proxy by hundreds of third parties.

Now, I'm perfectly aware that** you NEVER turn on mod_proxy without securing your server**. 

Trouble is, **NOTHING I did would make this stop.** I put directives into httpd.conf. I put directives into the individual sites' configuration files (I run several virtual hosts). The hits just kept coming.

Eventually, with the help of a bunch of web searches, I found a reference to a proxy.conf file in /etc/apache2/mods-available. When you run a2enable, it's linked in mods-enabled. And it says:


<IfModule mod_proxy.c>
        #turning ProxyRequests on and allowing proxying from all may allow
        #spammers to use your proxy to send email.

        ProxyRequests On 

        <Proxy *>
                AddDefaultCharset off
                Order deny,allow
                Deny from all
                Allow from all
        </Proxy>

        # Enable/disable the handling of HTTP/1.1 "Via:" headers.
        # ("Full" adds the server version; "Block" removes all outgoing Via: headers)
        # Set to one of: Off | On | Full | Block

        ProxyVia On
</IfModule>

This makes my head explode.

The moment you a2enable proxy_http and reload the server, you're running an unsecured, open proxy that's just asking to be discovered and hijacked. And there are apps designed to do exactly that.

What I wanted is to enable one specific resource with one specific mod_rewrite directive for one specific server -- which I did, but I also let a pack of spammers through my doorway. 

Removing the "ProxyRequests On" directive fixed the problem.

In my opinion, this should NOT be the default, as it's specifically warned against in the Apache documentation.

At any rate, I'm putting this note here in hopes of helping others avoid this problem when they attempt to configure internal proxy services.

---

