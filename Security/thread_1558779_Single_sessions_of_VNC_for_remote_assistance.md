---
title: "Single sessions of VNC for remote assistance"
date: 2010-08-22
forum: Security
---

### Post by msandoy on 2010-08-22
I'm not sure if this is the correct place for this question, but here it goes.
Would it be possible to make a default setup for VNC, so that a user in need of assistance can fire up a single session in a similar manner to the program Teamviewer? I mean just one session, not a continous running server? And so simple it can be done by anyone? And most of all, would it be possible to make VNC safe for this use?

---

### Post by martin_legion on 2010-08-23
What do you mean by "a single session". I'm not familiar with Teamviewer...
If you mean to start a new session where you can log in remotely, then you could try tightvncserver or vnc4server.
If you want to log into the same session the user is logged in, you can try this steps:
[http://ubuntuforums.org/showpost.php?p=5952053&postcount=5](http://ubuntuforums.org/showpost.php?p=5952053&postcount=5)

---

### Post by msandoy on 2010-08-23
The thing is, Teamviewer runs out of the box, without configuring any ports. I have not checked what protocols are in use by this program, but I suspect it connects to an external server from both sides. For people with less than average computer skills, this makes it easy to get assistance. Install and run. Give a session ID number and password to the tech guy and watch the magic. 
I would love to see an open source, easy to use sollution for remote desktop on Ubuntu. This would make it easier to convince others to try it out, due to easy assistance.
The big question is, would it become a safety risk using i.e. VNC to do this job.

---

### Post by OpSecShellshock on 2010-08-23
Couldn't you just have the user enable VNC manually after confirming over the phone that you're ready to log in? Afterwards, they can disable it again and restart. Interactive remote sessions are always going to be a risk. However, being on the phone might help with at least part of it. What I think would be tricky would be the user having to access their home router to forward the necessary port, and then do so again to stop. The alternative would be enabling UPnP, but that's not something I could ever in good conscience advise someone to do.

---

### Post by msandoy on 2010-08-24
I do support with people who actually do not know how to make new folders or how to find the files they download from internet. How do I explain to them over the phone, that they have to access their router, open some ports or enable UPNP, and then install VNC and SSH, so I can log on and set it all up. That would take approx. 8 hours. For me is ok, I get paid by the hour, but the customer would complain. Please test Teamviewer, it's free to use for private persons. See the features, and this is how simple I actually want it to be. I know the open source community can make really good software. Maybe a challenge?

---

### Post by OpSecShellshock on 2010-08-24
Teamviewer does have a Linux version. It appears to be in beta, but it can be downloaded from their website. It supports 32 bit and 64 bit, and comes in handy .deb packages. The site claims that admin privileges aren't required to run it, but I don't know if that extends to the installation as well. I certainly hope not (my experience with the software has been in an intrusion detection/incident response context, which somewhat affects my view of it).

---

### Post by martin_legion on 2010-08-24
Well, I think it would not be more risky than leaving remote desktop enabled on any Windows system (with the corresponding ports open on the router or whatever). You can set a strong password for VNC if you decide to try the vncserver as a daemon, or you can also use the desktop sharing that comes with Ubuntu, that lets you configure some further authorization by the local user (the local user sees a popup informing that someone wants to access it's desktop and asks for permission to do it)

---

