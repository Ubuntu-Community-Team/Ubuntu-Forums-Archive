---
title: "Questions about VGA passthrough"
date: 2012-09-01
forum: Virtualisation
---

### Post by sonnet on 2012-09-01
I'd like to set up a vm and assign to it a discrete vga (pci-e) and possibly a soundcard.
My understanding after reading for days about it, is that XEN is the best solution to do that. Now before to buy the wrong/unnecessary hardware , I'd like to have some point cleared possibly by someone who already had to deal with those issues.
My questions are:
1-Can I use integrated vga (intel sandy bridge) for the dom0 (the ubuntu installation) and the discrete one for the domU (in my case, Windows 7 virtualized in the VM)? I read that Xen can assign the primary graphic adapter (defined as the one with which you start the system) and not the second one, which seems a bit weird. So maybe I musnderstood.

2-A big issue (apparently, unless I misunderstood) is that I will have to assign physically a number of cores to the domU which then won't be utilized by the dom0, and that will be permanently (since the domU will start every time I start the dom0 automatically). **_Isn't possible to make so that the 2 machines share the cpu resources dinamically _**(menaning allocating up to 100% of the whole cpu resources, based on the contingent needs of one or the  other?)

3-Can the same as at question number 2 be applied to the RAM?

Questions about KVM:

A-Did anyone tried vga-passthrough with KVM with Debian/Ubuntu/Mint? Is yes, do you know any guide about it? So far I found one ,but it's based on fedora (which might not be much different from Ubuntu, but still..)


B-Do the preoblems relative to point 1, 2 and 3 apply with KVM too?

---

