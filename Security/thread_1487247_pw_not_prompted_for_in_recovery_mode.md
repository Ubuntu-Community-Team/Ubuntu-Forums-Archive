---
title: "p/w not prompted for in recovery mode"
date: 2010-05-18
forum: Security
---

### Post by madtyper on 2010-05-18
I used grub to get to recovery mode (with networking) -- I think it's called netroot (??) -- but noticed I wasn't asked for a username or password. I could be mistaken ... but if not is this normal?

---

### Post by OpSecShellshock on 2010-05-18
Yes, it's the normal default setting. There's no real risk involved in leaving it as-is since you have to be physically present in order to use it.

---

### Post by CharlesA on 2010-05-18
> **OpSecShellshock said:**
> Yes, it's the normal default setting. There's no real risk involved in leaving it as-is since you have to be physically present in order to use it.

Indeed. Besides the whole deal that physical access = root access.

Not a huge deal. I think you can set a password to access the GRUB menu, but I cannot recall how you would set it with GRUB2.

---

### Post by fix_ on 2010-05-18
By default, ubuntu has empty root password. Setting root password will lead to asking password before loading root shell.
```

<snip>

```

---

### Post by cariboo on 2010-05-18
> **fix_ said:**
> By default, ubuntu has empty root password. Setting root password will lead to asking password before loading root shell.
```

<snip>

```

I edited your post, as you didn't follow the guide lines in [this]("http://ubuntuforums.org/showthread.php?t=1486138") sticky.

---

