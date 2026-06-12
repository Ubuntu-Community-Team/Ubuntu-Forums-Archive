---
title: "Can't Read CGI Scripts"
date: 2008-05-02
forum: Server Platforms
---

### Post by Black Mage on 2008-05-02
When I try to read CGI scripts, I get an an internal server error 500.
So I went to the logs and it says this:

(8)Exec format error: exec of '/var/www/cgi-bin/test.pl' failed
Premature end of script headers: test.pl

Here is what my setup look like.

The server running is Apache2. In the /etc/apache2/sites-available, I am using the default. In the default file, I have the scripts locations set as:

 ScriptAlias /cgi-bin/ /var/www/cgi-bin/
        <Directory "/var/www/cgi-bin/">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

So what else could I be doing wrong?

---

### Post by ghostknife on 2008-05-03
You need to send headers inside the perl file first.

Send at least the following: (with a blank line after it)
```

Content-Type: text/html

```

If you are doing this but it still doesn't work then try and make the script as plain as possible (only sending a basic message like "hallo world" or something. Test it again, if it still doesn't work, paste the script itself so I can have a look at it.

---

### Post by Black Mage on 2008-05-05
Yes I have that content type already in there, and the same script works under other Linux Distros. The script looks like this:

```

  GNU nano 2.0.6               File: test.pl                                    

###We're inside the text editor now###

#!/usr/bin/perl -w

Content-Type: text/html

print "Content-type: text/html\r\n\r\n";
print "Hello there!<br />\nJust testing some things.<br />\n";

for ($i=0; $i<10; $i++)
{
print $i."<br />";
}

###Done editing text. Save and exit program###


```

---

### Post by arizonagroovejet on 2008-05-05
I'm typing in a commerical break and not on a Ubuntu box but I'm going to suggest that your apache install doesn't know what to do with a perl script. Have you got libapache2-mod-perl2 installed? You may also have to uncomment or add a line in httpd.conf

---

