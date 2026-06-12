---
title: "Securing awstats by allowing only local network to run CGI script"
date: 2008-07-23
forum: Server Platforms
---

### Post by danielsbrewer on 2008-07-23
I have installed awstats and got it working fine.  The only problem I have is that I want it only to be accessible from my local network and not externally.  Whatever I try, I can't seem to get it to work. 

 Here is my apache2 config file:
```
<Directory /var/lib/awstats>
	Options None
	AllowOverride None
        Order deny,allow
        Allow from 127.0.0.0/255.0.0.0 ::1/128
	Allow from 192.168.0.
        Deny from all
</Directory>

<Directory /usr/share/awstats/icon>
	Options None
	AllowOverride None
        Order deny,allow
        Allow from 127.0.0.0/255.0.0.0 ::1/128
	Allow from 192.168.0.
        Deny from all
</Directory>

Alias /awstats-icon/ /usr/share/awstats/icon/

<Directory /usr/lib/cgi-bin/>
	Options None
	AllowOverride None
        Order deny,allow
        Allow from 127.0.0.0/255.0.0.0 ::1/128
	Allow from 192.168.0.
        Deny from all
</Directory>
# This (hopefully) enables _all_ CGI scripts in the default directory
# Security concerns: Are you sure _all_ CGI scripts are safe?
ScriptAlias /awstats/ /usr/lib/cgi-bin/
```

The first two seem to stop apache displaying icons outside the local network, but thats it.  Apache seems to ignore the Directory /usr/lib/cgi-bin stuff.

Anyone got any ideas how to fix this and only allow users on the local network to run the awstats script?

Is there a more secure web analysing tool?

---

