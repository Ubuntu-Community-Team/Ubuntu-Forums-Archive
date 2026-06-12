---
title: "virtual hosts, why so difficult"
date: 2006-01-09
forum: Server Platforms
---

### Post by pieboy314 on 2006-01-09
I have read 20+ threads on this board on how to do this...

I have read 10+ external pages via google on how to do this...

I have read the Apache2 docs over and over and over...

I have tried 100 combinations of set-ups to handle this...

why, oh why, is it so difficult to set up the sites-enabled directory to host different domains under a single IP?!?! if I hit "refresh" on more time have have my root index.html page staring me in the face one more time, I will snap.

I am not an idiot. I can follow instructions. This process took me all of 30 seconds under IIS. 

OK, I am sorry, this post is a waste, but I feel so much better getting this off of my chest. I guess my point is, it looked so much easier under the Apache1 process, was it? can I use that process on Apache2? 

I see they put the httpd.conf file in there, can it be used, the old fashioned way?

---

### Post by LordHunter317 on 2006-01-09
Are you using name-based virtual hosting?

If so, you are accessing the site by name, not IP, right?

---

### Post by [Rui] on 2006-01-09
It's so easy...

echo "IP   foo bar foobar" >> /etc/hosts

Listen IP:PORT
NameVirtualHost IP:PORT

<VirtualHost foo:PORT>
   ServerName foo
   TransferLogs logs/foo-access_log
   ErrorLor logs/foo-error_log
   DocumentRoot /srv/www/foo
...
</VirtualHost>

<VirtualHost bar:PORT>
   ServerName bar
   TransferLogs logs/bar-access_log
   ErrorLor logs/bar-error_log
   DocumentRoot /srv/www/bar
...
</VirtualHost>

<VirtualHost foobar:PORT>
   ServerName foobar
   TransferLogs logs/foobar-access_log
   ErrorLor logs/foobar-error_log
   DocumentRoot /srv/www/foobar
...
</VirtualHost>

---

### Post by pieboy314 on 2006-01-09
[QUOTE=LordHunter317]Are you using name-based virtual hosting?

If so, you are accessing the site by name, not IP, right?[/QUOTE]

I want to eventually host multiple domains...

I have DNS pointing a domain's A records at my IP.

I setup a bajillion different config files in the /etc/apache2/sites-available/ directory ranging from the simple,

> 
<VirtualHost *>
ServerName mydomain.com
DocumentRoot /var/www/site/
</VirtualHost>


to coping the default file and chaning all the values that I thought I needed to.

always remembering to symlink them to the /etc/apache2/sites-enabled directory, and restart Apache2

but every stinking time I checked mydomain.com, I get the default page located at /var/www/

..but I am now so confused, I need a break and a deep breath and I will go back at it again, starting all over and thinking, "keep it simple"

thanks for the concern and advice, I will keep you posted.

---

### Post by LordHunter317 on 2006-01-09
Well, I suspect you're breaking the golden rule: your NameBasedVirtualHost and VirtualHost Directives must match exactly.

Thus, if you write NameBasedVirtualHost *:80

You must write <VirtualHost *:80>.  It simply will not work otherwise.

As is, I'm 99% positive your vhosts are invalid.

---

### Post by pieboy314 on 2006-01-09
[QUOTE='[Rui]']It's so easy...

echo "IP   foo bar foobar" >> /etc/hosts

Listen IP:PORT
NameVirtualHost IP:PORT

<VirtualHost foo:PORT>
   ServerName foo
   TransferLogs logs/foo-access_log
   ErrorLor logs/foo-error_log
   DocumentRoot /srv/www/foo
...
</VirtualHost>

<VirtualHost bar:PORT>
   ServerName bar
   TransferLogs logs/bar-access_log
   ErrorLor logs/bar-error_log
   DocumentRoot /srv/www/bar
...
</VirtualHost>

