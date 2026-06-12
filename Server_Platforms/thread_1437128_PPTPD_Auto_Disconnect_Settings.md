---
title: "PPTPD Auto Disconnect Settings"
date: 2010-03-23
forum: Server Platforms
---

### Post by dfxdeimos on 2010-03-23
---

---

### Post by dfxdeimos on 2010-03-24
---

---

### Post by KB1JWQ on 2010-03-24
Not quite something I've dealt with before but is there some kind of keepalive option?  See the man pages for more.

You could always set up a ping stream across the pptp tunnel to keep the system up...

---

### Post by dfxdeimos on 2010-03-24
---

---

### Post by KB1JWQ on 2010-03-24
Add this to your config: 
lcp-echo-interval 30
lcp-echo-failure 4

---

### Post by dfxdeimos on 2010-03-24
---

---

### Post by KB1JWQ on 2010-03-24
No, and the former.  Respectively. :-)

---

### Post by dfxdeimos on 2010-03-24
---

---

### Post by KB1JWQ on 2010-03-24
Heh, try it and see! Worst case you learn something.  

Do not use the -timeout option.

Add the two configuration options I gave you to /etc/pptpd.conf

---

### Post by dfxdeimos on 2010-04-02
---

---

### Post by KB1JWQ on 2010-04-02
sudo is your friend.

---

### Post by dfxdeimos on 2010-04-02
---

---

### Post by dfxdeimos on 2010-04-02
---

---

