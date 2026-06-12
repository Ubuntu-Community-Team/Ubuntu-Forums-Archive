---
title: "[SOLVED] Reasons why a video card wont work?"
date: 2008-11-15
forum: The Cafe
---

### Post by chris4585 on 2008-11-15
I wasn't sure where to put this thread...

So I have a issue

I was given a dell precision 450 (yes given) its a beast of a computer with a xeon processor, and a ATI card, the works nearly.  It has two dvi-d outs, so because none of my monitors are dvi-d, I ordered two dvi-d to vga converters, a week later they arrive from Hong Kong, I was so happy to get them when I came home, to find that they are not working with two monitors (I know the monitors work) I'm pretty sure its not the converters (after I got the package I realized I had a dvi-d cord that could go to my samsung monitor)  So I tried that, and nothing... what could be wrong?  I'm guessing the ATI card could be bad? it was in a shed for god knows how long..

---

### Post by steeleyuk on 2008-11-15
Is it possible to try the graphics card in another machine? That should give you your answer. :D

Try reseating the card as well, if you haven't already.

---

### Post by chris4585 on 2008-11-15
> **steeleyuk said:**
> Is it possible to try the graphics card in another machine? That should give you your answer. :D

Try reseating the card as well, if you haven't already.

I'm almost positive its the graphics card, only problem is I don't have any cards I can switch out right now, I guess I'll have to wait

If the gpu fan isn't moving when its powered on, does that tell me anything?

---

### Post by steeleyuk on 2008-11-15
I'm not 100% on ATI cards, they could only spin up when they get to a certain temperature I suppose.

Is the power cable plugged into the card, assuming it needs one? That's often a problem I come across. Its easy to forget that one... :)

---

### Post by chris4585 on 2008-11-15
> **steeleyuk said:**
> I'm not 100% on ATI cards, they could only spin up when they get to a certain temperature I suppose.

Is the power cable plugged into the card, assuming it needs one? That's often a problem I come across. Its easy to forget that one... :)

you mean the cable that goes into the card that has the red, black, yellow colours?

if so then yes

I'm more than likely out of luck until I buy another video card after I find out it is the video card for sure

---

### Post by tom66 on 2008-11-15
Might be a bit risky and damage the card, but get a logic probe and test some exposed pins. Use the ground, e.g. metal shield, as negative.

---

### Post by Tomatz on 2008-11-15
It wont be the converters. They will work out of the box (as do mine). Firstly:

Was ubuntu installed prior to fitting the graphics card?

Is the graphics card set as your primary display adaptor, in the bios?

Do the screens work if plugged into the onboard vga port?

---

### Post by chris4585 on 2008-11-15
> **tom66 said:**
> Might be a bit risky and damage the card, but get a logic probe and test some exposed pins. Use the ground, e.g. metal shield, as negative.

I don't know what a logic probe is, I doubt I have one...

> It wont be the converters. They will work out of the box (as do mine). Firstly:

Was ubuntu installed prior to fitting the graphics card?

not that I know of, probably has win2k, or win xp

> Is the graphics card set as your primary display adaptor, in the bios?

without a monitor I can't see the bios

> Do the screens work if plugged into the onboard vga port?

there is no on board vga port, the reason why I bought converters

---

### Post by Tomatz on 2008-11-15
Well to be honest. I just noticed you said that your gpu fan isnt turning, even at boot. I would advise you to take that card out before it burns out the pcie/agp buss. If it hasn't already :(

---

### Post by chris4585 on 2008-11-15
> **Tomatz said:**
> Well to be honest. I just noticed you said that your gpu fan isnt turning, even at boot. I would advise you to take that card out before it burns out the pcie/agp buss. If it hasn't already :(

ok

If the pcie/agp buss is burnt.. what would I have to do to fix that?   take it to a professional?

---

### Post by tom66 on 2008-11-15
A logic probe is a device which measures for current in binary. If it detects more than 5 volts or a preset voltage, it lights up the 'one' light. If not... then there is nothing going through the pin. Which *could* be a bad thing. Logic probes cost about $25 and you can get one from Radio Shack.

---

### Post by chris4585 on 2008-11-15
> **tom66 said:**
> A logic probe is a device which measures for current in binary. If it detects more than 5 volts or a preset voltage, it lights up the 'one' light. If not... then there is nothing going through the pin. Which *could* be a bad thing. Logic probes cost about $25 and you can get one from Radio Shack.

