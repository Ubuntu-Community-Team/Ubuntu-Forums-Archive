---
title: "Lamp Trouble - Apache, Php"
date: 2007-05-14
forum: Server Platforms
---

### Post by magpy on 2007-05-14
Hi I am having two problems with LAMP at the moment,  PHP and APACHE.  I cannot read php scripts 

from my server.  My set up is a windows XP laptop, the client, connected to a local ubuntu server 

(which is not online or connected to the internet).  I have uncommented the section in apache2.conf 

thats makes documents with .php .phtml extensions be read/parsed like HTML.  But when I put these 

scripts below in the document root of the virtual host folder located at /var/www/mysite nothing 

happens.  Does anyone know why this may be or what I need to do?  I noticed that the ubuntu server 

.iso file [Dapper Drake 6.0.6 LTS] contained a copy of PHP5 in its library would I need to install 

this.  I would have thought that php would have been installed at install.  These are the scripts 

that I cannot read. 

script one:

<html>
<head>
<title>HTML form</title>
</head>
<body>
<form action="01.php" method="POST" enctype="application/x-httpd-php" accept-charset="ISO10646" 

accept="text/php">
Name: <br>
<input type="text" name="user" />
<br>
Address: <br>
<textarea name="address" rows="5" cols="40"></textarea>
<br>
<input type="submit" value="hit it!" />
</form>
</body>
</html>


script two:

<html>
<head>
<title>input from form 00</title>
</head>
<body>
<?php
print "Welcome <b>$_POST[user]</b><P>\n\n";
print "Your address is:<P>\n\n<b>$_POST[address]</b>";
?>
</body>
</html>

...continued from above, when I try to access them this is the error message that apache gives:

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/var/www/mysite/listing9.4.php' for inclusion 

