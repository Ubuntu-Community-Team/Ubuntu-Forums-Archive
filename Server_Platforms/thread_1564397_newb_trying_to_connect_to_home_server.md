---
title: "newb trying to connect to home server"
date: 2010-08-30
forum: Server Platforms
---

### Post by iitywygms on 2010-08-30
Hey all.
I am new at setting up a server.
I have mythbuntu running mythweb at home.  I have a dsl modem and a 4 port wireless router.  I have configured mythweb to use port 8282
I can access it fine from home internal netwrok using the ip xxx.xxx.x.x:8282
I have gone to dyndns and set up a host name.  It is configured to use my dls modems external ip.  I have run all the test from dyndns and those test say the link is good.
Okay, now when I type my host name in a browser, it just times out.
The really weird thing is. If i put the host name up here, [http://freeproxyserver.net/](http://freeproxyserver.net/)
it will bring me straight to my login screen.  That is good.
But if I type it straight into the address bar, I get a time out error message.
I should note that I am not using port 80 but port 8282.
So when i type my address I have to put :8282 at the end for it to connect.
Example.  Blahblah.com:8282
I do not know what else to tell you.  Please tell me what other info you need to help me figure this out.
Thanks.

---

### Post by arrrghhh on 2010-08-30
> **iitywygms said:**
> ...Okay, now when I type my host name in a browser, it just times out.
The really weird thing is. If i put the host name up here, [http://freeproxyserver.net/](http://freeproxyserver.net/)
it will bring me straight to my login screen. That is good.
But if I type it straight into the address bar, I get a time out error message...

This part isn't making sense to me.  You type it in, it times out.  If you "put the host name up here" it works...?

For one, you may not be able to access your external hostname from your LAN - are you trying to hit your external hostname from outside of your network?  Like at a friend's house, on a cell phone, etc...?

The other issue may be port forwarding.  Do you have port 8282 forwarded on your router to your server's IP?  Does your server have a static IP on your LAN?

---

### Post by iitywygms on 2010-08-30
[I](...Okay, now when I type my host name in a browser, it just times out.
The really weird thing is. If i put the host name up here, [http://freeproxyserver.net/](http://freeproxyserver.net/)
it will bring me straight to my login screen. That is good.
But if I type it straight into the address bar, I get a time out error message.)[/I]

If I go to freeproxyserver.net, and type in my web address in there "test area" my web page shows up.
If i type my address straght into a web browser address bar, it times out.
It is hard to explain, maybe go to freeproxyserver to see what I am talking about.

are you trying to hit your external hostname from outside of your network? Like at a friend's house, on a cell phone, etc...?  Yes.

The other issue may be port forwarding. Do you have port 8282 forwarded on your router to your server's IP? Does your server have a static IP on your LAN? yes and yes.

---

### Post by iitywygms on 2010-08-30
here are some pics of what I mean.
here is the way I checked my server connection.  I type in my address like so.
That is what I want.  Problem is, if I type my address in the address bar of any browser, it just times out.

---

### Post by arrrghhh on 2010-08-30
If I type "http://yoursite:8282" it gives me a user/pass auth window... Seems fine to me!!

---

### Post by iitywygms on 2010-08-30
Yeah, just figured out the two different places I have tried have firewalls blocking it](*,)](*,)](*,)
Such a newb I am.

---

### Post by iitywygms on 2010-08-30
> **arrrghhh said:**
> If I type ++++++++++++++ it gives me a user/pass auth window... Seems fine to me!!
THanks for the help.  If you would not mind, please delete my address from your post.
Thanks again. I am paranoid.

---

### Post by arrrghhh on 2010-08-30
> **iitywygms said:**
> THanks for the help.  If you would not mind, please delete my address from your post.
Thanks again. I am paranoid.

No worries.  Please use the "Thread Tools" drop-down menu to mark this thread as [SOLVED]!

---

