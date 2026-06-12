---
title: "apache2 and virtual ip hosts"
date: 2010-02-21
forum: Server Platforms
---

### Post by confusedstingray on 2010-02-21
Ok i have 2 servers running apache2 only one is seen from the outside world
cant get the 2nd server or any of the virtual hosts to be seen from the outside world
any help on this would be great getting baffled from all the apache conf tutorials 
i think i did it right
Bill:confused:
----
i have a linksys router with dd-wrt install and have port forwarding set 
these are hosted on server 1(bkserver.the-halls.ca ip 192.168.0.104)
http  port 80 protocol both point to ip 192.168.0.205 main site (the-halls.ca)
and 
http port 80 protocol both pointing to 192.168.0.104

these are hosted on second server (mantis.the-halls.ca ip 192.168.0.145)
http port 80 protocol both pointing to ip 192.168.0.208 legodude.the-halls.ca
http port 80 protocol both pointing to ip 192.168.0.212 mantis.the-halls.ca 
http port 80 protocol both pointing to 192.168.0.145

-----
server (1) have website running on ip 192.168.0.104
main server have bind 9 running and seems to be doing what it is to do 
every machine behind router gets all sites by pointing there dns to bind9
also have postfix mail server running mail is coming and going for some time 
no errors that i see
server 1 
copy of network interface:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
#auto lo eth0 eth0:1 eth0:2 eth0:3 eth0:4
auto lo eth0 eth0:1 eth0:2 eth0:3
iface lo inet loopback

# The primary network interface
iface eth0 inet static
    address 192.168.0.104
        netmask 255.255.255.0
        network 192.168.0.0
           broadcast 192.168.0.255
    gateway 192.168.0.2
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 69.49.32.2
    dns-search bkserver.the-halls.ca

iface eth0:1 inet static
        address 192.168.0.205
        netmask 255.255.255.0
        broadcast 192.168.0.255
    network 192.168.0.0

iface eth0:2 inet static
        address 192.168.0.200
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0
        
iface eth0:3 inet static
        address 192.168.0.210
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0
       

#static route for twonkymedia
up route add -net 224.0.0.0 netmask 240.0.0.0 dev eth0

copy of virtual hosts file thehalls.conf
<VirtualHost 192.168.0.205>
ServerAdmin [email]bghall@the-halls.ca[/email]
DocumentRoot /var/www/the-halls
ServerName [www.the-halls.ca](www.the-halls.ca)
ServerAlias the-halls.ca
ErrorLog /var/www/the-halls/logs/error_log
<Directory "/var/www/the-halls">
allow from all
Options +Indexes
</Directory>
<Directory "/var/www/the-halls/cgi-bin">
</Directory>
</VirtualHost>

second host file 
cat watersedge.conf
<VirtualHost 192.168.0.200>
ServerAdmin [email]watersedge@the-halls.ca[/email]
DocumentRoot /var/www/watersedge
ServerName watersedge.the-halls.ca
ServerAlias [www.watersedge.the-halls.ca](www.watersedge.the-halls.ca)
ErrorLog /var/www/watersedge/logs/error_log
TransferLog /var/www/watersedge/logs/access_log
<Directory "/var/www/watersedge">
allow from all
Options +Indexes
</Directory>
</VirtualHost>




server (2) have website running on ip 192.168.0.145
interface file for server 2
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0 eth0:1 eth0:2
iface lo inet loopback

# The primary network interface

iface eth0 inet static
    address 192.168.0.145
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255
    gateway 192.168.0.2



iface eth0:1 inet static
        address 192.168.0.208
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0

iface eth0:2 inet static
        address 192.168.0.212
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0



    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 192.168.0.104
    dns-search bkserver.the-halls.ca

first virtual host file 
cat legodude.conf
<VirtualHost 192.168.0.208:80>
DocumentRoot /var/www/legodude
ServerName legodude.the-halls.ca
ServerAlias [www.legodude.the-halls.ca](www.legodude.the-halls.ca)
<Directory "/var/www/legodude">
allow from all
Options +Indexes
</Directory>
</VirtualHost>


second virtual host

<VirtualHost 192.168.0.212:80>
DocumentRoot "/var/www/mantis"
ServerName mantis.the-halls.ca
<Directory "/var/www/mantis">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

here is my dns host file 
this is my www ip  69.49.41.150
         
#    type    host    value    prior(MX)
                     
1    A    @    69.49.41.150    --
2    A    mail2    69.49.41.150    --
3    A    bkserver    69.49.41.150    --
4    A    goemans    69.49.41.150    --
5    A    watersedge    69.49.41.150    --
6    A    legodude    69.49.41.150    --
7    A    mail    75.125.198.178    --
8    A    ftp    69.49.41.150     --
9    A    mantis    69.49.41.150    --
10    CNAME    www    the-halls.ca    --
11    CNAME    [www.legodude](www.legodude)    legodude.the-halls.ca    --
12    CNAME    [www.mantis](www.mantis)    mantis.the-halls.ca    --
13    MX    @    mail2.the-halls.ca    (1)
14    MX    @    mail.the-halls.ca    (5)

---

