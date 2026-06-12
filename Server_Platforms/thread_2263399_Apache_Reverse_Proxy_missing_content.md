---
title: "Apache Reverse Proxy missing content"
date: 2015-01-31
forum: Server Platforms
---

### Post by mdp-d on 2015-01-31
I have an "almost working" reverse proxy configuration and am totally lost on figuring out what is happening here.

If I go directly to the website's page using the proxy URL the following lines are included in the returned page's html source in IE11:

<meta http-equiv=x-ua-compatible content="IE=edge">
<!--[if lt IE 9]><script type="text/javascript" src="themes/modus/html5shiv.js"></script><![endif]-->

The result, with those lines getting returned, is that the page does not display properly.

However, those lines do not exist if I go directly to the site without using the proxy even though I am still using IE11.

This problem does NOT exist with Firefox.

Here is my reverse proxy conf config:

<VirtualHost *:80>
    ProxyPass /mdp/ [http://mdpw2k8s1.mdp.local/mdp/](http://mdpw2k8s1.mdp.local/mdp/)
    ProxyPassReverse /mdp/ [http://mdpw2k8s1.mdp.local/mdp/](http://mdpw2k8s1.mdp.local/mdp/)

    ProxyPass /gallery/ [http://mdpw2k8s1.mdp.local/gallery/](http://mdpw2k8s1.mdp.local/gallery/)
    ProxyPassReverse /gallery/ [http://mdpw2k8s1.mdp.local/gallery/](http://mdpw2k8s1.mdp.local/gallery/)

    ProxyPass /seccams/ [http://mdpw2k3s2.mdp.local:81/](http://mdpw2k3s2.mdp.local:81/)
    ProxyPassReverse /seccams/ [http://mdpw2k3s2.mdp.local:81/](http://mdpw2k3s2.mdp.local:81/)

    Include sites-enabled-user/*.conf
</VirtualHost>

I might also mention another problem I have with the last proxied site.

If I go directly to [http://mdpw2k3s2.mdp.local:81](http://mdpw2k3s2.mdp.local:81) the page I land on is [http://mdpw2k3s2.mdp.local:81/login.htm?page=%2F](http://mdpw2k3s2.mdp.local:81/login.htm?page=%2F)

But if I use the proxy URL and go to [http://proxysvrvr.mdp.local/seccams/](http://proxysvrvr.mdp.local/seccams/) I end up on [http://proxysrvr.mdp.local/]("http://proxysrvr.mdp.local/login.htm?page=%2F")_[COLOR=#0066cc][login.htm?page=%2F]("http://proxysrvr.mdp.local/login.htm?page=%2F")[/COLOR]_

...and that results in a Page Not Found error.

So something is happening that is stripping out "/seccams" in what is returned.

I am new to all of this so it is a small fete that I have this working at all.

Any help would be greatly appreciated.  Thanks in advance.[U][COLOR=#0066cc]

[/COLOR][/U]

---

### Post by volkswagner on 2015-02-01
I think we need more info.
Please post your entire vhost file with proxy info.
Also please describe the server(s) setup, LAN, WAN, same or different subnet, etc. What and why are you trying
to accomplish... ie why the reverse proxy etc.?

---

### Post by mdp-d on 2015-02-01
trying to delete this post....

Actually tried to edit my reply but it would not save so I posted it as a new reply and thought I could delete this one, but it would not allow me to do that either for some reason.  So please read my reply below.

---

### Post by mdp-d on 2015-02-01
The prime objective here is to expose a number of sites inside my home network so I can access them from work.  Work has some very tight firewall rules so using any port other than 80 is not an option.  My ISP's router/gateway has restrictions about how I can do port forwarding as well.  So the best option is to present all sites as subdirectories of a single site as far as how things are presented to the outside world.  However, please understand that my results are based on what I see inside my network so what the ISP's gateway/router might do is not an issue at this time and I have no reason to suspect that it will cause me any issues if I can serve up all these sites on port 80 and not use sub-domains.

 Down below all of this is the entire httpd.conf-user file.  It resides on a Synology DS415+ NAS Device which uses Ubuntu and other than the sections I call out otherwise in this post, it is the default file as found on that device from the factory.  I am very new to Apache and limited as to my Linux skills but I am an I.T. professional in a MS Windows environment.

There is nothing fancy going on with my home's LAN - everything is on a single subnet and I use a Windows DNS server to create A records which all systems inside my home network is pointed to for the Primary DNS and then the ISP's router/gateway is set to act as the Alternative DNS.

 In total there are three sites I would like to proxy to subdirectories at this time.

 The first server I want to proxy is [http://mdpw2k8s1.mdp.local/mdp/](http://mdpw2k8s1.mdp.local/mdp/) which is a Windows 2003 server running IIS and dishing up nothing but pure HTML.  

 This proxy works just fine which is Murphy's Law in practice since that is the one site that will go away soon.

 The second original website is [http://mdpw2k8s1.mdp.local/gallery/](http://mdpw2k8s1.mdp.local/gallery/) which is a Windows 2008R2 Server running Piwigo gallery software which is PHP driven.  I have a problem with this proxy under certain circumstances as explained later but otherwise works fine.

 The third original website is [http://mdpw2k3s2.mdp.local:81/](http://mdpw2k3s2.mdp.local:81/) which is a Windows 2003 server running Blue Iris software (Security Camera Monitoring software) which has its own webserver apparently compiled inside the executable which presumably cannot be modified.  When proxied, this does not work.

 I have edited, since my original post, the httpd-conf-user file to have the following (sadly, this site appears to have removed the indentations ):

< VirtualHost *:80>
    <Location /mdp/ >
ProxyPass [http://mdpw2k8s1.mdp.local/mdp/](http://mdpw2k8s1.mdp.local/mdp/)
ProxyPassReverse [http://mdpw2k8s1.mdp.local/mdp/](http://mdpw2k8s1.mdp.local/mdp/)
    </Location>
    <Location /gallery/ >
ProxyPass [http://mdpw2k8s1.mdp.local/gallery/](http://mdpw2k8s1.mdp.local/gallery/)
ProxyPassReverse [http://mdpw2k8s1.mdp.local/gallery/](http://mdpw2k8s1.mdp.local/gallery/)
    </Location>
    <Location /seccams/ >
ProxyPass [http://mdpw2k3s2.mdp.local:81/](http://mdpw2k3s2.mdp.local:81/)
ProxyPassReverse [http://mdpw2k3s2.mdp.local:81/](http://mdpw2k3s2.mdp.local:81/)
    </Location>
    Include sites-enabled-user/*.conf
< /VirtualHost>

The original httpd.conf-user file had this:
<VirtualHost *:80>
Include sites-enabled-user/*.conf
</VirtualHost>

 ...so I simply expanded on the original.

 When I use IE11 to go to [http://mdpw2k8s1.mdp.local/gallery/](http://mdpw2k8s1.mdp.local/gallery/) everything displays fine as is also the case when using Firefox.

 When I use IE11 and go to [http://proxyserver/gallery/](http://proxyserver/gallery/) there are some pages which have a section of the page shifted to the right by about 25% of the width of the page.  I have deduced that the offending code in the pages source is as follows:

< meta http-equiv=x-ua-compatible content="IE=edge">
< !--[if lt IE 9]><script type="text/javascript" src="themes/modus/html5shiv.js"></script><![endif]-->

 These lines do not appear in the same page using the same browser if I point it directly at the server and not the proxy server so the proxy server is causing them to get added.  Firefox works either way just fine.  Unfortunately I need this to work with IE11 because that is what we use at work.

 On the third site, if I point my browser to [http://mdpw2k3s2.mdp.local:81/](http://mdpw2k3s2.mdp.local:81/) I will land on this URL: [http://mdpw2k3s2.mdp.local:81/login.htm?page=%2F](http://mdpw2k3s2.mdp.local:81/login.htm?page=%2F)

 If I go to [http://proxyserver/seccams/](http://proxyserver/seccams/) I get a "Sorry, the page you are looking for is not found" and the URL displayed in the browser is [http://proxyserver/login.htm?page=%2F](http://proxyserver/login.htm?page=%2F) so something is causing the "/seccams" part of the proxied URL to be removed.

 If I change "<Location /seccams/ >" to "<Location / >" the page will display beautifully so somehow I need to be able to preserve the "/seccams" part of the URL when accessing the site via the proxy server.

 Any help would be greatly appreciated.


 This is the entire httpd.conf-user file:

ServerRoot "/etc/httpd"
 Listen 80
LoadModule authn_file_module modules/mod_authn_file.so
LoadModule authn_default_module modules/mod_authn_default.so
LoadModule authz_host_module modules/mod_authz_host.so
LoadModule authz_groupfile_module modules/mod_authz_groupfile.so
LoadModule authz_user_module modules/mod_authz_user.so
LoadModule authz_owner_module modules/mod_authz_owner.so
LoadModule authz_default_module modules/mod_authz_default.so
LoadModule auth_basic_module modules/mod_auth_basic.so
LoadModule auth_digest_module modules/mod_auth_digest.so
LoadModule include_module modules/mod_include.so
LoadModule filter_module modules/mod_filter.so
LoadModule deflate_module modules/mod_deflate.so
LoadModule log_config_module modules/mod_log_config.so
 #LoadModule logio_module modules/mod_logio.so
LoadModule env_module modules/mod_env.so
LoadModule mime_magic_module modules/mod_mime_magic.so
LoadModule headers_module modules/mod_headers.so
LoadModule setenvif_module modules/mod_setenvif.so
LoadModule proxy_module modules/mod_proxy.so
LoadModule proxy_http_module modules/mod_proxy_http.so
LoadModule mime_module modules/mod_mime.so
LoadModule status_module modules/mod_status.so
LoadModule autoindex_module modules/mod_autoindex.so
LoadModule asis_module modules/mod_asis.so
LoadModule cgid_module modules/mod_cgid.so
LoadModule negotiation_module modules/mod_negotiation.so
LoadModule dir_module modules/mod_dir.so
LoadModule actions_module modules/mod_actions.so
LoadModule userdir_module modules/mod_userdir.so
LoadModule alias_module modules/mod_alias.so
LoadModule rewrite_module modules/mod_rewrite.so
 User http
 Group http
ServerAdmin admin
ServerName *:80
< Directory />
    Options FollowSymLinks
AllowOverride All
RewriteEngine on
RewriteCond %{HTTP:Transfer-Encoding} chunked
RewriteRule ^(.*)$ [http://localhost:412/$1](http://localhost:412/$1) [P]
< /Directory>
< Directory "/var/services/web">
    Options MultiViews FollowSymLinks ExecCGI
AllowOverride All
    Order allow,deny
    Allow from all
< /Directory>
< Directory "/usr/syno/synoman/phpsrc/web">
    Options MultiViews FollowSymLinks ExecCGI
AllowOverride None
    Order allow,deny
    Allow from all
< /Directory>
< Directory "/usr/syno/synoman/empty/web">
    Options MultiViews FollowSymLinks ExecCGI
AllowOverride None
    Order allow,deny
    Allow from all
< /Directory>
< IfModule dir_module>
DirectoryIndex index.html index.htm index.cgi index.php index.php5
< /IfModule>
< FilesMatch "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy All
< /FilesMatch>
ErrorLog /var/log/httpd/user-error_log
 #ErrorLog /dev/null
TraceEnable off
LogLevel error
< IfModule log_config_module>
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
    < IfModule logio_module>
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\" %I %O" combinedio
    </IfModule>
CustomLog /dev/null combined
    #CustomLog /var/log/httpd/user-access_log combined
< /IfModule>
< IfModule alias_module>
    Alias /webman/pingpong.php /usr/syno/synoman/phpsrc/pingpong.php
< /IfModule>
ScriptSock /run/httpd/user-cgisock
DefaultType text/plain
< IfModule mime_module>
TypesConfig conf/mime.types
AddEncoding x-compress Z
AddEncoding x-gzip gz tgz
AddType application/x-compress .Z
AddType application/x-gzip .gz .tgz
AddType image/x-icon .ico
AddHandler cgi-script .cgi
< /IfModule>
MIMEMagicFile conf/magic
< IfDefine HAVE_PHP>
ErrorDocument 403 /webdefault/sample.php?status=403&from=user
ErrorDocument 404 /webdefault/sample.php?status=404&from=user
ErrorDocument 500 /webdefault/sample.php?status=500&from=user
    Include conf/extra/mod_fastcgi.conf
< /IfDefine>
EnableMMAP off
 Include conf/extra/httpd-mpm.conf-user
 Include conf/extra/httpd-autoindex.conf-user
 Include conf/extra/httpd-languages.conf-user
 Include conf/extra/httpd-default.conf-user
< IfDefine SSL>
    < IfDefine !SPDY>
LoadModule ssl_module modules/mod_ssl.so
        Include conf/extra/httpd-ssl.conf
    </IfDefine>
    < IfDefine SPDY>
LoadModule ssl_module modules/mod_ssl_npn.so
        Include conf/extra/httpd-ssl.conf
        Include conf/extra/mod_spdy.conf
    </IfDefine>
< /IfDefine>
< IfModule deflate_module>
DeflateCompressionLevel 2
AddOutputFilterByType DEFLATE text/html text/plain text/xml
AddOutputFilter DEFLATE js css
BrowserMatch ^Mozilla/4 gzip-only-text/html
BrowserMatch ^Mozilla/4\.[0678] no-gzip
BrowserMatch \bMSIE\s7  !no-gzip !gzip-only-text/html
< /IfModule>

< Files *.js>
    Header unset Etag
< /Files>
< Files *.css>
    Header unset Etag
< /Files>
 # For CVS-2001-1446
< Files ~ "^\.([Hh][Tt]|[Dd][Ss]_[Ss])">
    Order allow,deny
    Deny from all
    Satisfy All
< /Files>
 # For @eaDir
< DirectoryMatch "@eaDir">
    Order allow,deny
    Deny from all
    Satisfy All
< /DirectoryMatch>
 # For CVE-2003-1418
FileETag MTime Size
< VirtualHost *:80>
    <Location /mdp/ >
ProxyPass [http://mdpw2k8s1.mdp.local/mdp/](http://mdpw2k8s1.mdp.local/mdp/)
ProxyPassReverse [http://mdpw2k8s1.mdp.local/mdp/](http://mdpw2k8s1.mdp.local/mdp/)
    </Location>
    <Location /gallery/ >
ProxyPass [http://mdpw2k8s1.mdp.local/gallery/](http://mdpw2k8s1.mdp.local/gallery/)
ProxyPassReverse [http://mdpw2k8s1.mdp.local/gallery/](http://mdpw2k8s1.mdp.local/gallery/)
    </Location>
    <Location /seccams/ >
ProxyPass [http://mdpw2k3s2.mdp.local:81/](http://mdpw2k3s2.mdp.local:81/)
ProxyPassReverse [http://mdpw2k3s2.mdp.local:81/](http://mdpw2k3s2.mdp.local:81/)
    </Location>
    Include sites-enabled-user/*.conf
< /VirtualHost>
 include conf/extra/mod_xsendfile.conf-user
 Include conf/extra/httpd-reqtimeout.conf

---

### Post by volkswagner on 2015-02-02
Nothing from that config seems to be Ubuntu standard. Under Ubuntu Apache2 runs as www-data.

What version of Apache is running?

```
sudo apache2 -v
```

---

### Post by mdp-d on 2015-02-02
NASDSMDP> httpd -v
Server version: Apache/2.2.29 (Unix)
Server built:   Jan  7 2015 14:30:18

It would seem that the folks at Synology have taken a free hand with defaults concerning the way they organized their LAMP installations but generally I can figure out the Synology way once I know the more standard manner.  The one that really took me some hunting was how to properly and completely shutdown the httpd and then restart same.  While some more standard approaches seemed to do something, the server would still be running when I checked.  They apparently built a tool to handle all services so "synoservicecfg -restart webstation" will restart httpd when nothing else seemed to work completely.

---

### Post by mdp-d on 2015-02-02
Oh, to be fair, I'm trying to configure this Reverse Proxy on a Synology Diskstation Virtual Machine I have hosted on my VMware eSXI server and that is a slightly older version of the Synology DSM but they both still use the same version of Apache and they appear to set up identically.

If I get it working on the VM then all I have to do is port it over to my 'real' NAS device and it should work identically there ( see t[http://www.xpenology.nl/vmware-esxi-installatie/](http://www.xpenology.nl/vmware-esxi-installatie/) if you want to inspect under the hood).

---

### Post by volkswagner on 2015-02-02
Perhaps you can spin up a small Ubuntu VM to act as proxy server. You may also try Nginx which is considered
by many to be an efficient choice for this task.

I wouldn't even pretend to say I could help.  If you look at [Ubuntu server docs on setting up namevirtualhosts]("https://help.ubuntu.com/10.04/serverguide/httpd.html"), you'll
see the config files are different.

I don't want to give you the wrong advise. I do know this... I have had a terrible time in the past trying to configure directory base reverse proxy.
I suggest going the route of subdomains. You can use a service like no-ip.com and create several names, or if you have a registered domain name
you can use the no-ip.com as a cname record for several subdomains.

You may also want to check out ProxyPass Directive in this [Apache2 doc]("http://httpd.apache.org/docs/2.2/mod/mod_proxy.html").

It seems you can eliminate the "ProxyPassReverse" portion if I'm reading that correctly.

---

### Post by mdp-d on 2015-02-02
Thank you for your time and thought on this.  I have considered spinning up a LAMP with all the defaults but based on what I have read I am pretty confident that I will have the same problems with that.

After all I have read I am confident that the answer lies in some statements being added or modified between the line that starts with <VirtualHost *:80> and the line that ends with </VirtualHost> and possibly involves an additional modules such as, perhaps, the rewrite module.

Unfortunately, I am not well versed on the nuances of all the options and will remain hopeful that someone can see right away what is needed to solve this problem.

After all, to acquiesce to doing as you suggest (switch to subdomains) will be admitting defeat because there is little doubt that what I wish to do is doable and having to fall back on the easy button of using subdomains, which I am quite certain will solve at least the Blue Iris server proxy issue, is admitting defeat.

But then again, if I am going to do that, I might as well push the Easy Button even more confidently than that and stick with Windows Server 2008 and their proxy/reverse proxy/rewrite solution to do the same thing and basically state what you are implying and that being that Linux/Apache is too difficult and complex to get it to work the way one wishes and that approach is not at all how I got to being the guy folks come to in my job at my world wide company when they run into problems that seem to be too difficult to solve.

---

### Post by volkswagner on 2015-02-02
I certainly didn't mean to imply Linux was too difficult to administer the solution. What I did try to imply is to get help into his forum you should spin up an Ubuntu VM, or try a forum more familiar with the distro you're running.

There's a lot of well rounded Linux admins here, so you may find help. 

I'm just not familiar with that type of config file.

---

### Post by mdp-d on 2015-02-02
OK well then I misunderstood what you were saying.

Regardless of some of the paths and other configurations, this is still an Apache 2.2.29 installation on a Linux OS and the Apache conf-user file layout and directives is the same and oddly enough, if formatted properly, has identical section layouts to that used by Windows for their reverse proxy, etc. module though theirs must be all XML.

Last, unless I have understood what I read wrong, the section laid out between <VirtualHost [FONT=Lucida Console][SIZE=2][FONT=Lucida Console][SIZE=2]*[/SIZE][/FONT][/SIZE][/FONT][SIZE=2]:80> and </VirtualHost> is what matters and is pretty much first come first served so you can have numerous of those sections in the file.  As well, it is my understanding that it is what lands between those tags that will do what I need to get done if I can just figure out the correct directives and arguments to use.

Though I might still stand up a pure Ubuntu LAMP and see what I can figure out there as I already discovered that the proxy_html_module is missing with this box and I think I might need that - and certainly cannot play around with it to decide if I do or not when it isn't there to include in the first place.  I read I can recompile apache but that would send me off on a tangent that would have me solving problems to solve problems to solve problems and so on...[/SIZE]

---

