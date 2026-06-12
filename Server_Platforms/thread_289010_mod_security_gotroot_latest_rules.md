---
title: "mod_security gotroot latest rules"
date: 2006-10-30
forum: Server Platforms
---

### Post by brownrl on 2006-10-30
The latest rules from gotroot ( mod security site ) don't jive with the mod_security that gets installed with apt-get install ...

The latest version of mod_security doesn't like to be made either:

```

root@lounge:~/modsecurity-apache_2.0.3/apache2# make
Makefile:9: /usr/share/apache2/build/special.mk: No such file or directory
make: *** No rule to make target `/usr/share/apache2/build/special.mk'.  Stop.

```

I did a search on here for mod_security and only one guy seems to be running it or trying to. However he is with apache 1.3+ and can't get it to work either.

Can someone point me in the right direction for either getting the latest mod_security through apt-get install... or getting it to compile?

apt is preferred ;)

---

### Post by brownrl on 2006-10-31
bump...

---

### Post by brownrl on 2006-11-01
bump2

Sorry but I can't imagine that something as crucial as mod_security is standing at version 1.8 when version 2.0+ is out and considered to be extremely effective at stopping so many types of hacks. I am going to compile this thing myself some how then post a howto.

---

### Post by liquidpele on 2007-03-17
Yea, I had this same issue....   Here is how I got it working.

First uninstall mod_security (the libapache2-mod-security package) if you already have the 1.8.x version installed.

Next, Download the latest source here:
[http://www.modsecurity.org/download/index.html](http://www.modsecurity.org/download/index.html)

Also, take a look at their installation guide here:
[http://www.modsecurity.org/documentation/modsecurity-apache/2.1.0/html-multipage/02-installation.html](http://www.modsecurity.org/documentation/modsecurity-apache/2.1.0/html-multipage/02-installation.html)
Note it requies mod_unique_id to be installed, so do that.

Ok, so untar the source:
tar -xvzf <packagename>.tgz

Go into the directory, and then into the apache direcotory and find the Makefile.  Open the Makefile to edit it.

change top_dir to this for Ubuntu (this will be different for other distros):
top_dir      = /usr/share/apache2

So then try to run make.  If you get the error below like I did, fear not!

Makefile:25: /usr/share/apache2/build/special.mk: No such file or directory
make: *** No rule to make target `/usr/share/apache2/build/special.mk'.  Stop.

