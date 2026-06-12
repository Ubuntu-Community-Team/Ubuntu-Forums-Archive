---
title: "Why Doesnt the Military Use *nix"
date: 2007-10-03
forum: The Cafe
---

### Post by GSF1200S on 2007-10-03
Good question, huh? In every workcenter of a typical shop in the Navy for instance, there is at least 4 computers. Each computer needs its own copy of Windows, which is 2000 by the way (!). Each computer needs its own copy of MS Office (maybe theres a server pack). The network needs its own antivirus utility, as well as specific control on each computer based by user as to what rights they have. Think about the fact that Windows has many more security holes.

Now, using a Linux distro such as CentOS or hell even Ubuntu.. look at what would be remedied: Antivirus would be unnecessary, but they could run ClamAV or AVG to be safe. Every computer in the military could have this distro installed without one cent of cost. Sure, Linux admins would need to be used instead of Windows ones, and the computer guys in the military would need training on Linux and such networks, but that would seem to pale in comparison to the overwhelming costs of all the MS software. 

I think the reason is central to the military always sticking to tried and true methods, and possibly the cost of redesigning specific military applications to run on a unix base.

Still, security would be far higher, and in the long run, its bound to save them money.

Now, forget political allegiance here.. Mankind is apparantly to crude to *not* have a bunch of militaries running around, so im just trying to gain a prospective here. Yeah yeah, im a guy from the US, but I dont want my governments choices to be confused with my own (another words, lets be civil :) ).

What about your countries military? Do they use *nix or Windows, and what do you think makes it this way?

---

