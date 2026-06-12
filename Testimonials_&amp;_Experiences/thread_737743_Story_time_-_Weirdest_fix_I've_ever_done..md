---
title: "Story time - Weirdest fix I've ever done."
date: 2008-03-27
forum: Testimonials &amp; Experiences
---

### Post by revenant138 on 2008-03-27
Some people know the answers all the time. To everything. I'm wondering how I know so many geniuses. However, I am but a humble mortal, not blessed with infinite knowledge, and some days I have to slog through bad guesses and stupidity before a solution becomes clear.

Maybe you have had to do this too, had to fight to find an obvious solution made hidden by a coincidence. I empathize. 

This is the story of a kernel panic.

Since about three PM I had been working on getting usplash working. I had tried what must have been 300 ways to get that stupid kubuntu logo to cool my eyes with its blue hues while I boot up. Before I had had blank monitors, I had earned the right to see text scroll by as my machine revs up, but now I wanted some gears. After several combinations of uninstalling packages, editing menu.lst, changing the resolutions in the usplash.conf file, nothing. Ladies and Gentlemen, I can safely say I've tried harder than anyone on earth to see those gears. But its not going to happen. 

I change grub back to where it just shows text (remove the splash option), and sulk. 

$@*#%& gears.

While I was on a roll -.- I decided to hook up the 3rd hdd that's been sitting inside my hooge Thermaltake case for months, now that I have an adapter to convert its ide-ness, to sata-ness. I shut down, using init 0 like the 1337 POS I am, and popped the side panel off.

A few minutes later, I powered back on. And sat hanging at the bios boot screen. Urk. I'd had this problem with my Biostar mobo before when I tried to hook up two ide hdd's before. A firmware update hadn't fixed it, !@&*(# if I was going to. I could live without my Frasier episodes on that hdd and figured I'd fight it another day. 

...Disconnect 3rd hard drive and reboot..

BIOS doesnt hang, Grub does its thing, kernel starts booting - PANIC. Followed by colossal confusion. Can't find root filesystem on my main hard drive. First thing I'm thinking is my hard drive went bad in the previous five minutes. Or I gave it a little static surprise. 

I check the boot order again. Fine. I start looking around the net from another computer about wtf could have caused this. Sounds like my initrd something or other got hosed. Like I know what that is. Well...I could make changes...if the machine would boot! Honestly, who writes these fixes? I'm texting my girlfriend for moral support at this point because I'm thinking how many hours I spent setting up this machine - the equivalent of a whole semester's work of one of my engineering classes. 

What is initrd!? Bootup lists the UUID of my main drive as being unable to be found. As far as I can tell, the thing's toast. But why would it START booting the kernel? Its not like the first few thousand lines are somewhere besides the now dead hard drive, are they?

Cue the part where I start questioning my most basic computer knowledge. Maybe they forgot to mention something in computer architecture class, like how the first part of linux gets put on a chip on the motherboard, that makes sense right? Yup, and there's gnomes shoveling bits into the internet pipe.

Like a deer in headlights, I start trying random things to see what I can do. I see if Grub's working, it is. Strange. Some part of me knows that hard drive isn't dead.

I give a shot to recovery mode and what do you know? Thing boots! Now what?

The magic of the internets, available on my laptop, has whispered to me of a mkinitrd script that might do it. Apt-cache searching finds me something that might be close to it. OH but I dont have internet on my desktop at the moment, for absolutely no reason whatsoever -.-

I'm stuck. 

Searching around on the forums, I'm pulling down threads that even have the word initrd in them, and I see one where a fellow posted his menu.lst file. My desktop is sitting in the grub folder, and I think, well, maybe I can change the initrd image or whatever to some other initrd laying around. Hey, I dont know what initrd is or does, why not? Thats how I've made my way through linux so far. So I pop into menu.lst.

I scroll through the commented out demo parts of it until I see my main kernel's grub entry.

Then I see it.

...


...


...

Remember before when I said I removed the splash option? 

...

I hit the delete key one too many times.

This combined the kernel and initrd lines and made that Grub entry absolutely useless. 

Added the carriage return back, and booted up like a pro. 

It was the weirdest fix I've ever done, just because I'm wondering how long it would have taken me to figure out if I hadn't just checked menu.lst on a whim? The reboot with the 3rd hard drive made me sure something completely other than my menu.lst editing for my usplash problem was suspect.

I posted this story for everybody who's had a battle with a simple fix that made them feel like the dumbest person alive ;)

Any good similar stories? Also, it'd also be fun to know if anyone knew what had happened way before I clued everyone in.

---

### Post by Joeb454 on 2008-03-27
I've had similar things when programming...

A simple ; missing from the end of a line, and the whole thing doesn't compile. Now with small apps, that's not an issue, but with over 200 lines it starts to get a pain in the *** ;)

---

### Post by armandh on 2008-03-28
I am not a code person. 
the most I have ever done is copy/modify autoexe bat and config sys for multiple boots 
back when my son's games had their own memory manager.
so you are way over my head.

BUT

working with home made electronic gadgets or repairing stuff I know
That leaving out just 1 part can be a problem far greater than the parts relative mass.

---

### Post by revenant138 on 2008-03-28
> **armandh said:**
> 
working with home made electronic gadgets or repairing stuff I know
That leaving out just 1 part can be a problem far greater than the parts relative mass.

Tell me about it. I'm building a short sniffer right now, which is basically an inductor and a few amplifiers. Has a low frequency clicking I'm trying to get out, can't do it. Then, if I touch one of the resistors, it turns into a radio that picks up the local Christian station :D

---

### Post by armandh on 2008-03-28
try a little shielding from the cap coupling leaving only the inductive???

---

### Post by revenant138 on 2008-03-28
> **armandh said:**
> try a little shielding from the cap coupling leaving only the inductive???

Well, my plan now is to build it into a metal enclosure, making me a farady cage, and shorten all the leads.

How would I do what you're suggesting?

---

