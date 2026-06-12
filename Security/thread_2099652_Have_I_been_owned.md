---
title: "Have I been owned?"
date: 2012-12-30
forum: Security
---

### Post by jsvidyad on 2012-12-30
Hello,

 I just read the following wiki about ubuntu security: [https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned). That got me thinking about a post I made earlier : [http://ubuntuforums.org/showthread.php?t=1830859](http://ubuntuforums.org/showthread.php?t=1830859) . At that time, I had posted a copy of my syslog file and then deleted it because I was under the impression that it was not safe to post it. What do you think? Do you think there is some reason for me to get worried?

---

### Post by Ms. Daisy on 2012-12-30
Worried about what? That you posted your syslog for a few minutes?  

Or are you worried about the contents of the syslog?  Dangertux already gave you his two cents in your previous thread.

---

### Post by jsvidyad on 2013-01-04
Hello Ms. Daisy,

   I recently read that ubuntu wiki article by you(the one I referred to in the first post) mentioning that suspicious time stamps in the syslog file could be an indication of a intruder break in. That reminded me about that earlier incident I reported in that earlier thread(which happened over an year ago). And that got me worried. That's why I started this thread. Now, it's true that I got that reply from Dangertux. But, I am not sure if he made that reply before I deleted the syslog file I attached and therefore if he got a chance to look at the contents of that file. I would have attached that file to this post if I had not been worried that someone could get access to my system through the contents of that file. So, I am not sure if I need to get someone else to have a look at that file and if yes, how to do it securely.

---

### Post by cariboo on 2013-01-04
You can post your syslog output, without a problem, if you do a search and replace of your external ip address, any thing in the 192.168.xx.xx and 10.0.xx.xx net blocks are non-routeable (can't be accessed from the internet), if you are behind a router that uses NAT.

---

### Post by Ms. Daisy on 2013-01-04
FWIW the wiki isn't "by" me, I was just one of many contributors.

---

### Post by jsvidyad on 2013-01-25
> **cariboo907 said:**
> You can post your syslog output, without a problem, if you do a search and replace of your external ip address, any thing in the 192.168.xx.xx and 10.0.xx.xx net blocks are non-routeable (can't be accessed from the internet), if you are behind a router that uses NAT.

Unfortunately, my computer is not behind a router and therefore that file shows its external ip address. Is it still safe to show that file?

---

### Post by Ms. Daisy on 2013-01-25
Just mask the last two octets in the IP address, something like this: 204.58.x.x

---

