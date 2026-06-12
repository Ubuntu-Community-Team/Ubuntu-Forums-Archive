---
title: "Opening and Closing Projects that use Many Programs"
date: 2010-11-05
forum: Ubuntu Studio
---

### Post by halfpower on 2010-11-05
Let's say I have a musical project that uses many programs together.  Is there an easy way that I can open and close everything together?  Has anyone written any shell scripts that serve this purpose?

---

### Post by AutoStatic on 2010-11-05
Hello halfpower, at the moment session management is a hot topic. There are currently three ways to set up and maintain sessions:
[LIST][*][Ladish]("http://ladish.org/")
[*][JACK session management]("http://trac.jackaudio.org/wiki/WalkThrough/User/jack_session")
[*]Writing your own scripts
[/LIST]
As both Ladish and JACK session management are not fully adapted by all developers yet I personally prefer to write my own scripts.
And yes, there's [LASH]("http://www.nongnu.org/lash/"), but afaik it's not really being maintained anymore.

Best,

Jeremy

---

### Post by Pablo_F on 2010-11-05
Hi!

I also use scripts, but they are very simple, just launch a program-wait a bit-launch another-wait a bit, and so on. I normally use hydrogen and ardour, so, for example:

/home/pablo/bin/hydrogen-ardour

#!/bin/bash
hydrogen &
sleep 5
ardour2

Needless to say, I launch this after jack is up and running. It is not ideal, but it works and it helps a bit. To improve it, read this:

[http://digitaldub.wordpress.com/2009/12/16/linux-audio-session-scripting/](http://digitaldub.wordpress.com/2009/12/16/linux-audio-session-scripting/)

Also, you can use qjackctl to load scripts, at 4 differents stages (more or less this is what I understand):

1. Just before jackd starts
2. Just after jackd starts
3. Just before jackd stops
4. Just after jackd stops

So you can always put your script to launch the jack-aware apps at the second stage, so if you have configured qjackctl to launch the server at application start, you are done with a click, or almost done. At the third stage you can "killall patchage ardour2 hydrogen whatever". Then "killall jackd" at the 4th stage.

There are so many options... If you have a well defined workflow, session scripting can be the best choice by the time being, imho, at least in ubuntustudio. As Auto has pointed out, not all apps support ladish level 1 but I think falktx's KXstudio has ladish if you want to try from his PPA (if you are in lucid). Jacksm is not even released upstream to this day (but you can get it from svn or git, see Auto's link).

Cheers! Pablo

---

### Post by Pablo_F on 2010-11-06
There is another example here:

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

