---
title: "The Superiority of Linux: or not having to reboot"
date: 2009-09-05
forum: Testimonials &amp; Experiences
---

### Post by hetx on 2009-09-05
I have a decent computer, 3GB OCd RAM running 32bit Jaunty on 3.6GHz OCd core 2 duo. Ubuntu runs smooth as can, never had a problem and very few, what a Windows user would call, crashes.

In fact, I had one not 5 min ago. I run Chromium with 43 tabs (90MB mem use, you've got to be kidding me. That's Chromium's built in memory manager, other software will report incorrect numbers from what I understand.) Other than that I got a bunch of things going on, basically a horrible time for a freeze.

Which is of course what happened. Ubuntu One client (it is a beta and I'm fully aware of the risk I take) reported loss of connection. On reconnecting I got that nasty red exclamation mark. An impatient computer user I click it a couple of times more than I should, then quickly cancelling the Apport window, resulting in a freeze. I couldn't click anything, no commands.

Waited for a bit, feeling desperate (alot of work might have been lost, had I used Windows). But as a Linux user the problem was easy to solve. Switched to tty1, found the violating process, killed it and I'm back. Nothing lost, no problem.

And my class mates ask me WHY I use Linux...

Edit: 100th post on the forum!

---

### Post by jrusso2 on 2009-09-05
And you don't know how to kill a process in Windows? CTRL ALT DEL go to task manager, find your process, right click and end process.

---

### Post by hetx on 2009-09-05
Good job reading the post. I clearly pointed out that everything was frozen. Unresponsive to keyboard commands and mouse clicks. As a Windows install is prone to, and  Linux install will on occasion, become. Especially if you run beta software.

---

### Post by jrusso2 on 2009-09-05
Like you said the same thing happens in Linux.  In fact I was installing something with WINE and it just occurred.

---

### Post by hetx on 2009-09-06
It's nice not having to resort to flipping the switch!

---

### Post by j7%&lt;RmUg on 2009-09-07
My ubuntu install has only ever crashed once in the 9 months iv been using it.

Although i didnt blame ubuntu because i was running firefox with 9 tabs, amsn, xchat, openoffice, gedit, a terminal that was apt-getting around 400MB of stuff and i was also fiddling around in another terminal.

Though i was still surprised that ubuntu could do that much at the same time, windows would have not lasted long in the same situation.

---

### Post by Zoot7 on 2009-09-08
The only time Ubuntu ever locked up on me I was copying files, extracting files, torrenting, encoding video and fiddling with trying to compile an app from source at the time, and that was with Feisty.

Since the upgrade to Hardy it hasn't crashed on me since, despite heavier multitasking loads. Forget trying to similar amounts of things with Windows.
Granted the system is a tad sluggish doing all that at the one time, but drop the priority on the CPU intensive tasks and I find it's fine.

:)

---

### Post by xieqiao on 2009-09-08
Would you tell me what's the equivalent for CTRL ALT DEL under Ubuntu? 

How could I Switch to tty1 and kill a process?

---

### Post by wojox on 2009-09-08
Ctrl + Alt + F2

Login

Run the top command.

Press k

Enter PID #

q to exit top

exit to quit

---

### Post by hetx on 2009-09-08
Just to add some description to what he said.

**Ctrl + Alt + F2** switches tty

You will be prompted for user name and password.

Next you run **top** which will show you active processes. Your troublesome process will probably be easy to spot, overusing CPU. Note the PID number, press **k** and type in the number. Finish top by pressing *q*.

If you can't find the process in top but have an idea of what it is, try running the command
```
ps -e | grep NAME
```
Where name is whatever the process is called.

It will return the name of it and the PID #. You can now kill it by **kill PIDNUM** (some processes require sudo)

Now you can return to your graphical tty by pressing **Ctrl + Alt + F7**

There are of course many ways of finding and solving the problem, but these are some of the easier.

---

### Post by Irihapeti on 2009-09-08
Just a nitpick for anyone else who may be reading. It may be different on Jaunty, but on my Hardy machine the commands are Ctrl-Alt-F2 and Ctrl-Alt-F7. (Alt-F2 just gives me a "run" dialogue without switching the tty.)

I didn't know about this at all, so thanks for the information. I wish I'd known a lot sooner - could have got me out of a few difficulties more easily.

---

### Post by Bibek on 2009-09-08
> **hetx said:**
> Just to add some description to what he said.

**Alt + F2** switches tty



Its CTRL+ALT+F2 :)

---

### Post by hetx on 2009-09-11
ye sorry, fixed it

---

### Post by murderslastcrow on 2009-09-12
Lol, I love stories like this.

"The ONE TIME my Linux computer crashed, only after I compiled my own kernel, added a PPA for beta software and opened a ton of stuff and tested out several experimental features simultaneously.... and all I had to do was quit the program." XD

To be honest, I've never had a problem with Linux that wasn't specifically hardware related.

---

### Post by hetx on 2009-09-13
Wow this is really not the reaction I was hoping for. Since when did this forum get so hostile?

To clarify for murderslastcrow, the program that crashed was Apport. A stable native Ubuntu app. If you've never had a crash then you've just never pushed your system very hard. Not everyone needs to be a power user.

And the issue was not whether or not killing the offending process would stop a problem, I'm sorry if you feel special for understanding that, cause it's not really special knowledge, the issue was that in Linux you almost ALWAYS have the option to switch terminals and solve problems. This luxury you don't have in Windows.

But most of all I just wanted to share a moment of happiness with the forum. We've all had that situation where alot of work was riding on the computer being stable, and it dying for whatever reason. The panic, the desperate flailing about and shouting at the computer. And then the satisfying realisation that there's a solution.

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-09-13
Good OS design

---

### Post by moster on 2009-09-13
> **jrusso2 said:**
> And you don't know how to kill a process in Windows? CTRL ALT DEL go to task manager, find your process, right click and end process.

Only in theory, only in theory.

---

