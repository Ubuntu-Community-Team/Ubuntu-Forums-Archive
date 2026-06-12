---
title: "Accessing encrypted disk image over samba / NFS"
date: 2007-07-01
forum: Server Platforms
---

### Post by madoka on 2007-07-01
Here's the scenario: I have an encrypted disk image that's stored on a remote server, and I can access the server using samba or NFS.  If I mount the disk image, would my password / data be transported in the clear?

---

### Post by darkog on 2007-07-02
> **madoka said:**
> Here's the scenario: I have an encrypted disk image that's stored on a remote server, and I can access the server using samba or NFS.  If I mount the disk image, would my password / data be transported in the clear?

Interesting question and I am not sure. What is your setup?i.e what are you encrypting with? 

I have seen discussions like this and have heard both answers. A very easy way to find out though. Just run a user friendly sniffer (ethereal/wireshark) on one end, capture the traffic and search for your password.

---

### Post by madoka on 2007-07-02
Somehow I don't think it's going to be so simple.  Perhaps the authentication protocol doesn't require the actual password in cleartext, but if the protocol communique is intercepted an attacker can deduce the password, or replay the authentication.  In such case simply searching for my password using a packet sniffer wouldn't work.

The encrypted disk images are created using OS X's Disk Utility.  If someone knows that it's immune / vulnerable to this sort of access, please let me know.

Alternatively, maybe I should just leave the image file unencrypted, and then use [EncFS](http://en.wikipedia.org/wiki/EncFS), for [this](http://arg0.net/wiki/encfs/intro2) implies that EncFS is not at risk.

---

### Post by madoka on 2007-07-07
Replying to my own post--I seem to do that a alot; mabye it means I should have done more research before posting... >_< --[this](http://discussions.apple.com/thread.jspa?messageID=3835107) and [this](http://discussions.apple.com/thread.jspa?messageID=3179585) seems to imply that it's safe to access encrypted disk images remotely.  Safe insofar as eavesdroppers are concerned, but I presume it's still vulnerable to injection attacks.  But this is good enough for my purposes.

---

