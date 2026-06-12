---
title: "The PhysX Card...droool..."
date: 2006-10-02
forum: The Cafe
---

### Post by bonzodog on 2006-10-02
Ageia have just announced the release of their first production PhysX GPU PCI-E Card. The power of this beast is awesome, and it seems linux support is already in the SDK.
[Article here]("http://www.reghardware.co.uk/2006/10/02/ageia_pcie_x1_physx_card/")

---

### Post by moeFinley on 2006-10-02
I don't think PhysX are going to be around for long.  Apparently their card doesn't make much difference with current games and when DirectX 10 comes out any DX10 GPU will be able to handle physics. :-k 

The support for Linux in the SDK is interesting though.  Does Linux get used alot for game development?

---

### Post by zachtib on 2006-10-02
> **bonzodog said:**
> Ageia have just announced the release of their first production PhysX GPU PCI-E Card. The power of this beast is awesome, and it seems linux support is already in the SDK.
[Article here]("http://www.reghardware.co.uk/2006/10/02/ageia_pcie_x1_physx_card/")

neat, i clicked on this thread fully ready to slam it with "No Linux support!!!!!1111oneone" but apparently, that isn't the issue.  Now if only PhysX would demonstrate that it actually accomplishes something, I may consider buying one.

another question, how open is the SDK for PhysX, i mean, could anyone up and use a PhysX card on a project, or do they need something special from AGEIA?  It seems like this would be really cool, not necessarily for games, but for all sorts of physics simulation programs, and even 3d modelers

---

### Post by EdThaSlayer on 2006-10-02
> **bonzodog said:**
> Ageia have just announced the release of their first production PhysX GPU PCI-E Card. The power of this beast is awesome, and it seems linux support is already in the SDK.
[Article here]("http://www.reghardware.co.uk/2006/10/02/ageia_pcie_x1_physx_card/")

niiiiicceeee...except it is pretty useless if i dont play a game that has a lot of physics...and are there a lot of linux games with physics???...it might work out for now but will gradually dissapear as CPU's become far more powerful--but just think how this card will help speed up all the physics calculations scientists usually do!

---

### Post by Pathfinder_ on 2006-10-02
with quad-cores coming out and ati+nvidea trying to make their GPUs do physics i don't think these will ever be usefull.

---

### Post by PriceChild on 2006-10-02
The idea though is that its not just for Physics though is it?

I'm sure that the idea is to make custom apps which can use the card as another processor for anything. Physics just being what its optimized and most useful for.

---

### Post by raublekick on 2006-10-02
> **moeFinley said:**
> I don't think PhysX are going to be around for long.  Apparently their card doesn't make much difference with current games and when DirectX 10 comes out any DX10 GPU will be able to handle physics. :-k 

The support for Linux in the SDK is interesting though.  Does Linux get used alot for game development?

Seems somewhat unfair to judge it based on current games. Current games aren't made to take full advantage of it because the card is not a standard need that everyone will use, and it's also such a new technology that it would be hard to take full advantage of it at this point. 

I agree with zachtib, it could be really useful for simulations at stuff. One of the big issues with 3D and physics is that physics is very dependent on mass, but how 3D objects don't have a mass, so they have to be artificially assigned one, and I would think that most basic physics calculations in games and such don't even bother. But instead of making animations to make it look like a guy is jumping across a building when you press the jump key, they could change it so that the character has a bunch of point-masses, and when you press the jump key, a force is applied to one or more of the point-masses, and the PhysX card calculates the effect on the rest of the character system, making an almost infinite number of possible animations without having to explicitly create any by hand.

---

### Post by weematt on 2008-05-02
All of the blurbs I've seen about the card seem to suggest that HW support for PhysX cards is *only* available on the Win platform...that you can simulate it in Linux (whoopydoo) but that hardware support is not yet there for linux.

Have any of you seen evidence to the contrary?

from   [http://www.ageia.com/physx/faqs.html#10](http://www.ageia.com/physx/faqs.html#10)

The PhysX Accelerator and AGEIA PhysX system software require a PC running Windows XP Pro, Home or Media Center Edition or Windows Vista with the most recent service pack installed, a minimum of 512 MB of system memory, a vacant PCI expansion slot, at least 50MB of free hard disk space and an additional 4 pin molex power connector (most systems will have one available, if your system does not, a Y-adapter can be used).

Note that requirements to run specific PhysX-enhanced game titles will vary and should always be followed for the best possible game play experience.

177E

---

### Post by skymera on 2008-05-02
Nvidia own Ageia, and from what i've read i think they've added Ageia PhyX technology into the 9 Series Nvidia cards.

So the PhyX card is obsolete really with DirectX10 and Nvidia

---

### Post by rajeev1204 on 2008-05-02
> **skymera said:**
> Nvidia own Ageia, and from what i've read i think they've added Ageia PhyX technology into the 9 Series Nvidia cards.

So the PhyX card is obsolete really with DirectX10 and Nvidia



Yep.

---

