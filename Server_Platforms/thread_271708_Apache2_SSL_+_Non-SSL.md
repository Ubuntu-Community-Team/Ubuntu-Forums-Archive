---
title: "Apache2 SSL + Non-SSL"
date: 2006-10-05
forum: Server Platforms
---

### Post by jreige on 2006-10-05
I have succesfully installed apache2 with ssl.  I can now browse sites I have with SSL.  Has someone configured apache2 to enable both port 80 unsecure and port 443 at the saem time and then you enable virtual servers to the type of binding you want.

Thanks.:)

---

### Post by bobmct on 2006-10-27
If you've got SSL working, that's the hardest part!!!

It's all in the definitions.  BUT - you can have ONLY ONE SSL site working!

First, be sure that you have BOTH the following lines in your conf file:

Listen *:80         # This is for non-secured access
Listen *:443        # This is for secured access

For the site that you want to be THE secured site, start its definition section with this statement:

<VirtualServer *:443>

and include the other necessary ssl directives as well.
ALL SSL (https:) requests should be directed to this virtual site.

Hope this helps.

Bob

---

### Post by jaripetteri on 2006-11-18
I have site up with three http domains and one of those also https. I can use every site but not secure. I can open my https site as [http://mydomain.com:443](http://mydomain.com:443) and also [http://mydomain.com](http://mydomain.com) (as :80). Webabmin uses also ssl and it's up an running fine. So how I can get that secure site also up? what am I missing?

---

### Post by MJN on 2006-11-19
Post your config and we can tell you! :)

Mathew

---

### Post by jaripetteri on 2006-11-19
Here are my virtualhost settings. What else is needed?

```
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/[^.#]*

<VirtualHost *:80>
DocumentRoot /var/www/mydomain.net
ServerName mydomain.net
<Directory "/var/www/mydomain.net">
allow from all
Options +Indexes
</Directory>
Alias /phpmyadmin/ "/usr/src/phpmyadmin/"
</VirtualHost>

<VirtualHost *:80>
DocumentRoot /var/www/my2nddomain.net
ServerName my2nddomain.net
<Directory "/var/www/my2nddomain.net">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

<VirtualHost *:443>
DocumentRoot /var/www/my3rddomain.net
ServerName www.my3rddomain.net
SSLEngine on
SSLCertificateFile /etc/ssl/certs/server.crt
SSLCertificateKeyFile /etc/ssl/private/server.key
<Directory "/var/www/my3rddomain.net">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

<VirtualHost *:80>
DocumentRoot "/var/www/my3rddomain.net"
ServerName www.my3rddomain.net
<Directory "/var/www/my3rddomain.net">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

```

---

