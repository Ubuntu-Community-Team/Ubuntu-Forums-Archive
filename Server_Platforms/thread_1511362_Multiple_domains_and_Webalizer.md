---
title: "Multiple domains and Webalizer"
date: 2010-06-16
forum: Server Platforms
---

### Post by BigTraz on 2010-06-16
Hello everyone.

Can someone guide me on how to install webalizer and configure it to push stats for multiple domains? Much appreciated.

:confused:

---

### Post by hictio on 2010-06-16
I don't have that much experience with Webalizer under Ubuntu, but basically what you have to do is using a Webalizer configuration file for each one of the domain(s) that you want to graph usage.
Of course, inside of any of those configuration files there is the path to the Apache log file, which is already setup to log in separately files for each one of the domains you want to graph.

---

### Post by BigTraz on 2010-06-16
Is there a thread that has been posted somewhere I can refer to? I need to get this going. Thanks and bump for the night crowd.

---

### Post by BigTraz on 2010-06-19
Bump for the weekend. Cmon guys. Im sure I'm not alone on this. Post a tutorial or a link to something that explains how to do this.

---

### Post by hictio on 2010-06-19
Check [Tips and tricks: How can I use webalizer to process the logs of multiple virtual hosts?](http://magazine.redhat.com/2007/09/24/tips-and-tricks-how-can-i-use-webalizer-to-process-the-logs-of-multiple-virtual-hosts/)
(It is not Ubuntu Server, but it'll give a head start, maybe)

---

### Post by BigTraz on 2010-06-20
Thanks guys. I'll look into this and post on what I come up with.

---

### Post by BigTraz on 2010-06-21
> **hictio said:**
> Check [Tips and tricks: How can I use webalizer to process the logs of multiple virtual hosts?](http://magazine.redhat.com/2007/09/24/tips-and-tricks-how-can-i-use-webalizer-to-process-the-logs-of-multiple-virtual-hosts/)
(It is not Ubuntu Server, but it'll give a head start, maybe)

Thank you very much Hictio. This was very helpful.

---

