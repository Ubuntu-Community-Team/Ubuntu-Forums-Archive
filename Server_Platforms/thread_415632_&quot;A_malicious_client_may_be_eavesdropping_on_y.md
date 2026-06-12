---
title: "&quot;A malicious client may be eavesdropping on your session&quot;"
date: 2007-04-20
forum: Server Platforms
---

### Post by use a name on 2007-04-20
Alarming message, but I think I have found an explanation. But I still want to know if this excludes an intruder.

I'm trying to checkout an svn project from my server using KDevelop. As soon as I tye the location
```

svn+ssh://xxx.xxx.xxx.xxx/

```
it pops up a ssh-askpass dialog. I had not finished typing the full url yet, so I continued typing as the dialog was created. Then I got this message:
> 
Could not grab keyboard. A malicious client may be eavesdropping on your session

I can reproduce this by continuing to type the url. It seems that another ssh-askpass is launched, as soon as I type the second '/' before the first ssh-askpass grabs input. Then two ask-pass dialogs are trying to grab input, causing the error.

Would that explain the whole problem or should I worry about an intruder?

---

