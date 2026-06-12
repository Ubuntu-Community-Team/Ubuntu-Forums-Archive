---
title: "BIOS will be dead in three years"
date: 2010-06-08
forum: The Cafe
---

### Post by Sporkman on 2010-06-08
> **Exclusive: BIOS will be dead in three years**

MSI says shift to UEFI coming soon

08 June, 2010

It's the one major part of the PC that's still reminiscent of the PC's primordial, text-based beginnings, but the familiarly-clunky BIOS could soon be on its deathbed, according to MSI. The motherboard maker says it's now making a big shift towards point and click UEFI systems, and it's all going to kick off at the end of this year...

[http://www.thinq.co.uk/2010/6/8/exclusive-msi-bios-will-be-dead-three-years/](http://www.thinq.co.uk/2010/6/8/exclusive-msi-bios-will-be-dead-three-years/)

---

### Post by jerenept on 2010-06-08
I wonder... will I be able to overclock using this "point and click" stuff? GUIs mostly encourage bloat, imho.

---

### Post by spupy on 2010-06-08
What does this mean for users? The article mentions point-and-click interface, but doesn't seem like a big deal to me.
Easier programming was also mentions, I'm guessing this will make the life of firmware/OS developers easier?

---

### Post by FuturePilot on 2010-06-08
Does this mean we can move to GPT and ditch MBR and all the restrictions that go with it?

---

### Post by McRat on 2010-06-08
So "text based" BIOS is going away?

Because all computers need BIOS (Basic I/O Sys)

---

### Post by Hyper Tails on 2010-06-08
is it only for curtain motherboards?

I have the ASUS P5W DH Deluxe motherboard

---

### Post by Paqman on 2010-06-08
> **jerenept said:**
> I wonder... will I be able to overclock using this "point and click" stuff?

I'd put money on it. They'd never be able to sell gaming mobos otherwise.

---

### Post by Hyper Tails on 2010-06-08
> **paqman said:**
> i'd put money on it. They'd never be able to sell gaming mobos otherwise.

+1

---

### Post by snova on 2010-06-08
> **spupy said:**
> What does this mean for users? The article mentions point-and-click interface, but doesn't seem like a big deal to me.

Zilch. Shiny interfaces are also optional, so I don't expect to see any more of these. They already exist anyway; calling it a feature of EFI is misleading.

> Easier programming was also mentions, I'm guessing this will make the life of firmware/OS developers easier?

Maybe, maybe not. I've yet to hear anything particularly nice about EFI; it tends to be described as pointlessly complicated without much tangible gain.

> **McRat said:**
> So "text based" BIOS is going away?

Because all computers need BIOS (Basic I/O Sys)

No, they're replacing BIOS with something that functions on the same layer and does essentially the same thing.

---

### Post by Breambutt on 2010-06-08
I don't really see any noticable benefits to this, aside from some new features of course. The Average Joe could probably survive a lifetime without entering BIOS and the more curious individuals have no problem with the non-graphical interface.

Would be fun if something failed to initialize and the graphical version landed on it's *** upon launch.

---

### Post by SunnyRabbiera on 2010-06-08
> BIOS will be dead in three years

As may linux due to OS bias on motherboard makers like asus and foxxcon

---

### Post by jerenept on 2010-06-08
> **SunnyRabbiera said:**
> As may linux due to OS bias on motherboard makers like asus and foxxcon

As if!
Never!!!!!

---

### Post by Dustin2128 on 2010-06-08
> primordial, text-based beginnings
I took great offense at that. That said, I agree that a GUI encourages bloat and security holes, imagine viruses screwing up people's BIOS in addition to OS, and NOT getting new systems from windows decay, not to mention a lesser degree of control. The problem is I can see most users endorsing this whereas I would fight it tooth and nail. This sucks.

---

### Post by lisati on 2010-06-08
IMO, BIOS in its current form won't go away for a while, but is likely to evolve. You'll still need something to take care of the basics of interacting with the hardware while the OS gets started and then gets its act together to run things.

---

### Post by new_tolinux on 2010-06-08
> "The main difference between a traditional BIOS and UEFI is  programming," said our source, pointing out that "UEFI is written in C,  rather than the assembly code used in a traditional BIOS." However, he  points out that this means that there's much more flexibility with the  code.Ah.... so they skip assembly code......
But isn't assembly the base which makes it possible to run other (C) code?

By the way, point-and-click BIOS isn't new. Before 2000 Compaq already had it, although I'm glad they went back to the traditional BIOS instead of having the configuration GUI on the harddisk.

---

### Post by snova on 2010-06-08
> **Dustin2128 said:**
> I took great offense at that. That said, I agree that a GUI encourages bloat and security holes, imagine viruses screwing up people's BIOS in addition to OS, and NOT getting new systems from windows decay, not to mention a lesser degree of control. The problem is I can see most users endorsing this whereas I would fight it tooth and nail. This sucks.

So you're against this technology based on the belief that unfounded assertions of being "graphical" in the article imply it will be buggy, insecure, and generally horrible?

I don't see the reasoning. In addition, said viruses already exist as proof of concept.

---

### Post by spupy on 2010-06-08
> **new_tolinux said:**
> Ah.... so they skip assembly code......
But isn't assembly the base which makes it possible to run other (C) code?

By the way, point-and-click BIOS isn't new. Before 2000 Compaq already had it, although I'm glad they went back to the traditional BIOS instead of having the configuration GUI on the harddisk.

C code is compiled to machine code, right? Even assembly is compiled I think - what you write as assembly isn't native machine code.

---

### Post by jerenept on 2010-06-08
He means that usability should not necessarily be an important feature of BIOS. It opens up the PEBKAC/ ID tenT risk.

---

### Post by snova on 2010-06-08
> **new_tolinux said:**
> Ah.... so they skip assembly code......
But isn't assembly the base which makes it possible to run other (C) code?

Yes it is, which is why that particular paragraph makes even less sense than the rest of it. I seriously doubt anyone actually still builds a BIOS in assembly.

> By the way, point-and-click BIOS isn't new. Before 2000 Compaq already had it, although I'm glad they went back to the traditional BIOS instead of having the configuration GUI on the harddisk.

So does text-based EFI. The entire article more or less comes down to "Manufacturers are slowly moving to EFI, graphical stuff will continue as it always has, and nobody is going to care except extremely low-level system programmers."

---

### Post by snova on 2010-06-08
> **spupy said:**
> C code is compiled to machine code, right? Even assembly is compiled I think - what you write as assembly isn't native machine code.

Eh? Assembly has a one-to-one correspondence to what most people refer to as "machine code"; i.e. binary. Assemblers exist purely as a programmer convenience.

You could say that the x86 instruction set is "compiled" (or interpreted on the fly?) to the microprocessor*, though.

** Might be incorrect terminology*

---

### Post by Nick_Jinn on 2010-06-08
> **jerenept said:**
> I wonder... will I be able to overclock using this "point and click" stuff? GUIs mostly encourage bloat, imho.


"Bloat" is less and less of an issue when people are walking around with TB hard drives in their netbooks. Its less and less necessary to shave off disk space usage by leaving it as a hackers text based environment. Most people dont care for that outside of the people who like showing that they can.


Unless you are talking about extra RAM usage.....again, people are walking around with 8gb netbooks. An extra 4mb of RAM usage isnt going to ruin anyones day.


A lot of these ideas about saving space and keeping it small are outdated or mostly apply to very old or budget hardware....still a place for it, but making technology more accessible to non geeks should be a bigger priority. Its also more marketable on top of being perfectly ethical.

---

### Post by Nick_Jinn on 2010-06-08
> **Dustin2128 said:**
> I took great offense at that. That said, I agree that a GUI encourages bloat and security holes, imagine viruses screwing up people's BIOS in addition to OS, and NOT getting new systems from windows decay, not to mention a lesser degree of control. The problem is I can see most users endorsing this whereas I would fight it tooth and nail. This sucks.


While I think that bloat is a non issue on modern hardware, especially if it has its own chip to take care of it on the motherboard, I do think that the security holes are a very real issue if they exist.

---

### Post by Dustin2128 on 2010-06-08
> **snova said:**
> So you're against this technology based on the belief that unfounded assertions of being "graphical" in the article imply it will be buggy, insecure, and generally horrible?

I don't see the reasoning. In addition, said viruses already exist as proof of concept.
Not necessarily, just that GUI's imply loss of control as opposed to text based BIOS. If you want to surrender control of your operating system, hey, fine by me, but I like BIOS the way it is. Not everything needs to be complicated by another GUI.

---

### Post by new_tolinux on 2010-06-08
> **Nick_Jinn said:**
> Its less and less necessary to shave off disk space usage by leaving it as a hackers text based environment. Most people dont care for that outside of the people who like showing that they can.
<snip>
A lot of these ideas about saving space and keeping it small are outdated or mostly apply to very old or budget hardware....
I'm not saying that I'm against a BIOS GUI but I'm very much against having that GUI on the harddrive.
Not because of the space it uses, but because of the trouble I went through to restore that setup partition on those Compaqs when users deleted it when they reinstalled their OS and needed something done in that BIOS.

Put a chip in it on which the GUI fits, but in my opinion it goes against all sanity to put something that essential on the harddrive.

---

### Post by jerenept on 2010-06-08
Where swapping out the HDD will remove it. (WTH?)

---

### Post by lisati on 2010-06-08
> **new_tolinux said:**
> Ah.... so they skip assembly code......
But isn't assembly the base which makes it possible to run other (C) code?

Assembly, huh? There's sometimes an extra layer of abstraction between "machine code" and the actual hardware, known as "[microcode]("http://en.wikipedia.org/wiki/Microcode")" - and I'm not thinking of the sense of the word that refers to what most of us call "BIOS". :)

