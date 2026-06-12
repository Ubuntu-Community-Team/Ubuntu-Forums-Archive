---
title: "Apache2 on Ubuntu problems"
date: 2008-08-26
forum: Server Platforms
---

### Post by Vegan on 2008-08-26
* Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

Here is one of my vhosts.conf files all are the exact same format

<VirtualHost *:80>
  ServerAdmin [email]veganfanatic@hotmail.com[/email]

  DocumentRoot /web/computer-chess
  ServerName computer-chess.dyndns.biz

  ServerAlias [www.computer-chess.dyndns.biz](www.computer-chess.dyndns.biz)

  ErrorLog /var/log/apache2/error.log

  logLevel warn
  CustomLog /var/log/apache2/access.log combined
  ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "/usr/lib/cgi-bin">
  AllowOverride None
  Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
  Order allow,deny
  Allow from all
</Directory>
<Directory /web/computer-chess>
  Options -Indexes
  AllowOverride All
  Order Allow,Deny
  Allow From All
</Directory>
</VirtualHost>

in hppt.conf I have Listen 80 only

what else? I need to do.

The machine is behind a Linksys WRT54G with a fixed address and ports are forwarded, Ubuntu is set for a static adress: 192.168.7.250

Any thoughts. I am converting from Win to Linux.

local host bring up the site no problem

---

### Post by Vegan on 2008-08-26
it working i hope, other comp brought it up

---

### Post by Retaliation on 2008-08-26
I too am trying to set up an apache2 server, but setting it up is proving to be a bit of a challenge. I've searched forums and google and cant seem to find what my problem is. 
   
I'm not sure if I change the Virtualhost from * to an ip address in my /etc/apache2/sites-available or what port I need to forward from my router to. I also would like to know how I set up an ip address that others can access from the web, or if i need to talk to my ISP or get a domain name.

Any info or help that would shed some light on my and the OP's problem would be much appreciated!

---

### Post by Iowan on 2008-08-27
> **Vegan said:**
> it working i hope, other comp brought it up IF it fails with that "Could not reliably determine the server's fully qualified domain name" message, add an entry in your **/etc/hosts** for **127.0.1.1 hostname**.

---

### Post by Vegan on 2008-08-27
It stopped working again. So I dumped the desktop version and installed the server version, upped telnet and now I can connect from my windows box and manage it remotely.

Now I can muck with it and install whatever I need. I set it up as LAMP. Whatever. sudo atp-get install this and that.

Still have not found the location of the 'hosts' name, that you put in the gnome network settings.

Next up, some ftp client other. probably use vsftpd as that is the official favorite. Problem is the defaults are useless, I want one that is not by default open. My goal is to have FTP access tied to user accounts.

---

### Post by cariboo on 2008-08-28
Your hosts file is located in /etc/hosts. You will find that most of your config files are in /etc.

Jim

---

### Post by windependence on 2008-08-28
You guys are going off in the wrong direction. You need to put a ServerName directive in your /etc/apache2.conf like so:

```
ServerName "YourSite.com"
```

Then don't forget to restart Apache.

-Tim

---

### Post by Vegan on 2008-08-28
See my site file:

<VirtualHost 192.168.7.250:80>
  ServerAdmin [email]blablabla@hotmail.com[/email]
  DocumentRoot /web/contract-developer
  ServerName contract-developer.dyndns.biz
  ServerAlias [www.contract-developer.dyndns.biz](www.contract-developer.dyndns.biz)
  ErrorLog /var/log/apache2/error.log
  logLevel warn
  CustomLog /var/log/apache2/access.log combined
  ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "/usr/lib/cgi-bin">
  AllowOverride None
  Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
  Order allow,deny
  Allow from all
</Directory>
<Directory /web/contract-developer>
  Options -Indexes
  AllowOverride All
  Order Allow,Deny
  Allow From All
</Directory>
</VirtualHost>

No Apache errors, all stamped out, and when I connect local on the LAN to the server's IP address I get 403 forbidden, suggesting Apache is listening, but not fully.

