---
title: "kde - cargar automaticamente los discos duros al inicio"
date: 2009-01-14
forum: Software
---

### Post by tsueseres on 2009-01-14
como cargar automaticamente los discos duros al inicio, he buscado en internet pero salen cosas del kde4 ahorita tengo la version 3.5

---

### Post by Hei Ku on 2009-01-14
Desde el administrador de discos, le pones que lo monte al inicio.

---

### Post by tsueseres on 2009-01-15
> **Hei Ku said:**
> Desde el administrador de discos, le pones que lo monte al inicio.

ha ok no lo encontraba pero ya 
gracias

---

### Post by z37a on 2009-01-18
Si no modificando manualmente el fstab

```
sudo nano /etc/fstab
```

Lo unico esto con mucho cuidado!!!!

---

### Post by zeroadrenaline on 2009-01-19
Yo soy partidario de modificar /etc/fstab .
El motivo es simple,. si por algun motivo, nececitas un live cd, o no tenes el administrador de discos tan lindo que tiene kde, nececitas saber como hacerlo, y sinceramente no es para nada complicado entender como funciona fstab.
Asique si tenes un poquito de tiempo para leer, y queres aprenderlo para en el futuro no tener que postear la misma pregutna, [http://www.guia-ubuntu.org/index.php?title=Acceso_a_particiones_Windows](http://www.guia-ubuntu.org/index.php?title=Acceso_a_particiones_Windows)

En este ejemplo se aclara como hacer el trabajo con particiones windows, pero es tranquilamente extendible, con algunos pequeños cambios, a particiones ext3, o de cualquier otro tipo.

---

