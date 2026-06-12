---
title: "New to Ubuntu, need suggestions!!!"
date: 2009-01-06
forum: Server Platforms
---

### Post by Turbotalk03 on 2009-01-06
Everyone, my name is Jason Hejny, I am currently stationed in Iraq on a depolyed tour for the Air Force.  The members of our squadron have purchased a satellite internet connection that gets 1.2 Mbps tops.  We have about 70 people on the network, 50 of which could be using the internet at any one time.  The network is currently being stood up with a Cisco 2600 router, that in my opinion is not up to the task, with multiple wire switches.  This network has been up for a couple of years now, and the cabling is starting to wither away(all out doors).  I am looking at setting up a WiFi connection with mulitple gateways and a server to control it all.  The main issue that I can see is when I go home, some poor sole gets to come out and work on this on his days off.  I need the server to be user friendly.  Windows was looking like a viable option, but if I am going to take the time and do this, I want to set the server up to do DNS Caching, and web caching with Squid. I have not been able to find any reasonable software that will work with windows to do web page caching.  The server will also need to do the DHCP side as well, so I can setup user accounts, for both windows and Mac machines.  I know that this can be done with Linux, but the question is how user friendly is it once it is all set up?  I have experience with some of the older versions of Red Hat but thats about it.  

The second problem is our internet connection and download speeds.  I am currently trying to download the server version of Ubuntu, but it is expected to take 60hrs to do it.  Can you buy the Server and desktop versions of Ubuntu, install the server version and then install the Gnome GUI from the Desktop CD?  Like I said before I would really like to use Linux on this machine because of its stability, but I need to know it is going to work, do to obvious supply issues and time constraints.  Any guidance that can be given in this area will be greatly appreciated.  Thank you in advance for you help.

Jason

---

### Post by the.ciscokid on 2009-01-06
How about looking into [webmin]("http://webmin.com/")... I haven't used it myself to be honest - but that would remove the need for the GUI download at least.

Just found [this]("http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html") which may be worth reading through.

Hope that helps!

---

### Post by nkassi on 2009-01-06
You could look at something like [http://www.vyatta.org]("http://www.vyatta.org") to replace your aging cisco router. I've use it here at florida state university as a gateway. Since it runs linux it can also run your dns server and squid all in one place. 

The newest release includes snort and clamav for added security. And in the comming months they will be re-adding a nice webinterface which should make this much much more userfriendly (It was removed when they did a major rewrite of their code.)

---

### Post by cariboo on 2009-01-06
You can request a free cd [here]("http://shipit.ubuntu.com/"), you can get both the desktop and server versions.

Jim

---

### Post by my_key on 2009-01-06
> Can you buy the Server and desktop versions of Ubuntu, install the server version and then install the Gnome GUI from the Desktop CD?

Yes. See: [https://help.ubuntu.com/8.10/add-applications/C/offline.html](https://help.ubuntu.com/8.10/add-applications/C/offline.html)

---

