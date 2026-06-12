---
title: "A musing about Linux future."
date: 2006-04-17
forum: The Cafe
---

### Post by prizrak on 2006-04-17
Alot of people have been real happy about Vista delay and saying that GNU/Linux in general and Ubuntu in particular will be able to gain some ground. I think there are some issues they might be overlooking. The main issue of the day IMO is 64 bit. AMD doesn't even produce 32bit CPU's AFAIK.
The issue at hand here is that, the hardware support for desktops (yes Linux runs on more hardware than Windows but we talking strictly x86/x86-64 here) is not all that great as it is. Right now we are catching up, but what is going to happen when Vista 64 is here and everyone starts creating 64 bit drivers/apps? This could be a pretty big issue, even though I'm sure the 32 bit version of Dapper will be better than Vista 64 but I doubt that Dapper 64 will be as good simply because of the 3rd party support. This quite possibly may put Linux in trouble and back into "enthusiast OS" state that it is FINALLY crawling out of. I beileve it could also be a possible reason for MS not worrying about delaying Vista despite the fact that Linux been getting better and better. 
That's my thoughts on it in any case, you may disagree and I will welcome any good counter arguments as I don't want this future to be :0

---

### Post by helpme on 2006-04-17
[QUOTE=prizrak] This quite possibly may put Linux in trouble and back into "enthusiast OS" state that it is FINALLY crawling out of. [/QUOTE]
How many billions in revenue does an OS have to generate per year before you consider it to be out of the "enthusiast OS" state?

---

### Post by GeneralZod on 2006-04-17
I don't see this as a huge problem, to be honest - open source drivers will almost always be ported to new architectures (I'm sure that most, if not all, of the drivers in the kernel are 64-bit clean already), so we've lost nothing there, and third-party drivers are largely relegated to 3d cards, and I think even ATI offer 64-bit Linux drivers.  I don't really see how this situation is any worse than our current one - perhaps you could expand on why you feel this is the case?

Edit:

I'm not sure if this "AMD doesn't produce 32-bit CPU's" thing is true - I thought they all had legacy support for 32-bit meaning you can still run 32-bit Linux and Windows (which includes the old drivers, of course) on them, if you choose.  Can someone who follows hardware clarify this?

---

### Post by BoyOfDestiny on 2006-04-17
[QUOTE=prizrak]Alot of people have been real happy about Vista delay and saying that GNU/Linux in general and Ubuntu in particular will be able to gain some ground. I think there are some issues they might be overlooking. The main issue of the day IMO is 64 bit. AMD doesn't even produce 32bit CPU's AFAIK.
The issue at hand here is that, the hardware support for desktops (yes Linux runs on more hardware than Windows but we talking strictly x86/x86-64 here) is not all that great as it is. Right now we are catching up, but what is going to happen when Vista 64 is here and everyone starts creating 64 bit drivers/apps? This could be a pretty big issue, even though I'm sure the 32 bit version of Dapper will be better than Vista 64 but I doubt that Dapper 64 will be as good simply because of the 3rd party support. This quite possibly may put Linux in trouble and back into "enthusiast OS" state that it is FINALLY crawling out of. I beileve it could also be a possible reason for MS not worrying about delaying Vista despite the fact that Linux been getting better and better. 
That's my thoughts on it in any case, you may disagree and I will welcome any good counter arguments as I don't want this future to be :0[/QUOTE]

Ok a lot of if's, discussing it further will lead to circular reasoning (i.e. if that then it implies this, and if that is the case then this must be true... if... etc etc.) With "if" I can put Paris in a bottle. Basically, take what I say here with a grain of salt.

Dapper 64 currently rocks. For 2 apps that need 32-bit I have a chroot, and yes I've made it a script to make it trivial to install chroot. Hopefully the ia32libs will continue to improve, so people can use more 32-bit apps without chrooting (i.e. as it is with openoffice.)

2nd if windows goes 64-bit, it will need to maintain 32-bit compatibility, literally tens of thousands of 3rd party apps will have to be rewritten/ported to 64 otherwise, and this doesnt' count apps which may no longer be supported.

Also, considering how widespread x86 is, some companies may not be releasing 32-bit and 64-bit drivers all at once. Imagine all the strange doodads people have, companies that have gone under, or no longer provide support for the hardware/software.

Basically what I'm saying is not everyone is going to start creating 64-bit only. Too many people and companies still have x86. Not to mention the 64-bit amd and intel chips are backward compatible with x86 (now this would be interesting if they eventually cut that...) In this way Linux and open source is way way ahead. I have around 18,000 packages in synaptic to choose from that are all 64-bit native. List all the windows apps that have 64-bit versions...

Anyway, as all this goes on, WINE continues to improve as well, so if what's tying people to Windows is merely software applications, this fades as well.

---

