---
title: "Average computer specs for developing nations?"
date: 2011-07-29
forum: The Cafe
---

### Post by Syndicalist on 2011-07-29
So, we are working on a distro and one of the questions that keeps coming up is whether we are discriminating against people who cant run heavier operating systems...

I want to base it on Debian Testing, but at least one person thinks thats too heavy and we should go with Puppy.....We are going to have Tor, P2P, I2P, IRC channels, podcast tools, tools for making flyers and propaganda, tools for streaming video and uploading it to the net.....user accounts built in.


Now realistically, is this even going to be possible on a computer that cant run debian with XFCE regardless of how heavy the DE is? Im thinking its a waste of time to attempt a media-activist distro that is geared for computers that are THAT old. Also, its going to be harder for new users as it would be less user friendly, imo.

Anyway, my understanding is that a lot of countries dont even have a lot of personal computers....what they have are internet cafes and computers at public libraries and schools....what kind of specs would you expect to find in a host of poorer countries, typically?

Egypt?
Sudan?
Greece? Admittedly not THAT poor, yet.
Ethiopia
Syria
Lebanon
Bali/Indonesia?
Philippines?



I doubt these people are running around with Macbooks, since only 1 in 130 people even HAVE personal computers in many of these countries, but Im guessing you are likely to encounter a lot of donated Windows computers of say.....5-10 years old? Pentium4s, Athlons and Core2 Duos? 256mb ram up to 2gb? Somewhere in that ballpark?

Are you going to encounter people walking around with pentium 2s and 64mb ram, commonly?

---

### Post by Bandit on 2011-07-29
Well my wife is Filipino and from what I can tell. City like Manilla is much like here in the US. Quad core CPUs and decent specs are normal. But in the other out lying islands. Your looking at higher end Single and Dual core systems with very few owning Quads or above. Most of those were prob systems sent home to PI by families in the US and other countries. Also most families don't actually own computers, some do but most go to internet cafes since they are a very chit-chatty culture..

---

### Post by Syndicalist on 2011-07-29
So, would you agree with my analysis then?

---

### Post by NightwishFan on 2011-07-29
> **Syndicalist said:**
> I want to base it on Debian Testing
If I would make a distro I would base it on Debian Stable instead. It really is not that old especially with some selective backports.

> but at least one person thinks thats too heavy
Debian 32-bit with Gnome uses around 100-150mb on boot. I got it down to 60mb removing some unneeded services. It boots and runs on 256mb of ram with a swap. With a lighter setup you could do with even less.

> Now realistically, is this even going to be possible on a computer that cant run debian with XFCE regardless of how heavy the DE is? Im thinking its a waste of time to attempt a media-activist distro that is geared for computers that are THAT old. Also, its going to be harder for new users as it would be less user friendly, imo.
I agree. I would support no less than 1ghz and 384mb ram.

