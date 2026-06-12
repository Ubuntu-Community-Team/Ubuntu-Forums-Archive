---
title: "Big push for FOSS apps / driver replacements?"
date: 2007-11-02
forum: Ubuntu Brainstorm
---

### Post by spoons on 2007-11-02
Hey!

There's starting to get some good closed-source nVidia and ATI drivers now, but no good free-software ones.
Also, software like Gnash is coming along, but it's not nearly as good as the official player. Since GNU/Linux is all about freedom, why not have a big push for "free" alternatives to binary blobs?

Thanks for any replies. :biggrin:

---

### Post by pay on 2007-11-02
Theres nouveau and radeonHD that are being developed  which will both offer 3d acceleration and there already is the =<r400 driver that offers 3d acceleration for radeon cards. We just need abit of time for these products to mature and for ati to release some more specs for their cards.

---

### Post by coolen on 2007-11-03
FOSS community support FOSS alternatives to non-FOSS drivers and software? Now why didn't I think of that?

Sorry, but this is already being worked on (the fact that these projects exist should make that obvious).

---

### Post by spoons on 2007-11-03
I know projects exist, what I'm saying is why doesn't Ubuntu help them along? That way they'd be ready quicker.

---

### Post by smartboyathome on 2007-11-03
> **spoons said:**
> I know projects exist, what I'm saying is why doesn't Ubuntu help them along? That way they'd be ready quicker.

Even Canonical doesn't have an infinate supply of developers. Ubuntu has a few paid developers, but the majority of develpoers (as I understand it) are volunteer.

---

### Post by amiga_os on 2007-11-03
What would be the best way for users to help?  Probably to use the FOSS apps and make sure we're careful and deliberate about bug reporting.

Having said that, I'm a hobbyist programmer, but I've never had any formal training, and the amount of time and effort required to get my head around trying to start helping with FOSS projects is a nightmare.  Something like Launchpad is a start, making it clear what different goals there are going on, but even then the learning curve is huge.

If there was a simple way that people like me could start contributing to projects, then that would certainly help push forward on FOSS software.

For example, if the Ubuntu devs set out blueprints for things they don't have time to work on, but made it clear on Launchpad what would need to be done, and what packages it affects, then maybe teams of hobbyists could find some way to work together to write the code for a particular feature.  They would have to be small things that could be done in isolation from other features.

It's very hard to get on the bandwagon and help with an existing project... it's much easier to start your own.  That's probably why the vast majority of innovations seem to be coming from professionals, who have time and training.

---

### Post by spoons on 2007-11-03
Ok guys. Sounds like we're just going to have to wait for the current devs to get something ready. Ah well. I'm new, and just thought it would be a good idea.

---

### Post by 23meg on 2007-11-03
[QUOTE=amiga_os]
If there was a simple way that people like me could start contributing to projects, then that would certainly help push forward on FOSS software.

For example, if the Ubuntu devs set out blueprints for things they don't have time to work on, but made it clear on Launchpad what would need to be done, and what packages it affects, then maybe teams of hobbyists could find some way to work together to write the code for a particular feature. They would have to be small things that could be done in isolation from other features.[/QUOTE]

Small bugs are tagged "bitesize" or "ubuntulove" on Launchpad; they're a good way to [get started]("https://wiki.ubuntu.com/MOTU#head-ec7a97d5af67e96747b4f36993232ff434f4486c") (you can do a tag search). Various distro teams and upstream projects also have their "small tasks" lists that are meant for new contributors, and often, those that don't will point you to such tasks when you ask.

Lowering the barriers of entry for new contributors is a big priority in Ubuntu, and community processes are almost constantly refined to get more people contributing at a greater rate.

---

### Post by RAOF on 2007-11-04
The nouveau project is desperately in need of testers.  If you've got the hardware (an nvidia graphics card (anything from a TNT2 to a GeForce8) and a bit of spare time, you can help by just seeing if/how much the nouveau drivers work (multihead?, video?, but not 3d yet).

My PPA contains packages of recent nouveau snapshots to help you test.  They should be fairly safe to install & and uninstall through apt.  [http://nouveau.freedesktop.org](http://nouveau.freedesktop.org) for other details.

---

### Post by coolen on 2007-11-05
Thanks for that. I've been curious as to the status of Nouveau. I don't have a multihead setup, but I'd love to try it out.

---

