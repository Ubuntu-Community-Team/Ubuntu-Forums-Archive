---
title: "Common Linux Complaints"
date: 2005-12-31
forum: The Cafe
---

### Post by Arktis on 2005-12-31
I'm tired of seeing the same complaints over and over again, so I thought I would address some of the most common ones here in the hope that it will help to bring some people up to speed.

**Complaint #1:** [COLOR="DarkRed"]It doesn't play proprietary media files out of the box![/COLOR]
**Reply:** [COLOR="Blue"] Some distributions do, others do not.  "Purist" distributions don't because that would put a cost on each distributed copy, a cost that would go to the folks who charge for their licenses.  This turns Linux into a source of revenue to support proprietary formats, something that doesn't exactly help open standards.[/COLOR]

**Complaint #2:** [COLOR="DarkRed"]My [insert hardware device here] isn't supported![/COLOR]
**Reply:** [COLOR="Blue"]It's your hardware manufacturer's fault.  If the manufacturer would release Linux drivers or their driver specifications, you wouldn't be so upset.  Don't blame Linux.  People are constantly looking for ways to reverse engineer drivers for companies that don't release Linux drivers or their driver specifications.  Tip your hat to these folks, and thank them for their hard work.[/COLOR]

**Complaint #3:** [COLOR="DarkRed"]Installing programs is too hard![/COLOR]
**Reply:** [COLOR="Blue"]Synaptic is point-and-click installation at it's easiest.  Use apt from the command line if you want to be quicker about things.  If something isn't in the repositories, you can usually download a package for it using your web browser and then install it quickly and easily with dpkg.  Any dependencies are easily satisfied with synaptic/apt-get.
[/COLOR]
[COLOR="SeaGreen"]Where there is some room for complaint is when you can't find a suitable package for your program and you need to install using a source tarball.  However, most often than not, it's as easy as ./configure, make, make install.  The configure script will tell you if you are missing anything when you run it.  If you are missing anything, it's most likely a development package which you can locate using synaptic.  It's not rocket science, but it does takes a bit of learning to be comfortable with.  If you want to be clean about it, use the checkinstall utility instead of the 'make install' command and you can have yourself a package that can be cleanly and easily removed (just in case there's no rules to do a 'make uninstall' command).[/COLOR]

**Complaint #4:** [COLOR="DarkRed"]Linux is not ready for the desktop![/COLOR]
**Reply:** [COLOR="Blue"]Sorry, but it is and it has been for a while now.  A great deal of people, myself included, have been using Linux for their primary desktop OS for a long time now.  We get by just fine.  The reality is that **you** and 75% or more of your fellow computer users (guesstimation) simply aren't ready for Linux.  The nix flavors represent ways of interacting with your computer and a philosophies that are just different enough to disorient, confuse, and frustrate you - especially if you're a long time Windows user.  If you're simply not familiar enough with the kind of thinking involved, "tools of the trade" or you simply just don't like to think too much, you're likely going to claim that it's Linux's fault when you run into initial problems.  The fact that Linux is also under a continual development cycle also tends to give the impression that it's just never quite "there" yet.  See [this]("http://ubuntuforums.org/showpost.php?p=644529&postcount=51") post as well.  I go into more detail there in response to some more LINRFTD posts.[/COLOR]

**Complaint #5:** (by request) [COLOR="DarkRed"]Linux isn't a good gaming platform![/COLOR]
**Reply:** [COLOR="Blue"] Well, yeah it is.  In the true sense, Linux already has all the components that an excellent high performance 3D gaming platform needs.  You wouldn't be able to run all those Windows games on it if it didn't (even if there is a performance hit, which should be expected when you're fitting a square peg into a round hole.).  But in the sense that there aren't nearly as many good/popular games out there specifically designed for Linux or that have Linux ports, there is obviously a problem.  So, to prove a point, here are some of my personal favorites mixed with a few other suggestions (in alphabetical order):[/COLOR]
[COLOR="DimGray"]
**3D Accelerated Games:**

[BZFlag]("http://bzflag.org/") - A 3D First Person Tank Shooter.  The map makers seem to be obsessed with pyramids, though.  Plus there is a map called "spiralzone" in which I could swear they hid the dollar bill on opposite sides... (visible from the HUD's mini-map display) Very fun; I suggest compiling it yourself from source code.

[Doomsday]("http://www.doomsdayhq.com/") - A beautifully designed cross-platform engine capable of using the data files from the old id games (doom series, hexen and heretic).  Graphically, it transforms these old games into something more like Quake 3.  It even has online play!  There is also an [Ubuntu repository]("http://eyagi.bpa.nu/~jamie/doomsday.html").

[FooBillard]("http://foobillard.sunsite.dk/") - The best d*** computer pool game _*ever*_.  It makes me weep.

[id Software's Linux index]("http://zerowing.idsoftware.com/linux/") - They have Linux FAQs for Quake 3 Arena, Quake 4, Doom 3, and Return to Castle Wolfenstein/Enemy Territory.  Thanks, id!

[Legends]("http://www.legendsthegame.net/") - This is a very well made cross-platform clone of Tribes.  It's very fun, but difficult to get good at, and it's main problem right now is that there aren't very many players (yet).  You just have to be sure to play at the proper times to catch everyone.

[Neverwinter Nights]("http://nwn.bioware.com/downloads/linuxclient.html") - Download and Instructions for the Neverwinter Nights Linux client.  A highly rated commercial 3D MMORPG.  I can't personally vouch for this game though, because I've never played it.

[TC:E]("http://www.truecombat.com/intro.php") (True Combat: Elite) - To say that this is a Counterstrike clone wouldn't do it justice.  It's a mod for Wolfenstein Enemy Territory, so it's cross platform and **free** (thanks, id software!).  Sniping is much harder, aiming is done with the actual gun sights instead of HUD cross-hairs, you can lean to the left or right side to peek/shoot around obstacles and corners, and you can even stealthily crawl around on your belly.  Without a doubt, my favorite game for Linux.  Also has easy installation, but I recommend installing to a subdir in your home directory.  You won't need root privileges.

[Unreal Tournament GOTY]("http://princessleia.com/UT.php") - Linux install instructions.

[UT 2003]("http://www.sujee.net/geeky/ut2003.html") - Linux install instructions.

[UT 2004]("http://www.sujee.net/geeky/ut2004.html") - Linux install instructions.

**2D Games:**

[Fish Fillets: NG]("http://fillets.sourceforge.net/") - A very addictive 2D Puzzle game.  It has audio in French but also has subtitles in several different languages.  This one looked kinda ridiculous to me at first, but it turned out to be both amusing and challenging.  I still have yet to beat it.

[XMoto]("http://xmoto.sourceforge.net/") - A cross-platform 2D game where you have to guide a motocross bike to collect all the items on a level before going to the exit.  This is not an easy game!

**Miscelaneous:**

[Linux Game Tome]("http://www.happypenguin.org/") - Good site for keeping up to date with Linux game development or just finding new games.

[LinuX-Gamers.net]("http://www.linux-gamers.net/") - The name says it all.  Check out the forums.

[Transgaming Compatibility Database]("http://transgaming.org/gamesdb/") - For determining what Windows games Cedega can run and how well.[/COLOR]

[COLOR="Blue"]There are a lot more games where these came from.  The list is not meant to be definitive.[/COLOR]

---

### Post by drfalkor on 2005-12-31
this one needs a sticky. Maybe you should add more common complaints ?:smile:

---

### Post by Perfect Storm on 2005-12-31
Nice work Arktis!

---

### Post by meborc on 2005-12-31
yeah.. you haven't mentioned games... games... games... :rolleyes: not that i'm complaining... 10 minutes of ET every day, keeps the doctors away

---

### Post by 23meg on 2005-12-31
It's only a matter of time until those same immature complaints will get voiced on this thread and the usual (useless) arguments will emerge. Just wait and see.

---

### Post by bonzodog on 2005-12-31
I second the sticky suggestion. People ought to be reading that.

But there will ALWAYS be whiners. It's an unfortunate fact of things. If people just learnt to ask questions in the right places before going off on a rant, this forum would be a happier place.

---

### Post by earobinson on 2005-12-31
Good read would like to see more :)

---

### Post by piedamaro on 2005-12-31
I understand the spirit and I agree with the first 2 points to some extent, but I think the majority of users want to do a task and don't care aboput reverse engegneering and whatnot. Sad to say but is the reality, and in this sense I agree that linux is not for everyone as you see. ù
But this statement is older than unix itself: "It's not that Unix isn't user-friendly. It's just that Unix is particular about who its friends are"
I think this is have to change if we are tired "seeing the same complaints over and over again". 
It's growing, and fast, but it still has a long way to go.
My 2 €cents.

---

### Post by gylf on 2005-12-31
[QUOTE=meborc]yeah.. you haven't mentioned games... games... games...[/QUOTE]

hear, hear!  I'm slowly sliding back into Windows for this reason alone...

---

### Post by majikstreet on 2005-12-31
stiiiiiiiiiiiiiiiiiiicky!

---

### Post by meborc on 2005-12-31
[QUOTE=gylf]hear, hear!  I'm slowly sliding back into Windows for this reason alone...[/QUOTE]
i'm so glad that frozen-bubble is enough for me... otherwise it would make me feel the same... but... the other day i was installing a xp box (don't ask why) and i was unable to make the sound work out of the box... doing the same with ubuntu, everything worked... so - i'm not leaving anywhere :p

---

### Post by prizrak on 2005-12-31
Sticky this mofo! Games isn't much of a thing to a good number of people I ran across some statistics a while ago (I don't remember the actual numbers) it said that majority of gamers are console gamers and something like 60% of US households have at LEAST one console. (This was a US study prolly diff in other countries)

---

### Post by opensourcerocks on 2005-12-31
I have heard of those complants and many more, but it has not stoped me from trying linux and learning to use it.

---

### Post by prizrak on 2005-12-31
[QUOTE=opensourcerocks]I have heard of those complants and many more, but it has not stoped me from trying linux and learning to use it.[/QUOTE]
Stops other people, I think the point is more along the lines of it being annoying. People keep whinning about the same thing and saying that Linux sux because of things that in some cases have very little to do with Linux itself.

---

### Post by jdong on 2005-12-31
The most annoying is when people make these assertions, and they havent' even tried Linux yet... Or they're working off their friends' advice who tried Red Hat Linux with kernel 1.6.whatever and it didn't support their hardware.


I started using Linux in early 2001, and am impressed with how Linux has progressed from the early Knoppixes that boot on less than 10% of commonly found PC's to a full-featured OS that runs on more hardware out-of-the-box than Windows.

---

### Post by Arktis on 2005-12-31
I've updated the complaints to add gaming.  I've also taken the liberty of including some games and misc. links. ;)