Thanks for the info

---

### Post by Tomatz on 2008-11-15
> **chris4585 said:**
> ok

If the pcie/agp buss is burnt.. what would I have to do to fix that?   take it to a professional?

Buy a new board :(

Computer parts aren't designed to be repaired.

---

### Post by chris4585 on 2008-11-15
> **Tomatz said:**
> Buy a new board :(

Computer parts aren't designed to be repaired.

I don't think it is, there's a green light that comes on the mobo when its turned on, or does that matter?

buying a new mobo would suck along with a new video card

---

### Post by Tomatz on 2008-11-15
> **chris4585 said:**
> I don't think it is, there's a green light that comes on the mobo when its turned on, or does that matter?

buying a new mobo would suck along with a new video card

The green light just means the board has power. It doesnt mean it works :(

Also usually when the board goes you may as well replace all the hardware (except hdd, DVD/ROM, case and PSU **_(test the PSU first)_**)as a surge may have damaged other components (i.e cpu, ram). These may then damage your new board.

Do you have a multimeter?

---

### Post by chris4585 on 2008-11-15
> **Tomatz said:**
> The green light just means the board has power. It doesnt mean it works :(

Also usually when the board goes you may as well replace all the hardware (except hdd, DVD/ROM, case and PSU **_(test the PSU first)_**)as a surge may have damaged other components (i.e cpu, ram). These may then damage your new board.

Do you have a multimeter?

Ah I see.. I don't have a multimeter, I'll probably take it to someone who knows more of what their doing...  

Thanks for your help Tomatz and everyone else

---

### Post by Tomatz on 2008-11-15
> **chris4585 said:**
> Ah I see.. I don't have a multimeter, I'll probably take it to someone who knows more of what their doing...  

Thanks for your help Tomatz and everyone else

NP

If you do get hold of a multimeter PM me and i can walk you through what to do to find out what is wrong. It may just be the 12v rail on the PSU that is faulty ;)

---

### Post by chris4585 on 2008-11-15
> **Tomatz said:**
> NP

If you do get hold of a multimeter PM me and i can walk you through what to do to find out what is wrong. It may just be the 12v rail on the PSU that is faulty ;)

okay thanks! :razz:

---

### Post by Frak on 2008-11-15
Is your BIOS set to boot from the specified graphics bus?

Oh, and if the port was fried, there would be a high chance that your board would give you the beep codes. Also, instead of testing with a multimeter (dangerous) use a PC-DOCTOR BIOS card instead. It doesn't cost as much as replacing that card.

---

### Post by Frak on 2008-11-15
I'm an idiot who cannot read the OP before posting.

---

### Post by mips on 2008-11-15
At times info available on the internet scares the living daylihhts out of me.

---

### Post by chris4585 on 2008-11-15
> **Frak said:**
> I'm an idiot who cannot read the OP before posting.

It's all good, gave me a laugh though :lolflag:

---

### Post by handy on 2008-11-15
Probably of no use here, but I have found on occasions in the past that rubbing the the contacts on both sides of the card, you know the bits that go into the PCI, AGP, or whatever slot, with a rubber, (no not that kind) the sort you use to rub out pencil on a page, can bring a dead card back to life.

---

### Post by chris4585 on 2008-11-16
> **handy said:**
> Probably of no use here, but I have found on occasions in the past that rubbing the the contacts on both sides of the card, you know the bits that go into the PCI, AGP, or whatever slot, with a rubber, (no not that kind) the sort you use to rub out pencil on a page, can bring a dead card back to life.

wonder why that happens

---

### Post by handy on 2008-11-16
> **chris4585 said:**
> wonder why that happens

Dirty contacts; sometimes people's grubby fingers, other times it may come down to the quality of the metal used on the contacts perhaps exacerbated by the environmental humidity, the metal may oxidize, I really don't know?  

I do know that it has worked for me when I used to fix the rotten little boxes. :lolflag:

---

### Post by chris4585 on 2009-01-02
old post, but I finally got my answer, the other day I bought a $2 video card from a computer shop, got home, stuck the card in, and I got video, windows 2000 was installed, I wiped it off, put ubuntu on it, but I may just put windows 2000 or xp on it for games, after I get a better video card

---

