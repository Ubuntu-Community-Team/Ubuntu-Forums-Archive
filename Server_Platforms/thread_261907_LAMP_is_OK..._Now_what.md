---
title: "LAMP is OK... Now what?"
date: 2006-09-20
forum: Server Platforms
---

### Post by bluevoodoo1 on 2006-09-20
Setting up a LAMP server was pretty easy. I even have Drupal.org's content management system running on my localhost. 

Now my question is... how do I make it accessible to the internet? Can someone point me to a guide on how to get it "live" to the internet instead of just my localhost. I'm not quite sure where or what to search for.

---

### Post by houstonbofh on 2006-09-21
Way to much to guess at here. What kind of internet do you have?  Are you using NAT?  Do you have a router?  Do you have a public IP address?  Does your ISP filter port 80?  If you can see it from your another machine at your home, it is no longer a ubuntu question.

---

### Post by bluevoodoo1 on 2006-09-21
> **houstonbofh said:**
> Way to much to guess at here. What kind of internet do you have?  Are you using NAT?  Do you have a router?  Do you have a public IP address?  Does your ISP filter port 80?  If you can see it from your another machine at your home, it is no longer a ubuntu question.

Hmm. Well, I guess it'll be more work than I had originally thought... I'll just play around with localhost. Thank you.

---

### Post by chrisfay on 2006-09-21
It's really not that difficult to go public once your server is up and running. If you're behind a router, you will need to give your server a static IP and port forward port 80 to that IP using your routers web interface.

Once that is done, barring your ISP does not block port 80, you should be able to access your site using your public IP. If you are blocked, you will have to adjust Apache's listen port to something else and add that new port to the end of your IP when browsing to your site. 

Once you can access it using your WAN IP, you will most likely need to grab a domain name so you're not typing in your IP everytime you want to access your website. If you get that far, I would suggest looking into using something like zoneedit.com; a free DNS service you can use to route your domain name to your server. They also provide a free dynamic DNS service to circumvent issues regarding servers ran on dynamic IP's.

---

