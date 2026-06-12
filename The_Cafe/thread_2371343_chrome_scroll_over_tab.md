---
title: "chrome scroll over tab"
date: 2017-09-13
forum: The Cafe
---

### Post by k28 on 2017-09-13
i hope im not completly wrong here. my problem is i want to disable the scroll over tab function. i think i found a solution but im not sure:

[https://bugs.chromium.org/p/chromium/issues/detail?id=407051](https://bugs.chromium.org/p/chromium/issues/detail?id=407051)

its comment 19. is tis a fix? if yes where and how to i apply it?

---

### Post by vasa1 on 2017-09-13
Comment #19 has this, in part:> 
- For users that dislike this feature: chrome.tabs.onBeforeActivate event: Fires before chrome.tabs.onActivated, with a reason for the activation. Gives an extension the chance to cancel the activation if the reason is mouse wheel scroll.
So it looks like they've allowed for an extension to disable the feature. In other words, you'll need an extension to disable the tab scrolling.

---