---

### Post by aysiu on 2006-01-01
[QUOTE=Arktis]
**Complaint #4:** [COLOR="DarkRed"]Linux is not ready for the desktop![/COLOR]
**Reply:** [COLOR="Blue"]Sorry, but it is and it has been for a while now.  A great deal of people, myself included, have been using Linux for their primary desktop OS for a long time now.  We get by just fine.  The reality is that **you** and 75% or more of your fellow computer users (guesstimation) simply aren't ready for Linux.  The nix flavors represent ways of interacting with your computer and a philosophies that are just different enough to disorient, confuse, and frustrate you - especially if you're a long time Windows user.  If you're simply not familiar enough with the kind of thinking involved, "tools of the trade" or you simply just don't like to think too much, you're likely going to claim that it's Linux's fault when you run into initial problems.  The fact that Linux is also under a continual development cycle also tends to give the impression that it's just never quite "there" yet.[/COLOR][/QUOTE] Don't forget that Windows comes preinstalled on most computers--Linux distributions generally do not. That's the main reason it seems "not ready."

---

### Post by ninotob on 2006-01-01
[QUOTE=piedamaro]I understand the spirit and I agree with the first 2 points to some extent, but I think the majority of users want to do a task and don't care aboput reverse engegneering and whatnot.[/QUOTE]

I'm not sure where you are going with this, but the only reason hardware has to be reverse engineered is because the manufacturer won't 1) release linux drivers or 2) release the specs for the hardware so the community can write drivers.  Reverse engineering isn't something people do to make an easy task difficult, it's something they do because there is no other choice.

I feel fortunate that some really talented people will invest the time needed to make hardware work even when the manufacturer refuses to lend a hand.  If any of you hardware hackers are listening:  Thank You.

---

### Post by 23meg on 2006-01-01
[QUOTE=ninotob]If any of you hardware hackers are listening: Thank You.[/QUOTE]I sincerely second that. I'd like to see more newcomers to Linux saying this rather than ranting single mindedly about how hard it is to install drivers for their hardware etc. 

This is not to say noone should criticize anything and that the current state of things is an ultimate ideal, but you should be thankful to these people who invest great amounts of time and energy into making your hardware usable at all when they have no obligation whatsoever to do so.

---

### Post by prizrak on 2006-01-01
I don't think games should be part of complaints. I don't understand WHY people complain that games don't work on Linux. Why not complain about XBOX, PS games not running on Windows? Or PS games not running on XBOX or Gamecube? Take it all the damn way why don't you. It doesn't seem to bother anyone that if you want GT4 you need a PS2 but if you also wanna play Halo 2 you gonna have to get an XBOX, why does it bother people that wehn they bought WoW (hate MMORPG's btw but that's a preference issue) for Windows it doesnt' work on Linux? It was NOT designed for Linux (actually Blizzard made a Linux port and canned it) it's not gonna run on it. It's a remarkable achievement that things like Cedega, Wine and Crossover Office allow you to run Windows applications (including games). I don't see a problem with games not running on Linux, they aren't supposed to. The OS isn't responsible for it, if you really, really, really, really want PC games you can dual boot (chances are your Windows came with the comp anyways) and treat Windows as a console for your gaming. There are actually many people on the forum that said they are running Windows w/o network support just so they can play games and use Linux for everything else. 
Sorry, this kinda turned into a rant it's just really annoying to see double standards.

P.S. Keeping with the previous two posters, I thank every single person who ever worked on a single line of code for this wonderful OS as well as any othe FOSS piece of software. I also thank every single person that ever took the time out of their life to help someone with a computer problem for free be it an FOSS system or proprietary. You guys are what FOSS is all about, even if you don't use it, thank you.

---

### Post by Curlydave on 2006-01-01
One thing you have to conisider: It doesnt' matter whose fault it is that most modern games don't work on Linux, or that certain hardware doesn't function properly. Sure, you can often correctly blame the manufacturer or developer, but the simple fact of the matter is knowing that doesn't help at all, and won't make your favorite games or hardware suddenly work on Linux.

---

### Post by poofyhairguy on 2006-01-01
[QUOTE=Curlydave] Sure, you can often correctly blame the manufacturer or developer, but the simple fact of the matter is knowing that doesn't help at all, and won't make your favorite games or hardware suddenly work on Linux.[/QUOTE]

Knowing helped me. It was the first step. The second step was top sell my incompatible hardware on Ebay and buy compatible stuff the same way. Next step was to sell or give me Windows games away (except one) and buy a Gamecube.

Now I a Windows free with a little work but almost no sacrifice of function.

---

### Post by TeeAhr1 on 2006-01-01
**#6: I can't run (Photoshop, MS Office, insert your gripe here) on Linux.**  True enough.  But you can probably run [something better]("http://www.ubuntuforums.org/showthread.php?t=33183").

(Special thanks to Poofyhairguy for the list, and my girlfriend for the complaint.)

---

### Post by piedamaro on 2006-01-02
What I'm saying is that I second the spirit of the thread, because I don't like to see people whine, but I'm afraid that someone will become even more upset with linux reading this. It would be nice if we could pass this idea really trying to explain why things work in this way, without "if u don't like unix, it's your fault" attitude, as I said, I think it's old.

