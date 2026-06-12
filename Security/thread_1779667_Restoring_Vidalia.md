---
title: "Restoring Vidalia?"
date: 2011-06-10
forum: Security
---

### Post by M3TAZ3R0 on 2011-06-10
I accidentally hid the GUI for Vidalia and I have no clue as to how to restore it to switch my ip. Tried running the exe only to have it tell me that i am still of course running vidalia and this would only open a second instance. Is there some magic keystroke to restore the gui window?

---

### Post by M3TAZ3R0 on 2011-06-11
the current problem is solved, though another has risen. Everytime I exit vidalia or hit stop tor then exit or shut down outright, Tor seems to still be running on restart and after exit not allowing me to open vidalia and connect to the tor network. I always have to end up using a stop command on tor to rectify the problem. Hopefully i explained this well enough.

---

### Post by robbiemacg on 2011-07-15
So, how'd you get access to the GUI? 
TOR's good, Polipo's doing what it should, TORButton is AOK... but I'm failing the TOR Check and my node's not showing up any more. That GUI might come in handy for me. Even when I kill all my TOR and Vidalia processes and try to start up a new instance of Vidalia I see nothing.

*Sure do wish I still had an applet

---

### Post by robbiemacg on 2011-07-15
p.s. I think I can solve your problem if you can help with mine.
When I do a new install of Vidalia on a system I make an** /etc/defalut/tor.vidalia** file that looks like this:
```

if [ -x /usr/bin/vidalia ]; then
    RUN_DAEMON=no
fi
```


 Keeps TOR from starting on it's own.

R.

---

### Post by robbiemacg on 2011-07-16
I got my applet/tray icon back by running:
```

gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

Now to troubleshoot Vidalia proper. :/

---

### Post by hkarn on 2011-08-29
Can you please tell me how you got the Vidalia GUI back? I hid it and unticked displaying the GUI on startup. Now it just runs in the background and I don't know how to restore the window...


For your other problem of TOR launching independently from Vidalia on boot my solution was this:
I solved the problem of TOR already running on boot by downloading BootUp-Manager from the software center. I removed tor in that which stopped it from starting automatically.

Then I added Vidalia to additional startup programs in System Settings -> Startup Applications.

I am not sure how clean that is but it works great now anyway. Vidalia will start automatically and launch TOR on it's own.

---

### Post by robbiemacg on 2011-08-29
Hi [hkarn]("http://ubuntuforums.org/member.php?u=1202859"),
Did you try running the above command? That should return the Vidalia applet to your panel, provide access to the GUI.

---

