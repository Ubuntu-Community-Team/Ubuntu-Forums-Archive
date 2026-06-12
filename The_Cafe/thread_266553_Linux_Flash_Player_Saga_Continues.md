---
title: "Linux Flash Player Saga Continues"
date: 2006-09-27
forum: The Cafe
---

### Post by newbie2 on 2006-09-27
> Considering some of the vitriol dropped into the comments section of the Penguin.SWF blog post he wrote, Melanson may not be so glad he tried to answer the question.

He placed the blood-stained finger of blame on three things: libraries, libraries, and libraries:

While we have the plugin limping along on our development machines, there comes a point where we need to hand off builds to our QA team for testing. This is when we notice that the plugin works great on our dev boxes, but hardly or not at all on any other distributions.

Generally, the problem is libraries, libraries, libraries. For example, the player dynamically opens libasound.so to dig out the ALSA audio functions. I recently learned that the 'libasound.so' symlink is only available on systems with the right devel packages installed. The proper file to open is 'libasound.so.2'. Hopefully. Repeat for the rest of the dynamic library loads.
[http://www.webpronews.com/expertarticles/expertarticles/wpn-62-20060927LinuxFlashPlayerSagaContinues.html](http://www.webpronews.com/expertarticles/expertarticles/wpn-62-20060927LinuxFlashPlayerSagaContinues.html)
:rolleyes:

---

### Post by NoTiG on 2006-09-27
if they open sourced it i bet a port would be up within minutes

---

### Post by skymt on 2006-09-27
> **NoTiG said:**
> if they open sourced it i bet a port would be up within minutes

What, and lose control of the format? Lose their near-monopoly on Internet rich applications?

---

### Post by NoTiG on 2006-09-27
whats the OS alternative to flash anyway?

ps. i bet this guy is just stalling so he can keep his job

---

### Post by skymt on 2006-09-27
> **NoTiG said:**
> whats the OS alternative to flash anyway?

I'll assume you mean OSS, and link you to [Gnash](http://www.gnu.org/software/gnash/).

---

### Post by FISHERMAN on 2006-09-27
If it weren't for those stupid webmasters who insist on using it for navigation buttons(instead of CSS), I wouldn't need their stupid ad-infested piece of junk.

---