(include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0


--

The second problem I have is with the apache server itself, I cannot access the virtual host via its 

name independently from the server root.  The only way I can view the site is by accessing the site 

via the server root directory listing like so: [http://myserver/mysite](http://myserver/mysite).  I have tried two methods for defining 

the site so far none of which have worked.  One with a static [1]  'address based' virtual host the other 

with a  [2] 'name based' virtual host.

 [1]  In the first instance I added a new ip address which I defined in /etc/network/interfaces:


#This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
face lo inet loopback


# The primary network interface
auto eth0

iface eth0 inet static
         address 169.254.164.150
         netmask 255.255.255.0
         network 169.254.164.0
         broadcast 169.254.164.255
         gateway 169.254.164.1
         # dns-* options are implemented by the resolvconf package, if installed	         
        dns-nameservers 169.254.164.1 169.254.164.2 169.254.164.3

auto eth0:1

iface eth0:1 inet static
         address 179.254.164.160 
         netmask 255.255.255.0
         network 179.254.164.0
         broadcast 179.254.164.255
         gateway 179.254.164.1


I also updated the /etc/hosts file to link the new ip address to a hostname in the folowing format:

179.254.164.160 mysite

I also made sure to include the ip address in the 1st apache VirtualHost container

<VirtualHost 169.254.164.160>   
        ServerAdmin webmaster@localhost
        ServerName mysite.com
         DocumentRoot /var/www/mysite
</VirtualHost>



[2] in the second instance concerning the 'name based' virtual I outlined it with the name virtual 

host directive:

NameVirtualHost 179.254.164.2

<VirtualHost 169.254.164.2>   
        ServerAdmin webmaster@localhost
        ServerName mysite.com
        ServerAlias mysite [www.mysite.com](www.mysite.com)        
 DocumentRoot /var/www/mysite
</VirtualHost>

     
I updated the name in /etc/resolv.conf where I have three virtual hosts:


search com

nameserver 179.254.164.1
mysite 179.254.164.2 
name server 179.254.164.3

I am at a loss,  in both instances [1] and [2] I pointed to the correct ip address in the 'VirtualHost' xml 

containers and named the right "DocumentRoot" where needed, also in both cases I enabled the site 

using "a2ensite mysite" I also "restarted" and "reloaded" apache.  I tried both [1] and [2]

independently of each other.  When I tried the 'name based' resolution I removed the details 

which were associated with the 'address based' resolution, vice versa.  Also I cannot access either [1] or [2] 

by just typing in the ip address itself either.

----

Whilst typing this thread, I found out that I would have to define a listen directive if either [1] or [2] was to  

work.  Where if you use a static 'address' based virtual host you would also have to include the port number 

in the VirtualHost xml container but if you use a 'name' based virtual host you would only have to include the 

'Listen' directive in the  Host header:


below 'address' based virtual hostheader:

NameVirtualHost 169.254.164.160
Listen 169.254.164.160:80

<VirtualHost 169.254.164.160:80>
</VirtualHost>

--

below 'name' based virtual hostheader:

NameVirtualHost 169.254.164.2
Listen 169.254.164.2:80 

<VirtualHost 169.254.164.2:80>
</VirtualHost>


I applied these in both instances [1] and [2] after which I received the error message:


(99)Cannot assign requested address: make_sock: could not bind to address 169.254.164.2:80 
no listening sockets available, shutting down 
Unable to open logs

To try and remedy this I looked in apache2.conf and could not finid a 'Listen' direrctive.  So I added:

Listen 80

...beneath 'MaxRequestsPerChild 4000' in the 'prefork.c' <IfModule> </IfModule> after which I received 

the same error message, I then tried becoming root in case the problem was related to user permissions.  I 

used the command sudo -i, executed the command re-loaded/started apache2, the same error message 

once again, I also redefined port 80 to 8080, still the same error message.

---

### Post by magpy on 2007-05-14
NB:  I noticed inconsistencies in the ip addresses given in examples [1] and [2] of the previous post I have 

updated them in this one also the hyper links to the other site should not be there, it was auto-generated.


Hi I have two problems with LAMP at the moment,  PHP and APACHE. My client cannot read php scripts 

located on my server.  My set up is a windows XP laptop, the client, connected to a local ubuntu server 

(which is not online or connected to the internet).  I have uncommented the section in apache2.conf 

that makes documents with .php .phtml extensions be read/parsed like HTML.  But when I put these 

scripts (below) in the document root of the virtual host folder located at /var/www/mysite and try to 

read/view them from my client I get an error message (listed below).  Does anyone know why this may be or 

what I need to do?  I noticed that the ubuntu server .iso file [Dapper Drake 6.0.6 LTS] contains a copy of 

PHP5 in its library would I need to install this in order to read/view .php scripts?  I would have thought that 

php would have been installed when I installed the LAMP server.  These are the scripts my laptop cannot 

view/read...

script one:

<html>
<head>
<title>HTML form</title>
</head>
<body>
<form action="01.php" method="POST" enctype="application/x-httpd-php" accept-charset="ISO10646" 

accept="text/php">
Name: <br>
<input type="text" name="user" />
<br>
Address: <br>
<textarea name="address" rows="5" cols="40"></textarea>
<br>
<input type="submit" value="hit it!" />
</form>
</body>
</html>


script two:

<html>
<head>
<title>input from form 00</title>
</head>
<body>
<?php
print "Welcome <b>$_POST[user]</b><P>\n\n";
print "Your address is:<P>\n\n<b>$_POST[address]</b>";
?>
</body>
</html>

...continued from above, when I try to access them this is the error message that apache gives:

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/var/www/mysite/00.php' for inclusion 

(include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

--

The second problem I have is with the apache server itself, I cannot access virtual hosts/sites via 

their names independently from the server root.  The only way I can view the site from my client is by 

accessing each site via the server's root directory listing like so: [http://myserver/mysite](http://myserver/mysite) from the client's 

broswer url.  I have tried two methods for defining sites/virtual hosts so far none of which have worked.  

One with a static [1]  'address based' virtual host the other with a  [2] 'name based' virtual host.   [1]  In the 

first instance I added a new static ip address which I defined in /etc/network/interfaces:


#This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
face lo inet loopback


# The primary network interface
auto eth0

iface eth0 inet static
         address 169.254.164.150
         netmask 255.255.255.0
         network 169.254.164.0
         broadcast 169.254.164.255
         gateway 169.254.164.1
         # dns-* options are implemented by the resolvconf package, if installed	         
        dns-nameservers 169.254.164.1 169.254.164.2 169.254.164.3

auto eth0:1

iface eth0:1 inet static
         address 179.254.164.160 
         netmask 255.255.255.0
         network 179.254.164.0
         broadcast 179.254.164.255
         gateway 179.254.164.1


I updated the /etc/hosts file to link the newly defined ip address to a hostname:

179.254.164.160 mysite

I made sure to include the ip address in the apache VirtualHost container:

NameVirtualHost 179.254.164.160

<VirtualHost 179.254.164.160>   
        ServerAdmin webmaster@localhost
        ServerName mysite.com
         DocumentRoot /var/www/mysite
</VirtualHost>



[2] in the second instance concerning the 'name based' virtual host I outlined it with the name virtual 

host directive and gave it an ServerAlias:

NameVirtualHost 169.254.164.2

<VirtualHost 169.254.164.2>   
        ServerAdmin webmaster@localhost
        ServerName mysite.com
        ServerAlias mysite [www.mysite.com](www.mysite.com)       
 DocumentRoot /var/www/mysite
</VirtualHost>

     
I updated the nameserver in /etc/resolv.conf where I have three virtual hosts:


search com

nameserver 169.254.164.1
mysite 169.254.164.2 
name server 169.254.164.3

I am at a loss,  in both instances [1] and [2] I pointed to the correct ip address in the <VirtualHost> 

containers and named the right "DocumentRoot" for the directory where needed, also in both cases I 

enabled the site using "a2ensite mysite", I "restarted" and "reloaded" apache and I tried both [1] and [2]

independently of each other.  When I tried 'address based' virtual host I removed the details 

which were associated with the 'name based' virtual host, vice versa.  Also I cannot access either 

[1] or [2] by typing in their defined ip addresses.

----

Whilst typing up this thread, I found out that I would have to define a 'Listen' directive if either [1] 

or [2] was to work.  Where if you use the 'Listen' directive with  an 'address' based virtual host you  

also have to include the port number in the <VirtualHost> container but if you use a 'name' based virtual 

host you would only have to include the 'Listen' directive in the  hostheader because the one address applies 

to more than one virtual host:


below 'address' based virtual hostheader:

NameVirtualHost 179.254.164.160
Listen 179.254.164.160:80

<VirtualHost 179.254.164.160:80>
</VirtualHost>


below 'name' based virtual hostheader:

NameVirtualHost 169.254.164.2
Listen 169.254.164.2:80 

<VirtualHost 169.254.164.2>
</VirtualHost>

--

I applied the appropriate hostheader to each instance once again independently of each other.  After which 

I received the error message:

(99)Cannot assign requested address: make_sock: could not bind to address 169.254.164.2:80 
no listening sockets available, shutting down 
Unable to open logs

To try and remedy this I looked in apache2.conf and could not find a 'Listen' directive.  So I added 'Listen 80'

beneath 'MaxRequestsPerChild 4000' in the 'prefork.c' <IfModule> </IfModule>:

<IfModule prefork.c> 
StartServers                 5
MinSpareServers          5
MaxSpareServers       10
MaxClients                  20
MaxRequestsPerChild   0
Listen 80
</IfModule>

after which I 

received the same error message, I tried becoming root in case the problem was related to user 

permissions.  I used the command sudo -i, executed the command re-loaded/started apache2, the same 

error message once again, I also changed port 80 to 8080, still the same error message.

---

