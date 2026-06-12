---
title: "Control Softsynths running in Ubuntu Studio in VMWare etc. from Host System?"
date: 2008-07-31
forum: Ubuntu Studio
---

### Post by tilllt on 2008-07-31
Hello,

maybe this seems like a weird question to ask but i am running Ubuntu Studio in VMWare Fusion on a Macbook Pro Running OS X 10.5

I wonder how i can make programs running in the Host (i.e. Pure Data) to control Softsynths etc. running in the Ubuntu Studio in the Virtual Machine. Is this possible?

cheers

---

### Post by tilllt on 2008-08-02
no one?

---

### Post by tilllt on 2008-08-13
For example you want to play a software synth in Ubuntu Studio running in a VMWare from Ableton Live running in OSX / Windows ... I was thinking about converting Midi to OSC Data and sending it over the Network. I guess that could be done with Pure Data (PD) but i am not very good with pd, yet.

---

### Post by Stochastic on 2008-08-13
I'm pretty sure you'll need to setup a network system for this.  Unfortunately I'm not very familiar with VMWare, so I'm not sure of any details.  I'd look into how VMWare works with networks, and then once the network is setup, come back and ask how to get the right data from one end to the other.

---

### Post by tilllt on 2008-08-14
i have setup VMWare to provide an emulated nic which is NAT´ed to the Host System. Networking is not so much the problem. The problem is, i.e. that Ableton Live (Running on OSX Host) does not have an OSC option, only Midi... Like i said, probably it would be possible to locally send Midi Data from Live -> Pure Data, let PD convert it to OSC, send it over Network to Ubuntu Studio in VMWare, Let PD convert OSC to Midi again... Or do you have a simpler idea?

---

