---
title: "No puedo instalar ubuntu (Ayuda)"
date: 2009-03-09
forum: Venezuela Team
---

### Post by pablocerg on 2009-03-09
Hola, tengo el mismo problema que cuando quise iniciar por el modo para probarlo, cuando termina de cargar el inicio (que esta el logo, al lado dice ubuntu y abajo una barra de carga) mi monitor pareciera que se apagara pero antes dice "OUT OF RANGE", ya probe con F6 y seleccionar "noapic nolapic" y no funcionó, tambien probe intentando bajar la resolucion con "ctrl" "alt" "-"

Puede ser que si espero luego ingrese a ubuntu?
porque lei que la pantalla de entrada es de resolucion 800*600 y descudrada pero que cuando ingresa al escritorio cambia a 1024*768

La version de ubuntu que intento instalar es la 8.10
Y mi placa aceleradora de video es Nvidia GeForce 8400GS

Si necesitan otro dato para poder darme una ayuda enseguida voy a responder

---

### Post by Patriciologico on 2009-06-07
Para ese problema se puede probar cambiar la resolucion (creo que es con F4) o iniciar con Safe Mode (todo esto lo digo de memoria) pero se trata de ver la resolucion correcta o iniciar con graficos en modo seguro.

Saludos

---

### Post by CdK1 on 2009-06-09
Yo que tú reinicio en Safe Mode y deshabilito todo lo que tenga que ver con la resolución... dejarla por defecto... y si te funciona, bueno ya sabes cual es el error, a todo esto, eso pasa cuando vas a levantar X? si es asi, reinicia en Safe Mode, y cambia en tu xorg.conf "nvidia" por "nv"

---

