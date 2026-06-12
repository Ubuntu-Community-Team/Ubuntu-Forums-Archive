---
title: "XP in VirtualBox:  No web access"
date: 2007-12-26
forum: Virtualisation
---

### Post by jasonrandolph on 2007-12-26
I'm a Virtualization newbie, and am excited about the possibilities it offers.  So I went ahead and installed Windows XP (Version 2002) on my notebook running Gutsy only (no dual-boot), and everything seemed to be working great until I tried connecting to the internet.  I tried going to the VirtualBox User's Manual, but it didn't help.  I normally connect via wireless DSL, and I know XP back then wasn't really geared yet for wireless.  Can anyone help me out here?

---

### Post by Shazaam on 2007-12-26
You can surf the internet fine with your wireless setup in Gutsy? 
Don't change the wireless setup on the host (Gutsy). What you need to do next is set up some kind of virtual networking between the "host" and the "guest". I don't use virtualbox myself but network setup should be similar. Make sure you set up internet access (Synaptic; Firefox etc) on the guest as a "Direct Connection to the Internet" after you can connect to the host. Use one of three types: "nat"; "bridged" or "host only. Once you get that setup you should be fine. What happens is you connect the guest to the host; then the host to your wireless setup.
I seem to recall a post on the forums here that tells you how to do wireless from the guest but I don't have a link at the moment.

---

### Post by jasonrandolph on 2007-12-26
Thanks for the advice.  I'll try it out and post the results.  Don't worry, I won't be altering anything in Gutsy!

---

