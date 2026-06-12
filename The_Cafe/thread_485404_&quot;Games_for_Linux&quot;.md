---
title: "&quot;Games for Linux&quot; ?"
date: 2007-06-26
forum: The Cafe
---

### Post by Extreme Coder on 2007-06-26
I just read this : [http://en.wikipedia.org/wiki/Games_For_Windows](http://en.wikipedia.org/wiki/Games_For_Windows)
 Wouldn't something similar but for Linux benefit and make it easier to make games for Linux? For example, a certain API/Program would be included in distros, and the games would have to follow certain specifications. They'd install to the same place, same install procedure,etc... You could also have an onlline service or something.

For example, a few features which interested me were:
> An "Easy Install" option that installs the title on your PC in the fewest possible steps and mouse clicks
Installs and runs properly on x64 versions of Windows Vista and is compatible with 64-bit processors (though the game itself can be 32-bit)

Your opinion?

---

### Post by Zzl1xndd on 2007-06-26
There is an Open Source game list 

[http://en.wikipedia.org/wiki/List_of_open_source_games](http://en.wikipedia.org/wiki/List_of_open_source_games)

---

### Post by CarpKing on 2007-06-26
Such a standard could be helpful.  We have OpenGL for graphics, but beyond that there are plenty of things Windows has standards for (sound, for example) that in Linux are covered by a convoluted mix of systems that each have strengths and weaknesses.  Methods of distribution and installation vary widely between games.

---

### Post by tcpip4lyfe on 2007-06-26
All I know is that call of duty 2 runs awesome in wine. pewpewpewpew

---

### Post by KIAaze on 2007-06-26
A standard for game installation would certainly be good and also help game developers make games that install  easily on all distros (altough I think that is already the case).

There is already a "/usr/games/" directory...

standards on GNU/Linux:
[http://www.linux-foundation.org/en/LSB]("http://www.linux-foundation.org/en/LSB")
[http://en.wikipedia.org/wiki/Linux_Standard_Base]("http://en.wikipedia.org/wiki/Linux_Standard_Base")
[http://www.freedesktop.org/wiki/]("http://www.freedesktop.org/wiki/")

But personnally, I still don't understand the difference between /usr/bin and /usr/local/bin...:confused:

/usr/bin/	Non-essential command binaries (not needed in single user mode); for all users.
/usr/local/	Tertiary hierarchy for local data, specific to this host. Typically has further subfolders, eg. bin/, lib/, share/
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")

edit:
nvm, this clears it up...
> Historically and strictly according to the standard, /usr/local/ is for data that must be stored on the local host (as opposed to /usr/, which may be mounted across a network. In real world use however, /usr/ is rarely remotely mounted, and /usr/local/ is more often used for installing software/data that is not part of the standard operating system distribution (in such case, /usr/ would only contain software/data that is part of the standard operating system distribution). It is possible that the FHS standard may in the future be changed to reflect this de-facto convention.

But for "games fo GNU/Linux", the /usr/games directory seems more consistent, since some games come with the distro and others don't...

---

### Post by Extreme Coder on 2007-06-26
> A standard for game installation would certainly be good and also help game developers make games that install easily on all distros (altough I think that is already the case).
 
 There is already a "/usr/games/" directory...
 
 standards on GNU/Linux:
 [http://www.linux-foundation.org/en/LSB](http://www.linux-foundation.org/en/LSB)
 [http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)
 [http://www.freedesktop.org/wiki/](http://www.freedesktop.org/wiki/)

AFAIK, the LSB has no effects _I_ can see.

>  
Such a standard could be helpful. We have OpenGL for graphics, but beyond that there are plenty of things Windows has standards for (sound, for example) that in Linux are covered by a convoluted mix of systems that each have strengths and weaknesses. Methods of distribution and installation vary widely between games.
Definitely.It could be also implemented in some way similar to CNR, with screenshots and reviews and a way to buy games.

---

### Post by KIAaze on 2007-06-26
The thing I liked about the "Games for Windows" thing is the integration with parental controls.
I can understand that some might specifically dislike it because of that, but I think it's a pretty good idea (even though I'm still far from having children ^^).

The categorization of programs is something I really like in Ubuntu and should make a similar apps control possible there too I think. At least when you open the apps menu, things are not all in one place by default like on Windows (in XP and older at least, don't know about Vista).

I wonder if those app categories are standardized for all distros.
I know it's about the same in Debian, but I haven't really tried out other distros yet.

---

### Post by Baelfael on 2007-06-26
What the hell is the point of having "Games for Windows" now on games? It's not like 99.9% of games are already for Windows or anything. I swear, it's so pointless. Any god damned game you buy in a store is obviously going to be for Windows, it's not like there isn't a game in the store that ISN'T.

---

### Post by DoctorMO on 2007-06-26
> Linux are covered by a convoluted mix of systems that each have strengths and weaknesses. Methods of distribution and installation vary widely between games.

Nah we have SDL + openGL which kicks donkeys over DirectX (for a start it's open source so works on all platforms) we also have a whole host of SDKs and various game related libs. have you never tryed to develop a game? tis easy once you have the media (models, textures, graphics, gui etc)

---

### Post by KIAaze on 2007-06-26
> **Baelfael said:**
> What the hell is the point of having "Games for Windows" now on games? It's not like 99.9% of games are already for Windows or anything. I swear, it's so pointless. Any god damned game you buy in a store is obviously going to be for Windows, it's not like there isn't a game in the store that ISN'T.
Marketing?
I guess Microsoft saw that the only reason to "need Windows" now is games.
And games are also about the only thing that simple home users pay for since they can get gratis equivalents of all "useful software" and who wants to pay extra for software used to work except companies (they also don't want too, but have less choice)?
For games and other artistic contents, which are unique, paying is easier to accept.
Windows sells games, Apple sells music. Maybe GNU/Linux should do movies? ^^

Well, that's my personal view anyway.

---

### Post by Extreme Coder on 2007-06-26
>  
What the hell is the point of having "Games for Windows" now on games? It's not like 99.9% of games are already for Windows or anything. I swear, it's so pointless. Any god damned game you buy in a store is obviously going to be for Windows, it's not like there isn't a game in the store that ISN'T.

But that's not the case for Linux, so that's why it would be useful for us.

---

