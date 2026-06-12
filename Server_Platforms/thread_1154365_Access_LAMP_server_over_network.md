---
title: "Access LAMP server over network"
date: 2009-05-09
forum: Server Platforms
---

### Post by danielgroves on 2009-05-09
Hi,

I have set-up a LAMP home-server using the latest version of ubuntu-desktop.  I have installed SAMBA as well as LAMP so I can map /var/www/ as a network drive on my vista laptop to edit files on the servers "localhost", but need to be able to access these files as if they are live.  

For example, I can go to "\\DANIEL-SERVER\www\" to edit all files that are accessed on the server by typing "localhost" into the URL bar in firefox on the actual server, in if I type "\\DANIEL-SERVER\www\" intot eh URL bar on my laptop itself then all I get is a preview of what is in that directory on my laptop.  The "\\DANIEL-SERVER\www\" location is password protected form network access on the server, so how can I view these files as-if a real server client over the home network?

Thanks,
Dan.

---

### Post by ad_267 on 2009-05-09
You should be able to access your web pages with "http://IP_ADDRESS/" where IP_ADDRESS is your local ip address. You can find out what this is by running ifconfig in a terminal, and looking at where it says "inet addr". Eg, my IP address on my local network is 10.1.1.3 so I can access my web server with "http://10.1.1.3/"

---

### Post by capscrew on 2009-05-09
> **danielgroves said:**
> Hi,

I have set-up a LAMP home-server using the latest version of ubuntu-desktop.  I have installed SAMBA as well as LAMP so I can map /var/www/ as a network drive on my vista laptop to edit files on the servers "localhost", but need to be able to access these files as if they are live.

Dan,  Don't think of it as "localhost".  Localhost only means the host you are in front of. > 

For example, I can go to "\\DANIEL-SERVER\www\" to edit all files that are accessed on the server by typing "localhost" into the URL bar in firefox on the actual server, 

By that I assume you mean can edit the data on the Apache server's web page root directory from the Vista laptop.
> 
in if I type "\\DANIEL-SERVER\www\" intot eh URL bar on my laptop itself then all I get is a preview of what is in that directory on my laptop. 

To have Apache serve the data you should use the HTTP:// prefix.  This tells the server to send the file to the requestor.  The browser then parses the data and presents it for viewing.  If you use \\server\folder the later browsers interpret this as as a need for a listing of data in the folder.
> 
 The "\\DANIEL-SERVER\www\" location is password protected form network access on the server, so how can I view these files as-if a real server client over the home network?

Thanks,
Dan.

When the network is set up correctly, you should be able to view the web pages just as you would on the Internet using [http://server](http://server) or some such name.  You could even setup a fake root domain name.  Don't use domain.local as this has now become part of the zeroconf/bonjour/ahavi setup.

---

### Post by danielgroves on 2009-05-10
Thanks all, I didn't relise it would be that simple!  Thanks for all your help!

---

