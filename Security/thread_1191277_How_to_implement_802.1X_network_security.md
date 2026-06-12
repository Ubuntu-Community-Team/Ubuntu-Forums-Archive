---
title: "How to implement 802.1X network security?"
date: 2009-06-18
forum: Security
---

### Post by The Question on 2009-06-18
If possible, I would like to put 802.1x security on my network.  More security is better than less, so I figured why not try.

First, what do the various authentications mean--TLS, Tunneled TLS, PEAP?

Then I am supposed to find a user certificate, CA certificate and a Private Key somewhere on my system, but I have none of these files.  How to create them or get them?

---

### Post by Dave_Connor on 2009-06-19
For wireless connections, run WPA-PSK instead of WEP, WEP can be broken as quick as 10 minutes due to its flaws with its encryption. Also run services that don't provide encryption over ssh (like browsing within FF).

---

### Post by The Question on 2009-06-21
This is for a wired network.

---

### Post by rookcifer on 2009-06-21
> **The Question said:**
> This is for a wired network.

What, specifically, are you trying to do?

---

### Post by SunRhythms on 2011-04-12
These might help

[http://networking.grok.lsu.edu/Article.aspx?articleId=14968](http://networking.grok.lsu.edu/Article.aspx?articleId=14968)
[http://www.sans.org/reading_room/whitepapers/firewalls/wired-8021x-security_1654](http://www.sans.org/reading_room/whitepapers/firewalls/wired-8021x-security_1654)
[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)
[https://help.ubuntu.com/community/Network802.1xAuthentication](https://help.ubuntu.com/community/Network802.1xAuthentication)
[http://answers.yahoo.com/question/index?qid=20081011234342AAlAqF0](http://answers.yahoo.com/question/index?qid=20081011234342AAlAqF0)

---

### Post by imac_89 on 2011-04-12
Hold on, you want to run a 802.1X authentication server on your home network?

---

### Post by SeijiSensei on 2011-04-13
Check the dates, please.  The OP was asked a question in 2009 and never replied.  I doubt he or she will be paying attention two years later.

---

### Post by uRock on 2011-04-13
Necromancy

Thread Closed

---

