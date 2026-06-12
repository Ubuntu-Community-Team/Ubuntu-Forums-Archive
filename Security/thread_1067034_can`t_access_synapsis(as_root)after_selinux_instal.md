---
title: "can`t access synapsis(as root)after selinux install"
date: 2009-02-11
forum: Security
---

### Post by vriesdehh on 2009-02-11
After (trying) to install selinux,i can not acces synapsis and nautilus again,"E: ERROR: can not make configuratiemap /home/root/.synaptic - mkdir (2 bestand or map doesnt exist)"...

Those maps are (were)in /home/devrieshh/  and also in /root/

What to do to make the system look for those configurate files in /home/devrieshh/... or/root/
again...
or how to transfer those files to /home/root/... or /root/

Because i can not use nautilus as root either...(also with conf file in /home/devrieshh/ instead of /home/root/ ...

thanks for the advice.

for example running package pekwm

root@ubuntu:/home/devrieshh# pekwm
FAILED TO OPEN /home/root/.pekwm/config
Can't create /home/root/.pekwm directory!
Can't copy config files !
FAILED TO OPEN /home/root/.pekwm/mouse
FAILED TO OPEN /home/root/.pekwm/autoproperties
FAILED TO OPEN /home/root/.pekwm/keys
FAILED TO OPEN /home/root/.pekwm/menu
FAILED TO OPEN /home/root/.pekwm/menu
pekwm: root window unavailable, can't start!
root@ubuntu:/home/devrieshh#

---

### Post by HermanAB on 2009-02-11
You have to disable SELinux at boot-up:
[http://www.crypt.gen.nz/selinux/disable_selinux.htmlhttp://www.crypt.gen.nz/selinux/disable_selinux.html](http://www.crypt.gen.nz/selinux/disable_selinux.htmlhttp://www.crypt.gen.nz/selinux/disable_selinux.html)

Cheers,

Herman

---