### Post by MJN on 2006-11-19
Okay, thanks. What exactly is the problem? (sorry for not spotting it but it's not clear, to me at least!) You've said '*I can use every site but not secure*' but also '*I can open my https site as *[URL="http://mydomain.com:443/"]*http://mydomain.com:443*' :-k
[/URL]

---

### Post by jaripetteri on 2006-11-19
here is the problem:

[http://www.mydomain.net](http://www.mydomain.net) -> fine
[http://www.my2nddomain.net](http://www.my2nddomain.net) -> fine
[http://www.my3rddomain.net](http://www.my3rddomain.net) -> fine
[http://www.my3rddomain.net:443](http://www.my3rddomain.net:443) -> fine, meaning that port 443 is open
[https://www.my3rddomain.net](https://www.my3rddomain.net) -> can't open

so something wrong with ssl. first I get errors about ssl keys but using correct directory for those fix it. I'm using webmin BTW. And can access webmin via [https://www.mydomain.net:10000](https://www.mydomain.net:10000). 

Just ](*,) with this for a while...

---

### Post by MJN on 2006-11-19
That does seem strange, after all [http://www.my3rddomain.net:443/](http://www.my3rddomain.net:443/) = [https://www.my3rddomain.net/](https://www.my3rddomain.net/)

Is there any particular reason you've obfuscated your URLs? It would help enormously if we knew what they were then we can attempt connection from this end and see what's being served up.

Mathew

---

### Post by jaripetteri on 2006-11-19
I try with another pc from my localnet and [http://www.obd.fi:443/]("http://www.obd.fi:443/") is working but [https://www.obd.fi/]("https://www.obd.fi/") gave error:

```
www.obd.fi has sent an incorrect or unexpected message. Error Code: -12263
```

so something weird is going on here... :confused:

---

### Post by MJN on 2006-11-19
Hmm... I can't the same from here.

Do your Apache error log files show anything?

Sorry for the rather slow diagnosis.... I'm scratching my head just as much as you here... but two sets of eyes has got to be better than one!

Mathew

---

### Post by MJN on 2006-11-19
Aha....

Missing the woods for the trees here...

Just noticed that connecting to [http://www.obd.fi:443/](http://www.obd.fi:443/) is not producing any padlock in Firefox hence it's not truly 'working'. In my config (for [https://secure.newtonnet.co.uk/](https://secure.newtonnet.co.uk/)) I have a **SSLCipherSuite** **HIGH:MEDIUM **directive - try putting that in and see what happens... this limits the cipher suites available for client connections - the default is quite wide hence I think it's allowing a method which won't work. Connecting via http on port 443 is allowing the most basic, whereas a true https connection is already starting much higher.

Mathew

---

### Post by tturrisi on 2006-11-19
What does /etc/apache2/ports.conf look like?
Have a look at the end of /var/log/apache2/error.log just after failing to connect using https://

---

### Post by MJN on 2006-11-19
Incidentally, what guide did you use to implement SSL? This'll give us an idea of what keys (and backend configration) you're using.

Mathew

---

### Post by jaripetteri on 2006-11-19
I'm using this quide for ssl:
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html")

and probably mess it up with webmin virtualhost settings.

and about the link I gave to my site... use [http://www.obd.fi:88](http://www.obd.fi:88)... its routed to correct server to port :80 while port:80 is routed to my old server still serving... this anyway can't couse the fault when port:443 is routed directly to new server.

ports.conf:```
Listen 80
Listen 443

```

---

### Post by MJN on 2006-11-19
Which guide?

(you seem to have missed it out)

---

### Post by jaripetteri on 2006-11-19
hups doing to many thinks same time here... :rolleyes: 

link added and BTW that error I got with firefox on windows xp desktop I have.

---

### Post by MJN on 2006-11-19
Where's your** SSLOptions +FakeBasicAuth +ExportCertData +CompatEnvVars +StrictRequire **line (as per the guide)?

I'm not sure it will make any difference however I'm wondering why you left it out?

Mathew

---

### Post by jaripetteri on 2006-11-19
> **MJN said:**
> Where's your** SSLOptions +FakeBasicAuth +ExportCertData +CompatEnvVars +StrictRequire **line (as per the guide)?


that was missing but still no help. I also made new keys which didn't help either but after a many hour search I finally found it... :p 

there were two files under site-enable directory containing lines:

```
NameVirtualHost *:0
```

I fix those with ```
NameVirtualHost *:80
``` and tadaa now its running. Now idea when those have changed to 0 put I don't really care. I can no move on with this new server thing... :mrgreen:

Probably editing those config files partly by hands and partly with webmin couses this. but atleast I learn a lot about apache while doing this.

Anyway thanks for your help!!!

---

### Post by MJN on 2006-11-19
Ah nice one!

Shame it was nothing to do with what we were all concentrating on.... ho hum! :)

Mathew

---

### Post by tturrisi on 2006-11-19
> there were two files under site-enable directory
That would have been my next question.
Those files are symlinks.
Same goes for mods_enabled.

A symlink is required in sites_enable for each virtual host.

apache-1.3 was soooo much simpler!

---

