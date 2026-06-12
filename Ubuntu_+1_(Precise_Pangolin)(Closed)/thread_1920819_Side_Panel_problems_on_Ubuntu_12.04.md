---
title: "Side Panel problems on Ubuntu 12.04"
date: 2012-02-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by joelstitch on 2012-02-05
Whenever I point my mouse to the left side of the screen the side panel doesn't come out unless I have no windows open or if I press the Window key. Is this a common issue? anybody knows of a fix?

---

### Post by dcstar on 2012-02-06
> **joelstitch said:**
> Whenever I point my mouse to the left side of the screen the side panel doesn't come out unless I have no windows open or if I press the Window key. Is this a common issue? anybody knows of a fix?

Anything whatsoever to do with development releases must be posted using the process for that release, they have no place in the support forums which are only for released versions:

[https://wiki.ubuntu.com/Testing/](https://wiki.ubuntu.com/Testing/)

---

### Post by nothingspecial on 2012-02-06
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

---

### Post by mc4man on 2012-02-06
maybe because it's Point & Push?
(sometimes it has to be repeated over or over & over again, if desired open the unity plugin settings & lower the 'pressure' value from it's default of 20 to what works for you

---

### Post by kyleabaker on 2012-02-06
> **mc4man said:**
> maybe because it's Point & Push?
(sometimes it has to be repeated over or over & over again, if desired open the unity plugin settings & lower the 'pressure' value from it's default of 20 to what works for you

This change occurred with the upgrade from Unity 5.0 to Unity 5.2 and has also been a royal pain to me. I'm hoping the default pressure value will be fine tuned before release.

I also preferred to not have a duplicate panel on my extended monitors, but I can live with it for now.

---

### Post by redcylon on 2012-02-06
Basically there are 2 ways:

1. Keep pushing the mouse to the left until it came out (instead of where most people would just stop when the cursor reached the left edge of the screen)

2. Push the cursor to the left and thereafter drag it upwards (still at the edge of the screen) until the launcher came out.

The biggest benefits (for me that is) you won't accidentally brought the launcher out when trying to reach those back button at mozilla!

---

### Post by joelstitch on 2012-02-06
> **redcylon said:**
> Basically there are 2 ways:

1. Keep pushing the mouse to the left until it came out (instead of where most people would just stop when the cursor reached the left edge of the screen)

2. Push the cursor to the left and thereafter drag it upwards (still at the edge of the screen) until the launcher came out.

The biggest benefits (for me that is) you won't accidentally brought the launcher out when trying to reach those back button at mozilla!

If I do what you suggested it works. I just wonder why it changed from it coming out immediately to me having to keep draging the mouse for it to come out. Thanks!

---

### Post by kyleabaker on 2012-02-06
> **joelstitch said:**
> If I do what you suggested it works. I just wonder why it changed from it coming out immediately to me having to keep draging the mouse for it to come out. Thanks!

The change was intended to prevent accidentally revealing the side panel when you're attempting to click the back button in Firefox (as an example). The problem is that its not very intuitive or user friendly. I really think they should go back to the drawing boards on this one.

---

### Post by xyzzyman on 2012-02-06
If you install ccsm 

```
sudo apt-get install compizconfig-settings-manager
```

and run it, under the experimental tab you can change the setting. 20 is much to high as people are finding. Be careful in ccsm as you can thoroughly hose your setup.

---

### Post by kyleabaker on 2012-02-06
> **xyzzyman said:**
> If you install ccsm 

```
sudo apt-get install compizconfig-settings-manager
```

and run it, under the experimental tab you can change the setting. 20 is much to high as people are finding. Be careful in ccsm as you can thoroughly hose your setup.

These are the settings I've been using...

[[IMG]http://img43.imageshack.us/img43/1921/screenshotat20120206110.png[/IMG]]("http://img515.imageshack.us/img515/1921/screenshotat20120206110.png")

They could probably be fine tuned more, but this is already much better for me. Also, I've changed the "Edge Stop Velocity" to 20 and this helps with multiple monitors.

---

