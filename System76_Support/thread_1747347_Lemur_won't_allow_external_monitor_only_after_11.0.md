---
title: "Lemur won't allow external monitor only after 11.04 upgrade"
date: 2011-05-02
forum: System76 Support
---

### Post by Wood Prof on 2011-05-02
I upgraded to 11.04 on May 1st.  I have a model lemu2. Everything went smoothly and runs great, except when I cut off the laptop display and try running only an external monitor.  When the laptop display is cut off, the external monitor flickers and does not display anything recognizable.  Allowing it to revert back to the previous configuration causes both screens to turn black only showing the cursor.  Logging into tty3 and restarting X brings things back to normal with both displays on.

---

### Post by isantop on 2011-05-02
How are you attempting to activate the external monitor? I recommend using the "Monitors" configuration dialog over the Fn+F7 hotkey.

---

### Post by Wood Prof on 2011-05-02
All of this occurs using "Monitors" to select the monitor to use.

---

### Post by idotal on 2011-05-04
I had the same problem. A quick and dirty fix for me was to use the older 2.6.35 kernel. I've had random crashes before and after this.

---

### Post by isantop on 2011-05-05
Actually, I think I saw a bug report on that. I can't remember the number, but make sure your system is up to date, and try it again. If it isn't fixed yet, it will be soon.

---

### Post by Wood Prof on 2011-05-05
That's kind of what I thought, but it was worth asking to make sure I wasn't the only one.

---

### Post by isantop on 2011-05-06
UPDATE: We have been able to replicate this in the shop, and we've started a bug report on it:

[https://bugs.launchpad.net/system76/+bug/778641](https://bugs.launchpad.net/system76/+bug/778641)

---

### Post by Wood Prof on 2011-05-07
That's good to know. It means I didn't mess something up.

---

### Post by Wood Prof on 2011-05-11
So I tried using Xfce to see if I could replicate the problem there, and I am able to turn off the laptop display and run the external monitor.  Both Unity and Ubuntu Classic still will not allow it to happen.

---

### Post by isantop on 2011-05-12
Make sure you're totally up to date and give it another try today. For some reason, ours just started working.

---

### Post by markwillis82 on 2011-05-14
I have restored my drivers with the system76 program + performed all my updates, however I still have issues with external monitors (new lemu2 laptop)

Mark

---

### Post by Wood Prof on 2011-05-14
Even with all the updates, still have the problem except when using Xfce.

---

### Post by isantop on 2011-05-16
We'll keep looking at this issue. It is odd, since ours worked during testing, and we haven't done anything to ours to get it to work. Try getting an extended setup working first, by setting it up in monitor preferences, then pressing Alt+F2 and run this command:

```
unity
```

This will reset Unity and should get an extended monitor setup working. Then, try turning off the laptop monitor.

---

### Post by markwillis82 on 2011-05-16
Hi isantop,

That has worked... well eventually - I had to setup the monitors to the resolution I wanted then run the unity command.

I have attached a screenshot of my screens after I have setup the resolutions (before running unity) 

Am willing to help find a more permanent fix.

Mark

---

### Post by Wood Prof on 2011-05-16
I kind of got it to work to.  Here is what I did and the outcome:

I hooked up the external monitor (acer AL2216W, resolution 1680X1050) and opened the Monitors in Ubuntu.  I turned on the external monitor, leaving the laptop display on.  The monitor came on, but parts of the laptop display blacked out (not all of it).  I then pressed Alt+F2 and ran unity.  That made the laptop display go back to normal along with the external monitor.  I then tried to turn off the laptop display, which then made both screens go black, I had to then restart GDM (the unity reset would not work).

I then hooked a different monitor up (same model number), set the resolution lower (1024X768) and was able to cut the laptop display off with no problem.  I then changed the resolution to 1680X1050 and also had no problem.

So I tried one more thing, and plugged in the monitor I had had issues with, and had no problem.  

Then I tried starting over with the external monitor I had issues with from the beginning, by starting at a lower resolution (1024X768), and got the black screens again.

But if I use the other monitor and cuttoff the laptop display, I can then switch to the other monitor and get it to work no problem.  So it seems that one of the monitors is not communicating well with Unity, while the other one is.  

Now that I have written this I am throughly confused at why it worked.

---

### Post by Wood Prof on 2011-05-31
OK, so I was still having issues.  I changed the configuration so that the external monitor was the primary monitor when attached and bingo the problem is fixed.  I assume since I didn't have an issue with XFCE and the external monitor that it doesn't use the config file.

---

### Post by isantop on 2011-06-03
Actually, I think it's related to compiz. It seems to be having in issue with the Intel graphics driver.

---

### Post by stewpac on 2011-06-26
Is there some reason this thread is marked as solved? It doesn't appear to be solved to me. This is one of the reasons I have not upgraded my lemur so I would be interested in knowing when it is actually solved.

---

### Post by Grelf on 2011-06-26
This also sounds exactly like the issue I'm having with my new Pango p8. Thread [http://ubuntuforums.org/showthread.php?t=1788581]("http://ubuntuforums.org/showthread.php?t=1788581")

Seeing it marked solved, and knowing it's NOT solved, is really pushing me towards just returning it, and going with a different company.

---

### Post by Eldera on 2011-06-26
[quote=wood prof]I changed the configuration so that the external monitor was the primary monitor when attached and **bingo the problem is fixed**.[/quote]

Have a great day!

---

### Post by Grelf on 2011-06-26
> **Eldera said:**
> Have a great day!

That's not a bug fix, that's a workaround.

---

### Post by isantop on 2011-06-27
I should note that the thread is marked as Solved because the original posted was satisfied with the workaround. We (Systen76) actually can't mark threads as solved ourselves. We *don't* consider this solved.

This is caused by a bug in Unity, which currently seems to affect systems based on Intel graphics. It is currently filed in Launchpad, and is set at "Fix Committed, meaning that there is a fix that works, but hasn't been pushed down through the update manager yet. It should be coming in a couple of days.

[LP Bug# 795458](https://bugs.launchpad.net/bugs/795458)

---

### Post by isantop on 2011-06-30
As an update, there was a recent update to Unity pushed through Update Manager that seems to have fixed this problem on our Lemur in the shop. Updating fully should fix this issue.

---

### Post by Conzar on 2011-07-06
I am currently having the same issue with my Lemur.  HDMI with external monitor worked correctly before 11.04 update (on 10.10) and now is not working (blank screen of death - yes this is so bad its like windows).

Because of this problem, I tried using and am currently using the xorg-edgers repo.

Should I disable xorg-edgers and go back to Ubuntu xorg server?  Or is this problem still a problem (because xorg-edgers is using the latest code so any changes to fix the problem on Ubuntu xorg server should already be in xorg-edgers)?

Anyone else still having problems with this?

Thanks

---

