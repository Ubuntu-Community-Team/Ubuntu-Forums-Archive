---
title: "Ubuntu 7.10 server question"
date: 2007-11-13
forum: Server Platforms
---

### Post by fedex1993 on 2007-11-13
okay is there anyway that after i get ubuntu LAMP server instaled can i install a desktop envirement and if i can how most likly fluxbox for the desktop envirment

---

### Post by llamakc on 2007-11-13
Yes. Just use aptitude or apt-get to grab what you want.

```

sudo apt-get install fluxbox

```

---

### Post by portalcake on 2007-11-13
You may also need to get the xorg package

---

### Post by llamakc on 2007-11-13
Huhm, I didn't recommend that b/c I made a faulty assumption that xorg would be pulled in via the package depends, but it does not.

You'd want to also install xserver-xorg-core and some of the xfonts-* packages too.

---

### Post by fedex1993 on 2007-11-13
okay i will try it and see if it works if it doesnt i will tell yall and we will try to find out the answers

---

