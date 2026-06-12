---
title: "Do I Need to Set up Postfix?"
date: 2006-04-05
forum: Server Platforms
---

### Post by WelterPelter on 2006-04-05
A question for you gurus. Here is what I want: a cron job that sends emails with files attached to gmail, as a form of data backup. 

Cron I can handle. 

Postfix looks like an awful lot of messing about, just to send an email. Is there a better (i.e. much simpler to set up) program that cron could use to do this? I don't need to receive any emails. Just send. 

I'm on a LAN with DHCP at home, so that could figure into the equation. 

Any tips? Also, is this approach even sensible, or are there better methods?

---

### Post by Velvet Elvis on 2006-04-08
No guru here, just a philosophy student who got on the anti-microsoft bandwagon and switched to linux back in the mid 90s when you still had to figure out all this crap to make anything work.

Postfix has a lot of complicated options, but could very well work out of the box for what you are talking about.  If not, most all of the options you'd need to fiddle with are available via dpkg-reconfigure.  There is also a supurb GUI available with webmin. You may need to set up a real root password to use webmin.  I don't remember.  

To start out install postfix and set the SMTP server to localhost on the default port with no login or password in whatever mail client you are going to be using.  That might be all it takes.

You might also want to take a look at exim.  It's the default MTA for debian sarge and has logical config settings and lots of well written documentation in /usr/share/doc.

Stay far far away from pretty much any of the other MTAs unless you want to spend a lot of time reading.

---

