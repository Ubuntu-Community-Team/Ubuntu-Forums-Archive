---
title: "Gutsy Server Beta- Postfix has no main.cf"
date: 2007-10-09
forum: Server Platforms
---

### Post by jimbojones on 2007-10-09
Hello, I was going to follow some tutorials to get a feel on how postfix works (looks fun) and one of the first things I run into is editing the main.cf file ......but I do not have one in my /etc/postfix directory, just a master.cf which I believe is not the same thing.  Is it normal to not have that file, like something you need to make by hand, or did my install not go well? :confused:
Ultimatly I am trying to collect mail for 2 different domain names that I have, but I have come to an abrupt halt.

Thanks

---

### Post by jimbojones on 2007-10-10
Ok, i see what happened. I removed postfix and reinstalled, now I see a message saying that postfix has not been setup, i need to cp main.cf.debian to the /etc/postfix directory.  I will try this and go from there.   Thanks

---

