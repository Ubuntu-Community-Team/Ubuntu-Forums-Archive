---
title: "Trackpoint option for System76 laptops?"
date: 2013-03-17
forum: System76 Support
---

### Post by ttkciar on 2013-03-17
Hello!

I am a long-time Lenovo Thinkpad user, but I don't like the direction they're going with their laptops (they've gotten a lot shoddier and more fragile since they took over the Thinkpad line from IBM), so I'm looking to jump ship to another brand.

I need a laptop which is large, highly capable, and well-supported under Linux.  I'm something of an ogre (6'4" with fingers like sausages), so weight is not an issue, and larger is better (easier to type upon and handle in general).

I thought I'd have to build something myself, but System76's Bonobo Extreme looks *perfect*.

There's just one speedbump:  I really despise touchpads, and have fallen in love with Lenovo's touchpoint (aka "nipple mouse").  It lets me move and click the pointer without taking my fingers off the home row, lets me move the pointer any distance without having to pick up my finger and re-drag, and is more responsive than a touchpad.

I even went and bought Lenovo USB keyboards with the touchpoint device for my desktops at home and the office.

So here's the question:  Is there any way to get System76 laptops with a touchpoint instead of (or in addition to) the touchpad?

If not, would it be at all feasible for me to replace the Bonobo Extreme's stock keyboard with a Lenovo USB keyboard?  I can't tell from the pictures on system76.com how much wiggle-room there is to play with, but from its stated dimensions it seems like it might fit in the X and Y directions.  Less clear is how much room there will be in the Z direction once the stock keyboard is removed.

I'm a second-rate hardware hack, so wouldn't try to mate the Bonobo's keyboard interface with the Lenovo's.  My first thought is to hijack one of the USB ports and wire it to the Lenovo keyboard's USB plug internally, and just leave the Bonobo's keyboard interface unattached.

Might this be at all feasible, or would it cause problems?  And is there even room, once the Bonobo's keyboard is removed and the Lenovo keyboard's case is removed?

---

### Post by kurt18947 on 2013-03-17
I too prefer the trackpoint over the pad only.  Actually, I prefer the ultranav, both devices have their place.  Some Dells have similar to the ultranav and I believe some HP may as well though I'm not certain about current HP.  I'm sorry to hear about Thinkpads being cheapened though it's not a surprise.

---

### Post by isantop on 2013-03-18
We're not really evaluating options for trackpoints right now, since there really isn't enough demand for them on consumer laptops.

---

### Post by ttkciar on 2013-03-18
> **isantop said:**
> We're not really evaluating options for trackpoints right now, since there really isn't enough demand for them on consumer laptops.

That's what I anticipated, which is why I was asking questions about the feasibility of swapping the keyboard out myself.

If someone could tell me the three dimensions of the Bonobo keyboard (especially depth), and whether the laptop will boot with the keyboard interface disconnected, I would appreciate it greatly.  It would help me decide whether I want to buy a Bonobo.

Thanks much,
-- TTK

---

### Post by isantop on 2013-03-18
It does use a special mounting system; I'm not sure there are any 3rd party keyboards that would be compatible.

---

### Post by ttkciar on 2013-03-18
> **isantop said:**
> It does use a special mounting system; I'm not sure there are any 3rd party keyboards that would be compatible.

I'm happy to do the dremel and layup work myself to shoehorn it in, and don't care if the end result is pretty.  I just want to be sure there's enough room to make it feasible in the first place.  If I were closer, I'd drive to your location and stick a caliper in a Bonobo myself, but since I'm in California, perhaps someone there could do this for me?

What I'd need is:
    * A photograph of a bonobo with the keyboard removed,
    * A measurement of the depth of the space in the bonobo where the keyboard is housed,
    * Someone to try booting the bonobo with its keyboard removed (unplugged from the internal keyboard's electrical interface), but with a USB keyboard plugged into one of its USB sockets, to see if the boot process completes normally.

If that's above and beyond the call of duty, I totally understand.  Kudos in any case for making such an excellent product.

Thanks,
-- TTK

---

### Post by isantop on 2013-03-18
It doesn't have electrical connections required for a trackpoint either. It's simply not supported on the Bonobo.

---

### Post by ttkciar on 2013-03-18
> **isantop said:**
> It doesn't have electrical connections required for a trackpoint either. It's simply not supported on the Bonobo.

Yes, this is why I would hijack a USB port, like I stated previously.  A lenovo USB keyboard with an integrated trackpoint device works on any system supporting use of USB keyboards and USB mouse devices.

Sorry this is so confusing.  I should have done a better job of explaining it.

EDIT:  Yes, I understand that I am trying to do something crazy and unsupported.  Yes, I do know how to do it.  I just need a little information, easily obtained.  Yes, I am asking you to do me a weird favor, and totally understand if it's not going to happen.

-- TTK

---

### Post by isantop on 2013-03-19
I see.

There isn't physically room for a keyboard thicker than the stock one (about 5 mm at the thickest). There also isn't a way to acces the USB ports from inside the system. There just isn't space inside the laptop to do what you're trying to do.

---

### Post by ttkciar on 2013-03-19
> **isantop said:**
> I see.

There isn't physically room for a keyboard thicker than the stock one (about 5 mm at the thickest). There also isn't a way to acces the USB ports from inside the system. There just isn't space inside the laptop to do what you're trying to do.

Thank you.  Since the lenovo keyboard case is less than 10mm thick, it's possible that it might be less than 5mm once the case is removed.  I'll open one up and see.  A more precise measurement of the bonobo's cavity would be nice, but maybe this is all I'm going to get.

I expect the USB sockets are either connected via PET ribbon cables or soldered directly to the motherboard.  Either way, it should be possible to get at them with a little work.

---

### Post by isantop on 2013-03-19
I have disassembled the system. It's 7mm thick, and that doesn't count room for clearance. That said, there isn't any clearance on the side, bottom, or top. In addition, the motherboard is exposed when the keyboard is removed, so you'll need to ensure the keyboard installed is exactly 35cm by 10.8cm.

I should also point out that this sort of modification will void your system warranty, and we can't cover any system damage caused. 

You also wouldn't be able to disable the built-in trackpad, since in order to do that, you need to use the default keyboard (The trackpad toggle isn't persistent across reboots).

I'm really not trying to be harsh, but you're about to perform irresverible modifications to a $1500+ laptop with very little chance of success. It's extremely likely that the laptop will not be recoverable after this attempt, and since it wouldn't be covered under warranty, your only option would be to buy a new one entirely or front very large repair costs. I'm very sorry, but it simply isn't possible to have a trackpoint built-in to the Bonobo.

---

### Post by GeneSalamin on 2013-03-19
Perhaps you would have better luck from the other major linux vendor, ZaReason.  They have expressed a willingness to build custom systems.  This way you can get a yes/no decision on buying a guaranteed linux compatible laptop to your liking.  Good luck.  I too hate trackpads, and I use an external mouse instead.

---

### Post by ttkciar on 2013-03-19
> **isantop said:**
> I have disassembled the system. It's 7mm thick, and that doesn't count room for clearance. That said, there isn't any clearance on the side, bottom, or top. In addition, the motherboard is exposed when the keyboard is removed, so you'll need to ensure the keyboard installed is exactly 35cm by 10.8cm.

Thank you!  That is extremely useful information.

You clearly think I'm nuts, but actually measuring something is unbelievably helpful by tech support standards.  Kudos to you, sir.

> I should also point out that this sort of modification will void your system warranty, and we can't cover any system damage caused.

Duly noted.  If it doesn't work out, I won't come crying for money, repair, or replacement.

> You also wouldn't be able to disable the built-in trackpad, since in order to do that, you need to use the default keyboard (The trackpad toggle isn't persistent across reboots).

