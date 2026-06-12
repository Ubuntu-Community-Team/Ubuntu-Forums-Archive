---
title: "Indicator Applet no longer visible"
date: 2014-04-13
forum: Ubuntu Development Version
---

### Post by pfeiffep on 2014-04-13
When booting the applet is visible, after login to either flash back (compiz or metacity) desktop environments it is not present. If I choose Ubuntu desktop  environment (unity) after login it is present.
> pfeiffep@Pete-dell:~$ uname -a
Linux Pete-dell 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux
pfeiffep@Pete-dell:~$ 
pfeiffep@Pete-dell:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty
pfeiffep@Pete-dell:~$ 


I'm not certain how to relaunch the applet nor how to trouble shoot.

Went to startup applications in order to discover the command and issued command below - also included are the returned results
> pfeiffep@Pete-dell:~$  /usr/lib/i386-linux-gnu/indicator-application/indicator-application-service


(process:10584): indicator-application-service-WARNING **: Unable to get watcher name 'org.kde.StatusNotifierWatcher'


(process:10584): indicator-application-service-WARNING **: Name Lost
pfeiffep@Pete-dell:~$ 


Problem exists only on 32 bit - 64 bit machine seems normal

Found this[ page]("https://launchpad.net/ubuntu/+source/cairo-dock-plug-ins/+changelog") seemingly indicating this was a problem and an earlier version was decided

---

### Post by kansasnoob on 2014-04-13
Have you tried just adding [the applet]("http://ubuntuforums.org/showthread.php?t=1966370&page=2&p=11900657#post11900657") back to the panel?

I haven't seen that here in ages. I typically use 'indicator-applet' instead of 'indicator-applet-complete' but you can see in this screenshot that I've added a new top panel and then added the "complete" applet:

[ATTACH=CONFIG]252034[/ATTACH]

---

### Post by pfeiffep on 2014-04-14
> **kansasnoob said:**
> Have you tried just adding [the applet]("http://ubuntuforums.org/showthread.php?t=1966370&page=2&p=11900657#post11900657") back to the panel?

I haven't seen that here in ages. I typically use 'indicator-applet' instead of 'indicator-applet-complete' but you can see in this screenshot that I've added a new top panel and then added the "complete" applet:



Thank you for your assistance.

I can add the clock with no problems, but adding the indicator-applet-complete results in immediate failure. I like the network icon showing wifi strength.
[ATTACH=CONFIG]252050[/ATTACH]
I like the network icon showing wifi strength that's included in 'complete'. Also I don't seem to find just indicator applet. I also tried to add 'complete to bottom and it worked....go figure

---

### Post by kansasnoob on 2014-04-14
Everything is fine here in a flashback w/metacity session but in flashback w/compiz I get this:

[ATTACH=CONFIG]252053[/ATTACH]

I personally wish they'd just drop the flashback w/compiz session altogether!

---

### Post by pfeiffep on 2014-04-14
> **kansasnoob said:**
> Everything is fine here in a flashback w/metacity session but in flashback w/compiz I get this:

I personally wish they'd just drop the flashback w/compiz session altogether!

Thanks again - I changed the number of worspaces to 1 and then rempved the workspace switcher from bottom panel  giving me a bit more space on the bottom bar.

I think I'll not mark this as solved quite yet.

---

### Post by kansasnoob on 2014-04-14
Once Trusty iso testing is out of the way I'll likely file a "wishlist" bug report requesting that the "flashback w/compiz session" be disabled altogether because no-one truly works on it!

Flashback w/metacity is needed for Edubuntu's LTSP installs but the compiz sessions only serve to complicate and break things!!!!!

---

### Post by pfeiffep on 2014-04-14
> **kansasnoob said:**
> Once Trusty iso testing is out of the way I'll likely file a "wishlist" bug report requesting that the "flashback w/compiz session" be disabled altogether because no-one truly works on it!

Flashback w/metacity is needed for Edubuntu's LTSP installs but the compiz sessions only serve to complicate and break things!!!!!
Mia culpa ... :redface:
I had changed the properties of the top panel to a solid color and then made it transparent and I didn't "connect the dots" correctly. Upon changing back to "use system theme" the indocator applet complete works perfectly.

Maybe this is a very minor bug .... I'll play around with it a bit more. I suppose I can mark this solved in the mean time.

---

### Post by pfeiffep on 2014-04-14
Interesting - my HP desktop (64 bit) has about 90% transparency and it works just fine! 

I'll play around with both and report back on this post.

Any Transparency on my Dell installation (32 bit) causes the failure ... I'm suspecting this is caused in part by the slow processor on this laptop

---

### Post by Ravi Gadhia on 2014-05-05
> **pfeiffep said:**
> Mia culpa ... :redface:
I had changed the properties of the top panel to a solid color and then made it transparent and I didn't "connect the dots" correctly. Upon changing back to "use system theme" the indocator applet complete works perfectly.

Maybe this is a very minor bug .... I'll play around with it a bit more. I suppose I can mark this solved in the mean time.


Hi I had same problem and fixed it by change color to "use systme theme" and it's work, Thank you :)

---

