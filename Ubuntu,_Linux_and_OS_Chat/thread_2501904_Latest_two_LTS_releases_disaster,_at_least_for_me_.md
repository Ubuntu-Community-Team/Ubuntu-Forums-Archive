---
title: "Latest two LTS releases disaster, at least for me on 2 Mac Airs"
date: 2024-10-25
forum: Ubuntu, Linux and OS Chat
---

### Post by maestrobwh1 on 2024-10-25
I have been using ubuntu since 2006.  There have always been glitches with hardware but generally had been solvable on most of the hardware I had on Acer or IMB thinkpads. 

16.04, 18.04 and 20.04 were rock solid on several Intel based Macs.  Everything worked except perhaps the WiFi but that was solvable installing broadcom-sta-dkms.

Machines suspended, hibernated, all controls for backlights and keyboard backlights worked well.

Along came 22.04.  Now, on several machines, suspend no longer required a password to wake... went down that rabbit hole for a week and the broadcom driver on two machines would have the WiFi connect but there was no internet.  Did research from time to time, never could fix it.  Then along came 24.04 and not only were those same issues still there, but also the laptop would just suspend randomly if I plugged it in, and attempting to wake it required opening and closing the lid several times and it was like rolling dice.  That certainly won't work.  Then on top of all of that the internet stopped working AGAIN... it would connect to the wifi but there was some issue with /etc/resolv.conf, and I "fixed" the symlink but alas, once the internet "broke" I could never get it back even after a reboot no matter what suggestions for forums or help I researched.

So I re-imaged my drive with a 20.04 backup I had and sure, it is not as pretty, but everything just works again... every single time.  Using Ubuntu Pro and aside from being "barked" at during an apt-update about my kernel being outdated at 5.15, I guess I am good for another half decade.

Perhaps it is just because the newer versions don't particularly support hardware well that is 7 years old or older now.  These things even happened to a "fresh" install after crashed upgrades.

---

### Post by ian-weisser on 2024-10-25
> **maestrobwh1 said:**
> Perhaps it is just because the newer versions don't particularly support hardware well that is 7 years old or older now.  These things even happened to a "fresh" install after crashed upgrades.

No, it's usually because users with that hardware are not reporting the bugs.
Testing and reporting bugs is the community's role in this ecosystem.

On the developers' systems, those releases work properly. That's why it's so important for folks with other hardware to test, diagnose, and report those bugs.

---

### Post by maestrobwh1 on 2024-10-27
I will do my best, as I have time to do so.  Thank you for the reminder, since I have been "around a while" and should report the bug.  This one item, I have sort of resolved, and I am putting it here firstly to help anyone who finds this and has a similar "no screen lock" on suspend.  I also put this on another thread on a different section of the forum, as this is more or less for chat and not help:

The "fix" or workaround actually is here to get the screen to lock during (seems to be after wake from) suspend:

[https://askubuntu.com/questions/1231910/screen-does-not-lock-on-suspend](https://askubuntu.com/questions/1231910/screen-does-not-lock-on-suspend)

See the above if anyone is needing a fix to a similar issue.

The fix is to add a service that runs this script (again, see link to get the details):

```
#!/bin/sh
export XDG_SEAT_PATH="/org/freedesktop/DisplayManager/Seat0"
dm-tool lock
```

So now after adding a service that activates this script (I put the script named suspend-lock-fix.sh in /usr/bin/local so now when I close my lid, the computer suspends (that never stopped working as long as i did not try to manually lock the screen and if I did, the computer would not suspend), and when I wake it, the desktop does flash for a second, then the lock screen shows up.  

Oddly, this similar effect happens with a fresh install of Ubuntu Budgie on a different partition and I thought it was odd that the suspended desktop would show for a second, if that, then the lock screen would show up, and that was not my doing.  It is just how it seems to work after a fresh install.

**Is this something I should file a bug for in either case?**

Now I just have to figure out why BOTH desktops on different partitions have the computer randomly suspend when connected to external power, and the worst result is that it is really hard to wake up and even when the power button is held down for a minute, it doesn't turn off because input for the keyboard and trackpad seem not to work so the close-wait-open-close-wait-open for a few cycles gets things working again.  Very odd.  If I just close the lid when using the computer, it suspends and wakes easily.  it is only when the suspend occurs when I didn't do anything that should activate it.

That definitely is a bug and I am still trying to figure out how to retrieve the information as to where that is going awry.

---

### Post by maestrobwh1 on 2024-10-29
Did a chroot from a different Ubuntu partition and based on some other random research, I did

```
apt install --reinstall ubuntu-desktop^
```

The ^ forced all related packages to be downloaded, installed and configured.  I removed the service in the above post.  The machine behaves appropriately now.

---

### Post by ne29914 on 2024-10-31
> **ian-weisser said:**
> No, it's usually because users with that hardware are not reporting the bugs.
Testing and reporting bugs is the community's role in this ecosystem.

On the developers' systems, those releases work properly. That's why it's so important for folks with other hardware to test, diagnose, and report those bugs.

Nope. Reporting a bug results in it staying open for 3 months and then self-deleting.
Been there, done that.

---

### Post by ian-weisser on 2024-11-01
Bugs marked 'Invalid' are self-deleting. Others remain open until manually closed.

An invalid bug usually means more information is needed.
Typically, that means the developer asked a question and was awaiting an answer.
Or there is some other issue with the report. Bug reports don't mark themselves invalid. A human triager does that.

I know reporting bugs properly isn't easy. Been there, done that too.
I've also done bug triaging, reviewing a lot of garbage bugs, fire-and-forget bugs, bugs that don't describe how to reproduce the issue, bugs that are support questions, etc, and helping to turn them into useful bug reports that a developer can use to find the whack code and fix it.
It's worthwhile to invest the time and effort to do it right. To get past the learning curve. Because then the bug gets fixed. For everybody.

---

### Post by ne29914 on 2024-11-01
It wasn't "invalid", I even had ping-pong with the developers, supplying more information.
Then it went to "open" (or something like that, don't remember the exact word, could also have been "valid").
After that it timed out automatically after three months. I'm not going to spend that kind of effort again.
It was apparently uninteresting (laptop brightness control not working. WGAS).
My option was to stay with 20.04 forever, which is my solution now.

---