p.s. I know what reverse engeneering is, and of course I'm thankful to who made possible to run "closed" hardware on linux.

---

### Post by prizrak on 2006-01-02
I think the most annoying thing is that while people percieve Linux based OS's as a competitor for Windows (which isn't bad in itself) they hold Linux to a higher standard. When a USB kbd driver crashes in Windows and the entire OS is brought down with it people reboot and say nothing. If the same driver crashes in Linux and you need to unplug and plug the kbd back in (or restart) people start screaming that Linux is not ready for the desktop. Yes there is hardware it does not support but there is plenty it does. I personally been using Linux of and on for like 6 years now and never had it not recognize my hardware on various machines. Right now I got 2 machines a laptop (with wireless) and desktop with all the hardware recognized straight out of the box (and I didn't get either with Linux in mind) the only thing that took some fiddling was my Lexmark Z25 (which took all of 20 minutes to set up by following a how-to) I even got the CUPS network sharing online and NFS file sharing. The only thing that I cannot do that Windows can is play some games, neither of my machines has power enough to run the newest games anyway and DOSbox runs PERFECTLY on Linux ;) Oh and jDoom is da shiznit ;)
It is obviously possible to have a completely working Linux desktop that enables you to do everything you need even by chance if you put some thought into it you will see what Trusted Computing (^_^) is really about. It's about me trusting my computer not to give all my private info and to work in the manner specified ;)

---

### Post by 23meg on 2006-01-02
[QUOTE=piedamaro]It would be nice if we could pass this idea really trying to explain why things work in this way, without "if u don't like unix, it's your fault" attitude, as I said, I think it's old.
[/QUOTE]There's only a limited number of times one can explain why things work in the particular way they do; past that, one grows weary of explaining the same things that have been explained many times already, and it's useful to point people to threads such as this. If people need explanations, they will find explanations by asking around, searching, questioning, but not whining / bashing / trolling / complaining unconstructively.

The attitude here is more like "If you don't like *nix and don't plan on contributing to improve the aspects you're not satisfied with, don't use it. And don't whine and bash and troll either."

---

### Post by aysiu on 2006-01-02
[QUOTE=prizrak]I think the most annoying thing is that while people percieve Linux based OS's as a competitor for Windows (which isn't bad in itself) they hold Linux to a higher standard.[/QUOTE] Amen. People will put up with mysterious errors, multiple reboots, applications crashing, whatever... as long as it's Windows. One Quicktime video doesn't play in Ubuntu out-of-the-box, and people go running for the hills.

---

### Post by piedamaro on 2006-01-02
[QUOTE=23meg]There's only a limited number of times one can explain why things work in the particular way they do; past that, one grows weary of explaining the same things that have been explained many times already, and it's useful to point people to threads such as this. If people need explanations, they will find explanations by asking around, searching, questioning, but not whining / bashing / trolling / complaining unconstructively.

The attitude here is more like "If you don't like *nix and don't plan on contributing to improve the aspects you're not satisfied with, don't use it. And don't whine and bash and troll either."[/QUOTE]

I agree totally, using this thread to point people at is useful, I was afraid it would be understood like: "read here before you whine noob" and for me it's ok too, as long as "you're not ready for linux" it's omitted. 
Why not something on the lines of "linux doesn't fly this way", etc.
Only my 2 cents in the end it's your will :)

---

### Post by ardchoille on 2006-01-02
Awesome thread!!! Thank you Arktis and I totally agree, this thread should be a sticky. I hear the same tired old complaints and I reply with mostly the same things Arktis said. I have been using Linux for about four years now and there isn't anything I was able to do on Windows that I can't do on GNU/Linux - in fact Linux can do much more.
[B]
Good work![/B]

---

### Post by JeffS on 2006-01-02
Linux is a spectacular desktop.  Most stuff "just works".  Occasionally, some hardware is not supported, but that is becoming more and more rare.  Linux gives you choice, including a very "windows-like" feel with distros like Xandros and Linspire (which also, btw, come with all the proprietary stuff like Java, Flash, MPS, etc).  

And someone can choose a more "purist" distro, that's still easy to use (and downloading the proprietary stuff is trivial), like Ubuntu.  

Linux gives you tons of great free software (which often works as well or better than proprietary equivelants), and many proprietary titles have Linux versions (like Adobe Acrobat), and if there isn't a Linux version, stuff like CrossOver Office (not only MS Office, but also Photoshop, Quicken, and many more), Win4Lin (runs Win9x in emulation, thus all titles targeted for that platform will run), and Cedega (tons of Windows games). will run most major Windows titles.  

Finally, Linux has a vastly superior "out of the box", fresh install experience to Windows, simply because it detects the hardware and loads the drivers automatically (well, with most distros), and Widows does not (you have to have a hardware driver CD from the PC vendor, or manually search, download, and install the drivers yourself).

I just laugh when people say "Linux isn't ready for the desktop".  But I just remind myself that those people are usually either speaking from ignorance (no true Linux experience), or they are paid Microsoft astroturfers (a common occurence these days), or they are among the few who have had some problems, and are just frustrated.

Linux is a great desktop, and an even better server, and a great embedded OS as well. :D

---

### Post by Arktis on 2006-01-03
I'm glad to see that this thread has been recieved well.  I was somewhat afraid that it might become just another backyarded topic. :D 
> using this thread to point people at is useful, I was afraid it would be understood like: "read here before you whine noob" and for me it's ok too, as long as "you're not ready for linux" it's omitted.
Why not something on the lines of "linux doesn't fly this way", etc.
Only my 2 cents in the end it's your will
I can understand that.  I should make it clear that I don't want anyone to think that if you have complaints or think that Linux could use something additional that you're automaticly wrong.  That would go against the spirit of shared responsibility for the growth/progress of open source, now wouldn't it?  This thread is only about trying to curtail the unreasonable redirection of problems that Linux faces onto Linux itself, when in fact it is for the most part a victim of nasty circumstance and what are in my opinion several missjudgements due to a lack of understanding.  In sharing that perspective, I hope that this will encourage fresh users to take their difficulties with a grain of salt and perhaps make a commitment to take a small part in the further adoption of Linux by the masses.  That would solve a lot of these difficulties. 

Thanks everyone for your attention and contributions.  :D

---

### Post by egon spengler on 2006-01-03
[QUOTE=prizrak]When a USB kbd driver crashes in Windows and the entire OS is brought down with it people reboot and say nothing. If the same driver crashes in Linux and you need to unplug and plug the kbd back in (or restart) people start screaming that Linux is not ready for the desktop. [/QUOTE]

Exactly, right now at work we run XP and our printer has been giving us loads of hassle, ask anyone and they would tell you it's a printer problem. Let a printer not work with a version of linux and you'll get 9 pages of why Linux is "not ready"

---

### Post by valnar on 2006-01-04
I didn't read this whole thread, but I'll add my 2 cents.

> Complaint #3: Installing programs is too hard!

True if its not in the repositories.  Sorry, but with all the different versions of Linux out there, it will never be as simple as Windows by definition.  Windows is a single OS, and all programs for Windows work on it.  Installshield and MSI files don't get any easier, including Synaptic.

I tried just the other day to install Win4lin and VMWare.  Still working on Win4lin.  'Need to patch the Kernel and it's not working right.  You think the average Joe 6-pack can do that?

Linux, in all its' distributions pride's itself on the diversity of the operating system.  Different flavors, different Window managers, different package formats, etc.  Linux developers embrace this - users do not.  I repeat, users do not.  Anyone reading this reply is not your average user.  The very thing that make Linux great is its biggest thorn.  In order to make it better, you'd have to become more like Windows......  One version for everything.  :o 

Robert

---

### Post by prizrak on 2006-01-04
[QUOTE=valnar]I didn't read this whole thread, but I'll add my 2 cents.