---

### Post by snova on 2010-06-08
> **Dustin2128 said:**
> Not necessarily, just that GUI's imply loss of control as opposed to text based BIOS.

Maybe yours looks different, but my BIOS looks like a fullscreen curses interface. Features are laid out in logical order and simple to manipulate. You're *implying* that by virtue of being presented in another, coincidentally somewhat glitzier fashion, we must therefore lose functionality, which does not follow. Nobody said EFI was by definition graphical either.

> If you want to surrender control of your operating system, hey, fine by me, but I like BIOS the way it is.

It's just firmware. It boots the computer when I turn it on. I'm not losing anything.

> Not everything needs to be complicated by another GUI.

You know, GUI is generally used to *simplify* things. This is probably why they all look like curses.

---

### Post by sixstorm on 2010-06-08
As long as this means a faster boot up time, I'm all for it.

---

### Post by jerenept on 2010-06-08
> **sixstorm said:**
> As long as this means a faster boot up time, I'm all for it.

+1000...

But I don't want some dumbed down garbage. I like editing advanced BIOS settings. I don't want it to ask me "Are you sure?" when I am overclocking a poor helpless Sempron 3000+ to an insane degree, and setting the RAM voltage to "High".

And I do not want it warning me "This computer does not currently have Windows installed." :lolflag:

