---
title: "debian-transmission group problem"
date: 2010-12-26
forum: Security
---

### Post by brainformat on 2010-12-26
Hi!
I have quite an annoying problem with group permissions. 
I use Transgui as a client for transmission-daemon. It works great, but files downloaded by it are owned by owner "debian-transmission" and group "debian-transmission" and therefor I, as a regular user, can not remove or edit those files (write permission).
Also, the partition I download files to has to be owned by group "debian-transmission".
I know that i can change permissions of the files with chmod, but i wonder whether it is possible to change ownership of transmission-daemon and make it owned by me as a regular user? I think that would be the most elegant solution.
The other solution would be to alow transmission-daemon to write on partitons I owe and to alow me to write on all files owned by "debian-transmission". 
What of theese two metods would be easier to achieve and how to do it?

thanx a lot!

---

### Post by mikewhatever on 2010-12-27
This howto pretty much has you covered.
[http://1000umbrellas.com/2010/10/04/updated-transmission-installationconfiguration-on-ubuntu-server](http://1000umbrellas.com/2010/10/04/updated-transmission-installationconfiguration-on-ubuntu-server)

---

