---
title: "How does AIR manage to install itself with root privileges?"
date: 2008-12-30
forum: The Cafe
---

### Post by jfernyhough on 2008-12-30
(I'll post this here as I'm not sure of the best place - mods feel free to move it)

So I thought I'd give the BBC iPlayer desktop application a go. It uses AIR and once you've gone through and set the prerequisite cookie and found a programme to download it asks whether to install AIR. Which it does. In /opt.

Hence, my question is this:

**How the hell does a Flash applet running with my credentials manage to install an application to /opt ?**

---

### Post by mister_pink on 2008-12-30
Bearing in mind I have used neither of these applications, I can only imagine that when air is installed with root priviledges it uses setuid to enable it to install other applications as root. basically setuid means that anyone can run a specific program as though they were whatever user owns that program.

---

### Post by Sealbhach on 2008-12-30
> **jfernyhough said:**
> 

Hence, my question is this:

**How the hell does a Flash applet running with my credentials manage to install an application to /opt ?**

You mean Ubuntu doesn't ask for your password?


.

---

### Post by jfernyhough on 2008-12-30
> **Sealbhach said:**
> You mean Ubuntu doesn't ask for your password?Yes, sorry, probably should have mentioned that. It didn't on both machines I installed it on, but whether this was due to running Synaptic relatively recently...

I'm trying to test it again now but it doesn't seem to want to work. :D The applet just sits there with a constantly moving stripy progress bar...

I'll try some other things.

---

### Post by Vadi on 2008-12-30
Adobe AIR does ask for the password.

sudo, however, remembers it for 15 mins by default. If you gave your password recently, it won't bug you again. There's a setting to change this if you'd like, but air does nothing fishy here.

---

### Post by jfernyhough on 2008-12-30
Ah, then that's fine.

I did start to wonder, though. :D

---

### Post by Vadi on 2008-12-30
And that is good behavior :)

---

