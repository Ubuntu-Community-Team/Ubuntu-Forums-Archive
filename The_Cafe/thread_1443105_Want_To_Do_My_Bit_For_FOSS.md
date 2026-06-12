---
title: "Want To Do My Bit For FOSS"
date: 2010-03-30
forum: The Cafe
---

### Post by jsriz on 2010-03-30
We have a budding foss community at our college.
And my discipline being computer science have a dear bond with ubuntu as it is the one used in all our labs .
Well I frankly started using ubuntu because of this reason, loved the experience so much as I wiped out windows after a week of inactivity in windows .
At our college there are about 120 people enrolled into our dicipline and almost everyone has a system and almost half of us decide to install ubuntu that is nearly 60-65 installations per year .
as everyone needs upgrading it takes hours to downloading form the main server or server for india 
I would like to know how to set up a server so that everyone at our college can access for upgrading and installing purposes.Is there a way to show it up in the synaptic repository along with server for india??

---

### Post by Crunchy the Headcrab on 2010-03-30
A quick google search brought up a program called apt-mirror.  It is in the repositories.  You can use it to set up a mirror of the ubuntu servers and share it with the LAN.  If you have an Apache server you can even access the mirror over the web.

I'm not sure if this is what you're looking for but at least by posting this I have bumped your thread. ;)

---

### Post by undecim on 2010-03-30
Apt-cacher.

It has to be set up properly on the client though. Or maybe you could get your IT adminstration to redirect all http traffic from the repos to the server and make it completely transparent.

Also, make sure you add getdeb, playdeb, and launchpad PPA's, too.

---

