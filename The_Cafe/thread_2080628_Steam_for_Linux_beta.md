---
title: "Steam for Linux beta"
date: 2012-11-04
forum: The Cafe
---

### Post by Eggnog on 2012-11-04
I just signed up for it.  I want to give this thing a shot and do what I can to help it succeed.  There seems to be quite the community growing in their Linux discussion area these days, with people really excited about it.

In my view, the ability to mainstream game natively, and having access to a growing number of popular games ported to Linux, would be a huge step in getting Ubuntu/Linux on to more desktops and keeping it there.  Getting Steam and Valve involved is a good first step.

---

### Post by GrubThemeArtist on 2012-11-04
Too bad they're only allowing for 1000 participants. :(

---

### Post by sffvba[e0rt on 2012-11-04
> **GrubThemeArtist said:**
> Too bad they're only allowing for 1000 participants. :(

Nothing is set in stone... Let us see how this develops :) (let us stay positive, a 1000 ppl is nothing to test a piece of software, especially something like Left for Dead 2 and TF2 that are online shooters).


404

---

### Post by BrokenKingpin on 2012-11-07
I was hoping to be part of the first 1000, but was not selected. Hopefully they will open up to more and more people over the next month or so.

---

### Post by mips on 2012-11-08
[http://blog.manjaro.org/2012/11/08/steam-hit-our-testing-repositories/](http://blog.manjaro.org/2012/11/08/steam-hit-our-testing-repositories/)

> **[SIZE="3"]Steam hit our testing repositories[/SIZE]**

Valve has launched a limited access beta for its new Steam for Linux client. There was an encouraging excitement around Steam for Linux. Valve received over 60,000 responses to its request for participants in the Steam for Linux Beta within its first week. The company has selected the first round of beta participants from those early adopters.

The arrival of Steam for Linux owes a lot to Microsoft which has started to turn Windows from a platform for OEMs and developers into a Microsoft only product inspired by Apple’s walled garden.

“This is a huge milestone in the development of PC gaming,” according to Gabe Newell, Valve President and co-founder. “Steam users have been asking us to support gaming on Linux. We’re happy to bring rich forms of entertainment and our community of users to this open, customer-friendly platform.”

Fortunately, and unfortunately, Steam for Linux is currently available only for Ubuntu. With some tricks we made it also available for Manjaro.

The Steam for Linux Beta client will become available to a widening group of users over the course of the beta. Subsequent participants will be chosen among survey respondents, and once the team has seen a solid level of stability and performance across a variety of systems, the Steam for Linux client will become available to all users of Steam.

If you’re one of the lucky beta-testers you can install Steam for Linux from our Testing Repositories with:

```
sudo pacman -Syu steamclient
```

---

### Post by Artemis3 on 2012-11-10
You can run the steam client just fine, if you were not selected you can't try valve's own titles, but steam runs and you can still install and play a few other games, such as **World of Goo**.

Finding which games work is a hit & miss, some people are compiling lists already. The linux filter doesn't work, you have to list all games and try each.

I used gdebi to install, here is the .deb: [http://media.steampowered.com/client/installer/steam.deb](http://media.steampowered.com/client/installer/steam.deb)

Nvidia users should also install nvidia-experimental-310 otherwise the client will nag you about it. Check: [https://wiki.ubuntu.com/Valve](https://wiki.ubuntu.com/Valve)

To run the client, use: **steam steam://store** or else you will get a message and the client will close.

Ubuntu 12.04 (or later) and derivatives should have no problem using that .deb
Note that the first time you run steam, it will pull about 100MiB worth of data.

---

### Post by sffvba[e0rt on 2012-11-10
Purchased Trine2, installed and played it... worked like a charm :) (and I am not a beta invitee)


404

---

### Post by Jakin on 2012-11-10
Im amazed at how well the client works, its as if steam had been on linux all along. If a game works, then it works.

Purchased World of Goo full, smooth.

---

### Post by philinux on 2012-12-13
[http://www.omgubuntu.co.uk/2012/12/steam-linux-to-launch-open-beta-next-week?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2012/12/steam-linux-to-launch-open-beta-next-week?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

---

### Post by Jakin on 2012-12-13
In the "supported games" list, i see a few of the games that were in humble bundle, but there are plenty of other humble bundle games that we know are linux compatible, and steam has them- but not in this "supported games" list. Thats alittle saddening... it would make the list alot bigger.

---

### Post by forrestcupp on 2012-12-13
> **philinux said:**
> [http://www.omgubuntu.co.uk/2012/12/steam-linux-to-launch-open-beta-next-week?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2012/12/steam-linux-to-launch-open-beta-next-week?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

Awesome. That was much quicker than I expected.

---

### Post by Shibblet on 2012-12-13
> **not found said:**
> Nothing is set in stone... Let us see how this develops :) (let us stay positive, a 1000 ppl is nothing to test a piece of software, especially something like Left for Dead 2 and TF2 that are online shooters).


404

I'm wondering how many people know they need proprietary drivers for their Nvidia Cards, and not just Nouveau.

Same with ATI.

Off topic:  That's the best Avatar I have ever seen!

---

### Post by sffvba[e0rt on 2012-12-14
> **Jakin said:**
> In the "supported games" list, i see a few of the games that were in humble bundle, but there are plenty of other humble bundle games that we know are linux compatible, and steam has them- but not in this "supported games" list. Thats alittle saddening... it would make the list alot bigger.

I suspect it has all to do with the specific companies, they have to submit the games and files to Steam to make them available... I do believe they will appear in time.

> **Shibblet said:**
> I'm wondering how many people know they need proprietary drivers for their Nvidia Cards, and not just Nouveau.

Same with ATI.

Off topic:  That's the best Avatar I have ever seen!

:)

I know of some users that have gotten better results with the open drivers (especially on older hardware)... it will all depend on what games you are trying to play.


404

---

### Post by Jakin on 2012-12-14
> **not found said:**
> I suspect it has all to do with the specific companies, they have to submit the games and files to Steam to make them available... I do believe they will appear in time.


I do hope so, surely we all were'nt able to purchase all the humble bundles, and so missed out.

---

