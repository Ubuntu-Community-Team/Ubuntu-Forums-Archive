---
title: "disabling sudo"
date: 2006-07-21
forum: Server Platforms
---

### Post by markcarey on 2006-07-21
All,

I have downloaded the ubuntu 6.06 server iso, burnt it, installed it, logged in set a root password and now I wish to disable sudo.

I know that if I empty the /etc/sudoers file then sudo will no longer function, will this break anything irreprably?

Any thoughts?

Regards,

Mark Carey

---

### Post by simonn on 2006-07-21
> **markcarey said:**
> will this break anything irreprably?


Not if you keep a backup of the original sudoers file.

---

### Post by nagilum on 2006-07-22
Disabling sudo will break the graphical administration tools available in GNOME for example, but as you run a server it probably doesn't even have a GUI. It shouldn't break anything.

---

### Post by markcarey on 2006-07-22
Have even gone a step further and used;

apt-get remove --purge sudo

To fully remove sudo and all its configuration files

Also removed wpasupplicant, alsa, w3m, libasound2, linux-sound-base ..... why are these packages included on a server setup?

---

### Post by markcarey on 2006-07-22
Given that I am new to the ubuntu/debian method for packaging I also found 

dpkg -l

Very useful for listing what was installed.

---

