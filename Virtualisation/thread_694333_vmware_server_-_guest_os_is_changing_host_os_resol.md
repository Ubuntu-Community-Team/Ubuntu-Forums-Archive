---
title: "vmware server - guest os is changing host os resolution on exit."
date: 2008-02-11
forum: Virtualisation
---

### Post by finnclipp on 2008-02-11
Hi there, I'm fairly new to linux and very new to forums, so please bear with me.

I'm running vmware server on a few Ubuntu 7.04 boxes, some of which are producing an interesting problem for me.  When I shutdown the guest os win98se (don't laugh) or winxp the host machine is left rendering at the resolution the guest was last at.  In the case of the 98se machine, this is about 512x384 due to the shutdown screens.  The host thinks it's still at 1024x768, a resolution change and cancel sets the machine back to where it should be.

The same thing happens when you ctrl-alt out of fullscreen.  taking all screen settings along for the ride.  and how do you stop the guests from using interlacing at 1024x768? cause that's just mind bending for office work.

All the guests have vmware tools installed, hosts are mixed AMD and intel, all over 2GHz with a gig of ram each.

Any help would be greatly appreciated,  Thanks.

---

### Post by fjgaude on 2008-02-12
Have tried using the VM Edit/Preferences/Display options?

One or both may change what you are getting.

---

### Post by finnclipp on 2008-02-12
Sadly neither option has yielded results any different, the resolution issue seems fairly deeply rooted.

Turning off most of the toolbars and setting the remaining controls to "text only" appearance has rendered the machines useful in windowed mode.  I may just use them like this until times end.

Though I must say, I'm pretty impressed with this software.  It is powerful stuff.

Cheers for the help.

---

### Post by fjgaude on 2008-02-12
This issue you have likely has to do with your video board. What kind is it?

---

### Post by finnclipp on 2008-02-12
I'd thought the same, but one of the machines doing it has a Matrox millenium g550 , one has a Nvidia geforce 6200  and one is running an onboard pci based chipset of some kind (I could check what type, but I think you get the idea).  The machines have fairly large hardware diversities, and then again, I have two more just like the Nvidia machine that are working properly on identical hardware, drivers, and software.  Perhaps I broke something way down in the configuration, I just can't imagine what.

I'm stumped anyway.  And I have too many machines, but it makes for an interesting troubleshooting sample.

---

### Post by fjgaude on 2008-02-12
Well, you have the option of reinstalling vmware and starting over, carefully watching what happens as you go.

I have always used the server version directly from the vmware.com web site and use the same license number over-and-over.

If you find out what the problem is, let us know. It could help others.

---

### Post by finnclipp on 2008-02-12
I'll keep at it, and if I find a solution, or a method to avoid this at install, I will post it here.  I will add that I have also always used the file directly from vmware.com though I have used different keys for each machine.

Thanks for all the help.

---

