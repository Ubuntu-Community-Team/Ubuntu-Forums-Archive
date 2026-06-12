---
title: "Webmin, eBox, or Other"
date: 2008-04-23
forum: Server Platforms
---

### Post by deejross on 2008-04-23
I have a couple of questions actually:

First Question:
We have a linux box running Dapper right now that we plan to wipe clean and install Hardy on. Currently, we have been using FreeNX + Gnome to do all the management tasks, but would like to use something a little more convenient. So the real question is, should we use Webmin, eBox, or something else?

The main uses for the box are web(apache), instant messaging(openfire), and email aggregation(dovecot imap + getmail). So which management interface would best suit our needs while being easy enough for the average user to use?

Second Question:
We use OpenFire for our internal XMPP instant messaging server. It's a nice product, but doesn't integrate very well with the rest of the system. Is there a Jabber server that can be administered through Webmin, eBox, etc. that supports OpenFire's features? The main features it has are: groups, broadcasting to all or to groups, and logging of conversations.

Thank you in advance for any help.

---

### Post by honeydew on 2008-04-23
I used ebox a few months ago and had a great time using it, even though it was still a bit buggy.  I know that recently they have been in a transition stage moving everything from debian to ubuntu hardy.  So if you were going to dive into using it, I would expect bugs.  Though I havnt checked recently it may be to a point of being useful.  I have seen webmin quite a few times before though have never touched it so I cant be of much help there.

---

### Post by mmichalik on 2008-04-23
I use Webmin for all of our servers and it's very nice as well.  Although I haven't used eBox yet so I can't give you an honest comparison of the two.

But, I can say that Webmin is intuitive, powerfull and user friendly.

---

### Post by Dr Small on 2008-04-23
+1 for Webmin. It works great for me.

---

### Post by deejross on 2008-04-23
Thanks for the replies to question one. I have also used Webmin before, but a while back and it was quite clumsy. I was just wondering if it was still the best thing. I have looked at eBox and its traffic shaping, domain controller, and other cool features. I'm sure I will eventually try it once it stabilizes a bit more. Any chance Webmin has anything like that already?
Thanks for the replies so far!

---

### Post by Dr Small on 2008-04-23
What would the problem be for having both eBox and Webmin installed?

---

### Post by deejross on 2008-04-23
I guess I really didn't think about that one :) But I would think that they would fight for control of the system though. In other words, a change in Webmin might break something in eBox. If anyone has ever tried it, I'd love to know the results.

---

### Post by Dr Small on 2008-04-23
I don't see how it would, as they are simply utilities. Webmin reads the configuration files and outputs it in your browser in a simple, readable, editable format.

I can't say the same for eBox, as I have never used it, but I imagine it would be identical. The only real problems you would encounter, was if you attempted to edit the same setting in both eBox and Webmin at the same time.

That is where things would most likely conflict.

Dr Small

---

### Post by deejross on 2008-04-24
Well, that's probably true, but I think I will start with Webmin, then later, when eBox matures a little bit, I'll try installing them both on a virtual machine and see how it all turns out.

Thanks to everyone for their help.

---

