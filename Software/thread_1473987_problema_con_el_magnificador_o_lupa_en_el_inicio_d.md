---
title: "problema con el magnificador o lupa en el inicio de linux"
date: 2010-05-05
forum: Software
---

### Post by pcman1 on 2010-05-05
Eso es basicamente , active el magnificador que trae el inicio de sesion y se queda pegado al inicio de sesion con la pantalla dividida, la primera mitad en tamagno normal y la otra mitad con el magnificador, reinicio el sistema y se pega nuevamente al inicio, no responde el mouse ni el teclado...

No se que puedo hacer....

Gracias de antemano al que me pueda pegar una ayudita

PcMan

---

### Post by Carlos C on 2010-05-06
Hola. Más datos nos serían de utilidad, como por ejemplo la versión de Ubuntu que estás usando.

Se me ocurre que una forma, bien poco elegante, es desinstalando el paquete "gnome-mag". Tendrias que iniciar en recovery mode para hacerlo. Inicias el sistema y apretas "Esc" para ver las opciones del grub y así iniciar en esa modalidad. Luego bastaría con el comando
```
sudo apt-get remove gnome-mag
```

Nunca lo he intentado ni estoy en Gnome en este momento, así que no puedo asegurarte que funcione. Seguramente hay una forma más elegante de deshabilitar el magnificador.

Saludos.

---

### Post by ricardoreis on 2010-05-27
Gracias Carlos C sino elegante si que ha resultado efectivo

 mismo problema que pcman1 en Lucid linx

 por si le sirve a alguien, el cuadro de logeo se queda partido por la mitad pero te deja meter el pass.  al darle intro el puntero del mousse tiene que estar en la media pantalla no magnificada sino no entras, curioso no?

---

### Post by Carlos C on 2010-05-28
Lo damos por solucionado entonces?

---

