---
title: "Personal Sockso Server and Ubuntu 9.10"
date: 2010-01-25
forum: Security
---

### Post by cosmicsteve on 2010-01-25
I am not sure whether this is the correct spot for this, but I would like to set up my a personal music server so that I can listen to my personal music collection at work. I had been using Sockso to do this, and it worked very well until I updated to the latest version of Ubuntu 9.10. 

It seems as though this upgrade has now made all of the outside access to my music impossible, even though I know that Sockso is working (I can see the website by typing 127.0.etc and I did have it working before so I know it is not a router issue)

Is there anything I should be doing in terms of the Ubuntu security to make sure this works, or do I need to start making some sort of more elaborate server than simply Sockso?

Thanks for your help.

---

### Post by cariboo on 2010-01-25
I just installed sockso to try it out, I'm running karmic on this system. There are a couple things to check, if you are behind a router, make sure you have it port forwarded, to port 4444. To check, you can go to [canyouseeme]("http://canyouseeme.org"), and make sure the port is open. 

If you have another computer on your home network, try it from there:

```
http://192.168.1.215:4444
```

Substitute your servers ip address for the one in the example above.

---

