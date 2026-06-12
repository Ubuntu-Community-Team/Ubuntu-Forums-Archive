---
title: "Solution to the gaming problem in Ubuntu?"
date: 2007-03-12
forum: The Cafe
---

### Post by Mazza558 on 2007-03-12
Perhaps Ubuntu users and devs could design a unified dev kit so that games developers could port their games into OpenGL? If we could make it easy for devs to port games over, they would see it as an oppurtunity to get another 300k sales, and would be encouraged to do so, providing the tools are there and don't cut back on development time.

What do you think? Is this under way, or would it be too difficult to do?

---

### Post by IYY on 2007-03-12
Porting games that use OpenGL is already very easy, especially if cross-platform compability is something they consider throughout the development process. If a developer *wants* to make a game cross platform, he can do so at an almost negligable effort. 

Game developers just aren't interested, that's all.

---

### Post by Mazza558 on 2007-03-12
> **IYY said:**
> Porting games that use OpenGL is already very easy, especially if cross-platform compability is something they consider throughout the development process. If a developer *wants* to make a game cross platform, he can do so at an almost negligable effort. 

Game developers just aren't interested, that's all.

It's interesting that if a big-name game was ported over, I think it'd get a lot of sales, as there is little competition in the field. Perhaps as linux develops as a whole, this might become more common.

---

### Post by Polygon on 2007-03-12
well that depends iiy... if games are designed only for direct x then i would imagine it would be pretty hard to rewrite most of the engine to use open gl

but engines like unreal and the doom3 engine were made with opengl and directx in mind so its incredibly easy to port games.

linux and mac in general just need a larger userbase. games arnt made for other os's right now because there isnt enough gamers that would buy the games to make a profit off of it...

---

### Post by Redlance on 2007-03-13
most people overlook the obvious when it comes to commercial games on linux.

1) different builds of linux to account for.
2) technical knowledge needed by end user to install.
3) and a SERIOUS showstopper. Copy protection. as it is no SANE game company will want to release a NEW release to linux.There is no safe DRM. There is no standard for cd copy protection. (yes doom and unreal and X2 and X3) but for the rest of the companies how do they protect thier investments? force linux to go along with the windows Bandwagon and restrict certain parts of the OS from Users? (Cold day in hell in my book)

---

### Post by cowlip on 2007-03-13
For 3, that's a pro for Linux in my book.  I'd personally rather have no games on my computer than have to download a crack that may or may not be safe for the game to function normally.  Copy protection is such a hassle for legit customers and I'd love to see if these copy protection companies could show me that new games that aren't already up on a torrent site somehwere, to justify these onerous schemes (such an appropriate word)

As an alternative to OpenGL+OpenAL, there's the SDL (Simple DirectMedia Layer) DirectX-Linux equivalent which I think the now-defunct LokiGames made to make porting Windows games easier.  But as we know, DirectX is only an artifical barrier since games are ported to OpenGL if they run on any consoles other than the (Direct)Xbox.

[http://en.wikipedia.org/wiki/Simple_DirectMedia_Layer](http://en.wikipedia.org/wiki/Simple_DirectMedia_Layer)

---

### Post by Redlance on 2007-03-13
cowlip posted:

For 3, that's a pro for Linux in my book. I'd personally rather have no games on my computer than have to download a crack that may or may not be safe for the game to function normally. Copy protection is such a hassle for legit customers and I'd love to see if these copy protection companies could show me that new games that aren't already up on a torrent site somehwere, to justify these onerous schemes (such an appropriate word)

As an alternative to OpenGL+OpenAL, there's the SDL (Simple DirectMedia Layer) DirectX-Linux equivalent which I think the now-defunct LokiGames made to make porting Windows games easier. But as we know, DirectX is only an artifical barrier since games are ported to OpenGL if they run on any consoles other than the (Direct)Xbox.
________________________________________________________________________


I agree with ya on that. It would be nice to see SDL get some reviving. This will come in time. as since the market for Linux use is growing very well and steadily in 5 years who knows.. :) i expect it to achieve critical mass in the gaming section by then to be a viable platform. Just the waiting annoys me :D

---

### Post by beefcurry on 2007-03-13
D3D code can already be easily ported to OpenGL, theres no problem with that. Linux Distro's have no unified API, sound system bla bla bla bla. Too many things to think about, just not woth the investment and time (normally)

---

### Post by prizrak on 2007-03-13
> **Redlance said:**
> most people overlook the obvious when it comes to commercial games on linux.

1) different builds of linux to account for.
2) technical knowledge needed by end user to install.
3) and a SERIOUS showstopper. Copy protection. as it is no SANE game company will want to release a NEW release to linux.There is no safe DRM. There is no standard for cd copy protection. (yes doom and unreal and X2 and X3) but for the rest of the companies how do they protect thier investments? force linux to go along with the windows Bandwagon and restrict certain parts of the OS from Users? (Cold day in hell in my book)

1) LSB
2) BS - CnR is being ported to Ubuntu it can be ported to others. Just about every distro has a double click install of packages. It's easy enough to do STEAM approach and just have a client that you double click on to start no install required (ties in with above)
3) I see no issue with implementing DRM on Linux or any other OS. It would be just as (in)effective on Linux as it is on Windows.

---

### Post by celsofaf on 2007-03-13
> **prizrak said:**
> 1) LSB.

What does this stand for...?

---

### Post by prizrak on 2007-03-13
> **celsofaf said:**
> What does this stand for...?

Linux standard base - an initiative to create a standard base for all Linux distributions making it easier to develop distro independent [closed]software.  Ubuntu is LSB certified so is SuSE and RedHat AFAIK. It also proposes a unified package manager based on RPM but that doesn't seem to be going anywhere.

---

### Post by hanzomon4 on 2007-03-13
LSB = [Linux standard base]("http://www.linux-foundation.org/en/LSB")

---

### Post by GeneralZod on 2007-03-13
> **celsofaf said:**
> What does this stand for...?

[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)



I still have an install of Ut04 from when I used Mandrake 10.  So far, I've gone through Mandrake 10 -> Mandrake 10.1 -> Gentoo -> Kubuntu 5.04 -> Kubuntu 5.10 -> Kubuntu 6.06 and it has "Just Worked" every single time, as soon as the 3D drivers were installed.

---

### Post by Tomosaur on 2007-03-13
Graphics wise, it's not a big problem to port to Linux. Things like file handling etc can be a bit more difficult, but they're more or less non-issues. A clean room design approach can ensure platform independence, you just have to be careful about things. Porting **existing** games is more tricky, but it CAN be done. The problem is marketability more than anything. Developers just do not see big sales on Linux. Given Linux' growing popularity, this may change. They'll always spout the same excuses about development difficulty, but this is much less of a problem than they make out. CNR will hopefully persuade some serious developers to start letting Linux users play their games too - many are catching on to distribution methods such as Valve's Steam.

---

### Post by igknighted on 2007-03-13
The solution to linux gaming: Every linux user who wants to game, instead of buying a top end PC since lord knows you don't need that with linux, spends the extra money on a PS3 or Wii or *gasp* and Xbox and games on that.  They have more games anyway these days, and its a trend I don't see changing anytime soon.

---

### Post by prizrak on 2007-03-13
What I wanna know is who decided that it's a problem? If you are a gamer you will likely not be able to run Linux anyway on the latest and greatest hardware that has some crazy proprietary interfaces. Last I hear the PhysX cards didn't work under Linux and I hear that it's something very useful for PC games. So you couldn't be a serious gamer under Linux anyway and a casual one can easily live with dual booting or switching over to consoles.

---

