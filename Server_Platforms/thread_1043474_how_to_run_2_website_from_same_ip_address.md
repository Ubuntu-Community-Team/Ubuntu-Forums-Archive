---
title: "how to run 2 website from same ip address"
date: 2009-01-18
forum: Server Platforms
---

### Post by Fertech on 2009-01-18
i have 2 computers with ubuntu, and well when i started  both computer apache can't not find one of my website. i get this error.

root@fertech-desktop:~# sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                                                               apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 6239) already running

how to i fix this error, i want to make two different website. i also want to know if i keep the same data on both how can i set up my server, as when one website goes down the other one take over, i heart servers have like a heart beat and when one goes down the other server takes over

---

### Post by q.dinar on 2009-01-18
sudo /etc/init.d/apache2 restart
or
sudo /etc/init.d/apache2 reload

---

### Post by Fertech on 2009-01-18
i know how to do that, but i have one on 127.0.0.1 and the other on 127.0.1.1 i can't view the 127.0.1.1 thats just to start apache.

---

### Post by mr.generic.user on 2009-01-19
haven't done that before, but...

do you have the 127.0.1.1 set up on on a separate VirtualHost under /etc/apache2/sites-enabled/000-default?

```
<VirtualHost 127.0.0.1:80>
	...
</VirtualHost>
<VirtualHost 127.0.1.1:80>
	...
</VirtualHost>
```

if you had separate domain names i think you would actually use the domain name under those.

if you need to access this from a second computer on the same network:
maybe install a second nic, and have apache use the second nic for the second site????

```
<VirtualHost 192.168.1.2:80>
	...
</VirtualHost>
<VirtualHost 192.168.1.3:80>
	...
</VirtualHost>
```

then you couldn't access the site by localhost, but i think you could with the actual lan ips.

i don't know if you could acutally have apache listen on multiple ports.

like i said, i haven't done multiple 'sites' before so you may already know this...

in ref to above posts, i have never had a service restart work correctly.  i usually use stop then apache2 start...

---

### Post by bodhi.zazen on 2009-01-19
See this wiki page :

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

It reviews apache and how to configure virtual hosts.

Usually you would do this with host name , although you can specify an ip if you prefer.

---

### Post by Fertech on 2009-01-19
I have 2 machines running Linux Ubuntu Servers. I have 2 of everything. 2 apache, 2 domain, 2 nic card one wireless router, but i have both towers wired. both nic card support Linux. but yea i will look into that see what happens, after i get some result i will let you know.

---

### Post by cteneyck on 2009-01-19
i would install bind and set that up to point to your servers. then just go on over to your domain registrar and point it to your bind server.

check out howtoforge it can help you out with setting up bind and apache


