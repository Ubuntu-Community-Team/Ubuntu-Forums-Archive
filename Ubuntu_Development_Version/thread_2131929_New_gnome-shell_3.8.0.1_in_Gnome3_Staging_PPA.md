---
title: "New gnome-shell_3.8.0.1 in Gnome3 Staging PPA"
date: 2013-04-03
forum: Ubuntu Development Version
---

### Post by Harry33 on 2013-04-03
There is a new gnome-shell build in Gnome3 Staging PPA (3.8.0.1).
This is built against libmoz-17.0-0 (and not libmoz185-1.0 anymore).
You need to upgrade packages gjs and libgjsc0 to versions 1.36.0+js17 at the same time.
The reason behind this is the new JavaScript engine Spider Monkey.

---

### Post by VinDSL on 2013-04-03
> **Harry33 said:**
> You need to upgrade packages gjs and libgjsc0 to versions 1.36.0+js17 at the same time.
That should be libgjs0c, yes?  ;)

---

### Post by sgage on 2013-04-03
It seems that 3.8.0.1 has already moved from staging to the main gnome3 ppa.

---

### Post by sgage on 2013-04-03
A couple of things re: 3.8.0.1:

1) There seems to be no way to shut down/restart from the status menu.

2) Backup (deja-dup) is missing from Settings.

---

### Post by Harry33 on 2013-04-03
> **sgage said:**
> It seems that 3.8.0.1 has already moved from staging to the main gnome3 ppa.

Yes the version is 3.8.0.1, but:
- in Gnome3 PPA the gnome-shell is built agains older libmoz185-1.0
- in Gnome3 Staging PPA the gnome-shell is built against newer libmoz-17.0-0

---

### Post by Harry33 on 2013-04-03
> **VinDSL said:**
> That should be libgjs0c, yes?  ;)

That is correct.
Thank You VinDSL.

Which one do you use, gnome-shell from Gnome3 PPA or Gnome3 Staging PPA?
If both are enabled, the Gnome3 Staging one is higher and choosen.

---

### Post by sgage on 2013-04-03
> **Harry33 said:**
> Yes the version is 3.8.0.1, but:
- in Gnome3 PPA the gnome-shell is built agains older libmoz185-1.0
- in Gnome3 Staging PPA the gnome-shell is built against newer libmoz-17.0-0

Yes, I see that now. In any case, it seems to be working fine other than the two items I mentioned in a previous post.

---

### Post by Harry33 on 2013-04-03
> **sgage said:**
> A couple of things re: 3.8.0.1:

1) There seems to be no way to shut down/restart from the status menu.

2) Backup (deja-dup) is missing from Settings.

I don't have deja-dup, but
the power off and restart options work normally here.

---

### Post by sgage on 2013-04-03
> **Harry33 said:**
> I don't have deja-dup, but
the power off and restart options work normally here.

I had a conflict with an obsolete extension - I removed it and it's working normally now.

---

### Post by VinDSL on 2013-04-03
> **Harry33 said:**
> Which one do you use, gnome-shell from Gnome3 PPA or Gnome3 Staging PPA?
Staging... ;)

Seems to be working fine!

---

### Post by Roasted on 2013-04-03
I'm running the regular Gnome3 PPA. I ran into a new issue which has me thinking about rolling back to 3.6, at least on my work system.

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1164086](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1164086)

I also have yet to see a battery indicator on any laptop running Ubuntu GNOME 13.04 that I've installed to (total of about 5 laptops of different models).

There's also a 2nd bug that I ran into on my home install when I was trying to add a printer.

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1163674](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1163674)

Other than that I'm loving 3.8. :guitar:

---

### Post by VinDSL on 2013-04-03
> **Harry33 said:**
> Which one do you use, gnome-shell from Gnome3 PPA or Gnome3 Staging PPA?

> **VinDSL said:**
> Staging... ;)

Seems to be working fine!
Er...  I stand corrected.

Just checked :oops:

Ricotz/Testing...

