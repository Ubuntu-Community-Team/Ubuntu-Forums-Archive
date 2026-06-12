---
title: "Found LKL and now I can't remove it."
date: 2010-04-07
forum: Security
---

### Post by dayv2005 on 2010-04-07
I found LKL on my computer. I need to remove it. It isn't showing up in synaptic and i can't figure out how to remove it. SUDO apt-get remove lkl tells me this. E: Couldn't find package lkl. Can anyone help me with this? Because i can't find it with the search and with google.

Thanks.

---

### Post by cariboo on 2010-04-07
Are you sure lkl is installed, go to /usr/bin, and type:

```
ls -l lkl
```

If it is installed, it should show up in a directory listing.

Now for the crucial questions, how did you install lkl? Are you the only person with admin privileges on the system? Is it your own system, or does it belong to someone else?

---

### Post by dayv2005 on 2010-04-07
ls -l lkl seems to say No such file or directory. But when i type lkl the help menu for it displays. 

No one else does have access, it might have been me from the past so i'm not too worried about people having my information i just wanted to maKE sure it was removed. Is there any other way i could check this?

---

### Post by CharlesA on 2010-04-08
apt-get purge lkl?

norly!

Try "which lkl"

---

### Post by EJeanmaire on 2010-04-08
> **dayv2005 said:**
> ls -l lkl seems to say No such file or directory. But when i type lkl the help menu for it displays. 

No one else does have access, it might have been me from the past so i'm not too worried about people having my information i just wanted to maKE sure it was removed. Is there any other way i could check this?

Sounds like a help file was left behind when you removed it.  If you want to further search for it:

```
find / -name lkl
```

---

