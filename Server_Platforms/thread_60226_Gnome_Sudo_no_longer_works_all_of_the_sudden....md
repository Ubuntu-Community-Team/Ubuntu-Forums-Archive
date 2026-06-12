---
title: "Gnome Sudo no longer works all of the sudden..."
date: 2005-08-26
forum: Server Platforms
---

### Post by ZephyrXero on 2005-08-26
I don't know why, I haven't made any changes recently, but any graphical sudo logins now give me this error message:
> Failed to run <program location>:
Unable to copy the user's Xauthorization file.

I can still do sudo from the commandline but anytime I try to open synaptic or any other graphical adminstration tools it gives me this error. Any ideas as to why?

Also, on a side note...just tonight my Beep media player started acting funny as well, it won't use skins anymore...might be related, might not...but very weird.

---

### Post by ZephyrXero on 2005-08-27
Ok, now it's randomly working again...

---

### Post by ZephyrXero on 2005-08-27
Ok, I guess I spoke too soon...it's broken again. I also noticed Firefox acting a little strange when downloading a file too... this just really sucks :(  I guess as long as I can still sudo in commandline there's nothing I should really worry about right?

---

### Post by amohanty on 2005-08-27
what does:
ls -l ~/.Xauthority
return?

AM

---

### Post by ZephyrXero on 2005-08-27
-rw-------  1 zephyrxero zephyrxero 118 2005-08-27 01:08 /home/zephyrxero/.Xauthority

---

### Post by ZephyrXero on 2005-10-15
Found possible cause. It seems my ubuntu partition got full, and because I had no more room to write these kind of errors started popping up. When I deleted a few things stuff went back to normal for the most part ;)

---

