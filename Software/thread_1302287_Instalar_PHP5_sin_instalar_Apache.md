---
title: "Instalar PHP5 sin instalar Apache"
date: 2009-10-26
forum: Software
---

### Post by moFeta on 2009-10-26
Muy buenas.
Hay alguna forma de instalar php5 sin que se instale apache simultáneamente? Quiero usar otro servidor web (lighttpd) pero para instalar php5, instala como dependencia el servidor apache.
Esto es en Karmic (rc)

Gracias

---

### Post by moFeta on 2009-10-30
Bueno, al parecer alguien arreglo los paquetes.
Si buçien aún se instala Apache al instalar PHP5, se puede eliminar usando
```
sudo apt-get remove apache*
```
Hacer esto hace una semana atrás, también removía la instalación de PHP5.

Cerrado

---

