---
title: "Link problem"
date: 2011-04-19
forum: Server Platforms
---

### Post by acii on 2011-04-19
Hi,

I've spent days trying to set up access properly from a public address to a monitoring server that works fine locally.

Everything works from public access until I try to link to a CVS repository. The rancid CVS repository is set up as a separate server (virtualhost). It appears the referring link causes a DNS error (105: Server Not Found) when the CVS repository server is accessed from the public address. Things work fine when accessing via localhost.

Localhost link:

'http://localhost:8980/opennms/inventory/rancidViewVc.htm?node=1&groupname=routers&viewvc='
'http://infoopennms.org/viewvc/routers/configs/10.101.0.1?view=log'

Public link: (this results in 105 error caused by redirection (bold portion of link))

'http://xxx.xxx.xxx.xxx/opennms/inventory/rancidViewVc.htm?node=1&groupname=routers&viewvc='
**'http://infoopennms.org/viewvc/routers/configs/10.101.0.1?view=log'**

```
Virtualhost config:

 LoadModule jk_module /usr/lib/apache2/modules/mod_jk.so
 JkWorkersFile /etc/apache2/workers.properties
 JkLogFile /var/log/apache2/mod_jk.log

User rancid
Group rancid

<VirtualHost *:80>
        DocumentRoot /var/www
	ServerName infoopennms.org
	ServerAdmin webmaster@localhost
	JkMount /opennms* ajp13
        JkUnmount /opennms/images* ajp13
ScriptAlias /rws /var/www/rws-server/rws-cgi/rws-cgi.tcl
ScriptAlias /viewvc /usr/lib/viewvc/cgi-bin/viewvc.cgi
SetEnv RWS_STORAGE_ROOT  /var/lib/rancid/rws-storage-root   
 ErrorLog /var/log/rws-error_log
 TransferLog /var/log/rws-access_log  
SetEnv RWS_LOGFILE  /var/log/rws-cgi/rws-cgi.log
SetEnv RWS_LOGLEVEL debug      
        RedirectMatch ^/?$ [http://infoopennms/login.jsp](http://infoopennms/login.jsp)
        Alias /favicon.ico /var/www/favicon.ico
        Alias /opennms/images /usr/share/opennms/jetty-webapps/opennms/images
</VirtualHost>

```
If anyone has any thoughts, I'd be eternally grateful.

Many thanks.

---

### Post by usatonycuba on 2011-04-20
@acii

[COLOR="Sienna"]Suggest[/COLOR]: when you copy and paste (any file-code, command-line-code, etc.), try [COLOR="DarkRed"]QUOTE[/COLOR] your information ..  that way does not break down the info and appears to be wrong (less readable).. In the message area from ( Post New Thread or replay an exinting one) click on the [COLOR="DarkRed"]#[/COLOR] character .. add inside [COLOR="DarkRed"]CODE[/COLOR]  and  [COLOR="DarkRed"]/CODE[/COLOR] . that you may whant to type.

---

### Post by usatonycuba on 2011-04-21
> **acii said:**
> ...It appears the referring link causes a DNS error (105: Server Not Found) when the CVS repository server is accessed from the public address. Things work fine when accessing via localhost...
Have you looked if these files have the proper permissions ben set..?... I guess they don't .. since you are able to reach then locally, but not trough  public address..?

---

