---
title: "What if Ubuntu were licensed under BSD?"
date: 2008-06-04
forum: The Cafe
---

### Post by Luke has no name on 2008-06-04
Rather, what if the Ubuntu project were created as a fork of a BSD derived OS?

It'd be awesome. Then we could have commercial companies free to improve the software and make money on their investment! Users could charge money for more than just the packaging! We could have ZFS and Java and Flash and MP3 integrated into the OS without FUD'ed "It's not really free" comments!

People > Software. Give freedom to the PEOPLE to modify and redistribute software the way THEY wish it to be done. For a group of people who value restrictions on software distribution, you guys SURE do hate DRM. Kind of hypocritical, don't you think?
 
Damnit, Mark, why couldn't you base Ubuntu off FreeBSD? 

The big question to ask is this: Is there a correlation between community participation and upstream licensing? Would Ubuntu have such participation if it were BSD licensed? Or is the reason BSD licensed OSes aren't as "popular" because:

---FreeBSD has a slow dev cycle
---OpenBSD hates you
---Dragonfly BSD doesn't count
---PC-BSD is late on the scene (though their packaging is arguably better than apt)
---NetBSD is too niche

If Ubuntu were based of FreeBSD as it is based off Debian now, things would really be interesting.

[quote=FreeBSD Documentation]
The GPL is an attempt to keep efforts, regardless of demand, at the research and development stages. This maximizes the benefits to researchers and developers, at an unknown cost to those who would benefit from wider distribution.
[/quote]

[color=white]
[size=-3]Author's note: I stand by my comments above, though I am more intelligent than to think everything is cut-and-dry like this. I could have a long, productive discussion on licensing philosophy, but it's so much easier to get emotion and response and passion out of people with text-bytes like those above. I now see why politicians do it all the time...[/size][/color]

---

### Post by madjr on 2008-06-04
canonical could always create a BSDbuntu (from pc-bsd) nothing stoping them, but the bsd license is kind of crap.

i do like .pibs for portability. But we might get .debs to do that soon (all dependencies in a single deb).

---

### Post by Ebuntor on 2008-06-04
> **Luke has no name said:**
> Rather, what if the Ubuntu project were created as a fork of a BSD derived OS?

It'd be awesome. Then we could have commercial companies free to improve the software and make money on their investment! Users could charge money for more than just the packaging! We could have ZFS and Java and Flash and MP3 integrated into the OS without FUD'ed "It's not really free" comments!
 

I'm certainly no expert on this subject (so please correct me if I'm wrong) but nothing is keeping commercial companies from improving and/or making money because Ubuntu is licensed under the GPL. There's countless big companies that release and improve GPL code; IBM, Google, Novell, Ret Hat, Intel etc.

>  We could have ZFS and Java and Flash and MP3 integrated into the OS without FUD'ed "It's not really free" comments!
How would MP3 support be any different if Ubuntu was under the BSD license? The reason all the codecs aren't included is because it has to do with royalties.  

> People > Software. Give freedom to the PEOPLE to modify and redistribute software the way THEY wish it to be done. For a group of people who value restrictions on software distribution, you guys SURE do hate DRM. Kind of hypocritical, don't you think?I'm not gonna start a whole GPL vs BSD discussion however I think I should mention that this "restriction" actually protects the author from other people/companies from taking/stealing his code without giving anything back, why would they?

---

### Post by MaximB on 2008-06-04
It is GOOD that Ubuntu and GNU/Linux in general use the GPL license and not the BSD.
Want BSD ? use BSD.
See MacOSX - they took the BSD source code, changed it, closed it and called it MacOSX and that's it - now if you want to use the modified version you need to buy a whole Mac.
No real benefit to the community and the FREE developers.
Yes Apple did release some parts of the code but that's not because they had to, nothing in the BSD license can prevent you from using the code selling it and not giving back - I call it "legal stealing" but suite yourself.
In GPL that cannot happen , what was open stays open and the modified versions also stays open and benefit the community.

---

### Post by Methuselah on 2008-06-04
Yeah, the bsd license does not gurantee that freedom in perpetuated. This is an advnatage or disadvantage dependign on who you speak to. As a volunteer developer you probably don't want to be working for free for Apple or Microsoft.

---

### Post by qazwsx on 2008-06-04
So most of the software are still licensed under GPL.


Besides forking free software and licensing it under restrictive license is disgusting. It will most likely break compatibility later etc.

---

### Post by shadylookin on 2008-06-04
nothing would change because the majority of the software is licensed in gpl. most open source developers have qualms with working hard only to have a corporation come in and take their code without compensation or helping out the community which is why they choose the gpl.

---

### Post by ssam on 2008-06-04
the good thing about it being mostly GPL, is that when people make modifications (and distribute them) they have to provide the source. that means new stuff created in derivatives can flow back upstream.