True if its not in the repositories.  Sorry, but with all the different versions of Linux out there, it will never be as simple as Windows by definition.  Windows is a single OS, and all programs for Windows work on it.  Installshield and MSI files don't get any easier, including Synaptic.

I tried just the other day to install Win4lin and VMWare.  Still working on Win4lin.  'Need to patch the Kernel and it's not working right.  You think the average Joe 6-pack can do that?

Linux, in all its' distributions pride's itself on the diversity of the operating system.  Different flavors, different Window managers, different package formats, etc.  Linux developers embrace this - users do not.  I repeat, users do not.  Anyone reading this reply is not your average user.  The very thing that make Linux great is its biggest thorn.  In order to make it better, you'd have to become more like Windows......  One version for everything.  :o 

Robert[/QUOTE]

Joe 6Pack won't be installing VMware I can guarantee that :) I must say there are a couple of programs not in the repos that I needed/wanted and all of them had a .rpm package at the very least. Those are trivial to install, it's not a double click but that's being worked on. I only installed 2 non-rpm packages one was Netbeans/java bundle a .bin file that works exactly like an .exe in Windows and another was an alpha of DC++ from CVS, neither of those are for an average user anyway and only one was more or less not trivial to install.

---

### Post by Tuf on 2006-01-09
I dont think that people that come to forums looking for help are whining. If you are blue in the face from answering the same question, don't answer :/

But if you think that most people think that they are there for their computers and not the other way around I think you are mistaken. Theres a learning curve to use Linux. I am going through it right now.  Most people have been using Windows forever.

I dont think its about is Linux better than Windows, because clearly its not.  Windows isn't better than Linux either. They are different. I am very interested in the advantages that Linux offers.  As more software becomes available for Linux it becomes a viable choice for more and more people.

I think instead of beating on the people that are interested in joining the Linux Community and understanding that a good deal of them are frustrated before they even register for the forum that you should either offer help if you have any of just take your mom's advice. If you dont have anything good to say ....

---

### Post by aysiu on 2006-01-09
[QUOTE=Tuf]I dont think that people that come to forums looking for help are whining. If you are blue in the face from answering the same question, don't answer :/

...

I think instead of beating on the people that are interested in joining the Linux Community and understanding that a good deal of them are frustrated before they even register for the forum that you should either offer help if you have any of just take your mom's advice. If you dont have anything good to say[/QUOTE] I've read a lot of posts on these forums, and I can tell you right now that there are a lot of people asking for help... and then there are a few people who just whine and complain. The two are different things.

Stick around here for a while. You'll notice that when folks ask for help, they get it, and not begrudgingly.

When folks complain, they get annoyed responses, and rightly so.

I'll give you two examples to highlight the difference:

**Whining and complaining**: Ubuntu sucks. Linux isn't ready for the desktop. Why do I have to type in commands? Why can't everything just work like in Windows.

**Asking for help**: For some reason, Ubuntu doesn't seem to play my MP3s. What can I do to get Ubuntu to see my MP3 files or play them? Any help is much appreciated.

---

### Post by poofyhairguy on 2006-01-09
[QUOTE=Tuf]
I dont think its about is Linux better than Windows, because clearly its not.  Windows isn't better than Linux either. They are different. I am very interested in the advantages that Linux offers.  As more software becomes available for Linux it becomes a viable choice for more and more people.
[/QUOTE]

Wow. You are right on!

---

### Post by Arktis on 2006-01-09
Can't say I dissagree.  I will add the point that in one sense, Windows and Linux are like two opposite sides of the same coin.  The two sides are Open and Proprietary.  I think one is better than the other, but both can serve good purposes and both can be exploited for bad purposes.  I just think that currently, proprietary is being primarly used for the advancement of greed,  accomplished by restrictions/lockdowns/legal maneuvering, so Linux is obviously going to be my symbol for the "good guy".  I'm such a steer...

---

### Post by donjuan on 2006-01-09
We can also point those people who want Linux to be Windows here: [http://www.reactos.org/xhtml/en/index.html](http://www.reactos.org/xhtml/en/index.html)

---

### Post by scaine on 2006-01-09
[QUOTE=prizrak]I don't think games should be part of complaints. I don't understand WHY people complain that games don't work on Linux. Why not complain about XBOX, PS games not running on Windows? Or PS games not running on XBOX or Gamecube? Take it all the damn way why don't you.[/QUOTE]

They complain because they have people telling them that Ubuntu (or Linux, whatever) is ready for the desktop.  It isn't, if all that person does it cruise the net and play games.  Which is a huge chunk of people - probably mostly kids.  Arktis lists a good many supported games for Linux.  That's great - it represents an absolutely tiny fraction of the latest games to hit the stores though.  If it wasn't for ID in fact, commercial support for games in Linux would be near non-existant.

You'll no doubt argue that we're better off without these kids.  Maybe you're right.  But for them, Linux isn't desktop-ready.  That's all.

I'd also argue against the desktop-readiness from a corporate angle.  If I tried to get even just my team of two to try ANY Linux distro, there would be pandemonium.  And nope - training isn't an issue here.  Connectivity into commercial back end systems like Exchange and support for Checkpoint, Cisco and other bespoke products would be the main gripes.

Of course, that's assuming dropping in a linux desktop to our predominantly Windows environement, which is pretty unfair.

I do agree with the spirit of the anti-complaint though - I love my desktop on Ubuntu and it's certainly ready for me.

[QUOTE=23Meg]
It's only a matter of time until those same immature complaints will get voiced on this thread and the usual (useless) arguments will emerge. Just wait and see.[/QUOTE]

Isn't that what Community Chat is for? ;)

---

### Post by poofyhairguy on 2006-01-09
[QUOTE=scaine]They complain because they have people telling them that Ubuntu (or Linux, whatever) is ready for the desktop. [/QUOTE]

I see your point....but what else are we supposed to say? It IS ready for my desktop.

> 
I'd also argue against the desktop-readiness from a corporate angle.  If I tried to get even just my team of two to try ANY Linux distro, there would be pandemonium.  And nope - training isn't an issue here.  Connectivity into commercial back end systems like Exchange and support for Checkpoint, Cisco and other bespoke products would be the main gripes.


Depends. It makes a good secretary's desktop or is a cheap way to turn old machines into dumb terminals.

---

### Post by egon spengler on 2006-01-09
[QUOTE=scaine]They complain because they have people telling them that Ubuntu (or Linux, whatever) is ready for the desktop.  It isn't, if all that person does it cruise the net and play games.  Which is a huge chunk of people - probably mostly kids.  Arktis lists a good many supported games for Linux.  That's great - it represents an absolutely tiny fraction of the latest games to hit the stores though.  If it wasn't for ID in fact, commercial support for games in Linux would be near non-existant.

You'll no doubt argue that we're better off without these kids.  Maybe you're right.  But for them, Linux isn't desktop-ready.  That's all.[/QUOTE]

Ok, so now the definition of "desktop ready" is how plentiful the suply of games is? I am not the most au fait with all of the various operating systems but am I right in thinking that :

a) macs also have barely any commercial games available?

b) macs are seldom, if ever, declared to be not ready for the desktop

---

### Post by aysiu on 2006-01-09
[QUOTE=scaine]They complain because they have people telling them that Ubuntu (or Linux, whatever) is ready for the desktop.  It isn't, if all that person does it cruise the net and play games.  Which is a huge chunk of people - probably mostly kids.[/QUOTE] [It all depends on how you define "ready for the desktop,"](http://www.ubuntuforums.org/showthread.php?t=113874) of course.

---

### Post by scaine on 2006-01-10
[QUOTE=egon spengler]Ok, so now the definition of "desktop ready" is how plentiful the suply of games is? I am not the most au fait with all of the various operating systems but am I right in thinking that :

a) macs also have barely any commercial games available?

b) macs are seldom, if ever, declared to be not ready for the desktop[/QUOTE]

For many people, simply yes.  I believe that it is the supply of games that will determine how successful a desktop is in the home.

