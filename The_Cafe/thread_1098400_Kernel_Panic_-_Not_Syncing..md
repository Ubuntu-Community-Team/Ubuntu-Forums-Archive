---
title: "Kernel Panic - Not Syncing."
date: 2009-03-17
forum: The Cafe
---

### Post by Roasted on 2009-03-17
This isn't anything related directly to Ubuntu so I didn't know where else it'd fit in...... But my story is this:

I'm working with an open source cloning program, which is actually very nice, known as FOG. It's built on top of Ubuntu (or Fedora), but in my case it's obviously Ubuntu 8.10. I have it installed on my work laptop, a Dell Precision M4300, so my laptop basically acts as a server.

I network boot machines to deploy/upload images. In this instance, I wanted to upload an image. I've tested this on about 5 different model computers, all with flying success.

We have a wide array of computers at work (school district) and among the oldest is the Compaq iPaq C700. 700mhz Celeron with 128mb RAM. Makes you cringe, eh? 

When I network boot these computers, which these computers have NIC booting built in, I get a kernel panic followed by "not syncing - out of memory and no killable processes." 

Can anybody clarify this or tell me what I can do to rectify this? These computers are being replaced soon but I'd love to figure it out if anybody can help me.

Thanks!

---

### Post by k2t0f12d on 2009-03-17
Best first guess...you need a smaller initrd.  How much RAM does each machine have and how big is the initrd?

---

### Post by Roasted on 2009-03-17
I have no idea what initrd is, to be honest with you.

I thought it was just due to the 128 RAM, but I network booted a Compaq Deskpro EN which had the same amount of RAM (though, a faster processor, but not by a lot).

The fortunate side is I can still use Clonezilla Live to image these computers individually. But they must have USB 1.1 ports, because the transfer takes about 45 minutes per PC, whereas FOG (unicast 1 to 1 through a patch cable) pushes the same size image in about 5 minutes.

---

### Post by Roasted on 2009-03-18
All right, we found the problem here.

FOG requires at least 256mb of RAM to function. The two computers I was dealing with, though different models, came originally with 128mb of RAM, so I was confused when one worked and the other didn't.

At some point somebody stuck an other stick of 128mb RAM in the one computer that worked, so it indeed had 256mb RAM which was the minimal required for FOG to work which it indeed worked.

Solved.

---

