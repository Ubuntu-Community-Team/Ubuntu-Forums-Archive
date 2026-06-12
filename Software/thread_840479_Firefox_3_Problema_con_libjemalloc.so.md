---
title: "Firefox 3 Problema con libjemalloc.so"
date: 2008-06-25
forum: Software
---

### Post by undiaperfecto on 2008-06-25
Despues de la actualizacion de hoy de firefox 3, reinicie y nunca mas volvio a la vida.
El error que me da es el siguiente:

```
/usr/lib/firefox-3.0/firefox: error while loading shared libraries: libjemalloc.so: cannot open shared object file: No such file or directory
```

Se supone que me falta esa libreria, o es lo que deduzco, pero la trato de instalar y no la encuentra

```
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se pudo encontrar el paquete libjemalloc
```

Esto sucede si pongo libjemalloc o libjemalloc.so

Ahora me baje el Opera para no aburrirme de mientras, pero la verdad, no me gusta, es feito, extraño al zorro!!!

Mil gracias por la ayuda de siempre.

---

### Post by sdennie on 2008-06-25
libjemalloc.so es un parte de xulrunner 1.9.  Probá:

```

sudo apt-get install --reinstall xulrunner-1.9

```

---

### Post by undiaperfecto on 2008-06-25
Nada :(
No hay manera, sigue tirando el mismo error.

---

### Post by sdennie on 2008-06-25
Fijate si lo podés encontrar con:

```

locate libjemalloc

```

---

### Post by undiaperfecto on 2008-06-25
Lo encontre, pero lo copie en la carpeta /usr/lib/firefox-3.0/
pero no pasa nada 
:(

```
/usr/lib/xulrunner-1.9/libjemalloc.so
```

---

### Post by undiaperfecto on 2008-06-25
Perdon por el REPOST, pero lo solucione con esto.

```
sudo cp /usr/lib/xulrunner-1.9/libjemalloc.so /lib
```

---

### Post by konradk on 2008-06-25
Thanks, I don't really speak Spanish but this worked, I had the same problem.. thanks!

---

### Post by hofa on 2008-06-29
This helped me too, thank you very much

---

### Post by marianom on 2008-06-29
> **undiaperfecto said:**
> Perdon por el REPOST, pero lo solucione con esto.

```
sudo cp /usr/lib/xulrunner-1.9/libjemalloc.so /lib
```

La próxima vez, en vez de copiarlo podes hacer un enlace simbolico, de forma tal que si el archivo original se actualiza también lo hará en el destino donde lo necesitas.

Eso sería así (parado en /lib):

```
sudo ln /usr/lib/xulrunner-1.9/libjemalloc.so . --symbolic
```

---

