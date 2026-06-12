---
title: "New User Needs Connection"
date: 2010-01-03
forum: Server Platforms
---

### Post by psb962 on 2010-01-03
Hi

I downloaded the ubuntu server (command line only) iso and set up a server on a spare computer. The only partition is ubuntu. 

LAMP server installed, and runs.

Its plugged into my home network and the router assigns it a DMZ.

I use ptty and that allows me to connect the server from my Windows PC. 

I installed samba and that works, I set up the server as Z: to my windows PC, and I can now use Filezilla FTP to move gigs of files over from my windows PC to the ubuntu server. I have to log in to activate the connection to Z: but it works.

Problem is getting a database connection from my windows PC (client) to my ubuntu server. Server is running a MySQL server and an Apache Derby server but both give connection:refused every time I try to connect with a java app, or with ij from my client. I tried MySQL Workbench, as that has a GUI, that doesnt connect to MySQL either. 

Every time I start my server I have to add lots of jar files to the CLASSPATH just to get the Derby server running. The Derby client connection on my client PC is also properly set up with PATH and CLASSPATH etc etc all configured and tested. But the server refuses every attempt to connect even though it tells you the Derby server is up and runnign as listening on port 1527!!! 

What I want is a script or app that will "unlock" my server so I can actually do something with it instead of constantly trying new settings and packages in the vain hope it will then actually 'serve'. 
 
I am missing something here. There is nothing of value on this server that cannot be 'exposed' to the internet,  so I'd be happy to turn off all the security just so the damn thing allowed connections...! 

Help.

---

### Post by sylvester_0 on 2010-01-03
I'm not quite sure what Apache Derby is but I believe that MySQL is configured to listen on [bind-address = 127.0.0.1 (localhost)] by default. Comment this under /etc/default/mysql or /etc/mysql/my.cnf then restart the service and you should be good to go. Maybe Derby is configured to listen on localhost too?

No matter how much you aren't worry about your data I wouldn't DMZ a server. Either NAT port forward it or run a firewall.

---

### Post by psb962 on 2010-01-04
Derby is a small DB app that's pure java and can be embedded in a distributable java app or run as a small network and client server. I'm just finishing a java primer and its the app the book uses to teach db connectivity without too much drama. I went a stage further and tried to connect client - server rather than just embedded so made it harder for myself..

Anyway, I commented out the bind and with a few more actions got it connected, as follows:

I had to configure the Derby server with 

java -jar derbyrun.jar server start -h 192.168.0.105 

which told it the network IP it was hosting from...

...and it then gave me some exceptions about the "" user string so I didn't pass any user or password properties to the driver, to take care of that.

It then connected and ran through all the test sequences in my java code.

So tomorrow I'll turn to MySQL and try to get that going via odbc.

---