Do you think the laptop boots normally if the touchpad's electrical connection is simply disconnected?  I know some laptops do, but BIOS startup logic differs from model to model.

> I'm really not trying to be harsh, but you're about to perform irresverible modifications to a $1500+ laptop with very little chance of success. It's extremely likely that the laptop will not be recoverable after this attempt, and since it wouldn't be covered under warranty, your only option would be to buy a new one entirely or front very large repair costs. I'm very sorry, but it simply isn't possible to have a trackpoint built-in to the Bonobo.

I've been taking apart and putting together computers since 1982, so if I mess it up beyond my ability to repair it, then I deserve to lose my $1500.  You're not coming across as harsh at all, just telling it like it is.

Thanks again,
-- TTK

---

### Post by jawilljr on 2013-03-19
I have a Bonox6, but I am not willing to void my warranty. but [here is a post that has the service manual](http://forum.notebookreview.com/sager-clevo-reviews-owners-lounges/685692-official-clevo-p370em-sager-np9370-owners-lounge-68.html#post9007185)

---

### Post by isantop on 2013-03-20
> **ttkciar said:**
> Thank you!  That is extremely useful information.

You clearly think I'm nuts, but actually measuring something is unbelievably helpful by tech support standards.  Kudos to you, sir.



Duly noted.  If it doesn't work out, I won't come crying for money, repair, or replacement.



Do you think the laptop boots normally if the touchpad's electrical connection is simply disconnected?  I know some laptops do, but BIOS startup logic differs from model to model.



I've been taking apart and putting together computers since 1982, so if I mess it up beyond my ability to repair it, then I deserve to lose my $1500.  You're not coming across as harsh at all, just telling it like it is.

Thanks again,
-- TTK

I have no idea if the system will boot without the trackpad connected.

At this point, this project is far beyond the scope of something I can support. I can't provide any more help with this.

---

### Post by rewyllys on 2013-11-27
> **ttkciar said:**
> Hello!

I am a long-time Lenovo Thinkpad user, but I don't like the direction they're going with their laptops (they've gotten a lot shoddier and more fragile since they took over the Thinkpad line from IBM), so I'm looking to jump ship to another brand. . . . There's just one speedbump:  I really despise touchpads, and have fallen in love with Lenovo's touchpoint (aka "nipple mouse").  It lets me move and click the pointer without taking my fingers off the home row, lets me move the pointer any distance without having to pick up my finger and re-drag, and is more responsive than a touchpad. . . . 

[Emperor Linux]("http://emperorlinux.com/") offers certain Lenovo Thinkpads running Linux.

---

