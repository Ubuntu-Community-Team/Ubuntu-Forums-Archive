---
title: "Package monitoring tool"
date: 2009-09-11
forum: Server Platforms
---

### Post by globemast on 2009-09-11
Hi all,

I'm looking for a system where i can monitor the package update status of my Ubuntu servers.

For example:

Server 1: 4 Updates to be installed.

Server 2: 1 Update to be installed.

Server 3: Distribution Upgrade.

etc.

Do you have any ideas for such systems...? Preferable web-based.

Thank you in advance.

---

### Post by globemast on 2009-09-12
Hi ,

Any suggestions on the above?

Thanks.

---

### Post by wojox on 2009-09-12
Every time I log into my Jaunty Server it tells me that. Are you not running Jaunty Server?

---

### Post by Josh1 on 2009-09-12
> **globemast said:**
> Hi all,

I'm looking for a system where i can monitor the package update status of my Ubuntu servers.

For example:

Server 1: 4 Updates to be installed.

Server 2: 1 Update to be installed.

Server 3: Distribution Upgrade.

etc.

Do you have any ideas for such systems...? Preferable web-based.

Thank you in advance.
[http://www.canonical.com/projects/landscape](http://www.canonical.com/projects/landscape)

---

### Post by apmcd47 on 2009-09-12
Write your own? I imagine playing with the output of *apt-get -s* using perl/python/ruby may get the number and names of packages ready to be updated, and formatted into html. You could then run these as scripts over ssh (*ssh ranger /usr/local/sbin/pickupdates*) to copy them to the web server, using a cgi script. Using ajax you could even have a dynamically-updated web page allowing you to check up and the apply updates on a per-server basis, possibly even ignoring appropriate packages.

Andrew

---

### Post by cariboo on 2009-09-12
I think what you are looking for is apticron, It checks for updates, and emails you the result. Apticron is in the repositories.

---

### Post by apmcd47 on 2009-09-12
> **apmcd47 said:**
> Write your own? I imagine playing with the output of *apt-get -s* using perl/python/ruby may get the number and names of packages ready to be updated, and formatted into html. You could then run these as scripts over ssh (*ssh ranger /usr/local/sbin/pickupdates*) to copy them to the web server, using a cgi script. Using ajax you could even have a dynamically-updated web page allowing you to check up and the apply updates on a per-server basis, possibly even ignoring appropriate packages.

Andrew

[Look at this post for a script to get the number of updates available]("http://ubuntuforums.org/showthread.php?t=1012974")

---

### Post by globemast on 2009-09-16
> **Josh1 said:**
> [http://www.canonical.com/projects/landscape](http://www.canonical.com/projects/landscape)

Yes i saw landscape, 

but from what i understand unfortunately Landscape is payware :)

I've heard ok Pakiti...i don't know if anyone tested it out?

Thanks.

---

