---
title: "setting up mail server"
date: 2006-07-03
forum: Server Platforms
---

### Post by jordans on 2006-07-03
Being new to Ubuntu I am stuck. Where do i find the postfix file main.cf?

Thanks

---

### Post by Glut on 2006-07-03
/etc/postfix

---

### Post by jordans on 2006-07-03
Ya, thats where I thought it would be but for somereason its not. I am positive it is all installed. Any ideas.

---

### Post by Glut on 2006-07-03
That's the debian/ubuntu default. Check /etc/mail, but it's unlikely. I suggest reinstalling postfix if the postfix directory is missing - you never know what else might be missing.

---

### Post by jordans on 2006-07-03
Ok, it isn't there but the file /etc/postfix excists and contains dynamicmaps.cf, postifix-files, postfix-script, sasl, master.cf, postfix-files.save, post-install. I reinstalled and still the same

---

### Post by Glut on 2006-07-03
Ok, you could either run the *dkpg-reconfigure* or same with aptitude or synaptic, or you could create your own. There should be an example: /usr/share/postfix/main.cf.dist

*edit - fixed dpkg-reconfigure*

---

### Post by jordans on 2006-07-03
Sorry , I am very very new to this, could you tell me exacly how to go about that.
thnx

---

### Post by Glut on 2006-07-03
My bad, I've also given the wrong command above, I'll edit it for future reference...

sudo dpkg-reconfigure postfix

---

### Post by jordans on 2006-07-03
I think that fixed it but i will get back to you later if it did go through. Thanks SOOO MUCH!

---

