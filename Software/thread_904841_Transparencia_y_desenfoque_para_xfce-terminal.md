---
title: "Transparencia y desenfoque para xfce-terminal"
date: 2008-08-29
forum: Software
---

### Post by madelaki on 2008-08-29
¿Hay alguna manera de lograr transparencia real y desenfoque en la terminal de XFCE? Compiz parece no afectarla y por alguna razon no puedo encontrar ningun post o articulo que trate el tema, asi que no se por donde empezar.

---

### Post by santiagoward2000 on 2008-08-30
> **madelaki said:**
> ¿Hay alguna manera de lograr transparencia real y desenfoque en la terminal de XFCE? Compiz parece no afectarla y por alguna razon no puedo encontrar ningun post o articulo que trate el tema, asi que no se por donde empezar.

Hola!
¿Ya setiaste que el fondo sea transparente? Lo podés hacer en **Editar>Preferencias>Estilo>Fondo**. Ahí seleccionás **Fondo transparente** y listo. Si tenés Compiz (o algún otro compositor) activado te tendría que dar la transparencia real, sin tocar nada más. ¿Ya hiciste eso y no lo toma?
Suerte!

---

### Post by madelaki on 2008-09-02
Tampoco me tomes de... xfce-terminal no tiene transparencia real por defecto, simplemente muestra la parte del wallpaper sobre el que esta.

---

### Post by santiagoward2000 on 2008-09-02
> **madelaki said:**
> Tampoco me tomes de... xfce-terminal no tiene transparencia real por defecto, simplemente muestra la parte del wallpaper sobre el que esta.

Como que no? Si tenés Compiz o algún otro compositor prendido si tiene (yo puedo ver los íconos atrás de mi terminal), sino si te copia la imagen.

---

### Post by faktorqm on 2008-09-02
Claro, lo que le pasa a el es que no tiene ningun composite andando. yo no uso composite y me hace lo mismo y anda muuuuy lento. con el composite realmente es transparente. incluso si tiras una ventana atras de la terminal te sigue mostrando el fondo del escritorio... 
Yo la verdad ni idea de esas cosas eyecandy, asi que Santi te va a explicar como habilitarlo en xfce :lolflag: Salu2!!!

---

### Post by santiagoward2000 on 2008-09-02
Ah, perdón! Es que arriba decía que compiz no parece afectarlo, por lo que supuse que tenía compiz activado (que ya es un compositor).
La xfce4-terminal se fija si tenés o no algún compositor. Si tenés uno, lo usa para generar las transparencias reales. Si no, te copia la imagen del fondo.
Si no tenés compiz y querés usar el compositor de Xfce, podés prenderlo en Applicaciones>Configuración>Gestor de Configuración. Ahí vas a **Window Manager Tweaks**. Si los drivers de tu placa de video soportan transparencias, vas a tener una pestaña al final que se llama **Compositor**. Ahí lo prendés y listo, tendrías que tener la transparencia verdadera.
Suerte!

---

