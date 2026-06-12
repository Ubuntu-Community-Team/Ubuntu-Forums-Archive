---
title: "NOT AUTHENTICATED message in synaptic."
date: 2012-06-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-06-28
On one of my quantal installs I get this message warning me that a malicious individual can take control of my machine.

  I'm just wondering how to get rid of it. Also , I have updates in the que and wonder if it is safe to update to the new 3.5.0-2 kernel.

thanks in advance

---

### Post by fjgaude on 2012-06-28
Sounds like your WiFi link needs to be freshened. Try deleting the .ssh file in hidden home directory and see what happens when you try to connect to your router.

---

### Post by cariboo on 2012-06-28
It looks like you are missing some repository keys, have a look at [this]("http://www.howtogeek.com/72934/how-to-automatically-import-missing-gpg-keys-in-ubuntu/") article. It may solve your problem.

---

### Post by ventrical on 2012-06-28
Thanks Cariboo907.

 I went into synaptic and noticed that I had 2 ppas for unity-desktop when I was testing  precise. I just removed that and that got rid of that notification.

---

### Post by ventrical on 2012-06-28
> **fjgaude said:**
> Sounds like your WiFi link needs to be freshened. Try deleting the .ssh file in hidden home directory and see what happens when you try to connect to your router.

Thanks figaude.  The problem took place on one of my homebuilt towers (ethernet). I do a lot of testing on this one machine  with half a terabyte of space I can do a lot of multiple testings.

---

