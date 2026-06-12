---
title: "Update 10.04 fetchmail to 6.3.17 (or SSL tolerant version)"
date: 2010-06-25
forum: Server Platforms
---

### Post by jakeharrop on 2010-06-25
Hi All,

I've spent all day trying to work this out.  We have a ticketing system (request tracker), which polls a POP3 mailbox for new inbound ticket emails.

We've upgraded both our mailserver to exchange 2007 and are trialling RT on a new ESXi host.  While this arrangement has worked perfectly for 2 years on exchange 2003, 2007 gives you the option of using TLS.

Unfortunately, the version of fetchmail in the repositories for 10.04 (fetchmail 6.3.9) just does not want to work with exchange 2007, no matter what i specify in /etc/fetchmailrc, however by playing around with the production RT server, I've found that upgrading fetchmail to 6.3.17 (which is the latest version) just makes everything work again.

However, I've pretty much broken the fetchmail install on my production box - I now seem to have both 6.3.9 & 6.3.17 installed on there, and if I use /etc/init.d/fetchmail to restart it, it'll restart 6.3.9 which then generates errors about certificates and never collects any mail, however if I manually start fetchmail then it starts 6.3.17 (which is the version that i want the init script to start for me).

So, 2 questions.  How do I fix my garbled install of fetchmail on my production box, and how do I upgrade my ESXi instance to fetchmail 6.3.17 without breaking anything?  I'm happy with doing the ./configure and make install to get 6.3.17 on the box, but it then extracts it to my home directory - what do I do then to update the 6.3.9 fetchmail files that are currently in existance ?

Thanks very much,

jake

---

### Post by Bachstelze on 2010-06-25
6.3.17 is in Debian squeeze. With a bit of luck, it will work on your Ubuntu.

---

### Post by jakeharrop on 2010-06-28
Thanks for the tip - I'd actually already downloaded and tried to use dpkg with the debian  Sid version, but it didn't want to work.

ended up making from source and just spending the time working out where I was going wrong - in the end it was very simple, for some reason the path in the init script didn't like pointing to /usr/local/bin and refused to see the new fetchmail executable in there.  I just copied it into /usr/bin and all seems to be working great now.

Thanks

jake

---

