---
title: "[Problema] Parche BFS"
date: 2012-11-08
forum: Software
---

### Post by Mustaine666 on 2012-11-08
Buenas, como andan!? estoy tratando de compilar el kernel 3.6 con BFS de kolivas.. pero cuando lanzo el comando patch para parcharlo y luego compilar me tira este error

> 
sudo bzcat /home/****/patch-3.6-ck1.bz2 | patch -p1
patching file arch/powerpc/platforms/cell/spufs/sched.c
patch: **** Can't rename file /tmp/pogFAZXn to arch/powerpc/platforms/cell/spufs/sched.c : Permission denied


alguien tiene idea como lo puedo solucionar?!... desde ya gracias

---

### Post by guillermolisi on 2012-11-08
> **Mustaine666 said:**
> Buenas, como andan!? estoy tratando de compilar el kernel 3.6 con BFS de kolivas.. pero cuando lanzo el comando patch para parcharlo y luego compilar me tira este error



alguien tiene idea como lo puedo solucionar?!... desde ya gracias

Hace lo mismo pero en lugar de usar sudo simple, usa ```
sudo su
```y ejecuta el resto de la linea de comando directamente porque tu usuario ahora sea root hasta que ingreses exit para volver a tu usuario normal.

---

