---
title: "windows manager tweaks"
date: 2014-12-02
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-12-02
Why is 'Synchronize drawing to vertical blank' OFF by default?  Enabling this option gives a smooth screen transition when moving and placing windows.  The off default setting detracts from (choppy) the ambiance and so , by default, noobs or new converts may think that xubuntu-desktop has choppy screen movement by default.

---

### Post by Elfy on 2014-12-02
No idea why. 

```
ubuntu-bug xfwm4-tweaks-settings
```

Then you can find out :)

---

### Post by ventrical on 2014-12-02
> **Elfy said:**
> No idea why. 

```
ubuntu-bug xfwm4-tweaks-settings
```

Then you can find out :)

Aye??

---

### Post by Elfy on 2014-12-02
You'll have to report against xfwm4 then. 

If you report it upstream as well - you can actually fine tune the bug there so it's against Settings. (if you don't then someone else will ... )

---

### Post by Toz on 2014-12-03
Might have something to do with the fact that it won't work well in certain multi-monitor setups. See [the original bug report and especially comment #20 here]("https://bugzilla.xfce.org/show_bug.cgi?id=8898").

---

### Post by ventrical on 2014-12-03
> **Toz said:**
> Might have something to do with the fact that it won't work well in certain multi-monitor setups. See [the original bug report and especially comment #20 here]("https://bugzilla.xfce.org/show_bug.cgi?id=8898").

Ahh... I keep forgetting that xubuntu is more of a minimalist DE for older PCs first and foremost.

thnxs 

Regards..

---

### Post by Elfy on 2014-12-03
> **ventrical said:**
> Ahh... I keep forgetting that xubuntu is more of a minimalist DE for older PCs first and foremost.

thnxs 

Regards..

It might have been once, it isn't so much now.

> 
Xubuntu does not explicitly target users with low, modest, or high powered machines but instead targets the entire spectrum. Xubuntu's extra responsiveness and speed, among other positive traits, can be appreciated by all users, regardless of their hardware. 

[https://wiki.ubuntu.com/Xubuntu/StrategyDocument#The_Target](https://wiki.ubuntu.com/Xubuntu/StrategyDocument#The_Target)

---

### Post by ventrical on 2014-12-03
> **Elfy said:**
> It might have been once, it isn't so much now.



[https://wiki.ubuntu.com/Xubuntu/StrategyDocument#The_Target](https://wiki.ubuntu.com/Xubuntu/StrategyDocument#The_Target)

Alright then.  But it doesn't make sense because all the other flavours have their best 'appearance foot forward' so why not xubuntu with the little setting I mentioned?

 However .. as toz has said .. it must have to do with certain  muliple monitor setups.

---

