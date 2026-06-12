---
title: "HELP! LVM botched on server"
date: 2010-10-20
forum: Server Platforms
---

### Post by clegends on 2010-10-20
Hi folks, I've managed to stuff up the install on my server by trying to extend my LVM /home partition. After unmounting my /home partition, I ran:
```

#/:lvextend -L +20G /home/CuriousInstall/home
Extending logical volume home to 49.62 GiB
device-mapper: resume ioctl: Invalid Argument
Unable to resume CuriousInstall/home (251:6)
Logical volume home successfully resized
#/:

```

Then I rebooted. The only way I can bootup now is if I skip mounting my /home partition, and there's no way I can mount it within the shell when I boot up. Obviously I'm not wanting to reformat & loose my data, is there another way around this?

Would appreciate your advice, I've no idea what to do. Thanks.

---

