---
title: "One way communication between Docker containers"
date: 2020-04-08
forum: Virtualisation
---

### Post by Drenriza on 2020-04-08
Hi all!

I have a question i cant quite find a answer too (_**very new**_ to Docker).
I have three Docker containers in the same network, i would like for container1 (tomcat webapp) to be able to contact container2 (mysql) - works.
But container3 (tomcat webapp) should not be able to contact container1.

So both container1 and container3 can contact container2, but container1 and container3 cannot contact eachother.
Is that possible?

Thanks on advance!
Best regards!

---

### Post by kevdog on 2020-04-11
Yes what you want to do is possible.  I'm not hugely experienced with docker either although I've been running containers for about 6 months.  What your describing in a way is a firewall.  Must applications in docker are built on top of a base linux distribution.  In my experience I've commonly seen alpine linux, ubuntu and debian used as these base distributions. It's possible to login to the container you want to protect and setup the firewall within the particular container to limit access.  The only problem with this solution is that when your container becomes updated you'll lose your changes.  To preserve your changes you are going to have to set up a Docker file that will build your changes back into the container.  Heck you could even host this dockerfile on docker hub and pull from this repository for the image rather than the source.  What i like about docker hub for this purpose is everytime the parent image is updated, your image will be updated as well and then your changes built back into your image.  It's very convenient.

There may also be other ways to do what you want.  You might want to ask on other forums for other suggestions.

---

