---
title: "Webmin you need a bloody degree to use it"
date: 2008-05-12
forum: Server Platforms
---

### Post by ade234uk on 2008-05-12
We are moving away from our current hosts to a dedicated server. This server has webmin on it and I dont have a bloody clue how to use it and where to start.

1) This webmin looks like a CP to admin a complete server am I correct?

2) Ok lets say I want to host the site [www.ilovewebmin.co.uk](www.ilovewebmin.co.uk) on it, how do I go about setting up an account?

3) After this how do I go about setting up an email address say [email]help@ilovewebmin.co.uk[/email]

Looking at forums people rate this highly, but the only control panels I have used are cpanel and one provided by the hosts themself. Am I being thick, or is webmin reserved for experts?

---

### Post by MarkHowells on 2008-05-13
> **ade234uk said:**
> We are moving away from our current hosts to a dedicated server. This server has webmin on it and I dont have a bloody clue how to use it and where to start.

You're probably not going to like this, but I'd _seriously_ suggest you invest some time to learn about the underlying applications and and a more manual configuration (normally by editing the configuration files directly).  There are a number of reasons for this
[LIST]
[*]Knowledge. Running your own dedicated server is like deciding to maintain your own car. You're going to need knowledge of how the system works and how to do routine maintenance and fix errors / faults.
[*]Tools like webmin generally only make a subset of features available. If you want to build the best system you may need access to features unknown to/unsupported by the webmin panel creator.
[*]If you're running your own server ("dedicated server") then you are likely to be responsible for all security on that server. This may mean being able to respond very rapidly to security notices. You don't want to be waiting for the webmin authors...
[*]Webmin you need a bloody degree to use it ... ;)
[/LIST]
I'd recommend running a local test box to play with /learn before attempting to run a production server too.

Edit: Having looked at you profile since posting I suspect that you may be already knowledgeable about Linux. Sorry if the above treats you a bit beginner-ish...

---

### Post by Dr Small on 2008-05-13
I started using Webmin at 16. (by the way, that means I don't have a degree :D )
Webmin is much simpler than editing every configuration file from the command line in a dark room in a black terminal. Trust me :)

It just takes some getting used to, but most all your system settings should be in the Webmin menus. Browse around, learn the atmosphere, and become a professional at it.

Dr Small

---

### Post by hyper_ch on 2008-05-13
webmin is overkill for just hosting a website...

---

### Post by whitey on 2008-05-13
I'm more a fan of using the command line for this type of administration, but I've had to teach a few people to use webmin from time to time.  What you are looking for is to click on the following path:

Servers>Apache Webserver

In this area you will see a list of your Virtual Hosts from the httpd.conf or the apache.conf depending on how you have it setup.  Look at the tabs at the top, in grey you should have one that says [Create New Virtual Host].

At this point you just punch in your information in, list the document root (which you can also create in webmin using the file manager in the Others section), list the IP address you want it to listen on, and your are good to go.

Keep in mind that if you want to add aliases you will have to do that later, by going back into the Apache Webserver area and and clicking on the particular virtual host.

After all is said and done, you will want to find the button that says [Apply Changes], this will restart the apache webserver for you and load your new changes in.

Have Fun at it,
~whitey  :mrgreen:

---

### Post by Thirtysixway on 2008-05-13
Yes it is true that you should learn how to configure applications via text editor, but sometimes a gui can make it a bit easier and faster.  I know people who have had to get dedicated servers for their web applications, but they didn't know how to configure apache settings.  webmin is okay in some situations.

---

