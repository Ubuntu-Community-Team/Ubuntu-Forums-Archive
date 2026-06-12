---
title: "long connect to repositories"
date: 2013-11-08
forum: Ubuntu Development Version
---

### Post by lonniehenry-gmail on 2013-11-08
When I try to update using synaptic, there is a long lag before the repositories are checked and it takes a long time to complete the check of the reload.  If I select updates, I select apply and it takes 30 seconds to a minute to begin hankdownloading the updates.  If I do it from terminal using cli, it seems to hang on getting the ip address for the repository.  It shows a ipv6 address when it hangs.  If I wait sooner or later it will continue until it hangs again.  Where to start looking for a solution?  I don't seem to have a problem with browsers finding and loading sites. 
Thanks in advance.Testing Trusty  (been using ubuntu since dapper)  
Lonnie

---

### Post by cpatrick08 on 2013-11-08
> **lonniehenry-gmail said:**
> When I try to update using synaptic, there is a long lag before the repositories are checked and it takes a long time to complete the check of the reload.  If I select updates, I select apply and it takes 30 seconds to a minute to begin hankdownloading the updates.  If I do it from terminal using cli, it seems to hang on getting the ip address for the repository.  It shows a ipv6 address when it hangs.  If I wait sooner or later it will continue until it hangs again.  Where to start looking for a solution?  I don't seem to have a problem with browsers finding and loading sites. 
Thanks in advance.Testing Trusty  (been using ubuntu since dapper)  
Lonnie
I have the same problem with ppas on saucy xubuntu

---

### Post by cariboo on 2013-11-08
> **lonniehenry-gmail said:**
> When I try to update using synaptic, there is a long lag before the repositories are checked and it takes a long time to complete the check of the reload.  If I select updates, I select apply and it takes 30 seconds to a minute to begin hankdownloading the updates.  If I do it from terminal using cli, it seems to hang on getting the ip address for the repository.  It shows a ipv6 address when it hangs.  If I wait sooner or later it will continue until it hangs again.  Where to start looking for a solution?  I don't seem to have a problem with browsers finding and loading sites. 
Thanks in advance.Testing Trusty  (been using ubuntu since dapper)  
Lonnie

Which mirror are you using?

---

### Post by vasa1 on 2013-11-09
> **cariboo907 said:**
> Which mirror are you using?

I'm using the main one, not any mirror. It's getting stuck at ppa.launchpad.net (91.189.95.83)

And it maybe "down for everyone": [http://www.isup.me/91.189.95.83](http://www.isup.me/91.189.95.83)

I'm using **sudo apt-get update**.

```
Err http://ppa.launchpad.net saucy InRelease        
  
Err http://ppa.launchpad.net saucy Release.gpg      
  Unable to connect to ppa.launchpad.net:http:
Reading package lists... Done
W: Failed to fetch http://ppa.launchpad.net/lubuntu-dev/non-official-apps/ubuntu/dists/saucy/InRelease  

W: Failed to fetch http://ppa.launchpad.net/lubuntu-dev/non-official-apps/ubuntu/dists/saucy/Release.gpg  Unable to connect to ppa.launchpad.net:http:

W: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  openssh-client

```

---

### Post by cariboo on 2013-11-09
I got a failure notice, tonight too. I didn't pay attention to how long it took to update the sources list, or download the updates, but there was a notice that it failed to download some packages from the ppas I have enabled. I have synaptic running on another desktop, so I don't always notice any problems right away.

---

### Post by monkeybrain20122 on 2013-11-09
Me too. Usually it takes long to when it has difficulty reaching the server because it will try until time out, so if the server is down or something it is normal to take long time to update the database (and exit with warning)

---

### Post by Elfy on 2013-11-09
works ok for me now - probably you got hit by this [https://twitter.com/launchpadstatus/status/398980619880775680](https://twitter.com/launchpadstatus/status/398980619880775680)

---

### Post by lonniehenry-gmail on 2013-11-09
Thanks, guys.  Thought it was only me.  Just got back from vacation and couldn't figure out what was wrong.

---

### Post by Elfy on 2013-11-09
> **lonniehenry-gmail said:**
> Thanks, guys.  Thought it was only me.  Just got back from vacation and couldn't figure out what was wrong.

Neither could they till the cleaner owned up to using the wrong plug for the vacuum cleaner :P

---

### Post by QDR06VV9 on 2013-11-09
> **Elfy said:**
> Neither could they _till the cleaner owned up to using the wrong plug for the vacuum cleaner :P_

LMAO I can just imagine the look on there face now!](*,)
Thanks Elfy.

---

### Post by Bucky Ball on 2013-11-09
Yep, all good here now, too. I was having a problem for a few days with anything from Launchpad. Couldn't work out why it was stalling there.

---

