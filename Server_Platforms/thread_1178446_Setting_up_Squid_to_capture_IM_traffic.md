---
title: "Setting up Squid to capture IM traffic?"
date: 2009-06-04
forum: Server Platforms
---

### Post by CyberCowboy on 2009-06-04
My sister-in-law has 4 teen & pre-teen girls and she's worried about whom they are IMing with.

I'm thinking a squid proxy server MAY be the solution since the girls use a mix of client based (i.e. AIM, Yahoo messenger, etc.) and web based (Facebook, My Space.)  However is there an output method from squid that is going to be fairly easy for my Sister-in-law to read and know what's going on without myself or someone else having to decode?  I've never worked with Squid myself so if there is something else is more appropriate feel free to let me know.

Also if someone could point me at a fairly novice configuration guide I'd be very grateful.

---

### Post by Jago6060 on 2009-06-04
Just putting in my two cents, but normally, people have their passwords stored in IMing utilities and web services like myspace and facebook.  My short term suggestion would be to attempt to gain access to the accounts, and enable chat logging.  Of course this won't work if the use isn't happening at home, but given the title, I assumed it was :-)

---

### Post by CyberCowboy on 2009-06-04
While a good suggestion the problem is each girl has their own machine and we're trying to limit/minimize likely-hood they would know they're being monitored (by nabbing their machine or them coming across the logs or seeing anything installed locally.)  Their main network equipment (router, modem, switch) is in a back corner of the basement that no one ever goes in so an additional box would never be noticed.  If we have to we'll go with the logging solutions, but I'd rather have all the logs consolidated into one central repository where mom can browse at her pleasure rather than trying to either snag the girls machines, or figure out when the machines are powered on and have a short-cut to the log location on each of 4 different machines.

Thanks though.  We're rather concerned because whenever an adult walks in on the two older girls windows quickly close, it could just be normal teenage secrecy but we'd rather be safe than sorry.

---

### Post by Jago6060 on 2009-06-04
Oh no I completely understand where you're coming from.  My younger sister used to talk to an older guy on AIM, long story short, she had to go to court to testify against this guy because he had a huge archive of child porn.  Nothing happened to my sister, but she definitely learned her lesson.  Anyway...on a more technical note-->

Is it a possibility to just block all traffic flowing through IM reserved ports?  Or does "Mom" want to let them IM and just monitor?

---

### Post by CyberCowboy on 2009-06-04
For now we want to just monitor, especially since PROBABLY not all of them are being stupid.  Also it's multiple different IM applications and protocols so I think we'd just wind up chasing them further underground.

We both agree it'd be better to gather evidence and then face whatever is going on, especially since we don't know at the moment what it is anyway and it may be a case of a single mother over-reacting.

---

### Post by Jago6060 on 2009-06-04
Ok.  I took a look through a sample squid config file.  It looks like you can specify port numbers for what you want to monitor.  My thought would be to close all ports except those that are necessary from a system standpoint like http, https, ftp, etc.  Also allow ports that are actively used, like the ports used by IM services(which are most likely static).  This way you can eliminate the chance of the IM randomly assigning a port number.  Then set up squid to monitor open ports.  I think the tough part would be getting the packets and translating them to something readable, since squid probably doesn't handle that.

---

