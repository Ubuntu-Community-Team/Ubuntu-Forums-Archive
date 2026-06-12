---
title: "Play the &quot;rm -rf&quot; game with me."
date: 2008-01-09
forum: The Cafe
---

### Post by jingo811 on 2008-01-09
Ever since the forum mods started warning ppl about bad persons tricking newbies into running this destructive command and thus destroying their Ubuntu systems.
```
rm -rf
```

I wanted to try doing it myself even though it was bad for my health.  Besides I needed to wipe away everything anyways in order to make room for my triple-boot-system.

So I ran the command (on Debian) and it started deleteting stuff thinking that it will all be over within 1 minutes or so I waited.  But then it kept on deleting so I switched on my Nintendo DS to kill some time.  After 5-10 minutes it was still deleting ( not sure about the actual time it took, it felt like over 5 minutes ).
So I "Ctrl+C" to cancel the operation.

Then I tried to log into X11 with Gnome it still worked, I could still use Firefox to reach Internet.  I could still do important tasks to save my system such as apt-get.
That's why it maked me wonder how long does "rm -rf" need to run before all your basic "fix-things-up" functions will be out of your reach.

**If you're planning on deleting your Linux system and re-install things fresh.  Please clock yourself and write down your observations on how many minutes you could run "rm rf" yet still be able to X11 and surf the Internet with Firefox and use apt-get.  You know all the important stuff that matters to newbies when they need help via Internet and the forums.  When things go horribly wrong.**

---

### Post by maybeway36 on 2008-01-09
What were you deleting? You can just delete the partition if you want to get rid of everything.

---

### Post by Kingsley on 2008-01-09
I can't but remember a pointless game some of my friends played in high school. They'd cut off circulation to each others brains to see how long it takes to pass out.

---

### Post by steeleyuk on 2008-01-09
It all depends on how many gigabytes of files you have on your machine. rm -rf goes through every folder on all your drives that are mounted and attempts to delete them. If you've got tens or hundreds of thousands of files then it could take a couple of hours depending on certain things like hard drive speed and CPU speed.

---

### Post by milton1 on 2008-01-09
If you run this from your home directory, without using sudo, it will only hose the one user. The root system will remain intact. This is one of the security features of linux. The real killer would be: 
```

foo

```Run this and you're hosed.

---

### Post by danillo on 2008-01-09
rm -rf what? The command means "remove recursive (remove directories and their contents recursively) force (ignore nonexistent files, never prompt)"
> **milton1 said:**
> If you run this from your home directory, without using sudo, it will only hose the one user. The root system will remain intact. This is one of the security features of linux. The real killer would be: 
```

foo

```Run this and you're hosed.

Exactly.

---

### Post by PriceChild on 2008-01-09
This "game" is in bad taste and I see absolutely no benefit whatsoever to it remaining open.

---

