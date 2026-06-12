---
title: "Little nudge needed."
date: 2005-12-19
forum: Server Platforms
---

### Post by x__dark on 2005-12-19
Okay, I just want to see if I can actually get my computer running as a small server.

So I installed Apache 2 via apt, as well as PHP4.

Where do I go from here? I'm not particuarlly interested in having a domain pointed to it or anything, just being able to get it viewable from the internet. How would I go about doing/checking this?

---

### Post by Ahriman on 2005-12-19
If you know your external IP address, and if your router is set up to allow connections on port 80 to computers behind it, try something like this:

(assuming 111.222.333.444 is your external IP)
[http://111.222.333.444/](http://111.222.333.444/)

(If you don't know your IP, visit [www.whatismyip.com](www.whatismyip.com))

Your web pages are stored in /var/www/

If you run a firewall as well, you'll have to allow incoming connections to your machine on port 80, too.

---

### Post by x__dark on 2005-12-19
thanks, i think i may have to set my router to allow connections on port 80.

---