It's a bit like the supply of porn will determine how successful a video format is (some say it's the only reason the awful VHS beat the far superior Beta - the porn came out on the cheaper to produce VHS format).  It's not pretty, but it's the way the world works.

And is the Mac ready for the desktop in the home?  For those kids - of course not, for the same reasons, and then some (having to buy Mac hardware at a premium compared to cheaper PC counterparts is another for example).

How many kids do you hear about pestering their parents to buy them a Mac, or a PC with Linux on it?  None.  They're shallow little creatures who want to play F.E.A.R, World of Warcraft and Sims2.

However, as they grow up, hit university, or whatever, they'll have learnt about computers and how they work - such a shame that they've learnt it all on Windows, where the games live.

---

### Post by nocturn on 2006-01-10
[QUOTE=Curlydave]but the simple fact of the matter is knowing that doesn't help at all, and won't make your favorite games or hardware suddenly work on Linux.[/QUOTE]

This is the a chicken and egg problem...  Commercial games will only come out for Linux once it gains critical mass (like hitting 10% of the OS market).  The same goes for drivers where we are already seeing commercial companies like ATI and Nvidia picking it up.

My point is that without enough users, the games won't come.  And without the games, many users won't come.

---

### Post by nocturn on 2006-01-10
[QUOTE=aysiu]Amen. People will put up with mysterious errors, multiple reboots, applications crashing, whatever... as long as it's Windows. One Quicktime video doesn't play in Ubuntu out-of-the-box, and people go running for the hills.[/QUOTE]

That is what I find the most amazing.  You'd think that when they pay so much for Windows+Office+AntiVirus+Firewall+... you'd think they have a 0-tollerance to failures...

---

### Post by nocturn on 2006-01-10
[QUOTE=valnar]
True if its not in the repositories.  Sorry, but with all the different versions of Linux out there, it will never be as simple as Windows by definition.  Windows is a single OS, and all programs for Windows work on it.  Installshield and MSI files don't get any easier, including Synaptic.
[/quote]

Yes, but in Windows each install can have a different look which is more difficult to learn then a unified way like synaptic.
Additionally, windows does not have any package management, if you download a prog and it pops up VBRUN4.dll is missing, that's it.

Programs just dump libraries in system(32), often overwriting newer versions, so in what state is your system actually?

Uninstalling in Windows is nearly impossible because of the above reasons (you can uninstall but a lot of residue remains).

> 
I tried just the other day to install Win4lin and VMWare.  Still working on Win4lin.  'Need to patch the Kernel and it's not working right.  You think the average Joe 6-pack can do that?


I never had to compile to run VMWare in the past.  But running emulation software is not for average joe.  He does not perform such complex tasks on Windows, so why require it on Linux...

> 
Linux, in all its' distributions pride's itself on the diversity of the operating system.  Different flavors, different Window managers, different package formats, etc.  Linux developers embrace this - users do not.  I repeat, users do not.  Anyone reading this reply is not your average user.  The very thing that make Linux great is its biggest thorn.  In order to make it better, you'd have to become more like Windows......  One version for everything.  :o 


Users do not, no.  That is why Linux needs OEMS to thrive.
Distributions and OEMS can make a usefull selection of a desktop and some basic software so that most users do not have to do this.  Ubuntu shines at this (giving a completely usable desktop on first install).  But to make this selection, alternatives need to be available.

The one thing for all has given Windows users a 5 years old OS on modern computers and a browser that hasn't been updated for as long as most can remember (tabbed browsing, ad blocking, ...?).

---

### Post by nocturn on 2006-01-10
[QUOTE=scaine]
I'd also argue against the desktop-readiness from a corporate angle.  If I tried to get even just my team of two to try ANY Linux distro, there would be pandemonium.  And nope - training isn't an issue here.  Connectivity into commercial back end systems like Exchange and support for Checkpoint, Cisco and other bespoke products would be the main gripes.

Of course, that's assuming dropping in a linux desktop to our predominantly Windows environement, which is pretty unfair.
[/QUOTE]

I'm glad you admitted the unfair equation in your last statement.  Linux is ready for the corporate desktop, but it has to be either a new setup or a planned migration.  

In my previous job, we used Thin Clients with a Solaris server running Ximian Desktop 1.0 and Evolution as a productivity suite, it worked fine and everyone was happy.

We even had such advanced features as preparing a presentation on my desk, pulling out the smartcard, plugging it in to a terminal connected to a beamer and giving the presentation with my own desktop still open...

The *Nix dogma is very different from Windows.

---

### Post by scaine on 2006-01-10
[http://www.silicon.com/publicsector/0,3800010403,39155468,00.htm](http://www.silicon.com/publicsector/0,3800010403,39155468,00.htm)

That's a good link to a very (very!) short article on Linux in the education sector.  I'll be keeping a close eye on this one - it could have massive repercussions.

Still have the game problem though... but it's a step in the right direction - people aren't going to try Ubuntu (for example) if they don't know it exists.

---

### Post by egon spengler on 2006-01-10
[QUOTE=scaine]For many people, simply yes.  I believe that it is the supply of games that will determine how successful a desktop is in the home...

...And is the Mac ready for the desktop in the home?  For those kids - of course not, for the same reasons, and then some (having to buy Mac hardware at a premium compared to cheaper PC counterparts is another for example).

How many kids do you hear about pestering their parents to buy them a Mac, or a PC with Linux on it?  None.  They're shallow little creatures who want to play F.E.A.R, World of Warcraft and Sims2.[/QUOTE]

Well again, this is something that I do not know for fact but I was under the impression that pc gaming was considered somewhat of a niche market and that most real gaming was done on console. I don't know many kids, my only interaction with them comes on public transport, but based on that neglible contact their don't seem overly wrapt with pc games either. Of the young adults I know who play games I can think of only one who plays on pc, he still has a ps2 though.

Anyway, the fact that you need to keep readjusting your position sort of reveals the bankruptedness of "Linux is not ready for the desktop" as a blanket statement (which is the way most people apply it). The same criteria you use to declare Linux unready should by rights also apply to Mac but of course noone wouldbe outlandish enough to declare macs not ready and so you have to throw in some provisos and context dependent escape clauses. "Mac ain't ready for 13-16 year olds every third thursday if they've had less than 2/5 of their recommended calcium allowance and it's sunny outside"

---

### Post by Arktis on 2006-01-10
[COLOR="DimGray"]So you're saying that ready for the desktop is subjective to the person using the OS, giving examples like **for gamers, Mac isn't ready for the desktop?**  That would be true if Mac OSX was a gaming OS, but it isn't.  Ready for the Desktop refers to an operating system's ability to do it's job.  What job is that?  Depends on what it was designed for.  There are some basic things that are fundamental to any OS performing it's job, though.[/COLOR]

#1.   Work on conventional hardware.  The stuff most everyone has.  It's conditional to everything else.  
#1a. Be stable.
#2.   Functionality.  You know, the mechanisms present for getting work done on it.  That means two criterea:  
#2a. The ability to efficiently process information without crashing (see #1a.).
#2b. Some kind of logical interface between itself and the user.
#3.   Software that makes use of the OS's functionality in order to complete the work you need the computer for.

All these conditions have been MORE than met for Linux.

[COLOR="DarkRed"]Then along comes Joe Anyuser.  He's sits down in front of the machine and starts to use it.  He thinks it needs more games to be ready, something the OS doesn't require to do it's job.  Suzie Everygal comes along and wants it to be more like windows, something the OS doesn't require to do it's job and wasn't designed for.  Billy Someguy comes along and wants it to run windows software, something the OS doesn't need to do it's job and wasn't designed for.  Jenny Generic comes along and wants it to play certain restricted formats out of the box even though she can add the functionality herself, and it's something that the developers can't afford to pay for.  Bobby Unreal comes along and wants it ALL.  So they all say, **"Linux isn't ready for the desktop!** [because it doesn't have these extra things or doesn't behave the way I think it should.].".
[/COLOR]
[COLOR="DarkBlue"]Wrong.  Linux does it's job and it does it's job well.  It's ready.  It's got an excellent CLI, several different featureful (and featureless depending on your tastes) GUI's to choose from, it's stable, it works on most hardware, there's tons of software to choose from, it's modular, and it even has wonderful gaming functionality.  Be it programming or word processing or image editing or any other work you can think of that a computer is used for, Linux can do it.  IT-IS-READY.[/COLOR]
[COLOR="DarkGreen"]
If you still don't understand, let me put it to you this way:  Microsoft has the goal of it's OS being used by as many people as possible.  It caters to the lowest common denominator.  A tool that holds your hand for you.  Linux developers do not have the goal of profit.  It's not a corporation.  So Linux does not have to be a tool that holds your hand, it just has to be a good tool period.[/COLOR]

[COLOR="DimGray"]If you want hand holding, there are people on the forums here that will be happy to accommodate... for a while.  Then it's up to you to become a good tool user.[/COLOR]

**Edit:**  I've updated the complaints again so that The "not ready for the desktop" one contains a link to this post.  I've also gone back and re-edited this post to try and keep people from feeling insulted.  :razz:

---

### Post by J-B on 2006-01-10
I agree with you on some points and disagree on others.  I agree that people should quit complaining and start learning, if they want to use linux.  If not, then they should go back to Windows.  It's as simple as that.   There is a learning curve within any transition, and with linux that learn can at times be steep, but I think just from my meager experience that anyone can learn to use it, provided they put forth the time and effort to do so.  If not...oh well.  

However, I disagree that MS catering to the lowest common denominator is a bad thing.  The lowest common denominator does not necessarily mean "the stupidest computer users", rather in alot of cases it means the most uneducated computer user.   PCs have not been around that long (comparitively speaking), and there are alot of people, especially older people, who didn't grow up with them they way my generation did (I'm 24).   These people need to be educated or they need to be catered to.  Just because they don't know everything about computers that you do, doesn't mean they're stupid.  

