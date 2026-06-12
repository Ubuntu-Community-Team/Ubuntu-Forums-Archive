---
title: "Ubuntu Exit Strategy Proposal"
date: 2008-02-04
forum: Ubuntu Brainstorm
---

### Post by krokosjablik on 2008-02-04
It's a proposal for the new [Ubuntu Exit Strategy Specification]("https://wiki.ubuntu.com/DesktopTeam/Specs/ExitStrategy"), what is trying to solve actual problems with the quit dialog that is confusing in many ways. I think the actual problem is not only a lot of exit options, but also the wise this options are offered &#8211; in the two-dimensional matrix of buttons.
I find the new approach is very interesting in many ways (even revolutionary), but I think some things as to take the control away from users is not a good idea. I definitely want  to decide myself when and how to exit, the computer should support but not control me (decides for me too, but only if I want it...).
So I used some ideas from this new specification, but with the goal to remain the control by users and, yes, to simplify the actual exit approach. It's more the classical way, let take a look...

Downloads:
[ubuntu-exit_specification_20080204_version2.pdf]("http://forum.ubuntuusers.de/download/9031/")   (162.66 KB)
[ubuntu-exit_specification_20080204_version2.odt]("http://forum.ubuntuusers.de/download/9030/")  (135.05 KB) 

PS: my proposal isn't a dogma, please feel free to change it, make it more better (or also worse :)), I think the both approaches could collaborate in many ways...

---

### Post by Zeroangel on 2008-02-04
I think there are some good points on the specification you provided. 

- Allowing the user to restart into a different OS or kernel is an excellent idea. As it prevents them from having to wait around for the reboot and grub screen to select a different OS.

- I disagree with the hibernate option being brought into a new menu. In my opinion 'sleep' and 'hibernate/suspend' are two distinct options and easy to pick apart when all of the shutdown-related icons are displayed.

- I'd like to push my idea a little more about CTRL+ALT+DEL being used for a process/service/security manager. The logout should be moved to CTRL+ALT+END since the end session button is already accessible from the gnome-panel -- and Windows users or windows 'refugees' have been trained through repetition to think of that as the 'task manager'.

- I'm not all for the lack of 'session' options on GDM. I personally like to switch between KDE and GNOME sometimes.

---

### Post by lexen on 2008-02-04
Things I liked:
Menu attached to shut down button
Preferences added to shut down
Shutdown warning when other users have unsaved things open

Things I think you should change:
"Stat finally" should be re-worded to "restart to:" because "start finally" isn't self-explanatory.
double clicking the shut down button should shutdown

Things I don't like:
I fear the entire thing makes it too complicated.  If we did this, a lot of people would find it a step back.  Lessen the amount of work it takes to do each task, not make it harder.



Those are my two cents,
Lexen

---

### Post by zekopeko on 2008-02-04
here's a read

[http://www.joelonsoftware.com/items/2006/11/21.html](http://www.joelonsoftware.com/items/2006/11/21.html)

---

### Post by krokosjablik on 2008-02-05
> **Zeroangel said:**
> I think there are some good points on the specification you provided. 

- Allowing the user to restart into a different OS or kernel is an excellent idea. As it prevents them from having to wait around for the reboot and grub screen to select a different OS.

"restart into a different OS" isn't my idea (see [original specification]("https://wiki.ubuntu.com/DesktopTeam/Specs/ExitStrategy")), i have only placed this option in the shutdown alert dialog, but i'm surely glad if you like it too :-)

> **Zeroangel said:**
>  
- I disagree with the hibernate option being brought into a new menu. In my opinion 'sleep' and 'hibernate/suspend' are two distinct options and easy to pick apart when all of the shutdown-related icons are displayed.

Do you mean, the exit menu should have explicit the Suspend and Hibernate items: Lock Screen, Log Out, Suspend, Hibernate, Shutdown?

> **Zeroangel said:**
>  
- I'd like to push my idea a little more about CTRL+ALT+DEL being used for a process/service/security manager. The logout should be moved to CTRL+ALT+END since the end session button is already accessible from the gnome-panel -- and Windows users or windows 'refugees' have been trained through repetition to think of that as the 'task manager'.

