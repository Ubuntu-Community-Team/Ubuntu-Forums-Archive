---
title: "Moving web server to new machine"
date: 2010-04-28
forum: Server Platforms
---

### Post by cr0nick on 2010-04-28
So ive been trying to do this for a few days now and it keeps getting worse and worse. I have a webserver running Ubuntu 9.10. I need to move this server to a virtual machine I have setup using VMWare Server 2.0. 

I tried using The VMWare vCenter converter for two days with no luck whatsoever. So ive given up on that and read a thread about how it is possible to just zip everything on my current server and unzip it onto the new one and be good to go. 

My question is, are there any tutorials that can walk me through this? What tool(s) should I use? Is there a better way?

Thanks!

---

### Post by windependence on 2010-04-28
If the server you are moving is already running as a VM, then most certainly you can just copy the directory over to the new machine, right click on the .vmx file and click on "add to inventory". Then fire it up. You CAN use converter to do this, you just need the correct version that will allow you to pick "other" as the target. Unfortunately this is probably going to be the Windoze version as VMware support for Linux is not what it is for Windoze.

-Tim

---

### Post by ghost_ryder35 on 2010-04-28
I'd just tar up your web servers directory (usually /var/www/ but look in /etc/apache2/httpd.conf), and /etc/apache2/.  Keep in mind if you installed something like Nagios3 or Drupal6 the web directory might be /usr/share/nagios3/ and it might also reference scripts in /usr/lib/<blah>.

So what I would recommend is to follow this how to guide.
[http://www.windley.com/archives/2007/08/p2v_how_to_make_a_physical_linux_box_into_a_virtual_machine.shtml](http://www.windley.com/archives/2007/08/p2v_how_to_make_a_physical_linux_box_into_a_virtual_machine.shtml)

Oh yea you could also 'dd' the physical machines drive and move the file generated from that to the VMware Server and mount that.

---

### Post by koenn on 2010-04-28
I'd go somethin,g along this route:

- set up the new machine with OS + apache, preferably the same versions as the old server
-copy /etc/apache + subdirs
-copy /var/www  and/or any other web content dir (incl. subdirs)
-restart apache

you can use scp or rsync to do this

you may have to reset ownership and permissions on /var/www (or whereever your web content is)

---

### Post by cr0nick on 2010-04-30
> **ghost_ryder35 said:**
> I'd just tar up your web servers directory (usually /var/www/ but look in /etc/apache2/httpd.conf), and /etc/apache2/.  Keep in mind if you installed something like Nagios3 or Drupal6 the web directory might be /usr/share/nagios3/ and it might also reference scripts in /usr/lib/<blah>.

So what I would recommend is to follow this how to guide.
[http://www.windley.com/archives/2007/08/p2v_how_to_make_a_physical_linux_box_into_a_virtual_machine.shtml](http://www.windley.com/archives/2007/08/p2v_how_to_make_a_physical_linux_box_into_a_virtual_machine.shtml)

Oh yea you could also 'dd' the physical machines drive and move the file generated from that to the VMware Server and mount that.

I followed this guide and it booted right after i copied the image over but now I dont have an eth0 interface, I set the VMWare to give it a bridged connection. Any ideas?

Edit: Got it!! 

Had to remove a file for persistent connections

---

### Post by ghost_ryder35 on 2010-04-30
> **cr0nick said:**
> I followed this guide and it booted right after i copied the image over but now I dont have an eth0 interface, I set the VMWare to give it a bridged connection. Any ideas?

Edit: Got it!! 

Had to remove a file for persistent connections

awesome, super glad it worked for you!

---

