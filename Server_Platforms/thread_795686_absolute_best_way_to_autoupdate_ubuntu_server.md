---
title: "absolute best way to autoupdate ubuntu server?"
date: 2008-05-15
forum: Server Platforms
---

### Post by at0mic on 2008-05-15
hi,

What is the absolute best way to schedule daily updates and send some sort of warning if a reboot is required ?

---

### Post by dmizer on 2008-05-15
automated updates are dangerous for a number of reasons, not the least of which is that it can render the server inoperable.

here's a good rundown on why: [http://www.linux.com/feature/119162](http://www.linux.com/feature/119162)

---

### Post by songshu on 2008-05-16
i never schedule daily updates, always manually and i do it about weekly. during the week i see the messages from the security list come in and i scim through them briefly.


[https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

---

### Post by utdream on 2010-01-20
While some administrators prefer to update manually, many administrators simply do not have the time or the inclination to update servers manually - particularly when there's an entire farm of them to manage.

Personally, I'd rather deal with the ramifications of the VERY RARE update problem then deal with a security breach due to an unpatched system, but to each their own.

How about answering the question that was asked instead of pushing an administrative philosophy?

At0mic, here's some Ubuntu docs on the subject:
[https://help.ubuntu.com/8.10/serverguide/C/automatic-updates.html](https://help.ubuntu.com/8.10/serverguide/C/automatic-updates.html)

Hope this helps!

---

### Post by zaksworld on 2010-01-20
If your server is not well maintained, updates might make your server go down for a bit.  But at the same time, this does not usually happen often, so I always like to update my servers.  Also, it doesn't have to be time wasting, and you don't need to automatically update them either, because that can have problems in itself.

There are ways to update your servers automatically that are very easy, such as scripts, but these can be very dangerous.

Personally, I like to use a private network to ssh into my servers all at once, then update only a few at a time.  On a private network, my connection is safe, I'm just controlling all my servers on one machine.  I only update about one to two different servers at a time, this way if there's an update that isn't working to well, if it has to reboot, or something along those lines happens, then i still have other servers to take it's place.

Now, to answer your question, if I absolutely had to update my servers automatically, I would definitely make a script that would do it for me.  Scripts are easy to make, and put in motion.  They can also hold administrative passwords and use them just in case.

---

### Post by kewlrichie on 2010-01-21
I also like to get the security updates via email and apply patches according to what I think is important. I had a public facing mail server and FTP server so of course if anythig having to do with those will updated asap after checking the details of the update of course and I rarely ever do kernel updates becuase I have had problems in the past unless there is some critical update that is needed. I like to stick with using apt-get instead of aptitude for update and upgrade cause it holds back the kernel updates automatically which is nice for me.

---

### Post by dmizer on 2010-01-21
> **utdream said:**
> While some administrators prefer to update manually, many administrators simply do not have the time or the inclination to update servers manually - particularly when there's an entire farm of them to manage.

Personally, I'd rather deal with the ramifications of the VERY RARE update problem then deal with a security breach due to an unpatched system, but to each their own.

How about answering the question that was asked instead of pushing an administrative philosophy?

At0mic, here's some Ubuntu docs on the subject:
[https://help.ubuntu.com/8.10/serverguide/C/automatic-updates.html](https://help.ubuntu.com/8.10/serverguide/C/automatic-updates.html)

Hope this helps!

With a server farm, you would be pushing your updates from a central server, rather than pulling them per-machine. Something like this: [http://www.howtoforge.com/installing_puppet_on_ubuntu](http://www.howtoforge.com/installing_puppet_on_ubuntu) would be ideal for a server farm. And, since most server farm administrators would seek to manage their network in such a way, and would know about these kind of solutions, I assumed (perhaps wrongly) that the OP was only dealing with one or a handful of servers.

This is not pushing an administrative philosophy, this is advocating safe computing.

---

### Post by jrevillini on 2010-05-07
> **utdream said:**
> Personally, I'd rather deal with the ramifications of the VERY RARE update problem then deal with a security breach due to an unpatched system...

Second that.  And what about development servers?  Development servers are, in a lot of cases, the perfect way to test the updates before they make it to your production server.  Why not make it easy on yourself.

> **utdream said:**
> How about answering the question that was asked instead of pushing an administrative philosophy?

Second that.

---

### Post by sylvester_0 on 2010-05-07
While I second what everyone else said (what if an upgrade breaks www/smtp/imap etc and you have to put out that fire?), you're looking for the "unattended-upgrades" package.

---

### Post by sylvester_0 on 2010-05-07
> **kewlrichie said:**
> I like to stick with using apt-get instead of aptitude for update and upgrade cause it holds back the kernel updates automatically which is nice for me.

Apt-get doesn't hold back kernel upgrades for me; I wonder where this is coming from. Why not let it install the kernel upgrades? It doesn't force you to reboot... If for some reason you do have to reboot then you'll boot into the latest kernel. I'm paranoid about using the latest kernel so I always reboot the night following a kernel upgrade.

---

