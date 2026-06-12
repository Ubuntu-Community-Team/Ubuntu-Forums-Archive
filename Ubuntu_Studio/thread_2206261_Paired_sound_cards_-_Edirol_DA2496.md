---
title: "Paired sound cards - Edirol DA2496"
date: 2014-02-18
forum: Ubuntu Studio
---

### Post by brianmc on 2014-02-18
I have a pair of Edirol DA2496 cards and breakout boxes; these give me 8 channels each, and are linkable via a word-clock cable on the rackmount breakout boxes - or with a jumper cable between the cards.

What's got me scratching my head is how to make the two cards appear as a single 16 in/out card to Jack. From what I've read, this is a matter of writing some bits of alsa configuration - but, as I'm sure others are familiar with - the documentation is head-scratchingly well-nigh incomprehensible. I've seen an old example or two for pairing RME Hammerfall cards, but they're a dialect of geek I don't grok.

I'm using Ubuntu Studio 64bit 13.10 as the base operating system, but I don't think that's a major stopping point here.

I know I'll likely have to supply additional information on this, and I'm not adverse to getting my hands dirty and recompiling stuff. These are great pieces of kit, which I've managed to run reliably at 4ms latency when using just the one card. Getting both running together will turn what I've got into a pretty serious piece of kit, so any help on this would be greatly appreciated.

The Roland page on the cards can be found here: [http://www.roland.com/products/en/DA-2496/](http://www.roland.com/products/en/DA-2496/) But, don't click on the specification and expect anything more than a chuckle; it looks as if someone has hacked those bits or Roland never filled in the details.

---

### Post by CrocoDuck on 2014-02-18
Hi! I never tried to use multiple soundcards, but I've collected some informations some time ago when I was considering to purchase one or more than one M-Audio Delta 1010. It is possible, but you have to create your personal asoundrc file. Here what is it: [http://www.alsa-project.org/main/index.php/Asoundrc](http://www.alsa-project.org/main/index.php/Asoundrc) . Also, some infos are here: [http://jackaudio.org/multiple_devices](http://jackaudio.org/multiple_devices) . Maybe you could try to use the asoundrc for the multiple M-Audio Delta 1010 as a base/guide. Here the links I've found: [http://www.jrigg.co.uk/linuxaudio/ice1712multi.html](http://www.jrigg.co.uk/linuxaudio/ice1712multi.html) , [http://www.ilovemyjournal.com/?action=view_entry&eid=4773](http://www.ilovemyjournal.com/?action=view_entry&eid=4773) , [https://community.ardour.org/node/4653](https://community.ardour.org/node/4653) .

---

### Post by brianmc on 2014-02-18
Not so much 'use the Delta 1010 as a base/guide', more-likely just drop it straight in. M-Audio actually designed the cards for Roland's AD2496, but with a few extras like the jumpers to sync the cards, and DIP switches to define consistent card numbering. Crazy thing is, the Delta 1010 cards consistently go for more on Ebay, but have more features on the rackmount component.

Probably going to need a CPU upgrade to get this running optimally, though. Using just one card with Jack 'idling' sits at just under 20% CPU usage; I'll need a bit more spare capacity for DSP and whatnot.

Thanks for those *extremely* useful links!

---

