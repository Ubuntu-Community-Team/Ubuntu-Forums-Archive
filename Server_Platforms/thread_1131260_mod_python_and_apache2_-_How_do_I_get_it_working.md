---
title: "mod_python and apache2 - How do I get it working?"
date: 2009-04-20
forum: Server Platforms
---

### Post by TCarr on 2009-04-20
I been googling and searching this forum for about an hour and tried various suggestions and still can't get this working.

I have Ubuntu 8.04 LTS server.
I used apt-get install libapache2-mod-python to install it.
I edited my /etc/apache2.conf CGI directories area (virtual hosting system, btw) as follows:

```

# CGI Script Configuration
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory /var/www/public_html/*/>
#AddHandler cgi-script .cgi
AddHandler cgi-script .cgi .py
#AddHandler cgi-script .py
Options +ExecCGI +Includes
AddHandler mod_python .py
PythonHandler mod_python.publisher
PythonDebug On
AddType text/html .shtml
AddHandler server-parsed .shtml
AddOutputFilter INCLUDES .shtml
</Directory>

```

This is my Python test program:

```

from mod_python import apache

def handler(req):
  req.content_type = 'text/plain'
  req.write("Hello World!")
  return apache.OK

```

In Firefox 3, I get a pop-up window asking me what application I want to open the .py file with.

In IE 7, it just dumps the source code to test.py without line breaks.

Can someone please point me in the right direction? 

Thanks...

---

### Post by johnl on 2009-04-20
Hi,

Did you enable the module? If not, you'll need to do that and then restart apache.

```

sudo a2enmod python
sudo /etc/init.d/apache2 force-reload

```

---

### Post by TCarr on 2009-04-20
Yes, I did that and it said that the module is already installed. I've also restarted using the /etc/init.d/apache2 force-reload and after that, just to be extra sure I did an /etc/init.d/apache2 restart.

I seem to not be able to get it to work.

---

### Post by example010 on 2009-04-21
follow this instruction

[http://www.howtoforge.com/embedding-python-in-apache2-with-mod_python-debian-etch]("http://www.howtoforge.com/embedding-python-in-apache2-with-mod_python-debian-etch")

---

### Post by TCarr on 2009-04-22
I did that, followed the instructions exactly and Firefox 3 still wants to download the test.py file while IE 7 just prints the source code without line feeds.

It still won't work.

Furthermore, if I do the psp route, I get a 403 Forbidden error instead of anything else.

I've even tried to make the test files executable with no different results.

---

### Post by TCarr on 2009-04-22
I just took a look at /var/log/apache2/access.log and /var/log/apache2/error.log and no log entries were made from trying these files.

---

### Post by TCarr on 2009-04-22
Got it working. Instead of putting the AddHandler and other Python references in /etc/apache2/apache2.conf, I put them in /etc/apache2/sites-enabled/000-default and it works fine.

Thank you for the link. I led me to the answer, eventually. :)

---

### Post by Saruman_W on 2009-09-25
I am trying to get this to work as well. I have looked at every single tutorial I can find and none of them work.

I install both apache2 and libapache2-mod-python through apt-get. And I follow the instructions on modifying the default. Restart apache and I get this:

apache2: Syntax error on line 185 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/mods-enabled/mod_python.load: No such file or directory

Apparently mod_python.load is nowhere to be found! I made sure to install libapache2-mod-python so that should mean that all the files should be in there. but they're not! What's going on?

Where can I download this mod_python.load file or make it myself?

---

