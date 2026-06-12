---
title: "Web server questions."
date: 2008-01-09
forum: Server Platforms
---

### Post by Ikith on 2008-01-09
So I got apache working on Ubuntu 7.10. ([http://jeatin.ath.cx/](http://jeatin.ath.cx/)) But I was wondering is there a way to get rid of the default folder in www? Or change the directory in which the server gets the .html files?

Another question I'm looking for a FTP server that works well and blocks people that are trying to brute force it. (I have one on windows and there was a setting that would block the IP after a set number of failed logins).

Please help :-)!

---

### Post by freebeer on 2008-01-09
You should be able to change the default directory for Apache in Apache's configuration file, I would imagine.  I've never done it, so I have no direct experience.

With regards to an FTP server, I use gproftp.  Others have had issues with it, and recommend something else.  (Don't recall the names off-hand.)

I don't think that any FTP server will block brute force attacks.  That's usually left up to a separate application.  (This is in keeping with the philosophy of a program doing one thing well and avoids bloatware.)  I use fail2ban on my FTP server.  If a user fails to log in after 3 tries, the IP address is banned for a specific (user configurable) time.  It works well.

---

### Post by Ikith on 2008-01-09
What I'm looking for currently is an FTP that I can create users and specify folders within my apache webserver directory. I'm going to take a look at the selection above but are there any more options?

---

### Post by freebeer on 2008-01-11
options other than gproftp?  Yes, there are several.  I'd do a search here (even within the server subforum) to check out what others are recommending.

As for setting up the ftp server under your web directories, there's no reason that shouldn't be possible with any of the choices.  You'll want to keep an eye on the permissions, of course.

---

### Post by Sporkman on 2008-01-11
> **Ikith said:**
> So I got apache working on Ubuntu 7.10. ([http://jeatin.ath.cx/](http://jeatin.ath.cx/)) But I was wondering is there a way to get rid of the default folder in www? Or change the directory in which the server gets the .html files?


Yes - look in /etc/apache2/sites-available/ - there's a file there for each site. In the site's file, change the "DocumentRoot" parameter to point to the new directory. Then restart apache:

sudo /etc/init.d/apache2 restart

---

### Post by daniel6 on 2008-01-13
Thank You!!! I was having trouble getting a php file to run on the server. Evidentally was a permission problem with the initial install. I have spent 5 or 6 hours pouring over documentation to no avail. Seems pretty lame to set the server up by default to use anything in /var for http docs to me. I just wanted a way to test my web pages on my local machine before loading them to my ISP's server. I have been wanting to learn some php in the privacy of my own enviornment and now I can. Guess I have a lot to learn about Apache2. I hope it gets easier as I go along. I have some experience with Novell and Windows and did not seem to have near as much trouble trying to find useable documentation.

Thanks again for your excellent support!

Daniel

---

