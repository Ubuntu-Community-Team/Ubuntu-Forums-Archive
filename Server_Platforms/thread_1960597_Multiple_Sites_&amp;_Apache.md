---
title: "Multiple Sites &amp; Apache"
date: 2012-04-17
forum: Server Platforms
---

### Post by jonedney on 2012-04-17
Hello Everyone,

This is kind of an Apache question, but everyone has been so helpful here, I wanted to ask here before I went onto the Apache community.

I recently setup Apache on an Ubuntu 10.04 LTS system, and have set it up to handle 3 different domains (using Virtual Hosts).  I have the DNS of my domain in question (jonedney.me) hosted elsewhere and an A record pointing to my VPS IP.  What I am running into now, is that A record propagated properly, but it points my domain to the main www directory; it isn't recognizing that the domain should be accessing another folder to display the proper content.

Anyone have any ideas?

Thank you,
Jon Edney

---

### Post by mörgæs on 2012-04-17
Moved to the server forum.

---

### Post by sj1410 on 2012-04-18
[http://www.techpage3.com/2011/01/hosting-multiple-websites-with-apache.html](http://www.techpage3.com/2011/01/hosting-multiple-websites-with-apache.html)

---

### Post by jonedney on 2012-04-18
Hello,

Great tutorial.  I followed it and received this when I reloaded Apache.

```
root@jonedneycreative:~# /etc/init.d/apache2 reload
 * Reloading web server config apache2                                                                                                       [Wed Apr 18 20:46:15 2012] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                                                                                      [ OK ]

```

Additionally, going to the specified domain still pulls content from the default www directory.

Thank you,
Jon Edney

---

### Post by jonedney on 2012-04-18
Additionally, I'm considering re-installing and configuring Apache, so it's a clean config for VirtualHosts.

Jon

---

### Post by SeijiSensei on 2012-04-18
Are you asking how to point domain.name to a different location on your server than [www.domain.name?](www.domain.name?)

If so, just make sure you have an A record for the base domain name that points to your server's IP address and create separate VHost definitions with "ServerName domain.name" and "ServerName www.domain.name".  Make sure these definitions don't include a ServerAlias that points to the other name.

---

### Post by jonedney on 2012-04-18
Hello!

What I did was the following:
```

mkdir /var/www/www.jonedney.me
mkdir /var/www/www.jonedney.me/www
mkdir /var/www/www.jonedney.me/cgi-bin
mkdir /var/www/www.jonedney.me/logs
```

Then I created a sites-available document for my site.

```
vi /etc/apache2/sites-available/www.jonedney.me
```[FONT=Courier New]

And it looks like this

[/FONT]```
<VirtualHost *>
        ServerAdmin sysadmin@jonedneycreative.com
        ServerName  www.jonendey.me
        ServerAlias jonedney.me

        # Indexes + Directory Root.
        DirectoryIndex index.php index.html
        DocumentRoot /var/www/www.jonedney.me/www/

        # CGI Directory
        ScriptAlias /cgi-bin/ /var/www/www.jonedney.me/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /var/www/www.jonedney.me/logs/error.log
        CustomLog /var/www/www.jonedney.me//logs/access.log combined
</VirtualHost>
```[FONT=Courier New]

Then I enabled the site and restarted Apache

[/FONT]```
a2ensite www.jonedney.me
service apache2 restart
```[FONT=Courier New]
[/FONT][FONT=Courier New]
Currently, I have an A record pointing my Domain to my VPS IP, and the domain is working properly, but it's pulling '/var/www/' instead of 'var/www/www.jonedney.me/www' as defined in the VirtualHost.

Thank you,
Jon Edney
[/FONT]

---

### Post by SeijiSensei on 2012-04-18
Do you have a NameVirtualHost directive in /etc/apache2/apache2.conf?  I have a clean version of apache2, and that directive isn't included there.

[s]Edit apache2.conf and place 

```
NameVirtualHost *:80
```

above the "Include sites-enabled/" directive.[/s]  Don't do this, read on.

In /etc/apache2/ports.conf, you'll see the declaration "NameVirtualHost *:80".  That tells apache2 to use name-based virtual hosting for requests matching "*:80".  You need to edit your virtual host definitions to match that pattern like this:

```
<VirtualHost *:80>
     stuff
</VirtualHost>

```

then restart apache. (Note that you must include the port specification for name-based virtual hosting.)

---

### Post by jonedney on 2012-04-18
Hello,

Thanks for your post with some direction.  I've made the following changes, to receive the same problem.

```
# Include the virtual host configurations:
NameVirtualHost *:80
Include sites-enabled/
```

And then I altered my sites-available/www.jonedney.me to:
```

<VirtualHost *:80>
        Stuff
</VirtualHost>
```

Then restarted Apache, received this error on restart, and then the same error of redirection:

```
* Reloading web server config apache2
[Thu Apr 19 04:00:58 2012] [warn] NameVirtualHost *:80 has no VirtualHosts
```

Thank you,
Jon Edney

---

### Post by SeijiSensei on 2012-04-18
I made a mistake when I told you to add the NameVirtualHost directive to apache2.conf. It turns out that declaration is already loaded in the /etc/apache2/ports.conf file included from apache2.conf.  That redundancy causes the warning you saw reported, so if you remove that statement and restart, you shouldn't see the warning any more.  I confirmed this by running a simple apache2 instance and adding then deleting the redundant NameVirtualHost directive.

Even though you get the warning your virtual hosts should now work correctly.  To be sure, I ran a test parallel to yours where I created a new configuration in /sites-availble/ with a ServerName declaration and a custom DocumentRoot, and a symbolic link to that configuration in /sites-enabled/. I left the Ubuntu defaults /sites-available/default and /sites-enabled/001-default alone. Then I restarted apache2.

I get the expected result when I use a browser.  If I enter a URL with the ServerName I get the custom site.  If I connect to localhost or one of the machine's IP addresses, I get the Ubuntu default page at /var/www/index.html.

Your original configuration didn't work because you used
```
<VirtualHost *>
```
which didn't match the "*:80" pattern.  In that case Apache returns the default page and not your custom index.  Now that you have *:80 in your <VirtualHost> container, you should get the index of DirectoryRoot when you request ServerName (or any existing ServerAlias entries).

Hope that makes sense!  If not, ask me again.

---

### Post by jonedney on 2012-04-19
Hello!

Interesting, I think I must be missing something somewhere; I've got to be missing something somewhere.

I removed the 'NameVirtualHost' line from apache2.conf, and ensured that my 'sites-available/www.jonedney.me' has <VirtualHost *:80>, and then restarted Apache.  I didn't get an error message, but going to the domain still pulls content from '/var/www' and not '/var/www/www.jonedney.me/www' as I specified in the VirtualHost settings as document root for that domain name.

Frustrating!

---

### Post by SeijiSensei on 2012-04-19
Something isn't matching correctly then.  Perhaps your using [http://server/](http://server/) as the URL and you only have "ServerName server.domain.name" defined in the <VirtualHost> stanza?  If so, add a "ServerAlias server" directive as well.

What do you see in /var/log/apache2?  How about those custom logs you defined in <VirtualHost>?

---

### Post by jonedney on 2012-04-19
First of all, I appreciate all of your help in your posts for this Ubuntu newbie here.  

As I was going to double-check things, I noticed something simple that I didn't even consider checking: jonedney.me directs to the proper location, while [www.jonedney.me](www.jonedney.me) doesn't.  This don't make sense to me.

Jon

---

### Post by newbie-user on 2012-04-19
What you could do is set up a wildcard for your domain *.jonedney.me on whatever DNS service you use and point it to a CNAME record for your domain.

Alternatively, you could set up a sites-available file with ServerName [www.jonedney.me](www.jonedney.me) and point that to the correct ServerRoot.

Or, like SeijiSensei said, add a ServerAlias.

---

### Post by jonedney on 2012-04-19
Hello!

I wasn't aware I could have 2 server alias!  When I had 'ServerAlias jonedney.me' I didn't know I could add a second.

```
ServerAlias jonedney.me www.jonedney.me
```

Did the trick!

I think I'll enjoy the fact that it works for a day, and then move on to try and get a mail server set up!

Thanks for the guidance!
Jon Edney

---

