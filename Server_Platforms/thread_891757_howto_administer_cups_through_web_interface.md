---
title: "howto administer cups through web interface?"
date: 2008-08-16
forum: Server Platforms
---

### Post by stairwayoflight on 2008-08-16
Hello,

I followed the tutorial here:
[http://ubuntuforums.org/showthread.php?p=1831119](http://ubuntuforums.org/showthread.php?p=1831119)

Up to the point where I am supposed to be able to get an administration page when connecting the browser to port 613 of the box. All I get is "413 Forbidden."

I read somewhere that debian/ubuntu restrict remote admin'ing of cups by default and that it has to be enabled, but I don't know how.

This is just a sub-problem of my larger problem, which is getting printer sharing to work on ubuntu-server like it did on u-desktop.

Any suggestions on .conf file tweaks, etc?

---

### Post by Girya on 2008-08-16
change your /etc/cups/cupsd.conf file stanza to below ie: Allow 192.168.1.100 if you are trying access the interface from 192.168.1.100

> # Restrict access to the admin pages...
<Location /admin>
Order allow,deny
Allow <your ip address>
</Location>

You need to change this stanza also to whatever your local network is. this would allow anyone with an ip address 192.168.1.0 to 192.168.1.255 to print. ( I have DHCP server set up to deny all clients except hosts with specified MAC addresses for security)

> # Restrict access to the server...
<Location />
  Order allow,deny
Allow from @LOCAL
Allow 192.168.1.*
</Location>



Then restart cups server: 


> sudo /etc/init.d/cupsys restart

---

### Post by stairwayoflight on 2008-08-17
Thanks for the suggestion, but I applied the changes and restarted cupsys and I still can't use the admin interface from firefox; even a reboot didn't help.

I managed to install elinks and use that locally through an ssh session though.

---