---

### Post by Dr. C on 2010-06-08
> **snova said:**
> It's just firmware. It boots the computer when I turn it on. I'm not losing anything.

There is the very real danger here that the firmware only permits an "approved" OS, namely Microsoft Windows in the PC case, as is currently the case with most mobile devices or devices such as the PS3. The motivation DRM which was the real reason SONY blocked GNU / Linux on the PS3.

Those of us in the FLOSS community need to be very vigilant about this, since once GNU / Linux gets into a system with the end user having root access it is usually the end of the DRM.

---

### Post by sixstorm on 2010-06-08
> **jerenept said:**
> +1000...

But I don't want some dumbed down garbage. I like editing advanced BIOS settings. I don't want it to ask me "Are you sure?" when I am overclocking a poor helpless Sempron 3000+ to an insane degree, and setting the RAM voltage to "High".

And I do not want it warning me "This computer does not currently have Windows installed." :lolflag:

It's rare that I really go into the BIOS anymore.  I have to be doing some crazy troubleshooting at work to ever go into the BIOS.  Even when updating the BIOS, you can do it from Windows now so there is no reason to go into it.  I just want a faster startup time.

---

### Post by snova on 2010-06-08
> **FineE said:**
> There is the very real danger here that the firmware only permits an "approved" OS, namely Microsoft Windows in the PC case, as is currently the case with most mobile devices or devices such as the PS3. The motivation DRM which was the real reason SONY blocked GNU / Linux on the PS3.

