---
title: "How to recompile mod_ssl for Apache2?"
date: 2009-05-01
forum: Server Platforms
---

### Post by evank on 2009-05-01
**A disclaimer:** I'm moderately experienced with Linux, but not too experienced in system administration, so pardon me if I'm being stupid.

I'm wanting to run Apache with [SNI (server name indication)]("http://en.wikipedia.org/wiki/Server_Name_Indication") in order to use name-based SSL virtual hosts, using the Apache from Ubuntu's apt repositories.  In order to do this, I have to recompile OpenSSL, and patch then recompile mod_ssl.

For OpenSSL, I could either recompile the version Ubuntu comes with (0.9.8g) with the *enable-tlsext* flag, or compile the latest stable version (0.9.8.k) which has that flag enabled by default.  I chose to use 0.9.8k, and configured it with the /usr prefix, so it replaces Ubuntu's current version.
```
wget http://www.openssl.org/source/openssl-0.9.8k.tar.gz
cd /usr/src/
sudo tar xvzf ~/openssl-0.9.8k.tar.gz
cd openssl-0.9.8k
sudo ./config –prefix=/usr
sudo make && sudo make test
sudo make install
```

That goes off without a hitch, so the next step is to patch & recompile mod_ssl.  After installing the apache2-src and apache2-prefork-dev packages (prefork because PHP doesn't play nice with threads), I unzip and patch the mod_ssl source.
```
wget https://sni.velox.ch/misc/httpd-2.2.x-sni.patch
cd /usr/src/
sudo tar xvzf apache2.tar.gz
sudo mv apache2 httpd-2.2.11
sudo patch --verbose -p1 -d /usr/src/httpd-2.2.11/ -i ~/httpd-2.2.x-sni.patch
```

So far, so good.  But now, I'm unsure of exactly how to compile just the module as a shared dynamic library...Do I need to run the configure script in /usr/src/apache?  Do I need to use the exact same config options Apache was originally built with? If so, how do I find them -- keeping in mind that I just installed from apt rather than rolling my own apache?

---

### Post by zeepal on 2009-05-14
Hello Evank,

First up: Welcome to Ubuntu Forums!

Now i'm not very experienced either but I have a "workaround" to compile the "mod_ssl.so" file to copy to the correct folder location for SNI to work.

After all the steps you have done in your post I ran these commands to compile Apache (It doesn't appear to install into Ubuntu's default folder and I cant find the correct configure setting for Ubuntu):
```
./configure -enable-ssl=shared
make
make install
```

I then stopped Apache2 and copied the file from "/usr/local/apache2/modules/mod_ssl.so" to "/usr/lib/apache2/modules/mod_ssl.so" with:
```
cp /usr/local/apache2/modules/mod_ssl.so /usr/lib/apache2/modules/mod_ssl.so
```

I then started Apache2 and SNI is all working.

Here is my website config file:
```
<VirtualHost *:443>
	SSLEngine on
	SSLCertificateFile /etc/apache2/sslcertificates/zeepal.net.crt
	SSLCertificateKeyFile /etc/apache2/sslcertificates/zeepal.net.key
	ServerName tds.zeepal.net:443
	SSLProtocol all -SSLv2 -SSLv3
	DocumentRoot /var/www/tds.zeepal.net
</VirtualHost>
```

If someone can please provide a proper way of getting mod_ssl.so for the source code (If there is) please let us know.

I have attached my mod_ssl.so file if my instructions done work (as I was playing around for a while).
It has been compiled for Apache2.2.11-2ubuntu2 with "http://people.apache.org/~fuankg/diffs/httpd-2.2.x-sni.diff"

FYI: I choose to recompile OpenSSL from Ubuntu with *enable-tlsext*

Hope this helps you Evank.

---

### Post by zeepal on 2009-08-15
Hello Guys,

Sorry to resurrect an old thread but I have a better answer now on the compiling of Apache 2.2 with SNI.

I have recently setup SNI again on my server and added it to my documentation website (doc.zeepal.net) for all to see in how I did it.

I have the document below to help other people setup SNI on Ubuntu until it comes precompiled (I believe Karmic will have it correct?)

_**Prerequisites**_

   1. APT Packages: "zlib1g-dev" & "libssl-dev"

**_Downloading OpenSSL and Apache2 Source Code_**

   1. Login: To the Server
   2. Run: "sudo apt-get source apache2 openssl" 

_**Enabling SNI in OpenSSL Source**_

   1. Change Directory: "./openssl-0.9.8g"
   2. Run: "sudo ./config --prefix=/usr --openssldir=/usr/lib/ssl no-idea no-mdc2 no-rc5 zlib enable-tlsext no-sslv2"
   3. Watch & Wait: For OpenSSL to be configured ready for compiling, Watch for errors and repair manually (You shouldn't continue if errors aren't repaired)
   4. Run: "sudo make depend"
   5. Watch & Wait: For OpenSSL's Dependancys to be Compiled, Watch for errors and repair manually (You shouldn't continue if errors aren't repaired)
   6. Run: "sudo make"
   7. Watch & Wait: For OpenSSL to be Compiled, Watch for errors and repair manually (You shouldn't continue if errors aren't repaired)
   8. Run: "sudo make install"
   9. Watch & Wait: For OpenSSL to be installed, Watch for errors and repair manually (You shouldn't continue if errors aren't repaired) 

_**Enabling SNI in Apache 2.2**_

   1. Save: "https://sni.velox.ch/misc/httpd-2.2.x-sni.patch" on the server
          * Disclosure: I take no credit for work on the file above.
          * Reference: "https://sni.velox.ch/misc/httpd-2.2.x-sni.patch" 
   2. Run: "sudo patch --verbose -d apache2-2.2.11/modules/ssl/ -i httpd-2.2.x-sni.patch"
   3. Watch: For errors and repair manually (You shouldn't continue if errors aren't repaired)
   4. Change Directory: "./apache2-2.2.11"
   5. Run: "sudo ./configure --enable-layout=Debian -enable-ssl=shared --enable-mods-shared=all --enable-deflate --with-program-name=apache2"
   6. Watch & Wait: For Apache2 to be configured ready for compiling, Watch for errors and repair manually (You shouldn't continue if errors aren't repaired)
   7. Run: "sudo make"
   8. Watch & Wait: For Apache2 to be compiled, Watch for errors and repair manually (You shouldn't continue if errors aren't repaired)
   9. Run: "sudo make install"
  10. Watch & Wait: For Apache2 to be installed, Watch for errors and repair manually (You shouldn't continue if errors aren't repaired)
  11. Save: "LoadModule log_config_module /usr/lib/apache2/modules/mod_log_config.so" in a new file called: "/etc/apache2/mods-available/log.conf"
  12. Run: "do ln -s /etc/apache2/mods-available/log.conf /etc/apache2/mods-enabled/log.conf"
  13. Edit: "/etc/apache2/apache2.conf"
         1. Add: "NameVirtualHost *:443" just before "Include /etc/apache2/sites-enabled/" 
  14. Run: "sudo /etc/init.d/apache2 stop"
  15. Wait: For Apache 2.2 to stop
  16. Run: "sudo /etc/init.d/apache2 start"
  17. Watch & Wait: For Apache2 to be started, Watch for errors and repair manually (You shouldn't continue if errors aren't repaired) 

_**Notes**_

May not need to recompile OpenSSL 0.9.8g as it seems it comes precompiled with "enable-tlsext". 

Hopefully this helps you guys.

---

### Post by gali98 on 2009-09-29
For others:
Yes Karmic will have SNI:
[https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/184131](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/184131)

Kory

---

### Post by krishanuofficial on 2012-01-23
Thanks zeepal!!! Your mod_ssl.so file has helped a lot..

---

