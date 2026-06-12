---
title: "ya think WINE will get better from now on?"
date: 2009-07-11
forum: The Cafe
---

### Post by SonnHalter on 2009-07-11
WINE has its ups and downs in each version like version 1.1.21 won't run photoshop whilst 1.1.20 will run it better.

---

### Post by MaxIBoy on 2009-07-11
Just add WINE's special repositories, not from Ubuntu's repositories. You'll get a much more up-to-date version that way, and you get updates to it every two weeks.

Up until very recently I was using 8.04, and I was able to keep up with the latest updates to WINE. It's really getting there. (Although I still can't get steam:// download links to work for some reason.)

---

### Post by SonnHalter on 2009-07-11
not talking about the wine version, the ubuntu version.

---

### Post by swoll1980 on 2009-07-11
> **SonnHalter said:**
> not talking about the wine version, the ubuntu version.

"ya think ***WINE ***will get better from now on?"

---

### Post by SonnHalter on 2009-07-11
> **swoll1980 said:**
> "ya think ***WINE ***will get better from now on?"

sorry

 WINE*

---

### Post by stwschool on 2009-07-11
Ok I'll take a guess you're new to all this as you seem a little confused so I'll help you out..

Ubuntu is the version of linux you're using. They offer lots of packages, and they tend to pick something stable rather than the latest and greatest.

Wine is a project to make windows stuff work in linux. It's a brilliant piece of engineering. The version you get by default in ubuntu is something like 1.0.1 wheras the version you can get from Wine's own servers is 1.1.25. It doesn't sound much but it's a big difference. My current box runs football manager, civ 4, braid, COD 4, MS Office 2007 and a whole bunch of other stuff without problems, so really it's damn good.

You want the latest? Go to System -> Administration -> Software Sources -> 3rd Party and add one of these (depends on your version):

For Ubuntu Jaunty (9.04):
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"

For Ubuntu Intrepid (8.10):
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

For Ubuntu Hardy (8.04):
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"

Hope this helps clear things up a little.

---

### Post by SonnHalter on 2009-07-11
you people make me facepalm so much. :(


nevery mind.

---

### Post by Sealbhach on 2009-07-11
> **SonnHalter said:**
> you people make me facepalm so much. :(


nevery mind.

Wine improves with age, everybody knows that.


.

---

### Post by stwschool on 2009-07-11
Nice way to talk to people who are trying to figure out what your on about/help you.

---

### Post by toupeiro on 2009-07-11
> **SonnHalter said:**
> you people make me facepalm so much. :(


nevery mind.

Say what you mean, mean what you say.

---

### Post by Sealbhach on 2009-07-11
> **stwschool said:**
> Nice way to talk to people who are trying to figure out what your on about/help you.

Well you help him then, I don't know what he wants, I don't understand the question.


.

---

### Post by Tipped OuT on 2009-07-11
He's just asking if you think Wine will get better over time or not.

---

### Post by Danny Dubya on 2009-07-11
> **SonnHalter said:**
> WINE has its ups and downs in each version like version 1.1.21 won't run photoshop whilst 1.1.20 will run it better.
Depends on your definition of "better", I guess. More supported features and compatibility with a growing number of Windows applications? Probably. Better able to run *Photoshop*, or <put any other single app here>? Who knows. WINE is a huge project and there's thousands of apps that can run on it. One well-intended change to WINE's codebase can have unforeseen consequences, much like whatever caused Photoshop to regress to not running for you in 1.1.21.

---

### Post by stwschool on 2009-07-12
The thing with Wine is it's a hugely complex project. As the site states, the development version has occasional regressions but generally things are on an upward curve. I understand why, as they make a change to fix things in some apps, and then find other apps don't like it, but usually a couple of updates down the line things are smoothed out. The development version has been remarkably stable for me so I'm very happy with it.

For me, I take the occasional regressions in my stride, and enjoy the end result of these peoples work, and I'm immensely greatful for what they give me. They make it possible for me to be in Linux for everything that matters, and thus help me keep secure.

---

