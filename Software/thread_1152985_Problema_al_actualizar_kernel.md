---
title: "Problema al actualizar kernel"
date: 2009-05-08
forum: Software
---

### Post by Kernel Loco on 2009-05-08
Buenas,
Desde que actualicé al nuevo kernel (desde la barra de actualizaciones), mi driver de nVidia se fue al demonio. Traté de reinstalarlo y me dice que "No hay un driver para su kernel precompilado..."
Ahora el asunto es;
a) ¿Puedo volver al kernel viejo?
b) ¿Como se hace para precompilar el kernel?

Se agradeceran respuestas.

---

### Post by Hei Ku on 2009-05-08
No es que tengas que precompilar el kernel. De hecho, el kernel ya esta compilado o no te andaria. Lo que no puede hacer el instalador es compilar el driver, porque le faltan un par de archivos auxiliares de tu nuevo kernel.

Tenes que bajarte el paquete con los headers de tu kernel. De esa manera, el driver puede compilar para tu kernel en particular. N

---

### Post by Kernel Loco on 2009-05-08
Entonces, antes de instalar el driver tendría que correr este comando en una terminal (?)

```
sudo aptitude install linux-headers-$(uname -a) build-essential
```

---

### Post by Hei Ku on 2009-05-08
exactamente, con eso el instalador deberia poder compilar el driver e instalarlo.

---

### Post by Kernel Loco on 2009-05-08
Malas noticias para mi... La terminal me dijo "No se encontró el paquete linux-headers"
¿Ahora que hago?

---

### Post by Hei Ku on 2009-05-08
Fijate que no hayas puesto un espacio en headers y $(uname -a)

---

### Post by Kernel Loco on 2009-05-09
Bueno, finalmente lo pude solucionar metiendo el CD de Ubuntu 9.04 (tenía el 8.04) e instalando todos los paquetes de actualizaciones disponibles. Después, con el EnvyNG pude encontrar los drivers apropiados para mi tarjeta.
Gracias Hei Ku por la ayuda!

---

