---
title: "apache2 reverse proxy"
date: 2011-04-20
forum: Server Platforms
---

### Post by andriu1 on 2011-04-20
Hello all,

    I'm having some problem with an apache2 web server over ubuntu 10.0.4, and I'd like to share with all you, to try to get a solution

    First of all, I've not experience in this platforms, so i'm a bit stressed because my configuration don't work and i don't know the reason.

    I've an apache2 installed on a server and a tomcat+nuxeo in another server, both over Ubuntu 10.0.4. The webpage has a pair of buttons that connects to tomcat or nuxeo directly, so when a client select this buttons, the conexion is stablished to Tomcat. Because i think that this is a bad configuration I've been reading how to make a reverse proxy on my apache to make that all conexions from internet pass through apache, and Tomcat could not be accessed from internet.

    The first step has been to modify the web page. When the ip of tomcat was referred as 172.17.1.3, it's been written the URL accessed from internet, for example, [https://myapp.one.es](https://myapp.one.es). This has been don by web developer

    the second step has been to modify apache2 httpd.conf, like this:

##### start reverse proxy configuration #####

# Loading necessary modules #

LoadModule proxy_module      /usr/lib/apache2/modules/mod_proxy.so
LoadModule proxy_http_module /usr/lib/apache2/modules/mod_proxy_http.so
LoadModule headers_module    /usr/lib/apache2/modules/mod_headers.so
LoadFile   /usr/lib/libxml2.so.2
LoadModule proxy_html_module /usr/lib/apache2/modules/mod_proxy_html.so
#LoadModule xml2enc_module /usr/lib/apache2/modules/mod_xml2enc.so

# reverse proxy rules #

