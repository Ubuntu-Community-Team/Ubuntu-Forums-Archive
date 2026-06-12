---
title: "Mod_Security finally installed but now..."
date: 2012-03-10
forum: Server Platforms
---

### Post by everN00b on 2012-03-10
I'm a noob...in terms of Apache and Linux. 
I've installed the newest version of Ubuntu as well as Apache. I've got mod_security installed, created the mod_security2.so, etc. Now I have no idea where to go from here. I've read a lot of tutorials and documentation from OWASP, gotroot, etc...but the terminology is a bit over my head at this time, to be honest. 
The main tutorial I've been following is [http://cauhoi.wordpress.com/2012/02/28/how-to-install-modsecurity-2-x-on-ubuntu-server-10-04-lts/#more-85](http://cauhoi.wordpress.com/2012/02/28/how-to-install-modsecurity-2-x-on-ubuntu-server-10-04-lts/#more-85) .

Where do I place the mod_security2.so, how do I create rules, etc. 

Any help, advice, further reading would be appreciated :P

---

### Post by Dangertux on 2012-03-10
If you built from source and did 

```

sudo make install

```

You shouldn't have to copy anything to anywhere however you can verify this by doing the following command.

```

find / -type f -name mod*2.so -exec ls -al {} \;

```

Your output should look something like this...

```

-rwxr-xr-x. 1 root root 1138985 Jan 21 13:03 /usr/lib/apache2/modules/mod_security2.so
-rwxr-xr-x. 1 root root 1138985 Jan 21 13:03 /usr/local/modsecurity/lib/mod_security2.so
-rwxr-xr-x. 1 root root 1138985 Jan 21 13:03 /usr/src/modsecurity-apache_2.6.2/apache2/.libs/mod_security2.so

```

As far as installing rules go you will need to do a few things. First you need to make sure mod-security is actually enabled for apache you can confirm with the following command.

```

grep security2_module /etc/httpd/conf/httpd.conf | grep -v '<'

```

Which should return something like this...

```

LoadModule security2_module /usr/lib/httpd/modules/mod_security2.so 

```

If this is commented out then you will need to uncomment it and reload your httpd service

```

sudo service apache2 reload

```

or 

```

sudo service httpd reload

```

As far as rules go you just need to download the rules (I prefer the OWASP core rules set but there are a few others out there. And follow their instructions to activate them, which usually involves simply including the rules in your httpd.conf (which looks like this)

```

<IfModule security2_module>
        Include /etc/httpd/conf/modsecurity_crs/modsecurity_crs_10_config.conf
        Include /etc/httpd/conf/modsecurity_crs/activated_rules/*.conf
</IfModule>

```

Again , after this restart your httpd service.

Hope this helps.

Side note : on the OWASP core rules set you will also need liblua, libxml and lua5.1-dev packages installed on your system (I don't tihnk the guide you're following mentions those)

---

### Post by everN00b on 2012-03-10
Thanks a lot :) Followed what you you said and now the service is running fine!

---

