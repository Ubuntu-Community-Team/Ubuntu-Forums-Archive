---
title: "Como abrir un terminal desde una ventaa en GNOME"
date: 2009-11-03
forum: Software
---

### Post by DrKenobi on 2009-11-03
Cuando usaba xfce (en xubuntu) yo iba al lugar que queria y con boton derecho ponia "abrir un terminal aqui" (o algo parecido).

Ahora que uso gnome (ubuntu), se puede hacer eso?

---

### Post by Mauro22 on 2009-11-03
> sudo apt-get install nautilus-open-terminal

> nautilus -q


):p

---

### Post by DrKenobi on 2009-11-03
> **Mauro22 said:**
> ):p

Mauro22 gracias!!! Me hiciste un hombre feliz!! jaja

---

### Post by emiliano_raso on 2009-11-03
```
emiliano@emiliano-laptop:~$ nautilus -q

(nautilus:5177): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

```

---

### Post by DrKenobi on 2009-11-04
> **emiliano_raso said:**
> ```
emiliano@emiliano-laptop:~$ nautilus -q

(nautilus:5177): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

```

Yo cuando use  "nautilus -q" me dio un error.
Lo que hice fue presionar "ALT+F2" y ahi ejecute "nautilus" y todo empezo a andar bien

---

