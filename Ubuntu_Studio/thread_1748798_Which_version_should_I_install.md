---
title: "Which version should I install?"
date: 2011-05-03
forum: Ubuntu Studio
---

### Post by Grone1985 on 2011-05-03
Hi everyone!
I got a new laptop (Samsung RV411, Intel Core i3, 2 GB RAM, NVIDIA GEFORCE 315M) and want to install UbuntuStudio on it for music production mainly. What I would like to know is which version should I install? Lucid, Maverick or Natty? 32 or 64bit?

---

### Post by cbanakis on 2011-05-03
64bit does have a few benefits, but if your new to ubuntu, it can be a pain to get some 3rd party programs to work.

When I first started using linux, I used 64bit, and getting the light-scribe software to work took some doin.
On 32bit it just worked.

I would go with Maverick.

Lucid is older, and I have noticed a few things that work in Maverick, that did not work in Lucid (Such as my scanner)

And Natty is brand new.  (Still might have some bugs to work out)

I'm running Natty, and all seems well, but I have seen a lot of threads on here, basically saying...
"How Come (Bla Bla Bla) doesn't work anymore in Natty"

Its the classic Goldilocks and the Three Bears scenario.

This one is too new.
This one is too old.
But this one is just right.

---

### Post by Grone1985 on 2011-05-05
Anyone else? What about rt- or low latency kernels? Do I need those to be able to record from my guitar without xruns? Which versions have them available?

Thanks!

---

### Post by jejeman on 2011-05-05
I have 10.04 64bit on my computer in the studio. It comes with preempt kernel and it's working fine and stable. I'm using it with firewire card.
I've just instaled 11.04 64bit on my other computer and got xruns with generic kernel which comes by default. But with abogani's lowlatency kernel there are no xruns. 11.04 is also working quite fine in general. Here I have pci audigy2 card.

Since you have new laptop, maybe it's better for you to install 11.04 because of network manager, support for the new hardware. 10.04 does not have network manager, which is pretty handy for laptops. Of course you can always set network by hand, no big deal.

64bit can be little tricky for some programs. There is not that much benefit over 32bit in performance (it is faster somehow), but I've been using it since 9.04. Personaly don't see the reason why not, since hardware can support it.

---

### Post by Lanathel on 2011-06-06
better to install as fresh as possible, for 2Gb i would like to use 32 bit OS, but this lappy can install up to 8G, 64 bit can be a benefit, anyway, its more a personal taste

the problem you can have - backlight, it does not work, so you will have your screen as bright as it can, everytime,
if you use kernel param acpi_backlight=vendor , then you can set brightness in grub menu before booting

tricks can be
1) edit dsdt
2) find a proper way to set brightness with setpci

i havnt found yet, so far

---

### Post by Grone1985 on 2011-06-06
Yes thanks! I ended up installing the 64bit. I heard about the backlight problems but oh well, most things work so I can deal with that for now. Thanks for all your answers!

---

