---
title: "Apache 2 with Virtual Hosts problem"
date: 2006-12-13
forum: Server Platforms
---

### Post by qwert231 on 2006-12-13
I'm trying to set up two (2) sites on my Apache2 server. I created 2 files in the sites-available folder:
mark.phillk.net
[www.greatwhitedata.com](www.greatwhitedata.com)

I then did:
 sudo a2ensite mark.phillk.net
 sudo a2ensite [www.greatwhitedata.com](www.greatwhitedata.com)
 /etc/init.d/apache2 restart

After the restart I get this:
open: Permission denied
 * Forcing reload of apache 2.0 web server...                                             apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 13424?) not running
open: Permission denied
                                                                                   [fail]

What do I need yet to do? I installed Apache2, PHP5, MySQL, and all the mods... 
Here is what I have in sites-enabled:
mark.phillk.net
[www.greatwhitedata.com](www.greatwhitedata.com)

---

### Post by Terryj1974 on 2006-12-13
You may need to restart apache as a super user (sudo /etc/init.d/apache2restart) in order to get it to restart. 

Let me know if this doesent work, and I will keep looking at it.

TJ

---

### Post by qwert231 on 2006-12-13
True, I tried again as sudo and got this:
 * Forcing reload of apache 2.0 web server...                                         apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                               [fail]


(I had tried that, but forgot to post those results...)

Any new thoughts?

---

### Post by pppetter on 2006-12-14
hi there!
Just thinking...have you disabled the "default" site that's automatically enabled? and please go ahead and post your site-available files, and we'll see if there's something strange with them :)

---

### Post by qwert231 on 2006-12-14
Hmm... yes... I did disable default...
mark@linux800:/etc/apache2/sites-available$ ls
default  mark.phillk.net  [www.greatwhitedata.com](www.greatwhitedata.com)  [www.greatwhitedata.com~](www.greatwhitedata.com~)

mark@linux800:/etc/apache2/sites-enabled$ ls
mark.phillk.net  [www.greatwhitedata.com](www.greatwhitedata.com)

What do you make of that?

---

### Post by MJN on 2006-12-15
That 'error' is only a warning - i.e. Apache is actually running (check with **ps aux |grep -i apache**) but it's having to assume 127.0.0.1 is its name. The reason it needs a name is because you've told it to use name-based virtual hosting and hence it needs to know what it's called (specifically it needs to know what each of its virtual hosts are called).
 
I'm guessing that inside your <VirtualHost></VirtualHost> container(s) you haven't specified a **ServerName** e.g. **ServerName [www.greatwhitedata.com]("http://www.greatwhitedata.com")** (also put a **ServerAlias greatwhitedata.com** in too for good measure).
 
(Just noticed that [Fail] bit - check /var/log/apache2/error.log (or whatever yours is called) to check for any config errors - however I'd have expected to see any on the terminal output)
 
Mathew

---

### Post by chrisfay on 2006-12-15
> You may need to restart apache as a super user (sudo /etc/init.d/apache2restart) in order to get it to restart. 

It's recommended to use:

```
sudo apache2ctl restart
```

....instead

---

### Post by qwert231 on 2006-12-15
Hmm... 
I was able to fix the fail. I didn't have folders for the logs...
However, I still get this on the Apache2 restart:
mark@linux800:/home/www/web$ sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server...                                    apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                          [ ok ]


Here is the [www.greatwhitedata.com](www.greatwhitedata.com) file:
#
#  [www.greatwhitedata.com](www.greatwhitedata.com) (/etc/apache2/sites-available/www.greatwhitedata.com)
#
<VirtualHost *>
        ServerAdmin [email]qwert231@yahoo.com[/email]
        ServerName  [www.greatwhitedata.com](www.greatwhitedata.com)
        ServerAlias greatwhitedata.com

        # Indexes + Directory Root.
        DirectoryIndex index.php
        DocumentRoot /web/GreatWhite/

        # CGI Directory
        ScriptAlias /cgi-bin/ /web/GreatWhite/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /home/www/GreatWhite/logs/error.log
        CustomLog /home/www/GreatWhite/logs/access.log combined
</VirtualHost>

---

### Post by MJN on 2006-12-15
I believe /etc/init.d/apache2 just calls /usr/sbin/apachectl anyway so a little extra PID/config checking doesn't hurt! ;)
 
Mathew

---

### Post by chrisfay on 2006-12-15
> I believe /etc/init.d/apache2 just calls /usr/sbin/apachectl anyway so a little extra PID/config checking doesn't hurt! 

ahhh....sneaky sneaky

> ServerName [www.greatwhitedata.com](www.greatwhitedata.com)

Does it make a difference if you list your domain in quotes?
```
ServerName "www.greatwhitedata.com"
```

Not sure if it does, but thats how I've always seen it...

---

### Post by MJN on 2006-12-15
As mentioned, Apache **is running** - check it with **ps aux |grep -i apache**.
 
What happens when you browse to [http://127.0.0.1](http://127.0.0.1) on your server?
 
And what's the config in /etc/apache2/sites-available/mark.phillk.net (as that's your default server - it's done alphabetically which is why you had a 00default entry in sites-enabled before you deleted it!)
 
(EDIT: Sorry Chris - we're posting simultaneously here! No, the quotes don't matter - they're just useful if you've got special characters within a directive and in the case of ServerName this would be something you wouldn't want anyway. The quotes don't matter either way.)
 
Mathew

---

### Post by chrisfay on 2006-12-15
> The quotes don't matter either way

.....good to know. thnkx

---

### Post by qwert231 on 2006-12-15
Wow, two helping at once... Thanks.

127.0.0.1 is the mark.phillk.net site.

My Firewall/Router has some issues, so I can't browse to [www.greatwhitedata.com](www.greatwhitedata.com) and see the site. (I see the router.) Can you guys tell me what you see?


Here's the other one...
#
#  mark.phillk.net (/etc/apache2/sites-available/mark.phillk.net)
#
<VirtualHost *>
        ServerAdmin [email]qwert231@yahoo.com[/email]
        ServerName  mark.phillk.net
        ServerAlias mark.phillk.net

        # Indexes + Directory Root.
        DirectoryIndex index.php
        DocumentRoot /web/

        # CGI Directory
        ScriptAlias /cgi-bin/ /web/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /home/www/web/logs/error.log
        CustomLog /home/www/web/logs/access.log combined
</VirtualHost>

---

### Post by MJN on 2006-12-15
The Great White homepage of course! ;)
 
Whatever you did in the last two minutes fixed it...
 
(I'd guess it was a router port forward issue)
 
Mathew

---

### Post by qwert231 on 2006-12-15
Ok... I need to set up some virtual folders, like images, for these sites. Do I put that in apache2.conf? Or the Virtual Host files?

---

### Post by MJN on 2006-12-15
I'm not sure I follow - can you elaborate?
 
However, what I can say is that now all your 'site specific' (i.e. stuff that's not relevent to the server as a whole, or other virtual sites you host) config now goes inside your VirtualHost container.
 
Mathew

---

### Post by pppetter on 2006-12-15
Hello Again!

Once you posted your Virtualhosts file, i can see the error right away. 

So if you want to get rid of the error message(even thou your server is running and works) 
Put 
> NameVirtualHosts *
At the top of your virtualhosts files(before the <VirtualHost *>). This argument tells the server what IP it should use for that specific virtual host. Since you only have one IP, you can go ahead with any ( * ). This is the same thing that the server now does for you when it can't find that argument.

If you however at some point install another networkcard, and thus have two IP-adresses the NameVirtualHosts argument can be used to set which IP that should be used for which VirtualHost.

---

