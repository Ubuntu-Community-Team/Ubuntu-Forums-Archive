---
title: "Server and desktop install"
date: 2006-12-03
forum: Server Platforms
---

### Post by NumberOne on 2006-12-03
Hello all,

I am new to Ubuntu and am having a problem.

I installed 6.10 server and all went well.  I then installed Ubuntu Desktop using "sudo apt-get install ubuntu-desktop".  I did not get any errors during install.  When I restarted I got the error stating "X windows did not start. It is propably not setup properly".

Is anyone else having this problem?
How do I fix this?

I tried the install twice. Completly reformated drive both times, and get the same error.

I previously installed 6.06 server and desktop the same way and all worked fine, so I don't think it is a hardware incompatibilit, but not sure.

Any help would be appriciated.

TGhanks.

---

### Post by benjy on 2006-12-03
Hi NumberOne,

I myself run a webserver from my ubuntu powered pc (I'm posting this straight from it). After some playing around myself, I found it easier to install the standard ubuntu desktop then setup any and all web server functions afterwards. 

I believe this is because during the desktop install, all the necessary hardware settings are auto-detected and configured for things like graphics and wireless adapters (at least to my own experience anyway) and so if you need things like that setting up it's better to get that done first (especially if you, like me, want to [use the official nvidia drivers]("http://albertomilone.com/nvidia_scripts1.html") and an occasional bit of [beryl]("http://wiki.beryl-project.org/index.php?title=Install/Ubuntu") ;).

What kind of server are you wanting to set up? I personally started small on my own home run and use the [abyss]("http://www.aprelium.com/abyssws/") web server because it's simple, small and is very easy to set up php with it. If you then use a cms or blog script that uses a flatfile databasing system (like [pivot]("http://pivotlog.net")) you can have a working website very quickly even if you use dsl internet there are many free [dynamic dns]("http://freedns.afraid.org") services available. But I feel I'm waffling slightly.

Before I can really help I need to know what it is you want to do, and some more specifics about your own setup. I've recently been playing around with this stuff myself. Currently (if I'm online) my little site can be found [here]("http://benjy.wtf.be").

---

### Post by NumberOne on 2006-12-03
What is the difference between the desktop version and the server version besides the GUI.  Will I be loseing and features or abilities doing it this way?  I plan on setting up both a web server and email server to replace my windows box.

---

### Post by D. S. on 2006-12-04
> **benjy said:**
> Hi NumberOne,

I myself run a webserver from my ubuntu powered pc (I'm posting this straight from it). After some playing around myself, I found it easier to install the standard ubuntu desktop then setup any and all web server functions afterwards. 

I believe this is because during the desktop install, all the necessary hardware settings are auto-detected and configured for things like graphics and wireless adapters (at least to my own experience anyway) and so if you need things like that setting up it's better to get that done first (especially if you, like me, want to [use the official nvidia drivers]("http://albertomilone.com/nvidia_scripts1.html") and an occasional bit of [beryl]("http://wiki.beryl-project.org/index.php?title=Install/Ubuntu") ;).

What kind of server are you wanting to set up? I personally started small on my own home run and use the [abyss]("http://www.aprelium.com/abyssws/") web server because it's simple, small and is very easy to set up php with it. If you then use a cms or blog script that uses a flatfile databasing system (like [pivot]("http://pivotlog.net")) you can have a working website very quickly even if you use dsl internet there are many free [dynamic dns]("http://freedns.afraid.org") services available. But I feel I'm waffling slightly.

Before I can really help I need to know what it is you want to do, and some more specifics about your own setup. I've recently been playing around with this stuff myself. Currently (if I'm online) my little site can be found [here]("http://benjy.wtf.be").
This looks absoutlutely fantastic I have a 3.8 gig intell box 500gigs of storage 4 megs ram and a cable connecton. However comcast has us locked into using them in this area and wondering if this setup could be used as an ip bassed site for a small closed word of mouth community?

---

### Post by hernan43 on 2006-12-05
> **NumberOne said:**
> What is the difference between the desktop version and the server version besides the GUI.  Will I be loseing and features or abilities doing it this way?  I plan on setting up both a web server and email server to replace my windows box.

The server version is a very stripped down and streamlined installation. It doesn't make as many assumptions about the purpose of the machine as the desktop install does. 

If you are going to install the desktop at all, I would suggest using the desktop installation and then install any server(i.e. apache, postfix, exim, etc) afterwards. 

Like benjy said, the desktop install will do all of your desktop setup for you. You won't lose nay functionality as the server and desktop both use the same apt sources so you will have the same software available to you.
--hernan43

---

### Post by aash on 2006-12-05
Did you edit the /apt/sources.list files and uncomment the extra rep's install ubuntu-desktop provide you with the necessary xorg, gdm packages to auto fire your desktop environement, but if you don't have all reps uncommented might not pull other packages.
 Try that allways worked well that way.

cheers

---

### Post by benjy on 2006-12-11
> **D. S. said:**
> This looks absoutlutely fantastic I have a 3.8 gig intell box 500gigs of storage 4 megs ram and a cable connecton. However comcast has us locked into using them in this area and wondering if this setup could be used as an ip bassed site for a small closed word of mouth community?

I see no reason why you couldn't, just check whether your cable company blocks port 80. If it does it's a pain, but possible to get around. If they do, you will have to append all URL's with an alternative port number (and obviously set your web server to use that alternative port - if you're using abyss this is very easy) or take advantage of some of the paid services for dynamic dns that are available. The Lower options are still much cheaper than paid hosting and offer workarounds to the problem.

---

### Post by houstonbofh on 2006-12-12
The server version uses a different kernel.  It also is set up more biased to cron than anachron.

No to the fix, did you try 'dpkg-reconfigure -phigh xserver-xorg' and did you look at the conf file?

---

