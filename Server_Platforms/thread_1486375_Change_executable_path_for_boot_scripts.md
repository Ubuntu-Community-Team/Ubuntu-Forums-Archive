---
title: "Change executable path for boot scripts?"
date: 2010-05-17
forum: Server Platforms
---

### Post by u-slayer on 2010-05-17
I have a startup script which calls other scripts which need to run some utilities I have. I've tried changing the executable path by adding it to .bashrc:

```

echo "PATH=\$PATH:$new_path" | tee -a /root/.bashrc /home/$user/.bashrc
echo "export PATH" | tee -a /root/.bashrc /home/$user/.bashrc
```

But this only works for finding executables once the boot process is over. The startup scripts don't see this path.:confused:

---

### Post by u-slayer on 2010-05-18
:)

---

