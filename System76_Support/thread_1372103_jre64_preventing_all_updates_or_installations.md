---
title: "jre64 preventing all updates or installations"
date: 2010-01-04
forum: System76 Support
---

### Post by watchpocket on 2010-01-04
When I try to update or install any software, I get this from Update Manager:

Exception:
```
CouldNotLoadArgumentException[ Could not load file/URL specified: 1]
    at com.sun.javaws.Main.launchApp(Unknown Source)
    at com.sun.javaws.Main.continueInSecureThread(Unknown Source)
    at com.sun.javaws.Main$1.run(Unknown Source)
    at java.lang.Thread.run(Unknown Source)
```Wrapped Exception:```

java.io.FileNotFoundException: 1 (No such file or directory)
    at java.io.FileInputStream.open(Native Method)
    at java.io.FileInputStream.<init>(Unknown Source)
    at java.io.FileInputStream.<init>(Unknown Source)
    at com.sun.javaws.jnl.LaunchDescFactory.buildDescriptor(Unknown Source)
    at com.sun.javaws.Main.launchApp(Unknown Source)
    at com.sun.javaws.Main.continueInSecureThread(Unknown Source)
    at com.sun.javaws.Main$1.run(Unknown Source)
    at java.lang.Thread.run(Unknown Source)
```

I'd really like to know what to do to fix this -- I can't update, upgrade, or install anything.  Please help, thanks for any suggestions, tips, ideas.

---

### Post by thomasaaron on 2010-01-04
Geesh! I've never seen Update Manager throw java errors! Those errors are given by the JRE, and they *seem* to be related to WebStart. But I'm not exactly sure yet.

Could you let me know *anything* you've done pertaining to Java? Have you installed a java base game? A little history...

---

### Post by watchpocket on 2010-01-04
Sorry, those messages indeed weren't from Update Manager, but I did last night get an error from update manager -- I posted it in the Absolute Beginner Talk forum.

Well, after briefly running a 32-bit Firefox (mistakenly not from package manager), I finally got a 64-bit FF with 64-bit Flash and 64-bit Java up & running right.

Things seemed ok for quite awhile, then this in the last week.  I have in System > Prefs > Sun Java 6 Plugin Control Panel and Sun Java 6 Policy Tool.  FWIW, looking in Java Cache Viewer, in the Java Control Pasnel, I see I have an "Expired" Resource named LQApplet.jar, URL of [http://cdn.pingtest.net/LQApplet.jar](http://cdn.pingtest.net/LQApplet.jar), modified Sep 25, 2009 and expired Dec 13, 2009, size 14 KB.

I havne't done any games (not a gamer), there is a Java applet I mainly use from my windows box at work to access my panix.com ISP shell,but  I've ony brought that up a couple of times from home. . . .

---

### Post by thomasaaron on 2010-01-04
Well, I don't see anything interesting online about the LQApplet.jar, and it's expiration date doesn't coincide with the problem. So, let's count that one out.

What version of Java does...

sudo update-alternatives --config java

...show you running?

---

### Post by watchpocket on 2010-01-04
Thanks for the reply -- I'll have that info tonight when I get home, when I also will go through this step-by-step remove-&-re-install guide [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java) posted by Tom.Swartz07 in absolute beginner talk.

---

### Post by watchpocket on 2010-01-05
> **thomasaaron said:**
> 
What version of Java does...

sudo update-alternatives --config java

...show you running?

I've just gone through the removal-and-install steps at:
<http://sites.google.com/site/easylinuxtipsproject/java>
 and installed the current java successfully, I think. 

But to answer your question:
```
[rj-home:~]  [v4.3.10]  zsh  612 --> sudo update-alternatives --config java
zsh: correct java to .java ?  ([Y]es  [N]o  [E]dit  [A]bort) n
There are 1 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                               Priority   Status
------------------------------------------------------------
  0            /opt/java/64/jre1.6.0_17/bin/java   1         auto mode
* 1            /opt/java/64/jre1.6.0_17/bin/java   1         manual mode

Press enter to keep the current choice
[*], or type selection number: 
```(I pressed enter.  I gather that this java should remain in "manual mode" because I installed it manually.) 

I just sucessfully downloaded the accessory "7zip" with no problems.  Looks like the problem of my being unable to download software from repositories because of jre warnings has been solved.

---

