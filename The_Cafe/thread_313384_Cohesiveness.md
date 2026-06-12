---
title: "Cohesiveness"
date: 2006-12-05
forum: The Cafe
---

### Post by mushroom on 2006-12-05
Ubuntu's made great strides towards improving the Linux user experience, but how can we take this further? At what point can Ubuntu be perceived as a complete operating system rather than just Linux with a GUI on top of it like most other distributions? They're making the right choice concerning hardware acceleration and composite by default, but I propose the following further improvements:

-Grub and the text "Starting up..." should not be visible unless, of course, you have more than one OS on your system. Even then, try to dress it up in a more Ubuntu-like theme.

-When the DE starts up, a splash screen shouldn't appear, as one already appeared as the system started. It gives the perception that the OS boots really slowly and makes it seem like there are just too many things loaded for it to be stable, like the entire thing could crash at any second. At least, to the non-computer literate, which is a large target for Ubuntu.

-Try not to include too many references to the DE running, as it creates the perception explained above. The OS should be referred to as one unified thing. This isn't to say that credit shouldn't be given to those that essentially built what Ubuntu is, but it should only be mentioned where those who want that information would look for it, such as a topic in Help.

-The first boot page elaborates on the purpose of Ubuntu and things that a new user wouldn't care about a bit too much rather than giving the user a "start". A single-page introduction should appear on first boot that specifies the most basic functions and includes buttons linking to the web browser, music player, photo editor, etc., with a list of more in-depth options and then a link to a page "For more experienced users..." I believe the first mission of Ubuntu should be helping users to get things done with their OS, where promoting FOSS should be secondary (but not far behind).

-The user should be easily able to change all of the internal-hiding aspects back to their more verbose modes.

-Kubuntu should have a much smaller panel by default. This doesn't have anything to do with cohesiveness, but I might as well mention it.

The fourth proposed change may seem a bit extreme, but a new user coming from another OS should be made to feel comfortable. Having the first thing on screen when the OS boots be a long page describing all the wonderful freedom (I say that without a hint of sarcasm) that comes from using Ubuntu isn't exactly user-friendly. "Just Works" is a term I've come to dislike, but in this context, that's exactly what the user wants. He/she would want to know how to get started as quickly as possible without an ideology shoved in his/her face. Things like that should be included as a topic in Help, on the web page and on the packaging, but not as the first thing a user sees when booting.

Proposing this to the devs would probably be a better way to go about this, but I just wanted to see what you thought about it.

---

### Post by aysiu on 2006-12-05
In regards to your fourth proposed change, I don't think this is the way to go for Ubuntu, to be honest. Ubuntu is in an interesting position in that it appeals to both new users and veteran users. Very few distros are like that.

PCLinuxOS, Mepis, Xandros, Linspire, SuSE, Mandriva, etc. have the kind of integration and cohesiveness you're talking about. Linspire even has the first-boot tutorial that gets you started if you have no idea what you're doing.

On the other end, you have the notoriously user-unfriendly distros like Slackware, Gentoo, LFS, and Debian (though Debian is probably the friendliest of the aforementioned).

And in the middle... Ubuntu--touted as a new user distro but without all the bells and whistles that scare aware the veterans. I think this is largely why Ubuntu has become successful. Unlike Linspire, Ubuntu does not try to be Windows, treat users like idiots with an overdose of wizards and pop-up balloons, and cater to the lowest common denominator. But unlike Gentoo, Ubuntu does try to be simple and not confusing.

As for everything else... I'm in total agreement. The graphics part of Ubuntu has always been a little rough around the edges, especially when distros like Fedora, Mandriva, and SuSE have had that kind of polish for years. The good news is that with every successive release, Ubuntu becomes more and more polished. Hoary, no boot splash; Breezy, ugly boot splash; Dapper, better-looking boot splash; Edgy... well, it's debatable whether the boot splash got better for Edgy. But the rest of the artwork has improved immensely, particularly the icons and default Human theme.

---

### Post by mushroom on 2006-12-06
I'm certainly not saying it should be Windowsified, no wizards and pop-up balloons and such, but I'd like Ubuntu to achieve that OS X-like "zen", where it's not very complex, but it's not bombarding you with things that try to make the OS easy but instead make it annoying and restrictive. The DE's have the raw material required to acheive this, but it should appear in a certain way by default. Maybe there shouldn't be a start page. Maybe on first boot it should appear as "here's the applications that you most likely would want to use, but hey, feel free to change me to conform to your needs," like how OS X appears and there's the iLife apps right there on the dock, but everything there is completely and easily mutable. Right now all Ubuntu gives you is two toolbars (which is completely illogical to me, but that's just me) with a few buttons. The trash and logout buttons probably should not be there, as trash most logically would be on the desktop and the logout button is already in the menu. Firefox and Evolution buttons on the toolbar are good, but why not The Gimp and OO.o Word, etc.? Without the "full suite", it just makes it look like clutter for the sake of clutter. Help also seems out of place, for the fact that it's not really seen as an application.

Knowing that I'm using FOSS definitely makes me feel good, but it's prominently displayed on the packaging and the website, so why should it remind you after you install it? If there is a start page, shouldn't it be a bit more helpful?

I love the Edgy splash, it's sleek. Hiding the output was definitely a good choice as well.

---

