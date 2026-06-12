---
title: "directory listing denied"
date: 2008-03-16
forum: Server Platforms
---

### Post by knudsenUK on 2008-03-16
Please spare me from returning to microsoft. I can't seem to get my websites to list or display from a public network. I can use webmin to access the server remotely using dns domain name rather than an ip address so i figure dns is ok. Although it says "This web server is running in SSL mode." Is that normal for webmin? SSL module is disabled in apache.

I can view the websites via the domain name if logged on locally.
All websites are located in /var/www/site1 for example.

There is some talk of -index of which i have no instances anyway.

This is on LAMP setup and is one of my many problems I face at the mo with trying to install a oscommerce site.

PLease help

---

### Post by TurboRush on 2008-03-16
Just thinking of some obvious things...

If your root folder is /var/www/site1 are you trying to hit [www.somesite.com](www.somesite.com) or [www.somesite.com/site1/](www.somesite.com/site1/) ?

Are you sitting behind a router and are you port forwarding port 80?

If you are attempting to host multiple sites, do you have your virtual servers configured correctly?

---

### Post by knudsenUK on 2008-03-17
I could happily host 1 site if that is simpler. As far as I know the virtual servers are setup ok with references to folders, domain names and ip adresses (one IP many/ names).

The former in answerr to which site so that site 1 / site 2 correspond to each website and are thus virtual servers......

---

### Post by TurboRush on 2008-03-17
Were you able to run with a single website at a point and time or did you jump right into hosting multiple domains? Personally, I think it's easier to start with a single domain, no virtual servers and then progress from there.

Can you post the contents of your httpd.conf?

Are you able to access any of your domain names successfully or do all of them fail?

---

### Post by knudsenUK on 2008-03-18
I'm amazed this is proving so hard. Is there no logical process / flowchart that I can look at. :
Step 1 Create folder in /var/www
Step 2 Creat directive for virtual server linking IP with dns name location of webpages........with the following example......


Much as I like what Linux stands for it has no chance in the mainstream while simple tasks seem impossible to resolve. In IIS this it is a 2 minute job to get a website up and running. Here you can't even get a common consensus on basic issues.

The httpd file has nothing in it now, having reloaded the os for the 3rd time in less days. I am sure I saw a note saying it was a legacy file for old systems?!?!?!?

Even if I DONT use virtual server and just want to host one website I still see references to virtual server *.*  in the directive for default site in sites enabled

I am sorry I just don't get this - how can I get webmin working with no issues and yet I cant find any help on the web for displaying a webpage with Apache
:-(

---

### Post by TurboRush on 2008-03-19
Ok... no worries, lets take a step back and take some small steps.. lets start from ensuring apache is working out to getting access from remote sources.


First, do a clean install of apache. By default apache creates a folder /var/www/apache-default. Verify this folder is there and that there is some content in it.

To be safe, restart or start apache...

```
sudo /etc/init.d/apache2 restart
```

Once Apache is up point your browser to [http://localhost/apache-default/](http://localhost/apache-default/)

Did you get the default Apache page? If yes, Apache is installed and working....

Let me know if you are successful and we'll take the next step.

---

