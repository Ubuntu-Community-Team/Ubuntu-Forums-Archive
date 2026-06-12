---
title: "Good Linux Distro For Windows 95 Era Computer?"
date: 2009-06-19
forum: The Cafe
---

### Post by kh1116 on 2009-06-19
My mom got a computer from a guy at her work and he wants me to fix it up. Its pretty old with like a 150mhz processor and 48mb ram. Are there any linux distributions that would work well with this setup? with a graphical desktop of course... and games would be a plus bc its for a kids computer

---

### Post by donkyhotay on 2009-06-19
Only one I know of that minimal is [DSL](http://www.damnsmalllinux.org/)

---

### Post by Therion on 2009-06-19
Try Puppy Linux:  [http://www.puppylinux.org/home](http://www.puppylinux.org/home)

You may have to fall back on Damn Small Linux:  [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by blackxored on 2009-06-19
Slackware and DSL worth a try in such a situation (and many others too ;))

---

### Post by starcannon on 2009-06-19
I think you may have to do a bit of experimenting to find just the right one; by today's standards you are definitely on the bleeding edge of retro compatibility (hehe couldn't resist). That said, some ideas on where to start would be:

[SliTaz Linux]("http://www.slitaz.org/en/") is 30mb of Linux Power, and could run entirely in RAM on the laptop in question, this would be my first choice for this project if it were mine to do.

[Damn Small Linux (aka DSL)]("http://www.damnsmalllinux.org/") The entire OS is 50mb, indeed if you could manage to get just a bit more ram in that old machine you could run the entire OS in memory, and it would feel VERY fast, even on that old machine.

[Puppy Linux]("http://www.puppylinux.org/") another very lite distro, with some tweaking you could likely make this one go as well.

[Fluxbuntu]("http://www.fluxbuntu.org/") is also out there, though I have never personally tried to run it with less than 128mb of ram, I have run it on a 133mhz cpu though.
[URL="http://featherlinux.berlios.de/"]
Feather Linux[/URL] is a great possibility as well, and [I read a post]("http://featherlinux.berlios.de/phpBB2/viewtopic.php?t=471") while doing a bit of googling for you that its author claimed to be running it on a 150mhz cpu with only 32mb of ram.

And as always [Google]("http://www.google.com/#hl=en&ei=0e47SsDlLoqkswOf0o35Cg&sa=X&oi=spell&resnum=1&ct=result&cd=1&q=linux+on+a+150+mhz+laptop&spell=1&fp=JJ2lHziMUzc") is a great resource to continue looking for the right fit.

GL and way to go with keeping an old computer out of the landfill. These things definitely can have another life in them serving as Web Browsers, Email Readers, and basic Word Processors.

---

### Post by Old_Grey_Wolf on 2009-06-19
This is not a linux OS; however, you could try ReactOS at [http://www.reactos.org/en/index.html](http://www.reactos.org/en/index.html).

I have never tried it. Therefore, I can not recommend it.

Enjoy your journey trying to make that old computer useful.

---

### Post by MaxIBoy on 2009-06-19
Try a Debian net-install, and then build up your desktop manually. Install Xvesa (not Xorg) and fluxbox, and it should do the trick just fine.

> **Old_Gray_Wolf said:**
> This is not a linux OS; however, you could try ReactOS at [http://www.reactos.org/en/index.html](http://www.reactos.org/en/index.html).

I have never tried it. Therefore, I can not recommend it.

Enjoy your journey trying to make that old computer useful.I'd suggest staying away from ReactOS for now. It's very promising, but the last time they synced their DLLs with WINE was back in January '08. In other words, if it didn't run on an ancient version of WINE, it won't run on ReactOS.

---

### Post by Bachstelze on 2009-06-19
> **MaxIBoy said:**
> Try a Debian net-install, and then build up your desktop manually.

I wouldn't recommend Debian or any Debian-based OS for a machine with such a slow processor, since apt sometimes runs highly cpu-intensive tasks when installing packages, which will take *very* long on such a machine (an example is generating the initrds when a new kernel is installed).

Slackware would be my choice, with a light window manager like Fluxbox or IceWM.

---

### Post by &#32 Greg on 2009-06-19
SliTaz, DeLi, TinyCore, and Basic Linux should work.

I think DeLi would be my choice.

---

### Post by CharmyBee on 2009-06-19
It's a 150MHz, so it's most likely a Pentium MMX laptop.

> **Old_Gray_Wolf said:**
> This is not a linux OS; however, you could try ReactOS at [http://www.reactos.org/en/index.html](http://www.reactos.org/en/index.html).

I have never tried it. Therefore, I can not recommend it.

Enjoy your journey trying to make that old computer useful.

It's still in alpha state, no one should really try it unless they're debugging it.

---

### Post by starcannon on 2009-06-19
I was hanging out in the Fluxbuntu irc channel and a user there told me about [VectorLinux Light Edition]("http://vectorlinux.com/news/vectorlinux-light-edition-released"), its very beautiful in the screen shots, and if it will work on those meager system specs, I think it could be a hands down winner in the light wieght beauty category (highly subjective I know :D )

---

### Post by Pogeymanz on 2009-06-19
+1 for SliTaz
-1 for Fluxbuntu  -It's not very good and pretty buggy.

---

### Post by I-75 on 2009-06-19
If you can add some ram...why not Windows 2000 ?

---

### Post by CharmyBee on 2009-06-19
> **I-75 said:**
> If you can add some ram...why not Windows 2000 ?

Windows 2000 will only start being usable by the 233MHz mark.

---

### Post by starcannon on 2009-06-19
> **I-75 said:**
> If you can add some ram...why not Windows 2000 ?
Correct me if I'm wrong, but I am under the impression that security updates for Win2000 end next year in 2010. No tinge of Win Bashing here, but even if the hardware they have would be viable, it seems better to go with something like Linux, that will continue security support for as long as they own/use the machine (short of something catastrophic happening to GNU/Linux).

---

### Post by CJ Master on 2009-06-19
Do not use Xubuntu. It's about the fattest Xfce distro you can find.

I would recomend a lightweight distro with LXDE.

---

### Post by snowpine on 2009-06-20
SliTaz recommends 256mb ram for best performance, be sure to use the 'loram' flavor.

---

### Post by Viva on 2009-06-20
DSL or Puppy linux. I recommend the former because I don't like dogs.

---

### Post by gymophett on 2009-06-20
Puppy, Tinycore, or DSL.
Maybe Crunchbang?

---

### Post by drawkcab on 2009-06-20
Damn Small Linux
Puppy
Slitaz
AntiX

---

### Post by HappyFeet on 2009-06-20
Tiny Core.

---

### Post by cmay on 2009-06-20
i have a similar specked comp standing. with FreeDos in it right now.  

from what my experience tells me using old computers the right distributions are limited to in this case damn small linux. tinycore. and maybe if you are really lucky puppy.

 else best play with debian netinstall or even ubuntu minimal netboot iso but then the wired network has to work. 

which mine does not so i use freedos and minix on it. minix can not run x on htis old computer by the way. but it can run on as low as 8 mb ram and i had  a100 mzh and 16 mb ram using minix once. (no network in that either)

fort anything useful i suggest FreeDos or damn small linux. (if you talk about kids and games then freedos)

---

### Post by Sublime Porte on 2009-06-20
I have a box with higher specs than that (200mhz cpu, 128mb ram) and the only distro I really find usable is TinyCore. Some puplets (remixes of PuppyLinux) are ok, but TinyCore would have to be the best bet here.

Many of the other distros mentioned would not even run with 48mb of RAM, and I can't for the life of me understand how they've been recommended.

---

### Post by gymophett on 2009-06-20
Don't expect anything fancy looking.
You can do an Ubuntu minimal install, and install and extremely light window manager. That would work!

---

### Post by lisati on 2009-06-20
I once managed to get Puppy Linux up and running on a 133mHz machine with 64Mb RAM and a 3GB HDD - it was a bit slow but usable.

---

### Post by gymophett on 2009-06-20
In the end, either TinyCore, or DSL are probably your best bets.

---

### Post by stwschool on 2009-06-20
SLitaz has worked for me on some real old slow machines and even had it working on 16mb ram. It's as close as you'll get to what you're looking for. It gives you firefox + flash for web games (which is fine for most kids), though installing openoffice for their homework seems like harder work than I can be bothered with!

---

### Post by daverich on 2009-06-20
another vote for puppy linux here.

Kind regards

Dave Rich

---

### Post by K.Y.A on 2009-06-20
Wow, people jump to the threads like fire ants when we talk about old computers running Linux, don't they?:D

I recommend Puppy Linux, or Damn small Linux. 

Reactos had the requirements of Windows 2000. And windows 2000 would be more reliable, actually.

---

### Post by kk0sse54 on 2009-06-20
[**Crux**]("crux.nu"), though the architecture type will be the limiting factor here.

---

### Post by sertse on 2009-06-20
> **C!oud said:**
> [**Crux**]("crux.nu"), though the architecture type will be the limiting factor here.

You're thinking Arch which is limited to i686 and can't run on i386. CRUX doesn't have at restriction.., Kmandla demonstrated it by running it, and using it as his main PC on comps much worse than the OP's..

---

### Post by kk0sse54 on 2009-06-20
> **sertse said:**
> You're thinking Arch which is limited to i686 and can't run on i386. CRUX doesn't have at restriction.., Kmandla demonstrated it by running it, and using it as his main PC on comps much worse than the OP's..

Actually crux does, from their own website
> CRUX is a lightweight, i686-optimized Linux distribution targeted at experienced Linux users.

Now there are other crux iso available most notibly the i586 iso, so yes crux will easily run on older computers. However when I said that the arch type was the limiting factor it was in reference to the which iso the op could use ;)

---

### Post by Bachstelze on 2009-06-20
Also, i686 goes as far back as the Pentium Pro, so chances are the op's machine *is* i686.

---

