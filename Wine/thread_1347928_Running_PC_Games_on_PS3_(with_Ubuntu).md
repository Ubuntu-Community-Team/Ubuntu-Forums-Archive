---
title: "Running PC Games on PS3 (with Ubuntu)"
date: 2009-12-06
forum: Wine
---

### Post by m0rrigan on 2009-12-06
So...my question is...can it be done? 

I did some searching and found some posts indicating that it was impossible due to hardware incompatibilities, but I couldn't find anything definitive on that more recently than 2007. I've done some research and think I can manage it via Wine, etc. as long as the hardware was compatible. 

If the answer is just no, as I suspect it may be, does anyone have any additional information on whether it seems likely it will be possible in the future? Or are we all just stuck buying expensive gaming PCs?

Thanks in advance for your help!

---

### Post by beastrace91 on 2009-12-06
This is not possible because Wine Is Not an Emulator - meaning it cannot run code compiled for x86 processors on non-x86(or x86_64bit) hardware - this is the same reason Wine software does not work on PowerPC Macs.

Regards,
~Jeff

---

### Post by m0rrigan on 2009-12-06
Thank you very much for your response. I was afraid of that. If it's not too much trouble, could you confirm another thing for me? It looked to me from the research I did that running a game using an emulator didn't really work because it uses too much system resource to run the emulator, thus causing games to run painfully slowly or not at all. Is that right?

I'm in a bind because I'd like to be able to play current video games, but as I'm primarily an RPG geek, I prefer to play them on PC due to the (generally) superior interfaces on PC releases. However, I don't have a lot of money to throw around at the moment for a new gaming PC. When I heard that you could load Ubuntu on a PS3 I thought perhaps I could get around having to buy a top of the line gaming station, but it sounds like maybe I've hit a brick wall and should start saving $'s!

(I'll come clean and 'fess up that I'm trying to find a way to play the upcoming Mass Effect 2 without buying a new PC!)

Thanks again! I'm a relative newb, and I really appreciate the help. It saves me a lot of time groping in the dark on Google!

-m

---

### Post by beastrace91 on 2009-12-07
You could try something like [VirtualBox](http://virtualbox.org/) but on this one I am unsure if the PS3 processor supports virtualization. And even if this does work it is only good for playing older games (Starcraft, Diablo II, or WC3 at best)

Regards,
~Jeff

---

### Post by m0rrigan on 2009-12-07
Thanks for clarifying! You've been a big help! I guess I'll just have to pony up after all.

---

### Post by redzsky on 2009-12-09
or !!!!!
there is a version of windows vista or maybe even 7 which you could run vmware
[http://hothardware.com/News/Toshiba-Launches-First-Cell-CPUbased-Laptop/](http://hothardware.com/News/Toshiba-Launches-First-Cell-CPUbased-Laptop/)  this laptop runs windows  and use the spe but maybe its only designed for chips with 4 spe
the ps3 has 6 active


just a thought

---

### Post by beastrace91 on 2009-12-09
> **redzsky said:**
> or !!!!!
there is a version of windows vista or maybe even 7 which you could run vmware

VMWare requires the processor in the computer supports virtulization - just like any other virtulization software (such as VirtualBox that I listed above)

EDIT: Also note the fact that the laptop you linked to has a standard 64bit processor in it - which is why it can run 32/64bit applications.

Regards,
~Jeff

---

### Post by Marlonsm on 2009-12-09
Just a note: The PS3 while having lots of processing power, can't actually use it outside spcecific applications (it is, games for PS3) so even if you can get everything right and install the game, I don't think it'll have a good performance.

---

### Post by beastrace91 on 2009-12-09
> Just a note: The PS3 while having lots of processing power, can't actually use it outside spcecific applications (it is, games for PS3) so even if you can get everything right and install the game, I don't think it'll have a good performance.

Already stated not possible and why

> **beastrace91 said:**
> This is not possible because Wine Is Not an Emulator - meaning it cannot run code compiled for x86 processors on non-x86(or x86_64bit) hardware - this is the same reason Wine software does not work on PowerPC Macs.

Regards,
~Jeff

~Jeff

---

