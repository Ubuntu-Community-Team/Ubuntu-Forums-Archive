---
title: "UI vs. No UI - Is one better than another for a production environment?"
date: 2012-04-23
forum: Security
---

### Post by pctx on 2012-04-23
Hey all,

So I would say that I'm still a beginner to the *nix administration scene but one of the early things I learned early last year when I start moving some of the my college's web application servers to Ubuntu, was that in order to manage the web server, from a security perspective, you should run in "headless" mode.

Fast forward a year and I do pretty much all of my administration in SSH and text (which I'm sure makes some people cringe) but I started to think about the Pro's and Con's of having a UI.  The most obvious being "vulnerabilities" in the UI code etc.  One of the weird things (to me at least) was a colleague was mentioning that he was deploying Fedora at Intel for web servers in which they deploy them with the UI intact.  This puzzled me as again, my school of thought is an Ubuntu web server or any *nix web server is almost like a Firewall, only turn on what you need access to.

This brings me to my question:  In a production environment, from a purely security standpoint, is headless still the way to go?  I ask because I am getting pressure for cross training other co-workers and boss of which I get blank stares when I tell them to SSH and edit text in VIM or Nano.

Curious what people's experiences are with this out there.

---

### Post by newbie-user on 2012-04-23
For me, it's more about performance than security, since having a GUI installed reduces the performance due to more processing overhead. 

Security really depends on the user. My #1 security rule is not to let anyone other than myself have physical access to my servers. Any server that is physically accessible to anyone is already compromised. 

If other users need to access the server, give them nfs or samba shares. There's no need for others to have physical access to the server, hence there's no need for a GUI.

---

### Post by |{urse on 2012-04-23
If the hardware is more than adequate and I know the server is in a secure location that will be away from non-technical staff, I generally will go ahead and gui-install (currently I like LXDE). Simply because I know I have one extra way to explain things to techs/office staff over the phone if need be. It's saved me an on-site trip many a time.
 
If I know these techs are linux guys I'll do the cli-only server install. It's always good practice to ask them what they would prefer before-hand, blank stares or not.
 
-NOW-
 
In an already existing production environment, there should be stringent rules as to what each and every server install should be. If it's up to you then go with what you are most comfortable with and remember, the more you install the more potentially damaging variables you open your environment to (in other words, stick with cli unless you absolutely need the gui). Also keep in mind you can do a server install and later on, down the road, install the gui if you need to.

---

