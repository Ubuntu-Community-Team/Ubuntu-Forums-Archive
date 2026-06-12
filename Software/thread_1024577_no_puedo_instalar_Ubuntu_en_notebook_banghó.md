---
title: "no puedo instalar Ubuntu en notebook banghó"
date: 2008-12-29
forum: Software
---

### Post by musidora on 2008-12-29
Hola. Es mi primer mensaje en este foro. 
Me compré una notebook Banghó con un micro intelpentium dual core T2370. Intenté instalar la última versión de Ubuntu (que es la que tenía mi PC anterior y funcionaba perfectamente) pero...no pude. 
El cd arranca pero cualquier opción que elija ("probar ubuntu", "instalar ubuntu", "chequear integridad del cd", etc) calquier opción que elija,digo, hace que la máquina entre "en estado de coma":  la pantalla en negro, como suspendida, sin mensaje de error ni nada.

El cd está íntegro, lo probé en otra máquina y anduvo.

Alguien tiene idea de qué podría estar fallando? 
Muchas gracias
paula

---

### Post by faktorqm on 2008-12-29
Hola y bienvenida al foro. Pueden pasar varias cosas, lo primero que probaria es entrar al bios y ver si hay una opcion que se llama "HPET timer" o algo por el estilo, y activarlo/desactivarlo dependiendo cual te ande.
Si no funciona, lo segundo que probaria es poner la opcion de editar y te aparece una linea para editar un tanto precaria y agregas ahi la palabra "noapic" (sin comillas).
Si no funciona, lo tercero que probaria es poner "nolapic" (sin comillas).
Si no funciona, lo cuarto que probaria es poner "nohz" (sin comillas).
Postea que ocurre en cualquiera de los casos. Salu2!!

---

### Post by musidora on 2008-12-30
despues de mucho intentar, acabo de instalar el ubuntu 8.04 en mi máquina. fantastique! Lo que hice fue más o menos lo que me indicaste. Directamente  mandé 
"boot: live noapic nolapic" y ya.

etsoy probando que todo funcione bien, y creo que hay algún problemilla con la placa de video: tiene muy poca definición. En un ratito me voy a ocupar de esto. Muchas gracias por la respuesta!!! Postearé que pasa con la placa. paula

---

