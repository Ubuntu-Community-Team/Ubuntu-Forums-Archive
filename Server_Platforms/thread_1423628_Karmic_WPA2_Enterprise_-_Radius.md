---
title: "Karmic WPA2 Enterprise - Radius"
date: 2010-03-06
forum: Server Platforms
---

### Post by mastermindg on 2010-03-06
I'm running KK 9.10 with x86_64 Desktop version on my desktop computer that is WIRED to my router. I'd like to implement WPA2 Enterprise with AES for wireless clients. My router is a Linksys WRT160N. WP2 Enterprise mode is requesting the Radius server IP and port along with the Shared Secret.....

I used the following guide to setup FreeRadius on my system:

[http://blog.csatpk.com/2010/03/installing-and-configuring-freeradius-with-mysql-authentication/]("http://blog.csatpk.com/2010/03/installing-and-configuring-freeradius-with-mysql-authentication/")

I've got FreeRadius installed and configured to run off of my MySQL database. I had to use 127.0.0.1 with radtest, but everything is working fine at this point. I am able to login to my radius server with a user account via password authentication.

Now that I've got Radius operational...How do I setup Host key encryption to work with Radius so that I can authenticate to my router?

There's a guide on the forums but it's from 2006 and FreeRadius has changed a little in 4 years ;)

---

### Post by adalal on 2010-03-22
I tried using that, but I never get the "rad_recv: Access-Accept packet...", and that it keeps sending itself Access-Request packets...

---