You say that MS' goal is to be on every desktop, but that that is not the goal of Linux.  I disagree with you here too.   The people who put their time and effort into coding and such do so of their own free will with no compensation whatsoever.  I doubt that they would do that if they didn't want people to use it.   Or if they only wanted a tiny percentage of people to use it (because let's face it, computer savvy people still aren't the norm).  I personally think having a free OS, and tons of free software on every computer in the world is a totally worthy goal.  I bet there are alot of people working within the linux community who would agree.  

I'm totally new to linux, and there are still tons of things I don't know how to do.  I personally am very grateful to the people within this community who have helped me get started.  I'm esepecially grateful that not every one in this community seems as exasperated by those of us not in the know yet, as you seem to be.  

Just my two cents.

---

### Post by TeeAhr1 on 2006-01-10
[QUOTE=scaine]eo format is (some say it's the only reason the awful VHS beat the far superior Beta - the porn came out on the cheaper to produce VHS format).  It's not pretty, but it's the way the world works.[/QUOTE]
[offtopic]Whoa.  That was profound, I'd never heard that idea before.[/offtopic]

---

### Post by aysiu on 2006-01-10
[QUOTE=J-B]
However, I disagree that MS catering to the lowest common denominator is a bad thing.  The lowest common denominator does not necessarily mean "the stupidest computer users", rather in alot of cases it means the most uneducated computer user.   PCs have not been around that long (comparitively speaking), and there are alot of people, especially older people, who didn't grow up with them they way my generation did (I'm 24).   These people need to be educated or they need to be catered to.  Just because they don't know everything about computers that you do, doesn't mean they're stupid.[/quote] People who don't know anything about computers are almost always better off with Linux (as opposed to Windows), but someone has to install and configure it for them (just as in Windows--usually "someone" like Dell or HP).

> 
You say that MS' goal is to be on every desktop, but that that is not the goal of Linux.  I disagree with you here too.   The people who put their time and effort into coding and such do so of their own free will with no compensation whatsoever.  I doubt that they would do that if they didn't want people to use it. I don't think you can make generalizations like this. Some Linux distributions *do*, in fact, want to conquer the desktop market. Others want the server market. Some just want to be good for a niche desktop. It all depends on the distribution.

---

### Post by TeeAhr1 on 2006-01-10
[QUOTE=aysiu]People who don't know anything about computers are almost always better off with Linux (as opposed to Windows), but someone has to install and configure it for them (just as in Windows--usually "someone" like Dell or HP).[/QUOTE]
I totally agree.  I've only been using Ubuntu for a few months, but it's obvious right away; it's a hell of a lot harder to really hose your system with Linux (especially Ubuntu; sudo saves lives).  I encourage my friends to switch partly out of ideology, partly because I'm sick and tired of dealing with it when they break their machines.

---

### Post by Arktis on 2006-01-10
[QUOTE=J-B]You say that MS' goal is to be on every desktop, but that that is not the goal of Linux.  I disagree with you here too.   The people who put their time and effort into coding and such do so of their own free will with no compensation whatsoever.  I doubt that they would do that if they didn't want people to use it.   Or if they only wanted a tiny percentage of people to use it (because let's face it, computer savvy people still aren't the norm).  I personally think having a free OS, and tons of free software on every computer in the world is a totally worthy goal.  I bet there are alot of people working within the linux community who would agree.[/QUOTE]

Perhaps I should have been more precise here.  So I will elaborate.  Since the people who make Linux are not out for profit, they don't need to gear it towards the lowest common denominator.  All they have to worry about is that it works well, performing it's functions - it's jobs.  It does this.  I'm certain they would like people to use Linux, yes.  But they don't necesarily need to try and dumb things down like the Windows developers do.  Is this good or bad?  That's up to you to decide.  But it certainly does NOT translate to "Linux isn't ready for the desktop.".

But to those of you who want an open source windows clone that will run windows software, I refer you to [this]("http://www.reactos.org/xhtml/en/index.html").

**Edit:** ah, I see donjuan posted this link as well.  :smile:

---

### Post by scaine on 2006-01-10
Ah, well, everyone seems to have latched on to my games example and conveniently forgotten the corporate example.

And many are putting words into my mouths too - I didn't disagree with "Linux is not ready for the desktop".  It is for me, remember?  In fact, I just qualified it - I said "Linux is not ready for everyone's desktop".  Sweeping generalisations are usually a bad thing and this case, paint the wrong picture.

I sincerely hope this thread doesn't get stickied to be honest.  If I was complaining about something which I think ought to be better in Linux, and someone linked me to such an insulting response, I'd be outta here.  Maybe thats the point though.

I do notice that Arktis has taken out the Synaptic "This is laughable" line - thank goodness.  If I came from the Autopackage thread (dealing with the fact that proprietary software is insanely counter intuitive / impossible to install on Linxu) to this one and read that paragraph, I'd be on the rampage for sure!

And don't get me started on that "Linux is not Windows" thread a few people have linked.  The tone of the document alone grates just enough to get your teeth grinding, and then it lashes out with the examples do more harm than good.  Vi, anyone?  The author has mistaken the phrase "user-friendly" for "intuitive"

Honestly, link newbies to that inane drivel and this complaints thread and watch they're fragile spirits fade away one by one.  Like I say, maybe that's the point.

---

### Post by aysiu on 2006-01-10
[QUOTE=scaine]If I was complaining about something which I think ought to be better in Linux, and someone linked me to such an insulting response, I'd be outta here.  Maybe thats the point though.[/QUOTE] [Complaining doesn't fix problems. It just annoys people.](http://www.ubuntuforums.org/showthread.php?t=78741)

---

### Post by Maupertus on 2006-01-10
Although I don't think the remarks about "people who want a windows clone" are appropiate in this thread (or indeed at all) as aysiu has pointed out, there are a number of Distro's that aim to be just that, and are popular because of it, I've even used a couple of them and liked them (although I found them wanting in the end) when I don't have warm feelings toward Windows. 

*Complaint I've heard about Linux:*
Yeah, but what if I have a problem, there is no support and I can solve some simple problems in windows because I know how "The System" works!

Reply:
1) Community support for most Distro's I know is just great where each question is regarded as a serious one and often a problem will be solved by this community.
2) Have you ever tried to get Windows or Microsoft support as a private user? Haver your ever visited the MSCommunity? If the awnser to these questions is "No" then you are a very lucky person. I've never heard of a case where a problem was succesfully solved by MS, most people use sites created by tweakers.

