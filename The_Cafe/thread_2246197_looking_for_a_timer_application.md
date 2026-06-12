---
title: "looking for a timer application"
date: 2014-09-29
forum: The Cafe
---

### Post by kurja on 2014-09-29
I'm looking for a configurable interval timer program that could be used to display the time and preferably also round numbers (rounds, as in, rounds of a boxing match) and graphically free of other clutter. Searching the web I'm seeing lots of apps for phones but not for desktop... Idea would be to put up a second display so spectators could see the time. Any ideas? I have a pretty good idea for what would be ideal but I can't learn enough programming to make it work in one week, it's showtime next saturday ;)

Not sure if this is an appropriate forum for this?

---

### Post by tgalati4 on 2014-09-29
Not any open source projects that I could find.  Here is a web-based timer:  [http://www.speedbagforum.com/timer.html](http://www.speedbagforum.com/timer.html)

---

### Post by Habitual on 2014-09-29
Stopwatch is a stopwatch and timer program that uses the Tk toolkit. It has millisecond accuracy.
in a repo near you?

---

### Post by kurja on 2014-09-29
Thanks guys. Stopwatch app in the repos doesn't seem to have any interval timer functions, and the web based one doesn't run properly on my machine / browser for some reason :/

---

### Post by georgelappies on 2014-09-30
Draw me a rough mock-up of what you want and possibly I could create a Qt app for you.

---

### Post by kurja on 2014-09-30
> **georgelappies said:**
> Draw me a rough mock-up of what you want and possibly I could create a Qt app for you.

That would be incredibly awesome! I'll make a sketch right away.

---

### Post by kurja on 2014-09-30
Okay! I actually [found a timer]("http://www.bridgehands.com/R/Round_Timer_Clock.htm") that is almost what I need, but not quite (it's a timer for bridge games with insufficient controls and it won't go full screen). Attached a screenshot of that, and a simple illustration of what I'd actually want.

These are the absolute requirements:  

[LIST]
[*]time and round number displayed in _large_ numbers, filling the screen. Time should run towards zero
[*]gui controls with which to configure number of rounds (up to at least 5), duration of rounds (up to at least 5 min), and the pause duration in between (up to at least, say, 5 min) running of which should also be displayed
[*]ability to quickly and easily pause and resume the time
[*]ability to run on windows machines (I might not be able to get my linux box to the event)
[/LIST]

With all that in there, I could already use it. What I would also like:
[LIST]
[*]ability to add or remove time in one second increments (while time is paused, this is for cases of human error in pausing/starting the clock. So this would be very very useful ;) )
[*]sound at the end of each round (another sound at end of pause between rounds would be nice too, plus a sound ten seconds before end of round, aka the "ten seconds!" clapper)
[/LIST]

In a perfect world, the controls would exist in a second window displayed on the official's screen and the clock would be shown on a second screen but I think that to ensure compatibility it would be best to have controls displayed 'in a discreet fashion', ie. not in bright colors or the like, at the bottom below the clock itself. They'll be visible to the crowd but it's no big deal.

Color / font / such things aren't critical one way or the other, as long as the numbers are easy to see, as people will look at it over a distance.

For what I need it atm, I would need the program by friday evening at the latest (central europe). If that's too tight a deadline, I would still appreciate it very very much if you could do this at a later time, there will be other occasions where this would be useful. In that case I could help you to help make it as usable as possible to as many people as possible, across as many combat sports as possible.

Thank you!!!

my quick and not at all dirty sketch:
[ATTACH=CONFIG]256832[/ATTACH]

that bridge clock
[ATTACH=CONFIG]256833[/ATTACH]

---

### Post by tgalati4 on 2014-09-30
Open source Bum Fights will never be the same.  Linux development would happen faster if differences of opinion were handled this way.  Takes "agile" management to a new level.

---

### Post by kurja on 2014-09-30
A triple witticism - five points!

---

### Post by tgalati4 on 2014-09-30
A Haiku:

GNU versus Linux . . .
Let's spar over it.  But wait . . .
We have no timer.

---

### Post by georgelappies on 2014-10-01
Ok, thanks for info. Let me see what I can come up with. May not have the full feature list ready for you by Friday (will definitely need some iterative testing from your side as there is bound to be a difference in interpretation between what you require and how I will implement it :) ), but lets see what we can do.

---

### Post by pqwoerituytrueiwoq on 2014-10-01
if you need one that can display the same time on multiple devices i have made one, given they have the date set accurately
it does not have a pause feature, maybe someone can mod it
it is web based, just run it on a server with php installed
*click clock to set time
*you can also put a ?set=true in the url to make it show the setting panel on load
*default password is password (stored as a md5 sum in apply.php)
*i did not make the icon image (found it online)
*i copied 1 or 2 js functions i found on stackoverflow IIRC, i am sure i modified them a little

---

### Post by georgelappies on 2014-10-01
> **pqwoerituytrueiwoq said:**
> if you need one that can display the same time on multiple devices i have made one, given they have the date set accurately
it does not have a pause feature, maybe someone can mod it
it is web based, just run it on a server with php installed
*click clock to set time
*you can also put a ?set=true in the url to make it show the setting panel on load
*default password is password (stored as a md5 sum in apply.php)
*i did not make the icon image (found it online)
*i copied 1 or 2 js functions i found on stackoverflow IIRC, i am sure i modified them a little

Excellent, and it works on any device with a browser :)

---

### Post by kurja on 2014-10-01
Thank you pqwoerituytrueiwoq. Ability to run on any device is nice indeed, though it lacks the must have features to be usable in itself in my case.

---

### Post by CantankRus on 2014-10-01
There is a downloadable java timer in the link below. See vid attachment to see in action.
You need java. You can install the open-source implementation of the Java via terminal with...
```
sudo apt-get install openjdk-7-jre
```

It's possible to replace the image on the left in the application.
[**_[COLOR="#B22222"]Tabata Clock[/COLOR]_**]("http://tabata.sperker.de/index.php?nav=download&d_sub=dld_wl")

---

### Post by kurja on 2014-10-02
CantankRus, that's actually quite close to what I need but not quite - there is no pause button. Vomiting clown is hilarious though =D

Trying this out I realized I didn't specify a couple details, in case someone decides to create a new clock program:
[LIST]
[*]almost all workout interval timers have a start delay; for match use this is no good, clock needs to be started when the ref calls it
[*]it would be mighty convenient to have the clock auto-pause at end of rest time - again, match clock is started when the ref calls it
[/LIST]

---