```
vindsl@Zuul:~$ apt-cache policy gnome-shell
gnome-shell:
  Installed: 3.8.0.1+git20130329.29e89491-0ubuntu1~13.04~ricotz0
  Candidate: 3.8.0.1+git20130329.29e89491-0ubuntu1~13.04~ricotz0
  Version table:
 *** 3.8.0.1+git20130329.29e89491-0ubuntu1~13.04~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
     3.8.0.1-0ubuntu1+js17~raring2 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main i386 Packages
     3.8.0.1-0ubuntu1~raring1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ raring/main i386 Packages
     3.6.3.1-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ raring/universe i386 Packages
        500 http://samaritan.ucmerced.edu/ubuntu/ raring/universe i386 Packages
     3.6.2-0ubuntu0.2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe i386 Packages


vindsl@Zuul:~$ apt-cache policy gjs 
gjs:
  Installed: 1.36.0+js17-0ubuntu1~13.04~ricotz0
  Candidate: 1.36.0+js17-0ubuntu1~13.04~ricotz0
  Version table:
 *** 1.36.0+js17-0ubuntu1~13.04~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ raring/main i386 Packages
        500 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
     1.36.0-0ubuntu1~raring1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ raring/main i386 Packages
     1.34.0-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ raring/universe i386 Packages
        500 http://samaritan.ucmerced.edu/ubuntu/ raring/universe i386 Packages


vindsl@Zuul:~$ apt-cache policy libgjs0c
libgjs0c:
  Installed: 1.36.0+js17-0ubuntu1~13.04~ricotz0
  Candidate: 1.36.0+js17-0ubuntu1~13.04~ricotz0
  Version table:
 *** 1.36.0+js17-0ubuntu1~13.04~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ raring/main i386 Packages
        500 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
     1.36.0-0ubuntu1~raring1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ raring/main i386 Packages
     1.34.0-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ raring/universe i386 Packages
        500 http://samaritan.ucmerced.edu/ubuntu/ raring/universe i386 Packages
vindsl@Zuul:~$ 

```

Nobody can be perfect all the time!  :D

---

### Post by Roasted on 2013-04-04
Anybody on 13.04/Gnome 3.8/Gnome3 PPA experiencing the GUI crash when you open Nautilus?

To replicate:
1) Close all windows (even if it's not a fresh install)
2) Open Nautilus (system should crash and Gnome will recover)
3) Once Gnome Shell is back, open Nautilus a 2nd time. This time it will hard lock requiring a forced poweroff.

I noticed even if I fire up gedit, THEN Nautilus, it'll be fine. There's something about opening "Nautilus" with NO other windows open that is causing my instances to tank hard.

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1164086](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1164086)

---

### Post by ronacc on 2013-04-04
yes I have the same bug , I added myself to your bug .

---

### Post by Stinger on 2013-04-04
@ Roasted
I have the same bug too, reported a new bug with all my apport info and added it as duplicate of yours

---

### Post by mc4man on 2013-04-04
> **Roasted said:**
> Anybody on 13.04/Gnome 3.8/Gnome3 PPA experiencing the GUI crash when you open Nautilus?

To replicate:
1) Close all windows (even if it's not a fresh install)
2) Open Nautilus (system should crash and Gnome will recover)
3) Once Gnome Shell is back, open Nautilus a 2nd time. This time it will hard lock requiring a forced poweroff.

I noticed even if I fire up gedit, THEN Nautilus, it'll be fine. There's something about opening "Nautilus" with NO other windows open that is causing my instances to tank hard.

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1164086](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1164086)

Doesn't happen with latest nautilus git (3.8.0 release+), maybe they (gnome3 ppa) just need to get more current.
Edit- did a deb package build of 3.8.0, nautilus is fine

---

### Post by VinDSL on 2013-04-04
> **mc4man said:**
> Doesn't happen with latest nautilus git (3.8.0 release+), maybe they (gnome3 ppa) just need to get more current.
Edit- did a deb package build of 3.8.0, nautilus is fine
Dittos. Doesn't happen here either...

