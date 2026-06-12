---
title: "Another person with a firewall server problem"
date: 2012-10-19
forum: Security
---

### Post by 0011235813 on 2012-10-19
Hello forum.
As one of the many things I do, I like to write fictitious novels in my spare time. However, some of my friends have requested copies- and revisions. Now, what I attempted to do was set up a content server with calibre and ask them to connect on that, so they could see my book, later revisions and download whichever format suits them. 

I configured calibre with the standard configuration running on port 8080. I realized that the listener therefore required incoming port 8080 to be open, so I ran:
```

sudo ufw allow 8080

```
All was working well. I was able to test the address on my other computers and it worked fine. However, they couldn't open the link- and I realized that my router probably has it's own NAT.

Thing is, it's one of those Virgin Media 'Homehub' thingies, so the router and the modem are one unit. I'm confused- how do I disable NAT? Or do I have to ask my ISP for a different router without the annoying firewall?

---

### Post by 0011235813 on 2012-10-19
I seem to have found a solution guys. Never mind. In any case, if any of you get similar problems, you have to type [http://192.168.0.1](http://192.168.0.1) in your address bar and enter the username and password on the back of your unit. You can change its settings from there.

---

