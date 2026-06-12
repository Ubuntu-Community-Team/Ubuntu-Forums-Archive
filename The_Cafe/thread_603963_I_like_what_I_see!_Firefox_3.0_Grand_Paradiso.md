---
title: "I like what I see! Firefox 3.0 Grand Paradiso"
date: 2007-11-05
forum: The Cafe
---

### Post by -grubby on 2007-11-05
I was looking for an "unknown" plugin in Firefox (still haven't found it) I searched in synaptic for "firefox" and found Firefox 3.0. (I thought I had to manually compile it to install it)
     When I saw Firefox 3.0 in the repos I installed it. Although it has some rather apparent bugs (things like not exiting when I hit the exit button, telling me what program I want to use for autolink emailing when right clicking sometimes,etc.etc.) Its the best version of Firefox I've seen! Really it's much faster (for me, at least) when opening pages and isn't a RAM hog like Firefox 2.0. It also doesn't crash every other time I open a Youtube video. My only extension I use, adblock plus also works with firefox 3.0. So I really  think I'm going to keep This on here

UPDATE:update: I have since gotten a screenshot of Firefox 3 and Firefox 2s RAM usages. It looks like Firefox 3 wins (both were at google.com) and I assume that Firefox-bin is also firefox2 as it was that way before and Firefox-bin doesn't run when only firefox3 is open. Also,there is no way Firefox is using 76KB of RAM. Screenshot on PG 2

---

### Post by smartboyathome on 2007-11-05
I too like Firefox 3 when on GNOME. I have found a bug on Enlightenment where it doesn't always work (it crashes a lot more frequently), but I still have Epiphany!

---

### Post by -grubby on 2007-11-05
I'm using KDE and it's just fine

---

### Post by n3tfury on 2007-11-05
you say the RAM use is not as much, but that doesn't mean there's no leak.  have you looked into that?

---

### Post by -grubby on 2007-11-05
> **n3tfury said:**
> you say the RAM use is not as much, but that doesn't mean there's no leak.  have you looked into that?

all I've really noticed is how much faster it is and how less often it crashes. Let's see how much RAM It's using right now...
I can't seem to find it in K system guard (RAM usage)

---

### Post by n3tfury on 2007-11-05
doh.  if you can find out and post your results, i'd be interested to see it.

---

### Post by smartboyathome on 2007-11-05
I know I probably found one memory leak. When firefox 3 loads large images it freezes.

---

### Post by -grubby on 2007-11-05
> doh. if you can find out and post your results, i'd be interested to see it.I'll try to find it:)

---

### Post by -grubby on 2007-11-05
well whatever "VMsize" is its using 200,000 [units] of it and Firefox 2.0 is using only 1,270 [units] of it

---

### Post by n3tfury on 2007-11-05
lol, i don't know either.

---

### Post by aninaiian on 2007-11-05
I'm not entirely sure but I think the VM in VMsize is virtual memory.  If that's the case then firefox-3.0 thinks it has 200000 bytes of memory to work with which doesn't really say much.  Is there RMsize (real memory) or something similar?  That should tell you how much firefox is really using.  On my system, real memory for firefox-3.0 is around 50-60 MB.

> **nathangrubb said:**
> well whatever "VMsize" is its using 200,000 [units] of it and Firefox 2.0 is using only 1,270 [units] of it

I think the you might have posted the shell script for firefox 2.0 as there is no way that it thinks it has 1.2 MB of RAM to work with.

---

### Post by macogw on 2007-11-05
It's *almost* CSS2 compliant!  Still no glow :(  Safari added rounded corners on divs (CSS3 draft spec) to KHTML and KHTML already does glow, so Gecko is still a bit behind.  I'd really like to see it become fully CSS2 compliant and implement at least some of CSS3.

---

### Post by p_quarles on 2007-11-05
To find out system usage for an individual process, you can do this:
```
ps -e
```
Make a note of the PID (the number in the first column) next to Firefox 3. Then
```
top -p*#PID#*
```
will give you a summary of usage (RAM, CPU time, etc.)

---

### Post by sp0onman on 2007-11-05
is there a way to install it with out uninstalling 2.0.0.7?

---

### Post by -grubby on 2007-11-05
> **sp0onman said:**
> is there a way to install it with out uninstalling 2.0.0.7?

when I installed it it didn't uninstall Firefox 2.

---

### Post by smartboyathome on 2007-11-05
> **nathangrubb said:**
> when I installed it it didn't uninstall Firefox 2.

Same here. In fact, I use Firefox 2 for work and Firefox 3 for play, as if one crashes it doesn't affect the other.

---

