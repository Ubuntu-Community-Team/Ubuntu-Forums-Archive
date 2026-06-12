---
title: "One your computer - ONE BUTTON for end-user"
date: 2014-01-07
forum: Ubuntu, Linux and OS Chat
---

### Post by Raoul Soibel on 2014-01-07
Tune your computer - ONE BUTTON for end-user


Windows is rich on this type package. For many years I have been using 
      a) Iobit Advanced SystemCare - comprehensive, press one button it does all the job
      b) ToolwizCareFree - very fast, quick cleaner


Here in Ubuntu 13.10 I am looking at 2 applications: 
     a) **Synaptic Package Manager** - very comprehensive, a bit slow 
     b) **Muon Package Manager** - fast


As end user, I am afraid to use these Managers and make a mess out of my system.


My wish is that the developers of those two packages would invest a little to implement the ONE BUTTON SOLUTION special for End Users like me.


First step: run analysis of exists inside my computer, and find out whatever needs doing.
Second step: Ask the question, if this repair will take a long time, needs WiFi connection, run it now or later.


Thanking you for your kind attention.

---

### Post by Bucky Ball on 2014-01-08
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request.

---

### Post by QIII on 2014-01-08
> First step: run analysis of exists inside my computer, and find out whatever needs doing.

That is already done, to a great extent.

Have someone else make all the decisions?  Sorry.  I don't want someone deciding that for me on my Linux machine.

---

### Post by Bucky Ball on 2014-01-08
By the sounds of it, you want a Linux Windows. That's not going to happen. :-k

---

### Post by Copper Bezel on 2014-01-08
There used to be a thing called "computer janitor," right? But yes, Ubuntu handles most of these things internally, such as via the package manager itself (even when you're using Ubuntu Software Center instead of Synaptic.) There's no real need for those kinds of applications even in Windows, because they're frankly a bit scammy, but there's even less need in something like Ubuntu. (Likewise OSX, iOS, or Android, all of which also do internal housekeeping.)

---

### Post by oldos2er on 2014-01-09
If you're afraid to use a package manager (why?), wouldn't you be absolutely terrified to use a "one button solution"? I love package managers, but the one button idea does scare me.

---

### Post by Dave_L on 2014-01-09
[i]One Button to rule them all, One Button to find them,
One Button to bring them all and in the darkness bind them
In the Land of Mordor where the Shadows lie.[/i]

---

### Post by deadflowr on 2014-01-09
I don't know, but whenever I install Ubuntu, after I boot in the new install the first time, I normally get a notification for any additional drivers my system can use. Such as graphic card drivers and any wireless card driver if available.
I also notice that if I ignore the suggestion of installing those drivers that first time, I don't see those notifications again.

Also, in the update manner of 12.04, the old style update manger would display numbers in the icon, which told the user that X-number of updates where ready to download and install. It too would show a notification of updates, like the additional drivers, but those notifications would keep appearing until I installed them.
I can't remember if newer version of update-manger notifies of newer updates. But I think it does.

Outside of those two things, why would you need a one button solution to figure out what the system needs done.
All the system configuring should have been done mostly during the installation.

---

### Post by Habitual on 2014-01-09
> **Raoul Soibel said:**
> Tune your computer - ONE BUTTON for end-user
...
Here in Ubuntu 13.10 I am looking at 2 applications: 
     a) **Synaptic Package Manager** - very comprehensive, a bit slow 
     b) **Muon Package Manager** - fast
...
As end user, I am afraid to use these Managers and make a mess out of my system.

Doesn't this actually need 2 buttons? End users cannot run Package Managers without additional prompting (sudo password), IIRC.
There is no "one button" fix or "undo".

Your fear will alleviate when you find that the folks who built the OS have probably seen every situation that the "end user" can get himself 
screwed up on, and have prepared for it.
They wouldn't allow "end users" to push a single button and hose the system.

Just my opinion.

---

### Post by Copper Bezel on 2014-01-09
The ability to easily revert changes from the Software Center's History tab would be useful and "one-button" in the actual sense of the phrase, if not literally involving one button. Hell, it might be a right click and a menu option, then an authentication prompt, which technically *does *involve exactly one button. = ) 

I don't think that's what the OP is looking for, however.

---

