---
title: "Looking forweb based Remote support"
date: 2008-02-29
forum: The Cafe
---

### Post by PhishHead4:20 on 2008-02-29
I'm looking for a web based on-demand remote support application. something similar to logmein rescue, gotoassist,etc.  i would like to host it myself.  

I've been search for a while, but can't seem to find the right program..

Any help would be appreciated.

---

### Post by NullHead on 2008-02-29
like openssh? or realVNC?

---

### Post by PhishHead4:20 on 2008-02-29
not really, let me explain.  I want to host a web based support app. eg. a user goes to a website, installs a small package/active x, and i can take remote control of their desktop from a web browser.

i'm mostly looking to support windows, as that's what most of my clients run, but i would like app to be open source, and would like to run it on linux, specifically ubuntu server. Not even sure everything i'm looking for is possible.

I've found products, but the cost is a bit high. logmein rescue is a perfect example of what i'm looking or, but also very expensive.

---

### Post by NullHead on 2008-02-29
I think this is possible with RealVNC or remote desktop protocol. 

Windows has this remote desktop  pre-installed so you'll need to explain how to enable this and than you'll have to explain how to get it through the router.

Other than that I'm out of ideas ... 

Are you thinking of what Dell is doing with it's technical support?

---

### Post by ryanhaigh on 2008-02-29
Perhaps your app could create a virtual connection between the client and your system, something like openvpn/hamachi (at least I think this is what they do), you could host the server on you linux system, then you could use RDP or vnc, you wouldn't need a web based app, but VNC includes a java based http accessible server. You would need to bundle these apps and make sure the installer does any required config, maybe include a connectivity test incase a firewall is interfering (not sure how windows software firewalls handle hamachi etc).

---

