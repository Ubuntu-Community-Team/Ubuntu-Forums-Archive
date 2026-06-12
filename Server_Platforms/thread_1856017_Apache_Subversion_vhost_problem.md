---
title: "Apache Subversion vhost problem"
date: 2011-10-07
forum: Server Platforms
---

### Post by semick on 2011-10-07
I'm having a real problem with using subversion and apache as a vhost.  I've successfully set this up before many times, but this time i am really stumped.  I've tried about 30 different combinations from every page I could find on Google and nothing works (with TortoiseSVN).  

Here is my current config:


```
<VirtualHost 192.168.213.102:80>
        ServerName webserv01.gva-twn.com
        <Location /svn>
                DAV svn
                SVNPath /usr/local/subversion/development
                AuthType Basic
                AuthName "Subversion Repository"
                AuthUserFile /etc/apache2/dav_svn.passwd
                Require valid-user
        </Location>
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```


Almost every configuration I've tried works fine when a browser is used to access the repository, but none, including the above, work with TortoiseSVN. 

The difference, I have observed from looking at the apache logs is that when requesting pages using a browser, a simple http request is generated.   But tortoiseSVN is interacting with webdav:

```

192.168.210.139 - - [07/Oct/2011:10:42:15 -0400] "OPTIONS /svn HTTP/1.1" 401 672 "-" "SVN/1.6.17 (r1128011) neon/0.29.6"
192.168.210.139 - scotte [07/Oct/2011:10:42:20 -0400] "OPTIONS /svn HTTP/1.1" 200 877 "-" "SVN/1.6.17 (r1128011) neon/0.29.6"
192.168.210.139 - scotte [07/Oct/2011:10:42:20 -0400] "PROPFIND /svn HTTP/1.1" 207 556 "-" "SVN/1.6.17 (r1128011) neon/0.29.6"
192.168.210.139 - scotte [07/Oct/2011:10:42:20 -0400] "PROPFIND /svn/!svn/vcc/default HTTP/1.1" 207 458 "-" "SVN/1.6.17 (r1128011) neon/0.29.6"
192.168.210.139 - scotte [07/Oct/2011:10:42:20 -0400] "PROPFIND /svn/!svn/bln/106 HTTP/1.1" 207 472 "-" "SVN/1.6.17 (r1128011) neon/0.29.6"
192.168.210.139 - - [07/Oct/2011:10:42:20 -0400] "PROPFIND /svn HTTP/1.1" 403 442 "-" "SVN/1.6.17 (r1128011) neon/0.29.6"
192.168.210.139 - - [07/Oct/2011:10:42:21 -0400] "OPTIONS / HTTP/1.1" 200 299 "-" "SVN/1.6.17 (r1128011) neon/0.29.6"
```

I read the docs for webdav and RFC 2518, but not getting anywhere there.

The apache error logs show this:

```

[Fri Oct 07 10:54:15 2011] [error] [client 192.168.210.139] client denied by server configuration: /etc/apache2/htdocs
[Fri Oct 07 10:54:15 2011] [error] [client 192.168.210.139] client denied by server configuration: /etc/apache2/htdocs
```

which tells me for some bizarre reason, when tortoise is requesting docs, apache, not webdav is handling the request.  Because /etc/apache2/htdocs is the default directory since I didn't specify with DocumentRoot in my vhost.  

If I do specify document root, then I get other errors because the webdav location cannot coexist with the document root.

Does anyone else have any ideas?  The information about using subversion-webdav-vhost is so sparse on the web I don't know what else to try at this point.

Thanks

Scott

oh yeah versions:

```
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID: Ubuntu
Description:    Ubuntu 11.04
Release:        11.04
Codename:       natty

svn, version 1.6.12 (r955767)

apache version:

Server version: Apache/2.2.17 (Ubuntu)
Server built:   Sep  1 2011 09:31:14


```

---

