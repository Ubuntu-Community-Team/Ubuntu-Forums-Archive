---
title: "Samba Installation problem"
date: 2004-11-02
forum: Repositories &amp; Backports
---

### Post by Enygma on 2004-11-02
Hi, 

I tried to install samba via synaptic but there was some kind of an error during the installation. The error then appeared every time I used synaptic, even for other packages. 

I tried to completely remove samba using synaptic and I got this message:

```

invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102

```

Does anyone know how to fix this or what went wrong?

Thanks

---

### Post by kastorff on 2004-11-02
I had that too...just reloaded to make sure it wasn't something more serious. I had been playing around with stuff...figured I broke it.

---

### Post by Enygma on 2004-11-02
Bah just got it there, took a look at the symlink in /etc/rc.2/ it was pointing to /samba rather than ../init.d/samba

That did the trick.

---

### Post by xethm55 on 2004-11-27
how do you change the symlink?

---

### Post by senectus on 2004-12-21
Like this:
cd /etc/rc2.d/
ls -l
(look for the samba link and see where its pointing in this case the link name was "S91samba")
rm S91samba
ln -s /etc/init.d/samba S91samba


thats it.. after that you update the package and its happy :-D

**EDIT oh yeah and either do it as root or sudo everything..

---

### Post by FX on 2004-12-25
Bah I can't get it to work and I've tried the rm and ln -s.  :( Not sure whats going on. Even tried to removing and resinatlling and I get errors about the smylink being wrong.

---

### Post by senectus on 2004-12-25
[QUOTE=FX]Bah I can't get it to work and I've tried the rm and ln -s.  :( Not sure whats going on. Even tried to removing and resinatlling and I get errors about the smylink being wrong.[/QUOTE]

you may actually find that there are multiple broken links.. make sure you look in /etc/rc3.d/ 
as well

---

### Post by BiGBuG on 2005-03-07
[QUOTE=FX]Bah I can't get it to work and I've tried the rm and ln -s.  :( Not sure whats going on. Even tried to removing and resinatlling and I get errors about the smylink being wrong.[/QUOTE]

pay attention, correct command is

ln -s ../init.d/samba S91samba

and not

ln -s /etc/init.d/samba S91samba

This solved my issues ;)

---

