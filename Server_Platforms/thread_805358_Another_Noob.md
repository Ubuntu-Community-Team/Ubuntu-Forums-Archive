---
title: "Another Noob ?"
date: 2008-05-23
forum: Server Platforms
---

### Post by ItsGambit on 2008-05-23
I have now setup my Ubuntu 8.0 LAMP Server with ISPconfig ... but now I am lost on making a site. I go to my server ip address and I see "It Works" so I know all is fine. Even ISPconfig says all is online. I have also installed phpmyadmin... if that helps. 

Any help will be great.. 

- ItsGambit.

---

### Post by Phoenixzeus on 2008-05-24
What exactly are you lost on, like do you need help making the HTML files or on the layout or on where to actually save the files on LAMP?

---

### Post by Phoenixzeus on 2008-05-24
Sorry to double-post but,
First, you have to route the HTTP port on your modem/router to pass it on to your internet IP address of your LAMP server. Also from memory I'm pretty sure the default location to place your webpage is:
/var/www/
In there you will find the "It Works!" index.dat file.
However most people prefer to change is default folder and point it elsewhere.

---

### Post by ItsGambit on 2008-05-28
Well it was showing it works! and then I added the port forwarding to the router so any http request would go to my server xxx.xxx.xxx.22 and it does that but is show the page that says "Shared IP" I only want to host one site and I have made a client and site inside of ISPconfig.

---

