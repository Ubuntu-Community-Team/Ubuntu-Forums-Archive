---
title: "How do you clear old Firefox addon data?"
date: 2010-05-11
forum: The Cafe
---

### Post by Pogeymanz on 2010-05-11
I have un/installed quite a few Firefox addons in the last few years and when I go to about:config it still has lots of entries from those old addons that I've uninstalled.

Is there an option to clean them automatically?

For now I just open the profile file in a text editor and start deleting crap, which I imagine is probably dangerous. At least I back up the file first.

---

### Post by TheNessus on 2010-05-11
.

---

### Post by lovinglinux on 2010-05-11
I have thought about this my self several times, since I usually clean up my profile too. Nevertheless, I do so just because my OCD tendencies, because orphan preferences doesn't affect browser performance or stability.

The safest way is to open **about:config**, then click the status row to sort the preferences by status. Look for the bold ones, which are those changed from the default value. Right-click on the orphan preferences and select the "Reset" option. Unfortunately, you need to click one by one. 

Restart Firefox. When the browser loads again, all orphan preferences with default values will be automatically removed.

I don't think there is a way to automatically remove orphan preferences with non-default values. The thing is Firefox keeps those if you decide to install the extension again and because you can add some custom browser preferences that don't exist by default. If there was a way to remove non-default orphan preferences, then the custom browser preferences would also be removed.

---

### Post by Pogeymanz on 2010-05-12
Well, it isn't automatic, but the way you described is much less dangerous.

I know it's just obsessive to do these things but whatever.

---

### Post by lovinglinux on 2010-05-12
> **Pogeymanz said:**
> I know it's just obsessive to do these things but whatever.

Yeah, but we like to do it anyway :)

Want to cleanup your bookmarks too? See [Check Places](https://addons.mozilla.org/en-US/firefox/addon/10897) (not mine).

---

