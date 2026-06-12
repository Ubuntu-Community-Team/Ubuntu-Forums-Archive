---
title: "Proxy Server Setup"
date: 2008-05-28
forum: Server Platforms
---

### Post by haryoh on 2008-05-28
Hello guys.
Please help, how can I do these things below?

1.) I want to setup a proxy server on my web server so that I can filter what my siblings and guests do online(Sites/IM they visit). I want to be able to redirect anything I don't want them to access to my proxy server and then resolve their request if successful or I don't want them to access the site.

Is there anyway I can accomplish this? How will accomplish it?

2.) One of my clients informed me about his employees misbehaviors in accessing bad/good sites. I want my same web server to serve as a proxy server where by I will redirect all employees access from his server to my proxy server then give them result.

---

### Post by bmathis on 2008-05-28
Here is a quick guide on Squid Proxy Server and DansGuardian Filter

[http://ubuntuforums.org/showthread.php?t=320733]("http://ubuntuforums.org/showthread.php?t=320733")

All you need to do is add IP tables to make your proxy transparent or make a change in their browser and youre good to go.

---

### Post by haryoh on 2008-05-29
Thanks Bmathis.

I've been reading your tutorial since morning at work and going through other things.
There is one thing I didn't mention in my post; I have a Linksys router. and in your tutorial and [another another squid tutorial]("http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html") I found which is basically like yours didn't cover anything like "if there is a linksys".

Please help.

---

### Post by haryoh on 2008-06-04
Is there any way I can keep track of the client IP address that request anything over my proxy server using the access.log?

---

### Post by haryoh on 2008-06-06
I was able to figure that out. thanks.

---

