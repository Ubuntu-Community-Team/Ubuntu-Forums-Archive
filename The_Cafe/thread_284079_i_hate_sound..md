---
title: "i hate sound."
date: 2006-10-25
forum: The Cafe
---

### Post by dmizer on 2006-10-25
i want to rant.  those who wish to disagree, fine.  those who wish to agree, fine.  i'm just so completely frustrated that i need to say something before i can move on.

i hate sound.

actually, i love sound. i played string bass all through high school and college, and i still plink now and again.  but this is all in fun, and as far as i view the world ... it's extra-curricular.  especially when it comes to digital sound.  mp3's?  please, i cringe when i hear that slop.

so actually, to be more precise ... i hate digital sound.

but sound is so essential to the computer world.  announcements, alerts, and general day to day activities all require sound to work.  also, today's internet is a media based experience.  video and sound are everywhere.

but getting sound to work in ubuntu (and linux in general) has been the single most frustratingly impossible thing i've ever attempted to undertake.

the [comprehensive sound solutions guide](http://ubuntuforums.org/showthread.php?t=205449) has never ceased to be extremely helpful on each new install i do.  but this is pages of cli editing, and still only works if you cross your fingers juuuuust right.

so let me tell you what i love about configuring linux:

i love configuring X.

why?

it's cake!  just 'sudo dpkg-reconfigure xserver-xorg' and click through the options.  select your monitor and shezam, you have a working desktop.  if you want more than the basics (3d, compiz etc), of course you should expect to have to do more configuration, but to get working video is nothing.  one command and answer questions.

i know many people will disagree with me on this, but that's not my point here.  my point is that this kind of simplicity is what i want with my sound.

i want to 'sudo dpkg-reconfigure alsa-server' answer questions and have two sound devices work in harmony, my skype (now with alsa support by default) to work, keep gaim sounds from crashing the system, while still being able to hear my mail notification.

but alsa isn't even installed by default ... it's oss.  which in my experience so far ... has been buggy and unreliable at the best of times, and system haltingly bad at others.  i have to spend weeks configuring everything, and still i have issues.

i hate sound, and it has recently been making me consider giving flying lessons to several of my machines.

to end on an upbeat (but completely unrelated) note:
after a year of beating my brain into bloody bits, with the help of [this genius](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/canon-pixus25.html) i finally successfully printed my first test page directly from ubuntu.

---

### Post by woedend on 2006-10-25
well...on the bright side, sound cards are dirt cheap...you could always just buy one that does work well.  my audigy works perfectly here with every distro out of the box.

---

### Post by Bloch on 2006-10-25
Things used to be worse: remember when you had the choice of oss, alsa, esd and a couple of others? And if you asked anyone they answered "linux is all about choice"

Dapper hid away that (hurray). I get the impresion it's mainly laptops and extra soundcards that have problems.

---

### Post by dmizer on 2006-10-25
my sound cards work fine.  the problem is with making everything work in ... er ... harmony.  sound mixing.

i've always been successful in producing sound from all the systems i've installed to.  my problem comes in with the fact that so many different applications want to control the card through different sound servers, and they can't work together.  furthermore, not only is it not easy to convert everything to use one sound server, in some cases, it's impossible.

unlike with video ... everything that makes use of the video runs through x ... i don't have to configure the system to use coolvid(tm) for web browsing, and xorgpart32768 for open office etc.

note: i'm basing the above example on how mac makes use of xorg to operate open office.

---

### Post by .t. on 2006-10-25
I have a laptop with a CardBus Audigy 2 and it's wonderful. Make sure your drivers are open source!

---

### Post by 3rdalbum on 2006-10-25
When I'm typing up a post for my blog and the cartoon banner advertisement on Friendster yells "Oh my god! No way!", I really REALLY hate sound.

---

### Post by DoctorMO on 2006-10-25
3rdalbum with the open source flash player that fell through a wormwhole from the future, it supported flash 12 and had a right click menu to *enable* sound as it was disabled by default. websites of the future were far better as a result.

---

### Post by dmizer on 2006-10-25
> **.t. said:**
> I have a laptop with a CardBus Audigy 2 and it's wonderful. Make sure your drivers are open source!

no ... really ... this is not about drivers for the hardware.  all my hardware works.

this is about how linux handles sound in general.

it's far from "the nail in the coffin" so to speak.  i'm not about to wine about going back to windows because of it, but it is a huge annoyance trying to hunt all the little obscure settings for all the programs to try to make them cooperate.

---

### Post by dmizer on 2006-10-25
> **3rdalbum said:**
> When I'm typing up a post for my blog and the cartoon banner advertisement on Friendster yells "Oh my god! No way!", I really REALLY hate sound.

and THAT is why i love the adblock extension in firefox!  lol

---

