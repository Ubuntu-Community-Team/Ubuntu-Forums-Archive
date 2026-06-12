---
title: "Ubuntu Server, FGS Environment, wget problems"
date: 2009-03-21
forum: Server Platforms
---

### Post by 0bsidian on 2009-03-21
I'm running a Ubuntu server and have installed FGS (includes apaches pre configured to work with the rest of the tools in FGS for web applications involving geospatial data). There is a script within FGS that deals with installing new FGS related modules used at command thus;

$ FGS install module_name:version location

The installation script uses wget to retrieve files. I've had a problem with it (and attempted to use wget alone to download the files on my home laptop as well as the server with the same issues). wget is returning a 404 error even though I can surf to the page with a browser and ping the server. It may be useful for you to know that the files are zipped tarballs (.tar.gz). Anyone know why I'm getting a 404 with wget, but can reach the information by other means? I can download the files using Firefox, but I'm also having some weird problems with scp and can't get them to the server that way. I would have thought it was a problem then with my server except that I'm getting the same wget problem from my laptop. Any help is appreciated,

Chris

---

### Post by cariboo on 2009-03-21
A little more info would be helpful the only thing I came up with when checking google for FGS was Fish Guidance System :) and others not related to servers.

Jim

---

### Post by 0bsidian on 2009-03-21
Oh sorry - I suppose I should clarify. FGS is a bundle of pre-configured packages specifically designed to be an environment for operating geospatial web-servers and web-applications. MapServer is essentially jsut a CGI handler (itself a CGI) that is also specifically designed to provide an interface between your website and a Geographic Information System back-end (I'm using Geographic Resource Analysis Support System - GRASS).

"The FGS Linux Installer is a self-extracting file that will install MapServer with PHP/MapScript and all of their dependencies on your Linux system. It provides a stand-alone environment with all the required software (incl. Apache and PHP) to run PHP/MapScript webmapping applications."

links:
[http://www.maptools.org/](http://www.maptools.org/)
[http://wiki.osgeo.org/wiki/FGSDevNotes](http://wiki.osgeo.org/wiki/FGSDevNotes)

The problem I'm having with it all right now involves wget and the install script for FGS (see [http://www.maptools.org/fgs/index.phtml?page=downloads.html](http://www.maptools.org/fgs/index.phtml?page=downloads.html) at the bottom of the page under installing modules). Thanks again for the help,

Chris

---

### Post by cariboo on 2009-03-21
I just tried the wget command at the bottom of th page and it worked without any problems. are you pasting the command in a terminal eg:

```
wget -q http://www.maptools.org/dl/fgs/releases/1.0/1.0.0/installer.sh ; sh installer.sh
```

the $ at the start of the command on the webpage tells you to run as a normal user. If there had been a # sign at the start of the command, it means you should run the command as root.

Jim

---

### Post by 0bsidian on 2009-03-21
I tried it at the command line for the particular module I want. I can also ping the server with 0% packet loss - so I'm really confused about the 404 error.

```

ccarleton@ccarleton-laptop:~$ wget http://dl.maptools.org/dl/fgs/releases/1.0/1.0.0/modules/fgs-kamap-1.0-20070205-linux-i386.tar.gz
--20:12:39--  http://dl.maptools.org/dl/fgs/releases/1.0/1.0.0/modules/fgs-kamap-1.0-20070205-linux-i386.tar.gz
           => `fgs-kamap-1.0-20070205-linux-i386.tar.gz'
Resolving dl.maptools.org... 209.172.32.228
Connecting to dl.maptools.org|209.172.32.228|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
20:12:39 ERROR 404: Not Found.

ccarleton@ccarleton-laptop:~$ 


```

---

### Post by 0bsidian on 2009-03-21
I just noticed the typo - the error message is correctly responding to the lack of ...kamap-1.0... because the only file there is ...kamap-base-1.0... this solved everything - for now. Although I'm finding webservers and networking to be very complicated so I'm sure there will be more problems. Thanks for the help!

Chris

---

### Post by untana on 2010-06-10
This is throughly not the environment problem therefore i am not able to answer this,all the best 




[]("http://www.MSDScompliance.com")

---