I cannot get the site up on my window machine, I have 4 other files like this and think they are OK, I added 

NameVirtualHost 192.168.7.250:80

to my apache2.conf file. Swatted errors, you can only have one of these commands.

---

### Post by windependence on 2008-08-28
Actually the 403 doesn't mean it's not listening, it means you have a permissions problem on the document root. You need to add read and execute access for others to your doc root.

-Tim

---

### Post by Vegan on 2008-08-28
I have the doc root set for rwx at the moment so I can FTP new content to the machine. I am accessing it from a Windows box, using TELNET and FTP as the console is a tad hard to manage from the machine itself.

My hpptd.conf contains all directives, I do not change the apache2.conf file as it is not needed to be changed.

```
#Needed to allow for mass numbers of virtual hosts on one IP address
NameVirtualHost 192.168.7.250:80

#Needed to install a CGI directory in each virtual host
<Directory "/usr/lib/cgi-bin">
  AllowOverride None
  Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
  Order allow,deny
  Allow from all
</Directory>

<Directory /web>
  Options -Indexes
  AllowOverride All
  Order Allow,Deny
  Allow From All
</Directory>

```

The vhost.conf files are very simple. Everything  is set to defaults as much as possible.

```
<VirtualHost 192.168.7.250:80>
  ServerAdmin [email]wwhatever@hotmail.com[/email]
  DocumentRoot /web/contract-developer
  ServerName contract-developer.dyndns.biz
  ServerAlias [www.contract-developer.dyndns.biz](www.contract-developer.dyndns.biz)
  ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
</VirtualHost>

```

Seems pretty generic? Thoughts? URL does not load the page, can access the machine my telnet and ftp no problem by ip address on the local network. Cannot connect with any URL for some reason.

---

### Post by windependence on 2008-08-29
Yes, on your local LAN, your client machine doesn't know what IP address [www.yoursite.com](www.yoursite.com) resolves to. Unless your router supports NAT loopback (uncommon), your router will not send traffic outside your LAN and then have it routed back in again.

So you need a way of telling your client machines just exactly what the IP address is for the machine at [www.yoursite.com](www.yoursite.com). You can do this by setting up an internal DNS server (not fun and not necessary unless you have 100s of PCs) or you can put an entry like this into the hosts file of each client computer that needs to access the server:

```
xxx.xxx.xxx.xxx   [www.yourservername.com](www.yourservername.com)   yourservername
```

Where xxx.xxx.xxx.xxx is the internal(LAN) IP address of your server.

The hosts file is located at /etc/hosts on most Linux and Unix boxes, and at C:\windows\system32\drivers\etc\hosts on most Windows boxes. Edit the file, save it, and you will be able to type [www.yourservername.com](www.yourservername.com) in your browser from a computer inside your network and display the web site. Links will work correctly also.

You will still need to correct your permissions problem first though.

-Tim

---

### Post by Vegan on 2008-09-03
permissions, the cure ALL

sudo chmod -R a=rwx /web (or wherever the content is)

---

### Post by windependence on 2008-09-03
Well, not the BEST option to make it read write and executable for all.

Read and execute for others would probably have done it, but then you would have the problem of your FTP. This is simple Linux security. Windoze has no concept of this.

-Tim

---

### Post by Vegan on 2008-09-10
Turns out I had a problem with Firefox on the LAN, so I am using Internet Explorer for checking the site on the Windows box, as the Linux machine has no GUI i.e. its a 'real' server.

---

### Post by ssavelan on 2008-09-14
> **windependence said:**
> You guys are going off in the wrong direction. You need to put a ServerName directive in your /etc/apache2.conf like so:

```
ServerName "YourSite.com"
```

Then don't forget to restart Apache.

-Tim

* Restarting web server apache2                                                             
Syntax error on line 300 of /etc/apache2/apache2.conf:
ServerName takes one argument, The hostname and port of the server
                                                                                      [fail]

hmm...

---

### Post by Vegan on 2008-09-14
Don't use the quotes

---

