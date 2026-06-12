---
title: "VMing existing XP onto VirtualBox harmed XP"
date: 2008-07-31
forum: Virtualisation
---

### Post by AegisTalons on 2008-07-31
So a little bit ago, I reformatted my computer because I had to much junk on it. I installed XP first, followed by Ubuntu of course. I use XP for video games and SolidWorks. Anyways, I wanted to get my existing XP install working under Ubuntu, so I ran it under VirtualBox.

On my computer, I partition my drives out, so I have a partition just for XP, a partition for my work, my games, and so on. I have my hard drives running in SATA mode, not IDE. Had to slipstream drivers into XP install. 

I also got already the issues with XP registering by having two profiles (VM and Native). When I ran XP under VirtualBox, it would not let me access the other drives, though it could see that something was there.

I then booted into Windows natively, and VirtualBox screwed all my partitions around. No link worked, software did not know where it was; basically painful to work with. 

When I did not want to have a pain in the *** of fixing it, so I reformatted it and here I am again. Thinking of trying it again. But before I do, does anyone have any insight into this issue? Sorry for the long post.

---

### Post by tuxxy on 2008-07-31
Maybe jsut make another install for virtual, with shared folder, atleast this way you wont need to boot down.

---

### Post by AegisTalons on 2008-07-31
What exactly do you mean shared folder? Are you saying make an image of each drive and placing in a shared thing?

Before I learned about VirtualBox, I was using VMWare Server and created a "VM" of existing windows. When I would go into the VM it would see all the connected hard drives and everything. Is there an option or something in VirtualBox to do that?

---