### Post by NeghVar on 2006-04-17
I agree that Vistas delay will not mean huge gains for Linux, Sorry but I just don't see it happening. Not because of 64 vs 32 and such, but rather because people hate change like that. Your average user is not going to go out and download Linux just because MS is late, no, they will wait a few months then spend an obscene amount of money just to buy a new comp[uter and OS.

Also major companies, the only thing I could see them moving on based on this is that they are growing concerned with the stability of MS and its release/development cycle/system. But MS s never been great at releases this is just par for the course.

So basically I just don't see what all these reporters touting the Vista delay as being great for Linux, it helps yes but I honestly doubt many people will switch. We may see a few, but those will be more of a shockwave effect that we won't see for about a year or two when MS is screwing over its XP owners and they don't want to pay for all of the upgrade costs.

Just my humble opinion.

---

### Post by SSTwinrova on 2006-04-17
[QUOTE=BoyOfDestiny]if windows goes 64-bit, it will need to maintain 32-bit compatibility[/QUOTE]
At least on XP x64, it does, and I'd be amazed if Vista didn't.

WP Entry: [http://en.wikipedia.org/wiki/WOW64](http://en.wikipedia.org/wiki/WOW64)

---

### Post by Compucore on 2006-04-17
The one thing that Ubuntu should also take a look at as well. Is to take a look into other machines like Sun Microsystem, SGI, Nexstep machines as well. For those who are using machines that are still in working order. Reason that I am saying this is that there are people like myself who use some of these older machines. And osome more powerful machines like the SGI O2 that are true RISC/Sparc base processors. I had at one point two Sun Microsystems sparcstation 1+ machines at my place. And OS like ubuntu availale. Yes Intel are AMD are geting into the 64 bit cpu's here. But there are a lot of other machines that are already 64 bit RISC/Sparc based machines out there that you can still get wokring with. I may be the one of the rare people who know about this where there are the general public do not know about the other computers that are out there. But still should be considered looking into something like this. 

COmpucore

---

### Post by prizrak on 2006-04-17
[QUOTE=helpme]How many billions in revenue does an OS have to generate per year before you consider it to be out of the "enthusiast OS" state?[/QUOTE]
You take one thing I said out of the entire article. There was a reason it was in quotes, and it has nothing to do with revenue, it's all about market share. As it stands right now Linux is a minority on private desktops (and business ones as well) which puts it into "entusiast OS" range.
When I was talkign about 64bit I didn't mean that it's impossible to run Ubuntu 32 on x86-64 but rather that you need Ubuntu 64 to get the full power of the system. The fact that all the repo software can be compiled as native 64 puts me at ease though, I didn't realize that :)

---

### Post by helpme on 2006-04-18
[QUOTE=prizrak]You take one thing I said out of the entire article. There was a reason it was in quotes, and it has nothing to do with revenue, it's all about market share. 
[/QUOTE]
If a system that can be used for free, or if one takes the commercial distros, is cheaper than the competition, generates billions in revenue, what does that say about market share?
I'm sorry, reading my post again it probably came of as pretty unfriendly, though it certainly wasn't intended this way. I just get tired of the many people misrepresenting Linux as only an enthusiast OS. This is simply not the case. 

[QUOTE=prizrak]
As it stands right now Linux is a minority on private desktops (and business ones as well) which puts it into "entusiast OS" range.
[/QUOTE]
Not really. While what you say is probably true for the private desktop, Linux is used extensively on the server, so it's not an enthusiast OS.

[QUOTE=prizrak]
When I was talkign about 64bit I didn't mean that it's impossible to run Ubuntu 32 on x86-64 but rather that you need Ubuntu 64 to get the full power of the system. The fact that all the repo software can be compiled as native 64 puts me at ease though, I didn't realize that :)[/QUOTE]
Let's put it this way. Right now, out of Windows and Linux only Linux is really an option if you want to run a 64bit OS, so I don't see how Windows maybe catching up with Vista should lead to the problems you fear.

---

### Post by SeanTater on 2006-04-18
In the computer market, I doubt much of anything will happen fast. The whole computer world are ["sheeple"](http://en.wikipedia.org/wiki/Sheeple), who think that windows is the only OS in existance, and that the only way to escape the viruses is to upgrade immediately, then apply SP #1,2,3,4,5, etc..
I think that Firefox is a sword piercing the stomach of Microsoft.. If only it could radiate Open Source into the world.

The most "different" think about GNU / Linux, etc is that in this case, Free does not mean filled with viruses, Free does not mean "Trial Version". Free does not mean "I did not want to shell out $15 for the "pro" version. For once, Free does not mean going to an old run-down site, looking for that one piece of software. Free does not mean "Sign up for our free e-newsletter to get: etc." Free is no longer the "old" version that's been stripped of all it's features. Free is now cutting edge. Free is now the full featured version. Free competes with "expensive". Free was limiting. Free is now freedom. That is the difference..

---

### Post by 3rdalbum on 2006-04-18
64-bit? The man on the street doesn't give two winks about 64-bit. 32-bit systems can still access 4 gigs of RAM... the only people who use more than that are scientists, and they use supercomputers which run Linux anyway.

---

### Post by prizrak on 2006-04-18
> Not really. While what you say is probably true for the private desktop, Linux is used extensively on the server, so it's not an enthusiast OS.
I know that it's server share is huge and it is hardly enthusiast there, but private desktop is. In reality private desktops don't matter, what matters is organizational desktops and that's what we gotta aim for. That is also why I'm worried about the 64 bit issue, Joe Sixpack has no understanding of CPU architecture and register addressing to care what 64bit is, organizations however do and might look away from an OS that can't fully support 64 bit (backwards compatibility notwithstanding). 
Well as many people pointed out 64bit is not issue for Linux, the software can be recompiled as needed and so can the drivers. I guess the only "threat" would be proprietary stuff like nVidia drivers and Flash (this one is getting cloned by GNU anyways). So there is not much reason to worry :)

---

### Post by awakatanka on 2006-04-18
I think it only can get more desktop users on 2 ways. Target the company's and show them its better and cheaper and more secure. That is what is happening now.

But also target the future , that are the youngsters. They like the bling and the and the games. XGL is pushing the bling for linux , Gaming is a difficult point atm.

People that are used to work with linux at the company will faster switch to it at home to.

The youngsters we need to keep with all the cool stuff we got and attract more game company's, that way they getting familiar with this OS and will install it at mom's and dad's pc

.

---

### Post by prizrak on 2006-04-18
[QUOTE=awakatanka]I think it only can get more desktop users on 2 ways. Target the company's and show them its better and cheaper and more secure. That is what is happening now.

But also target the future , that are the youngsters. They like the bling and the and the games. XGL is pushing the bling for linux , Gaming is a difficult point atm.

People that are used to work with linux at the company will faster switch to it at home to.

The youngsters we need to keep with all the cool stuff we got and attract more game company's, that way they getting familiar with this OS and will install it at mom's and dad's pc

.[/QUOTE]
I very much believe that organizational desktop adoption is what's going to drive everything. Youngsters won't care all that much but when you are using Linux at work and you need to take work home (which most people do) you will be interested in having a home Linux machine. In turn the OEM's will start offering Linux as an option (w/o having to dig through the site), which in turn will drive 3rd parties to develop Linux applications/drivers.

---

### Post by aysiu on 2006-04-18
[QUOTE=prizrak]I very much believe that organizational desktop adoption is what's going to drive everything. Youngsters won't care all that much but when you are using Linux at work and you need to take work home (which most people do) you will be interested in having a home Linux machine.[/QUOTE] I'm not sure I agree with this 100%.

First of all, the youngsters of today are the workers (including managers who make computer purchasing decisions) of tomorrow. If they all used Linux in school, they're less likely to believe all the Microsoft FUD out there.

Secondly, many jobs do not require you to take work home with you. My job, for example, does not require me to take work home. I have worked from home on occasion, by choice, but even then I just use Ubuntu to VPN to my workplace and VNC my work computer.

My old job *did* require me to take work home, but it also gave me a laptop to do that work on, so even then I could have had a separate Ubuntu home computer.

---

### Post by mips on 2006-04-18
[QUOTE=Compucore]The one thing that Ubuntu should also take a look at as well. Is to take a look into other machines like Sun Microsystem, SGI, Nexstep machines as well. For those who are using machines that are still in working order. Reason that I am saying this is that there are people like myself who use some of these older machines. And osome more powerful machines like the SGI O2 that are true RISC/Sparc base processors. I had at one point two Sun Microsystems sparcstation 1+ machines at my place. And OS like ubuntu availale. Yes Intel are AMD are geting into the 64 bit cpu's here. But there are a lot of other machines that are already 64 bit RISC/Sparc based machines out there that you can still get wokring with. I may be the one of the rare people who know about this where there are the general public do not know about the other computers that are out there. But still should be considered looking into something like this. 

COmpucore[/QUOTE]


You have a valid point, Debian caters for a lot of architectures out there, [www.debian.org/ports/index](www.debian.org/ports/index)

As far a I know Ubuntu currently runs on i386, AMD64, PPC,  Sparc, IA64, HPPA. How well they run is a different story as some are probably in dev stages. But I have heard of someone here running on sparc.

[http://www.ubuntuforums.org/archive/index.php/t-75117.html](http://www.ubuntuforums.org/archive/index.php/t-75117.html)

Have a look here:
[http://cdimage.ubuntu.com/ports/releases/dapper/flight-6/](http://cdimage.ubuntu.com/ports/releases/dapper/flight-6/)

Maybe download a cd and try it out. Breezy versions are also available but for sparc there is no breezy cd.

I think the sgi/mips processors will take some time though. Probaly have a big&little endian version.

Unfortunately you don't see much about the above ports anywhere. They need a place on this forum as well.

---

