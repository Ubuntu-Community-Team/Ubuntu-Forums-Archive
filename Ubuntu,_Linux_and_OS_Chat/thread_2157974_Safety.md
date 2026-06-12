---
title: "Safety"
date: 2013-06-27
forum: Ubuntu, Linux and OS Chat
---

### Post by coldbrains on 2013-06-27
Is Ubuntu (and Linux in general) still considered safer than Windows or Mac?

---

### Post by MadmanRB on 2013-06-27
For the most part yes, though I say Mac and linux are on par with eachother.
Windows is still the odd man out with the security stuff, sure its gotten better but it still has everything under the same roof.
I would be more worried about browsers right now, and browsing habits.

---

### Post by snowpine on 2013-06-27
The most important factor is the user. 

For example, a Windows security expert who knows nothing about Linux will probably be safer on Windows.

---

### Post by Cheesemill on 2013-06-27
Also the OS you use isn't really the biggest factor in security.

Things like the browser you use, whether you use Java (and other runtimes) or not and user habits are a much bigger contribution to security, good or bad.

---

### Post by 3rdalbum on 2013-06-29
> **MadmanRB said:**
> For the most part yes, though I say Mac and linux are on par with eachother.

I would say that Linux is the most secure of those three. Windows is next, and Mac OS X trails behind.

Back when Apple's engineers were developing Mac OS X 10.0, they didn't really care too much about working within the Unix security system. They just wanted everything to work. Now, those decisions are coming back to bite Apple, as the system is badly designed from a security standpoint, and it can't be fixed without breaking most programs.

Maybe Mac OS XI will finally take security seriously.

---

### Post by buzzingrobot on 2013-06-29
> **coldbrains said:**
> Is Ubuntu (and Linux in general) still considered safer than Windows or Mac?

Frankly, I think if you use Windows 7 or 8, understand how its security works, don't deliberately disable part of it for convenience, don't use old versions of apps, and understand the risks of using the net, you'll be as safe on Windows as anywhere.

To oversimplify, Windows security problems began when it began to include network tools -- LAN tools -- that assumed everyone on the network was well-behaved. Then, when similar technology was bolted on in the mid-1990's after MS decided to jump on the internet bandwagon, the security problems skyrocketed.

Today, the issue is more the ubiquity of Windows and the presence of users who do something they should not and leave themselves open to exploitation. The odds of a bad actor running a bot network finding Windows machines with compromised security is much, much higher than finding compromised Mac and Linux machines.

---

### Post by buzzingrobot on 2013-06-29
> **3rdalbum said:**
> I would say that Linux is the most secure of those three. Windows is next, and Mac OS X trails behind...Maybe Mac OS XI will finally take security seriously.

Evidence? (Not hearsay.)

I've used OS X since the first week of the first release. I strongly disagree with your assertion.

---

### Post by MadmanRB on 2013-06-29
Yes i find it odd too, after all Windows had its share of security bugs and has slowly caught up to us in linuix land.
But OSX insecure, never heard of it.

---

### Post by 3rdalbum on 2013-06-30
> **buzzingrobot said:**
> Evidence? (Not hearsay.)

I've used OS X since the first week of the first release. I strongly disagree with your assertion.

Just because you haven't been actually hit by a virus, doesn't make OS X secure. I never had a virus when I used Windows XP, either. I used classic Mac OS for years without getting a virus, doesn't mean it's secure.

On my old Mac I had a link to a great site that explained it all... I can't find it now. OS X does have a history of terribly amateur security flaws:

1. Any program running as the user can send Apple Events to programs running as root, without question.
2. One such program ran setuid root on Mac OS X, and actually accepted the "run terminal command" Apple Event from any unprivileged program. Result: An easy three-line Applescript, run as user or even guest, could erase your hard drive without prompting for your password or even displaying an "Are you sure?" dialog box. It was two major versions of OS X before that one was patched, and it was only patched by making that setuid program ignore any "run terminal command" events NOT by restricting the ability of non-root programs to send Apple Events to root programs.
3. Early versions of Safari had a setting, turned on by default, that would automatically run shell scripts inside compressed archives as soon as you downloaded them.
4. In early versions of OS X, if you ran a program that ran as root, and then started another program from the Apple menu, that second program would also run as root.
5. Permissions sometimes get messed up on OS X (NEVER on any real Unix or Linux system), and Apple ships a program to correct the permissions whenever it happens. It shows that the higher levels of OS X are working around the security system at times, instead of working with it.

These are the programmers you trust to keep your computer safe? You're a braver man than I.

---

