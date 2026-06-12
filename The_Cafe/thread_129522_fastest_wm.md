---
title: "fastest wm?"
date: 2006-02-13
forum: The Cafe
---

### Post by fuscia on 2006-02-13
so far, for me, flwm was just a little bit faster than openbox, but it had some irritating limitations, as did 9wm. i'm just starting to mess with icewm (crux looks great on it, otherwise, it would be 'outta here!'). sorry, no poll. (polls suck.)

---

### Post by Bandit on 2006-02-13
WindowMaker!! It Rules!!

---

### Post by JimmyJazz on 2006-02-13
fvwm is really quick most the time.

---

### Post by Iandefor on 2006-02-13
From running it on legacy hardware, I can say, definitively, that Enlightenment DR16 is pretty damn fast (But I don't know how fast it is compared to wm's like ratpoison). The latest fluxbox is disturbingly fast (starts up in less than a second on my system).

---

### Post by mstlyevil on 2006-02-14
All these acronyms! I'm so confused! :confused:

---

### Post by fuscia on 2006-02-14
i just tried the most recent flubox and while it only loads in a few seconds (as opposed to the 30+seconds of the older version), it doesn't strike me as being as zippy as openbox. ratpoison is pretty fast too, but once the novely wears off, it's kind of a pain in the 'series of asterisks'.

---

### Post by bored2k on 2006-02-14
I wouldn't go as far as to say it's the fastest, but [this build]("http://www.archlinux.org/packages.php?id=900") of fluxbox is pretty fast. Now, if fluxbox had openbox's intuitive alt+tab, it would be complete greatness.

---

### Post by fuscia on 2006-02-14
any of you try pywm yet?

---

### Post by poofyhairguy on 2006-02-14
e16

---

### Post by mcduck on 2006-02-14
ION sure is fast, if you consider that as a WM ;)

---

### Post by benplaut on 2006-02-14
yeah, ion is really, really fast (and good for productivity, once you learn it well)

try Openbox... it's incredible.

right now i use e17... it's very fast, but not giving up eye-candy ;)

---

### Post by Lovechild on 2006-02-14
Opinion are useless, to determine this we need:

a) Establish what is required for the definition "fast"

I would suggest: Throughtput and latency as the two baring metrics, we also need CPU usage, RAM usage and supporting library ressource cost.

b) How do we meassure

Obviously we meassure each WM in it's natural environment (metacity in GNOME, KWIN in KDE) and obviously we meassure on the same machine and configuration. We should also do pure runs for WMs like metacity that can run solo without it's supporting DE.

c) How do we weight the results

I would opt for a 2:1 ratio in favor of latency as snappiness is most likely to be the "feel" of speed. If we have so poor throughtput that it cannot keep up with the refresh rate it's a horrible WM regardless though.

d) How do we consider subjective experience that contradict the evidence (namely looking for what causes visual displeasure but is not WM related as the meassurements are clean room meassurements)

Here it gets hairy and subjective, Take something like redraw issues with metacity/gtk+/cairo/nautilus combinations that was recently uncovered - looks horribly slow but the data says otherwise, the cause, a slow path in GTK+ when using Cairo.

I suggest starting with Rasterman' WM torture tester for some basic results, able scripters and coders should definately look at extending this test and commit it to Freedesktop.org maybe.

[http://www.rasterman.com/files/wm_torture-0.1.tar.gz](http://www.rasterman.com/files/wm_torture-0.1.tar.gz)

---

### Post by Stormy Eyes on 2006-02-14
[QUOTE=fuscia]any of you try pywm yet?[/QUOTE]

I did, but I stick with Openbox.

---

### Post by fuscia on 2006-02-14
[QUOTE=Lovechild]d) How do we consider subjective experience that contradict the evidence (namely looking for what causes visual displeasure but is not WM related as the meassurements are clean room meassurements)
[/QUOTE]

lot's of reasonable points, but i wasn't trying to be reasonable. i just felt like talking about wms and speed. and speaking of subjectivity, have any of you ever noticed how much faster a wm is during the first fifteen minutes you ever use it, than it ever will be again?

[quote=Stormy Eyes]I did, but I stick with Openbox.[/quote]

what was it like? any unique features? or, was it just like flwm at a different speed?

---

### Post by super on 2006-02-14
on my machine my two fastest wm are:

openbox - this is the fastest according to top. it uses the least amount of cpu and mem. and it starts-up like greased lightning. but dragging windows around leaves the window contents half a second behind the window.

e17 - this is the fastest judged by how it appears. opening tons of windows and moving them around randomly seems to have no effect on the user interface. no  window/background artifacts when moving things. but top says that it's using 15% of my cpu when it's not in swap.

---

### Post by Stormy Eyes on 2006-02-14
[QUOTE=fuscia]what was it like? any unique features? or, was it just like flwm at a different speed?[/QUOTE]

Since I tried it a year ago and wasn't particularly impressed, I don't remember. Try it yourself; it might have improved.

---

### Post by Lovechild on 2006-02-14
[QUOTE=fuscia]lot's of reasonable points, but i wasn't trying to be reasonable. i just felt like talking about wms and speed. and speaking of subjectivity, have any of you ever noticed how much faster a wm is during the first fifteen minutes you ever use it, than it ever will be again?
[/QUOTE]

That is actually a well understood process in the brain, it simply adjusts to the new speed as being "default", this is also why hardware seems really fast when you get it, then a few weeks after it will seem slower than it was, however hard data shows the exact same metrics - the brain simply fools itself.

---

### Post by fuscia on 2006-02-14
[QUOTE=Lovechild]That is actually a well understood process in the brain, it simply adjusts to the new speed as being "default", this is also why hardware seems really fast when you get it, then a few weeks after it will seem slower than it was, however hard data shows the exact same metrics - the brain simply fools itself.[/QUOTE]

i'm not sure if it's that simple. in golf, there's something called the '45 day' rule. it states that a new piece of equipment will improve one's game for 45 days. after that, there is a return to one's previous level of mediocrity. my theory is that the new equipment forces the golfer to break out of a stagnating technique, for a while. after 45 days, the golfer becomes stagnant again and is usually not as suited for his new club as he was for his old club. there is a variety of responses when returning to the old clubs, including everything from making a step forward to completely losing one's previous feel (often leading to the placement of the club at the bottom of a favorite water hazard). so, in my experience, i think it is the novelty of a new wm that makes me think it's faster. (it may just be that it seems faster compared to my relative inefficiency with the new environment. that would certainly be somewhat inkeeping with your point.)

---

