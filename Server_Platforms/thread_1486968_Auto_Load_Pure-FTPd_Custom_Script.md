---
title: "Auto Load Pure-FTPd Custom Script"
date: 2010-05-18
forum: Server Platforms
---

### Post by bananafishbones on 2010-05-18
As the title reads, I need to learn of the best way to load a custom set of switches or script for Pure-FTPd.

The reason I ask is that for some strange reason, I had to add the -H switch on a new install to allow clients to connect.

In the past I had added the line below to the following location:
Pure-ftpd startup script is located in /etc/rc.local
/usr/sbin/pure-ftpd -A -B -c 10 -C 2 -E -k 95 -T 45 -u 1000 &

I'm not sure this script though is what's loading Pure-FTPd since I added the line below.

sudo update-rc.d pure-ftpd defaults

Now there is an example within /etc/default/pure-ftpd-common that appears to allow you to point to a startup script. Should I use this instead? 

# example: UPLOADSCRIPT=/usr/local/sbin/uploadhandler.pl

I'm confused as I thought I had this install down pat but with the problem with needing to add the -H switch, I find that I may not have things working as I had specified.

Thank you for any help you can provide.
Cheers,
BF

---

