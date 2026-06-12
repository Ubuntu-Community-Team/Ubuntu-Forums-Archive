---
title: "Slow writing speed on usb flash drives"
date: 2015-03-08
forum: Ubuntu, Linux and OS Chat
---

### Post by ckrles on 2015-03-08
I'm sorry. I've googled for the answer but I couldn't find it, or at least, a clear one for me. I'm kind of a new. I have 2 devices running Xubuntu 14.04 Lts and the transfer speeds when I write on a usb flash drive are very low. They start at 30mb/s and quickly drop to about to. On 2.5" hdd it stays at 8 mb/s or so. It's not a problem of the flash drives since I tried several of them (recently bought) under windos and the speed transfer is much higher. 

My two pcs are a laptop bought in 2008 powered by core 2 duo at 2.2ghz and a desktop pc powered by a Pentium 4 at 3.00ghz bought in 2003. I haven't checked it out, but I supposed both of them should come with USB 2.0 (how can I check it out?)

So, how could I make them, improve their writing speeds on external usb drives? I am a noob, so I would highly appreciate a kind of detailed explanation.

I think (don't know if I am wrong) transfer speed in usb drives has been kind of an issue in Ubuntu for quite some time.

Any solutions?

THANK YOU VERY MUCH.

---

### Post by tgalati4 on 2015-03-08
Don't use Nautilus to copy files.  Use the terminal and measure the speeds with a stopwatch.  There can be issues with file permission checking while copying which slows transfers to a crawl.  I don't know if it is a bug or a feature.

If the flash drives are near full, then writing to them will slow down as it takes the controller much longer to find free blocks to write to.

---