They can already do this. I'm not concerned about changing implementation details.

---

### Post by Yarui on 2010-06-08
> **jerenept said:**
> I wonder... will I be able to overclock using  this "point and click" stuff? GUIs mostly encourage bloat, imho.

In the article there is a screenshot that shows some menu categories, one of which is "OC".  I can only assume that is an overclocking menu, but I may be wrong about that, I didn't actually read the whole article so I don't know if it is mentioned.  I doubt that we need to worry that functionality will be lost, the BIOS menus of computers are already menu-based, so I would imagine the graphical interfaces will have the same options, although they may be rearranged in a way that is easier for new users to find what they are looking for, meaning that it will likely require a bit more menu navigation than the current system.  I can see how that would be annoying to users who are familiar with the menus, having to click on several things to get to where they are going every time.  In my experience, though, going through an unfamiliar BIOS menu often involves checking each menu for the function you are looking for until you find it, so I can't imagine it would be any slower to those unfamiliar with the system they are on, even if that user is experienced in managing his own BIOS.  I also don't often find myself going back to reconfigure my own BIOS regularly, any time I do anything in my own BIOS it has been so long since the last time I did it that I don't remember what menu I need to look in, but that's just me.

> **snova said:**
> No, they're replacing BIOS with something that  functions on the same layer and does essentially the same thing.

I think the user you responded to was referring to the hardware, while you seem to be talking about the software.  The impression I get is that they are replacing the software not implementing some new mechanism in the hardware to take the place of the I/O system, and even if they were, something has to deal with the input and output of the system, so surely it would still be considered an I/O system regardless of whatever changes they made.  Just a silly technicality, but I think the two of you were making slightly different points.

> **Nick_Jinn said:**
> While I think that bloat is a non issue on modern hardware, especially if it has its own chip to take care of it on the motherboard, I do think that the security holes are a very real issue if they exist.

I don't fully agree with the idea that bloat is a non issue, there are times when making something as efficient as possible is important, especially when it is not uncommon for hundreds of programs to be running on a machine at once.  In this case, though, I agree with you.  There is no need to worry about a graphical interface making an impact on performance here.  If it was something that was causing startup times to drop I could understand why some would be upset, but since it only loads when you want to go into it anyway, I doubt it's going to do any harm.

> **Dustin2128 said:**
> I took great offense at that. That said, I agree that a GUI encourages bloat and security holes, imagine viruses screwing up people's BIOS in addition to OS, and NOT getting new systems from windows decay, not to mention a lesser degree of control. The problem is I can see most users endorsing this whereas I would fight it tooth and nail. This sucks.

I took slight offense to that comment as well, although I suppose that the article was probably written for an audience who thinks that way about text based interfaces.  As far as security issues go, I would be surprised if there were any,  although the more complex you make something the more likely you are to  overlook an issue, so I suppose it could be possible.  If they were to include some kind of built in internet-based flashing utility I could see there being some potential for abuse, but that is just speculation.

---

### Post by 98cwitr on 2010-06-08
unless it makes the machine boot faster...I really could care less. BIOS boot is slower than my SSD :?

---

### Post by Nick_Jinn on 2010-06-08
> **new_tolinux said:**
> I'm not saying that I'm against a BIOS GUI  but I'm very much against having that GUI on the harddrive.
Not because of the space it uses, but because of the trouble I went  through to restore that setup partition on those Compaqs when users  deleted it when they reinstalled their OS and needed something done in  that BIOS.

Put a chip in it on which the GUI fits, but in my opinion it goes  against all sanity to put something that essential on the  harddrive.


Good point. It should be on the motherboard instead. There should be a  small bit of memory built in that only the motherboard can access.


