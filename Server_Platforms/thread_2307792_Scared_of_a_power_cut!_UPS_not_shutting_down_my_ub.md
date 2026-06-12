---
title: "Scared of a power cut! UPS not shutting down my ubuntu server!! Please help."
date: 2015-12-28
forum: Server Platforms
---

### Post by jonah1980 on 2015-12-28
Hi I have an APC ES550 ups and I'm running ubuntu server 14.04.3

I've installed NUT and set up the config files best I could from what I've read online. I thought everything was working great so I tested a power out and disconnected my UPS from the wall socket. The UPS wasn't fully charged but said I had 45% battery left.

It started beeping etc and I could see from my Webmin UPS monitoring module the battery going down slowly when suddenly BAMM! Server just goes off, monitor off and power off without any attempts at a shutdown. I couldn't even get to the wall socket fast enough to avoid everything just powering out.

Now I'm not sure what to do, how can I get nut to properly power down my server sooner rather than later (or too late in this case!!) in the event of a power cut?

Thank you for any help at all.

---

### Post by darkod on 2015-12-28
I haven't touched ups config in ubuntu but can something like this help you for apc model?
[https://help.ubuntu.com/community/apcupsd](https://help.ubuntu.com/community/apcupsd)
[http://www.cyberciti.biz/faq/debian-ubuntu-centos-rhel-install-apcups/](http://www.cyberciti.biz/faq/debian-ubuntu-centos-rhel-install-apcups/)

---

### Post by jonah1980 on 2016-01-10
Thanks, adding an admin user to the config file seems to have fixed things!

---

