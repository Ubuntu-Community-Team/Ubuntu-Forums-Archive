---
title: "Sharing a bzr branch with another person"
date: 2007-12-08
forum: Server Platforms
---

### Post by Ces on 2007-12-08
Basically, I know very little about servers.

The context:
• Me and a friend are writing our master’s thesis, and need to collaborate
• We have sat up a local working copy of a bzr repository, works gallantly
• I have a laptop with which I connect to the internet from a variety of places (ip:s)

What we want:
• Publish our bzr branch so we can work together (I guess one of us have to set up a server of some kind)
• Lets say I’m the one to put up the server, is there some easy way to do it? (Only my friend needs to connect, and then only to check in commits to the bzr branch.)

Yes, we are aware that my friend would only be able to connect when I’m online, and that I would need to share my current ip every single time, or however that works.

We cannot use any public services until the thesis is published (under a Creative Commons license), due to confidentiality reasons.

Thanks. :D

---

### Post by freebeer on 2007-12-09
Have you considered a dynamic dns service such as offered by DynDNS.com?  You can run a script that monitors your IP address, then updates DynDNS' address for you.

So basically, when you're online, the script tells DynDNS your new IP address and your collaborator needs only use your URL to access it (such as [www.yourdynamicname.org](www.yourdynamicname.org)).

There MAY be a lag between when the script makes the the IP change and when access is available, but in my experience it's almost instantaneous.

---

### Post by Ces on 2007-12-10
Thanks, freebeer! That really solves one problem. :)

---

### Post by freebeer on 2007-12-10
Glad that I could be of some help.  If you need some help setting it up, let me know... been there, done that.  :D

---

