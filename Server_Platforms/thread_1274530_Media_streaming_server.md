---
title: "Media streaming server"
date: 2009-09-24
forum: Server Platforms
---

### Post by wlraider70 on 2009-09-24
I'm not sure if this is the right place, please move it if not.

I'm interested in setting up a media streaming server to stream live video. 

Would that be a specific server distro, is that a feature in Apache, or is it simply a specific program that would work on any distro?

Thanks.

---

### Post by openfly on 2009-09-24
Are you looking to do this in your house or across the internet?

---

### Post by Lars Noodén on 2009-09-25
I used icecast a long time ago on Apache.  There are several streaming tools to work with now.  A new one is Darwin Streaming Server:
[indent][http://dss.macosforge.org/](http://dss.macosforge.org/)[/indent]

Or you can be traditional and go with icecast or videolan on Apache2.
[indent]
  [http://packages.ubuntu.com/jaunty/icecast2](http://packages.ubuntu.com/jaunty/icecast2)
  [http://www.videolan.org/vlc/streaming.html](http://www.videolan.org/vlc/streaming.html)
  [http://packages.ubuntu.com/jaunty/vls](http://packages.ubuntu.com/jaunty/vls)
[/indent]

Are you OK with Apache2 or were you looking for Lighttpd or nginx instead?   VLS and Icecast should work on any AFAIK.

---

### Post by i.r.id10t on 2009-09-25
Look at Darwin Streaming Server from Apple.

---

### Post by wlraider70 on 2009-09-30
across the internet, but out of curiosity what would the difference be?

i am not yet familiar with Apache, but i would be willing to learn a bit of it to accomplish this task.

---

### Post by Lars Noodén on 2009-10-01
It was a long while since I looked at Icecast so I installed Icecast2.
It looks like icecast2 does not need anything else it will stream on its own.  

[http://www.icecast.org/docs/icecast-2.3.2/icecast2_basicsetup.html](http://www.icecast.org/docs/icecast-2.3.2/icecast2_basicsetup.html)
[http://www.icecast.org/docs/icecast-2.3.2/icecast2_config_file.html](http://www.icecast.org/docs/icecast-2.3.2/icecast2_config_file.html)
[http://www.icecast.org/docs/icecast-2.3.2/icecast2_admin.html](http://www.icecast.org/docs/icecast-2.3.2/icecast2_admin.html)

Things change.  


Just for future reference here is a howto on proxying icecast through Apache, but that's not needed

[http://blogs.linux.ie/fuzzbucket/2008/04/12/proxying-icecast-through-apache2-another-mini-howto/](http://blogs.linux.ie/fuzzbucket/2008/04/12/proxying-icecast-through-apache2-another-mini-howto/)

---

### Post by Lars Noodén on 2009-10-01
> **wlraider70 said:**
> across the internet, but out of curiosity what would the difference be?


Not a lot, mostly one of bandwidth and delay but also more attention must then be paid to access control across the Internet.

---

