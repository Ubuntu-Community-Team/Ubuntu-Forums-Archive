---
title: "Style issues with Python GTK app in Unity"
date: 2012-08-19
forum: Ubuntu Application Development
---

### Post by niktto on 2012-08-19
Hi all,

For some simple testing I've tried lunching my GTK app under Unity with default settings on Ubuntu 12.04. I've spotted some issues with rendering widgets (at least I think that is the cause of problem). Sample code that shows this issue is in this gist: [https://gist.github.com/3397368]("https://gist.github.com/3397368")

As you can see after running this code - button is "blinking" when hovered, this issue shows only if you use picture as background. Additionally there is some orange border around button while window is in focus, this also didn't occur in Gnome (3) while I tested on Debian.

My question is - are there some known differences between styling GTK for Gnome and Unity? How do you work around that differences? (And how to get rid of these 2 issues sampled above? ;))

Thanks!
- Mark

---

### Post by niktto on 2012-08-20
Ok, it seems that root of the issue lays not in Unity but in themeing system. Depending on theme that is enabled - app window looks different (not only borders, but things such as image scaling). This is huge and I guess there is only one way out - disable os theme in my app.

Now, I just need to find how to do this ;).

---

### Post by niktto on 2012-08-28
After some testing this setting in css fixes most of issues:
```

* {
    engine: none;
  }

```

---

