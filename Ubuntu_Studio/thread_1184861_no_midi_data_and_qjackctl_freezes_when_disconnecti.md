---
title: "no midi data and qjackctl freezes when disconnecting midi port"
date: 2009-06-11
forum: Ubuntu Studio
---

### Post by MisterBark on 2009-06-11
Hi !

I got Ubuntu Studio (Ubuntu 8.10 normal version, upgraded to Ubuntu studio) on a Pentium4 with 2GB.
linux 2.6.27-3-rt
jackd version 0.109.2
qjackctl version 0.9.10

A M-audio audiophile 24/96 soundcard (with 1 midi in/out)

[B]I got 2 problems :

1- I can see the maudio midi in and out in jack connections, but there's no data[/B]

In qjackctl / connections / alsa, I can see the midi input of my m-audio audiophile, I can connect it to a software (i.e. rosegarden or linuxsampler) but no data arrives !
I'm 100% sure there's data in my input, on the channels expected by the softwares.
The audio routing works fine.

If I route midi from rosegarden to linuxsampler, just to test with a mouse made track, the midi is correctly forwarded.

That's why I think there's a midi data problem with the audiophile drivers, or jack doesn't like the audiophile midi input.

**2- when I disconnect the midi in, in qjackctl connections, qjackctl freezes !**

Exactly when I click on "disconnect" (i.e. audiophile to rosegarden midi connection) qjackctl freezes (the window is not redrew anymore) and there's absolutly nothing in the terminal if I run qjackctl with it.
If I kill qjackctl, a few process of jackd are "unkillable" (even with kill -9). If I restart qjackctl, it freezes at startup.
Then, the only one solution is rebooting !

THANKS A LOT in advance for your enlightenments ! :p

---

### Post by MisterBark on 2009-06-16
Hi !
sorry to up the topic but anybody has an idea ? :(

just for the first or second problem ! :-\

---