> **Yarui said:**
> I don't fully agree with the idea that bloat is a non issue, there are times when making something as efficient as possible is important, especially when it is not uncommon for hundreds of programs to be running on a machine at once.  In this case, though, I agree with you.  There is no need to worry about a graphical interface making an impact on performance here.  If it was something that was causing startup times to drop I could understand why some would be upset, but since it only loads when you want to go into it anyway, I doubt it's going to do any harm.


I cant disagree with that. Of course there are times when being as lean as possible is important, especially if it is cumulative with hundreds or thousands of processes that add up to significant bloat, or when you are trying to be lean for older hardware or special appliance needs. Its not a dead issue, I just dont think its the issue that it used to be when it comes to desktops specifically, especially newer hardware that will be shipped out with 12 gigs of ram and 4 TB of RAM as the standard.

---

### Post by murderslastcrow on 2010-06-08
I wouldn't be surprised if they start booting a light distribution from RAM that has a nice blending effect into whatever OS you choose to boot into. In 10 years it's likely that we'll all be dual-booting in one way or another.

---

### Post by Shining Arcanine on 2010-06-08
> Last month, Seagate revealed to THINQ that a UEFI system would be an essential requirement in order for a PC to boot from a drive larger than 2TB.

They could just modify the old BIOS software to support the newer format. As far as I know, there is no technical need to switch to UEFI for 2TB boot drive support unless vendors refuse to modify their BIOS software.

---

### Post by mmix on 2010-06-09
we don't need stinking commercial bios,
we had coreboot. we need time and good mainboard.

