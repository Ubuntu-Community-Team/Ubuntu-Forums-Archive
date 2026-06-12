---
title: "How I &quot;Fixed&quot; my ubuntu installation"
date: 2010-09-21
forum: The Cafe
---

### Post by Fifthmarch on 2010-09-21
I spent the last 4 days this way:

[LIST=1]
[*]Started by deleting an application.
[*]The application deleted a few others with it, and my desktop didn't load.
[*]Tried installing from a backup USB, but grub didn't load. Wrestled with grub for a day.
[*]Gave up and did a fresh installation.
[*]Again, the same application was there - deleted it. This time, I reinstalled the other applications that were deleted along with it. My initial problem was still right there, staring at me.
[*]Found a post on ubuntu forums that suggested a workaround. With a minor config change to the original app I deleted FOUR.DAYS.AGO.
[*]Problem solved five minutes later. System working perfectly.
[/LIST]
Just how often does this happen in Ubuntu? As you can guess, I'm a newbie!

---

### Post by CharlesA on 2010-09-21
I'm guessing that the problems were due to it removing dependencies that other packages required.

How did you remove it?

---

### Post by Tibuda on 2010-09-21
what app are you trying to remove?

---

### Post by MooPi on 2010-09-21
That would be my question as well. What program was so offensive that you went out of your way to delete it ?

---

### Post by chriswyatt on 2010-09-21
Always check which packages are being removed. ;)

If you installed something and then later decided to remove it, your package manager shouldn't remove anything more than what you installed.

Sounds like you accidentally removed an important dependency.

Were you using Ubuntu Software Centre or Synaptic?

---

### Post by Fifthmarch on 2010-09-21
I removed pulseaudio because it was messing with my mic. When it went out, it took gimp, blender, ubuntu-desktop and around 10 other applications with it. 

What does pulseaudio have to do with blender?

@Chriswyatt - I check EVERY package that's being installed/removed now. And I used synaptic. I don't really like the Software center.

---

### Post by kaldor on 2010-09-21
It's stuff like this that make me use other distros over Ubuntu.

Same thing with removing firefox.

---

### Post by CharlesA on 2010-09-21
> **Fifthmarch said:**
> I removed pulseaudio because it was messing with my mic. When it went out, it took gimp, blender, ubuntu-desktop and around 10 other applications with it. 

What does pulseaudio have to do with blender?

@Chriswyatt - I check EVERY package that's being installed/removed now. And I used synaptic. I don't really like the Software center.

Pulseaudio is a dependency of a bunch of packages. 

Check [here]("http://art.ubuntuforums.org/showthread.php?t=1313253") for some info on how to remove it safely.

---

