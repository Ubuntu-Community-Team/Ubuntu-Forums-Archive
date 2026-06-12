---
title: "How do I search for drivers and then share an internet connection?"
date: 2011-06-21
forum: Server Platforms
---

### Post by That Guy Is Here on 2011-06-21
Hi all,

So I have three machines(2x Dell Optiplex GX620, 1x Dell Optiplex 330) and I salvaged a D-Link Ethernet card from another PC, and I want to put it in the Optiplex 330. I was wondering if there was something I needed to do before I take the server offline and install it and how do I find the drivers for it? Or does Ubuntu go ahead and do that?

And my second question is, once I get the network card installed, how do I share the internet connection of that machine with another server? And how would I SSH in to the server connected to the other? I'm guessing that I have to set up some ports to do that, but I don't know how as I am very new to the Ubuntu Server scene and Im doing this for educational purposes.

Cheers,
Joshua

---

### Post by arrrghhh on 2011-06-21
> **That Guy Is Here said:**
> Hi all,

So I have three machines(2x Dell Optiplex GX620, 1x Dell Optiplex 330) and I salvaged a D-Link Ethernet card from another PC, and I want to put it in the Optiplex 330. I was wondering if there was something I needed to do before I take the server offline and install it and how do I find the drivers for it? Or does Ubuntu go ahead and do that?

And my second question is, once I get the network card installed, how do I share the internet connection of that machine with another server? And how would I SSH in to the server connected to the other? I'm guessing that I have to set up some ports to do that, but I don't know how as I am very new to the Ubuntu Server scene and Im doing this for educational purposes.

Cheers,
Joshua

Hrm.. well you'd need a router between the two server's to properly share the internet connection.  You can use a crossover cable, and directly connect the two machines... but that's not exactly the preferred method.

As for drivers, this isn't Windows :p.  It should "just work".  I'd say 99.9999% of wired ethernet controller cards are completely functional out of the box on Ubuntu.  Wireless cards are a different story.  Not sure the exact number, but there are quite a few cards (mostly Broadcom chipsets) that need special drivers (sometimes proprietary) in order to function correctly or at all.  A quick boot of a LiveCD will confirm for you.

---

### Post by That Guy Is Here on 2011-06-21
Thanks for the quick reply! Ok so ill take it offline and try it. And I ran out of ports on my router :P that's why I was asking about the connection sharing.

---

### Post by arrrghhh on 2011-06-21
> **That Guy Is Here said:**
> Thanks for the quick reply! Ok so ill take it offline and try it. And I ran out of ports on my router :P that's why I was asking about the connection sharing.

Oo.  Well... you'll need multiple ports on your server then.  You'll need one port to take in a connection from the router/internet, and then another port to plug in the other machine.  Perhaps that is what the additional network card is for?  If you do this, you will need a crossover cable between the two computers.  Router to computer, straight thru cable, but computer to computer needs a crossover cable.  Kind of like switch-to-switch trunks - if you use ethernet, cable's gotta be crossover.

---