[http://en.wikipedia.org/wiki/Coreboot](http://en.wikipedia.org/wiki/Coreboot)

---

### Post by mobilediesel on 2010-06-09
> **Sporkman said:**
> [http://www.thinq.co.uk/2010/6/8/exclusive-msi-bios-will-be-dead-three-years/](http://www.thinq.co.uk/2010/6/8/exclusive-msi-bios-will-be-dead-three-years/)

It's been at least 6 years since I first read about EFI replacing BIOS within 3 years. It seems like the sudden renewed interest is the result of the ever-increasing size of hard drives.

I wouldn't mind some kind of replacement for the BIOS I'm using now. Whatever this Dell OptiPlex GX110 is using takes at least 35 to 45 seconds just to start looking at the MBR of the boot drive! Kickstart 1.3 on my old Amiga 1000 started loading Workbench WAY faster than that.

---

### Post by Dustin2128 on 2010-06-09
> **snova said:**
> Maybe yours looks different, but my BIOS looks like a fullscreen curses interface. Features are laid out in logical order and simple to manipulate. You're *implying* that by virtue of being presented in another, coincidentally somewhat glitzier fashion, we must therefore lose functionality, which does not follow. Nobody said EFI was by definition graphical either.



It's just firmware. It boots the computer when I turn it on. I'm not losing anything.



You know, GUI is generally used to *simplify* things. This is probably why they all look like curses.

By OS I mean that I often run in text only mode for more power- unrelated to BIOS (sorry half watching T.V. still) but as far as you saying GUIs simplify things.. from my standpoint they don't. Text based is as simple as you can get. Suppose I could always flash some older text based bios but I'd really *really* hate to have to find an exploit to put linux on ____ brand motherboards. It seems we have to agree to disagree though, since you and I seem to disagree on this issue no matter the argument.

---

### Post by rottentree on 2010-06-09
Those screens look ugly :(
I don't have a problem with using modern looking 'BIOSes' hell I think I would even like that and I guess while mouse support doesn't do much it certainly makes it more user friendly.
Though I do find it funny how they justify the move. Yeah 2TB drives are sooo advanced that they even refuse to be used by GUI-less BIOSes :D

---

### Post by DeadSuperHero on 2010-06-09
I think I'm just going to wait for Coreboot to mature a teensy bit more, and switch to that when I have the chance.

---

### Post by SnappyU on 2011-04-17
> **mobilediesel said:**
> It's been at least 6 years since I first read about EFI replacing BIOS within 3 years. It seems like the sudden renewed interest is the result of the ever-increasing size of hard drives.

I wouldn't mind some kind of replacement for the BIOS I'm using now. Whatever this Dell OptiPlex GX110 is using takes at least 35 to 45 seconds just to start looking at the MBR of the boot drive! Kickstart 1.3 on my old Amiga 1000 started loading Workbench WAY faster than that.

I suspect the renewed interest is also due to the newer machines that come with UEFI bios.

---

### Post by ikt on 2011-04-17
"Hell, it's about time"

---

### Post by handy on 2011-04-17
My 2007 model 24" iMac runs the GPT/EFI system. I had to install rEFIt to be able to use GRUB/Lilo & therefore any systems that can be run from such boot loaders.

Apart from having to do that (quick & simple really) & the menu I'm presented with on boot, I wouldn't know it was there.

I've upgraded the 320GB internal drive to a 1.5TB drive & the RAM from 1 -> 6GB without a whisper from the internal system firmware.

Here is a good read for anyone interested in the subject, it has relevant links to the standards authorities behind this "new" scheme also:

[http://developer.apple.com/library/mac/technotes/tn2166/_index.html](http://developer.apple.com/library/mac/technotes/tn2166/_index.html)

---

### Post by Windows Nerd on 2011-04-17
> **Shining Arcanine said:**
> They could just modify the old BIOS software to support the newer format. As far as I know, there is no technical need to switch to UEFI for 2TB boot drive support unless vendors refuse to modify their BIOS software.

There was a technical need, because it was a limitation of the 16 bit BIOS that it could only address 2.2 terabytes.

In any case, the BIOS was long overdue for a recall - it was already a hacked together bits of technology for some time. BIOSes were written in assembly, ran in 16-bit mode, with ACPI and other such extensions hacked with it that made it actually slower, given that most new processors are 64 bit these days. UEFI is written in c, 64 bit, and actually posts much faster than BIOS does.

See for more specifics:

[http://en.wikipedia.org/wiki/Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Extensible_Firmware_Interface)

---

### Post by Quake on 2011-04-18
> **windows nerd said:**
> there was a technical need, because it was a limitation of the 16 bit bios that it could only address 2.2 terabytes.

In any case, the bios was long overdue for a recall - it was already a hacked together bits of technology for some time. Bioses were written in assembly, ran in 16-bit mode, with acpi and other such extensions hacked with it that made it actually slower, given that most new processors are 64 bit these days. Uefi is written in c, 64 bit, and actually posts much faster than bios does.

See for more specifics:

[http://en.wikipedia.org/wiki/extensible_firmware_interface](http://en.wikipedia.org/wiki/extensible_firmware_interface)
+1

---

### Post by Artemis3 on 2011-04-20
Mine has one of those. If you switch to "advanced mode", its layout is very similar to the "horizontal navigation" from the Phoenix and some AMI bioses; and can be done fully with the keybooard. I just has fancier colors, and a bit more clunky interface.

[[img]http://images.hardwarecanucks.com/image/mac/reviews/asus/P8P67PRO/P8P67_PRO_75th.jpg[/img]](http://images.hardwarecanucks.com/image/mac/reviews/asus/P8P67PRO/P8P67_PRO_75.jpg)

As for the boot time, it would be fast but it has to initialize (and show) the onboard Marvell controller (the same one Linux doesn't recognize its IDE (Pata) interface). Also if the power is lost, the motherboard cold resets twice, but thats an asus overclock protect thing (i don't overclock, but it does it anyway).

The "simple" (Easy?) mode tries to show all the info in a single screen, with 3 options for "energy, normal, overclock".

[[img]http://images.hardwarecanucks.com/image/mac/reviews/asus/P8P67PRO/P8P67_PRO_73th.jpg[/img]](http://images.hardwarecanucks.com/image/mac/reviews/asus/P8P67PRO/P8P67_PRO_73.jpg)

Mouse and "Gui" in a bios is nothing new. AMI did it in the 90ies, it emulated a windows 2/3 look; called: AMI WinBios. If you had a mouse attached you could see and move a pointer; otherwise the keyboard worked just fine alone.

[img]http://users.tpg.com.au/buubox01/OCAU/AMI.jpg[/img]

---

