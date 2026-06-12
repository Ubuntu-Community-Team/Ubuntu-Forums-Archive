---
title: "mod_rpaf AND mod_remoteip not working properly in 14.04 ?"
date: 2014-04-24
forum: Server Platforms
---

### Post by picbits on 2014-04-24
I've been pulling my hair out over this one.

Installed 14.04 server a couple of days ago. I've been waiting for its release so I can upgrade my existing 12.04 installations.

Installed mod_remoteip as per the various tutorials online - the best I managed was to get the access.log logging the real ip using the %a variable in apache2.conf.
No matter what I tried, phbBB3 wouldn't log my real IP, only that of the reverse proxy server. SMF fared slightly better being able to log the x-forwarded-for but it still wasn't right.

I did a simple phpinfo() script to double check what was going on and again, no matter what I tried, REMOTE_ADDR still showed the reverse proxy IP.

A TCP dump of port 80 showed the headers were coming through correctly.

Then I got excited after finding libapache2-mod-rpaf - installed it after disabling mod_remoteip, configured it and had exactly the same results. With the mod enabled and configured, the access log was correctly logging my remote IP but again, no luck on anything PHP based. phpinfo() showed the reverse proxy again and any applications behind the proxy incorrectly reported the originating IP as the proxy IP.

Scrapped that install of 14.04 and installed a fresh copy of 12.04 server. I followed the Perfect Server instructions for the first few pages (until Mailman) then tried again. After puzzling over where mod_rpaf had disappeared to, I did an apt-get-install libapache2-mod-rpaf (d'oh !) and edited the .conf file with my proxy server settings.

Everything worked straight away. phpinfo() reported the correct remote_addr and my forums were logging the correct IP addresses.

So now I have a fully working installation on 12.04 I decided to do a dist-upgrade to 14.04

Straight away, the mod_rpaf stopped passing the remote IP address to remote_addr. I can only assume that there is either something that breaks it in the 14.04.

Any ideas ?

---

### Post by picbits on 2014-04-24
Quick update - had another play with mod_remoteip and it started working for no apparent reason. Will update tomorrow after a bit more of a play with it.

---

### Post by fsando on 2014-08-15
So you never came back, and now I'm in the same situation. Please give an update, it will be very much appreciated.

---

### Post by picbits on 2014-08-15
Apologies - it has been a busy couple of months.

It has been working fine since my last post - I am using mod_remoteip and my remoteip.conf file looks like this :

```
RemoteIPHeader X-Forwarded-For
RemoteIPInternalProxy 192.168.1.100 127.0.0.1
```

I had issues with the SMF software not picking up the correct IP address and no matter how much I played with the settings continued to have issues but moving to Phpbb sorted this. My shop software (Oscommerce) also picks up the correct IP from mod_remoteip

My frontend has the following lines in the 000-default.conf under the sites-enabled. I'm not saying this is correctly set up but it seems to work nicely for me.

```
        ProxyPass /webshop http://192.168.1.103/webshop
        ProxyPassReverse /webshop http://192.168.1.103/webshop
        ProxyPassReverseCookiePath /webshop /

        ProxyPass /forum http://192.168.1.102/forum
        ProxyPassReverse /forum http://192.168.1.102/forum
```

If you need me to check any more of my settings give me a yell.

---

