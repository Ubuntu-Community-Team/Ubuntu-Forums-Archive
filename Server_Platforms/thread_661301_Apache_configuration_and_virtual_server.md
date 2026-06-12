---
title: "Apache configuration and virtual server"
date: 2008-01-07
forum: Server Platforms
---

### Post by ecrissman on 2008-01-07
I have set up a home server running Gutsy and have everything working except I am a bit confused about the proper configuration for an Apache virtual server and I have a few questions that are probably easily answered.  In my research I have not found a straightforward tutorial for setting up apache.  Here is what I have done:
1. Fresh LAMP install on a headless box
2. Set up SSH with RSA keys for remote access
3. I have Webmin running but I am trying to learn so I amprimarily using command line
4. Ports are forwarded on my router to my server's ip. My ISP doesn't block port 80
5. Set up dynamic DNS so that my domain name is now working.
6. Everything is working locally, but if I go outside my network I can not access my site.
6. For apache I have created my site directory, copied the default in sites-available,  enabled it and disabled the default.  Here is my virtual server file
```
NameVirtualHost *
<VirtualHost *:*>
ServerName mysite.com
ServerAdmin webmaster@mysite.com

DocumentRoot /home/eric/www/mysite.com
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/eric/www/mysite.com>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
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
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
ServerAlias *.ecrissman.com

</VirtualHost>


```

My problem is that I have seen conflicting information on what information to include in this file.  Spefically NameVirtualHost* and <VirtualHost *> Should I include port 80 there? Also, is there an IP address I need to include? 

Secondly, do I need to change anything /etc/hosts?
```
127.0.0.1       localhost
127.0.1.1       eschomeserv.domain.actdsltmp    eschomeserv

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Lastly, how do I chmod the directory for my site/home folder so that apache has access to it and is that secure?

Thanks in advance.  I know it is a long post, but I have spent many hours trying to figure this out before posting here.

---

### Post by freymann on 2008-01-08
> **ecrissman said:**
> 
My problem is that I have seen conflicting information on what information to include in this file.  Spefically NameVirtualHost* and <VirtualHost *> Should I include port 80 there? Also, is there an IP address I need to include?

 This had me going in circles for a while too.

 One of the examples i followed said to copy the 'default' file over to a new file if you wanted a second virtual domain, edit it, use it.

 At the top of the /etc/apache2/sites-available/default file was 

NameVirtualHost *
<VirtualHost *>
etc..

 and when I literally copied it to a new filename and made some edits, the duplicate "NameVirtualHost *" command caused some grief. When I removed it from the copy I made, things worked better. It did not need an ip number or :80 appended to it.

My ports.conf file looks like:

Listen *:80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>

Again, no IP but I may have added the :80 to it. Can't remember now.

> Lastly, how do I chmod the directory for my site/home folder so that apache has access to it and is that secure?

 Hmm. The default web root is /var/www and the web server must have read access to it. You need to decide what permissions you need on the folder and subfolders that suit your needs.

 In my case I wanted to be able to edit the files in my web directory structure so I had to 

chown -R myname /var/www

The /var/www folder is 

chmod 755

From there it varies from folder to folder. Any folder where I want the web server to be able to write to a file has to be set up differently.

I usually 

chown www-data foldername

and make sure the foldername is

chmod 755

These are all specific to your needs.

---

### Post by ecrissman on 2008-01-08
Thanks for the input. I am not new to Linux but I am just beginning the server stuff. I finally figured out how to change ownership and set file permissions for the directory doing exactly what you suggested.  It is just the virtual host setup that is stumping me.  I know there are different ways to do it, but the dynamic DNS, nameserver stuff is what is getting me. How do I set it up to only recognize the ServerName and forward it to DNS? And do I have to put something in /etc/hosts besides the local ip?

---

### Post by freymann on 2008-01-08
> **ecrissman said:**
> the dynamic DNS, nameserver stuff is what is getting me. How do I set it up to only recognize the ServerName and forward it to DNS? And do I have to put something in /etc/hosts besides the local ip?

 For Dynamic DNS, go create an account.

 Then set up your virtual domain to match whatever DDNS name you selected.

 Put that name between the <VirtualHost *></VirtualHost> tags using the 'ServerName' tag.

 For instance:

```

<VirtualHost *>

        ServerAdmin webmaster@ddns.org
        ServerName www.ddns.org

        DocumentRoot /var/www
        <Directory />
                Options Indexes FollowSymLinks ExecCGI Includes
                AllowOverride All
        </Directory>
        <Directory /var/www>
                Options Indexes FollowSymLinks MultiViews ExecCGI Includes
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
</VIRTUALHOST>

