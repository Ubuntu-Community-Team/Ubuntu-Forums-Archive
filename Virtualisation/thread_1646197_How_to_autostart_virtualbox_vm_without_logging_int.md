---
title: "How to autostart virtualbox vm without logging into kubuntu"
date: 2010-12-15
forum: Virtualisation
---

### Post by xmrkite on 2010-12-15
Hello, I am trying to be able to power up the computer and have it autostart the virtual machine.

I am able to run: VBoxManage startvm "Fileserver" --type vrdp

And it starts up the fileserver virtual machine just fine. But, this computer is not logged into, and so i want it to fire that vm up automatically in the background, all by itself.

Does anyone know how i can do that? I tried to put a script in the /etc/init.d folder, but it just doesn't seem to do it.

-Thanks

---

### Post by CharlesA on 2010-12-16
Throw it in a shell script and add it to a crontab with the @reboot time.

```
crontab -e
```

```
@reboot /path/to/script
```

The script would look something like this:

```
#1/bin/bash
VBoxHeadless -s "Fileserver"
```

---

### Post by xmrkite on 2010-12-16
Perfect. Thanks a ton

---

