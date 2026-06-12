---
title: "Using ffado with Terratec Phase88 Rack Firewire"
date: 2008-07-29
forum: Ubuntu Studio
---

### Post by babarosa on 2008-07-29
Hello,

I compiled successfully ffado and jack. So now I can use ffadomixer to control the special settings on the Terratec Phase88 Rack FW :)

Now my question:

I can't find the ffado-driver in e.g. ardour's menue or qjackctl (I still can use freebob which works great anyway). Do I have to make additional settings to use the ffado-driver or is ffado a mere mixer-application?

Best wishes and thanks for advices in advance,
Michael

---

### Post by Stochastic on 2008-07-29
ffado is not merely a mixer, it's a firewire soundcard driver.

You should see it in qjackctl listed as 'firewire' not 'ffado', if you don't I'd compile qjackctl from source too, or you can just start up jack via the command line: ```
jackd -dfirewire
``` then open qjackctl and all the other jack-dependent programs your heart desires (you may want to take a look at how to change the default values of jack via the command line too by running jackd --help or jackd -dfirewire --help)

---

### Post by babarosa on 2008-09-20
I solved the problem already by myself.

Regards,
Michael

[I]Edit Oct, 11nd 2008
Do not know where the smiley comes from, i am happy everthing works fine (thanks amongst other things the help from the community).

"I solved the problem already by myself." concerns the strange vanishing and reappearing from module raw1394 that i face from time to time. fiddling around with user's and group's permissions and rebooting generally solves this problem although it is inconvenient (especially when a customer waits besides me or at alive recording occasion).[/I]

---

