---
title: "Ayuda con Blender..."
date: 2009-10-09
forum: Software
---

### Post by Mr-Judo on 2009-10-09
Tengo una noteboock HP Compaq 515 (Athlon x2 QL64 - 3 gb ram - video Ati hd3200), con ubuntu 8.04 (harby). El tema es que por medio de la aplicacion "Añadir y quitar aplicaciones" instale el programa Blender, resulta que cuando lo ejecuto el programa pareciera que se tilda y cuando muevo el puntero del mouse se inercala con la imagen del escritorio. No se bien como decirlo, pero la cuestion es que el programa no permanece estable ni en pantalla completa ni en una ventana. 
Sera que no es compatible con Gnome?
Sera que mi placa ATI no es compatible?
O al hard mi noteboock no le da el cuero para correr este programa, cosa que me parece un poco rara?

---

### Post by pablo.s on 2009-10-09
Verificá si la aceleración
3D está efectivamente activada.
Podés comprobarlo mediante
el comando
```
glxgears
```
y si los engranajes se mueven
de manera fluida, significa que si.

---

### Post by Mr-Judo on 2009-10-11
si ejecuto ese comando y efectivanmente los engranajes se mueven sin problemas...

---

### Post by pol666 on 2009-10-11
Desactiva los efectos de escritorio antes de correr el programa y  si sigue sucediendo lo mismo, correlo en una terminal y copia la salida.

---

