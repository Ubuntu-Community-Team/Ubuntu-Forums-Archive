---
title: "Two hostnames in the same webserver (APACHE)"
date: 2007-07-18
forum: Server Platforms
---

### Post by hidden80 on 2007-07-18
I have several websites in the root of my linux server (mantis, dotproject, etc), and I access them from a Windows XP machine typing "http://myserver/mantis", "http://myserver/dotproject", etc.

Also I have a project made with Symfony that I would like to access with a different name, for example "http://mysymfonyproject", but it doesn't work (it says the server was not found).

Here's my apache2.conf configuration:

```

NameVirtualHost *:80

#original apache location
<VirtualHost *:80>
  ServerName myserver
  DocumentRoot "/var/www"
</VirtualHost>

<VirtualHost *:80>
  ServerName mysymfonyproject
  DocumentRoot "/var/www/mysymfonyproject/web"
  DirectoryIndex index.php
  Alias /sf /usr/share/php/data/symfony/web/sf

  <Directory "/usr/share/php/data/symfony/web/sf">
   AllowOverride All
   Allow from All
  </Directory>

  <Directory "/var/www/mysymfonyproject/web">
   AllowOverride All
   Allow from All
  </Directory>
</VirtualHost>

```


But then I type this in my Windows XP machine:

```

http://myserver

```


And it doesn't find the server.


But if I modify the HOSTS file in my Windows XP machine adding this:

```

192.168.0.20 myserver mysymfonyproject

```


Then it works, BUT... both are pointing to the same IP, so the server doesn't know which virtual server it has to serve... therefore the result is always "http://myserver", even if I type "http://mysymfonyproject".

Here's an alternative:

- Delete the added lines in the HOSTS file.
- Open cmd.exe and type "nbtstat -a 192.168.0.10" (the server's IP)

Then, "http://myserver" works perfectly, but "http://mysymfonyproject" is not.

Inside the server all works perfectly, so it seems to be a problem serving inbound petitions from the network.


What am I doing wrong?

---

### Post by Abetorius on 2007-07-18
I'm not apache expert but two toughts that could help:

Alias directory shouldn't be placed between "..."?

Also you coul listen on different ports, for example 80 for first and 8080 for second.

---

### Post by Pinger05 on 2007-07-18
I have had a smilar problem for the last 2 days.  If I come up with something I will post it here.

---

### Post by MJN on 2007-07-18
> **hidden80 said:**
> Then it works, BUT... both are pointing to the same IP, so the server doesn't know which virtual server it has to serve... therefore the result is always "http://myserver", even if I type [http://mysymfonyproject.](http://mysymfonyproject.)
 
Whoa! Hold on there....
 
It matters little that multiple names point to the same IP as when your web client connects to the server it sends a HTTP Host header-request specifying the name you typed in and hence the server is able to serve the correct set of pages up.
 
Hence your use of the hosts files is entirely correct (an alternative would be DNS but that's simply a different means to get to the same end). The issue here is not one of domain to address resolution - the fact you're reaching the server at all is proof positive that all is fine with that.
 
Unless I am not seeing the woods for the trees your Apache config seems fine so I'm unsure what the problem is.
 
You say that 'inside the server works perfectly' - what exactly do you mean by this? Are you saying that local connections to [http://mysever](http://mysever) and [http://mysmyfonyproject](http://mysmyfonyproject) each reach their intended (different) targets? If so, it sounds like an issue at the web client end of your network given the local proof demonstrates the correct Apache config.
 
Mathew

---

### Post by koenn on 2007-07-18
> **MJN said:**
> Whoa! Hold on there....
when your web client connects to the server it sends a HTTP Host header-request specifying the name you typed in and hence the server is able to serve the correct set of pages up.
  The issue here is not one of domain to address resolution 
 .
I agree.
But for the host-header mechanism to work, don't you need to tell apache about what sites it's hosting, and where the documents corresponding to that host/website are located, eg 

```

NameVirtualHost myserver                 #answers to http://myserver/
<VirtualHost myserver>                    
  ServerName myserver
  DocumentRoot "/var/www"
</VirtualHost>

NameVirtualHost mysymfonyproject     #answers to http://mysymfonyproject/
<VirtualHost mysymfonyproject>       
  ServerName mysymfonyproject
  DocumentRoot "/var/www/mysymfonyproject/web"
</VirtualHost>
```

Could be mistaking in principle and in syntax, and I don't have an apache nearby (using lighttpd atm) so I can't chek, but I seem to remember something along those lines. 
If I remember correctly, you can also use separate conf files in a subdirectory of the apache conf  dir, /etc/apache2/sites-available (or something like it), or via symlinks to ...../sites-available

---

### Post by Mr. C. on 2007-07-18
On a hunch, make separate hosts lines:

```
192.168.0.20 myserver
192.168.0.20 mysymfonyproject
```

MrC

---

### Post by gregor171 on 2007-07-19
Unless you specify, where to look for **mysymfonyproject** in your internal** DNS**, your xp box can't tell, what is **[http://mysymfonyproject](http://mysymfonyproject)**, and where to find it. It just might be possible, that it works from within a box?! But for xp is something out of space...

**myserver** is probably your server name, where **mysymfonyproject**  is something virtual.

I suggest you to use **aliases**!!! Outcome would come like this:
```

http://myserver/{your firs page}
http://myserver/mysymfonyproject/{your 2nd page}
```

For testing or developing as well as internal production it should do.
But if you prefer to mess with DNS...

---

### Post by MJN on 2007-07-19
There is no need for DNS as the OP is using local hosts files.
 
We really need to know further info, including the outcomes of the suggestions above. I have a feeling that the OP is misinterpreting the results of what they're seeing.
 
Speaking of which, where is the OP? We're all chatting amongst ourselves here! ;)
 
Mathew

---

