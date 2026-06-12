---
title: "How to acces a VPS from an virtual domain"
date: 2021-03-21
forum: Server Platforms
---

### Post by raduenea on 2021-03-21
[COLOR=#242729][FONT=Arial]I have a vmware installed on my desktop with an Ubuntu 18 with LAMP installed. Can be acces only from my internal network (desktop and other machines) without any problem. 
What I want is to access the server (from the desktop where vmware is installed) not only from an ip but also from an virtual domain like lsapp.dev. 
So I duplicate "[/FONT][/COLOR]**000-default.conf**[COLOR=#242729][FONT=Arial]" and rename to "[/FONT][/COLOR]**lsapp.dev.conf**[COLOR=#242729][FONT=Arial]". Inside of [/FONT][/COLOR]**lsapp.dev.conf**[COLOR=#242729][FONT=Arial] I have:

[/FONT][/COLOR]```
 <VirtualHost *:80>
    ServerName lsapp.dev
    DocumentRoot /var/www/html/lsapp/public
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/html/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride all
                Order deny,allow
                allow from all
        </Directory>
</VirtualHost>
```[COLOR=#242729][FONT=Arial]

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]Also, on windows I add on hosts file the line:
[/FONT][/COLOR]```
192.168.40.128 lsapp.dev
```[COLOR=#242729][FONT=Arial]

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]192.168.40.128 is the ip of Ubuntu from vmware.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]After all this I try to acces the VPS from browser with lsapp.dev but I have the message "This site can’t be reached".[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]It's something that I missed ?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thanks[/FONT][/COLOR]

---

### Post by darkod on 2021-03-21
1). Did you copy the .conf file in the sites-available folder?

2). Did you enable the new site?
```
sudo a2ensite lsapp.dev
```
And restart apache service after that.

---

### Post by raduenea on 2021-03-21
1. Yes, the file it's in /etc/apache2/sites-available/lsapp.dev.conf
2. I enable the new site and restart apache but the same message.

I also edit the "**000-default.conf**" file with:

 ```
<VirtualHost *:80>
    ServerName localhost
    DocumentRoot /var/www/html/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/html/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride all
                Order deny,allow
                allow from all
        </Directory>
</VirtualHost>
```

And in windows hosts file I add :
```
192.168.40.128 localhost
192.168.40.128 lsapp.dev
```
After that when I access localhost from the browser message it's the same "This site can’t be reached".

Do you think this it's possible only if i run XAMPP as a local server and not LAMP on a virtual machine vmWare ?

---

### Post by TheFu on 2021-03-21
VMWare makes 6 virtualization products.  Which are you using?  The skills to run each are different.

The process to determine the root cause of this problem is to trace the packets from computer A to computer B. At each step, there are log files, especially on the server.
Verify the web server is actually running.
Verify the client can ping the server by IP and by name.
Verify a firewall isn't preventing connections.
Verify that the access and error logs for the enabled website are seeing "some" traffic.

On all Unix systems, log files are in /var/log/ somewhere.  Apache usually created a subdirectory. 000-default.conf should specify where logs go.
```

        LogLevel warn
        CustomLog /var/log/apache2/access.log combined
        ErrorLog /var/log/apache2/error.log
```

Lastly, .dev is an approved TLD, so it is not ok to use that without a formal, public, registration.  .local or .lan are typically used on private subnets like 192.168/16.

```
$ ping lsapp.dev
PING lsapp.dev (103.224.182.210) 56(84) bytes of data.
64 bytes from lb-182-210.above.com (103.224.182.210): icmp_seq=1 ttl=45 time=61.4 ms
```
It could be that your client is trying to connect to THAT server, not yours.  The nsswitch.conf controls the order for name resolution. If avahi is running on both systems, then {hostname}.local can be used - assuming mDNS is allowed in the nsswitch.  I only allow *files dns* to be used, but I don't think that's the default on desktop Ubuntu systems.

---

