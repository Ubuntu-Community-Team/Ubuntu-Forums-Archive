---
title: "Sim City 4 Graphics Problem"
date: 2011-06-01
forum: Wine
---

### Post by peterson2k4 on 2011-06-01
The Attached screenshots will show what I a dealing with. When it loads up I hear "EA Games...Challenge Everything" but I don't see the ea logo.  I do see the Maxis logo afterwards though.  Then I get the clouds above oblivion and the empty menus.

Any help is greatly appreciated and will be rewarded with that good feeling you get when you help someone.

---

### Post by bobwyajnr on 2011-06-03
Hi **peterson2k4**

Does that Atom box have an Ion graphics card? If not you might need to get subscribed to one of those 'fix Intel Mesa graphics driver' threads :popcorn:

Wine version? Console output?

Do native OpenGL games run OK your box e.g. Nexuiz? (Since I gather SimCity 4 needs DirectX 7.0 support...)

Bob

---

### Post by peterson2k4 on 2011-06-04
my graphics card is an Intel GMS 950.  I am running Wine 1.3 but, 1.2 does the same thing.  I searched "fix Intel Mesa graphics driver" and I couldn't find anything useful.  was there a particular thread you saw?  Also, I downloaded Neverput and it played great.  Not a very advanced game but it seemed to be on par with Sim City 4

---

### Post by cwwilson721 on 2011-06-04
Try reading [what the Wine HQ has on Sim City 4.]("http://www.tomshardware.com/reviews/best-graphics-card-game-performance-radeon-hd-6670,2935-7.html")

Might steer you into the correct direction...

---

### Post by peterson2k4 on 2011-06-04
I found out that [COLOR="DarkRed"]WINEDEBUG=-all wine C:\\Program\ Files\\Maxis\\SimCity\ 4\ Deluxe\\Apps\\SimCity\ 4.exe -d:software -intro:off[/COLOR] will make it work.  apparently it skips the intro and that seems to make all the problems go away.  don't know why but at least I am able to play it.  Thank you for your help Bob.  I would not have found the fix without your guidance.

---

### Post by bobwyajnr on 2011-06-05
> **cwwilson721 said:**
> Try reading [what the Wine HQ has on Sim City 4.]("http://www.tomshardware.com/reviews/best-graphics-card-game-performance-radeon-hd-6670,2935-7.html")

Might steer you into the correct direction...

lol... or the wrong direction ;)

---

### Post by cwwilson721 on 2011-06-05
Actually, IF YOU READ THE ARTICLE LINKED:

It says THE SAME THING.

Being unable to comprehend simple instructions must be a hard thing in life.

---