### Post by aysiu on 2007-10-03
The NSA uses Linux:
[http://www.nsa.gov/selinux/](http://www.nsa.gov/selinux/)

---

### Post by GSF1200S on 2007-10-03
> **aysiu said:**
> The NSA uses Linux:
[http://www.nsa.gov/selinux/](http://www.nsa.gov/selinux/)

Interesting article. Im kinda surprised theyd release the source code, but its cool nonetheless. 

That clearly shows some security benefits for Linux. Though, even IF Linux and Windows were on the same page security wise, I would think a linux setup would cost the government less...

---

### Post by fdrake on 2007-10-03
it's interesting to see the strong relationship between huge private companies and the military programs. Companies like Microsoft and others have invested a huge amount of money in the war business and are making a lot out of it. 
Don't look just at the military but also at the hospitals and public schools. Don't u think medical and educational resources  whould be more affordable in this way?
In this case it's not a of problem of performance or cost of the technology it's mostly political(how much money can you make out of it, of the tax payers?).

---

### Post by raggari on 2007-10-03
SELinux has been part of Fedora since start of the project. This is actually one of the hottest topics right now on the Linux kernel list:
[http://www.vnunet.com/vnunet/news/2200143/linus-irate-linux-smacking]("http://www.vnunet.com/vnunet/news/2200143/linus-irate-linux-smacking")

---

### Post by FuturePilot on 2007-10-03
> Each computer needs its own copy of Windows, which is 2000 by the way (!)I feel safe now\\:D/

---

### Post by GSF1200S on 2007-10-03
> **FuturePilot said:**
> I feel safe now\\:D/

LOL! When you mention it that way.. lol. hahaahaha

---

### Post by kopinux on 2007-10-03
in the future...yes

[IMG]http://img413.imageshack.us/img413/9686/fcs11042105ih9.jpg[/IMG]

---

### Post by anaconda on 2007-10-03
Hih..
would be interesting to see what happens when they move to vista.

In the middle of war:
"vista genuine ADVANTAGE thinks that this version might not be genuine" Please contact M$ and until then vista will be running in reduced functioning mode.. Which means you wont be able to do anything..

---

### Post by GSF1200S on 2007-10-03
> **anaconda said:**
> Hih..
would be interesting to see what happens when they move to vista.

In the middle of war:
"vista genuine ADVANTAGE thinks that this version might not be genuine" Please contact M$ and until then vista will be running in reduced functioning mode.. Which means you wont be able to do anything..

hehe.. good thing I carry a Knoppix CD under the seat of my bike... im just a one man computer rambo- j/k :)

---

### Post by Armadillo Kilr on 2007-10-03
the military doesn't use linux/unix because they couldn't figure out how to partition their hard drives because i'm sure that stopped me for a bit:guitar:

---

### Post by eph1973 on 2007-10-03
I was in the Navy for 11 years, and they do use Unix.  You just don't see it.  They run Windows NT, but they also do interfaces to Unix servers that run certain databases (Like you OMMS is probably run off a Unix server).  If you have anything where you gotta run StartX to get to them, that's because it's interfacing with a Unix server.  If you were to go down to IT division on your ship or command, you will see most of the admins running Windows NT.  They run all the user accounts, and the e-mail from NT, because the Windows interface is more familiar to most people.  There's usually only a couple of people (depending on how big your command is, it may only be one person) who know how to deal with the Unix servers.  Most of the other IT's pretty much just know the Windows NT admin end of things.

By the way, pretty much all of their classified networks run Unix.

---

### Post by mips on 2007-10-03
The use of linux/unix is pretty widespread in the DoD.

[http://www.terrybollinger.com/index.html#dodfoss](http://www.terrybollinger.com/index.html#dodfoss)

---

### Post by GSF1200S on 2007-10-03
> **eph1973 said:**
> I was in the Navy for 11 years, and they do use Unix.  You just don't see it.  They run Windows NT, but they also do interfaces to Unix servers that run certain databases (Like you OMMS is probably run off a Unix server).  If you have anything where you gotta run StartX to get to them, that's because it's interfacing with a Unix server.  If you were to go down to IT division on your ship or command, you will see most of the admins running Windows NT.  They run all the user accounts, and the e-mail from NT, because the Windows interface is more familiar to most people.  There's usually only a couple of people (depending on how big your command is, it may only be one person) who know how to deal with the Unix servers.  Most of the other IT's pretty much just know the Windows NT admin end of things.

By the way, pretty much all of their classified networks run Unix.

I didnt realize the transparency involved. Although, I dont know if the way you think it works applies everywhere (maybe it does). I know at least at a shore based facility its all windows, even the main haunchos in ADP are using Windows. I havent *seen* any unix around. On the ship, once again windows was everywhere. Of course the ITs had Windows too.

This is what doesnt make sense. Anyone whos spent time in the military knows that NOTHING is done out of convienience. Its whatever way the military feels its best balancing cost vs. mission readiness. Thats why supply spends quite a bit- to augment a ready now status. So, with that said.. why wouldnt the military force its members to use *nix all the way? I dont know about ITs or other rates specifically as I fix aircraft electronics, but our rate needs only 1 specific program (NALCOMIS, I-level equivalent of OMMS), a web browser, and an email client. Seems pointless to spend millions implementing a windows interface for members when a FREE *nix environment could be used and 3 shortcuts placed on the desktop to cover what programs were needed...

---

### Post by GSF1200S on 2007-10-03
> **mips said:**
> The use of linux/unix is pretty widespread in the DoD.

 
[http://www.terrybollinger.com/dodfos...tml/index.html](http://www.terrybollinger.com/dodfos...tml/index.html)
 [http://www.terrybollinger.com/stenbi...memo_html.html](http://www.terrybollinger.com/stenbi...memo_html.html)
[http://www.terrybollinger.com/index.html#dodfoss](http://www.terrybollinger.com/index.html#dodfoss)

The first 2 links gave me a 404, but the last one was informative. I guess I should have looked more thoroughly for articles like this.. but dang- i guess i didnt expect the military to spend so much on familarality (sp?)...

---

### Post by mips on 2007-10-03
> **GSF1200S said:**
> The first 2 links gave me a 404,

Removed them, should be available via the main site.

---

### Post by bailout on 2007-10-03
The control system for Britain's nuclear missiles is based on windows 2000 :eek:

---

### Post by floke on 2007-10-03
...and you know this because?

---

### Post by Mr.Auer on 2007-10-03
The Finnish army decided to move all its core systems to Linux some year ago. I think theyre now making the transition. Reasons given were first of all security and availability of source code, and better reliability, price, and the ability to modify systems as needed.

I am, by the way, a militant anarchist and pacifist, and would very much like to see more of open source licenses prohibiting any military use of the software. Like Asimovs rules of robotics. This has sometimes been done already.

"GPU is a Gnutella client that creates ad-hoc supercomputers by allowing individual PCs on the network to share CPU resources with each other. That's intriguing enough, but the really interesting thing about GPU is the license its developers have given it. They call it a "no military use" modified version of the GNU General Public License (GPL)."

"Both developers do agree about one aspect of their license clause. It is based on the first of science fiction writer Isaac Asimov's Three Law of Robotics, which states, "A robot may not harm a human being, or, through inaction, allow a human being to come to harm." That, they say, is a good thing, "because the guy was right," Tegel says, "and he showed the paradox that almost any technological development has to solve, whether it is software or an atom bomb. We must discuss now what ethical problems we may raise in the future."
[http://www.linux.com/articles/56426](http://www.linux.com/articles/56426)

---

### Post by GSF1200S on 2007-10-03
> **bailout said:**
> The control system for Britain's nuclear missiles is based on windows 2000 :eek:

Thats good. Its too bad all nuclear frameworks arent on windows. If mankind was stupid/ignorant/selfish/unrefined enough to start WWIII, hopefully enough of the machines would bluescreen to save the human race.

I guess thats one instance where unix is a bad thing...

---

### Post by proalan on 2007-10-03
Do we really want linux to be associated with warfare?

---

### Post by GSF1200S on 2007-10-03
> **Mr.Auer said:**
> The Finnish army decided to move all its core systems to Linux some year ago. I think theyre now making the transition. Reasons given were first of all security and availability of source code, and better reliability, price, and the ability to modify systems as needed.

I am, by the way, a militant anarchist and pacifist, and would very much like to see more of open source licenses prohibiting any military use of the software. Like Asimovs rules of robotics. This has sometimes been done already.

"GPU is a Gnutella client that creates ad-hoc supercomputers by allowing individual PCs on the network to share CPU resources with each other. That's intriguing enough, but the really interesting thing about GPU is the license its developers have given it. They call it a "no military use" modified version of the GNU General Public License (GPL)."

"Both developers do agree about one aspect of their license clause. It is based on the first of science fiction writer Isaac Asimov's Three Law of Robotics, which states, "A robot may not harm a human being, or, through inaction, allow a human being to come to harm." That, they say, is a good thing, "because the guy was right," Tegel says, "and he showed the paradox that almost any technological development has to solve, whether it is software or an atom bomb. We must discuss now what ethical problems we may raise in the future."
[http://www.linux.com/articles/56426](http://www.linux.com/articles/56426)

I dont know, thats a toughie. Im a pacifist, and I would be an anarchist if I thought the human race could handle it. But prohibiting the use of OSS? I fail to see how it would make a difference in that arena.

Windows is just as capable of running launch codes as *nix is.. so prohibiting use is kind of a nil point. If we as HUMANS are that angered and unrespective of our own race to push the buttons, were all done for anyways.

What originally started as a question of curiosity has evolved into a discussion of nuclear war- I need a beer.

---

### Post by GSF1200S on 2007-10-03
> **proalan said:**
> Do we really want linux to be associated with warfare?

Do we want ANYTHING to be associated with warfare?

Hell no- war sucks. We should be able to have our war in conversation, not through neanderthal physical force.

---

### Post by Officer Dibble on 2007-10-03
> **proalan said:**
> Do we really want linux to be associated with warfare?

Good point.

Some few years ago there was a major (forgive teh pun) roll-out of [manufacturer will remain unnamed] Servers, [manufacturer will remain unnamed] desktops, and [manufacturer will remain unnamed] laptops to be used in the Army and Navy based on a Windows OS. The Army eventually put their own build on these systems but they were Windows of a particular flavour.

The desktops went into all sorts of places, even Tanks.

Government gets its own pricing level on Windows licenses, and they do have to take into account logisitics, ineroperabiltiy for both the software and the users... and a big one... backwards compatibility. So any changes if at all will be very gradual.

If they're gonna fight about things using computers I don't know why they don't just let the computers battle it out over a game of [Tic Tac Toe]("http://en.wikipedia.org/wiki/WarGames")... or just play a nice game of Chess... :)

---

### Post by jc87 on 2007-10-03
> **GSF1200S said:**
> Thats good. Its too bad all nuclear frameworks arent on windows. If mankind was stupid/ignorant/selfish/unrefined enough to start WWIII, hopefully enough of the machines would bluescreen to save the human race.

I guess thats one instance where unix is a bad thing...

WWhat if the happens fire BECAUSE a BSOD?

---

### Post by diskotek on 2007-10-03
ohh no, so they can buy much more bullets with that profit. they must be better with miscosoft.

---

### Post by happysmileman on 2007-10-03
> **diskotek said:**
> ohh no, so they can buy much more bullets with that profit. they must be better with miscosoft.

Well then let's hope they upgrade to Vista for all their PC's soon, that way they won't be able to afford nukes foir another 20-30 years

---

### Post by stalker145 on 2007-10-03
> **proalan said:**
> Do we really want linux to be associated with warfare?

You are absolutely correct. While we're at it, let's get rid of [GPS technology]("http://www.smh.com.au/news/technology/gps-technology-finds-many-civilian-uses/2005/08/18/1123958172153.html"), [medicinal advances]("http://www.usatoday.com/news/world/iraq/2006-03-26-war-clinics_x.htm"), [the internet]("http://www.isoc.org/internet/history/brief.shtml"), and [miscellaneous other advances]("http://www.blackwell-synergy.com/doi/abs/10.1111/j.1467-9310.1996.tb00928.x").

I wonder what other "warfare-related" items you would be willing to give up. No, I do not think that the military and warfare is the be all and end all of existence. I would rather we have neither, to be honest. No one here can refute the usefulness of war and the military when it comes to technological advances. 

If it meant no war, I think I'd be happy still using an abacus to do math and the Pony Express to communicate with family.

The fact is, if the military were to keep to the spirit of the GPL and allow the dispersion of the source code, imagine how far and how quickly Linux could advance.

---

### Post by Kevin on 2007-10-03
Their UAV's (Unmanned Aerial Vehicles) run on linux.  At least the ones I've worked with do.

---

### Post by hobieone on 2007-10-03
leave it to the navy to use windows for every thing.  besides like the uav. the targeting sytems in tanks ect i know are unix based or all thier own os programing and not based on a particular system  due to security concerns. at least with the a u.s. army at leat it was when i was in the army  in the 90's.

---

### Post by popch on 2007-10-03
The 'military' invented the internet, and Unix did TCP/IP before Windows did. So what OS were they using?

---

### Post by w7kmc on 2007-10-03
There are many government agencies that use linux.   

Linux and *nix is better suited for scientific apps and servers.  If you walk into most gov't offices you'll see XP on the desktops...because it is  suited for administrative tasks and office functions.  (Spreadsheetsand word processors...just like the mac ads huh?) 

*nix runs behind the scene s for many agencies...including the military.

---

### Post by bailout on 2007-10-03
> **floke said:**
> ...and you know this because?

It was reported a while ago following some of the engineers who wanted an oss solution speaking out. This is a link about ship software but IIRC it also affects new software bing developed for nuclear submarines but I can't find that storey so I may be wrong.

[http://www.theregister.co.uk/2004/09/06/ams_goes_windows_for_warships/](http://www.theregister.co.uk/2004/09/06/ams_goes_windows_for_warships/)

---

### Post by Hortinstein on 2007-10-03
I think the cost of people having to learn something new outweighs any potential benefit.  A better question would be why does microsoft still have software vulnerabilities when an OS that was collectively made for free AND open source remedied those along time ago with not even a fraction of Microsoft's assets.

---

