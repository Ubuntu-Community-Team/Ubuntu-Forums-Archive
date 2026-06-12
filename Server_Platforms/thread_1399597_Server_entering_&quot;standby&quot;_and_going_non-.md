---
title: "Server entering &quot;standby&quot; and going non-responsive"
date: 2010-02-05
forum: Server Platforms
---

### Post by wallacetheweasel on 2010-02-05
I have a strange and very frustrating problem with my Ubuntu Server 9.10 install on an old (2003/2004) eMachines m6807 laptop.

It goes into some sort of standby state in which it stops responding to ping/ssh, stops serving web interfaces, etc.  It wakes instantly on the press of a keyboard button - I had another computer ping it repeatedly and watched them time out, and they start responding instantly after a key press.

Rather oddly, the system clock is wrong after coming out of the standby state - it hasn't advanced since going into standby.

[COLOR="Gray"]A probably irrelevant detail: it also blanks the screen. I haven't checked whether the blanking of the screen coincides with going non-responsive: I could, if this is relevant.[/COLOR] -- I just noticed it in a non-responsive state with the screen not blanked, so I guess they're not coincident events.

This happens very soon after booting or waking it - maybe 10 minutes or so? I haven't timed it precisely.

It's also a relatively clean install of Ubuntu Server - a month old, with few packages installed and no custom editing of configuration files.

If you anyone can help me shed some light on what's going on and how I might fix it, it would be greatly appreciated! It's extraordinarily annoying, and renders the server pretty much useless.

Thanks in advance! :D

---

### Post by volkswagner on 2010-02-06
Check the BIOS to see if there is any power saving options enabled, if so set to disable or "full power/Max performance".

By default Ubuntu server does not have any power saving, just screen blanking.

---

### Post by wallacetheweasel on 2010-02-06
I've checked the BIOS, and there are no power saving settings listed.

I have a hypothesis that it might have to do with a buggy ACPI implementation.  After quite a bit of research online, there are a fair few pages with info about this laptop's poor ACPI implementation, at least on early BIOS revisions.  Most seem to suggest that things are resolved by flashing to a newer BIOS, so I flashed to the latest BIOS (0F08.P00), but it's still going into this standby mode.

[INDENT]
*These are the sites I'm referencing. Note that the m6805 and m6807 are identical except for their optical drive. And these sites are old, because it's an old laptop with little recent info.*

[http://s8.zetaboards.com/emachineupgraders/topic/42102/?author=14204](http://s8.zetaboards.com/emachineupgraders/topic/42102/?author=14204)
[http://skreak.com/m6805/](http://skreak.com/m6805/)
[http://web.archive.org/web/20050306101244/http://www.rmecc.com/~v2/em/](http://web.archive.org/web/20050306101244/http://www.rmecc.com/~v2/em/)
[http://greg.primate.net/m6805/index.html](http://greg.primate.net/m6805/index.html)
[/INDENT]


The ACPI idea is just a hypothesis - of course other ideas would be welcome.

If you could help me even figure out exactly what's going on... I don't even know precisely what logs to look through or what to look for.  Is it possible I might be able to prevent this by passing a kernel flag? Again, I wouldn't know precisely what to try.

---

### Post by tgalati4 on 2010-02-06
Running a server OS (which doesn't have ACPI hooks) on a laptop (which is designed for battery life) is an incompatible strategy.  

Just install the desktop OS and run your services.  You don't need to run the X session, you can simply boot to a terminal and all of your services will still be started.

---

### Post by wallacetheweasel on 2010-02-07
Hrm, that doesn't really make sense to me - though it's quite possible I simply don't understand. I don't know precisely what an ACPI hook is.

Many people run Ubuntu server on laptops without any problem.  It's going to be plugged into AC, so it's not like I need any power saving features - they all can and should be disabled.  As volkswagner said, Ubuntu Server Edition doesn't have any by default.

You're proposing that I install the desktop OS... and certainly, I could install the "ubuntu-desktop" package.  Is there a reason to believe that that would solve this problem?  If so, couldn't I just install/configure whatever is necessary to fix it without having all kinds of packages I don't want or need on my system?

Or would installing the "ubuntu-desktop" package not be good enough, and are you suggesting I reinstall the system from the Desktop CD? If that's the case, how would it differ from installing "ubuntu-desktop", and again, why can't I do it without the many many packages I don't need?

As I said at the top, I don't entirely understand your reasoning, and I'd be happy to understand it better!  But installing the desktop OS seems like a drastic solution, especially when I don't have a clear diagnosis of what exactly is going on.

The most promising solution to my mind is if someone could help me or at least point me in the right direction regarding (a) finding the problem in the logs and/or (b) whether it might be solved by the correct kernel flags.

---

### Post by tgalati4 on 2010-02-07
I would install a clean desktop LiveCD.  The installation process detects your hardware and loads the appropriate ACPI module.  It will override the hardware (BIOS) power settings.  

Without the ACPI module, the laptop's BIOS will control power management.  If you can't turn off power-saving features in the BIOS (because it is poorly written, or just crappy) then you have to rely on software ACPI control.  The server version doesn't have it.  Loading the ubuntu-desktop meta package on top of a clean server install may or may not fix the problem.  You can try it then examine:

lsmod

See if any ACPI modules get loaded.  Then go into the Preferences-->Power Management and make sure everything is turned off.

---

### Post by volkswagner on 2010-02-07
Can't you add to the grub entry something like acpi=off, to see if that is related?

---

