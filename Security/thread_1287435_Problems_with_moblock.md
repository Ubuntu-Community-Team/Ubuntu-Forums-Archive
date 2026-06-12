---
title: "Problems with moblock"
date: 2009-10-10
forum: Security
---

### Post by mzulkoski on 2009-10-10
A couple of weeks ago I installed moblock and mobloquer. All went well for awhile but then strange things started happening; my updates and in general any connection to ubunto servers slowed to a crawl.

I removed both moblock and mobloquer to see if that was the problem.  Now I get this when trying to use the Update Manager or when "reloading" in Synaptic:

"W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused) [IP: 127.0.0.1 4001"

The list goes on but the point is I cannot connect to localhost 127.0.0.1 etc.

And when trying to change servers in Software Sources I get this:

"No suitable download server was found - Please check your internet connection"

I suspect this is all related to moblock changing a file somewhere but I do not know where to look.

Thanks,

Mike

---

### Post by jre on 2009-10-11
Are you sure you completely removed moblock and any related packages like i.e. blockcontrol?

Please post the output of
```
dpkg -l moblock blockcontrol nfblock mobloquer
``` or just purge them to be sure
```
sudo aptitude moblock blockcontrol nfblock mobloquer
```

These packages don´t alter any other files, but still they put their own files on quite a few places on your system. So if you only installed those packages from moblock-deb-sourceforge.net (or the jre-phoenix PPA) then your system is clean after you´ve purged them. If you installed them manually or form any other source you should tell us now :-)

---

### Post by mzulkoski on 2009-10-11
Thanks jre.

Before my original post I purged moblock and mobloquer per the (your?) excellent instructions at sourceforge.

Early this morning I realized that after installing moblock I installed a couple of proxy packages to experiment with.  I removed them and after two reboots the problem is solved.

BTW, all I did was install the proxy packages.  Didn't use them,  so one or the other must have been automatic.  Moblock certainly was not the cause of the problem. 

Thanks again for your help,



Mike

---

