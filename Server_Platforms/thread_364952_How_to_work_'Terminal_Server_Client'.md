---
title: "How to work 'Terminal Server Client'??"
date: 2007-02-18
forum: Server Platforms
---

### Post by WinterWeaver on 2007-02-18
Hi there!

I've been looking around for a 'Noobs Guide to using the Terminal Server Client'.

I'm sure it's pretty simple to use the app itself.. however... I need help with the technical stuff like:
how the network needs to be set up? What Protocol do I need to use? What do I enter for Domain, client Hostname and Protocol File?

Those are the things that I need help with.

I also need to know if I have to set this up on the networked PC I'm connecting to.

The reason I need to know how this works, is because I am helping 2 friends maintain their Ubuntu Desktops, and they are asking me how to do certain things, and set up things for them. This will be much easier if I can do this from home, and just connect directly to their PC's over the Internet.

Even a quick Link will be appreciated, as I have not really found "Noob"-documentation on this.

Thanks,

WW

---

### Post by veloce on 2007-02-19
Tricky.

Where to begin?

First you need a secure path over the internet to your friends computers.  This could be done just by everyone having a static ip address but you'd be better to set up virtual private networking.  I suspect you'll find this to be the hard bit.  I haven't done it myself. Probably best to do some searching on virtual private networks on this forum. When you can ping from one machine to the other you are ready for the next step.

Second, you need to decide how you want to control the other machine.  vnc might be the right protocol for helping other people with their systems.  That's the simple part - System Preferences: Remote Desktop on your friends computers and Terminal Services Client on your machine.

---

### Post by WinterWeaver on 2007-02-19
Thanks!

I'll start doing some research on VPN's and see if I can get that going.

^_^

---

### Post by WinterWeaver on 2007-02-19
Ok, looks like Network Manager will do the VPN job for me quite nicely. I already had it installed, and it was no problem installing the extra plugin for VPN (Network-Manager-pptp).

I'm not to sure what the next step is though :P ... Luckily I have a buddy in Computer Engineering. I'm sure he can help me set up the VPN. With the correct details etc.

I'll be sure to report back on that which manifests ^_^

TA!

WW

---