If you get that error, you need to install another package to get that file as noted here:
[http://packages.ubuntu.org.cn/listfiles/44/](http://packages.ubuntu.org.cn/listfiles/44/)

so install that packet (I use apt, but you can use synaptec if you want):
apt-get install apache2-threaded-dev

Then run make again.   If you get the error below like I got, fear not!

In file included from modsecurity.h:40,
                 from mod_security2.c:18:
msc_xml.h:19:31: error: libxml/xmlschemas.h: No such file or directory
msc_xml.h:20:26: error: libxml/xpath.h: No such file or directory
In file included from modsecurity.h:40,
                 from mod_security2.c:18:
msc_xml.h:25: error: expected specifier-qualifier-list before 'xmlSAXHandler'
make: *** [mod_security2.slo] Error 1

So for this, I commented out the libxml2 references.  I did have it installed, but not sure why it wasn't liking it.  Since it's not required for the installation, I just said screw it and commented it out:

Edited Makefile to exclude using libxml2 (Add the # signs in front of these lines):
#INCLUDES = -I /usr/include/libxml2
#DEFS = -DWITH_LIBXML2
#LIBS = -Lmy/lib/dir -lmylib

Run make again, for me it now compiled without errors (some warnings, but you can probably ignore those).

Then run make install:

root@ubuntu:~/modsecurity-apache_2.1.0/apache2# make install
make[1]: Entering directory `/root/modsecurity-apache_2.1.0/apache2'
/bin/sh /usr/bin/libtool --silent --mode=install cp mod_security2.la /usr/lib/apache2/modules/
make[1]: Leaving directory `/root/modsecurity-apache_2.1.0/apache2'

Then I tried to restart apache2:

root@ubuntu:/etc/apache2/mods-enabled# service apache2 restart
 * Forcing reload of apache 2.0 web server...                                   
Syntax error on line 1 of /etc/apache2/mods-enabled/mod-security.load:
Can't locate API module structure `security_module' in file /usr/lib/apache2/modules/mod_security2.so: /usr/lib/apache2/modules/mod_security2.so: undefined symbol: security_module
[fail]

I had to change the module name used for the module from the apache config.  The 1.8.x version uses "security_module", but you need to change this to "security2_module" like so (this is also noted in the modsecurity install guide link above):

LoadModule security2_module modules/mod_security2.so

Then reloading apache and it works!

For anyone interested, the rules for modsecurity2 and apche2 are here:
[http://gotroot.com/tiki-index.php?page=mod_security+rules#download](http://gotroot.com/tiki-index.php?page=mod_security+rules#download)

Have fun.

---

### Post by shamankick on 2007-05-20
i'm new here, and i say " hello everybody" :)

- your way for installing mod-security seem's a bit complicated but maybe work ..

2 things you have to do for a good install :

**mod "unique_id" enabled in apache**
and **apache2-dev installed** use apt-get, after what you can run the " apxs2" compilation command

what i've made to install the mod-security (version 1.9 which is the "production" version):

```
# wget [http://www.modsecurity.org/download/modsecurity-apache_1.9.4.tar.gz](http://www.modsecurity.org/download/modsecurity-apache_1.9.4.tar.gz)
```

untar it
```
# tar zvxf modsecurity-apache_1.9.4.tar.gz
```
move to the apache2 sub-directory
```
# cd modsecurity-apache_1.9.4/apache2
```
run
```
# apxs2 -cia mod_security.c
```
after what, i'don't remenber exactly (sorry) but you get

LoadModule security_module /usr/lib/apache2/modules/mod_security.so

in the httpd.conf, but you have to delete this line and  put it in a file named
mod_security.load in apache2/mod-available (with rw-r-r rights)

-----------------------------

Now we have to install the rules (mod-security version 1.9 for apache2)
check [http://www.gotroot.com/](http://www.gotroot.com/)  to get the rules you need.

create a directory in your apache2 folder : security_rules (in example)
```

# wget [http://www.gotroot.com/downloads/ftp/mod_security/apache2/apache2-gotrootrules-latest.tar.gz](http://www.gotroot.com/downloads/ftp/mod_security/apache2/apache2-gotrootrules-latest.tar.gz)
```

untar the package in the folder you've created "security_rules"
```

#tar zxvf apache2-gotrootrules-latest.tar
```

In your apache2.conf put this line :
Include /etc/apache2/conf_security.conf

then, in apache2 directory create a file named conf_security.conf with this inside :

> 
<IfModule mod_security.c>

# dynamic request only.
#SecFilterEngine DynamicOnly

SecFilterEngine On

SecFilterDefaultAction "deny,log,status:500"

# basic rules.
SecFilterScanPOST On
SecFilterCheckURLEncoding On
SecFilterCheckCookieFormat On
SecFilterCheckUnicodeEncoding Off
SecFilterNormalizeCookies On
# Active la version 1 (RFC 2965) cookies
SecFilterCookieFormat 1

SecServerResponseToken Off

SecFilterForceByteRange 1 255

#fake server banner - NOYB used - no one needs to know what we are using
SecServerSignature "NOYB"

#SecUploadDir /tmp
#SecUploadKeepFiles Off

# Only record the interesting stuff
SecAuditEngine RelevantOnly
SecAuditLog /var/log/apache2/audit_log

#mode debug conf.
SecFilterDebugLevel 0
SecFilterDebugLog /var/log/apache2/modsec_debug_log

# exclude rules.
# THIS LINE HAVE TO BE THE FIRST.
Include /etc/apache2/security_rules/exclude.conf

# Protect rules.
Include /etc/apache2/security_rules/rules.conf

# spam rules.
Include /etc/apache2/security_rules/blacklist.conf

# host, proxy, etc...
Include /etc/apache2/security_rules/blacklist2.conf

# 
Include /etc/apache2/security_rules/useragents.conf

# rootkits protection.
Include /etc/apache2/security_rules/rootkits.conf

# Règle empéchant l'utilisation du serveur comme proxy.
# A utiliser seulement si le serveur n'est pas en mod proxy.
Include /etc/apache2/security_rules/proxy.conf

# Apache2 rules.
Include /etc/apache2/security_rules/apache2-rules.conf

</IfModule>

**adapt this conf file for your server/website**
especially the exclude.conf (which is  in the /etc/apache2/security_rules directory)
This is where you can adjust the "exception" for the filters
have a look there is rules for "phpbb" or "wiki" .
i'have to setting up some exclude rules for my forum because i get some error500 when
i use administration control panel or U2U management
Sometime for installing some php script you can have to  "a2dismod mod_security"
especially if you use a "php installer" (= web installer)

that's all folks
sorry for my bad english
 Ubuntu Feisty server
:popcorn:

---

### Post by drhiii on 2007-07-02
Did you ever get around to creating a HOWTO for Modsec v 2.0+?



> **brownrl said:**
> bump2

Sorry but I can't imagine that something as crucial as mod_security is standing at version 1.8 when version 2.0+ is out and considered to be extremely effective at stopping so many types of hacks. I am going to compile this thing myself some how then post a howto.

---

### Post by drhiii on 2007-07-03
I followed both procedures mentioned above to get modsec working.  Neither procedure worked.  I see no output in the /var/log/apache2 directories.

Anyone get modsecurity WITH downloadable rules, working?  I have to agree with the original poster... something as vital as modsec that has not been ported to Ubuntu is a bit amazing at this point.  I know there is a version for 1.8, but it cannot utilize any of the rulesets from Modsecurity or GetRoot.  

Anyone have this working, with rules???  From any version?

---

### Post by drhiii on 2007-07-03
Ok, I finally tweaked up a 1.9 version of Modsecurity that can use rules.  

But... has anyone managed to get Modsecurity 2.0+ working with Ubuntu Feisty?  If yes, pointers??

---

### Post by shamankick on 2007-08-09
> **drhiii said:**
> I followed both procedures mentioned above to get modsec working.  Neither procedure worked.  I see no output in the /var/log/apache2 directories.


mod-security output are writed in the /var/log/apache2/**error.log** file 

> Anyone get modsecurity WITH downloadable rules, working?
Anyone have this working, with rules???  From any version?

it's fully working for me on  my Feysti server install
(mod-security 1.9 rules from [http://www.gotroot.com/](http://www.gotroot.com/) )

\\:D/

---

### Post by deptrai on 2007-10-05
I'm install apache2-prefork-dev and apache2-threaded-dev apache2-dev.
special.mk is in the directory: /usr/share/apache2/build/

Config: top_dir = /usr/share/apache2

---