(Note: This is the complaint that I always get when trying to get the Uni to adopt Linux as the OS for the student workstations and Laptops. That and the fact that they don't know how to set up the network, which is now done by NovellApplications)

---

### Post by Arktis on 2006-01-10
[QUOTE=scaine]Ah, well, everyone seems to have latched on to my games example and conveniently forgotten the corporate example.[/quote]Your corporate example appears to me as more of a complaint about there being no Linux software (that you know of) to connect to those backends.[QUOTE=scaine]"Linux is not ready for everyone's desktop"[/quote]The statements "Most people aren't ready for Linux" and "Linux isn't right for everyone"  are far, far more appropriate and have the added bonus of being true... not what looks to me like a backwards assignment of fault.  Should I blame the designers of a spoon if my 7 month old kid can't use it?  No, it's a great tool but my kid just isn't up to speed with it yet.[QUOTE=scaine]I sincerely hope this thread doesn't get stickied to be honest.  If I was complaining about something which I think ought to be better in Linux, and someone linked me to such an insulting response, I'd be outta here.  Maybe thats the point though.[/quote]The point is clearly outlined at the begining of this thread (or so I thought).  Then later I clarified that even more in another post.  I thought maybe "this is laughable" might be mistaken as one or just offend someone, but as you mentioned, I've removed that.  Any others?  Any worries of scaring people away or ticking people off who share certain opinions are IMHO legitimate.  You can't exactly tell someone not to be offended if they want to be stubborn about it.  And you can't tell them that their possible response of getting irate/upset isn't legitemate either.  Who's got the right to do that?[QUOTE=scaine]proprietary software is insanely counter intuitive / impossible to install on Linxu[/QUOTE]Buh?[QUOTE=scaine]And don't get me started on that "Linux is not Windows" thread a few people have linked.  The tone of the document alone grates just enough to get your teeth grinding, and then it lashes out with the examples do more harm than good.[/quote]Well, it's true.  Linux isn't Windows even if some distros do aim to "be more windows-like".  Just because they are both OS's doesn't mean they have to work the same.  To employ a commonly used analogy, apples don't look, feel, or taste like oranges even though they are both fruits.   I like apples and I like oranges and I don't like the idea of an apple being a variation of an orange.  I like apples the way they are.  Oh, and are you talking about [this]("http://linux.oneandoneis2.org/LNW.htm") or something else that I missed?[quote=Maupertus]Although I don't think the remarks about "people who want a windows clone" are appropiate in this thread (or indeed at all) ...[/quote]I don't think that it's innapropriate at all.  I think a lot of people want Linux to behave like windows because it's what they are comfortable with - they know how to use it.  I think that's where a lot of these complaints are coming from... uncomfortable and frustrated Windows users.  But making it the sole focus would be innapropriate.

---

### Post by J-B on 2006-01-11
Just out of curiousity, and slightly off-topic...Arktis, you seem to think (obviously correct me if I'm ASSuming the wrong thing) that Windows is easier to use.  I say this based off of your statements about it being written for the lowest common denominator.   However, I got two responses to my post saying that Linux is actually easier to use for the novice.  So what's the general consensus here?  

Frankly I don't see that either one, given adequate instruction in both (and having a good stable linux distro), is easier or more difficult to use.  I can see already that there are advantages and disadvantages to either.   

But there seems to be some differences of opinion,  i.e. the almost elitist phrase "most people aren't ready for linux", implying that most people aren't smart enough to use it, and then the other side, "People who don't know anything about computers are almost always better off with Linux (as opposed to Windows), but someone has to install and configure it for them (just as in Windows--usually "someone" like Dell or HP).", which to me seems to be the exact opposite, that people who aren't particularly educated or intelligent SHOULD use linux.  

I'm not trying to start anything or be a smart ass, really I'm not.  I just don't understand.  Is Linux too advanced for the average joe...or is Windows?

---

### Post by aysiu on 2006-01-11
[QUOTE=J-B]
But there seems to be some differences of opinion,  i.e. the almost elitist phrase "most people aren't ready for linux", implying that most people aren't smart enough to use it, and then the other side, "People who don't know anything about computers are almost always better off with Linux (as opposed to Windows), but someone has to install and configure it for them (just as in Windows--usually "someone" like Dell or HP).", which to me seems to be the exact opposite, that people who aren't particularly educated or intelligent SHOULD use linux.[/QUOTE] Right now Linux is rarely if ever preinstalled on a new computer. If you're using Linux as a desktop, most likely you or someone close to you installed and configured it. For most users, the user herself installs and configures Linux. The user *is* the installer, and thus must be advanced (anyone who installs and configures an operating system from scratch is more advanced than the average user).

If someone else installs and configures Linux for you, it's easier to *use*.

People often confuse *using* Linux with *installing and configuring* Linux, mainly because in order to use it, you or someone close to you has to install and configure it.

---

### Post by ade234uk on 2006-01-11
I get sick of hearing it as well. Remember when you have been using Microsoft for x amount of years it makes you stupid and lazy. 

You expect everything to just work out of the box. I have learnt more in 2 months using Ubuntu than I ever did with Windows. 

Linux is up for any task, just look at Doom 3 its runs better than on Windows. Also ever tried opening a 5mb .sql file in Windows lol, expect Notepad to freeze but stick this in Ubuntu and away you go.

---

### Post by prizrak on 2006-01-11
The saying that average (inexperienced) users are better off with Linux stems from more than one thing. 
I would say that both Windows and Linux are about the same in the newbie friendly territory. Both run a discovearable GUI that for the most part doesn't get in your way. Program installation is easier in Ubuntu than it is in Windows if you stick with the repos it's the opposite if you try to go for outside stuff (even though it's not hard to sudo alien -i *.rpm or dpkg -i *.deb it's not DISCOVERABLE w/o reading).
The "avg user is better off with Linux" attitude comes from the fact that administering a Linux box is about as complicated as not walking into walls in broad daylight while sober and paying attention. The things that make it easier for our non technical brothers/sisters are:
- Viruses are close to nonexistant
- Spyware plain doesn't exist (outside of cookies of course)
- Hard to screw anything up w/o having root permissions (there is an added bonus here that if you need to put in the password you probably shouldn't be doing it)
- Most things come out of the box
- The system itself is very resilient to attacks
Securing Windows requires certain amount of knowledge (although AOL is helping with that). Linux is alot more secure out of the box.

Installing and configuring an OS is a whole different story it actually takes me ALOT more time to get a Windows system up and running from an SP1 CD than it does Ubuntu.

---

### Post by micjustmic on 2006-01-28
My only gripe about Linux is the fact that I have to choose hardware for the OS, not (always) choose hardware that I prefer.

Because Windows is on the vast majority of desktop computers, bleeding edge hardware will more often then not come with Windows drivers, with Linux drivers either "planned" or simply never released by the manufacturer, putting driver production in the hands of "other" programmers, if/when they can get hold of what they need to even start writing the drivers.

This is, of course, not Linux fault, but it is annoying to have to take out my Sound Blaster X-Fi and put my Audigy 2 ZS back in to have sound in Linux.  

I wasn't a Linux user when I bought the X-Fi, but I've switched and would love to have my $130.00 sound card in the computer, not in a static bag on the shelf above it.  

So what's a penguin lover to do?

Wait, that's my option, or go back to Windows (bah!)

I'd like to reply to prizrak, while I agree with you about virus, malware and the inability to really "screw things up" since you don't run as root (or admin, in Windows lingo) I have to disagree about the installation.

I don't know why it takes you "ALOT more time" to install Windows, I have an SP2 CD I use to install Windows on boxes that I build/sell/repair (the customer buys a retail version and I use that CD key on their machine) and all I've really added to it is a provision to keep the sound and video drivers up to date on the CD itself, and it installs them at the S18 stage (install message "Registering components") and since the only two video card manufacturers that seem to count are ATi and nVidia, it's easy to simply download the new driver and re-burn the CDRW.  

Oh, and the critical updates are kept updated on the CD.  It takes all of 20 minutes from keying in the CD key to fully loaded desktop.

For those that are willing to pay for MS Office I have a DVD that does all of this, plus installs Office.  Pausing only for the Windows CD key and the Office CD key.

This takes all of 30 to 35 minutes, depending on the machine.

If you haven't made yourself a SP2 CD, I can understnd why it would be time consuming, upgrading an installed SP1 to SP2 using the update function is VERY time consuming.  

It's not hard to make an SP2 CD, but I digress . . .

This is a Linux forum after all . . . so I should stop talking about Windows.  :-)

Mic

---

### Post by aysiu on 2006-01-28
[QUOTE=micjustmic]My only gripe about Linux is the fact that I have to choose hardware for the OS, not (always) choose hardware that I prefer.[/QUOTE] I agree. My wife runs into the same thing with her Powerbook, except that she has one distinct advantage--software, hardware, whatever will often say it's Mac-compatible if it is. I almost never see a penguin on a piece of hardware or software, indicating it's Linux-friendly.

It really depends on what kind of "freedom" you're looking for. With Linux, I like the freedom to customize my desktop and to choose which distribution and packaging system to use and to be able to install it as many times on as many machines as I like (yeah, I know that doesn't work for Linspire, but that's the exception to the general trend).

Most Windows users like the freedom to not worry about compatibility. You walk into Office Depot, Best Buy, Circuit City, or whatever, and you just pick up a printer--it'll most likely be either auto-detected by Windows *or* come with a CD-ROM including the proper drivers and software. If you buy that same printer and plug it into a Linux distro, it will *probably* work right away, but if it doesn't... you're screwed. The software that comes with it will not really help you.

There's really no perfect OS out there--it all depends on what you prefer.

---

### Post by prizrak on 2006-01-28
micjustmic,
The lack of SP2 CD is really the issue, the one time I tried one it didn't install properly on my machine so I had to reinstall. So I use SP1 installer with all the updates that take forever of course. The biggest issue really is all the extra stuff I install that comes with Ubuntu for the most part (and the rest is quickly and easily available via Automatix). A sleepstreamed DVD would cut my install time considerably except that my laptop doesn't have either nVidia or ATI (but also works fine with stock Windows drivers). 
I will agree it's not the fairest of comparisons since for most people a Windows reinstall involves popping a restore CD in. Just sharing my experience really :)

---

### Post by micjustmic on 2006-01-29
prizrak,

Ugh!  Restore CDs are the WORST!

A friend had an old Compaq, his computer wouldn't start, so Compaq told him to simply put the restore CD in and restart the computer, do a restore and everything would be fine.

They didn't inform him the restore operation would FORMAT his hard drive.

Lucky for him he had a fairly recent backup of his data or he'd have been screwed.  This was a rare occasion that he'd actually backed up though.

Another thing that bothers me about them, in the price of the computer you've purchased is the cost of the licensing fee that goes to Microsoft, that's fine, but if you decide to scrap that computer (and I mean, rip the good parts out and use them in a home built computer) you can NOT use that CD to install the OS.  It simply won't work.  It's designed for that brand/model of computer and if you try to use it in another it spits it back out at you.  Now, you've paid the fee, you have the right to use the software on one machine at a time (read the ULA, that's what it says) so if you've removed it from the original machine you should be able to use it on another, but nope, not happening due to the way it's set up.  And these days, since they bundle quite a bit of software on these machines, the rescue CD usually doesn't even have the OS on it, a drive image (think Ghost) will be on a hidden partition on the hard drive and the rescue CD simply runs a small program to uncompress and install that image on the main partition.

Funny that a slipstreamed SP2 CD wouldn't work for you but the updates will, it's usually the other way around.  

I understand what you mean about having to add things to Windows that already come with Ubuntu (and most Linux distributions).  Ironically, people are always griping about Microsoft adding things TO Windows, "If they include (product) then (company) will go out of business, Microsoft shouldn't bundle that . . ." (IE, the suit over Internet Explorer) but come over to the Linux camp and having features/extra programs included on the OS install CD is a perk.  

Of course, all the software on a Linux CD is programmed by many, usually unconnected people, and the concern on the Windows side is that Microsoft would be the only choice if they started bundling everything with Windows and knocked everyone else off the map, but I doubt that would happen anyway.  Netscape is still around, Firefox is doing well . . . and there are many other examples . . . Office dominates, true, but Word Perfect is still being updated, so you do still have a choice.  You could use Open Office as well, and not spend hundreds of dollars, or ANY dollars (pounds, yen, whatever your currency), for that matter  :-)

