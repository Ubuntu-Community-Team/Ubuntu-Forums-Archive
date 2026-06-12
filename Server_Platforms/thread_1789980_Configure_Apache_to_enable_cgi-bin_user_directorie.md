---
title: "Configure Apache to enable cgi-bin user directories"
date: 2011-06-24
forum: Server Platforms
---

### Post by yotam on 2011-06-24
What is the right (Ubuntu) way to configure apache2 to allow *all* users to have CGI scripts under their
[FONT="Courier New"]/home/*/public_html/*...*/cgi-bin[/FONT]

That is
[LIST]
[*] Scripts may be located in any sub-directory depth under    [FONT="Fixedsys"]/home/${USER}/public_html[/FONT]
[*] Allow any suffix script file.
[*] Run as user=${USER} with her permissions.
[/LIST]

Currently, I have tried endless configurations settings.
For example
  [FONT="Arial Black"][COLOR="Green"]/etc/apache2/mods-available/userdir.conf[/COLOR][/FONT]
```
<IfModule mod_userdir.c>
  UserDir public_html
  UserDir disabled root

  <Directory /home/*/public_html>
    AllowOverride None
    Options +ExecCGI +Includes MultiViews Indexes SymLinksIfOwnerMatch
    AddHandler cgi-script .cgi .pl .py
    Order allow,deny
    Allow from all
  </Directory>
</IfModule>
```

But in the browser JavaScript console, I still get :(
  **POST [http://localhost/cgi-bin/foo.cgi](http://localhost/cgi-bin/foo.cgi) 404 (Not Found)**

When I do have (0755)
  [FONT="Courier New"]/home/yotam/public_html/foo/cgi-bin/foo.cgi[/FONT]
  [FONT="Courier New"]/home/yotam/public_html/cgi-bin/foo.cgi[/FONT]

---

### Post by ruffEdgz on 2011-06-24
Did you try going to the user directory where your problem is happening?

So in your browser, use the following urls that relates to your setup:
```

A users main site: http://localhost/<username>/

A users directory on their site: http://localhost/<username>/foo/cgi-bin/foo.cgi

A users main cgi-bin location: http://localhost/<username>/cgi-bin/foo.cgi

```
**<username>** = the users that have their public_html directory

Hope that helps.

---

### Post by yotam on 2011-06-24
The reference to foo.cgi is from my (user=yotam) own small application. 
I can *successfully* surf to 
  [FONT="Arial Black"]http://localhost/~yotam/foo[/FONT]
But when activating some (JavaScript) button there, that calls
   **cgi-bin/foo.cgi**
I get that (404 Not Found) error.

I am still trying various dirty solutions such as 
sym-linking this foo.cgi to **/usr/lib/cgi-bin**,
in this case [FONT="Courier New"]/var/log/apache2/error.log[/FONT]
 ```
[error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible
```

My guess is that the clean solution should be in some magic setting in one of
[list]
[*] /etc/apache2/apache2.conf
[*] /etc/apache2/httpd.conf
[*] /etc/apache2/mods-available/userdir.conf
[/list]

---

### Post by yotam on 2011-06-25
Brought
[LIST]
[*] [FONT="Fixedsys"]/etc/apache2/apache2.conf[/FONT]
[*] [FONT="Fixedsys"]/etc/apache2/mods-available/userdir.conf[/FONT]
[/LIST]
back to default. 
Then made **/etc/apache2/httpd.conf**
```
<Directory /home/*/public_html/cgi-bin>
Options ExecCGI
SetHandler cgi-script
</Directory>
```
(see [How2 User Dirs]("http://httpd.apache.org/docs/2.2/howto/cgi.html")).

Now if my JavaScript calls [FONT="Courier New"]post()[/FONT] using "**cgi-bin/foo.cgi**"
I do not get the *404 Not found* error,
it seems that the script is *not* executed.

Note that if I copy the script to [FONT="Fixedsys"]/usr/lib/cgi-bin[/FONT]
(owned by **root** :() 
and call [FONT="Courier New"]post()[/FONT] using "**/cgi-bin/foo.cgi**" (*with* a leading slash) the script is found and successfully executed.
But the whole idea is to avoid root privileges.

---

### Post by yotam on 2011-06-27
Only now I have realized that a separate **<Directory...**/>
stanza for each depth of [FONT="Fixedsys"]cgi-bin[/FONT] will solve this problem. May be there is a cleaner solution,
but currently the following
[FONT="Fixedsys"]/etc/apache2/httpd.conf[/FONT]
works for me.

```
# See: /usr/share/doc/apache2-doc/manual/en/howto/cgi.html

ServerName localhost

<Directory "/home/*/public_html/cgi-bin">
Options ExecCGI
SetHandler cgi-script
</Directory>

<Directory "/home/*/public_html/*/cgi-bin">
Options ExecCGI
SetHandler cgi-script
</Directory>
```

---

### Post by clearwood on 2012-01-29
Hallo there
I have success with [http://localhost](http://localhost)

and I have done as you recommended above but when I try:

[http://localhost/~rub](http://localhost/~rub)

'rub' being my username

it says :
Forbidden

You don't have permission to access /~rub on this server.
Apache/2.2.20 (Ubuntu) Server at localhost Port 80

Maybe you have an idea?

---

