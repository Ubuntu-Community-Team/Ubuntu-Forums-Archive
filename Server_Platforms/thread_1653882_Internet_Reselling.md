---
title: "Internet Reselling"
date: 2010-12-27
forum: Server Platforms
---

### Post by minigilani on 2010-12-27
Hello, i sorta need help with this project i decided to start. All i need is a helpful push in the right direction, as in, stuff i should know about to start it up, i really want to learn stuff along as i do this.

Here's a scenario; students living at a hostel are offered internet at various packages. Basically, what i'm trying to do, is equally divide the bandwidth of a DSL connection to students, but that's just the beginning.
.
To keep track of which student paid for their connection, and which package they're on, i'll assign each student a login ID. Only the login ID's that have been paid for, will be allowed to access the internet.
.
Say a computer logs onto the network and tries to open a website, it's served with a login page, only if the login is successful, is it allowed to go online. After the login is successful, the package type has to be determined.
.
Package types will probably depend on timings, certain users will be allowed online at certain times. If they log on at a time not specified in their package, they'll be charged for data consumption.

**Note:** I know this is a long thing, and i'm willing to work on it, i have about a month to get this thing in workable condition, and i'm ready to learn stuff if i need to. I don't have much experience with Web Dev apart from a little HTML/CSS, but i understand a bit about how PHP works, and i understand the login page will need to work on PHP with a MySQL backend, i can learn that, it's the rest of the things i'm confused about.

Thanks in advance.
minigilani

---

### Post by cariboo on 2010-12-27
Have a look at [ISPConfig3]("http://www.ispconfig.org"), it may be a bit more than what you need. If you decide to try it, follow the directions [here]("http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3").

---

### Post by minigilani on 2010-12-27
Hey, thanks for the reply.

I did find ISPConfig3, infact, i almost bought the manual! But then, i read the following [here]("http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-3"):
> This tutorial shows how to prepare an Ubuntu 10.10 (Maverick Meerkat) server for the installation of ISPConfig 3, and how to install ISPConfig 3. **ISPConfig 3 is a webhosting control panel** that allows you to configure the following services through a web browser: Apache web server, Postfix mail server, MySQL, BIND or MyDNS nameserver, PureFTPd, SpamAssassin, ClamAV, and many more.

So, naturally, i concluded that ISPConfig was for Web Hosts. Will it be able to do all that i need it to do? And should i pony up the 5 EUR for the manual? (5 EUR = 564 in my currency)

**Update:** installed ISPConfig3 on Ubuntu 10.10 (Maverick Meerkat).. now what? As in i'm staring at the webpanel.

---

### Post by HugoSerrano on 2010-12-28
I don't know ISPConfig3 very well, but I think that it's for webhosting...

What you may look for is something with a Captive Portal. 
Search for Untangle, pfSense, Zentyal. There are more solutions.

---

### Post by doogy2004 on 2010-12-29
> **minigilani said:**
> Say a computer logs onto the network and tries to open a website, it's served with a login page, only if the login is successful, is it allowed to go online. After the login is successful, the package type has to be determined.

sounds like a job for a RADIUS server.

---

### Post by James78 on 2010-12-29
I've seen and used ISPConfig 3. I didn't like it, it had way too little features. I use Webmin and Virtualmin now, which by far is one of the best I have ever seen. It has tons of features, which will allow you to get whatever type of reselling too people. You should check it out. ;)

---

### Post by Justin_Ferrell on 2010-12-29
Hey I would check this out.
[http://www.chillispot.info/](http://www.chillispot.info/)
I know some people that have used this to do exactly what you are talking about. Throw a untangle proxy in the mix to to have a great all around system

---

### Post by James78 on 2010-12-29
Hmm, ya, Chillispot is a pretty good solution for that too.

---

### Post by HermanAB on 2010-12-30
What you want is a RADIUS authentication system with a walled garden / captive portal as suggested above.

For example, you can hook RADIUS authentication to the Squidcache proxy server, so that only paying users can access the web, like at an Airport or Hotel:

[http://www.aeronetworks.ca/howtos/radius.html](http://www.aeronetworks.ca/howtos/radius.html)
[http://www.aeronetworks.ca/howtos/prepaid.html](http://www.aeronetworks.ca/howtos/prepaid.html)

---

### Post by Justin_Ferrell on 2010-12-30
Something to think about as well. Since these are students, Im sure illegal torrenting will be in the mix. Might want some MIME type filtering as well. Also, it will help with your bandwidth issues....

---

