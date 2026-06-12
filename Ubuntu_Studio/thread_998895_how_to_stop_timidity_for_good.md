---
title: "how to stop timidity for good"
date: 2008-12-01
forum: Ubuntu Studio
---

### Post by zettberlin on 2008-12-01
Hello,

I' d like to stop timidity from being started automatically whithout hacking the /etc/init.d - stuff by hand.

Is there an easy way (be it point and click or command line...)?

---

### Post by thorgal on 2008-12-01
install sysv-rc-conf
start it as superuser in a terminal
disable timidity
quit the script
that's all.

---

### Post by zettberlin on 2008-12-01
> **thorgal said:**
> install sysv-rc-conf


JUst exactly what I was looking for :-)

Thanks a lot :-)


strange though, why it is not installed by default / why services-admin has not got the same functionality...

---

### Post by thorgal on 2008-12-02
no idea why ...

I have a few guesses but it's just conjectural, no need to expand on this. I think you can also use some webmin tools for all sorts of sys admin tasks. It works through a web browser and is quite versatile but I'm old school and prefer using a good ol' shell :)

---

### Post by markbuntu on 2008-12-02
Boot Up Manager (bum) is good for getting rid of annoying stuff that starts at boot.

---

