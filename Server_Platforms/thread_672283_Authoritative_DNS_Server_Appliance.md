---
title: "Authoritative DNS Server Appliance"
date: 2008-01-19
forum: Server Platforms
---

### Post by bsc_boss on 2008-01-19
Folks,

I currently have a Microsoft win2k3 DNS server that is authorative (sp) for about 25 registered domains.  I am registered w/Godaddy, and they point to bsc.bsc-online.net.  the 2 backups are at frontiernet.net.
auth01.roc.ny.frontiernet.net & auth.lkv.mn.frontiernet.net.
I have a T1 from frontier communications w/128 ip's and have a linux web server, a windows mail server, and the windows DNS server as mentioned above.

right or wrong, i have configured an Ubuntu Dapper Drake server following the How to Forge pefect setup tutorial, and installed bind9 per said tutorial.  

What i would like to do is repalce my win2k3 DNS server with a linux one.  

Todate, i have been directed to a number of artcles about the named.conf, named.conf.options, and zone files, but cannot seem to see clearly what goes where.

Most of what i read smacks of the flavor of local dns and i need internet dns.

Additionall, i have a copy of the zone records out of the backup frontier name servers, but with no reference to the files that they are in.

Right now, my Ubunto server is running on my home/test private network and i see no problem with giving it a public ip address, but the details of the bind9 file structure are kicking my @$$.

Is this forum the right place to get real examples of which files to edit, and create for my name servers and zone name files to support my A,MX,cname, etc., records?

---

### Post by HermanAB on 2008-01-19
Well, as a minimum, you need a named.conf and a zone file.  Most problems with BIND are due to missing periods in these gawddamm files.  

Note that the MS DNS is BIND version 8.  The config files are almost exactly the same as you would need and they are hidden somewhere on the Win2003 server.  So you 'should' be able to copy the setup from the Win2003 server to the Ubuntu server and then fix the annoying little differences between BIND8 and BIND9.

The way to do that, is to run BIND9 in the foreground, so that it will give you some error messages.  Basically you have to read the man page to see what are the debug options and turn them all on, then spend a couple hours banging your head against it.

If you send me a private message then I can send you the files from my BIND9 server for reference.

'Hope that helps!

Herman

---

