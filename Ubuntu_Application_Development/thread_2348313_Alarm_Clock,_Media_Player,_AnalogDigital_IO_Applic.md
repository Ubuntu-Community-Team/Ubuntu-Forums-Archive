---
title: "Alarm Clock, Media Player, Analog/Digital I/O Application"
date: 2017-01-02
forum: Ubuntu Application Development
---

### Post by vector3 on 2017-01-02
I thought of an application or, change(s) to existing applications that I would like to carry through and develop.  I need some level of direction from those more knowledgeable than I.

The idea is fairly straight forward at a high level.  After the alarm clock executes I want it to output a variable to a media player (e.g., VLC Player) to turn it on for a specific album or play list.  Ideally, I would like to program the time the media player operates as well.  Do you consider this feasible?  Why or why not?  Please direct me to the appropriate modules or packages in source code as well as a distribution or version if appropriate.

I am considering this for both Ubuntu and Android applications yet, should pursue the easier target initially.  For example, the Android application would require installing 10.04.4 LTS onto one of my Linux machines.  At the moment, I have a net book running Bodhi 4.0 (no alarm clock so, I may need to use apt-get to add this functionality).  This may not be the best hardware/OS platform to proceed with so, this is why I mention it.  Alternative pc's that I will be installing Ubuntu on are an i5 2.67 GHz Lenovo Thinkpad X201 w/Win7 Pro or an i7-5400U Acer TMP-645 Ultrabook also running Win7 Pro.  I intend to install an Ubuntu LTS on each of these laptops resulting in dual boot systems to preserve Win7 and protect the machines.  Lastly, I could also install a extremely light weight Ubuntu on my P3-866 Dimension 4100 or XPS 8800 if need be.  I am simply looking for a sound platform to proceed with yet, prefer to use the Lenovo or one of the older Dell's because, the Acer belongs to my wife and an ultrabook can be delicate in view of their light weight whereas the Eee PC 1000H and the X201 are more robust portable machines.  Ultimately, the computer and OS do not matter..I just want to bring this idea to fruition.

Thanks for the help.

---

### Post by TheFu on 2017-01-02
Welcome to the forums.

Without a GUI, doing this on any Linux is trivial. Use **bash** and **sleep** and send the playlist as an option to vlc.  **man vlc** will provide the different options that program can accept. As a programmer, you need to get used to reading manpages. Same for sleep.  I would use perl myself, since there is a date/time class which supports math functions.  I suspect python and ruby can probably easily handle this too.

We cannot discuss 10.04 here. That release has been unsupported for almost 2 yrs.

Android development is an odd version of java.  It requires a powerful machine with as much RAM as you can provide, 8G is barely enough.  32G would be better.

There are lots of alarm-clock applications on both Android and Linux. Not sure why you want to re-invent that wheel. Find the source for one of those and work your way through it.  I use alarm-clock-applet on Ubuntu.

Don't know anything about Bodhi, so I won't reply to any of those questions. If it is Linux, then there are alarm-clocks available.  Just look a little deeper or get the source for an existing one and work from there.

Most people come  to programming with a specific language they need to learn. You don't seem to have that which is shocking.

When a alarm occurs, I'd make a configurable system() call. Any language should be able to do this. That way, you don't hardcode vlc into the program.  In fact, you might want to have 10-20 options for what any alarm does at completion. It wouldn't be hard.

BTW, at the first of the year, lots of people decide they want to learn to code. Then after a few hours, they learn this is a 3-12 month project just to become a beginner.  Do a little every day, at least 5 days a week.  A little is 1-2 hours. 

People used to ask "how to learn to program" all the time - I wrote this: [http://blog.jdpfu.com/2011/10/19/how-to-learn-to-program](http://blog.jdpfu.com/2011/10/19/how-to-learn-to-program)

Doing GUI programming takes another level of skill - usually delayed for 3+ months.

---

### Post by vector3 on 2017-01-03
TheFu,

Thanks for the response.  It is useful.  I clearly do not own a computer to handle Android/JAVA.  This project required 10.04 so, it is off the table for now; perhaps permanently.

I have a background in programming, primarily embedded systems, just did not mention it.  Sorry for the oversight.  Realizing my idea is the import rather than the language used to achieve this.

I looked at your html page regarding programming.  It is a good collection of information.

---

