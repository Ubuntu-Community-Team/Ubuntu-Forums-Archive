---
title: "Loopback issues?"
date: 2010-04-02
forum: Server Platforms
---

### Post by TooManyGames on 2010-04-02
Lemme first say, I don't really know much about Linux in general, I'm just trying to help my boss out with the website for his business.

I have LAMP installed with Ubuntu 9.10 desktop edition (boss wants a GUI, so that's the version he installed).  If you visit our website ([www.challengearcade.com](www.challengearcade.com)) everything resolves normally (straight HTML).

Now, I'm working on installing WordPress so we can make easy update to the site from anywhere.  When visiting the site from outside our local network ([www.challengearcade.com/wordpress/](www.challengearcade.com/wordpress/)) everything renders fine, I can log into the back end of WordPress and update and all that good stuff.  When I attempt to log in using the IP of the machine on the local network (10.1.10.35/wordpress or localhost/wordpress) I get the blog but none of the CSS is rendering.  If I attempt to log into the backend of the site while on the local network (10.1.10.35/wordpress/wp-admin/ or localhost/wordpress/wp-admin) I get:

Access Error: Page not found

when trying to obtain /wordpress/wp-login.php?redirect_to=http%3A%2F%2F10.1.10.35%2Fwordpress%2Fwp-admin%2F
Cannot open URL /wordpress/wp-login.php?redirect_to=http%3A%2F%2F10.1.10.35%2Fwordpress%2Fwp-admin%2F

I don't know if I'm having problems with WordPress and that's where my questions should be asked, or if this is more of an Apache problem, or an Ubuntu configuration problem, or what.  Can anyone help?  8*)

---

### Post by HermanAB on 2010-04-03
Sounds like DNS and default path problems in Apache.

---

