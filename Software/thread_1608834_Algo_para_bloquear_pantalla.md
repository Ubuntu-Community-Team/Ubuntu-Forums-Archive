---
title: "Algo para bloquear pantalla"
date: 2010-10-29
forum: Software
---

### Post by Yer Blues on 2010-10-29
hola a todos

les cuento...busco un programa para bloquear la pantalla y no cerrar sesiones asi como lo tiene windows como cuando apreta el boton de windows + L

eso! saludos

---

### Post by 3nG3ndR0 on 2010-10-29
bueno en ubuntu esta igual con la combinación Ctrl+Alt+L, o en el botón de 1/0 al lado del user dice bloquear pantalla.

---

### Post by Yer Blues on 2010-10-29
si lo intente pero no la bloquea con contraseña o a menos que no la tenga asi!

---

### Post by RafaelG on 2010-10-29
A mi el Ctrl+Alt+L me bloquea a la perfeccion!

Saludos!

---

### Post by themasterdark on 2010-10-30
Idem ctrl + alt + L sin problemas

---

### Post by moreback on 2010-10-30
A mi también me funciona. ¿Le tienes puesta contraseña a tu usuario?

---

### Post by asterix77 on 2010-10-31
Pues hay varias opciones:

1)  Click izquierdo en el panel ---->agregar al panel ----->Apagar. Una vez agregado (que aparezca el icono), click derecho del mouse y aparecen todas las opciones.

2)  Como te comentaron en los post anterioriores  Ctrl+Alt+L

3)  Confeccionar un script, y agregarlo al panel. Del tipo más o menos de la siguiente forma:

#!/bin/bash
gnome-screensaver-command --lock
sleep 5
xset dpms force off

4) Finalmente una solución muy bonita y elegante que uso (si es que posees un celular bluetooth, y por supuesto un pc o notebook también con bluetooth), consiste en instalar blueproximity que está en los repositorios, lo configuras y ya está. Con esto cada vez que te alejes por ejemplo 5 mts, en forma automática se bloqueará, y al acercarte, también en forma automática se desbloqueará.


Saludos

---

### Post by Lutho on 2010-10-31
te puedo recomendar algo de [_**Taringa**_]("http://www.taringa.net/posts/linux/6925037/Bloquea-y-desbloquea-la-pantalla-con-detector-de-presencia.html"), si es que tiene bluetooth
pudes revisar eso, es muy util sobre todo cuando no quieres que nadie ocupa tu pc o tu notebook :). Funciona.

---

### Post by RafaelG on 2010-11-02
> **Lutho said:**
> te puedo recomendar algo de [_**Taringa**_]("http://www.taringa.net/posts/linux/6925037/Bloquea-y-desbloquea-la-pantalla-con-detector-de-presencia.html"), si es que tiene bluetooth
pudes revisar eso, es muy util sobre todo cuando no quieres que nadie ocupa tu pc o tu notebook :). Funciona.


He probando lo sugerido y trabaja muy bien pero yo la verdad iria al problema raiz ya que el Ctrl+Alt+L  deberia funcionar y si no funciona entonces hay algo que no esta funcionando correctamente en la maquina del usuario por eso yo prestaria atencion a ese pequeno detalle.

Saludos!

---

### Post by asterix77 on 2010-11-04
¿Servirá lo siguiente? (no sé si aparece en todas las versiones, al menos en lucid, sí aparece)

Sistema ----->Preferencias ---->Combinación de teclas ------> Escritorio -------->Bloquear la Pantalla y verificar aquí si es que está esta combinación de teclas.

Saludos

---

