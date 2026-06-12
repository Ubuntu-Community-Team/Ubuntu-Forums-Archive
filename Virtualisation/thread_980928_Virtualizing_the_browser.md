---
title: "Virtualizing the browser"
date: 2008-11-13
forum: Virtualisation
---

### Post by liveandletlive on 2008-11-13
Here is my requirement.

I would like target set of users (from anywhere in the world) access internet such that when they do, they get my IP. One way of doing that in windows is to let them login to a terminal services session that I host on our servers. That way when they open a browser in that session and go to the internet, they are using my IP address. 

I know we can do it using X-Session. However, I have had little success with it so far. Also, I dont necessarily need them to have access to the entire X Session, just the browser.

I tried using Xming and NoMachine without much success. 

Can someone pls guide me how to do it?

If I am in the wrong thread, please let me know.

Thanks

---

### Post by anthro398 on 2008-11-28
[CGI Proxy]("http://www.jmarshall.com/tools/cgiproxy/") has worked well for me.  It fulfills your requirement (users get your IP address while using a web browser) but is much, much lighter weight than the approaches you've tried.  I've also used danted SOCKS 5 proxy and had great success with it.  You'd run either of these on your machine and point users to it.

---

