---
title: "Creating a Webserver step-by-step"
date: 2012-10-12
forum: Server Platforms
---

### Post by prostudent on 2012-10-12
So here's my problem:

I have an old computer (OS Windows 2000) which I have to turn into a webserver running Moodle and a website I'm going to create from scratch.

I need that server running at the maximum speed possible ASAP.

So I though about asking you about how to do it since I've got no idea of what system to use (it doesn't need to have a GUI. It can be text based if it improves speed) and how to install the software (I've never used ubuntu before).

---

### Post by cariboo on 2012-10-12
You got a pretty stiff learning curve ahead of you. Hopefully you've got at least a couple of weeks before the server needs to be up and running.

Have look at [this]("http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/") page for a web server howto.

For a moodle setup how  to have a look at this [page]("http://docs.moodle.org/20/en/Step-by-step_Installation_Guide_for_Ubuntu").

The web server set up page, is a bit dated, but all the information is still valid.

Before setting up your server, it probably would be a good idea to learn a few Linux basics, which you can do [here]("http://code.google.com/edu/tools101/linux/basics.html")

---

### Post by Lars Noodén on 2012-10-13
When setting up the web server in preparation for Moodle, it will be essential to also enable and use HTTPS.  A self-signed certificate will be sufficient.  There are lots of tutorials and howtos for Apache2, but here is one to get you on the path:

[http://www.debian-administration.org/articles/349](http://www.debian-administration.org/articles/349)

It's important that Moodle use HTTPS otherwise the students will be able to get the staff passwords and have more fun than should be allowed.

---

### Post by volkswagner on 2012-10-13
> **prostudent said:**
> 
I have an old computer (OS Windows 2000) which I have to turn into a webserver running Moodle and a website I'm going to create from scratch.

I need that server running at the maximum speed possible ASAP. ...

For quick deployment you may want to use a TurnkeyLinux prebuilt appliance.  They have one for [Moodle]("http://www.turnkeylinux.org/moodle")!

Yes, running a CLI only will reduce the necessary RAM.

---

