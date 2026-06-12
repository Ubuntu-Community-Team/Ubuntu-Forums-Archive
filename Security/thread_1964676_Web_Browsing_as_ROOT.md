---
title: "Web Browsing as ROOT"
date: 2012-04-24
forum: Security
---

### Post by robot_chicken_parm on 2012-04-24
I would like this thread to be as accurate and complete as possible.  If I make a mistake or leave out something, please post it.

I have rarely if ever seen the specific reasons precisely why one shouldn't surf the web as root, and what can happen to you and how it might happen, together in one place.  I think we can agree that web browsing with privileges escalated to superuser/root is bad.  Putting your cell phone in the microwave bad.  :)

Perhaps it should be thought of like driving in the wrong direction down the middle of a six-lane expressway.  I think we could agree there are nice odds you will collide with one of those cars.  The information superhighway is chock full of malware, bugs, malicious scripts and goodies, and vulnerabilities.  And web browsers are complex assemblies of software, with bugs and
vulnerabilities of their own.  Browsers are always offering updates to plug up security leaks, and there are people out there with malicious intent in their hearts looking for a known exploit for a published vulnerability.  There are layers of defense keeping your computer from being exploited or completely crapping out, but if you are running as root you don't have any protection.  Sooner or later, possibly sooner, you are going to crash your car into oncoming traffic.  

You don't even need to be running as root for a malicious hacker to get you in his clutches, but if you are it is his dream come true.  Especially vulnerable and potentially malicious are the "apps" for Google Chrome and Chrome OS.  Google specifically makes it difficult to run Chrome or Chromium as root for this reason.  The risks of running as root can apply to other programs as well.

In most instances there is NO reason to browse as root, or to be logged into your whole system as root, since Linux makes easily escalating user privileges for a task a cinch.  THE only reason I can think of why one might be running a web browser as root might be if they were using a penetration testing distro like BackTrack, BackBox, Pentoo or Matriux and so MUST be logged in as root, and in this case, there is likely a way to deescalate one's privilege level for an individual process(COULD SOMEONE POST WHETHER THERE IS A WAY TO DO THIS?).  

I have tried to be comprehensive on this matter.  Play safe  :P

---

### Post by Dangertux on 2012-04-24
I think to an extent this is one of those "No really?" posts. However, I think there are also some errors.

First -- Running as root has absolutely zero effect in terms of vulnerability, rather in depth of compromise. An application or system is either vulnerable or it isn't. That is not to say running a vulnerable service as root is a smart idea by any means. 

Second, there are some pretty sweeping assumptions about Chrome in there. I think a few sources on that one might help it go down easier.

As far as running as root in BT or other distros, sudo works in both directions, not just for escalation. I would suggest reading the man pages you might find exactly what you want in there.

It also might be noteworthy to point out that for the most common desktop user, even running as their standard user in unprivileged mode (not gksu kdesu etc..) A compromised browser is devestating. Let's be realistic, do you keep your personal files in your ~/ or in /opt? So truthfully if your browser becomes compromised you would lose positive control over the vast majority of your personal data. This is where a more granular permissions model comes into play, much like that offered with Apparmor or SELinux.


Hope this helps.

---

### Post by Hungry Man on 2012-04-24
If you're running Chrome as root on a default Ubuntu you are essentially disabling the sandbox. Chrome uses chroot to keep the browser confined, chroot is easily bypassed (on a default Ubuntu) once root is achieved. I don't know what you mean when you say that Chrome is more dangerous or that the apps are. There's just as much danger as running Chrome as root as there is any other application - they all have vulnerabilities, it's just a matter of the hacker picking one.

---

### Post by robot_chicken_parm on 2012-04-25
Thanks DangerTux and Hungry Man.  If I make a mistake about something, as I had in my initial post, I am glad that someone let me know.

I know that everything in my initial post, I've read in other places, so I will do my best to cite the URLs.  That does not mean that I may not have been mistaken in what I said.

It is my hope that when this thread is done, myself and others who may stumble onto it through searching a question will have the correct information and that the facts and fiction about this can be separated.

---

