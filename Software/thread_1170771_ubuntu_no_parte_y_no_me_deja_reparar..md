---
title: "ubuntu no parte y no me deja reparar."
date: 2009-05-26
forum: Software
---

### Post by vampireline on 2009-05-26
Ayer apague ubuntu 9.04 como de cotumbre y hoy al prenderlo en la parte cunado carga sale:
"unclean shutdown, checking drives
 /dev/sdb1       .................... "

pero cunado llega a 90% tira un mensaje de que no puede seguir y un error, luego sale para que ponga lineas e codigo..:

[[IMG]http://img154.imageshack.us/img154/751/ubuntu005.th.jpg[/IMG]](http://img154.imageshack.us/my.php?image=ubuntu005.jpg)

pongo lo que me pide "fsck" pero luego de empezar tira un error de que no puede seguir...

que sera?...murio mi ubuntu?

---

### Post by Carlos C on 2009-05-26
Te sugiero que inicies una sesión desde el livecd. Como la partición que te da problemas es /dev/sdb1 prueba escribiendo en el terminal:
```
e2fsck /deb/sdb1
```

---

### Post by vampireline on 2009-05-29
no me funciono eso que dijiste....me parece que murio ubuntu.

update: Ahora partió lo mas bien SOLO, sin hacerle nada...plop...no  si funciona cuando quiere.

---

### Post by Carlos C on 2009-05-29
> **vampireline said:**
> no me funciono eso que dijiste....me parece que murio ubuntu.

update: Ahora partió lo mas bien SOLO, sin hacerle nada...plop...no  si funciona cuando quiere.
Tendrías que ser un poco más específico cuando te refieres a que no te funcionó ¿Qué fue lo que falló? ¿El comando te dio un error? ¿No encontró nada? Si no dices qué está pasando es imposible avanzar con el problema.

Saludos.

---

