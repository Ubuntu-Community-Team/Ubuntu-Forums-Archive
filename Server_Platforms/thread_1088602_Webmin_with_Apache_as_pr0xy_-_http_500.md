---
title: "Webmin with Apache as pr0xy - http 500"
date: 2009-03-06
forum: Server Platforms
---

### Post by threetimes on 2009-03-06
**Short story:**
Look [here](https://webmin.peter-server.homelinux.net/) or [here](http://web-sniffer.net/?url=https%3A%2F%2Fwebmin.peter-server.homelinux.net%2F&amp;submit=Submit&amp;http=1.1&amp;gzip=yes&amp;type=GET&amp;uak=0).

**Long story:**
I installed webmin, but from inside school, I can't acces anything an any port but 80. So I use my main Apache installation as a pr0xy for anything else. With ajaxterm, it works. With webmin I get a HTTP 500 (see links above).

See my [httpd.conf](http://pastebin.com/f179b5fda).

As you can see, I used exactly the same trick as with ajaxterm, but webmin doesn't like it.
Why?

P.S. I can't use the word proxy in the title of this topic, because if I do that, I cant visit this page anymore. That's why I had to post this 2 times again...
Blame my school for this.

---

### Post by threetimes on 2009-03-06
**The good news:**
If you just go [here]("https://peter-server.homelinux.net:10000/"), it works. So webmin itself doesn't seem to be the problem.

---

### Post by drubin on 2009-03-06
> **threetimes said:**
> **The good news:**
If you just go [here]("https://peter-server.homelinux.net:10000/"), it works. So webmin itself doesn't seem to be the problem.
> 
Firefox can't establish a connection to the server at peter-server.homelinux.net:10000.

are you sure you have port 10000 forwarded on your router?

If you do are you sure you school isn't blocking that port 10000?

---

### Post by threetimes on 2009-03-06
> **drubin said:**
> .

are you sure you have port 10000 forwarded on your router?

If you do are you sure you school isn't blocking that port 10000?
i removed webmin 'cause i don't like it

---

