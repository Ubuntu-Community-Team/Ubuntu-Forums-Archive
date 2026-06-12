---
title: "How can audio tracks be mixed together at the command line?"
date: 2008-11-04
forum: Ubuntu Studio
---

### Post by sumadartsan on 2008-11-04
I wish to take two input audio tracks and mix them together into a single audio file that plays both audio samples simultaneously.  I understand that Audacity can do this, however, I require doing this to about 50 audio files or more and it is extremely tedious and time consuming to use Audacity for this task.  I need a command line method to mix the tracks so I can make a script to act on all of the audio files in succession. Could anyone tell what command line tools exist to accomplish this and perhaps give me some insight about how to use the tools to mix two tracks?

---

### Post by thorgal on 2008-11-04
you could have some luck with ecasound. It's a command line multitrack software.  I cannot guide you there because I rarely used it, only for quick capture. But i know itr is extremely powerful and is flexible enough to be used in batch mode (script) or interactive (terminal session).

[http://www.eca.cx/ecasound/](http://www.eca.cx/ecasound/)

the package should be in the repos.

From the website :

> 
Novel user-interface concept

      What makes Ecasound unique is its non-graphical user-interface. The basic working principle of ecasound is similar to the widely used gdb (software debugging) and mysql (database admin) tools. Ecasound allows the user to perform most common tasks directly from the terminal console. **Repeating or otherwise complicated tasks can be easily turned into shell scripts** or ECI apps. Ecasound tries to follow the time-tested UNIX design practises - see for example The Art of UNIX Programming by Eric S. Raymond. 


---

### Post by ajgreeny on 2008-11-04
**cat** may allow you to do it, though how much control you will have, I can not tell you.  I think it may just add one file to the end of another, which is not what you want, I think.  Have a good look at ```
man cat
``` for details of what is possible.

---

### Post by Stochastic on 2008-11-04
cat really shouldn't be used for audio as it doesn't deal with audio headers properly.  Use ecasound, it's quite robust.

---

### Post by sumadartsan on 2008-11-04
Thank you very much.  Ecasound looks like the solution.

---