Sorry, I don't understand your idea. I think my english ist not good enough. Could you explain it more detailed?

> **Zeroangel said:**
>  
- I'm not all for the lack of 'session' options on GDM. I personally like to switch between KDE and GNOME sometimes.
Oh no, I didn't mean it...
I only didn't want to show all items due to place saving in the specification :)

---

### Post by krokosjablik on 2008-02-05
> **lexen said:**
> 
Things I think you should change:
"Stat finally" should be re-worded to "restart to:" because "start finally" isn't self-explanatory.
double clicking the shut down button should shutdown

English is not my first language, neither the second :-) So please feel free to make the textes better or just get your comments here as above, thank you.

> **lexen said:**
> 
Things I don't like:
I fear the entire thing makes it too complicated.  If we did this, a lot of people would find it a step back.  Lessen the amount of work it takes to do each task, not make it harder.

It's a full specification, and full specifications are never implementated ;-)
Between the "Light Edition" and "Full Edition" you have the whole range of features you can choose, it's only a rough conception.

---

### Post by krokosjablik on 2008-02-05
> **zekopeko said:**
> here's a read

[http://www.joelonsoftware.com/items/2006/11/21.html](http://www.joelonsoftware.com/items/2006/11/21.html)
The [actual specification]("https://wiki.ubuntu.com/DesktopTeam/Specs/ExitStrategy") is very similar. I really think this approach will definitely be our feature soon, but not at this time (perhaps in two - four years), because for example our hard drives will be broken very quickly if you have too many stop/start cycles (in contrast to iPod that hasn't any hard drives)... In my opinion, we are not ready for this yet, the hardware is not ready. 
But I am sure the both approaches should cooperate with each other, so the new approach will be realized evolutionary and not revolutionary.

---

### Post by Zeroangel on 2008-02-05
> **krokosjablik said:**
> Do you mean, the exit menu should have explicit the Suspend and Hibernate items: Lock Screen, Log Out, Suspend, Hibernate, Shutdown?
Yes. The way that it is set up right now is perfect. There are 5 options, and each has a big, unique icon, and there is a description when you hover over them.
This is very usable compared to vista/XP.

Configuration would be nice though, as in your specification -- adding the ability to configure by right-clicking on the shutdown icon (in the panel) would be nice. KDE does this with their 'Lock/Logout' applet when it is added to Kicker (the KDE panel).

> **krokosjablik said:**
> Sorry, I don't understand your idea. I think my english ist not good enough. Could you explain it more detailed?
What I mean is change the 'Logout/shutdown' shortcut keys to CTRL+ALT+END -- Whereas CTRL+ALT+DEL is used for the task manager -- where you have the option to kill programs that are running.

> **krokosjablik said:**
> Oh no, I didn't mean it...
I only didn't want to show all items due to place saving in the specification :)
I understand. Any simplicity/elegance that we can add to the GDM/KDM is good I say. It is happening more often that GDM/KDM developers are starting to do this.

---

### Post by krokosjablik on 2008-02-07
> **Zeroangel said:**
> 
What I mean is change the 'Logout/shutdown' shortcut keys to CTRL+ALT+END -- Whereas CTRL+ALT+DEL is used for the task manager -- where you have the option to kill programs that are running.

I undestand, I have just now seen [ [IDEA] CTRL-ALT-DEL brings up system monitor]("http://ubuntuforums.org/showthread.php?t=420170") and your post  [Remapping CTRL+ALT+DEL logout to CTRL+ALT+END]("http://ubuntuforums.org/showthread.php?t=681788")

If a lot of people find out the same ideas independently from each other, I would say it's a good idea, because the good things are not invented but discovered.

And yes, I like your idea with "Remapping CTRL+ALT+DEL logout to CTRL+ALT+END". It's better than "ALT+DEL" in my proposal.

---

### Post by krokosjablik on 2008-02-11
I will be for next three weeks away, see you...

---

### Post by krokosjablik on 2008-03-20
If you want you can push this idea on the brainstorm.ubuntu.com: [Ubuntu quit actions as context menu under the quit button - not as quit dialog]("http://brainstorm.ubuntu.com/idea/4749/")

---

