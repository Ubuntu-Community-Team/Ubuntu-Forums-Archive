---
title: "Promted to download Perl scripts instead of run them with apache2"
date: 2012-07-02
forum: Server Platforms
---

### Post by octarice on 2012-07-02
I have been unable to run perl scripts from my home server.  I don't get  an error message when trying to run the script but I do get prompted to  download it. I know it is not a headers problem and that the perl  syntax is correct, I also do not think it is a permissions problem since I  have ran chmod a+x and chmod 755 on the script. This leads me to believe  its a problem with the way I configured apache but from what I read in  my /etc/apache2/sites-available it should be set up correctly. 

I'm pretty new to this, but I really did go out and for a solution to this for a now. However, my inexperience and lack of direction is making me quite flustered.  Here is my sites available in hopes of a solution and peer review.

```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /var/www
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI +Includes MultiViews Indexes SymLinksIfOwnerMatch
        AddHandler cgi-script .cgi .pl .py
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```

---

### Post by hawkmage on 2012-07-02
Are you setting the content MIME type in the output of your script?

---

### Post by octarice on 2012-07-02
> **hawkmage said:**
> Are you setting the content MIME type in the output of your script?

I think so, the script uses ```
print "Content-Type: text/htm\n\n";
``` right after the hash bang. I am pretty new with perl but that should be correct.

---

### Post by Lars Noodén on 2012-07-02
There's at least part of your problem it should read:

```

print "Content-Type: text/htm**l**\n\n";

```

text/htm is not a valid MIME type, it needs to be text/html.

---

### Post by SeijiSensei on 2012-07-02
You might want to consider installing [mod_perl]("http://perl.apache.org/") rather than using cgi-bin if you're writing perl scripts to generate web pages.  Install it with "sudo apt-get install libapache2-mod-perl2".  If you want the documentation as well, install libapache2-mod-perl2-doc.

---