canonical is already a commercial company "improving ubuntu and making money on their investment", so are dell and all the companies listed at [http://webapps.ubuntu.com/partners/](http://webapps.ubuntu.com/partners/)

i would not welcome lots of separate, incompatible, closed sourced forks of ubuntu.

ZFS is not held back because the kernel is GPL. yes it means we can't copy and paste the code from solaris. but not being able to copy and paste code does not not stop linux having FAT, NTFS and HFS filesystems support. we just need a team of people to write a GPL (or BSD) ZFS filesystem driver.

not having java and flash on the install CD is because of the goal for everyone to be able to copy and modify what is on the CD. If flash were on the CD you would not be allowed to duplicate it and give copies to your friends.

---

### Post by banjobacon on 2008-06-04
> **MaximB said:**
> See MacOSX - they took the BSD source code, changed it, closed it and called it MacOSX and that's it - now if you want to use the modified version you need to buy a whole Mac.
No real benefit to the community and the FREE developers.
Yes Apple did release some parts of the code but that's not because they had to, nothing in the BSD license can prevent you from using the code selling it and not giving back - I call it "legal stealing" but suite yourself.

How would Mac OS X be any different if it were based on Linux? The GPL would force Apple to contribute kernel modifications back to the community, but all non-kernel code could remain closed.

---

### Post by shadylookin on 2008-06-04
> **banjobacon said:**
> How would Mac OS X be any different if it were based on Linux? The GPL would force Apple to contribute kernel modifications back to the community, but all non-kernel code could remain closed.

the kernel would be improved, and so would any other gpl licensed software that they use. Otherwise if it is there own software they can license it how they please

---

### Post by banjobacon on 2008-06-04
> **shadylookin said:**
> the kernel would be improved, and so would any other gpl licensed software that they use. Otherwise if it is there own software they can license it how they please

But they do release kernel-related code through the Darwin project, correct? So there would be no difference if Mac OS X were based on a GPL-licensed kernel.

EDIT: I get that it could happen, I just don't see how OS X is a good example.

---

### Post by shadylookin on 2008-06-04
> **banjobacon said:**
> But they do release kernel-related code through the Darwin project, correct? So there would be no difference if Mac OS X were based on a GPL-licensed kernel.

EDIT: I get that it could happen, I just don't see how OS X is a good example.

I don't know I haven't used a Mac since my elementary schools apple 2:lolflag:

I suppose the difference is that now apple releases code when and if apple feels like it, but if they use the gpl they would have to release the code to the community immediately.

---

### Post by techmarks on 2008-06-04
Apple took code from the Mach 3 microkernel which was developed by Carnegie Mellon University and code from FreeBSD 3.2, and created the core of OS X, and then made it proprietary software.

---

### Post by DeadSuperHero on 2008-06-04
Now, correct me if I'm wrong:
-A BSD licensed project can be made proprietary.

But, can it also be made under a stricter license, such as the GPL? Are there GPL'd BSD distros out there?

---

### Post by wdaniels on 2008-06-04
> **Mr. Psychopath said:**
> But, can it also be made under a stricter license, such as the GPL? Are there GPL'd BSD distros out there?

Sure, you can do that, but I don't know of any examples.

---

### Post by Methuselah on 2008-06-04
> Just how does the GPL really guarantee that the GPL'd code is not made proprietary?

Well, it can be used, but derivative works are supposed to be open sourced.

I ran FreeBSD before I ran linux. Nice OS with great unified documentation. It taught me more about Unix than anything I'd read about linux. However, I migrated away from it when my disc burner simply wouldn't work properly and I absolutely needed that. Tried some linux live CDs and it worked and since then I've been using Ubuntu.

The BSD license is very liberal. However, I don't know if I like the idea of proprietary companies being able to fork the code and close it off.

---

### Post by bufsabre666 on 2008-06-04
> **wdaniels said:**
> Sure, you can do that, but I don't know of any examples.

PC-BSD, which i am a big fan of is GPL'd

---

### Post by DeadSuperHero on 2008-06-04
I thought PC-BSD was relicensed under a BSD license...

---

### Post by reyfer on 2008-06-04
Can I ask why so many threads recently putting GPL down? Is something going on I'm not aware of? Is somebody here trying to make a propietary Ubuntu derivative?(I get a smell of M$ bots :lolflag: )

---

### Post by techmarks on 2008-06-04
PC-BSD is licensed under the BSD license.

---

### Post by az on 2008-06-04
> **Luke has no name said:**
> Rather, what if the Ubuntu project were created as a fork of a BSD derived OS?

...

The big question to ask is this: Is there a correlation between community participation and upstream licensing? Would Ubuntu have such participation if it were BSD licensed? Or is the reason BSD licensed OSes aren't as "popular" because:

---FreeBSD has a slow dev cycle
---OpenBSD hates you
---Dragonfly BSD doesn't count
---PC-BSD is late on the scene (though their packaging is arguably better than apt)
---NetBSD is too niche



If Ubuntu was based on a BSD license, or for argument's sake, if any code that was written specifically for Ubuntu was BSD-licensed, there would not be as strong a community behind Ubuntu as there is today.   As an end-user, you simply can't trust BSD-licensed projects.  

A F/LOSS project is only as powerful as its community.

One of the reasons why the GPL is the most popular F/LOSS license on the planet is because it empowers the community behind the project.

---

