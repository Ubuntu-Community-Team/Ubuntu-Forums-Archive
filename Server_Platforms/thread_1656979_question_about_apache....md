---
title: "question about apache..."
date: 2010-12-31
forum: Server Platforms
---

### Post by jrbjr5 on 2010-12-31
If I run the command

sudo /etc/init.d/gdm restart

will it affect apache?


In other words.... if someone is downloading a file over http off of my server and I restart my gnome session, will it interrupt their download?  Thanks for your help!

---

### Post by wojox on 2010-12-31
It should just restart x-server. I don't know for certain. Maybe that's why it came without a GUI. :p

---

### Post by CharlesA on 2010-12-31
Should work fine. I haven't restarted gmd while running Apache, but they are different services soo..

---

### Post by t4thfavor on 2010-12-31
Well you can run apache on a server without GDM installed, so I would imagine that you could...

Do it, and post back your results, I am betting apache doesn't even notice.

---

### Post by jrbjr5 on 2010-12-31
I knew I would catch a little flack for using a gui  :)

I tested the question out and apache was unaffected.  Thank you all for your help!

---

### Post by t4thfavor on 2010-12-31
I knew the answer, I just like seeing threads solved... It really helps when you have a question, you actually get the answer in writing so that when someone else has a similar question when they google it they find an answer :)

---

