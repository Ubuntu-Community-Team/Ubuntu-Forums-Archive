---
title: "Printing from a Ubuntu Webserver to a (USB) Printserver."
date: 2012-04-09
forum: Server Platforms
---

### Post by victorbenjamin3000 on 2012-04-09
Hi everyone,

I trying to find out if an Ubuntu webserver (shared hosting solution running my Magento based webstore) can send a print job using LPD/LPR to a USB print server in my local office network.


Webhosting solution -> Cronjob -> Shell script (Print) -> Printserver in my local office network

I have a PHP script that automatically generates a PDF of new orders/invoices and saves them in a certain folder on the server. My plan is to use a shell script, or any other solution, to send a print job to my local print server connected to the internet.

I understand this can be done using lpr filename and or specify the printer etc, but is it possible to print to an external printer?

Thanks,

Victor

---

### Post by volkswagner on 2012-04-09
Are other WAN devices able to print to this printer from outside the LAN?
I think you want the ipp (ipp://server.ip:port_number) printer protocol for your server to connect.
Have you tried a more local approach, such as using wget, ssh/sftp to download the file then send to the printer?

---

