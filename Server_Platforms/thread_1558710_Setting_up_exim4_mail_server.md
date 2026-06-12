---
title: "Setting up exim4 mail server"
date: 2010-08-22
forum: Server Platforms
---

### Post by klaasvg on 2010-08-22
Hi,

I try to set up a mail server using the tutorial book of Mark Sobell. I already have a domain name: drsklaus.nl, according to the help the MX record should already point of my IP address by default.

I took the following steps:
-Installing the exim4 packages
-Forwarding port 25 on my router to the right LAN IP address (192.168.1.100)
-Configuring the /etc/exim4/update-exim4.conf.conf file, the following settings are modified:
dc_eximconfig_configtype='internet'
dc_other_hostnames='drsklaus.nl'
dc_local_interfaces=''
-Restart the exim server:
sudo /etc/init.d/exim4 restart

According to the tutorial, mail sent to the domain now should be caught by the server and visible in the directory:
/var/spool/exim4/input

But when I try to send a mail to [email]klaas@drsklaus.nl[/email], nothing seem to happen and the directory stays empty. I definatetly miss something here...
Any ideas are very welcome :)
TIA, Klaas

---

