---
title: "Start awesome in vnc with Ubuntu Server?"
date: 2010-11-19
forum: Server Platforms
---

### Post by Veovis Muad'dib on 2010-11-19
I'm setting up two servers with Ubuntu server 10.04, one file server at home and one web/game server.

I'd like to get awesome running at start up and accessible through vnc.  If at all possible I'd like to avoid it being available to the actual monitor.

I'm not a fan of eight character password limits, so if I could only use keys or something like that, even if I have to use ssh or something to do so, I'd be happy.

Does anyone have any recommendations for me?  I'd be very appreciative.

---

### Post by HermanAB on 2010-11-20
Uhmmm... Ubuntu server has SSH installed by default, so please do yourself a favour and kill VNC.  There are numerous threads on these forums about machines getting compromised via VNC.  It is pretty much a sure fire way to have your machine screwed up.

---

### Post by Veovis Muad'dib on 2010-11-20
If everything I needed to do had a command line way to use it, then sure.  But I have to do things on both servers through VNC.  So rather than attempt to tell me not to use it, offer suggestions on how to make it more secure, since that was one of my questions.  Can I require ssh access before use?  Can I use a key instead of a password?

EDIT: And the game servers are not something I can "Find a command line alternative for."

This sort of reply is inflammatory and not useful.  Please refrain from posting similar responses if that's all you have.  I don't want to wade through spam to find an answer.  Maybe if you said, "VNC is insecure, use X" where X is a graphical alternative, it would help.

Is there an alternative to VNC that I can connect to from Windows, Linux, OS X, iOS, and Android?  If so, I'd be glad to hear it.

---

