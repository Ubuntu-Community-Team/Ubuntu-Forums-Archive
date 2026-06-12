---
title: "Ubuntu Snort 2.8"
date: 2009-02-16
forum: Security
---

### Post by madnak on 2009-02-16
Hi,
I am looking into a roll out an IDS system based on Snort (latest version possible) on a large scale (about 25+ sensors) and would like to know if there is any stability (and/or security) issues with snort 2.8.* on Ubuntu and why are the versions in the Ubuntu package system still snort 2.7? [http://packages.ubuntu.com/search?keywords=snort&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=snort&searchon=names&suite=all&section=all)

I've tried snort 2.8.3.2 from source and came into a problem like the one in this thread below. I managed to fix the problem but I'm a bit concerned about it. 
[http://ubuntuforums.org/showpost.php?p=6180774&postcount=25](http://ubuntuforums.org/showpost.php?p=6180774&postcount=25)

Any information would be appreciated.

---

### Post by bodhi.zazen on 2009-02-16
When installing security applications, IMO, you are always best off compiling the latest version from source and not relying on the package managers to keep them up to date.

Snort is easy to compile from source and easy to update. I just updated to the latest snort version and rules recently and had no issues.

When compiling from source, however, you may run into some errors you will have to debug. While this is difficult at first, with time it gets easier.

---

### Post by madnak on 2009-02-16
Thank You bodhi for your reply.

I was leaning more to the source package, I used the pre-packaged version at home when messing about with it (just being lazy :) )

---

### Post by bodhi.zazen on 2009-02-16
One last comment :

25 sensors is huge :)

Unless you have a large network or need to monitor multiple points it is *probably* easier to look at a "smart switch". A smart switch will give you a monitoring port so you can monitor all you traffic going through the switch with one sensor, then keep the sensor isolated from the network.

In the long run it is almost certainly more cost effective to look a such a smart switch.

although "industrial strength" switches cost $$$$ you can get a "smart switch" with a monitoring port for $

---

### Post by madnak on 2009-02-16
Maybe 25 is a bit many but it's still a fair few. It would be set up on SPAN (mirror ports) on some old Cisco switches in a lab. My set up is a special setup with lots of small networks for a project.

But thanks that's all I really wanted to know.

---

