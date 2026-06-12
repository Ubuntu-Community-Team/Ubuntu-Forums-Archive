---
title: "Setting up a Subdomain. Nothing is working."
date: 2009-07-18
forum: Server Platforms
---

### Post by strujillo.jr on 2009-07-18
Hello Everyone:
 So I have been attempting (For about the last week) to set up a subdomain. My website is going to be a domain hack so I NEED to set up this sub-domain in order for everything to work. Anyways, here is what I did. I followed this tutorial >>> [This]("http://thinkingnectar.com/2008/getting-ubuntu-to-work-creating-subdomain-in-localhost/") and [This]("https://help.ubuntu.com/community/LocalhostSubdomain") and none of it worked. Nothing I am doing is working. Here is what I did

So I did the sudo command

```
 sudo nano /etc/hosts
```

Then i added 127.0.0.1      sch.localhost (like the tutorials said. SCH is my sub domain)

```

127.0.0.1       localhost
127.0.1.1       sonny-server.hsd1.nm.comcast.net.       sonny-server
127.0.0.1       sch.localhost

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


```

Then I did 

```
sudo nano /etc/apache2/sites-available/sch
```
 
and typed this into the new file

```

<VirtualHost *>
        DocumentRoot /home/sonny/sch/
        ServerName sch.localhost

        <Directory /home/sonny/sch/>
                Options Indexes FollowSymLinks MultiViews +Includes
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

```

then I typed
 ```
sudo a2ensite sch
```

and it said this 

```
Enabling site sch.
Run '/etc/init.d/apache2 reload' to activate new configuration!
```

and when I run ```
etc/init.d/apache2 reload
```
it says ```
-bash: etc/init.d/apache2: No such file or directory
```
So I ran ```
sudo etc/init.d/apache2 reload
```
and it said ```
sudo: etc/init.d/apache2: command not found

```

So I dont know how I figured it out but I ended up typing ```
sudo /etc/init.d/apache2 restart
``` and it restarted, but this was the output
```
* Restarting web server apache2
Warning: DocumentRoot [/home/sonny/sch/] does not exist
Warning: DocumentRoot [/home/sonny/sch/] does not exist
[Sat Jul 18 00:20:54 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting Warning: DocumentRoot [/home/sonny/sch/] does not exist
Warning: DocumentRoot [/home/sonny/sch/] does not exist
[Sat Jul 18 00:20:55 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
   ...done.

```

So yeah. I hope this helps. When I was done (I am accessing my server via ssh from my mac) I typed in Safari my ip (192.168.1.102) and then I typed in sch.192.168.1.102 and the usual error popped up saying ```
Safari can’t find the server.
Safari can’t open the page “http://sch.192.168.1.102/” because Safari can’t find the server “sch.192.168.1.102”.
```

So basically, I am doing something wrong. Do you know what it is, could you spot an error in my code? Please Please Please Please help me. I really want this to work that way I can ditch GoDaddy for good lol. 
:)

---

### Post by strujillo.jr on 2009-07-18
WOW, OMG I dont know what happened but it works!!!! OMG im so HAPPY! Anyone interested can go to sch.olar.ly lol. THANK YOU ALL IF YOU EVEN READ THIS :-)

---

