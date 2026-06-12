---
title: "Unable to install ColdFusion 9 on ubuntu 9.10 &amp; 9.04"
date: 2009-11-25
forum: Server Platforms
---

### Post by mleger on 2009-11-25
When i run the bin file on either a 9.10 or 9.04 ubuntu system (only 2 tested right now) the installer gets ready to start then fails saying it cannot find the java folder in the temp directory

```
[m]0;root@ColdFusion01: ~root@ColdFusion01:~# chmod +x ColdFusion_9_WWE_linux.bin
]0;root@ColdFusion01: ~root@ColdFusion01:~# sudo ./ColdFusion_9_WWE_linux.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

exec: 2470: /tmp/install.dir.4145/Linux/resource/jre/bin/java: not found
```

I started my guide from here => [http://www.howtoforge.com/installing-apache-and-coldfusion-9-on-ubuntu-9.04](http://www.howtoforge.com/installing-apache-and-coldfusion-9-on-ubuntu-9.04)

i tired on ubuntu 9.10 and 9.04 just today.

i have tried getting help from adobe, rackspace and now ubuntu and my questions go ignored.

Please help

---

### Post by Vegan on 2009-11-25
You might need to install Tomcat which supports Java on Linux servers.

```
sudo tasksel
```

and choose Tomcat

---

### Post by mleger on 2009-11-25
already installed according to tasksel

---

### Post by IkeLewis on 2009-12-02
Are you building from source or installing a binary?

---

### Post by mleger on 2009-12-04
issue resolved, apparently rackspace servers are 64 bit by default and i was trying to install a 32 bit file.

fine now.

thanks.:popcorn:

---

