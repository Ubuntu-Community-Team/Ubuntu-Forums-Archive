---
title: "Sudo &amp; password"
date: 2011-05-01
forum: Security
---

### Post by Mosabama on 2011-05-01
I added this line in visudo:

```

sam     ALL=(ALL) NOPASSWD: ALL

```

but bash still asks me for a password whenever I sudo. why?

---

### Post by EGamerHDK on 2011-05-02
I'm pretty sure that you can't change not having to enter a password. A password is mandatory for the first account you create, I believe, and also once you enter it once, you don't have to for another 15 minutes (im pretty sure I read that somewhere when reading about sudo for Natty Narwhal)

---

### Post by Lars Noodén on 2011-05-02
> **Mosabama said:**
> I added this line in visudo:

```

sam     ALL=(ALL) NOPASSWD: ALL

```

but bash still asks me for a password whenever I sudo. why?

That's' the right syntax so it should work.  (Whether it's a good idea is a separate topic.  I'd say the proposed settings are unsafe.)  What are you typing in bash, and as which user?  The above will only work for the user 'sam'

---

### Post by Mosabama on 2011-05-02
> **Lars Noodén said:**
> That's' the right syntax so it should work.  (Whether it's a good idea is a separate topic.  I'd say the proposed settings are unsafe.)  What are you typing in bash, and as which user?  The above will only work for the user 'sam'

yes, I only want it to work for sam !!

I am typing something like:

sudo hddtemp /dev/sda

---

### Post by Mosabama on 2011-05-02
> **EGamerHDK said:**
> I'm pretty sure that you can't change not having to enter a password. A password is mandatory for the first account you create, I believe, and also once you enter it once, you don't have to for another 15 minutes (im pretty sure I read that somewhere when reading about sudo for Natty Narwhal)

I used to do it in 10.10, it used to work

---

### Post by cariboo on 2011-05-02
Usually you have to log out and back in again for the change to take affect

---

### Post by sisco311 on 2011-05-02
sudo reads the sudoers file and applies permissions in order from top to bottom. The last line in the file will overwrite any previous conflict with the config settings. So if your user is in the admin group, you have to put the line after the **%admin	ALL=(ALL) ALL** line.

Also sudo reads the sudoers file each time it's invoked, so you don't have to log out and log back in.

---

### Post by Mosabama on 2011-05-02
> **sisco311 said:**
> sudo reads the sudoers file and applies permissions in order from top to bottom. The last line in the file will overwrite any previous conflict with the config settings. So if your user is in the admin group, you have to put the line after the **%admin	ALL=(ALL) ALL** line.

Also sudo reads the sudoers file each time it's invoked, so you don't have to log out and log back in.

Thanks it works now :)
you are the man :) :)

---

### Post by Mosabama on 2011-05-02
one question though,

is sam in the admin group? when I check etc/group file. I dont see that sam is in the group admins !!

---

### Post by Mosabama on 2011-05-02
Ops sorry .. it is.

---

