---
title: "ddclient problem"
date: 2006-10-27
forum: Server Platforms
---

### Post by Jeeevs2001 on 2006-10-27
Hi, 

I am having trouble using ddclient. I have been through the setup steps and the config file and thought I had set it all up correctly however when trying to start it I get the following message: 

dynamic DNS service update utility not in use

Does this mean the service is not running? 

Would be great to hear from anyone who has solved this problem!

---

### Post by Randy R on 2006-12-20
I have the same problem. Any one have a solution?

---

### Post by chrisfay on 2006-12-20
Is the daemon actually running?

```
ps aux | grep ddclient
```

---

### Post by Jeeevs2001 on 2006-12-30
It is running, however I have to start it manually each time I restart the computer, despite trying to make it run automaticaly. 

Is there an (easy) way to set it up to run automaticaly? 

Thanks

---

### Post by claypole on 2007-01-19
I had the same problem, after exiting the config screen when it was first installed.  Go into Synaptic and completely remove ddclient and then re-install (just removing and reinstalling won't work).  Be sure to answer all the questions on install and it should start fine.

---

