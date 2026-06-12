---
title: "Cursor gets stuck in text-select (highlight) mode"
date: 2011-12-28
forum: System76 Support
---

### Post by Brad1234 on 2011-12-28
I recently purchased a System76 Lemur UltraThin running Ubuntu 11.10 and am having this problem:

Occasionally, for reasons I cannot determine, the cursor sticks in text-select mode. Nothing is clickable but running the cursor up or down the page highlights text, even though no mouse button is depressed. Frequently only a hard reboot seems to fix the problem.

These do not help: Esc, ctl-x, ctl-q, ctl-c, ctl-z 

I thought perhaps I had some weird key-combination activated but I have not been able to locate anything like that (though I'm not ruling it out)

This most frequently happens when text editing (using LibraOffice Writer or gedit, but also in the browser (Chromium) - most frequently in a text field but even outside such fields.

The keyboard still works, and sometimes I can use keyboard commands to exit the program, in which case I can sometimes directly reopen the program and it is fine, but other times exiting the program simply means the cursor does not work on the desktop and I have to use the power switch to reboot.

Any wisdom would be greatly appreciated.

Brad

---

### Post by isantop on 2011-12-28
Are you using an external mouse? If so, does this ever happen when you unplug it and use the built-in trackpad only?

---

### Post by Brad1234 on 2011-12-28
Yes, I am using an external mouse, a Logitec Optical Mouse. I use the laptop so seldom without a mouse that I could not say if the problem occurs when using the pad.

---

### Post by isantop on 2011-12-29
Is it a wireless mouse? I've had problems with wireless mice many times before.

---

### Post by Brad1234 on 2011-12-29
No, it is a wired mouse.

---

### Post by zitch on 2011-12-29
I've experienced this issue in the past on my Serp 5 (both when it was running the original Ubuntu 8.10 and the current 10.04 on it) and I seemed to have link it to my palm brushing on the touchpad when I was typing and using an external USB wired mouse. Basically, the touchpad goes into a "hold and drag" mode, imitating the issues you're seeing and frustrating me in the process.

Basically, next time it happens, try clicking the touchpad's left mouse buttton or tap on the pad and see if this gets you out of the "drag" mode. If this is the case, you can either disable the touchpad manually when using an external mouse (On my Serp5, this is Fn-F1, may be different on your system), or uncheck "Enable mouse clicks with touchpad" or equivalent in your Mouse Preferences) if you rarely use the touchpad anyways.

I still often use the touchpad with the "tap to click" mode, but it seems I've adjusted my typing posture to avoid accidentally brushing on the pad while typing in the meantime, so I haven't hit on this issue while using an External mouse in some time.

---

### Post by Brad1234 on 2011-12-29
Great suggestion. I'll try it.

---

