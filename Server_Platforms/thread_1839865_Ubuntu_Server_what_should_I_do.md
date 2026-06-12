---
title: "Ubuntu Server what should I do?"
date: 2011-09-06
forum: Server Platforms
---

### Post by srlake314 on 2011-09-06
Ok, so here's what I want.  I have an older pc that Im going to use as my server.  What I want to do is use this pc as my own webbsite, sort of like a server for facebook, or some other website that I can also use to store info.  Not sure what selections, setup and so forth I should set up:
**Package Tasks**

                                                                                   During the Server Edition installation you have the option of installing additional packages from the CD.  The packages         are grouped by the type of service they provide.          
                                    
[LIST]
[*]                                    Cloud computing: Walrus storage service
[*]                                    Cloud computing: all-in-one cluster
[*]                                    Cloud computing: Cluster controller
[*]                                    Cloud computing: Node controller
[*]                                    Cloud computing: Storage controller
[*]                                    Cloud computing: top-level cloud controller
[*]                                DNS server: Selects the BIND DNS server and its documentation.
[*]                                LAMP server: Selects a ready-made Linux/Apache/MySQL/PHP server.
[*]                                Mail server: This task selects a variety of package useful for a general purpose mail  server system.
[*]                                OpenSSH server: Selects packages needed for an OpenSSH server.
[*]                                PostgreSQL database: This task selects client and server packages for the PostgreSQL database.
[*]                                Print server: This task sets up your system to be a print server.
[*]                                Samba File server: This task sets up your system to be a Samba file server, which is          especially suitable in networks with both Windows and Linux systems.
[*]                                Tomcat server: Installs the Apache Tomcat and needed dependencies Java, gcj, etc.
[*]                                Virtual machine host: Includes packages needed to run KVM virtual machines.
[*]                                    Manually select packages: Executes **apptitude** allowing you to individually select packages.
[/LIST]
                 
Are the selections given, and I'm not sure which selection.  I have it now setting up "base system" because the dhcp setup couldnt detect anything(currently not hooked up to internet).  Anything you could suggest?

---

### Post by haqking on 2011-09-06
> **srlake314 said:**
> Ok, so here's what I want.  I have an older pc that Im going to use as my server.  What I want to do is use this pc as my own webbsite, sort of like a server for facebook, or some other website that I can also use to store info.  Not sure what selections, setup and so forth I should set up:
**Package Tasks**

                                                                                   During the Server Edition installation you have the option of installing additional packages from the CD.  The packages         are grouped by the type of service they provide.          
                                    
[LIST]
[*]                                    Cloud computing: Walrus storage service
[*]                                    Cloud computing: all-in-one cluster
[*]                                    Cloud computing: Cluster controller
[*]                                    Cloud computing: Node controller
[*]                                    Cloud computing: Storage controller
[*]                                    Cloud computing: top-level cloud controller
[*]                                DNS server: Selects the BIND DNS server and its documentation.
[*]                                LAMP server: Selects a ready-made Linux/Apache/MySQL/PHP server.
[*]                                Mail server: This task selects a variety of package useful for a general purpose mail  server system.
[*]                                OpenSSH server: Selects packages needed for an OpenSSH server.
[*]                                PostgreSQL database: This task selects client and server packages for the PostgreSQL database.
[*]                                Print server: This task sets up your system to be a print server.
[*]                                Samba File server: This task sets up your system to be a Samba file server, which is          especially suitable in networks with both Windows and Linux systems.
[*]                                Tomcat server: Installs the Apache Tomcat and needed dependencies Java, gcj, etc.
[*]                                Virtual machine host: Includes packages needed to run KVM virtual machines.
[*]                                    Manually select packages: Executes **apptitude** allowing you to individually select packages.
[/LIST]
                 
Are the selections given, and I'm not sure which selection.  I have it now setting up "base system" because the dhcp setup couldnt detect anything(currently not hooked up to internet).  Anything you could suggest?

LAMP is the basic WEB server build


Anything else you can add later once things are up and running, possibly SSH depending on how you want to administer your box.

Read here [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

a little out of date but concepts for LAMP is pretty similar.

---

### Post by srlake314 on 2011-09-06
It's now asking for an HTTP proxy information access the outside world...If I leave this blank now, would it cause problems later?

---

### Post by haqking on 2011-09-06
> **srlake314 said:**
> It's now asking for an HTTP proxy information access the outside world...If I leave this blank now, would it cause problems later?


Do you use a HTTP proxy ? if not then leave it blank, if you do you can change things later.

I recommend reading the above resource before carrying on

---

