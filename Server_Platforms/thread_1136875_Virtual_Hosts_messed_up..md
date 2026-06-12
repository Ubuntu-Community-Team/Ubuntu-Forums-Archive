---
title: "Virtual Hosts messed up."
date: 2009-04-25
forum: Server Platforms
---

### Post by GolemdX on 2009-04-25
OK, I recently had a dumb problem which all I needed to do was portfoward port 80, but instead I changed some stuff with the apache settings. Now, all of the sites only point to the directory of another site.

Here are two of my virtualhost files. The other sites point to where the first site should (and also does).

```
#
#  bowmoreforum.info (/etc/apache2/sites-available/bowmoreforum.info)
#
<VirtualHost *>
        ServerAdmin golemdx@gmail.com
        ServerName  bowmoredir.servehttp.com
        ServerAlias bowmoreforum.info

        # Indexes + Directory Root.
        DirectoryIndex index.php
        DocumentRoot /home/simon/public_html/bowmoreforum.info/htdocs/

        # CGI Directory
        ScriptAlias /cgi-bin/ /home/simon/public_html/bowmoreforum.info/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /home/simon/public_html/bowmoreforum.info/logs/error.log
        CustomLog /home/simon/public_html/bowmoreforum.info/logs/access.log combined
</VirtualHost>
```

```
#
#  heliodore.info (/etc/apache2/sites-available/heliodore.info)
#
<VirtualHost *>
        ServerAdmin golemdx@gmail.com
        ServerName  heliodir.servehttp.com
        ServerAlias heliodore.info

        # Indexes + Directory Root.
        DirectoryIndex index.php
        DocumentRoot /home/simon/public_html/heliodore.info/htdocs/

        # CGI Directory
        ScriptAlias /cgi-bin/ /home/simon/public_html/heliodore.info/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /home/simon/public_html/heliodore.info/logs/error.log
        CustomLog /home/simon/public_html/heliodore.info/logs/access.log combined
</VirtualHost>
```

Please help!

---

### Post by GolemdX on 2009-04-25
I forgot to mention, I'm running ubuntu server 8.04, with desktop and edubuntu installed on top of it.

---

### Post by GolemdX on 2009-04-25
*sigh*, I fixed it. It seems I discarded a link to a file that I thought would be useless.

---