### Post by Old_Grey_Wolf on 2014-01-09
Microsoft Windows applications like Iobit Advanced SystemCare and ToolwizCareFree don't apply in the Linux world. Linux doesn't have a registry that needs to be cleaned like Windows nor do the disk formats used in Linux require defragmenting. You can run an Anti-Virus/Anti-Malware app if you wish.

I must not understand what system maintenance you want to perform in one button click.

---

### Post by Copper Bezel on 2014-01-09
> [COLOR=#000000]Linux doesn't have a registry that needs to be cleaned like Windows[/COLOR][FONT=arial]

Well, to be fair, it sort of does, but you just have to run 
```

dconf reset -f  /

```
 = D[/FONT]

---

### Post by stalkingwolf on 2014-01-10
recovery mode?

---

### Post by Old_Grey_Wolf on 2014-01-10
> **Copper Bezel said:**
> [FONT=arial]

Well, to be fair, it sort of does, but you just have to run 
```

dconf reset -f  /

```
 = D[/FONT]

Do you run that command as part of your normal maintenance routine? I think the OP is asking about maintenance applications.

---

### Post by Gone fishing on 2014-01-10
My reaction was NOOOOOO I don't want the scumware you get on Windows which most optimisers are. However, Old_Grey_Wolf is right Ubuntu other Linux and BSDs don't degrade like Windows (this is a Windows feature) you simply don't need optimisers (which don't fix windows like reinstalling does). There is no reason not to use synaptic etc if you want but it wont magically make your computer faster

---

### Post by Pinoy Tux on 2014-01-13
There's BleachBit.  And Computer Janitor found in Ubuntu Tweak.

BleachBit should be in the repo.  Ubuntu Tweak's from a PPA.

As always, use caution and common sense when using 'cleaners.'

---

### Post by Copper Bezel on 2014-01-13
> **Old_Grey_Wolf said:**
> Do you run that command as part of your normal maintenance routine? I think the OP is asking about maintenance applications.

God no. I mean, I do if something's jacked up, after backing up the areas I need (like Compiz and Dash settings.) I was just being silly since the Windows Registry was mentioned and since dconf really is very much like the Windows registry now, but at least has a kill switch.

---

### Post by lykwydchykyn on 2014-01-13
Sounds like placeboware.  Maybe we need something like this:

```

for i in `seq 0 100`; do echo $i; sleep 1; done | zenity --progress --title="Optimizer" --text="Optimizing your PC"

```

:D  j/k

---

### Post by Dave_L on 2014-01-13
> **lykwydchykyn said:**
> Sounds like placeboware.  Maybe we need something like this:
...


That works great!  My computer runs twice as fast now. You should submit that for inclusion in the repos. :KS

---

### Post by deadflowr on 2014-01-13
> **Dave_L said:**
> That works great!  My computer runs twice as fast now. You should submit that for inclusion in the repos. :KS

By the time it made it into the repos it'll be too old a version.:popcorn:

---

### Post by MartyBuntu on 2014-01-13
Running "cleaners" on Windows boxes is generally a bad idea. They tend to do more harm than good, especially with folks that don't know what every setting does.
Registry cleaning is highly overated.

---

### Post by Copper Bezel on 2014-01-13
> **lykwydchykyn said:**
> Sounds like placeboware.  Maybe we need something like this:

```

for i in `seq 0 100`; do echo $i; sleep 1; done | zenity --progress --title="Optimizer" --text="Optimizing your PC"

```

> **Dave_L said:**
> That works great!  My computer runs twice as fast now. You should submit that for inclusion in the repos. :KS

Dammit, where the hell is that Like button already?

---

### Post by Dave_L on 2014-01-13
> **deadflowr said:**
> By the time it made it into the repos it'll be too old a version.:popcorn:

What about a PPA?

lykwydchykyn, are you willing to license this under GPL v3?

---

### Post by lykwydchykyn on 2014-01-13
> **Dave_L said:**
> What about a PPA?

lykwydchykyn, are you willing to license this under GPL v3?

I think we could dual-license it under PUEL and CDDA, or maybe the BSD license with the advertising clause. :)

---

### Post by Dave_L on 2014-01-14
> **lykwydchykyn said:**
> I think we could dual-license it under PUEL and CDDA, or maybe the BSD license with the advertising clause. :)

Enhancement request: Make it a background service to *keep* the computer optimized.  It should periodically do some heavy CPU loading, just so you know it's working. :idea:

---

