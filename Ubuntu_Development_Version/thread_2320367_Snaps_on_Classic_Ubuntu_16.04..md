---
title: "Snaps on Classic Ubuntu 16.04."
date: 2016-04-13
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2016-04-13
It seems that development of 16.04 will continue a little bit after release day.

> In Ubuntu 16.04 LTS we will make it  possible to install snap packages alongside traditional deb packages.  These two packaging formats live quite comfortably next to one another  and enable us to maintain our existing processes for development and  updates to the OS. This reinforces our relationship with the Debian  community and it enables developers and communities to publish either  debs or snaps for the Ubuntu audience.

> Developers of paid apps have often been  the most frustrated with having to manage dependencies and compatibility  with various libraries, especially on older releases of Ubuntu. For  this reason these applications are going to be migrated from debs to  snaps_ by Autumn 2016._ Canonical will work with the developer community  to support that transition in the coming months with tools, training and  documentation. 

[http://insights.ubuntu.com/2016/04/13/snaps-for-classic-ubuntu/](http://insights.ubuntu.com/2016/04/13/snaps-for-classic-ubuntu/)
 
There is a Snaps on classic Ubuntu Q&A on Ubuntu On Air tomorrow (14th April) at 15.00 UTC. If anyone is interested.

Regards.

---

### Post by rrnbtter on 2016-04-13
Greetings,
Thanks for the info. This goes a long way towards explaining the (what for?) that has been present in the downstream since Wily. So it isn't all for nothing after all. Now what about all of that Mir stuff I have been seeing? Could be that's not dead either.

---

### Post by Morbius1 on 2016-04-13
Probably need a developer to answer this question but doesn't this snappy thingie sound a lot like an OSX app where some, most, or all of the dependencies are contained within the .app bundle?

On OSX these babies are huge.

---

### Post by rrnbtter on 2016-04-13
Greetings,

> **Morbius1 said:**
>  doesn't this snappy thingie sound a lot like an OSX app where some, most, or all of the dependencies are contained within the .app bundle? 

They (Canonical) intend to poll the app devs and create a dependency library that can support most or possibly all apps. The devs are spending more time managing dependencies than writing apps. That won't work very well.

---

### Post by grahammechanical on 2016-04-13
> doesn't this snappy thingie sound a lot like an OSX app where some,  most, or all of the dependencies are contained within the .app bundle?

There is a similarity and obviously such a system can lead to duplication of libraries being installed. And work is being done to reduce that duplication. Snap packaging is an evolution of click packaging which is used on Ubuntu phones & tablets. So, Ubuntu devs are starting from a baseline of limited storage space. The intention is for application developers to use the Ubuntu SDK & Snapcraft to create their apps & then have them available for phone, tablet & desktop Ubuntu and scale according to the form factor.

Is there a difference between having all dependencies in the app bundle & having a package manager work through a list of dependencies and download them? An app that is Debian packaged might have a relatively small deb file but then pull in a massive amount of other files as dependencies. Unless they are already on the system. It seems to me to be as broad as it is long.

[URL="https://developer.ubuntu.com/en/snappy/build-apps/"]https://developer.ubuntu.com/en/snappy/build-apps/
[/URL]
Regards.










[https://developer.ubuntu.com/en/snappy/build-apps/](https://developer.ubuntu.com/en/snappy/build-apps/)

---

