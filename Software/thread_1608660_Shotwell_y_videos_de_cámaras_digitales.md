---
title: "Shotwell y videos de cámaras digitales"
date: 2010-10-29
forum: Software
---

### Post by chulelinux on 2010-10-29
Me dispuse a bajar las fotos y los videos de una camara digital y di cuenta de que con shotwell solo se importaban las fotos y no así los videos. 
¿Es el funcionamiento normal de la aplicación o también tendría que bajar los videos? No encontré mayor info sobre el tema y en caso de que solo sirva para fotos ¿qué otra aplicación puedo utilizar para bajar ambas cosas? 
Slds

---

### Post by hectorivand on 2010-10-29
> **chulelinux said:**
> Me dispuse a bajar las fotos y los videos de una camara digital y di cuenta de que con shotwell solo se importaban las fotos y no así los videos. 
¿Es el funcionamiento normal de la aplicación o también tendría que bajar los videos? No encontré mayor info sobre el tema y en caso de que solo sirva para fotos ¿qué otra aplicación puedo utilizar para bajar ambas cosas? 
Slds

Shotwell más bien es para imágenes, no podes bajar los vídeos con un copiar y pegar?

Si no también podes probar con GTKam que importa vídeos también

```
sudo apt-get install gtkam
```

Saludos
Nacho

---

### Post by chulelinux on 2010-10-30
Si, si... puedo bajarlos copiando y pegando pero se hace molestísimo porque la cámara guarda las fotos o videos bajo una estructura de carpetas que te obliga a explorar un poquito bastante para encontrar cada archivo.

Aplicaremos gtkam entonces...

Slds y gracias

---

### Post by chulelinux on 2010-11-01
Consulta... instalé gtkam y me da el error de que no puede iniciar la camara. Desinstalé por las dudas shotwell y probé abrirlo como root y no pasa nada. Alguien sabe como se soluciona ese error? dejo el pantallazo de lo que me dice...

Slds

---

### Post by hectorivand on 2010-11-01
> **chulelinux said:**
> Consulta... instalé gtkam y me da el error de que no puede iniciar la camara. Desinstalé por las dudas shotwell y probé abrirlo como root y no pasa nada. Alguien sabe como se soluciona ese error? dejo el pantallazo de lo que me dice...

Slds

Según el cartel ese hay algún otro programa/proceso que te esta usando la cámara, asegúrate de no tener una ventana abierta de la memoria.

Saludos
Nacho

---

### Post by chulelinux on 2010-11-03
No hubo caso... Por monitor de sistema busqué los procesos en funcionamiento, corté los que me parecían podían estar en juego y nada. Asimismo comprobé que poniendo directamente la memoria en la pc también me tira el mismo error así que no es la cámara. Con Shotwell no pasaba esto y lo desinstalé para ver si era eso y nada. Abrí gtkam como root y nada. No se me ocurre mucho más.
Saludos

---

### Post by chulelinux on 2010-11-03
Para sumar... la verdad que es molesto el shotwell. No entiendo como el programa no permite ver también los videos de una cámara de fotos siendo algo de lo más común que se hace cuando uno quiere bajar sus archivos digitales. Además el modo de navegación y presentación por eventos que tiene es muy molesto y poco versátil.

---

### Post by guillermolisi on 2010-11-03
Parecen buenas ideas para aportarle al proyecto de Shotwell, cosa que podrias hacer suscribiendote a su lista de e-mail para dejar tus sugerencias. Mas info [aqui]("http://yorba.org/shotwell/")

---

### Post by chulelinux on 2010-11-05
Buenísimo Guillermo... después de postear me daban ganas de enviar o comentar esto como sugerencia para la aplicación y la verdad que no sabía donde y no insistí mucho tampoco. Saludos.

---

### Post by chulelinux on 2010-11-05
Sigo con los problemas al intentar bajar las fotos de la cámara. Con Gtkam seguí teniendo el mismo problema más allá de que busqué frenar todos los procesos que me parecían podían entrar en conflicto. 
1) Por otro lado, reinstalé shotwell y ahora no me anda. Me deja visualizar las fotos de la cámara pero no importarlas por el error que indica la imagen adjunta.  
[ATTACH]174657[/ATTACH]

2) Asimismo, no se que paso y cuando intento abrir una carpeta desde el menú lugares me tira el error de que "eye no encuentra ninguna imagen" (error de adjunto 2) Solo puedo entrar a mis carpetas por el menú de equipo. Ya reinstalé eye y sigue con el mismo error. Desinstalado el gestor de ventanas hace bien su trabajo.
[ATTACH]174658[/ATTACH]

