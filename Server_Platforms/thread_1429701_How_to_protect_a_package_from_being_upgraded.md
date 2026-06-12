---
title: "How to protect a package from being upgraded"
date: 2010-03-14
forum: Server Platforms
---

### Post by jocampo on 2010-03-14
Hi,

I do have virtualbox-3.0 on my Ubuntu Headless server that I do NOT WANT to be upgraded. How do I run "aptitude" command so I can download regular patches WITHOUT upgrading Virtual Box?

I remember or I think there is a way, like blocking that package from being touched by "aptitude" or something but can not remember ... can someone please provide some insight?

Thanks in advance,

---

### Post by joberly on 2010-03-14
The [apt_preferences]("http://linux.die.net/man/5/apt_preferences") man page may be what you're looking for.

---

### Post by Zeosa on 2010-03-15
```

echo virtualbox-3.0 hold | sudo dpkg --set-selections

```

---

