---
title: "Ubuntu in parallels world?"
date: 2023-11-19
forum: Ubuntu, Linux and OS Chat
---

### Post by enderbro763 on 2023-11-19
What if Canonical switched from Unity to Mate in 2012 in the Ubuntu 12.04 release and there was no redesign.
[IMG]https://i.imgur.com/zW8Xywj.png[/IMG]

---

### Post by ian-weisser on 2023-11-19
I remember those times well.

Without Unity, we would see a lot of endless complaining about the limitations of GTK2 (which we would still be using), and Gnome/MATE's ancient UX design standards, and we would still be fretting about all the unpatchable security holes in Xorg (which we would also still be using).

Unity gave a kick to complacency in design and user experience for a lot of projects. In 3-4 years, Unity's challenge transformed Gnome and KDE and many other DEs. It transformed their look, their user experience, and (in many cases) their project organization.

Unity also went hand-in-hand with conversion from sysvinit to Upstart. Without that change, no systemd. We would all still be kludging sysvinit scripts to do things it simply wasn't designed to do.

Unity was an example of healthy competition spurring improvement and innovation among peer projects.

---

### Post by #&amp;thj^% on 2023-11-19
> **ian-weisser said:**
> 
Unity was an example of healthy competition spurring improvement and innovation among peer projects.
Yes Sir well worded along with rest of your post.
However I still get wrapped around the wheel at times, I'm very very passionate on Linux.
And I believe QA was far better then, than now. :(

---

### Post by TheFu on 2023-11-19
Everything being touted as progress isn't seen as progress by everyone.  Certainly not Unity, not GTK3+, not upstart, nor systemd, and currently not Wayland.  

I miss init scripts.  They worked for me.  

I've dumped all DEs because they seem to be changed for "new" without any good reason. Upstart and systemd were created to solve problems 95% of the world never had.  Systemd is like the MPC that Tron warned us about, slowly taking over more and more and more, whether we want it or not.  I hear Firefox is considering dropping X11 support on Linux.  If that happens with the current state of Wayland, I'll have to drop Firefox as a browser, which will be painful, since it is part of some of my workflows. Chromium and chromium-based browsers don't behave correctly for some specific websites.

Fortunately, there are lots of people who fall into my type of thinking and have kept older software maintained for the world.  It means I have 2-10 yrs more for those tools to become production ready or mature enough to handle my workflows.  

Technical debt is a real thing and all older software has some. Probably the worst is X11.  Eventually, it will be replaced by something. I don't know if that will be Wayland or something else.  I've worked on software that had cross module dependencies where a tiny change 15 modules away always broke something else.  We had 1 module that for every line touched, at least 1 critical bug would be caused or uncovered, so everyone strove to avoid ever touching that specific module. I was lucky.  My "touch" uncovered 2 prior critical bugs, but at least I didn't introduce any.  Pure luck, not skill.

I'm also very passionate ... but to me "change" is a dirty word, unless there is actually a good reason beyond being new that helps most users.  Perhaps in 5+ more years, Wayland will be ready. I'm hopeful.   Replacing something complex that is 40+ yrs old doesn't happen overnight or in 78 yrs.  For most everything else, I may be forced to switch to MXLinux, which is fine.  I don't expect Canonical to care.  Their user-base is diverging more and more from my desires/needs.  Lots of distros don't fit my needs, so that's 100% ok.

If I could, I'd mandate that all programmers be forced to do 5 yrs of maintaining other people's code BEFORE they are allowed to create anything new.  Maintenance programmers know so much more about coding that people who only spew their own junk code.

I started this post with "no comment", but clearly that didn't stop me.

---

### Post by ian-weisser on 2023-11-19
> **TheFu said:**
> Everything being touted as progress isn't seen as progress by everyone.

That should be engraved in a lot of places. A reasonable and sensible perspective.

> **TheFu said:**
> I don't expect Canonical to care.  Their user-base is diverging more and more from my desires/needs.  Lots of distros don't fit my needs, so that's 100% ok.

That too: The wisdom to say that differences are OK.

---

### Post by enderbro763 on 2023-11-20
This is btw Debian 12 with a theme from the old ones Ubuntu (I stopped using it myself Ubuntu and moved on Debian)

---

