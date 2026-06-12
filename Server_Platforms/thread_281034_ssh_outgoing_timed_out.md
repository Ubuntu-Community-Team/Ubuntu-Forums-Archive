---
title: "ssh outgoing: timed out"
date: 2006-10-20
forum: Server Platforms
---

### Post by Curtis_B on 2006-10-20
I originally posted this thread because my ssh connection (from the ubuntu server to internet) attempts were failing. I'm starting to think the problem is an overall outgoing/connectivity problem. In aptitude, when I try to check for new packages, my system fails to connect to any of the FTPs. 

Ping, I really don't understand ping. ping [www.google.com](www.google.com) will give me a line every 2 seconds, which appears to confirm that I received a response in ~80ms, but it NEVER ENDS. I'm assuming this result means that I atleast have some internet connectivity, if I didn't get a reponse then I'm assuming ping would just hang for a while and give me a time out response.

Just to clarify, upon installation I was able to download new packages through aptitude just fine. The only administrative changes I've made in the last month were modifying the groups of my user. I'm guessing that since I'm doing sudo aptitiude or sudo ssh that my user's groups are irrelevant. 

On the lan, it's serving LAMP properly.

I'll admit it, I'm a newb and I don't know where to go from here other than a fresh install, which I really don't want to do. 

thanks

Curt

---

