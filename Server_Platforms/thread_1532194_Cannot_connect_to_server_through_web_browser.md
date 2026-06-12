---
title: "Cannot connect to server through web browser"
date: 2010-07-16
forum: Server Platforms
---

### Post by theviking10 on 2010-07-16
Hello, I just set up my first server in my home with Ubuntu Server Edition, and I'm in the process of installing Jinzora on it. However, I cannot access the server through my web browser like I believe I should.

Is it not just "http://<hostname>"?


I am very much a server newbie, do I need to install another application to view my server in a web browser? I am able to connect through SSH just fine.

Any help would be appreciated.

---

### Post by timothy_tim on 2010-07-16
I have never used Jinzora, nor installed it.  But I have some general debugging advise.
You could check if your service is already running or not.  Try using "ps aux|grep jinzora".
Check if your web server is running correctly.  Use "links http://localhost/".
Check if your web server is accepting your connections to port 80 (default http port).  Execute the command form an other computer: "nmap -p 80 <hostname>".


Good luck!

---

### Post by theviking10 on 2010-07-17
Thank you for the advice! I learned that I need to use apache to view the server, and am now attempting to configure the default page to my liking. Do you know how one would access a file in the server from a browser?

---

### Post by kemra on 2010-07-17
I don't believe you can access a server from a browser in the way you are saying if I am understanding you correctly.

Although something that sounds like it should meet most of your requirements is Webmin, just install it on your server then you can access the Webmin console from a browser.

---

