---
title: "Nutts! Nutts! Nutts! Nutts!"
date: 2007-03-14
forum: Server Platforms
---

### Post by hairshirt on 2007-03-14
:lolflag:  THIS IS DRIVING ME ABSOLUTELY NUTS. :lolflag: 

I've been trying to configure a home server to serve a number of sites (3) I have from Dyndns.  No word of a lie when I say I've been attempting this for months during which time it has consumed my whole life.  I&#8217;ve not washed for months and I&#8217;ve started to hum and my underwear makes its own way to the already overflowing washing basket and strange little insects have started to appear all over the walls; darting about in all directions and they sing silly little songs to me and and and.

Had it working under Fedora 6 but wanted to change to Ubuntu (6.10) and it's made me completely mad... yes, I've become quite mad. Hee Hee Hee Haa Haa Haa! Yes mad.  Ubuntu is responsible for sending me mad and my psychiatric team charged with my case/case want to know where Mark Shuttleworth lives so they can send him the bill.  I&#8217;m now completely BONkers!!!

Followed the instructions outlined here: [http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

As setting up a LAMP server from the default installation would be far too easy and boring!

I did not install ispconfig because it would be a waste of time and resources for me and besides it looks like shite (I can write words like that now because I&#8217;m now completely mad).  I did not do any of the configs for the ispconfig install.

Installed phpMyAdmin and then webmin &#8211; phpMyAdmin worked to start with but now does not work (load via the brower).

I&#8217;ve tried editing the httpd.conf and sites-available and it driving me nuts.  I remember having it working first go on Fedora but Ubuntu (debuntu) has now claimed my sanity.

I&#8217;ve tried many, many different configurations meaning server1.****.****.local or dev to the server100.****.com I&#8217;ve got from Dyndns.org.  I&#8217;ve nearly worn out the cdrom drive with the amount of times I&#8217;ve installed a fresh copy of ubuntu 6.06.1 and 6.10.

I&#8217;ve now been Sectioned under the Mental Health Act.  The only way I can get off this section is either by lots of sheets being knotted together, a file being secreted in a cake or by someone helping me out with this problem.  Help me please someone, help me please.  Get me out of this awful place.

Router is configured correctly: dyndns.org &#8211; user and pass &#8211; server100.****.com.

ddclient is installed and configured and started at boot as with all other relevant modules..

Setup different users for each web site &#8211; setup virtual servers for each web site &#8211; setup proftpd for each web site and the bbloodyy thing (site) still does not load.

And before you ask my ISP does not block any relevant ports&#8230;yes, port 80 is open. Can ping, set permissions to 777 and web dirs are under /var/www.

:guitar:  IS THERE ANY HELP OUT THERE PLEEEEEEEEEASE :guitar:

PS I'll even sing for you.

---

### Post by Nikron on 2007-03-14
Wait, so what's your problem?  Php doesn't work?  If it doesn't try..

sudo a2enmod php5

Though, I doubt that's your problem if your been going mad for months..

And personally I detest how the perfect setup is setup, but =P

---

### Post by hairshirt on 2007-03-15
I’VE ONLY BEEN GIVEN JUST A LITTLE TIME TO WRITE THIS POST.  SORRY FOR SHOUTING BUT THAT’S JUST WHAT MAD PEOPLE DO.  I’M HAVING TO TYPE THIS MESSAGE WITH MY NOSE AS THEY WON’T TAKE THE STRAIGHT JACKET OFF.  SORRY ABOUT THE DRIBBLE.
 
php is working.

The problem is that it's a pig to get my web sites to load on the browser.

Seems to me that there are too often too many people seeking help on these forums – especially in this regard.  This is a case in point – posted this last night – got one reply from someone asking me if I’ve got php installed – bless.

HELP!

---

### Post by conjur3r on 2007-03-15
Well first things first.  What do you see when you enter each and every one of those URLs you've setup using dyndns?  Do you get one of your sites for each of those URLs?  Do you get any?

---

### Post by hairshirt on 2007-03-15
Hi and thanks for your offer of help.

I've tried so many configs.  I have on previous installations got the one site regardless of where (which domain) I uploaded the site files.  Meaning got the site regardless of the web address and using IP 192.168.1.101.  The router forwards requests to that internal IP.

I completed the above install as it looked pretty good and worked on Fedora 6.  On this install (and I don't mind installing again if needbe) I don't get any of the sites load on the browser (either FireFox or IE (yuck)).

I think it's got something to to with how debuntu splits the httpd.conf (sites-available) but I'm buggered if I can figure it out.  I tried just about everything but the right one and I've run out of ideas.

Can I sing to you yet?  I just want to sing... :guitar:

---

### Post by darrenm on 2007-03-15
How are you trying to access the sites? If by the domain name and you are inside the same network (behind the same router) it won't work because the DNS lookup gives you the IP address of the external interface of your router. Your router says "Hold on, I have a route to you on my other interface but the traffic is coming from the wrong interface and now I have to NAT you and it won't work and I'm all confused" and of course won't work.

If all of that is wrong and you're accessing the site from inside using something like [http://localhost](http://localhost) or [http://server](http://server) then what happens when you try to access the sites? Are you trying to access localhost or a different machine? Whats the domain (if you feel like putting it on a forum)

---

### Post by hairshirt on 2007-03-15
Hi, and thanks for your offer of help.

This config has worked and worked well on fedora 6.  I have been able to load the site from inside and from outside my newwork.

These sites are just bogg standard dyndns sub domains.

I've tried localhost - server100.****.com - and the url proper with www and without.  It does ot load.

Perhaps I not crazy perhap I'm just stupid but I've tried just about every config I can think of... bar the correct one that I need.

Did you know that bla bla/phpMyAdmin works on Fedora 6 but /phpmyadmin does not and that the reverse is the case on debuntu normally.  Still can't get that to load on debuntu.

Perhap I am stupid!

---

### Post by darrenm on 2007-03-15
try ```
tail -f /var/log/apache2/error.log
``` as you refresh the page. What is the error message? Does the site just time out? 
Assuming the site is hosted on your own box you need to go to localhost... but if you have virtualhosts set up which will only load for the relevant domain then localhost won't work. Depends on how you set up the sites-enabled file.
If you have problems, paste your output of ```
ls -alt /etc/apache2/sites-enabled
``` and ```
cat /etc/apache2/sites-enabled/*
```

---