### Post by jpkotta on 2006-12-06
Ubuntu, and Linux distros in general, should be about giving you a free operating system that works, not one that works and happens to be free.  Right now, Linux is something people seek out.  It is not plopped into their lap.  Maybe in the future it will become more relevant to get the user up and running, but not yet.

Also, I consider separation of DE from OS a feature, not a bug, but I'm also not Joe User.

---

### Post by jpkotta on 2006-12-06
> **mushroom said:**
> I'm certainly not saying it should be Windowsified, no wizards and pop-up balloons and such, but I'd like Ubuntu to achieve that OS X-like "zen", where it's not very complex, but it's not bombarding you with things that try to make the OS easy but instead make it annoying and restrictive. The DE's have the raw material required to acheive this, but it should appear in a certain way by default. Maybe there shouldn't be a start page. Maybe on first boot it should appear as "here's the applications that you most likely would want to use, but hey, feel free to change me to conform to your needs," like how OS X appears and there's the iLife apps right there on the dock, but everything there is completely and easily mutable. Right now all Ubuntu gives you is two toolbars (which is completely illogical to me, but that's just me) with a few buttons. The trash and logout buttons probably should not be there, as trash most logically would be on the desktop and the logout button is already in the menu. Firefox and Evolution buttons on the toolbar are good, but why not The Gimp and OO.o Word, etc.? Without the "full suite", it just makes it look like clutter for the sake of clutter. Help also seems out of place, for the fact that it's not really seen as an application.

Knowing that I'm using FOSS definitely makes me feel good, but it's prominently displayed on the packaging and the website, so why should it remind you after you install it? If there is a start page, shouldn't it be a bit more helpful?

I love the Edgy splash, it's sleek. Hiding the output was definitely a good choice as well.

Trash is exactly where it should be.  It is always available, you do not have to minimize windows to access it.

---

### Post by mushroom on 2006-12-06
> Ubuntu, and Linux distros in general, should be about giving you a free operating system that works, not one that works and happens to be free. Right now, Linux is something people seek out. It is not plopped into their lap. Maybe in the future it will become more relevant to get the user up and running, but not yet.

But if you seek it out, you should already know that it's free. Again, why remind the user when you can help him/her?

---

### Post by jpkotta on 2006-12-06
> **mushroom said:**
> But if you seek it out, you should already know that it's free. Again, why remind the user when you can help him/her?

Touche.  And if the user has a Linux enthusiast friend that gives them an Ubuntu CD, then they're probably more concerned about figuring it out, like you said, and not learning about freedom right away.  You've convinced me.  Still, there should *always* be something about the Ubuntu philosophy and Free Software on the welcome screen, but maybe you should have to scroll past all the "this is how to get things done" stuff.

---

### Post by aysiu on 2006-12-06
Anyone who just hands someone a Ubuntu CD is doing that person a disservice.

If I had a friend who was interested in Ubuntu, I would either install and configure it for her, or (if she were a bit more tech-savvy) at least point her to some good resources. I wouldn't just be like, "Hey. Here's a CD. Good luck."

---

### Post by mushroom on 2006-12-06
My friend's done that a couple of times to people at school. He wants mass-migration just by handing people CDs, but I keep telling him that most people don't even know what Windows or an operating system is. It's the computer, to them. That's why Ubuntu or any other Linux distro hasn't witnessed any significant usage, because of hardly any preinstallation and such. Apple has it easy when it comes to marketing, because all they have to say is "tired of your PC woes? Get a Mac." It has that artificial separation. I know that a Mac is basically just a PC with a different OS, but to Joe User, it's a completely different type of computer. It may not be the best approach to marketing, but it's certainly the simplest. Ubuntu essentially has to explain that a PC runs something called an operating system and Windows is the operating system running on most PCs, etc. It's difficult enough communicating the idea of a new, better operating system to a normal user, but to convince one to actually stop using what came with his/her computer and switch is just plain hard. Apple doesn't have that problem because the user's old computer with Windows is still around. Ubuntu offers that, but there comes another abstract idea to explain: partitions. I think the difficulty with Linux doesn't lie within Linux itself, but with getting people to try something different. Then there's the whole paradox that OEMs won't preinstall Linux until there are a significant amount of companies developing software for it, but companies won't develop software for it until OEMs start preinstalling Linux. A bit frustrating.

That aside, your general-purpose use of feminine pronouns intrigues me. Please do explain.

> Still, there should always be something about the Ubuntu philosophy and Free Software on the welcome screen, but maybe you should have to scroll past all the "this is how to get things done" stuff.

Oh yeah, definitely. I certainly think that FOSS advocation should remain a part of Ubuntu, but it should get users on their way to work first. That's what I like about Ubuntu: it maintains a professional product while still keeping a very community-oriented atmosphere. It gets some flak for straying from Free principles for the sake of practicality every once in a while (proprietary drivers mainly), but overall it doesn't feel too much like something made by a faceless corporation (Xandros, Linspire), yet it doesn't feel too radical (BLAG). It's a nice balance.

---

### Post by aysiu on 2006-12-06
I'm in full agreement about the Mac/Linux dichotomy in terms of migration.

I wrote a full treatment on Linux migration challenges here:
[http://www.psychocats.net/essays/linuxdesktopmyth](http://www.psychocats.net/essays/linuxdesktopmyth)

I've moved discussion about the feminine pronoun to [its own thread](http://ubuntuforums.org/showthread.php?t=313881).

---

