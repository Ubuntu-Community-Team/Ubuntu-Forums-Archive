---
title: "Transparent Ubuntu virtualization in Windows possible/worth it?"
date: 2011-02-09
forum: Virtualisation
---

### Post by gibber1sh on 2011-02-09
I have been running Ubuntu 10.04 as my main operating system for a few months and like it very much. However, I'd like to be able to play Windows games (and to a lesser extent use flash and watch video more comfortably). I've tried running a virtual Win7 with my Ubuntu as host for this, but it isn't really able to handle most Direct3D games (yet?).

So right now I am thinking of doing it the other way around: running an Ubuntu guest on a Win7 host, with the guest as my main OS. I'm hoping the functionality/ease of Ubuntu won't be impaired by the virtualization, and the direct hardware access will let me do anything I want in Windows.

Before I do this, however, I have some questions:

- Can this be done somewhat transparently (as in automatically running a windows script on boot that starts up the Ubuntu VM fullscreen)? 

- Will this cause any problems in Ubuntu with regards to networking?

- Would I still be able to smoothly run Compiz (with my not-so-beefy graphics card) virtually?

- Any other possible issues I should know about?

- And most importantly: is it possible to backup/transfer my host Ubuntu configuration/applications/data to the virtual one?

My apologies if this has been asked before.

---

### Post by P4man on 2011-02-09
> **gibber1sh said:**
> 
- Can this be done somewhat transparently (as in automatically running a windows script on boot that starts up the Ubuntu VM fullscreen)? 


Yeah. Check out the virtualbox documentation how to start a VM from the command line, then put that in a batch file or whatever windows uses these days.
> 
- Will this cause any problems in Ubuntu with regards to networking?


Hopefully not :)

> - Would I still be able to smoothly run Compiz (with my not-so-beefy graphics card) virtually?

No :(
And videoperformance will be pretty damn poor in general.

- Any other possible issues I should know about?

> - And most importantly: is it possible to backup/transfer my host Ubuntu configuration/applications/data to the virtual one?


In theory, yes.  Google around for that, there are solutions.

---

