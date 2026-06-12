---
title: "Apache serves outside, but no localhost"
date: 2008-10-13
forum: Server Platforms
---

### Post by meadmarc on 2008-10-13
Hi...  In the most bizzare thing I have ever seen, my Ubuntu Moodle server is serving pages to the outside world, but whenever I try to access [http://localhost](http://localhost), [http://127.0.0.1](http://127.0.0.1), or the actual url [http://kas-moodle.kingsley.k12.mi.us](http://kas-moodle.kingsley.k12.mi.us) from the server itself, it will not display the page.

How can apache be serving moodle to the outside world but not to the machine it is operating on?  

I am concerned that there may be something severely messed up in there.

Thanks in advance,

Marcus

---

### Post by lykwydchykyn on 2008-10-13
Can you post your virtual host configuration file and the output of:
```

sudo netstat -tunap 

```

---

### Post by meadmarc on 2008-10-14
It would seem that one of the network guys at the school changed the IP address of our local DNS server without telling me.  I put in the new IP, and it's like butter.

Thanks for the idea, and I will have to put that command in my little ubuntu 3-ring binder of possible solutions.

Thanks!

---