3) El visor de imágenes tampoco me deja ver las imágenes de la cámara y me tira el error que adjunto en último término

Todo este lío se me armó solamente intentando hacer andar gtkam mediante la desinstalación de shotwell. Instalé y reinstalé estos dos programas y se me hizo este lío.
Si alquien me ayuda para ver por donde puedo revisar buenísimo porque la verdad que no se como solucionarlo y no encontré algo que me ayude.
Saludos

---

### Post by hectorivand on 2010-11-05
> **chulelinux said:**
> Sigo con los problemas al intentar bajar las fotos de la cámara. Con Gtkam seguí teniendo el mismo problema más allá de que busqué frenar todos los procesos que me parecían podían entrar en conflicto. 
1) Por otro lado, reinstalé shotwell y ahora no me anda. Me deja visualizar las fotos de la cámara pero no importarlas por el error que indica la imagen adjunta.  
[ATTACH]174657[/ATTACH]

2) Asimismo, no se que paso y cuando intento abrir una carpeta desde el menú lugares me tira el error de que "eye no encuentra ninguna imagen" (error de adjunto 2) Solo puedo entrar a mis carpetas por el menú de equipo. Ya reinstalé eye y sigue con el mismo error. Desinstalado el gestor de ventanas hace bien su trabajo.
[ATTACH]174658[/ATTACH]

3) El visor de imágenes tampoco me deja ver las imágenes de la cámara y me tira el error que adjunto en último término

Todo este lío se me armó solamente intentando hacer andar gtkam mediante la desinstalación de shotwell. Instalé y reinstalé estos dos programas y se me hizo este lío.
Si alquien me ayuda para ver por donde puedo revisar buenísimo porque la verdad que no se como solucionarlo y no encontré algo que me ayude.
Saludos

Proba con boletear todas las dependencias de estos programas desde Synaptic y volvelos a instalar... es raro che.

Saludos
Nacho

---

### Post by guillermolisi on 2010-11-05
> **hectorivand said:**
> Proba con boletear todas las dependencias de estos programas desde Synaptic y volvelos a instalar... es raro che.

Saludos
Nacho
Donde dice *boletear*, lease Remover Completamente :)

---

### Post by hectorivand on 2010-11-06
> **guillermolisi said:**
> Donde dice *boletear*, lease Remover Completamente :)

[ot]Perdón me sale el sicario de adentro de vez en cuando :P [/ot]

---

### Post by chulelinux on 2010-11-08
Ja ja... Nacho... esos son las instrucciones para Ubuntu Killer all no Maverick...
Removí e instalé de nuevo el gestor de imágenes y los programas y si bien shotwell volvió a andar, el error del menú lugares seguía. Reinstalé nautilus y ahí recién lo pude solucionar. Ahora, gtkam me sigue mostrando el mismo error (No se pudo listar las carpetas en '/'. Se ha producido un error en la biblioteca de entrada-salida ('No se pudo trabar el dispositivo'): La cámara ya está en uso).

y con el gestor de imágenes tampoco puedo acceder a las fotos (error: No se encontraron imágenes en «gphoto2://[usb:007,005]/).

Si alguien sabe como arreglar lo de gtkam estaría bueno. Encontré que este error lo han tenido algunos pero ninguna forma de solución. Entiendo que es un problema de montaje u otra aplicación que entra en juego pero no doy en el clavo.

Saludos y gracias.

---

### Post by chulelinux on 2010-11-08
Empecinado en solucionar este item, antes de pasar a otro, en el tránsito del camino al software libre 100 no dependiente, logré solucionar mi demanda como usuario recurriendo a otra aplicación. Comento la experiencia:

- Shotwell me anda bien ahora pero la verdad que es muy raro que no permita importar videos porque aleja a muchos usuarios, y además me parece un poco engorroso el sistema de orden que propone para su biblioteca (esto lo enviaré profundizando la explicación como sugerencia al proyecto). Sí, hay que decirlo, tiene herramientas excelentes para trabajar las fotos
- GtKam parecía por su simpleza que era lo que quería pero no lo pude hacer andar y probé todo lo que estaba al alcance de mis conocimientos.
- Luego de reinstalar y probar varias cosas leí sobre gthumb,lo instalé y zaz¡¡ era exactamente lo que buscaba. Simple, sencillo, absolutamente versátil y acomodable para organizar todo archivo audiovisual de la cámara.

Me queda saber por qué Gtkam me tiraba el error de "la cámara ya está en uso" pero pude solucionar la conectividad con la cámara de fotos. 

Gracias por la ayuda. 
Saludos

---

