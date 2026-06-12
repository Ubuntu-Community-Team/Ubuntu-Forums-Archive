---
title: "Borked my server-reset to defaults or re-install?"
date: 2007-02-15
forum: Server Platforms
---

### Post by wolfear on 2007-02-15
Everything has been going great till now using a CD installed LAMP with a KDE desktop (Edgy).
I have been using my LAMP install locally for months with no issues and decided to start sharing with my partner in another town.
Got set-up with DynDNS and went ahead and installed Shorewall. It's working fine.
But now, I have totally borked my server.

I was trying to configure Apache (using Webmin) to serve from a specific directory in /var/www when accessed from the DynDNS thing.

Now I have lost all access even under localhost. phpMyAdmin won't load...not a thing. Just a "cannot connect to server" error for localhost.
Can someone direct me to how I can reset the default configuration or is it easier to just unintall/reinstall Apache?
Maybe a "How to fix your server because you are an idiot" guide?....lol

---

### Post by conjur3r on 2007-02-16
The only way to learn is to try and fix it.  What you have described is very common throughout an administrator's life.  The first point of call is to check the appropriate logs such as /var/log/messages, /var/log/apache2/error.log and mysql's.  When there is an error, they will be reported in a logfile.

You could also issue the following command which checks to see if your apache config files are ok:
# apache2ctl configtest

---

### Post by wolfear on 2007-02-16
Thanks for the input.
You are right, the only way to learn is to do. I was hoping there might be somewhere I could find the default configs and compare it to what I have so I can see where I screwed up.

The config check came back with a "Syntax ok".

Looking at the message log, I didn't see anything (that I could tell) was related to apache.

The apache error log has numerous entries like this:

```
[Thu Feb 15 20:21:36 2007] [alert] getpwuid: couldn't determine user name from uid 4294967295, you probably need to modify the User directive
[Thu Feb 15 20:21:36 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Thu Feb 15 20:21:36 2007] [alert] Child 22590 returned a Fatal error... Apache is exiting!
[Thu Feb 15 20:21:36 2007] [alert] getpwuid: couldn't determine user name from uid 4294967295, you probably need to modify the User directive
```

I have no clue what that means, but I am guessing I messed up some permissions somewhere?
I am going through the Apache.org site (again) to try and get a handle on what I might have done.
On a lark, I downloaded the 2.2.4 since I am messing around with this anyway and the website said this fixed a security issue, how difficult is it to go ahead and upgrade?

---

### Post by Brazen on 2007-02-16
I'm not sure how nice Webmin plays with Ubuntu's Apache config, since it is a little different than a standard Apache setup.  About the only way we can help you  is to post everything under /etc/apache2 and find where the bad configuration is.  I love using Webmin, but Apache is one thing I prefer to just edit the config files by hand.

If you want to start over, unistall it with Synaptic and be sure to select "completely remove" rather than just "remove".  This might also be able to fix your configuration:```
sudo dpkg-reconfigure apache2
```

---

### Post by conjur3r on 2007-02-16
> **wolfear said:**
> 
[Thu Feb 15 20:21:36 2007] [alert] Child 22590 returned a Fatal error... Apache is exiting!
[Thu Feb 15 20:21:36 2007] [alert] getpwuid: couldn't determine user name from uid 4294967295, you probably need to modify the User directive

This seems to tell me that your **User** and/or **Group** declarations in /etc/apache2/apache2.conf is bad.  This could point to an incomplete webmin installation.  For reference, the default value for these two directives are **www-data**.

Have a look in your /etc/passwd file and search for that number.  It probably won't exist and that's why you're having this issue.

---

### Post by wolfear on 2007-02-17
Thanks for the inputs.
I had to re-install of the server.
I think it was partially webmin, as there were several files in the apache2 directory for webmin that I dont remember being there before, which is weird because Webmin never did that in the past (that I can remember, I could be wrong).

Plus the users were totally goofed up as Conjur3r suggested. That part I can understand.

The more I tried to sort it out, the worse it got, so as a last resort, I re-installed it.

At least it is another lesson learned.

---

