---
title: "Virtualbox made sound+wireless"
date: 2008-05-10
forum: Virtualisation
---

### Post by sam123 on 2008-05-10
--Solved--

After installing virtualbox, the sound and wireless on the host system (Hardy) stopped functioning. And even after doing a complete removal of virtualbox, they haven't started. How can I get them working again? 

Ubuntu doesn't detect any sound or wireless devices. They were working perfectly before installing virtualbox.


Clicking the sound icon gives the message:
No volume control GStreamer plugins and/or devices found.

Update: Solved. Had installed the 386 version of virtualbox modules which had replaced the kernel with an older one.

---

### Post by Sirchristopher on 2008-05-19
You say you did a complete removal and that didn't fix it, but then you said you selected the wrong item with the old kernel.  How do you get the right one back?

---

### Post by agerio on 2008-05-19
Same problem here. Can you give as a step by step guide to solve it?

Thank you very much

---

### Post by Sirchristopher on 2008-05-20
I found the answer...
[http://ubuntuforums.org/showthread.php?p=4998935#post4998935]("http://ubuntuforums.org/showthread.php?p=4998935#post4998935")

---

