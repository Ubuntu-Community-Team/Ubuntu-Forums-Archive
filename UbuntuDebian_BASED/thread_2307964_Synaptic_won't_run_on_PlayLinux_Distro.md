---
title: "Synaptic won't run on PlayLinux Distro"
date: 2015-12-29
forum: Ubuntu/Debian BASED
---

### Post by xvampssx on 2015-12-29
This may be a long shot, but I need help getting Synaptic to run on PlayLinux. I know it is in the alpha stage at the moment, and it is ubuntu based, so please any insight or workaround would be appreciated.
I installed it with the Software center, rebooted, it shows that it is installed but will not open. I doubled checked its installation in terminal, and still will not open. Trying to install libluabind 0.9.1. to run Ryzom with it.

---

### Post by deadflowr on 2015-12-29
Moved to [I]Ubuntu/Debian Based


[/I]&#8203;and edited the title to make it more clear to others...

---

### Post by xvampssx on 2015-12-30
Thank you [COLOR=#C61919]**deadflowr**[/COLOR]

---

### Post by v3.xx on 2015-12-30
>  I doubled checked its installation in terminal, and still will not open.

Did you try to open it in terminal?  Two ways to do that

```
synaptic
```

or

```
pkexec synaptic
```  or  ```
synaptic-pkexec
```

and I think graphical sudo still works in 14o4.

```
gksudo synaptic
```

---

### Post by xvampssx on 2015-12-30
[COLOR=#000000]and I think graphical sudo still works in 14o4.[/COLOR]

[COLOR=#000000]Code:
gksudo synaptic[/COLOR]
You are a life saver, thank you. I only verified the install did not try to run it from the terminal, as i did not know the codes, Thanks for this :)

---

### Post by v3.xx on 2015-12-30
/usr/share/applications/synaptic

contains the launcher.  You should also be able to click on that to open synaptic.

and..

Right click on that launcher and select properties to see the launch code.

---

### Post by xvampssx on 2015-12-30
sudo synaptic-pkexec

That is the code it is showing, it works. Thank you :D

---

### Post by v3.xx on 2015-12-30
And welcome to the forums :D

One last tip..
You can drag that launcher (or any other) to the panel from applications.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

