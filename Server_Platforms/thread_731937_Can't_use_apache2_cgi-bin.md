---
title: "Can't use apache2 cgi-bin"
date: 2008-03-22
forum: Server Platforms
---

### Post by Blah99 on 2008-03-22
Hi, 

Got a strange problem I don't know how to fix. Basically I can't run any .pl in my cgi-bin. I discovered this while installing awstats but it happens for any and all .pl.

I have a co-lo server that's been preconfigured with Ubuntu, the usual packages and set up in a way that makes it easy to add multiple domains etc to it.

> Distributor ID: Ubuntu
Description:    Ubuntu 6.06.2 LTS
Release:        6.06
Codename:       dapper

I have my cgi-bin in /usr/lib/cgi-bin, the websites are stored in /home/<groupname>/domain, eg: /home/mydomains/mysite.com/htdocs etc. Apache configs are in the usual place /etc/apache2/*

In my apache2 config I have:

ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
Options ExecCGI -MultiViews +SymLinksIfOwnerMatch

Yet whenever I try and run a .pl script I get the following error in my site error log:

[error] [client xxxxxx] Premature end of script headers: test.pl

I know there's nothing wrong with test.pl because I get the same error with awstats.pl, and I can run both from shell with no problems. perl -c also shows they are valid.

I'm somewhat confused as to how to fix this. I just can't see why I get that error. I've googled and read everything I can find on this error but none of the solutions actually fix my problem. All help appreciated.

Thanks.

---

### Post by Blah99 on 2008-03-22
Scrap that. Finally figured out what was going on, suexec was killing it.

---

### Post by Black Mage on 2008-05-05
Can you go back to how you resolved this problem? Because I'm having the same one.

---