<VirtualHost foobar:PORT>
   ServerName foobar
   TransferLogs logs/foobar-access_log
   ErrorLor logs/foobar-error_log
   DocumentRoot /srv/www/foobar
...
</VirtualHost>[/QUOTE]


is this what your "default" file would look like? do you choose to all your domains under one file? or have you just pasted the 3 files in succesion?

is so, can you show we what an example of these settings would be? 
Listen IP:PORT
NameVirtualHost IP:PORT

(I am using port 80)(and, my IP will vary but I will update it on the DNS records)

---

### Post by pieboy314 on 2006-01-09
followed these steps...

> I recommend following this convention. It makes it much easier to manage when there are a large number of virtual hosts on a server. In the example above, you would create two files, /etc/apache2/sites-available/default and etc/apache2/sites-available/example.com. The /etc/apache2/sites-available/default file would look like this:

NameVirtualHost *
<VirtualHost *>
ServerName incorrect.com
DocumentRoot /var/www/html/default
</VirtualHost>

And the /etc/apache2/sites-available/example.com would look like this:

<VirtualHost *>
ServerName [www.example.com](www.example.com)
ServerAlias example.com
DocumentRoot /var/www/html/example.com/html
CustomLog logs/www.example.com-access_log common
</VirtualHost>

Then, create symlinks to the files in the /etc/apache2/sites-enabled directory with the ln -s command: ln -s /etc/apache2/sites-available/example.com /etc/apache2/sites-enabled/example.com.

Now that you have the virtual hosts configured, it's time to test. To start Apache 2, type /etc/init.d/apache2 start. Fire up a browser and head to [www.example.com:80](www.example.com:80). Obviously, this will only work assuming you have a correct virtual host entry for a hostname which has DNS pointing to your server rather than [www.example.com](www.example.com).


guess what i get when I fire up a browser to [www.example.com](www.example.com)..... yep, my default index page. :(

---

### Post by shadowman on 2006-01-11
A couple of things (you may have already done..)
The default server has to have a virtual block so that it is a virtual host as well.
The easiest way I have found to set up virtual hosts is to setup a virtual IP for them to use.  With that said here are my configurations:

Default server:
root@ubuntuserver:/etc/apache2# less sites-enabled/000-default
NameVirtualHost 172.16.0.105  #this is the real ip of my server
<VirtualHost ubuntuserver.localnet.net:80>
        ServerAdmin webmaster@localhost
        ServerName  ubuntuserver.localnet.net
        DocumentRoot /srv/www/apache2-default/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /srv/www/apache2-default/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 172.16.0.0/255.255.0.0 ::1/128
    </Directory>

</VirtualHost>

virtual server:
root@ubuntuserver:/etc/apache2# less sites-enabled/multimedia

NameVirtualHost 172.16.0.110:80   #NameVirtualHost uses virtual ip (eth0:0)
<VirtualHost mymultimedia.servemp3.com:80>
        ServerAdmin [email]----------@yahoo.com[/email]
        ServerName mymultimedia.servemp3.com
        DocumentRoot /srv/www/vhosts/multimedia/
        <Directory /srv/www/vhosts/multimedia/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

Is it harder than IIS?  Initially yes.  But you have to remember that with power and flexibility comes some complexity.  In other words it is your choice how much to secure or not secure your server, define various DocumentRoots, cgi locations, what kinds of views to allow, etc. etc.  After you do it a couple of times it becomes second nature and is as easy as IIS.

hth

---

### Post by LordHunter317 on 2006-01-11
Except that Apache isn't more power or flexible in IIS in this regard.  It's actually slightly less so.

The configuration file is a known weak part about Apache.  They just had a humorous presentation about it at the last ApacheCon.

---

### Post by pieboy314 on 2006-01-11
well, I ended up getting it sorted... naturally it turned out to be my own fault.

I had an alias setup to map URLs outside of var/www/ once I removed that... everything got a lot easier.

thanks for all the help on this one guys.

---

