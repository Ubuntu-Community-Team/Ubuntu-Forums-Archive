---
title: "Does everything released on linux need to be GPL &amp; open source?"
date: 2007-08-18
forum: The Cafe
---

### Post by dgrafix on 2007-08-18
Basically, can people write commercial 'shareware' software for linux or not, as there seems to be some confusion with people i have spoken to.

By shareware i mean that it does stuff, but you can pay for it to do more stuff.

ie. extra levels for a game.

Also, can i use a normal EULA or do i need some special one.

---

### Post by euler_fan on 2007-08-18
In really short: Yes, but you can't include any GPL stuff with it. See their [FAQ]("http://www.gnu.org/licenses/gpl-faq.html").

---

### Post by tyfius on 2007-08-18
There are commercial applications on Linux. Take a look at Cedega, Komodo or SlickEdit.

The GPL (and some other license state) if you use this, then your application must be GPL to. Other license such as the BSD or LGPL allow you to use something and write commercial applications with it.

Personally, I don't really mind paying for software, if there is no equal free alternative. How high the price is you are willing to pay for something is up to you.

---

### Post by Bachstelze on 2007-08-18
> **euler_fan said:**
> In really short: Yes, but you can't include any GPL stuff with it.

Not exactly. If, say, the game engine uses GPL libraries, it must be released under the GPL. Hoever, if the "extra stuff" doesn't use GPL code, it can very well be released under another licence. So releasing a game as Free Software but releasing e.g. extra levels under a non-free license is perfectly possible.

---

### Post by ssam on 2007-08-18
lots of games have a different licence for the game data than the game engine.

so you could have GPL engine, but some pay for levels.

---

### Post by 23meg on 2007-08-18
Moved to Community Cafe, since the question doesn't pertain to Gutsy Gibbon development.

---

### Post by dgrafix on 2007-11-12
oops sorry, i thought it was general dev.

thanks everyone you have answered my question :)

---

### Post by DeadSuperHero on 2007-11-12
Wait, so that means that if you use an open source game engine to build a game, you HAVE to release all of the game's source code?
I'm all for contributing to the game engine, but releasing a commercial game with full source code kind of seems ridiculous.

---

### Post by toupeiro on 2007-11-12
False, False, False...  You do NOT have to make your code open source because it uses an open source platform.  Only the components you use to make your code work that are open source must be documented and remain open source.

---

### Post by DeadSuperHero on 2007-11-12
Oh..okay then.
*phew*

---

### Post by ZylGadis on 2007-11-12
> **Mr. Psychopath said:**
> Wait, so that means that if you use an open source game engine to build a game, you HAVE to release all of the game's source code?
I'm all for contributing to the game engine, but releasing a commercial game with full source code kind of seems ridiculous.

**Yes**, you have to, if the engine uses GPL. That is the entire purpose of the GPL. If the engine uses another Free license, say, LGPL or BSD/MIT, then you don't have to.

Why is it ridiculous to release the source code of a game? The game can only get better in this way.

---

### Post by DeadSuperHero on 2007-11-12
> **ZylGadis said:**
> **Yes**, you have to, if the engine uses GPL. That is the entire purpose of the GPL. If the engine uses another Free license, say, LGPL or BSD/MIT, then you don't have to.

Why is it ridiculous to release the source code of a game? The game can only get better in this way.

Well, I don't see the point in selling a game commercially if I have to release source code for each game. How am I supposed to make money from my hard work?
Like I said, I'm all for releasing any changes made to the engine, but I just don't see the point in releasing ALL of my source code so some nitwit can make a crappy or insulting version of MY game, or so that he can pass it off as his own.
As someone who hangs out in a game developer community alot, I can safely say that a lot of developers DON'T want to release their source codes. It's ridiculous.
How are we supposed to support Open Source? You're giving the end user an infinite amount of choices with it, but developers get no choice at all.

---

### Post by dgrafix on 2007-11-12
I reccomend engines like irrlicht and ogre, they are LGPL, You can keep stuff you make with it proprietry, as long as its only linking its lib and you are not distribing or selling any modified versions of the original engine without source (or so i believe from my readin),

---

