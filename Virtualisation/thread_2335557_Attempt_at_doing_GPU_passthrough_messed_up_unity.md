---
title: "Attempt at doing GPU passthrough messed up unity"
date: 2016-08-30
forum: Virtualisation
---

### Post by rasmus91 on 2016-08-30
Hi there

I no longer have any UI elements on my Linux desktop. The panel at the top is gone. CRTL+ALT+T doesn't do anything. I can rightclick and open a terminal, which appears at the top left cornor, undecorated. 

I've reverted all the steps i followed in the GPU Passthrough guide [Ubuntu GPU Passthrough]("https://youtu.be/w-hOr44oBAI") but i reverted after trying to black list my nVidia card since that just wouldn't work.

I've tried doing this:
```
unity-tweak-tool --reset-unity
dconf reset -f /org/compiz/
setsid unity
```

The screen flickers slightly, but otherwise it seems to have no effect, even after reboot.

Also: Guest session unity works perfectly.

Any suggestions?

---

### Post by ajgreeny on 2016-08-30
*Thread moved to **Virtualisation**.* which is more appropriate for the problem.

---

### Post by KillerKelvUK on 2016-08-30
Never heard of this type of corruption before as a result of GPU passthrough, maybe its coincidental?

Have you tried removing the contents of the .config folder in your home directory?  But of a sledge hammer approach but... (remember to backup first)

---

### Post by rasmus91 on 2016-08-31
> **KillerKelvUK said:**
> Never heard of this type of corruption before as a result of GPU passthrough, maybe its coincidental?

Have you tried removing the contents of the .config folder in your home directory?  But of a sledge hammer approach but... (remember to backup first)


Yes, I've considered that as well, but i can't think of anything else I've been messing around with lately that could possibly do something like this.

A bit, yes, but considering none of the usual methods works this would likely be worth a try. I'll let you know if it works :)

---

### Post by rasmus91 on 2016-08-31
Right, so i did CRTL+ALT+F1, logged in, and then did:

```
mv .config .configBU
```

Then CRTL+ALT+F7 and logged into unity... or so i thought. It's exactly the same issue as before, with one tiny difference: The background is now the standard one, and the cursor and theme is the standard Ambiance.

:(

I must admit I'm getting pretty frustrated, especially as I have really no idea what else to do. I considered whether it could be the fact that the integrated graphics accelerator has been activated, but then that should play just as much of an effect on the guest session, right? UGH!

any other suggestions? (besides a reinstall)

---

### Post by rasmus91 on 2016-09-01
And then, like magic after updating ubuntu this morning, (there was a kernel update and a .NET host update amongst a few others), after a reboot it suddenly worked again.

what changed? no idea, but i'm happy it did.

---

### Post by KillerKelvUK on 2016-09-02
> **rasmus91 said:**
> 
what changed? no idea, but i'm happy it did.

And like that we accept the magic for what it is :lolflag:

Glad this is sorted for you know.

---