```

 (this is by no means a complete or valid entry)

 You may want your computer to reflect that domain, so you could always go to System>Administration>Network Settings, go to the HOSTS tab, click ADD, enter the IP address of your machine and the ddns.org domain name you just selected. 

 This isn't absolutely necessary but it makes for a cleaner apache startup.

 So that configures your computer.

 I would just log into dynamic dns and update the IP of your domain manually (it should auto detect your IP when you are at that screen). Then you can test things to make sure your web site is visible from the outside world, barring any restrictions on port 80 by your ISP, firewall rules, etc.

 (If you have a router, you'll need to port-forward 80 to the IP of your computer... if your computer is getting an IP via DHCP you may want to change that to a static IP # instead).

 Assuming you can view your web server on your local LAN, local workstation, and from the outside world, then you can go about installing ddclient:

```

sudo apt-get install ddclient

```

 I prefer to tell ddclient to get the IP# by using a web page, so you either have to figure out how to do that during the install, or just edit the file afterwards and restart ddclient.

 My /etc/ddclient.conf file looks like this:

```

# Configuration file for ddclient generated by debconf
#
# /etc/ddclient.conf

pid=/var/run/ddclient.pid
protocol=dyndns2
#use=if, if=eth0
use=web, web=checkip.dyndns.org/, web-skip='IP Address'
server=members.dyndns.org
login=yourname
password='yourpass'
your.ddns.org

```

I would think you can restart ddclient with:

```

sudo /etc/init.d/ddclient restart

```

Now your IP number changes would be handled automagically.

Is that what you were looking for?

---

### Post by ecrissman on 2008-01-09
I am not giving up. I believe my problem is in my network configuration and not setting up the static ip correctly.  After reading a few posts I realized I needed to change my /etc/network/interfaces file to the following.
[CODEauto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.11.10
netmask 255.255.255.0
network 192.168.11.0
broadcast 192.168.11.255
gateway 192.168.11.1
][/CODE]

I am a bit confused about how to change the resolv.conf file to correctly resolve my dns. What do I put after search? and should I use the nameserver addresses I received from everyDNS.com (for dynamic DNS)?
```
search ???
nameserver 192.168.11.1
nameserver ???

```

Thanks

---

### Post by freymann on 2008-01-09
> **ecrissman said:**
> After reading a few posts I realized I needed to change my /etc/network/interfaces file to the following.
```
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.11.10
netmask 255.255.255.0
network 192.168.11.0
broadcast 192.168.11.255
gateway 192.168.11.1

```


 This looks fine.

> 
I am a bit confused about how to change the resolv.conf file to correctly resolve my dns. What do I put after search? and should I use the nameserver addresses I received from everyDNS.com (for dynamic DNS)?
```
search ???
nameserver 192.168.11.1
nameserver ???

```


 My /etc/resolv.conf file looks like this:

```

nameserver 207.164.234.193
nameserver 67.69.184.139
domain me.homeunix.com

```

 With the domain set for the DynDns domain I have (which obviously isn't what is shown above, that's just an example).

 Are you connecting to your ISP with a router or dialup or pppoe?

 The name servers to use are provided by your ISP.

 If you are using a router, you can enter the IP number of the router as your nameserver as it should forward DNS lookups for you. So that would be just one nameserver entry, which is fine. If that doesn't work log into your router and view your status and on the screen where it shows you are connected it should show you your WAN IP information and the current DNS servers. Write down the DNS server ip's and put them into your resolv.conf file.

 Once you get your DNS going you'll be able to view web sites by name and things should start kicking in a little better for you.

---

### Post by ecrissman on 2008-01-10
Thanks for the all help freymann.  I was finally able to work everything out and I am up and running.  The final problem I had was my modem and router configuration.  So I am now bridging the DSL modem and allowing my wireless router to do the DHCP. It has taken me two weeks to figure everything out, but it has been well worth it.  I have learned so much more about Linux in the process and I am now proudly managing my server through only the terminal and commandline.

---

### Post by freymann on 2008-01-10
> **ecrissman said:**
> Thanks for the all help freymann.  I was finally able to work everything out and I am up and running.

 Way to go! :-)

 I have many years experience at the command line in FreeBSD and using XWindows/Xorg/KDE there too, but I've also enjoyed my switch over to ubuntu (sorta forced there by new equipment that wasn't FreeBSD compatible).

 I enjoy the forums and I try to help out where I can.

---

