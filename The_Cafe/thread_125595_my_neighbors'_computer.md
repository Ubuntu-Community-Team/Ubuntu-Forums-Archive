---
title: "my neighbors' computer"
date: 2006-02-04
forum: The Cafe
---

### Post by fuscia on 2006-02-04
so, last night, i'm over at my neighbors' house, sitting on the deck watching tv with a fire going. the subject of their computer came up and he asked me to look at it ("in the kingdom of the blind, etc..."). "it's sooooooo slow and getting slower" was the complaint. this thing is about six years old with an amd k6-2 450mhz cpu, an 8gig hd and 256ram. her cousin put xp professional on it. am i correct in thinking that's not enough machine to run xp pro? (the cousin put the memory in.) they also seem to be afflicted by the bagel worm. 

i installed opera on their machine with the idea that if they can get to all the places they usually visit on opera, they could use linux (i would do a server install with a lightweight wm, for them). if they were too uneasy about that, i at least have my old copy of windows ME (microsoft's best ever), that would at least run on the thing. it may be an edsel, but i never had any major problems with it. also, these people are very much end users who don't even know what brand machine they have. 

they have an hp officejet which i would have to get working as they only do some internet, yahoo mail and some word processing. i don't have a printer and know nothing about them, so your advice would be most welcome there, especially.

---

### Post by mips on 2006-02-04
Hmm, seems abit slow for XP but probably ubuntu as well.

HP is generally well supported under linux, it would actually help a great deal if you posted the model numeber. Alternatively look it up.

Could alwasy do a server install + X + light window manager.

---

### Post by aysiu on 2006-02-04
A friend of ours put Windows XP on our five-year-old computer that had only 128 MB of RAM. Now *that's* slow. Maybe it has adware on it?

---

### Post by fuscia on 2006-02-04
[QUOTE=aysiu]A friend of ours put Windows XP on our five-year-old computer that had only 128 MB of RAM. Now *that's* slow. Maybe it has adware on it?[/QUOTE]

i did a run of hijackthis and there didn't appear to be too much crap on that end. most of the excess was stuff from symantec. they run ad-aware once a week (i think that was the cousin's doing). it may well be that using opera will give them enough relief in the speed department that they can stay as is.  i'm sure there's a lot of tweaking i could do of xp to get it running a little fas...uh, less slowly. 

i rebooted it at one point and he said "come on out on the deck and have a beer while you're waiting." i thought he was kidding. i went back in and it was still rebooting.

---

### Post by fuscia on 2006-02-04
[QUOTE=mips]HP is generally well supported under linux, it would actually help a great deal if you posted the model numeber. Alternatively look it up.[/quote] 

it's a v-40. it's about three years old, they think.

> Could alwasy do a server install + X + light window manager.

that's what i was thinking - server install, X, icewm, opera, abiword, penguin-command for the kids, etc.

---

### Post by raublekick on 2006-02-04
you could always try Damn Small Linux. Use it as a live CD first and kinda show them the ropes with general use, and then if they aren't too scared, install it and set up all of the software they need. It sounds like they are the type of people who really don't need much more than the email/browser/office trifecta.

---

### Post by aysiu on 2006-02-04
Wouldn't even Xubuntu work on 64 MB of RAM?

---

### Post by curuxz on 2006-02-04
I have linux running very well on a 450 with 364mg ram so I think you should not have too many problems. Esp with something like Xfce

---

### Post by tseliot on 2006-02-04
Xubuntu will run fine. Perhaps the only other DE which won't seem entirely alien to your neighbours can be Icewm (which should be more lightweight than xfce).

---

### Post by xequence on 2006-02-04
XP runs fine in anything 256MB RAM or over. Just make sure shared video isnt putting it down 64MB to 196MB or something.

---

### Post by raublekick on 2006-02-04
[QUOTE=xequence]XP runs fine in anything 256MB RAM or over. Just make sure shared video isnt putting it down 64MB to 196MB or something.[/QUOTE]

But it's still a 450MHz processor, which will be the main problem. At my internship I used a 600MHz PC, and it ran XP just fine with things like Fireworks, Homesite+, and various other web related software. But, it had over 600MB of RAM.

---

### Post by fuscia on 2006-02-04
they're video memory is wicked small (don't remember what it was). i've used gnome and kde on my 700mhz celeron with 256ram with perfectly acceptable results (if i weren't so impatient, they'd be fine). it would certainly be much faster than what they've got now. i just don't want to screw them up as i'm still a gnub.

---

### Post by mips on 2006-02-04
maybe you can pop some more ram into that machine...

---

### Post by fuscia on 2006-02-04
[QUOTE=mips]maybe you can pop some more ram into that machine...[/QUOTE]

it's got two slots, each with 128. i don't know what kind it is, either. i have a 256 chip that wouldn't fit in my machine. maybe it will fit in theirs.

---

### Post by mstlyevil on 2006-02-04
It is probally pc 100 RAM but i could be wrong on this. As long as they are using XP, you need to click on start->Run and type services.msc. When the window opens you should disable themes, fast user switching, error reporting, wireless zero (If they are hardwired to their internet connection.) and other services they do not use. Here is a link to a web site that will help you determine what services are necessary and ones that are not.

[Services Guide for Windows]("http://www.theeldergeek.com/services_guide.htm")

Disabling these services will free up both CPU cycles and RAM. Next got to My Computer and right click on C drive. Click on Properties and uncheck Indexing to turn that service off. Then next go to Start -> Run and type msconfig. When the dialog box appears go to the start up programs tab and uncheck everything but their Antivirus/Firewall. Then close the box and reboot.

Upon startup you will see a dialog box. You need to click on the check mark and then close the box. Now you should see the computer run faster because you have slimmed down XP's foot print on the system. If you try this, let me know how it works.

(If you already have done these things or already know how to do them then just ignore this suggestion.)

---

### Post by fuscia on 2006-02-04
thanks for the suggestions, mstly. i'll give that a shot. if i can get them going faster, for a while at least, that would be a little more comfortable choice than totally overhauling their computer life, especially since they do so little with it.

thanks, everyone else, for the input.

---

### Post by xequence on 2006-02-04
[QUOTE=raublekick]But it's still a 450MHz processor, which will be the main problem. At my internship I used a 600MHz PC, and it ran XP just fine with things like Fireworks, Homesite+, and various other web related software. But, it had over 600MB of RAM.[/QUOTE]

Yes, but it is an AMD chip. That might equal performance of a higher clock speed intel one... Or was AMD bad back then?

---

### Post by DeadEnd on 2006-02-04
I have  XP pro on a p2 350mhz with 128MB and it runs good.

Admittedly doing any heavy processes such encoding / decoding video it pratically crawls but everyday tasks listening to music / video surfing etc it is fine.
BTW:

---

### Post by Stew2 on 2006-02-04
I agree with Xequence and DeadEnd, it should run fine for general computing. Wont be doing any heavy gaming or intensive photo editing with it though, but that goes without saying. Those specs should run XP or Ubuntu fine though. I've got an old 633 celeron with 256 ram and it runs both OS's just fine, the AMD 450 should be equal or even more powerful than my old celeron. It might just be set up wrong or have too many background services running.

---

