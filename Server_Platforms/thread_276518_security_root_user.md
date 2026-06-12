---
title: "security root user"
date: 2006-10-13
forum: Server Platforms
---

### Post by ckonrad on 2006-10-13
i was just wondering, when i type sudo -i, my terminal just goes right into root without asking me for a password, i havn't changed any of the default configs of ubuntu. Isn't sudo -i supposed to ask for a password?

---

### Post by aysiu on 2006-10-13
When you use *sudo*, you will be prompted for a password, but then you won't be prompted again for another five minutes (or fifteen--I forget the exact number).

Did you use another *sudo* command before typing in ```
sudo -i
```?

---

### Post by ckonrad on 2006-10-13
> **aysiu said:**
> When you use *sudo*, you will be prompted for a password, but then you won't be prompted again for another five minutes (or fifteen--I forget the exact number).

Did you use another *sudo* command before typing in ```
sudo -i
```?

oh ok thats probably what the issue was, i must have used a sudo earlier. I just wanted to check.

thanks

---

### Post by aysiu on 2006-10-13
You can actually [change the sudo timeout](http://ubuntuforums.org/showpost.php?p=116697&postcount=6) if you'd like--make it shorter.

---

### Post by JonahRowley on 2006-10-13
You can also type 'sudo -k' to make it reset your timestamp.  Useful if you need to leave the terminal open, but turn your back.

---

