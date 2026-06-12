---
title: "Ntp"
date: 2007-11-30
forum: Server Platforms
---

### Post by jamart2005 on 2007-11-30
Guys... how to setup properly an ntp server in a local network?... I always get this error from ntpdate... "no server suitable for synchronization found"... but the server is broadcasting the time already... I really your need help... Thanks....

---

### Post by conjur3r on 2007-11-30
What does the following produce?

# ntpq -crv

or

# ntptrace

If it says stratum 16, then your ntp server is not synchronized and NO client will sync with it.  Usually this is because your ntp server is not able to connect to its upstream ntp server to sync with.

---

### Post by jamart2005 on 2007-11-30
It did said stratum 16... how can I set it up to make the clients sync with the time of the local server since I will just be using it for a little experiment with kerberos... 
btw, correct me if I'm wrong, is the default upstream ntp server is ntp.ubuntu.com?...
Thanks a lot...

---

### Post by conjur3r on 2007-11-30
If you do a ntptrace on ntp.ubuntu.com, nothing is returned meaning there is no ntp server at that address.  Try using an official ntp server found on [http://support.ntp.org/bin/view/Servers/WebHome](http://support.ntp.org/bin/view/Servers/WebHome)

The file you are interested in is /etc/ntp.conf.  If you are editing this file, make sure you restart the ntp daemon every time.

---