[http://www.howtoforge.com/perfect-server-ubuntu-8.10](http://www.howtoforge.com/perfect-server-ubuntu-8.10)

---

### Post by Fertech on 2009-01-20
i can't seem to change any data in /etc/apache2/sites-enabled/000-default?
i did try the chmod 777 but that don't work.

---

### Post by cteneyck on 2009-01-20
try 

sudo chown -R "yourusername" /etc/apache2/sites-enabled/000-default

then sudo chmod -R 777 /etc/apache2/sites-enabled/000-default

also did you get your servers setup so that you can see them from the internet?

---

### Post by Fertech on 2009-01-21
i try the wiki page, but i got this.

```
fertech@fertech-desktop:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                                             Warning: DocumentRoot [/home/fertech/Desktop/fer.html/] does not exist
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
Warning: DocumentRoot [/home/fertech/Desktop/fer.html/] does not exist
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

```

---

### Post by Fertech on 2009-01-21
ok see when i enable the site the work, i disable the default and enable the mysite at this time i'm trying to add 2 website too one server machine, cause using 2 server machine right now may just get more confuse. this is over my head. can someone give me detail on whats going on. at this point the only thing is a know is that when i restart apache i delete or add i site to enable-site. like default site disable and mysite enable.

```
fertech@fertech-desktop:~$ sudo a2dissite default && sudo a2ensite mysite
Site default already disabled
Site mysite already enabled

```

now when i restart the apache2 see what happens

```
fertech@fertech-desktop:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                Warning: DocumentRoot [/var/www/fer.html/] does not exist
[Wed Jan 21 03:22:37 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting Warning: DocumentRoot [/var/www/fer.html/] does not exist
[Wed Jan 21 03:22:38 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                         [ OK ]
fertech@fertech-desktop:~$ 
```

the only thing i change is this, every else is the same
```

DocumentRoot /var/www/fer.html/
<Directory /var/www/fer.html/>

```

---

### Post by bodhi.zazen on 2009-01-21
> **Fertech said:**
> i can't seem to change any data in /etc/apache2/sites-enabled/000-default?
i did try the chmod 777 but that don't work.

> **cteneyck said:**
> try 

sudo chown -R "yourusername" /etc/apache2/sites-enabled/000-default

then sudo chmod -R 777 /etc/apache2/sites-enabled/000-default

also did you get your servers setup so that you can see them from the internet?

Why did you do that ????

chmod -R 777 

will give world read/write permissions and is a very BAD IDEA !!!

First, please take the time to do a little reading on how to run apache and things such as permissions in Linux and how sudo works.

I do not mean to be rude, but you are going to have issues if you take such short cuts as changing permissions on system files to circumvent learning how your system works.

If you chmod -R 777 the wrong file / directory Ubuntu will break and/or you will open significant security holes in your server.

Now, if you have questions or do not understand parts of what you are reading, please ask and we will clarify.

From [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

> Troubleshooting Apache If you get this error: 

*apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for [ServerName]("https://help.ubuntu.com/community/ServerName")* 

then use a text editor such as "sudo nano" at the command line or "gksudo gedit" on the desktop to create a new file, 

sudo nano /etc/apache2/conf.d/fqdnor 
gksu "gedit /etc/apache2/conf.d/fqdn"then add 
ServerName localhostto the file and save.  This can all be done in a single command with the following: 

echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn

There is also an entire section on virtual hosts 

[https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts](https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts)

In addition I suggest you read through :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Fertech on 2009-01-21
yea i know that i gave the world read/write permissions but i was just testing it, i change it back to view only. i know when i can't seem to change the data in a file is cause of the permission. your right i can't rush this, i need to take my time and understand how apache work, cause i'm so confuse. i will read the links. about the bind9 i have no clue what that is i need to look into that. reply to the other person. i try to reply back to the reply.

---

### Post by bodhi.zazen on 2009-01-21
glad to hear it.

What you are wanting to do is run what is called virtual hosts.

It is very easy to do, but takes some time reading.

Basic steps :

1. Know what your public IP address (the one given to you from your internet provider).

2. Know our private IP address the one given to you by your router. If it is a server, set a static IP address. If you do not have a router either learn how to configure iptables or buy a router :).

3. If it a  public server, Buy a domain. You can get one for free at say DynDNS (or elsewhere) or but one for cheap. Then set up the domain and forward DNS to your public IP. Then forward port 80 to your private IP address.

4. Configure Apache to run Virtual Hosts. The link I gave you will walk you through it.

It takes about an hour to read how to configure Apache. The reason I gave you a link is I would be typing very similar information here otherwise and it would be a long post :twisted:

If as you are reading you do not understand what you are doing or get stuck, ask here and we will help. Be sure to include specific information on where you are having issues.

I run a public server, all on one machine, that uses virtual hosting, both by name and ip, with no problem other then reading and configuring the apache config files so I am sure you can do the same. It is just a matter of reading a few links and asking a few questions if you get stuck.

---

### Post by pitje on 2009-01-21
Although it doesn't help to learn apache and virtual hosts (as it takes you 'away' from the actual stuff), I find [rapache](http://www.rapache.org/) a very useful program to setup and configure virtual hosts :)

---

### Post by Fertech on 2009-01-21
ok i  read all that, before. i try all this

```
sudo nano /etc/apache2/conf.d/fqdn
gksu "gedit /etc/apache2/conf.d/fqdn"
then add

ServerName localhost

to the file and save. This can all be done in a single command with the following:

echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn
```

only problem is i see 2 images of everything cause im using the default html codes. i think i should just see one image. i have a google script and it's on there twice. i did disable the default site. i don't get what's going on.

---

### Post by Fertech on 2009-01-21
I'm try to do a name-based virtual hosts, do not confuse with address-base virtual hosts. the name-based hosts i can run more than one host on the same ip address, i'm just having a hard time. i know i need to add the names to my DNS as CNAMES of the machine , but i don't know how to do that. anyone has any information please reply back.

```
; zone file fragment for example.com
joe        IN      A      192.168.254.3   
www        IN      CNAME  joe ;canonical name is joe.example.com.
www        IN      CNAME  joe.example.com. ; exactly the same as above
ftp        IN      CNAME  www.example.com. ; bad practice
; better practice to achieve same result as ftp CNAME above
; by re-defining the same physical host with 2 A records
ftp        IN      A      192.168.254.3

; next line redirects bill.example.com to fred.another.com
bill       IN      CNAME  fred.another.com.

; this is theoretically invalid - but widely implemented
           IN      MX 10 mail.example.com.
...
mail       IN      CNAME  joe.example.com.

; classic www.example.com and example.com access
; resolves example.com to an IP
           IN      A      192.168.254.8
www        IN      CNAME  example.com.
; could also be defined as 
           IN      A      192.168.254.8
www        IN      A      192.168.254.8
```

---

### Post by Fertech on 2009-01-21
when i try this code i get in localhost, and 127.0.0.1 and fertech.ath.cx same error 404 page not found.

```

sudo a2dissite default && sudo a2ensite mysite
sudo /etc/init.d/apache2 restart

fertech@fertech-desktop:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                Warning: DocumentRoot [/var/www/fer.html/] does not exist
[Wed Jan 21 18:46:01 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting Warning: DocumentRoot [/var/www/fer.html/] does not exist
[Wed Jan 21 18:46:03 2009] [warn] NameVirtualHost *:80 has no VirtualHosts


```

---

### Post by dmizer on 2009-01-21
> **Fertech said:**
> i can't seem to change any data in /etc/apache2/sites-enabled/000-default?
i did try the chmod 777 but that don't work.
Always edit in /etc/apache2/sites-available. Everything in /etc/apache2/sites-enabled is just a symbolic link (no actual files) from /etc/apache2/sites-available.

Make new sites in sites-available, then run:
```
sudo a2ensite sitename
```
Then, restart apache2:
```
sudo /etc/init.d/apache2 restart
```
And your site should become available.

To disable the site, run:
```
sudo a2dissite sitename
```

To modify existing scripts, always edit in /etc/apache2/sites-available, and then restart apache2 after changes were made.

---

### Post by Fertech on 2009-01-22
as you can see here i did that, take a look at what i did here
and this is the error i get NameVirtualHost *:80 has no VirtualHosts

```
sudo a2dissite default && sudo a2ensite mysite
sudo /etc/init.d/apache2 restart

fertech@fertech-desktop:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                Warning: DocumentRoot [/var/www/fer.html/] does not exist
[Wed Jan 21 18:46:01 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting Warning: DocumentRoot [/var/www/fer.html/] does not exist
[Wed Jan 21 18:46:03 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
```

ok i fix the namevirtualhost *:80 has no virtualhosts check out the new error 
```


fertech@fertech-desktop:~$ sudo /etc/init.d/apache2 restart * Restarting web server apache2                                                Warning: DocumentRoot [/var/www/fer.html/] does not exist
 ... waiting .Warning: DocumentRoot [/var/www/fer.html/] does not exist
                                                                         [ OK ]
fertech@fertech-desktop:~$ 

```

---

### Post by dmizer on 2009-01-22
Please post the contents of /etc/apache2/sites-available/mysite

---

### Post by 0x29a on 2009-01-22
I don't mean to muddy the water, but I have one server running two name-based websites. It's late here, so understand that I'm writing this while tired. I've done my best to be thorough, but it's possible I've missed something. Sorry in advance if I did.

I was getting:
```

[Wed Jan 21 03:22:37 2009] [warn] NameVirtualHost *:80 has no VirtualHosts

```
several times. I had to create two different db files on my DNS server so apache could do a look-up of the names and know that it was hosting the sites. Using 127.0.0.1 the way you are, these sites will only be available on your local machine, and I think you realize that. You can basically make up any domain name you want as long as bind9 is not handling queries from beyond your local machine. You do have bind running, correct?

I'll post the db files for each virtual host below, but here are my site files in /etc/apache2/sites-available for both name-based sites first. Note the first line specifically. There is ***no*** NameVirtualHost directive in the second file and only an asterisk (*) defined in the first. Removing it got rid of the error you're getting for me, and everything started working. Also, I avoided using the name *default* for one of the site files because it was confusing (much like this post, I 'magine.):
Filename site1.net :
```

NameVirtualHost *
<VirtualHost *>
        ServerName www.site1.net
        ServerAlias www.site1.net
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/net/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/net/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ## By adding this directory to this site file the directory
        ## is only available from this virtual host and not both.
        ## I can't recall how I set up the user, atm. It's late...
        <Directory /var/www/net/dls>
                Authtype Basic
                Authname "By Invitation Only"
                AuthUserFile /etc/apache2/.restrict
                Require user myuser
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log
      LogLevel debug

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

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

Filename site2.org :
```

<VirtualHost *>
ServerName www.site2.org
ServerAlias www.site2.org
DocumentRoot /var/www/org/
DirectoryIndex index.php index.html
<Directory /var/www/org/>
AllowOverride all
Options Indexes FollowSymLinks Multiviews
Order allow,deny
Allow from all
</Directory>
CustomLog /var/log/apache2/site2.org.access.log combined
LogLevel debug
</VirtualHost>

```
You've learned about a2ensite. Run that after doing the stuff below.

Now, for DNS I created two zone files for each virtual host. Keep in mind that wherever it says "hostname" in the files below, it's going to be "fertech-desktop" (no quotes) in all your db files. Don't know how the hyphen in your hostname will affect things. Never tried a hyphenated hostname with DNS, but I don't think it will break things. The files I'm listing here are my production files modified to resemble your situation as I interpreted from your posts, so let me know if something doesn't make sense. Here's the db.site1.net file:
```

$TTL 3h
site1.net. IN SOA hostname.site1.net. admin.site1.net. (
                2008122801      ;serial
                        3h      ;refresh after 3 hours
                        1h      ;retry after 1 hour
                        1w      ;expire after 1 week
                        1h)     ;negative caching TTL of 1 hour
;
;name server
;
site1.net. IN NS hostname.site1.net.

;

;addresses of canonical names
;
hostname.site1.net.    IN A 127.0.0.1
site1.net.           IN A 127.0.0.1
;
;aliases
;
www.site1.net.       IN CNAME hostname.site1.net.
; I also run an ftp server on this machine so I define it, too.
ftp.site1.net.       IN CNAME hostname.site1.net.

```
The periods at the end of each FQDN is required. Don't forget the periods. Now, here's the db.site2.org file:
```

$TTL 3h
site2.org. IN SOA hostname.site1.net. admin.site1.net. (
                2008123004      ;serial - last time I made tweaks
                        3h      ;refresh after 3 hours
                        1h      ;retry after 1 hour
                        1w      ;expire after 1 week
                        1h)     ;negative caching TTL of 1 hour
;
;name server
;
site2.org. IN NS hostname.site2.org.
;
;addresses of canonical names
;
hostname.site2.org.    IN A 127.0.0.1
;
;aliases
;
www.site2.org.       IN CNAME hostname.site2.org.

```
Yes, I know that the SOA record just after the $TTL 3h at the top of both files is the same. After I set these up, I had to fix my db.127.0.0 file like this:
```

$TTL 3h
0.0.127.in-addr.arpa. IN SOA localhost.site1.net. admin.site1.net. (
                2008123101      ;serial - last time i tweaked this file
                        3h      ;refresh after 3 hours
                        1h      ;retry after 1 hour
                        1w      ;expire after 1 week
                        1h )    ;negative caching TTL of 1 hour
;
;name server
;
0.0.127.in-addr.arpa. IN NS localhost.site1.net.
0.0.127.in-addr.arpa. IN NS localhost.site2.org.
;
;addresses that point to canonical names
;
1.0.0.127.in-addr.arpa. IN PTR localhost.site1.net.

```

I had to add the zones to named.conf. Again, I'm assuming you have DNS working correctly. ;)
```

zone "site1.net" in {
        type master;
        notify yes;
        file "db.site1.net";
        allow-query { any; };
};

zone "site2.org" in {
        type master;
        notify yes;
        file "db.site2.org";
        allow-query { any; };
};

```

Now restart bind and check syslog and named.log to be sure that it restarted with no errors. Specifically, look for lines that say "ignoring out of zone" something. That would be bad and we'd have to debug that. If it restarted without errors, then sweet!

Now run a2ensite for each site. Then restart apache and look for error from it, too. If it restarts without any errors, then double-sweet!

Let me know if this helps. If you need help with DNS, I can probably figure out how to make that less cryptic.

Good luck!

---

