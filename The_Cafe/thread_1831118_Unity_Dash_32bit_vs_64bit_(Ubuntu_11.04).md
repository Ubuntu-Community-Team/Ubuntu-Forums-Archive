---
title: "Unity Dash: 32bit vs 64bit (Ubuntu 11.04)"
date: 2011-08-22
forum: The Cafe
---

### Post by 1roxtar on 2011-08-22
I've have been updating all my computers equally, but I noticed some differences between my 32 bit computers and my 64 bit machines all running 11.04 Natty Narwhal.  My 32bit machine's Dash looks like this...

[IMG]http://i220.photobucket.com/albums/dd237/1ROXTAR/NattyScreenshot.png[/IMG]

It resembles a lot of what 11.10's Scopes and Lenses is shaping up to be, but my 64 bit machines all still look like the same 11.04 Dash.  Does anyone know why this is?  I thought both 32 and 64 bit are supposed to look identical.  I like this and would like my 64 bit Dash to look and function like my photo above.

---

### Post by FuturePilot on 2011-08-23
You probably added a repo to one and not the other.

---

### Post by 1roxtar on 2011-08-23
Dunno.  I commit the exact same process for both architectures, but each 32bit system looks and behaves the same and so does each 64bit machine, as well.  Does anyone have a 64bit system that functions like the posted photo???  My curiosity is peaked.

---

### Post by 1roxtar on 2011-08-23
Anyone?

---

### Post by FuturePilot on 2011-08-23
Post your /etc/apt/sources.list and anything else that is in /etc/apt/sources.list.d/ from both machines.

---

### Post by sikander3786 on 2011-08-23
I agree with what *FuturePilot* said. They won't backport it to Natty, it looks like you installed a newer version of Unity from some PPA.

---

### Post by 1roxtar on 2011-08-24
I also noticed that the Overlay Scrollbars on the 32bit version are also squared like in Oneric and not rounded like my 64bit Natty.  I haven't installed any type of Unity ppa's.  I just recently did a clean install on my brother's laptop and after running the updates, he too has the same dash as illustrated in my original post.  All my 32bit machines look like this and all my 64 bit machines look like the regular original Natty.  I have all the same repos and my settings are all identical on both architectures, but I'm getting different updates from each.  I'm gonna try the source list idea, though.

---

### Post by sikander3786 on 2011-08-24
> **1roxtar said:**
> I also noticed that the Overlay Scrollbars on the 32bit version are also squared like in Oneric and not rounded like my 64bit Natty.  I haven't installed any type of Unity ppa's.  I just recently did a clean install on my brother's laptop and after running the updates, he too has the same dash as illustrated in my original post.  All my 32bit machines look like this and all my 64 bit machines look like the regular original Natty.  I have all the same repos and my settings are all identical on both architectures, but I'm getting different updates from each.  I'm gonna try the source list idea, though.
Yeah that would be better. We need to see the output of these commands:

```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d
```

---

### Post by 1roxtar on 2011-08-26
I just realized that I did add something different to my 32 bit computers.  It was Unity 2D.  I haven't added 2D on my 64 bit machines because I had lots of RAM on those computers.  I added Unity 2D to one of my machines and it updated just as my original posted screenshot.  I guess some of those updates also ported to Unity 3D, as well.

:guitar:

---

### Post by Oxwivi on 2011-08-26
That is great news. The more code-bases being shared, the better.

By the way, solved I guess?

---

