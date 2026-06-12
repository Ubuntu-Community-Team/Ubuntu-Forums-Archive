---
title: "Editar &gt; Preferencias desapareció en Nautilus"
date: 2011-06-04
forum: Software
---

### Post by nechus on 2011-06-04
Hola,

Instalé Nautilus elementary en maverick, y después de instalar breadcrumbs el menú Editar > Preferencias ya no está!!!

¿Alguien sabe por qué?

---

### Post by nechus on 2011-06-04
Aquí hay una captura para que vean de qué hablo.

---

### Post by nechus on 2011-06-04
SOLUCIONADO.

A pesar de que había instalado Nautilus elementary a partir de su PPA mediante este procedimiento...


sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa

sudo apt-get update

sudo apt-get upgrade

...por alguna extraña razón Nautilus no se actualizó de 2.32.0 a 2.32.2

Se solucionó con un simple sudo apt-get install nautilus y reiniciar sesión.

---