No crashes.  Opened n' closed 4-5 instances of Nautilus, several times.

Nothing remarkable occurred.

```
vindsl@Zuul:~$ apt-cache policy nautilus
**[COLOR="#B22222"]nautilus:[/COLOR]**
  **[COLOR="#0000CD"]Installed: 1:3.7.92-0ubuntu1~raring1[/COLOR]**
  Candidate: 1:3.7.92-0ubuntu1~raring1
  Version table:
 *** 1:3.7.92-0ubuntu1~raring1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
     1:3.6.3-0ubuntu13 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        500 http://samaritan.ucmerced.edu/ubuntu/ raring/main i386 Packages
     1:3.5.90.really.3.4.2-0ubuntu4.2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/main i386 Packages


vindsl@Zuul:~$ apt-cache policy gnome-shell
**[COLOR="#B22222"]gnome-shell:[/COLOR]**
  **[COLOR="#0000CD"]Installed: 3.8.0.1+git20130329.29e89491-0ubuntu1~13.04~ricotz0[/COLOR]**
  Candidate: 3.8.0.1+git20130329.29e89491-0ubuntu1~13.04~ricotz0
  Version table:
 *** 3.8.0.1+git20130329.29e89491-0ubuntu1~13.04~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
     3.8.0.1-0ubuntu1+js17~raring2 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main i386 Packages
     3.8.0.1-0ubuntu1~raring1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ raring/main i386 Packages
     3.6.3.1-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ raring/universe i386 Packages
        500 http://samaritan.ucmerced.edu/ubuntu/ raring/universe i386 Packages
     3.6.2-0ubuntu0.2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe i386 Packages
vindsl@Zuul:~$ 
```

---

### Post by Harry33 on 2013-04-05
> **mc4man said:**
> Doesn't happen with latest nautilus git (3.8.0 release+), maybe they (gnome3 ppa) just need to get more current.
Edit- did a deb package build of 3.8.0, nautilus is fine

In Gnome3 PPA there is a new nautilus (3.8.0) now.

---

### Post by Stinger on 2013-04-05
I can replicate this with GNOME Shell 3.8.0.1 from the Gnome3 ppa. Just crashed it three times in a row using the steps below.

[LIST=1]
[*]login to a fresh Gnome session with no other apps open
[*]open three instances of nautilus/files ( done with 'new window' every time )
[*]Now close all three windows
[*]Open nautilus/files again, Gnome-Shell will crash and recover again
[*]When GS has recovered, close the nautilus/files window and open it again, GS will crash permanently but you are still able to use nautilus without window borders  
[*]To shut your PC down you can use Ctrl-Alt-F1 to get the command line, login and do 'sudo poweroff'
[/LIST]
It's the same type of crash over and over again.

Edit.
The above  was done with nautilus 3.7.92, I just did an update and now have 'GNOME nautilus 3.8.0' but it makes no difference the problem remains the same.

---

### Post by mc4man on 2013-04-05
> **Stinger said:**
> 
The above  was done with nautilus 3.7.92, I just did an update and now have 'GNOME nautilus 3.8.0' but it makes no difference the problem remains the same.
You are correct - just noticed small but critical 'mistake' I & likely vin where doing. So while it takes at least 3 tries here with nautilus-3.8 Gs does crash as seen.
The mistake was enabling an alt. means to open nautilus other than the gnome-shell launcher/dock, whatever it's called. 
In that case the crash nevers happens, only happens if opened from the Gs launcher

---

### Post by Stinger on 2013-04-05
@ mc4man
It doesn't matter if I launch nautilus from the GS launcher or the app overview, GS crashes just the same.

---

### Post by Roasted on 2013-04-05
> **mc4man said:**
> Doesn't happen with latest nautilus git (3.8.0 release+), maybe they (gnome3 ppa) just need to get more current.
Edit- did a deb package build of 3.8.0, nautilus is fine

I actually read earlier that this is the issue. Evidently an older version of Nautilus, 3.6 I have to assume, was the cause of it.

