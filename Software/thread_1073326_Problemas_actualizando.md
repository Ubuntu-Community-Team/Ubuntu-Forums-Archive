---
title: "Problemas actualizando"
date: 2009-02-18
forum: Software
---

### Post by DrKenobi on 2009-02-18
Actualizando el sistema me salio el erro que les subo en una jpg
¿Hago algo? ¿O lo dejo asi como esta?

---

### Post by guillermolisi on 2009-02-18
> **DrKenobi said:**
> Actualizando el sistema me salio el erro que les subo en una jpg
¿Hago algo? ¿O lo dejo asi como esta?
El error es porque estas usando un paquete llamado debian-edu que tiene dependencias sin resolver, es decir, librerias y otros componentes externos a ese paquete que el mismo necesita para funcionar y como no los encuentra, avisa con ese mensaje.
 
Por el nombre supongo que estas usando algun respositorio que es de Debian y no de Ubuntu. Podrias confirmar esto ultimo ? (podes revisar que repos estas usando a traves de Synaptic).

La recomendacion es no usar repositorios que no sean propios de la distribucion y version en uso para evitar, entre otras cosas, este tipo de inconsistencias.

---

### Post by DrKenobi on 2009-02-20
Estoy usando repositorios de Ubuntu.
Yo nunca modifique en nada mi SO, esta todo como recien instalado, no moifique nada.... Por eso me llama la atencion eso de los repositorios de Debian

---

