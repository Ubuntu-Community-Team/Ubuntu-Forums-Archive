---
title: "How to backup twiki data?"
date: 2007-10-17
forum: Server Platforms
---

### Post by dazuixie on 2007-10-17
Dear all,

I installed twiki4 in Ubuntu 7.04. This is the first time for me to install wiki. Does anyone can tell me how to back up the data and which folder to intall plugin?
By the way, I install the default version of twiki, using apt-get install twiki.

Thanks in advance :-)

---

### Post by Cato2 on 2007-10-23
You just need to back up the 'data' and 'pub' folders under the /var/lib/twiki directory, which is TWiki's 'home'.  'data' has the topics, 'pub' has the attachments and images.

If you haven't seen it already, check out the [TWiki on Ubuntu HOWTO]("http://twiki.org/cgi-bin/view/Codev/TWikiOnUbuntu") page at TWiki.org - now updated for Ubuntu Gutsy.  Let me know any comments, I wrote it recently and would like some feedback!

Also, have a look at the [http://twiki.org](http://twiki.org) site and click into the Support web on left hand side - this is the best place to get TWiki questions answered, since the TWiki admin and developer community hang out there.  There's also an active IRC channel linked there.

---

