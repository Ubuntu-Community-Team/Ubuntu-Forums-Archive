---
title: "Backup"
date: 2008-06-06
forum: Software
---

### Post by Vero1 on 2008-06-06
Hola

Quiero hacer backup de mi home y otros archivos que me interesan como Documentos, Evolution, etc., porque estoy por hacer un dist-upgrade a Hardy.

Intenté usar Simple Backup Config pero al querer que el backup vaya a la partición donde tengo Debian, me rechaza diciendo: No es posible escribir en el destino seleccionado con los permisos actuales.

No sé cómo hacer para correr el programa como root porque no tiene opciones para especificar.

Por favor, alguna sugerencia de qué tengo que hacer.

Gracias.

---

### Post by Mauro22 on 2008-06-06
Correrlo con sudo desde la consola.

---

### Post by Vero1 on 2008-06-06
Mauro, ya lo intenté pero me contesta: command not found

---

### Post by Mister X on 2008-06-06
> **Vero1 said:**
> Mauro, ya lo intenté pero me contesta: command not found

```
sudo simple-backup-config  
```

si lo tenes instalado debe andar!

---

### Post by Vero1 on 2008-06-06
GRACIAS Mr.X, lo que pasa es que yo no lo puse así con guiones ni con minúsculas:oops:

Así si funciona :)

---

