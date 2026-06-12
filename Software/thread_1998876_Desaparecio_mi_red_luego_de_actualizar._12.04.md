---
title: "Desaparecio mi red luego de actualizar. 12.04"
date: 2012-06-07
forum: Software
---

### Post by Apipote on 2012-06-07
Hola estimados.
Luego de una actualización de rutina de mi 12.04 64bits, ya no veo mas mi red.
Borré y reinstalé samba y lo mismo. No encontré nada en la red que me ayude.
Alguna sugerencia?
Gracias.

---

### Post by euzkoarima on 2012-06-07
Se me ocurren dos pruebas

1. en una terminal ejecuta el comando
```
lspci
```
y copianos que te devuelve

2. Probá con el cd (o pendrive) de instalación, de ponerlo en modo "probar ubuntu" a ver si reconoce o no la red

Saludos,
Eduardo

---

### Post by Apipote on 2012-06-07
Juaaaaaa....!!!!!
El moco fue que tenía instalado samba 4 (una alfa que quería probar) y creo que se hizo algún tipo de conflicto.
Removí todo, reinstalé y voila...como un violín.
No instalen Samba4 !!!
Gracias.

---

