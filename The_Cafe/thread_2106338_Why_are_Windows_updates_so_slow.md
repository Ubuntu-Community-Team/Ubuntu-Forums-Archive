---
title: "Why are Windows updates so slow?"
date: 2013-01-18
forum: The Cafe
---

### Post by Paddy Landau on 2013-01-18
I have always wondered why Windows updates are so incredibly slow.

Windows XP was the worst — after installing, you had to update, reboot, update, reboot, update, reboot, … Even on a modern computer with broadband, it takes an entire day to install and fully update.

Windows 7 is much better, but it's still like treacle in comparison to Ubuntu, and that's even ignoring the fact that you don't have a package manager for the various non-Microsoft programs.

I am just curious. Why are Windows updates so time-consuming? Surely updates are just downloaded files and, for Windows, updates to the Registry? Or does Windows do all kinds of weird and wonderful stuff when updating?

---

### Post by CharlesA on 2013-01-18
Depends what the updates are for. I've had to download 1xx updates on a clean install of XP SP3 and if your internet is slow, that just blows. Install time takes a while too.

Win7 isn't as bad, but there are still a ton of updates for it.

As far as rebooting for updates, it's probably because Windows cannot update whatever file needs updating while the machine is running.

Ubuntu is the same way with various updates - they prompt you to reboot instead of stopping and restarting a service, or in order to boot into a new kernel.

---

### Post by deadflowr on 2013-01-18
I find Windows Updates run slow when it includes the malicious software removal tool, which executes a scan of the windows directory. Then if it finds anything out of the ordinary, it does its job of removing the problem(s).
This is released monthly as part of the super tuesday(or whatever day microsoft calls the bulk update day they use)update.
Most other updates go as normal, comparable to Ubuntu as far as speediness, but when that tool is installed, it feels like the system stopped.

---

### Post by drawkcab on 2013-01-19
I hate that windows doesn't warn you that it will take 20 or so minutes to process the updates before it shuts down.  Sometimes, when I need to leave the coffee shop for example, I'm stuck with a computer that I can't power down.  :(

---

### Post by Jakin on 2013-01-19
It's always a killer when you have a fresh install of any OS, the update hit you like a ton of bricks. The time it takes Windows to update though, is just rediculous, and not just as fresh install; everytime it updates.

---

### Post by HermanAB on 2013-01-19
The main reason is because MS is a cheapskate company. If MS would invest in better servers, then it will be faster, but they do not make money from updates.

---

### Post by Spike-X on 2013-01-19
"You can keep working while updates are being installed."

Okay, great!

*opens three programs, begins work for the day*

"Windows needs to restart in order to complete updates."

GAAAHHH!!!

---

### Post by Paddy Landau on 2013-01-19
> **HermanAB said:**
> If MS would invest in better servers, then it will be faster…

Well, even when the updates are already downloaded, it can take a long time. There is something about Windows updates that defies my attempts to understand them. The updates must be doing something significantly more than replacing files and making a couple of changes to the Registry.

I think that the sizes of typical Windows updates are larger than those of typical Linux updates, too. That makes sense, as the entirely of Ubuntu (which is a large distribution), including all the software that goes with it, plus all my data, fits into &#8532; the size of Windows installation, which has little additional software (not even Office) and barely any data.

The old XP style of updates (download, install, reboot; repeat about a dozen times) was madness; thank goodness MS has resolved that! If I recall correctly, Windows 7 needed "only" a couple of reboots for a fresh installation.

> **HermanAB said:**
> … but they do not make money from updates.They probably do, albeit indirectly. Without the updates, customers (especially business customers) would lose faith fast. The updates help to retain customers as repeat customers.

---

### Post by Spike-X on 2013-01-19
It just seems to take a lot longer to install anything on Windows generally. One time I had to install some printer software on my boss' computer, and in the time it took to do that I could have installed Ubuntu, realised I buggered up the partitioning, wiped it, and done it again.

---

### Post by kevinmchapman on 2013-01-19
I agree with all the irritations above. On the subject of size, I believe that Windows applications include all their libs, as opposed to Linux, which shares libs. That makes Windows applications larger, but more independent than Linux (which needs the entire OS to be updated when updating an application)

---

### Post by Paddy Landau on 2013-01-19
> **kevinmchapman said:**
> … Linux … needs the entire OS to be updated when updating an application
Doesn't an updated Linux application with new dependencies need only the relevant libraries to be updated?

---

### Post by kevinmchapman on 2013-01-19
> **Paddy Landau said:**
> Doesn't an updated Linux application with new dependencies need only the relevant libraries to be updated?

It does, but it doesn't take long to get messy, so it is not a long-term solution.

---

### Post by philinux on 2013-01-19
Windows is probably creating a restore point too. But in general I notice that small updates take ages to download. Then takes ages to install. This os win 7 too.

---

### Post by Paddy Landau on 2013-01-19
> **philinux said:**
> Windows is probably creating a restore point…
Sometimes it does, sometimes not; I do not know the reason why.

---

### Post by LADmaticCA on 2013-01-19
Microsoft's servers are definitely part of it. I work for a county government and when we run updates on a new or imaged Windows 7 install, the download takes much longer than you would expect for say 60MB of updates.

Whereas, I get 3 or 4MB/s when I do Ubuntu updates.

Good question OP. I've wondered about this myself.

---

### Post by pqwoerituytrueiwoq on 2013-01-19
> **drawkcab said:**
> I hate that windows doesn't warn you that it will take 20 or so minutes to process the updates before it shuts down.  Sometimes, when I need to leave the coffee shop for example, I'm stuck with a computer that I can't power down.  :(

[LIST]
[*]get to your next class
[*]auto shutdown due to low battery
[/LIST]
i think with XP MS is just trolling its users

---

### Post by Ender Shadow on 2013-01-19
That's why I disabled the automatic updates when I was using Windows.

---

