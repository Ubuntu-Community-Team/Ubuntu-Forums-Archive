---
title: "Problema instalando Wine"
date: 2009-04-12
forum: Software
---

### Post by ma_chro on 2009-04-12
Buenas Amigos, quise instalar Wine, se me tildó el equipo tuve que apagarlo porque no respondía a nada.
Al encenderlo funciona bien, pero no me deja entrar al Gestor de paquetes Synaptic, me tira:

[B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

Les agradecería mucho su ayuda.
Me imagino que es algo muy simple de solucionar, pero soy un usuario muy limitado de Ubuntu. Lo uso hace más de un año, pero sólo lo uso, no investigo nada.

Muchas gracias.

PD: Tengo instalada la versión 8.10

---

### Post by Air23 on 2009-04-12
Abri una terminal (Aplicaciones > Accesorios > Terminal) y ejecuta:
```
sudo dpkg --configure -a
```

---

### Post by ma_chro on 2009-04-12
Muchas gracias Air23, excelente lo tuyo.

Fuerte abrazo.

---

### Post by Air23 on 2009-04-12
De nada ;)

---

### Post by ma_chro on 2009-04-12
> **air23 said:**
> de nada ;)

l

---

