---
title: "how can I hide :8080 on url?"
date: 2009-06-09
forum: Server Platforms
---

### Post by kustomjs on 2009-06-09
Hi Guys
I just wanted to know how can I hide port number :8080 onto a url?

say mail server is on port 8080 (different server) and webserver is on port 80 I want to be able to hide port 8080 if possible.

---

### Post by windependence on 2009-06-09
If your domain registrar supports cloaking, you can do it in their DNS control panel. Otherwise, you could use a service like no-ip and cloak it there. You don't need to be running a dynamic IP to do that and I am pretty sure they will do that with a free account. Keep in mind though, that there will be people who can't view your site because some filtering software will deny access to a redirected site. Most people don't realize that the majority of web traffic is from people surfing at the place of employment which is where the bocking most aften takes place. I learned the hard way years ago, this is why I don't advocate running a production site without a static IP, or from another port.

-Tim

---

### Post by LepeKaname on 2009-06-09
You can use the proxy or url_rewrite modules of apache.

---

