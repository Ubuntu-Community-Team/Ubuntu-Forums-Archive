---
title: "Home key is not functioning as it should"
date: 2011-09-28
forum: System76 Support
---

### Post by mahermali on 2011-09-28
Hi all
I got the serval professional finally
I found a problem, I'm not sure if it is hardware or software problem.
When turning off the numlock key, the number 7 should be the home key, pressing shift+#7 gives always (7), but #7 works as home key.

Is it a bug ?

Regards

---

### Post by drewbenn on 2011-09-30
I'm running Debian Squeeze (Stable) on a non-System76 laptop (an "MS-1656") but it has a full numeric keypad.  Here's a table of how the Home key behaves for me, using the 'xev' utility (Applications | Accessories | Terminal | xev):

```
             | kp_7    | shift+kp_7
-------------+---------+-----------
num lock on  | KP_7    | KP_Home
num lock off | KP_Home | KP_7
```

I also have the same behavior for the End key, except of course "KP_End" and "KP_1".

It is really frustrating, because I have to use Fn+Shift+(PgUp/Home key above the numeric keypad) [for you, that's probably Fn+Shift+(left arrow key)] to get Shift+Home behavior, and it's a serious pain to have to always use the Function key to just press "Home" or else have two different Home keys depending on what you want to do, but I wanted to let you know: it's not just you.

---

