---
title: "Ubuntu 10.10 on Win 7/VirtualBox 4.0.6"
date: 2011-04-30
forum: Virtualisation
---

### Post by Spodgy on 2011-04-30
Hi There,

I'm running Ubuntu 10.10 on Windows 7 Home Premium with Oracle VirtualBox 4.0.6.

When I'm downloading files (e.g. System updates), I notice a 5-10 second delay when the download reaches between 98-100%, before Ubuntu moves onto the next file. 

I have Kapersky PURE running on the Win7 Host. Is this likely to be the cause? I've posted on their forum to confirm/eliminate this as the cause.

Any ideas on how best to debug this behaviour from a Ubuntu/VirtualBox perspective?

Thanks
Jim

---

### Post by CharlesA on 2011-05-01
The only thing I can figure is that it's checking the hash and whatnot to make sure the download isn't corrupted. Does it do the same thing if you use the terminal to upgrade?

---

### Post by Spodgy on 2011-05-01
Yes, I get the same behaviour from the terminal (using apt-get for instance). The hash checking is an interesting idea... would Ubuntu be doing that?

---

### Post by CharlesA on 2011-05-01
I'm not sure.

Try this: Boot off a livecd and try to install something and see if it does the same thing.

---

