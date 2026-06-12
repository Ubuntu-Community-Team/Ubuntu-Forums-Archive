---
title: "[SOLVED] Understanding server communications behind a NAT router"
date: 2007-08-14
forum: Server Platforms
---

### Post by freebeer on 2007-08-14
Hi folks!

I'm running into issues with my apache server and I suspect that I'm missing some key part of the equation that's preventing me from diagnosing the issue. Maybe someone can help me locate the source of my ignorance, or point me to some sources where I can do some further research.

I'm running apache2 on 6.06.  The box is behind a router which is in turn connected to my cable ISP.  I have a dynamic domain through dyndns.  The apache box has a static internal IP address and port 80 is forwarded in my router to that address.  So far so good.  I can access the web server both locally (behind the NAT) and externally.  

However, I find that there seems to be intermittent issues with this set up that I'm trying to understand (and overcome).  For instance, if I create a link in a forum, say, of a graphic I have on my server, some people have reported that they don't see it.  I'll try a sample here:

[IMG]http://www.freebeer.is-a-geek.org/graphics/hi.gif[/IMG]

You may (or may not) see a waving smilie there.  (I see it just fine internally, because I've altered my hosts file locally to look at the server using the internal IP addy.)  Outside of the local network, I generally see it too, but others are reporting that they don't.  What would be causing this?

This isn't the only example.  On my server, I have a forms page that people can fill out.  Upon completion, it sends the data to a specified email address.  That part is working so far.  The problem is that sometimes the form page doesn't always behave as it should.  When the user hits the submit button, they are redirected to a "thank you" type page.  Sometimes (not always), the user isn't successfully redirected to that page. The browser sits indefinitely waiting for a response from the server (the data and the email are successfully sent but they never get to the "thanks" page.)

The site is a very low volume site... I wouldn't expect any more than one or two forms being filled out per day on average, so I can't imagine it being a bandwidth or speed issue.  

Today's experience in testing this was weirder than normal.  I couldn't reach the forms page at all (this time getting a 404 error) yet when I got home to check the links, everything was fine.  The links checked out and I was able to access the page.  I suspect that I'm too close to the problem to see the real issue.  :(

Any thoughts?  Any additional information that you might need?  Any suggestions as to what I could look into?

Many thanks.

---

### Post by HermanAB on 2007-08-14
Some el'cheapo routers periodically flush their NAT tables which can break your connection from outside.  This is fine if it flushes once a day, but some flush every few minutes.

---

### Post by freebeer on 2007-08-14
Thanks for the comment!  It is an el-cheapo router.  I don't know how often it flushes.  But it gives me an idea to check into.

Thanks!

---

### Post by koenn on 2007-08-15
I think you should also look at your web server logs, to see what hapens with those failed connections : do they reach apache but are not handled correctly ? do they get replied to (but the reply can't reach the client ? ) or do they never reach apache at all. 

The 404 is defenitely a reply from apache (or perhaps a proxy server in between ?) so if you receive a 404, you've probably been able to connect to your apapche, but it couldn't server the requested page. 

Your problem may be a combination of apache config, network config, and NAT (the flushing).

---

### Post by freebeer on 2007-08-15
Thanks for the ideas.  I'm outside the home network at the moment and I can't see the little test graphic.  But I also can't reach the site directly either.  I checked my dyndns account and the wildcard setting was removed.  (I suspect my ddclient script which updates my IP every X number of days to dyndns may be playing a role in this (my IP rarely changes).  I'll wait several more minutes to give it time for the changes to propagate. 

I checked the logs briefly last night but couldn't spend much time on it before I had to head to bed.  I noticed the occasional entry  showing some failed requests (but the file was definitely there).  I also saw some GET requests for the same file with no errors.  I'll have to look into it a bit further and delve a little more into what the log files are trying to tell me.

Thanks!

---

### Post by freebeer on 2007-08-15
ok.. this doesn't make any sense.  After posting the previous message, I started to see the test graphic.  Yet when I try to go to the site, firefox is reporting that it can't find the server at [www.sitename.org](www.sitename.org).  *scratches head*

If I can pull the graphic properly from the site, doesn't it stand to reason that I should also pull the index page?

<mumble mumble *heads to medication locker*>

---

### Post by koenn on 2007-08-15
I couldn't see the waving smiley earlier, but I can now. As this also reveils the url of your site, i want to have a look,  and I can acces it from my browser. That suggest this is not a routing/NAT issue but rather

- a DNS issue, eg the result of caches queries and/or your dynDNS name not pointing to the correct address

- a http cache issue either on your server side (are you using an apache cache/proxy module  or a reverse proxy or something ?) or on the client side (I 'm behind a squid and have noticed some lag in refresh times, eg at these forums)

- an appache issue (eg apache has no access rights on some of the requested files ? did you change config options but forgot to reload ?)

probably your apache logs offer the best starting point o figure out what happens when a page is requested, and figure out where if then fails (sometimes)

---

### Post by MJN on 2007-08-15
It's working fine from here - the graphic and the root index page.
 
Incidentally, there's no point obfuscating your domain name now as it was included as part of the graphic URL!
 
As Koenn, you need to be going through your logs with a fine toothcomb as they will likely hold the key to the cause, of the problems (for which it sounds there could be more than one).
 
Mathew

---

### Post by freebeer on 2007-08-15
I know I didn't need to obscure my name... I just didn't want to bore you with the name, etc.  It's just a test server for me to screw around with and learn stuff.  My web skills are lacking, and my page is ugly, but that will change as I play more.

Thanks for all the suggestions, guys... it's helpful and appreciated (and even the suggestions that turn out not to be relevant to my particular issue is appreciated as it gives me more ideas and concepts to investigate).  [IMG]http://www.freebeer.is-a-geek.org/graphics/thumbsup.gif[/IMG]

It would appear that my issue was my dyndns registration.  I think the script that updates my dynamic address doesn't update the wildcard setting, which results in it being turned off, so www and presumably ftp, etc. URLs weren't being accessed. 

Again, thanks for all the help 'n idears!  :D

---

### Post by MJN on 2007-08-15
It sounds like you've sussed it - and looking at [http://www.dyndns.com/support/kb/using_ddclient_with_dyndns_services.html](http://www.dyndns.com/support/kb/using_ddclient_with_dyndns_services.html) it sounds like ddclient doesn't support the dyndns wildcard option.

Mathew

---

### Post by freebeer on 2007-08-15
> **MJN said:**
>  it sounds like ddclient doesn't support the dyndns wildcard option.



Seems that way, but it's a little unclear.  I removed the wildcard=YES option in the config file.  I'm hoping that by NOT setting it in the config, it won't change the setting at dyndns.  <*crosses fingers and sacrifices an XP disk to appease the gods*>

(Technically, it's not a sacrifice, but the gods might smile anyways.) :D

---

### Post by MJN on 2007-08-16
But what happens if/when your IP changes?

Perhaps you could manually enter your wildcard as a CNAME to [www.domain](www.domain).. Then you just need to look after the www record and the wildcard will follow it round.

Mathew

---

### Post by freebeer on 2007-08-16
hmmm... might look into that.  In reality, my IP hasn't changed in at least a year. So assuming that continues, running the update script is a little redundant (but I wanted to cover my butt in case it ever does).  :D

Thanks!

---

### Post by MJN on 2007-08-16
The wildcard option is often just redundant anyway, unless you've got a specific reason for it.
 
Mathew

---

