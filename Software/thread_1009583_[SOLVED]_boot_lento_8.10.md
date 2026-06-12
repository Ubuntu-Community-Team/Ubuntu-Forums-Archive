---
title: "[SOLVED] boot lento 8.10"
date: 2008-12-12
forum: Software
---

### Post by sitiomatic on 2008-12-12
Hola a todos.
No se si es mi impaciencia, pero me parece muy lento el booteo de mi notebook.
Si tengo el cable de red conectado, demora 2 minutos hasta que me muestra el relojito de gnome y despues esperar que cargue todo.
Si no esta conectado el cable de red, son 3 minutos hasta ver el relojito.
Alguien me daria una mano para ver donde se demora? Que log deberia postear?
Saludos y gracias

---

### Post by sherwoodinc on 2008-12-13
Para empezar, como guía, podés instalarte el paquete **bootchart**.
En cada booteo te hace un grafico del inicio, mostrándote todos los procesos y cuánto tarda cada uno.

Los gráficos se van guardando en la carpeta **/var/log/bootchart**.

EDIT: Te subo un ejemplo de un booteo mio (40 segundos aprox), generado hoy mismo.

---

### Post by Hei Ku on 2008-12-13
Generalmente, si no tenías red tardando por timeout cuando iba a actualizar la hora. Pero eso era hace un par de versiones, no se si lo habran mejorado.
Probaste de actualizar el readahead, y esas cosas?

---

### Post by sitiomatic on 2008-12-13
Gracias por los datos.
Probe las dos cosas.
Instale bootchart pero no graba nada, el directorio /var/log/bootchart esta vacio......ademas de instalarlo hay que tocar algo mas?
Actualice el readahead (despues de leer de que se trata) pero tampoco veo grandes cambios
Algun otro tip?

---

### Post by sherwoodinc on 2008-12-13
Fijate si se te creó un archivo /var/log/bootchart.tgz o similar.
Si eso está, pero dentro de la carpeta bootchart no hay ningún archivo, se me hace que te falta instalar algo. Creo que necesita el java instalado para poder hacer los graficos...

---

### Post by DrKenobi on 2008-12-13
no es taaaan lento, mi xubuntu tarda 1 min 45 seg / 2 min para terminar todo

---

### Post by sitiomatic on 2008-12-13
Bueno algo aprendi, el bootchart funciona pero solo genera el grafico para el ultimo kernel instalado y yo no lo veia porque no es el kernel con el cual booteo.
Todavia no compile el driver del wifi para el ultimo kernel asi que booteo con uno anterior.
Con la gente que hable le bootea en menos de 1 minuto, he visto algun caso de 40 segundos, en mi caso, mas de 3 minutos cuando estas en un cafe es una eternidad, llega el cafe antes de que arranque :)

Actualizo esto que escribi hace 15 minutos.......encontre mi solucion, la posteo por si le sirve a alguien mas o quieren probarla.
Leyendo en launchpad sobre un bug de booteo lento en 8.10, un tipo posteo que hay que editar el archivo interfaces, o sea
sudo gedit /etc/network/interfaces
comentar todas las lineas con # excepto la linea que dice auto loiface lo inet loopback
No me pregunten el porque , pero luego de eso, mi booteo mejoro notablemente, menos de 1 minuto :)
Saludos

---

### Post by sherwoodinc on 2008-12-13
Interesante.
Se me ocurre que tendrías alguna definición en /etc/network/interfaces que por alguna razón enlentece la levantada de la red... capaz que algo que hace conflicto con el NetworkManager.

Por curiosidad, qué decían las líneas que tuviste que comentar?

Saludos!

---

### Post by sitiomatic on 2008-12-14
Esto hay en mi /etc/network/interfaces

auto lo
iface lo inet loopback
#iface eth0 inet dhcp
#auto eth0

---

### Post by Hei Ku on 2008-12-14
Lo único que haces con eso es evitar que la interfaz ethernet busque direccion de IP al iniciar. 
No tenés despues problemas para conectarte cuando la usas cableada?

---

### Post by sitiomatic on 2008-12-14
Ningun problema para conectar.
Yo uso wicd y conecta automaticamente al bootear si esta puesto el cable de red.
Recien probe el wifi y anda bien tambien.

---

### Post by Hei Ku on 2008-12-14
Bien entonces. Podes marcarlo como Solved nomas. :)

---

