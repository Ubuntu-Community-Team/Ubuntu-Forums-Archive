---
title: "Re: LTSP Issues"
date: 2012-03-08
forum: Server Platforms
---

### Post by ceaecc on 2012-03-08
I cannot find instructions for starting a new thread, so this thread name will cover it; please excuse the intrusion.

Installing Edubuntu 11.10 on a Del Optiplex 755 with mainboard network connector plus another network card plugged into a PCI slot, only one network connection is not "unavailable" at a time. Whether I boot up with the internet line connected to eth1 (the connector embedded on the mainboard) or to eth0 (the PCI card) always the one connected to the internet is declared as "connected" and the other "unavailable." This is the case whether I am installing Edubuntu on the hard disk and choose to include LTSP, or whether I have booted from the DVD and click to test LTSP. I get the same results from nm-tool, except that the term for State is "unmanaged" instead of "unavailable" when I make no attempt to use LTSP.

I did find some references to "unavailable" or a few to "eth0 unavailable" in Ubuntu forums, but the replies seem to focus on complex steps to install drivers made for Windows rather than included with Edubuntu. Since the problem is reversible, depending on which network connector I choose to plug my intenet cable into, I wonder if someone might know about something simple I overlook, or if there it is a known issue with Dell Optiplex. I can provide some readouts to terminal commands. I want this server to have two separate networks, one for the internet and the other LTSP. As it stands, as soon as LTSP is set up the internet connection is shut off because only one NCI is available. I did read about the possibility of eth0:1 but I do not want to use that workaround. This Core-duo computer should be able to handle two NCI connections.

Thank you.

---

### Post by howefield on 2012-03-08
> **ceaecc said:**
> I cannot find instructions for starting a new thread, so this thread name will cover it; please excuse the intrusion....

How rude, let's not.

Please refrain from hijacking other threads.

Post moved to own thread.

---

### Post by ceaecc on 2012-03-09
Thanks for moving it. Now I see how to start a thread -- sorry

---