I'm finding it a little frustrating that I can't get as much of a Gnome 3.8 experience as I had hoped for, even with Ubuntu GNOME 13.04. There seems to be some friction between updating certain (and currently broken) packages via the Gnome3 PPA due to Canonical doing their own with their own time frame. I'm halfway tempted to switch to Arch to check out a real Gnome 3.8 experience that isn't quite broken. 

On a positive note, besides all of that, I'm loving it. :)

---

### Post by mc4man on 2013-04-05
> **Stinger said:**
> @ mc4man
It doesn't matter if I launch nautilus from the GS launcher or the app overview, GS crashes just the same.

Not sure what vindsl was using but here was using plank, fairly sure that doesn't interest you

> **Roasted said:**
> I actually read earlier that this is the issue. Evidently an older version of Nautilus, 3.6 I have to assume, was the cause of it.



No, definitely a gnome-shell bug

On a side note noticed that keyboard bindings/custom commands are non-functional in Gs unless a window of any sorts is open, a bit of a flaw there. Clear ex. would be the run command dialog (default disabled, typically alt+F2). If enabled only works when a window is open. Or key to open activities overview, again default disabled, same deal.

---

### Post by Roasted on 2013-04-05
Turns out I actually have Nautilus 3.8 installed. But yeah, no matter what I do, all windows closed + opening Nautilus crashes it. Most of the time I get lucky and nothing crashes the first time. But so far, 100% of the time when I close Nautilus and open it a second time the UI tanks.

---

### Post by VinDSL on 2013-04-05
> **mc4man said:**
> You are correct - just noticed small but critical 'mistake' I & likely vin where doing.[...]
Well...

I still cannot get Nautilus to crash.  :(

I upgraded to 3.8.0...

```
vindsl@Zuul:~$ apt-cache policy nautilus
**[COLOR="Red"]nautilus[/COLOR]**:
  **[COLOR="#0000CD"]Installed: 1:3.8.0-0ubuntu1~raring[/COLOR]**
  Candidate: 1:3.8.0-0ubuntu1~raring
  Version table:
 *** 1:3.8.0-0ubuntu1~raring 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
     1:3.6.3-0ubuntu13 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        500 http://samaritan.ucmerced.edu/ubuntu/ raring/main i386 Packages
     1:3.5.90.really.3.4.2-0ubuntu4.2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/main i386 Packages
vindsl@Zuul:~$
```

Then I opened 10 instances of Nautilus, and closed them. Nothing.

So, I opened and closed 3 instances.  Then, opened and closed another 10 Nautilus windows.  Still nothing.

What am I doing "wrong"?

LoL!  :D

---

### Post by Stinger on 2013-04-05
> **VinDSL said:**
> Well...
I still cannot get Nautilus to crash.  :(

I upgraded to 3.8.0...

** i386 Packages**

What am I doing "wrong"?
I highlighted it for ya ;)

The bugreport is **Architecture: amd64**

I think that's why you are immune and can't have the bug.  ;)

---

### Post by VinDSL on 2013-04-06
> **Stinger said:**
> I highlighted it for ya ;)

The bugreport is **Architecture: amd64**

I think that's why you are immune and can't have the bug.  ;)
Good job, detective!  

I knew I was missing something...  ;)

---

### Post by bmbaker on 2013-04-06
hmmm i just tested this opening 5 times nautilus and closing them and also running nautilus as root 5 times and then again as usr and no issues at all!
i am running 64 bit :P

---

### Post by Stinger on 2013-04-06
@ bmbaker 
Lucky you then, I don't know what you are trying to tell though :???:, the bug is very much present as you can see on these bugreports, [GNOME Bugzilla &#8211; Bug 695030]("https://bugzilla.gnome.org/show_bug.cgi?id=695030"), [Launchpad Bug#1164086]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1164086") and [Bug# 1164766]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1164766")

Just had a thought, what if we are 'barking up the wrong tree' and the villain is not GS but nautilus ? Maybe the bug should be reported against nautilus instead ?
But I'm sure the Ubuntu-GNOME team already took this into consideration. ;)

---

