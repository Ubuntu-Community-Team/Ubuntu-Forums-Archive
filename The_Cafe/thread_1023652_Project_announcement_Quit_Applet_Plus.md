---
title: "Project announcement: Quit Applet Plus"
date: 2008-12-28
forum: The Cafe
---

### Post by krokosjablik on 2008-12-28
I believe the current Ubuntu Hardy/Intrepid quit applet can be much better. For this reason the QuitAppletPlus project was started and is ready for your feedback now. Just test it and say what you think about it, the final results will be presented to the Ubuntu Desktop Team.

Highlights:
- friendly for non-technical users
- customizable default behavior to match power user's requirements, as well
- all quit actions are easy available, without overloading the view
- "Lock Screen" and "Shut Down" only with one click!
- extended quit options

See [QuitAppletPlus Wiki]("https://wiki.ubuntu.com/QuitAppletPlus") for more detailed description with a lot of screenshots, the installation guide and much more.

QuitAppletPlus is only a graphical prototype so you can test it without any fear :)

---

### Post by krokosjablik on 2008-12-29
Some comments from [brainstorm]("http://brainstorm.ubuntu.com/idea/16865/"):

> i think it should be also possible to add more items to the menu, or remove existing ones.
@kreep: for the beta version an option is planned for removing of the "Suspend(Standby)" and "Switch User" from the applet menu.
If you want to add any action dynamically (with user specified command), you could create a blueprint for this idea in quit-applet-plus project ([https://blueprints.launchpad.net/quit-applet-plus](https://blueprints.launchpad.net/quit-applet-plus)), it could be a central place to collect alternative ideas, finally that would be presented to ubuntu developers.

> We don't need yet another python interpreter running...
@hackel: the "QuitAppletPlus" is _only_ a graphical prototype/mock-up/fake. It will never be a real applet. It's only a kind of how to present the idea ;)

> I think the two should be merged...
@deathsshadow77: that is exactly the goal of this project! :)

> Save session? What?
@cyphax: you are right, some labels are not intuitive. In this case the tip text (in the screenshot not visible) could probably help: "Restore the actually running applications on the next log in".

---

### Post by krokosjablik on 2009-01-05
Vote on [Brainstorm]("http://brainstorm.ubuntu.com/idea/16865/")!
[[IMG]http://brainstorm.ubuntu.com/idea/16865/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/16865/)

---

### Post by krokosjablik on 2009-01-09
Die Beta Version is available, see the [installation guide]("https://wiki.ubuntu.com/QuitAppletPlus#Early%20access%20beta%20version").

P.S. some people have translated yet the applet in French and Spanish, it's just unbelievable! I love Open Source, Ubuntu, Launchpad and everything behind that! :D

---

### Post by Joeb454 on 2009-01-09
Moved to Community Cafe

---

### Post by Endolith on 2009-01-09
I'd really like the "reboot into..." functionality added.  I was looking at [packaging the bootnext script]("https://bugs.launchpad.net/ubuntu/+bug/304215"), but it would be best to build it into FUSA, like in this mockup.

---

### Post by krokosjablik on 2009-01-21
The final version is released! :)

See the project [wiki ]("https://wiki.ubuntu.com/QuitAppletPlus")for the [concept description]("https://wiki.ubuntu.com/QuitAppletPlus#Concept"), screenshots and [installation guides]("https://wiki.ubuntu.com/QuitAppletPlus#Installation").

---

### Post by Sand &amp; Mercury on 2009-01-21
Looks very powerful indeed, props to ya.

---

### Post by Endolith on 2009-01-21
Can you specify *which* users are still logged in?

---

### Post by krokosjablik on 2009-01-21
> **Endolith said:**
> Can you specify *which* users are still logged in?
Do you mean in this [warning message]("https://wiki.ubuntu.com/QuitAppletPlus#How%20to%20protect%20another%20logged-in%20users")? It would be very nice, but I have no idea how it should look exactly :D Perhaps somebody has an idea for this.

Additionally I think it would be much better if you could log out and switch to a related user from this dialog just with one click. But the current approach lacks this feature...

---

### Post by Endolith on 2009-01-21
> **krokosjablik said:**
> Do you mean in this [warning message]("https://wiki.ubuntu.com/QuitAppletPlus#How%20to%20protect%20another%20logged-in%20users")?Yes.  > It would be very nice, but I have no idea how it should look exactly :D Perhaps somebody has an idea for this.Just list them? 

> Other people (username1, username2, username3, ...) are currently logged into this computer.  If you restart or shut down the computer, they may lose their work.  You should log out and inform them.

[] Proceed anyway (not recommended)
[] Send a warning notification to other users, and then allow them [_10_] minutes to save their work before shutting down

---

### Post by krokosjablik on 2009-01-24
> **Endolith said:**
> Yes.  Just list them?

If the ubuntu developers will merge this applet into the current ubuntu applet (fast user switch applet), I will focus on this issue. Thank you.

You could track the current discussion about this project on the 	[ubuntu-devel-discuss]("https://lists.ubuntu.com/mailman/listinfo/Ubuntu-devel-discuss") and/or [ubuntu-desktop]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-desktop") mailing lists.

---

### Post by Endolith on 2009-01-24
> **krokosjablik said:**
> You could track the current discussion about this project on the     [ubuntu-devel-discuss]("https://lists.ubuntu.com/mailman/listinfo/Ubuntu-devel-discuss") and/or [ubuntu-desktop]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-desktop") mailing lists.

I hate mailing lists :)

---

### Post by krokosjablik on 2009-02-28
QuitAppletPlus conclusion.

The last status is, actually there aren't any plans to integrate the
ideas from this project into the f-u-s-a (I contacted Ted Gould from
Ubuntu Desktop Team directly, even though he finds some ideas
interesting). I respect this decision surely.

This project is completed from my point of view. If somebody would like
develop the QuitAppletPlus prototype further on or fill that with the
real life, please contact me, then I will change the project
maintainer/driver respectively: [https://launchpad.net/quit-applet-plus](https://launchpad.net/quit-applet-plus).
A short introduction of you and what is your intention for this project
would be appreciate.
 
I had fun with this project, I have learned a lot of thinks. I would
also say many thanks to all project contributors for your feedback,
translations and bug reports. :)

---

### Post by blueshiftoverwatch on 2009-02-28
I don't use the quit applet Ubuntu includes now. Mainly because I don't see the need to put something that I access maybe once a day on the taskbar.

---

