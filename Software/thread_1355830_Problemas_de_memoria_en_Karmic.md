---
title: "Problemas de memoria en Karmic"
date: 2009-12-15
forum: Software
---

### Post by leosr on 2009-12-15
Hola.
Hice una actualización de Jaunty a Karmic y todo salió bien. El problema es que se llena la memoria ram y la swap, mas precisamente cuando uso VirtualBox corriendo Win XP. La PC se pone lenta y cierra la VM sin ningún aviso. Luego de eso no vacía la swap y tengo que reiniciar la PC. En el pantallazo se pueden ver los procesos que quedan en memoria luego del cierre de VBox, hay uno que consume más de 500 mb de ram. 
Datos: Sempron 2600, 1500 mb ram, video FX5500 128mb, HD 80 gb, 512 mb swap y el resto en Root y el /home. Ah, 512 mb están asignados a la VM.
Con Jaunty nunca me pasó esto. No quisiera tener que volver a instalar Jaunty.

Saludos.

---

### Post by leosr on 2009-12-15
Por lo que pude encontrar en Google, el proceso "exe" tiene que ver con Google Chrome y Flash. Vean lo siguiente: [http://ubuntuforums.org/showthread.php?p=8418743](http://ubuntuforums.org/showthread.php?p=8418743)

En este momento estoy usando Chrome y éste proceso me está comiendo 447 mb!

---

### Post by alfplayer on 2009-12-15
En la línea de comandos se lee: tipo - extensión o tipo - plugin.

Esto hace pensar que los que empiezan con /proc/self/exe son de Google Chrome/Chromium.

Es probable que el problema sea falta de memoria, hay que tener en cuenta que el navegador consume mucha memoria (se puede ver el consumo de memoria de los procesos del navegador con el Administrador de tareas del navegador - Shift+Esc). Sumando el consumo del navegador al de la máquina virtual fácilmente sobrepasa los 1.5 GB de memoria RAM disponible en la máquina física, lo cual inevitablemente hace más lento a todo el sistema.

Además, también es posible que se esté saturando la memoria swap, que se recomienda en muchos casos veces que sea de un tamaño (por lo menos) igual al de la memoria RAM.

---