### Post by -grubby on 2007-11-09
update: I have since gotten a screenshot of Firefox 3 and Firefox 2s RAM usages. It looks like Firefox 3 wins (both were at google.com) and I assume that Firefox-bin is also firefox2 as it was that way before and Firefox-bin doesn't run when only firefox3 is open. Also,there is no way Firefox is using 76KB of RAM. Here's the screenshot

---

### Post by svtfmook on 2007-11-10
where can you install ff3?

---

### Post by -grubby on 2007-11-10
> **svtfmook said:**
> where can you install ff3?

just search in the repositories for Firefox 3 and download "grand paradiso" or "firefox 3"

---

### Post by svtfmook on 2007-11-10
> **nathangrubb said:**
> just search in the repositories for Firefox 3 and download "grand paradiso" or "firefox 3"

searched, can't find it

---

### Post by herbster on 2007-11-10
Hang up, it's a beta y'all are talking about, right? Or did I somehow completely miss its final release ??

---

### Post by p_quarles on 2007-11-10
> **herbster said:**
> Hang up, it's a beta y'all are talking about, right? Or did I somehow completely miss its final release ??
No, the one in the repos is alpha 8. You'll need to have the universe repository enabled, though. Here's the package's web page:
[http://packages.ubuntu.com/gutsy/web/firefox-granparadiso](http://packages.ubuntu.com/gutsy/web/firefox-granparadiso)

---

### Post by svtfmook on 2007-11-10
ah, it's in the gutsy repository, that's why i can't find it in the feisty repository, lol.

---

### Post by Billy_McBong on 2007-11-10
[COLOR="Blue"]i installed it but it doesn't have flash[/COLOR]

---

### Post by -grubby on 2007-11-10
> **Billy_McBong said:**
> [COLOR="Blue"]i installed it but it doesn't have flash[/COLOR]

go to a flash site (ex:google video) and try to use a flash control (in this case,playing a video) and it should install flash or alert you to install flash

---

### Post by herbster on 2007-11-10
> **p_quarles said:**
> No, the one in the repos is alpha 8. You'll need to have the universe repository enabled, though. Here's the package's web page:
[http://packages.ubuntu.com/gutsy/web/firefox-granparadiso](http://packages.ubuntu.com/gutsy/web/firefox-granparadiso)

Thanks!

---

### Post by smartboyathome on 2007-11-10
> **Billy_McBong said:**
> [COLOR="Blue"]i installed it but it doesn't have flash[/COLOR]

It also doesn't have Ubufox or apturl :(

---

### Post by n3tfury on 2007-11-10
> **smartboyathome said:**
> It also doesn't have Ubufox or apturl :(

did you *really* expect it to in its alpha stage?

---

### Post by maharbA on 2007-11-10
I just installed it -- it's remarkably stable for an alpha (only a few "quirks"). Although it is very similar to 2.0
It actually kept all my stuff from 2.0 (which is still there, BTW) which is very cool.

I had heard that 3.0 would have a "private" browsing mode. Is this available yet? If so, how -- I can't find it.

---

### Post by Billy_McBong on 2007-11-10
> **nathangrubb said:**
> go to a flash site (ex:google video) and try to use a flash control (in this case,playing a video) and it should install flash or alert you to install flash
[COLOR="Blue"]it should but it doesn't
i have flash installed(works on other browsers) but not on Grand Paradiso

ill just wait for Swiftweasel 3[/COLOR]

---

### Post by -grubby on 2007-11-10
> **Billy_McBong said:**
> [COLOR="Blue"]it should but it doesn't
i have flash installed(works on other browsers) but not on Grand Paradiso

ill just wait for Swiftweasel 3[/COLOR]

that's strange. One thing that might work is to copy the flash plugin folder in /home/xxxx/.mozilla/firefox/xx into /home/xxxxx/.mozilla/firefox3

---

### Post by Billy_McBong on 2007-11-10
> **nathangrubb said:**
> that's strange. One thing that might work is to copy the flash plugin folder in /home/xxxx/.mozilla/firefox/xx into /home/xxxxx/.mozilla/firefox3
[COLOR="Blue"]didn't work
but i was wrong before it does ask to install missing plugins(although it doesn't find any). i just didn't notice that youtube doesn't display the flash if you don't have the plugin[/COLOR]

---

### Post by gimmy_bond on 2008-01-15
Yes indeed, Gran Paradiso is fast, sleek and nice looking mama. But the fact that no easy installation of plugins (flash, Java, etc.) makes it somewhat limited to use.

---

### Post by jrusso2 on 2008-01-15
I downloaded mine from [http://www.mozilla.com/en-US/firefox/all-beta.html](http://www.mozilla.com/en-US/firefox/all-beta.html)

And flash and java both work.

---

### Post by FuturePilot on 2008-01-15
It's faster! :)

---

