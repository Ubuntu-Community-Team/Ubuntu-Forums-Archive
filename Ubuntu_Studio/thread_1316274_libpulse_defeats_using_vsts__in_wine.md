---
title: "libpulse defeats using vsts  in wine"
date: 2009-11-05
forum: Ubuntu Studio
---

### Post by sgx on 2009-11-05
Suddenly, I had problems using wine to run Reaper and Cantabile, their jackd thread would immediately zombify, although native apps like zynaddsubfx worked fine in the same session. After much futile experimenting, I checked my installed programs in synaptic, and discovered

libpulse

had been installed as a depencancy of mplayer, which I recently installed! :mad: :mad: :mad:

So I used synaptic to remove libpulse, rebooted, and once
again, I could use wine, Reaper, and Cantabile to host vsts in linux.

It is time for everyone to demand that all pulse audio code be removed from mainstream linux distributions, and that clear warnings are attached
to any downloads that include such code. Mplayer, sox, and K3b also were removed with libpulse, so I highly recommend coders in those projects to quickly remove dependant code, if any exists, or contact packagers/distribution managers to remove dependant status, if it is not really needed.

---

### Post by AutoStatic on 2009-11-06
I'm not with you sgx, on the contrary, I think it's a good thing that most distro's have chosen for PulseAudio. It's the folks at Ubuntu that mess up every now and then: [http://0pointer.de/blog/projects/pa-in-ubuntu.html](http://0pointer.de/blog/projects/pa-in-ubuntu.html)
Just read some relevant articles on [Lennart's blog]("http://0pointer.de/blog"). PulseAudio has the future in my opinion and besides what are the other options? ESD? OSS? Forking PulseAudio? JACK? PortAudio? Creating something new, complicating the state of audio in GNU/Linux even more?

---

### Post by sgx on 2009-11-06
Pulse is an ambitious pre-alpha project that has foolishly been pushed into the linux audio mainstream, which 'mainstream', by its very nature (unpaid developers kindly releasing rolling beta projects for many years), can hardly benefit from such inclusions. The result is legions of
dissapointed linux audio users, who attempted and failed with complex configurations that would challenge the coding skills of the highest paid commercial vendors. People that tried and failed to configure linux audio are quite vocal, and insure that linux will be considered highly unstable and unfit for use, by typical musician communities using mac or win xxx based computers. I gave one example of libpulse inadvertantly blocking use of audio industry standard vsts in a wine environment. Lots of beta software in that scenario. But I can play and record vst music without the pulse software, and I recommend it be removed by anyone who does not actually need it for a specific audio purpose.

---

### Post by AutoStatic on 2009-11-06
> **sgx said:**
> Pulse is an ambitious pre-alpha project that has foolishly been pushed into the linux audio mainstream, which 'mainstream', by its very nature (unpaid developers kindly releasing rolling beta projects for many years), can hardly benefit from such inclusions.Come on, the upcoming Nokia N900 will be shipped with PulseAudio too: [http://www.techworld.com.au/article/320807/open_source_identity_pulseaudio_creator_lennart_poettering](http://www.techworld.com.au/article/320807/open_source_identity_pulseaudio_creator_lennart_poettering) That's a high-end phone, do you really think Nokia would use a "pre-alpha project" for their flagship?

> **sgx said:**
> The result is legions of
dissapointed linux audio users, who attempted and failed with complex configurations that would challenge the coding skills of the highest paid commercial vendors.Aren't you exaggerating a bit? Is it really that bad? Point me out a relevant thread if possible.

> **sgx said:**
> People that tried and failed to configure linux audio are quite vocal, and insure that linux will be considered highly unstable and unfit for use, by typical musician communities using mac or win xxx based computers. I gave one example of libpulse inadvertently blocking use of audio industry standard vsts in a wine environment. Lots of beta software in that scenario. But I can play and record vst music without the pulse software, and I recommend it be removed by anyone who does not actually need it for a specific audio purpose.Then don't use PulseAudio! You're completely free to do so! I'm not a PulseAudio advocate, I don't use it on my main audio production machine, but your point of view is groundless and biased if you ask me.

Sorry I let myself go a bit but to be honest, a thread like this is an invite for a vivid discussion ;)

---

