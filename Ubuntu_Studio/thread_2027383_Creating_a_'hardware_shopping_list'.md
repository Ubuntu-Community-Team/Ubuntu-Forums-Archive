---
title: "Creating a 'hardware shopping list'"
date: 2012-07-16
forum: Ubuntu Studio
---

### Post by brianmc on 2012-07-16
I'm about to start putting together a shopping list for a new PC. This is to be multi-purposed, but a significant use-case will be with Ubuntu Studio - hence asking folks here.

Ideally I want luggable, and I can easily get a flight case put together. So, I'm thinking I want a half-height tower, or smaller-form case. The pros and cons likely to be related to getting a decent PSU into the box. But, that's not really Linux-relevant.

The 'studio' use cases would be: audio editing (to a lesser extent video editing, but I can live with that not being stellar in it's performance) and, more importantly, recording live. For that, I'd want 16 or 24 channels in, and assume that relevant hardware would also give me MIDI with that. What I don't know is what'd be compatible with Ubuntu Studio, even in a 2-card config, to give me that.

I'd rather not take out a 2nd mortgage to put the machine together so, in addition to considering a couple of cards paired, I'm happy to look at tech that's a few years old. I've used a Terratec DMX6 internal with the CD-bay front panel, that was a great card for it's time, but there must be newer solutions that will meet my needs.

Motherboard-wise, I'm waay out the loop on what'd be best for a smaller form factor. Going into a store and asking, given the planned use, I'm quite leery of being offered something overpriced. I've no qualms about stuffing 8-16GB of RAM in there, and I will be looking to use SSD for storage, but I know some configs will introduce more latency problems than I'd prefer. CPU-wise, I know it'll be the better video editing for more $$$, but there has to be a fair point of diminishing returns.

Graphics-wise, I know pretty much any semi-decent card will support a dual-head option nowadays. But, what have people found good 'n' robust with Linux?

I'm prepared to sacrifice an internal CD/DVD to keep form factor down, and I'd be interested to hear of any custom builds other people have done for 'luggable' live recording systems that wouldn't look out of place in a studio.

Since I'm talking about a good number of mics being fed into the box, a last point I'm wondering on is: Would putting the box onstage and using a remote X session via a crossover ethernet cable be feasible? Could such a setup have a flying faders desk run off the laptop on which the remote X session is pulled up? (I know, may be asking too much with this bit).

Just in case anyone is assuming I *need* all-XLR inputs, I'm capable of putting together the circuitry to drop XLRs (or a stagebox input) down to unbalanced inputs - if that's what the majority of cards have.

---

### Post by sgx on 2012-07-16
People have used pairs of maudio Delta 1010 pci cards.
That would narrow the motherboard search to those with
multiple pci slots.

netjack might be useful to link two setups
on stage, if a hotspot were set up.

google video cards to see if one is problem free
in the linux you'll be using, but be prepared to modify
the plan. The newer video cards with built-in audio, seem to
need some extra attention to configure properly.
Cheers

---