Maybe we should move this to a new thread, I seem to keep going on about Windows.  :-# 

Mic

---

### Post by steve.horsley on 2006-01-29
One complaint that I see very frequently and that hasn't been mentioned here is the difficulty of setting up the X resolution if the installer doesn't get it right. It defaults back to 640*480 and that's it. I really thing that some of the other resolutions like 800*600 and 1024*768 should be possible in a default install. Hell, a lot of the setup utilities don't fit on the screen properly at 640*480, so you can't get the mouse to the option you know is there just about an inch below the bottom edge of the screen.

---

### Post by fakie_flip on 2007-04-19
Does Neverwinter Nights costs money?

---

### Post by Perfect Storm on 2007-04-19
Aye. But it's worth it. It's one of the game that still is on my computer.

---

### Post by fakie_flip on 2007-04-19
> **Arktis said:**
> 
[TC:E]("http://www.truecombat.com/intro.php") (True Combat: Elite) - To say that this is a Counterstrike clone wouldn't do it justice.  It's a mod for Wolfenstein Enemy Territory, so it's cross platform and **free** (thanks, id software!).  Sniping is much harder, aiming is done with the actual gun sights instead of HUD cross-hairs, you can lean to the left or right side to peek/shoot around obstacles and corners, and you can even stealthily crawl around on your belly.  Without a doubt, my favorite game for Linux.  Also has easy installation, but I recommend installing to a subdir in your home directory.  You won't need root privileges.


I am getting the error "file not found." Where can I download this ET Mod?

[http://liflg.org/?what=dl&catid=6&gameid=52&filename=true.combat.elite_0.49b-english-2.run](http://liflg.org/?what=dl&catid=6&gameid=52&filename=true.combat.elite_0.49b-english-2.run)

---

### Post by vf514 on 2007-04-19
> **Complaint #4:** [COLOR="DarkRed"]Linux is not ready for the desktop![/COLOR]
**Reply:** [COLOR="Blue"]Sorry, but it is and it has been for a while now.  A great deal of people, myself included, have been using Linux for their primary desktop OS for a long time now.  We get by just fine.  The reality is that **you** and 75% or more of your fellow computer users (guesstimation) simply aren't ready for Linux. The nix flavors represent ways of interacting with your computer and a philosophies that **are just different enough to disorient, confuse, and frustrate you** - especially if you're a long time Windows user.  If you're simply not familiar enough with the kind of thinking involved, "tools of the trade" or you simply just don't like to think too much, you're likely going to claim that it's Linux's fault when you run into initial problems.  The fact that Linux is also under a continual development cycle also tends to give the impression that it's just never quite "there" yet.  See [this]("http://ubuntuforums.org/showpost.php?p=644529&postcount=51") post as well.  I go into more detail there in response to some more LINRFTD posts.[/COLOR] 

Sorry, but your argument defeats itself. Try again.

---

### Post by karellen on 2007-04-19
good work, clear and straight to the point :). the thread deserves to be sticky

---

