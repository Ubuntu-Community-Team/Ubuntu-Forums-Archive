---
title: "Nginx, too many redirects, err_too_many_redirects"
date: 2014-11-21
forum: Server Platforms
---

### Post by axetone on 2014-11-21
Hi,
  I have been learning and testing various installations of NGINX for proxy_pass (both custom compilation and standard install) using 2 servers. The problem(s) that I am having relate to "err_too_many_redirects"; Specifically, there are many references to clearing cache (I use Chrome) but that does not resolve the problem. I have also looked at the regular expressions hoping to find any misconfiguraitons, but so far nothing (from RTFM) has shown me anything that suggests a misconfiguration.

Primary server has a single domain, standard install, only 1 additional "server directive" noted below. The secondary server also has a standard install with a completely different domain name which resolves fine locally, just not from external requests (i.e. "hosts" file is configured).

<code>
server {
        server_name my2ndweb.com *.my2ndweb.com;
                location ~* {
                proxy_pass [http://172.16.0.12;](http://172.16.0.12;)
                        }
</code>

I have also modified the location directive with "/" instead of "~*", as well as the FQDN at the "proxy_pass" statement (I read somewhere the hosts file would resolve it rather than re-directing to a local address...did nothing for it though);

Anyway, this all works if I use a single server and just place the different domains within different folder structures, but that defeats the purpose of having a failover option if one server breaks...-no I did not configure failover, just thinking about it.

NOTE: There is no other error in the logs whatsoever regarding redirects!


k/r
axetone

---

### Post by axetone on 2015-01-21
[COLOR=#000000][FONT=Arial]ANSWER:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I made the mistake of not removing the wildcard "*" from the nginx.conf file path statement that points to the directory (or in this case with the wildcard DIRECTORIES) used for the site configurations...~thus the error(s) I was given at reload time pointing to a line item error was actually in one of the other conf files and NOT my "default" conf file.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Silly silly mistake![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Solution: Replace the wildcard "*" from the end of the "include.." path statement in nginx.conf and instead use the actual folder/file name ONLY.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Ex: include /etc/nginx/sites-enabled/*.conf;[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]REPLACE WITH: include /etc/nginx/sites-enabled/default; # or whatever your filename is.[/FONT][/COLOR]

---

