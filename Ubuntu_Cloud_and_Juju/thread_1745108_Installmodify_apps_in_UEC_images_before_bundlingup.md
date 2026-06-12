---
title: "Install/modify apps in UEC images before bundling/upload"
date: 2011-04-30
forum: Ubuntu Cloud and Juju
---

### Post by j.c.rush on 2011-04-30
[http://uec-images.ubuntu.com/releases/](http://uec-images.ubuntu.com/releases/)

I would like to install some applications in the UEC images before bundling and uploading them to the UEC Cloud.

For example:

installing java, vnc, codeblocks, etc. on "lucid-server-uec-amd64.img" which is in "ubuntu-10.04-server-uec-amd64.tar.gz" from "http://uec-images.ubuntu.com/releases/"

Thank you for your help and support :) :) :)

---

### Post by j.c.rush on 2011-04-30
Here is what I found as a resource to all future requests to modify a base image.

[http://open.eucalyptus.com/participate/wiki/modifying-prepackaged-image/](http://open.eucalyptus.com/participate/wiki/modifying-prepackaged-image/)

---

### Post by kim0 on 2011-05-03
An alternate approach to rebundling images with your changes, is to use cloud-init or similar to dynamically configure an instance as it boots. This is the way I prefer. You can read more about cloud-init at [https://help.ubuntu.com/community/CloudInit](https://help.ubuntu.com/community/CloudInit)
Also
[http://www.youtube.com/watch?v=-zL3BdbKyGY](http://www.youtube.com/watch?v=-zL3BdbKyGY)
Enjoy :)

---

