---
title: "Vhost setup problems"
date: 2009-05-12
forum: Server Platforms
---

### Post by chili_666 on 2009-05-12
Hello,

quite frankly - I don´t get it.

I have a ubuntu-server running apache2. I already have to virtual hosts setup that work like a breeze. I´ve been trying to setup a third one now, that just doesn´t want to work.

The server should only be reachable in our LAN - no need for fancy tlds or anything. It´s is just a phone directory for internal use.

Here is whats in my vhost.conf:

```
<VirtualHost 192.168.1.197:*>
ServerName 192.168.1.197
DirectoryIndex index.html
DocumentRoot /opt/klickTel/KTIN/klickTel
<Directory /opt/klickTel/KTIN/klickTel>
Options Indexes FollowSymlinks MultiViews +ExecCGI
AllowOverride None
   Order deny,allow
   Allow from all

</Directory>
</VirtualHost>

```So, the server should be reachable under 192.168.1.197. The other two are sitting on .198 and .199 respectively.

I followed the tutorial on [http://www.64bitjungle.com/tech/apache-virtual-hosts-and-mod_rewrite-on-ubuntu-hardy/ ]("http://www.64bitjungle.com/tech/apache-virtual-hosts-and-mod_rewrite-on-ubuntu-hardy/")but left out the mod_rewrite stuff. 

After that I restarted apache and lo and behold: I get an error message (time-out) in firefox.

Also the install-file tells me to add

```
Alias /klickTel/ "[TARGETDIR]/klickTel/"
Alias /klicktel/ "[TARGETDIR]/klickTel/"

```those two aliases. I have tried adding them to the .conf or even to the httpd.conf - but nothing works.

I am at my wits end - could somebody please push me into the right direction? 

Thanks in advance!

Cheers!

Chili

---

### Post by justatemptest on 2009-05-12
> **chili_666 said:**
> 
After that I restarted apache and lo and behold: I get an error message (time-out) in firefox.

Is apache listening on port 80 on these interfaces? A quick check with netstat will tell you that.

---

