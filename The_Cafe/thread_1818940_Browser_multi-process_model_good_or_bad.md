---
title: "Browser multi-process model good or bad?"
date: 2011-08-05
forum: The Cafe
---

### Post by lovinglinux on 2011-08-05
Mozilla has a project, called [Electrolysis]("https://wiki.mozilla.org/Electrolysis"), that aims to make Firefox a multi-process application, with separate processes for the user interface, each tab, and plugins. The plugin separation is already available since Firefox 3.6.

Such implementation would provide better performance and stability, since a crashed tab wouldn't take down the entire browser. You probably already experienced that when flash crashes. Before Firefox 3.6 it would take the entire browser down, but with out-of-process plugin implementation you just get a warning where the flash content should be displayed.

Chrome already is a multi-process application, which is one of the reasons why Chrome outperforms other browsers in benchmarks. However a recent [experiment]("http://gregor-wagner.com/?p=79"), conducted by a PhD student at the University of California, showed that Chrome chokes after opening 70 tabs and freezes after 150, while Firefox continues to operate without problems.

> To do this he used a script that opens 150 of the most popular websites in a browser instance automatically. One page is opened in a new tab every 1.5 seconds. On the latest Firefox nightly build that process takes roughly 6 minutes and 14 seconds. On Chrome, it’s a totally different story with the time escalating to 28 minutes and 55 seconds. That’s well over 4x slower than Firefox.

**For more info:**

[http://www.geek.com/articles/news/firefox-easily-outperforms-chrome-with-many-tabs-open-201108](http://www.geek.com/articles/news/firefox-easily-outperforms-chrome-with-many-tabs-open-201108)


.

---

### Post by unknownPoster on 2011-08-05
> **lovinglinux said:**
> .

Chrome already is a multi-process application, which is one of the reasons why Chrome outperforms other browsers in benchmarks. However a recent [experiment]("http://gregor-wagner.com/?p=79"), conducted by a PhD student at the University of California, showed that Chrome chokes after opening 70 tabs and freezes after 150, while Firefox continues to operate without problems.



I don't see how that's relevant. No one opens that many tabs in regular use. And even so, it's not surprising at all.

---

### Post by RiceMonster on 2011-08-05
I'll keep this in mind next time I want to open 150+ tabs.

---

### Post by 3Miro on 2011-08-05
I will try this tonight and let you know about the results. BTW did they try this under Windows or Linux, you can hardly impress the Linux kernel with 150 threads, windows on the other hand ....

---

### Post by NightwishFan on 2011-08-05
Running the bench now with Epiphany 3.0. I am assuming it would have done great except that i have like 20 instances of gtk gnash open as well.

At least i was smart enough to isolate it to a cgroup.

Edit: Stats when finished

Pages Opened: 15
Tasks: 171 total,  23 running
load average: 11.67, 11.38, 8.46
Ram: 1998/2988
Swap: 305/3336

Took around 20 mins. I am going to try again with gtk-gnash uninstalled.

---

### Post by fdrake on 2011-08-05
finally i don't have to do kill firefox for one plugin gone crazy. that's an awesome idea. Does that mean you can actually run a plugin from the command line and somehow be able to change the behavior, just like a program?

---

### Post by lovinglinux on 2011-08-05
> **3Miro said:**
> I will try this tonight and let you know about the results. BTW did they try this under Windows or Linux, you can hardly impress the Linux kernel with 150 threads, windows on the other hand ....

MacBook Pro

> **fdrake said:**
> finally i don't have to do kill firefox for one plugin gone crazy. that's an awesome idea. Does that mean you can actually run a plugin from the command line and somehow be able to change the behavior, just like a program?

The plugin separation is already available since the early versions of Firefox 3.6, which was released more than a year ago.

I don't think you can access it via command-line. Flash is not exactly a standalone program, but a shared object. It loads via firefox's *plugin-container* process. I have no idea how it works.

> **unknownPoster said:**
> I don't see how that's relevant. No one opens that many tabs in regular use. And even so, it's not surprising at all.

I never open more than a dozen tabs. However I have seen people with more than 90 tabs open and since Tab groups in Firefox 6 doesn't load the tabs until you click the group, which improves Firefox startup considerably, you might see people using more and more tabs simultaneously.

---

### Post by NightwishFan on 2011-08-05
I think the vast majority of users will use under 30 tabs so the separation should be to their advantage. Plus it will likely help stop tabs lagging when I open another tab in the background.

---

### Post by lovinglinux on 2011-08-05
> **NightwishFan said:**
> I think the vast majority of users will use under 30 tabs so the separation should be to their advantage. Plus it will likely help stop tabs lagging when I open another tab in the background.

Indeed: [https://testpilot.mozillalabs.com/testcases/tab-open-close/results.html](https://testpilot.mozillalabs.com/testcases/tab-open-close/results.html)

---

### Post by del_diablo on 2011-08-05
A browser is a psuedo background application, and because of that it never start hogging resources like some game.
Separating some threads is good, but multithreading for tabs? Really really bad.

---

### Post by 3Miro on 2011-08-06
I just tried opening 200+ tabs in Chromium 13. No choke, no slow down, everything worked just fine. The web-pages were not heavy, but I have flash-block installed anyway as even two flash windows tend to choke.

---

### Post by jerenept on 2011-08-06
> **RiceMonster said:**
> I'll keep this in mind next time I want to open 150+ tabs.

[Okay.]("http://tvtropes.org/")

---

### Post by Thewhistlingwind on 2011-08-06
> **jerenept said:**
> [Okay.]("http://tvtropes.org/")

It's not THAT addicting. Jeez.

---

### Post by krapp on 2011-08-07
At most I have 10 tabs open. Usually just 3 or 4. Am I doing something wrong?

---

### Post by lovinglinux on 2011-08-07
> **krapp said:**
> At most I have 10 tabs open. Usually just 3 or 4. Am I doing something wrong?

I do the same. I usually close tabs as soon as I finish reading them. I keep some sites/services like Gmail and GReader as App tabs, the most frequently used sites in Speed Dial and some sites I don't access much frequently on Tab Groups.

---