ProxyRequests off
ProxyPass /LanzaEnviosListados/download.php [http://172.17.1.3:8080/LanzaEnviosListados/download.php](http://172.17.1.3:8080/LanzaEnviosListados/download.php)
ProxyPass /nuxeo [http://172.17.1.3:8085/nuxeo](http://172.17.1.3:8085/nuxeo)
ProxyPassReverse /LanzaEnviosListados/download.php [http://172.17.1.3:8080/LanzaenviosListados/download.php](http://172.17.1.3:8080/LanzaenviosListados/download.php)
ProxyPassReverse /nuxeo [http://172.17.1.3:8085/nuxeo](http://172.17.1.3:8085/nuxeo)

### end reverse proxy configuration ###

    The line of module xml2enc_module has been commented by me because mod_xml2enc.so is not found, and an error appear when restarting apache2. I've been looking for this module but Ive not find it, and i don't know if this is the problem or perhaps it's my configuration.

Could anyone help me with this, please

thank you very much in advance
Regards
Andres

---

### Post by usatonycuba on 2011-04-20
Hola Andres .. did you check the apache log to see what he says?

> ..The second step has been to modify apache2 httpd.conf, like this:
That was in *httpd.conf* or *httpd2.conf* conf file?

---

### Post by andriu1 on 2011-04-20
Hello usatonycuba

Thanks for your response.

The apache error log says this when accesing one redirected url

[Wed Apr 20 12:12:00 2011] [error] [client *IP_APACHE*] The template "secureSuccess.pdf.php" does not exist or is unreadable in ""., referer: [https://*website](https://*website)*/listadospredefinidos/index

About the other info, I've configured httpd.conf, because no httpd2.conf is found. May I create httpd2.conf, and insert configuration into this file?

Thanks again
Andres

---

### Post by usatonycuba on 2011-04-20
> **andriu1 said:**
> 
 [Wed Apr 20 12:12:00 2011] [error] [client *IP_APACHE*] The template "secureSuccess.pdf.php" does not exist or is unreadable in ""., referer: [https://*website](https://*website)*/listadospredefinidos/index 
That php script (secureSuccess.pdf.php).. are supouse to be ( in "") << don't know where is that location... so go to listadospredefinidos/index ...open index and find the link is pointing to "secureSuccess.pdf.php" and make sure is correct linked to..   ...Or that php script (secureSuccess.pdf.php) have wrong permitions set.

> **andriu1 said:**
> 
About the other info, I've configured httpd.conf, because no httpd2.conf is found. May I create httpd2.conf, and insert configuration into this file?


@Andres ...First, the file apache2.conf .. is the main configuration file for apache .. it was created When You install your server ...and you should not modify this file (till you know what are you doin) It can crash the whole configuration in your server. ....try to find if at install time, your httpd2.conf get misplaced.. So, at your terminal type:
```
whereis apache2.conf
```

---

### Post by andriu1 on 2011-04-20
Ok Ok, usatonycuba. The first error is caused by permission, your are right. It works fine with certain users.

About the httpd2.conf, I've executed whereis command

$ whereis apache2.conf
apache2: /usr/sbin/apache2 /etc/apache2 /usr/lib/apache2 /usr/share/apache2 /usr/share/man/man8/apache2.8.gz

But, for conf file, neither httpd.conf or httpd2.conf are found, although httpd.conf is located under /etc/apache2

/etc/apache2$ ls
apache2.conf  conf.d  envvars  httpd.conf  magic  mods-available  mods-enabled  ports.conf  sites-available  sites-enabled  ssl
/etc/apache2$ whereis httpd.conf
httpd:
/etc/apache2$ whereis httpd2.conf
httpd2:
/etc/apache2$

Do you know if it's possible to see the proxypass redirections, is there any log where this information is stored?
 
It seems that proxypass configuration of httpd.conf is not working fine

If this is useful, i paste a ls of /etc/apache2/mod-available and mods-enabled

/etc/apache2/mods-enabled$ ls ../mods-available/
actions.conf        authz_groupfile.load  dbd.load         include.load       proxy_balancer.load  ssl.load
actions.load        authz_host.load       deflate.conf     info.conf          proxy.conf           status.conf
alias.conf          authz_owner.load      deflate.load     info.load          proxy_connect.load   status.load
alias.load          authz_user.load       dir.conf         ldap.load          proxy_ftp.load       substitute.load
asis.load           autoindex.conf        dir.load         log_forensic.load  proxy_html.conf      suexec.load
auth_basic.load     autoindex.load        disk_cache.conf  mem_cache.conf     proxy_html.load      unique_id.load
auth_digest.load    cache.load            disk_cache.load  mem_cache.load     proxy_http.load      userdir.conf
authn_alias.load    cern_meta.load        dump_io.load     mime.conf          proxy.load           userdir.load
authn_anon.load     cgid.conf             env.load         mime.load          proxy_scgi.load      usertrack.load
authn_dbd.load      cgid.load             expires.load     mime_magic.conf    reqtimeout.conf      version.load
authn_dbm.load      cgi.load              ext_filter.load  mime_magic.load    reqtimeout.load      vhost_alias.load
authn_default.load  charset_lite.load     file_cache.load  negotiation.conf   rewrite.load
authn_file.load     dav_fs.conf           filter.load      negotiation.load   setenvif.conf
authnz_ldap.load    dav_fs.load           headers.load     php5.conf          setenvif.load
authz_dbm.load      dav.load              ident.load       php5.load          speling.load
authz_default.load  dav_lock.load         imagemap.load    proxy_ajp.load     ssl.conf

/etc/apache2/mods-enabled$ ls
alias.conf          authz_groupfile.load  cgi.load      env.load          php5.conf        reqtimeout.load  ssl.load
alias.load          authz_host.load       deflate.conf  mime.conf         php5.load        rewrite.load     status.conf
auth_basic.load     authz_user.load       deflate.load  mime.load         proxy_html.conf  setenvif.conf    status.load
authn_file.load     autoindex.conf        dir.conf      negotiation.conf  proxy_html.load  setenvif.load
authz_default.load  autoindex.load        dir.load      negotiation.load  reqtimeout.conf  ssl.conf

Is it possible that i must enable some module that i've loaded with dpkg command, but i must do anything more to enable it?

Thank you very much

Regards,
andres

---

### Post by usatonycuba on 2011-04-20
@Andres Can you please paste your (complete) httpd.conf file ?

(please, Note that To post configuration files, command line, lines of code .. etc. in writing  Messages area, use the [COLOR="DarkRed"]#[/COLOR] symbol to enclose it in a block of code.. It will make it more readable).. thanks

---

### Post by andriu1 on 2011-04-20
Hello usatonycuba,

you're right. it's clearer marking copy/paste with # for example.

Here is httpd.conf file

################3
##### start reverse proxy configuration #####

# Loading necessary modules #

LoadModule proxy_module      /usr/lib/apache2/modules/mod_proxy.so
LoadModule proxy_http_module /usr/lib/apache2/modules/mod_proxy_http.so
LoadModule headers_module    /usr/lib/apache2/modules/mod_headers.so
LoadFile   /usr/lib/libxml2.so.2
LoadModule proxy_html_module /usr/lib/apache2/modules/mod_proxy_html.so
#LoadModule xml2enc_module /usr/lib/apache2/modules/mod_xml2enc.so

# reverse proxy rules #

ProxyRequests off
ProxyPass /LanzaEnviosListados/download.php [http://172.17.1.3:8080/LanzaEnviosListados/download.php](http://172.17.1.3:8080/LanzaEnviosListados/download.php)
ProxyPass /nuxeo [http://172.17.1.3:8085/nuxeo](http://172.17.1.3:8085/nuxeo)
ProxyPassReverse /LanzaEnviosListados/download.php [http://172.17.1.3:8080/LanzaenviosListados/download.php](http://172.17.1.3:8080/LanzaenviosListados/download.php)
ProxyPassReverse /nuxeo [http://172.17.1.3:8085/nuxeo](http://172.17.1.3:8085/nuxeo)

### end reverse proxy configuration ###
###########################

Thank you for your help
Regards
Andres

---

### Post by usatonycuba on 2011-04-20
@Andres do you speak Spanish? .. sorry for asking you.. if you do so:

Me refiero que al momento de escribir aqui en el foro.. cuando usas el area de texto para responder un mensage.. como el que acabas de hacer.. y quieres poner un CODIGO, un ARCHIVO, un COMANDO, etc... 

Vas a la parte de abajo del este foro (lado izquierdo), da click en "New Reply", te aparece la ventana de escribir, en la parte  arriba de el area de escribir de esa ventana.... hay un simbolo de numero (#).. cuando le das clik, te aparece 2 bloques encerrados en corchetes **[COLOR="DarkRed"][[/COLOR]** << entre ese y este >>> **[COLOR="DarkRed"]][/COLOR]**, dentro del primero te dira [COLOR="DarkRed"]CODE[/COLOR], Y el segundo [COLOR="DarkRed"]/CODE[/COLOR]... todo lo que escribas dentro te aparecera en un bloque de codigo en el foro...

Returning to the problem with the proxy .. :) .. some how it appears (to me)  that you have a configuration problem on your Apache httpd.conf configuration file, take a look at following links:
[http://community.nuxeo.com/5.3/books/nuxeo-book/html/admin-virtualhosting.html]("http://community.nuxeo.com/5.3/books/nuxeo-book/html/admin-virtualhosting.html")

> 
Reverse proxy with mod_proxy

For this configuration, you will need to load and enable mod_proxy and mod_proxy_http modules.
```

ProxyPass /nuxeo/ http://Nuxeo5ServerInternalIp:8080/nuxeo/
ProxyPassReverse /nuxeo/ http://Nuxeo5ServerInternalIp:8080/nuxeo/

```

You can also use rewrite rules to achieve the same result:
```

ProxyVia On
ProxyRequests Off
RewriteEngine On
RewriteRule /nuxeo(.*) http://Nuxeo5ServerInternalIp:8080/nuxeo$1 [P,L]

```
This configuration will allow you to access the Nuxeo EP webapp via [http://ApacheServer/nuxeo/](http://ApacheServer/nuxeo/).
The Nuxeo webapp will generate the URLs after reading the http header x-forwarded-host.

Unfortunately, this header does not specify the protocol used, so if your Apache is responding to HTTPS, you will need to send Nuxeo EP a specific header to indicate the base URL that the webapp must use when generating links.

RequestHeader append nuxeo-virtual-host "https://myDomainName/"
This will require you to load and activate mod_headers module.

And if you have "client denied by server configuration" error, you must check the access control directives of mod_proxy:
```

<Proxy *>
  Order Deny,Allow
  Deny from all
  Allow from 192.168
</Proxy> 

```

Note, this the way I do for my own setting when setting more than just one Web Servers (via Proxy) (it may no do for yours) ;)

Now, you must have a (proxy.conf file in /etc/apache2/mods-available/proxy.conf) wich a Proxy Module Enabled on it.. (I do make look to something like this):
```

<IfModule mod_proxy.c>
        #turning ProxyRequests on and allowing proxying from all may allow
        #spammers to use your proxy to send email.

        ProxyRequests Off

        <Proxy *>
                AddDefaultCharset off
                Order deny,allow
                Allow from all
        </Proxy>

        # Enable/disable the handling of HTTP/1.1 "Via:" headers.
        # ("Full" adds the server version; "Block" removes all outgoing Via: headers)
        # Set to one of: Off | On | Full | Block

        ProxyVia On
</IfModule>

```

then run:

```

a2enmod proxy
a2enmod proxy_http
/etc/init.d/apache2 restart

```

Any time that you get erros, check your log's at [COLOR="DarkRed"]/var/log/apache2/[/COLOR] .. to see what it says

---

### Post by andriu1 on 2011-04-25
Hello usatonycuba, I'm going to try your suggestions this morning. 

Here, in Spain, we've been on holidays last week because the "Semana Santa", and i couldn't do anything.

Thanks again
Andres

PD. Como ves, podemos hablar en castellano si lo prefieres ;-)

---

### Post by usatonycuba on 2011-04-25
> **andriu1 said:**
> Hello usatonycuba, I'm going to try your suggestions this morning. 

Here, in Spain, we've been on holidays last week because the "Semana Santa", and i couldn't do anything.

Thanks again
Andres

No problem, i will be around anyway..
> **andriu1 said:**
> 
PD. Como ves, podemos hablar en castellano si lo prefieres ;-)
Creo que no hay problemas.. solo hay que preguntar a los administradores...

PD: ...it will be limited the help that you can get, remember that I am not the only one who's pass by the  forums, if (we just type here in spanish) any other member will be not be able to follow and help you in this matter.. we need to ask the Forums Admins/Moderators any way

---

### Post by andriu1 on 2011-04-27
> **usatonycuba said:**
> No problem, i will be around anyway..

Creo que no hay problemas.. solo hay que preguntar a los administradores...

PD: ...it will be limited the help that you can get, remember that I am not the only one who's pass by the  forums, if (we just type here in spanish) any other member will be not be able to follow and help you in this matter.. we need to ask the Forums Admins/Moderators any way

Ok, usatonycuba, it's better to continue in English.

So, I've follow instructions, and no error message has appeared during apache restart. I think that it's configured and work, but there is are a couple of links in apache web that don't work, but i think that it's the web files programming, so I've told to developers, to check that the links are correct. This links are in tomcat server, therefore, when a client click, apache must get the request and send to tomcat

Meanwhile, I'm going to try writting url that fail with "httpfox" of firefox enabled to see http tracking. I've reviewed access.log file but it's empty

Thanks
Andres

---

### Post by andriu1 on 2011-04-28
OK, the problem was the links associated to the options of the web. Developers have been working and have corrected the problem.

I don't know how, but they have a development platform to try modifications, and they say that the options that failed me were fine into their platform. I don't know, but the problem is solved. :confused:

Thank you very much again usatonycuba for your help

Best regards,
Andres

---

