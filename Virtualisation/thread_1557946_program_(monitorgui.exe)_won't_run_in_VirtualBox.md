---
title: "program (monitorgui.exe) won't run in VirtualBox"
date: 2010-08-21
forum: Virtualisation
---

### Post by myotis on 2010-08-21
I am trying to install this program in winxp (all patches installed) running in VB 3.2.8 r64453 on Ubuntu 10.04 (all patches installed)

The program is at [http://www.esf.edu/efb/gibbs/monitor/](http://www.esf.edu/efb/gibbs/monitor/)

When I try to run the program, which seems to install OK, I am getting an error message 


"create process failed 14001

This application has failed to start because the application configuration is incorrect."

I have however now successfully installed it on a MacBook Pro running WINXP in Parallels (using the same binary that won't install here).

Anyone any suggestions on how to get this to run?

Many thanks,

Graham

---

### Post by DarthScape on 2010-08-21
Does the application utilize DirectX in any way? I know parallels is supposed to have some 3d support where virtualbox doesn't.

---

### Post by myotis on 2010-08-22
> **DarthScape said:**
> Does the application utilize DirectX in any way? I know parallels is supposed to have some 3d support where virtualbox doesn't.

Thanks, but I would think it unlikely as its a simple statistical analysis program. 

Graham

---

### Post by ubunter888 on 2010-09-03
try installing ".Net Framework", that worked for me. I had same error on a different application.

---

### Post by myotis on 2010-09-03
> **ubunter888 said:**
> try installing ".Net Framework", that worked for me. I had same error on a different application.

Thanks, I will give that a try, but at the moment, my thinkpad has decided to break :-(

Graham

---

