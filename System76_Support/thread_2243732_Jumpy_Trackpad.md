---
title: "Jumpy Trackpad"
date: 2014-09-10
forum: System76 Support
---

### Post by VinceG3 on 2014-09-10
Hi. I just purchased a System76 Galago UltraPro and everything works really well for me except for the trackpad. It's bordering on unusable, which is quite unfortunate. Whenever I click, the cursor often jumps before the click event registers, half the time what's clicked on is different than what I meant to click on, or it doesn't register meaning I have to go through click roulette again. Is there any configuration fix for this issue or am I stuck waiting on new drivers, if they ever show up?

---

### Post by VinceG3 on 2014-09-13
This command helped me out a lot.

```
[FONT=courier new]xinput --set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Noise Cancellation" 50 50
[/FONT]
```
Add it to Startup Applications

---

