---
title: "&quot;LCD brightness&quot; stopped working: System76 2.3 / kernel 2.6.27-11.23"
date: 2009-01-09
forum: System76 Support
---

### Post by phyzome on 2009-01-09
This morning I performed the following relevant updates:

[LIST]
[*]linux-image-2.6.27-11-generic (2.6.27-11.22) to 2.6.27-11.23
[*]system76-driver (2.2.7) to 2.3.0
[/LIST]

The GNOME Power Manager Brightness Applet now shows a red circle-and-slash, with flyover text of "Cannot get laptop panel brightness". Additionally, the Fn+F8 and Fn+F9 keys no longer adjust the backlight.

What should I do to regain this functionality? Are there any logs you want to see?

---

### Post by thomasaaron on 2009-01-09
Hi, Phyzome.

That is a proposed kernel, which, of course, is supposed to provide fixes but isn't fully tested yet.

Chances are these problems will fix themselves as the kernel works its way towards being officially released.

Of course, that estimation of the problem is assuming that the functionality you mentioned is still present in previous kernels. Is it?

---

### Post by phyzome on 2009-01-09
> **thomasaaron said:**
> That is a proposed kernel, which, of course, is supposed to provide fixes but isn't fully tested yet.

Chances are these problems will fix themselves as the kernel works its way towards being officially released.

*sigh*

How long have I been running with Proposed selected? That could explain a lot of problems...

I'll do a backup and see what I can safely downgrade to supported versions.

---

### Post by sebos69 on 2009-01-09
Yep, same problem for me. I 've just reported a bug here:

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/315596](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/315596)

---

### Post by phyzome on 2009-01-13
I backed the kernel (and other packages) down out of Proposed. Here is what has happened as a result:

* Screen brightness works again
* Cheese is back to not working
* I have had one of those kernel-module freezes again -- I think those had stopped after moving to Proposed.

---

### Post by thomasaaron on 2009-01-14
Do...

sudo apt-get --reinstall install linux-backports-modules-intrepid

...and that should stop the freezes. If not, try re-enabling backports in your software sources and running updates. I don't think it's the backports that caused your problems. I think it was the proposed kernel.

---

### Post by Lee_Machine on 2009-01-16
So I installed the new recommended kernel update to 2.6.27-11 and it fixed not being able to change to screen brightness. Although it is buggy.

When using the applet pushing + or - makes the brightness change slow, too slow. Upon going all the way down the screen the applet gets the red slash like it should, but when you go back up the red slash stays there until you either log out then back in, or remove then add the applet. 

Another thing is when you click on the applet a second time the scroll bar is not directly under the white applet but far off the the left. Never off screen.

When using the hot keys the screen is slow to respond to the command and takes too large off leaps instead of too little.


Anyone else get these?

System:
Panp4n
Ubuntu 8.10 64bit
Kernel 2.6.27-11

---

### Post by phyzome on 2009-01-21
> **thomasaaron said:**
> Do...

sudo apt-get --reinstall install linux-backports-modules-intrepid

...and that should stop the freezes. If not, try re-enabling backports in your software sources and running updates. I don't think it's the backports that caused your problems. I think it was the proposed kernel.

Nope, it happened again. When it happens, I can't even shut down normally. Here are various symptoms:
[LIST]
[*]System monitor disappears from gnome panel
[*]"Networking disabled"
[*]Firefox and Pidgin hang on quit
[*]sudo hangs
[*]Audio does not work
[*]Shutdown hangs
[*]...and various other bits of the system hang, fail, or have otherwise stopped working.
[/LIST]

Ultimately, I have to use [Alt/Gr]+[SysRq]+[r,e,i,s,u,b] to restart.

This usually occurs upon resume after the laptop has been suspended for a long period of time, such as overnight.

Attached are some interesting bits (maybe even relevent!) retrieved from kern.log.

---

### Post by thomasaaron on 2009-01-21
I don't see anything in the logs that really helps me understand this.
If it's never shutting all the way down, there is a seriously hosed script/configuration/something somewhere.

I'm guessing that backing out of the -11 kernel left something behind.

As far as the suspend not resuming intermittently after long suspends, that may be a bug. I can try to test that here.

---

### Post by phyzome on 2009-01-21
> **thomasaaron said:**
> If it's never shutting all the way down, there is a seriously hosed script/configuration/something somewhere.

No, it *usually* shuts down just fine. The hang-on-shutdown only occurs with this post-resume nonsense.

> **thomasaaron said:**
> I'm guessing that backing out of the -11 kernel left something behind.

This was happening before I ever messed with Proposed, I'm sure of it.

> **thomasaaron said:**
> As far as the suspend not resuming intermittently after long suspends, that may be a bug. I can try to test that here.

To clarify: The laptop does resume, but something (probably at the level of kernel module) gets broken in the process of either suspending or resuming.

It also may have something to do with Network Manager.

---

### Post by thomasaaron on 2009-01-21
Thanks. I understand better now. I've actually had that happen to me before. However, I never suspend for *really* long periods of time.

Probably filing a bug report is the best way to go on this one, as a) it's going to be kind of figure out, b) it should probably be checked out on a number of our systems.

About how long do you think we have to keep it in suspend to duplicate the problem?

[http://launchpad.net/system76](http://launchpad.net/system76)

---

### Post by phyzome on 2009-01-21
> **thomasaaron said:**
> About how long do you think we have to keep it in suspend to duplicate the problem?

Not sure. I usually suspend mine around midnight and resume it at 8:00 AM.

I don't know *why* the length of time would matter, but it *seems* to.

At one point, I noticed that if I disabled software wireless and then the hardware radio before suspending, the problem occurred *much* less frequently.

Next time this happens, what logs should I retrieve?

---

### Post by thomasaaron on 2009-01-22
messages
syslog
daemon.log

---