> Anyway, my understanding is that a lot of countries dont even have a lot of personal computers....what they have are internet cafes and computers at public libraries and schools.
If you are intending this to be used as a "live cd" I would support no less than 512mb regardless. Or have instructions for users to create a temporary swap file and remove it when finished. You might look into packaging compcache.
[https://code.google.com/p/compcache/](https://code.google.com/p/compcache/)

> Are you going to encounter people walking around with pentium 2s and 64mb ram, commonly?
Such machines would be unsuitable for many modern linux systems (including puppy).

Here is a of a basic 32-bit Debian system with no GUI or services to show you what the base is like.

---

### Post by Syndicalist on 2011-07-29
Thank you for the input.

---

### Post by el_koraco on 2011-07-29
The bigger concern would be bandwidth. Being based on testing would necessitate constant updates, which is not the ideal when you're talking about developing countries. So I'd go with stable.

---

### Post by Syndicalist on 2011-07-29
Fair enough.

Personally I want to target our distro to media-activists in populations like Greece and Egypt and Lebanon, maybe inside the USA or UK. I want to use most of a DVD for the live session instead of a CD.....The other guy thinks the "heavy" version should be no more than 300mb and the lite version around 150.

I think we are just going to do two different projects. Most students should have access to at least 512 ram and 1ghrz cpu.

---

### Post by keithpeter on 2011-07-29
> **Syndicalist said:**
> Fair enough.

Personally I want to target our distro to media-activists in populations like Greece and Egypt and Lebanon, maybe inside the USA or UK. I want to use most of a DVD for the live session instead of a CD.....The other guy thinks the "heavy" version should be no more than 300mb and the lite version around 150.

I think we are just going to do two different projects. Most students should have access to at least 512 ram and 1ghrz cpu.

Greece? Have a look at AntiX Linux and ask on their forum. The maintainer is based in Greece and the distro is aimed at PCs with 256Mb or less. Based on Debian. Can be set to Squeeze repositories to avoid the update download as mentioned.

UK? Contact Blag Linux

[http://www.blagblagblag.org/](http://www.blagblagblag.org/)

Trade Union based linux for designers/activists.

---

### Post by NightwishFan on 2011-07-29
I also agree with the above. It is probably a better idea to merge or work along with an existing project than create your own.

---

### Post by BrokenKingpin on 2011-07-29
> **Syndicalist said:**
> 
I want to base it on Debian Testing, but at least one person thinks thats too heavy
You have to be joking... Debian Testing is light as they come. If you do the net-install and something like Openbox or LXDE that will be plenty light, even for ancient machines.

---

### Post by jfreak_ on 2011-07-29
More than computer hardware it is the poor spread of broadband in developing countries. It is rather common to have internet connections on landline ( 2-3kbps download) or  mobile 'broadband' ( 8-10kbps download). Many don't have access to internet (Another reason why Linux will never take off in developing countries, hardly anyone can download the 1 Gb distro, let alone the frequent updates and upgrades, restricted packages, etc) . So in a nutshell, you should develop a distro with a small size but including essential stuff like drivers and restricted drivers and which does NOT need to update itself frequently.
In terms of hardware, below 512mb RAM is rare and so is above 2Gb. Older computers usually have 512 mb RAM.

---

### Post by 3Miro on 2011-07-29
jfreak_ is right. You need to include everything on a single DVD/CD/USB so you will not have to download anything. Security concerns are small since you are hardly ever going to be connected to the Internet, a good firewall and stable browser should be enough.

Actually most people in the 3d world wouldn't have computers at all, from the ones that do, I suspect Pentium 4 and higher with 256MB of RAM would be the low end.

(Greece is in no way or whatsoever a 3d world country nor is it going to become one. Once you are a industrialized and developed nation, I don't think it is possible to become a 3d world country.)

---

### Post by keithpeter on 2011-07-29
> **jfreak_ said:**
> So in a nutshell, you should develop a distro with a small size but including essential stuff like drivers and restricted drivers and which does NOT need to update itself frequently.
In terms of hardware, below 512mb RAM is rare and so is above 2Gb. Older computers usually have 512 mb RAM.

Interesting, especially the lower limit on RAM, I guess a feature of when people started to get PCs.

[http://spi.dod.mil/lipose.htm](http://spi.dod.mil/lipose.htm)

might be of interest. 

Supplied by the US military for people specifically to use for email/web on local computers. No updates. No installing of anything, locked down, no access to local hard drive. 

The bat file they put on the live CD for making USB sticks managed to install the 'de luxe' version to an old 512Mb stick I have that nothing else works on.

---

### Post by ssam on 2011-07-29
would it be worth looking at using gentoo as a base? that would allow a very high level of customising. you would be able to remove lots of stuff that was not needed.

users would not need to do any compiling them selves if you provided a repo of precompiled stuff.

also you may find that system requirements depend more on what packages you include, than which distro you use as a base. no distro can make openoffice 'light', but abiword is pretty light on any distro.

you could also look at the OPLC project. the XO-1 was pretty low spec. or openembedded which can be used for building distros that run on things like PDAs.

---

### Post by snowpine on 2011-07-29
Debian is a great choice as it's super-stable (assuming you use Stable!) and very well documented and supported. 

Another worth taking a look at is SliTaz. It's very lightweight and has excellent remastering tools (tazlito and tazusb).

---

### Post by 3Miro on 2011-07-29
I am a Gentoo user, but I would also recommend Debian or Ubuntu LTS as a basis. Currently 10.04 would be a good basis as it is already very stable and it will not need many more updates. Gentoo would require more time to stabilize.

---

### Post by kaldor on 2011-07-29
Base your distro on a snapshot of Debian Sid/Testing or CentOS. Stable/mainstream base with everything they'd ever need preinstalled by default on a 1 GB DVD (since connection is poor). Use a stable + lightweight DE such as LXDE or XFCE and go light on the software. 

- Abiword and Gnumeric instead of LibreOffice
- Epiphany instead of Firefox
- Claws Mail instead of Evolution/Thunderbird

etc.

Make sure essential software is preinstalled. It's a big problem to need to download large packages in some areas. Email clients, office productivity, web browsing, editors, media players, codecs, all that.

---

### Post by BrokenKingpin on 2011-07-29
I really don't see the point of creating another light distro. Lubuntu or ChrunchBang already cover most of what you are talking about: light distro, light software selection, yet still easy to use. There are plenty of distros out there that can be used on old machines.

---

### Post by 3Miro on 2011-07-29
> **kaldor said:**
> 
- Abiword and Gnumeric instead of LibreOffice
- Epiphany instead of Firefox
- Claws Mail instead of Evolution/Thunderbird


I have had horrible experience with Abiword and non-English alphabet/languages. A stripped down version of LibreOffice would probably be better.

I think FF is a must (unless Chromium is smaller). There are plenty of web-pages that would complain about Epiphany. Also, Epiphany depends on the Gnome libraries, if you go for a light distro, XFCE would probably be better and then Epiphany would come with unnecessary bloat.

I use Claws Mail, not as many features as Thunderbird, but it is mighty awesome.

---

### Post by Syndicalist on 2011-07-29
Personally, I am not really interested in making a lite distro. I want a heavier distro that is equipped for media-activists, reporters, people to make flyers from a live disk at libraries, accounts to upload and stream footage, ad hoc networking for when the internet is down, Tor and I2p and p2p to hide your location and fool those who think they can track you....you cant. If somebody doesnt want to be seen at their location, they dont have to be.


While there are privacy distro, offensive security distros, and artist and multi media distros, I have NEVER seen one that combines those into the total package for the covert media activist. The focus would not be on anti-social hackers, but on hackers who are uploading videos and music, making documentaries, uploading live video feeds to a database or user accounts, streaming video, offering the webcam for a persecutive of events on the ground.

Bloggers in in the middle of a civil war or riot, or people trying to report via ad hoc networking in the midst of martial law, or maybe just some students who want to show up at a protest and print out protest flyers can do this from live DVD at a public library or college without leaving a trace. Maybe they want to mix some music for the march and insert clips of inspirational speakers to some electronic music or rock music.


To my knowledge such a project does not exist. The closest was probably Dynebolic, but its OLD and not updated. PureDyne is another, but both of them lack offensive security and privacy. Also, they are still a bit light on multi-media. We want to be able to do podcasts and video feeds, ect. Use your computer as a server.



This is a nitch that actually needs to be filled, not just another personal flavor.

---

