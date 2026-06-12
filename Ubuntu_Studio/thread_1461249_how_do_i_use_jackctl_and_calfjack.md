---
title: "how do i use jackctl and calfjack?"
date: 2010-04-24
forum: Ubuntu Studio
---

### Post by zander1013 on 2010-04-24
hi,

i have them running and aparently working but i can't figure out how to get them to work together using a guitar interface.

please advise.:guitar:

---

### Post by sgx on 2010-04-24
Hi, to connect my guitar, I use a hardware fx unit, or digital amp with line-out, connected to soundcard line in. In qjackctl, line-in is the
left side of the Audio tab, labelled System. Click the widget to the left of System, and the list expands to reveal your system capture ports,
the line-in connectors on your card. I assume other interfaces should show
up there.

You also may need to select your interface by the 'Input device'
line in the middle far-right of the qjackctl setup page, click the  >
widget to see what devices your system can see.

Now when I start rakarrack fx processor, it appears in both the left and right sides of the audio pane. I connect rakarrack on the right, to
System on the left. Now turn on the rakarrack fx button, and its
rockstar on the hoof! 

I don't have the calf setup, but I'd be amazed if it would not work in
the same way. Calf on the right --> System on the left. Rakarrack is amazing, so at least you can use that.

Cheers :)

If problems persist, post your gear list to help folks aim their knowledge your way.

---

### Post by zander1013 on 2010-04-24
ty for your help,

i have a zoom g2 as the guitar interface plugged into the usb port. i can get it to play through jackctl okay.

when i start calf jack and select a plugin i get two new icons in the jack audio connection kit but selecting them as you described does not seem to have any effect but i can see the signal in the vu meters of calf. other combinations are no signal and feed-back.

my computer is an ibm thinkpad t60 (circa 2006) there seems to be some unwanted distortion when i play some patches from the g2 which could simply be from the speakers on the laptop being poorly voiced for guitar.

perhaps there are some settings in Sound Preferences>Hardware,Input,Output tabs that could clean up the sound some?

what compiler packages do i need to compile rackarrack please?

---

### Post by zander1013 on 2010-04-24
system output -> calf inputs, calf output -> system inputs.

that turned the trick :)

---

### Post by sgx on 2010-04-24
> **zander1013 said:**
> system output -> calf inputs, calf output -> system inputs.

that turned the trick :)
JAMIN! I saw a nice video on youtube  showing calf used with patchage, ardour etc, among other things. It started out slow, but got better as it went along. The youtube pic pic is bright green on top, red on the bottom, with a lizard. Lots of videos using ardour, hydrogen, zynaddsubfx...

Don't forget to try Rakarrack! :)

---

