---
title: "Problemas con sonidos del sistema en ubuntu 9.4"
date: 2009-06-30
forum: Software
---

### Post by dcorrea on 2009-06-30
Hola todos!!!
Mi Ubuntu ha funcionado bien, incluso el sonido me sale "5.1" y escucho sin problemas los MP3.
Pero los sonidos del sistema no se escuchan. Es decir, cuando inicio ubuntu, cuando lo cierro, cuando llega un correo nuevo, cuando hay que vaciar la papeleta...nada suena...
me voy a sistema->Preferencias->Sonido voy a la pestaña sonidos,,,todas las alertas y efectos de sonido estan por defecto pero no suenan....
como lo hago?
:(
Gracias por sus datos.

Otra consulta,,,,como instalo una tema de sonido despues de descargarlo???

---

### Post by kamus on 2009-06-30
> **dcorrea said:**
> Hola todos!!!
Mi Ubuntu ha funcionado bien, incluso el sonido me sale "5.1" y escucho sin problemas los MP3.
Pero los sonidos del sistema no se escuchan. Es decir, cuando inicio ubuntu, cuando lo cierro, cuando llega un correo nuevo, cuando hay que vaciar la papeleta...nada suena...
me voy a sistema->Preferencias->Sonido voy a la pestaña sonidos,,,todas las alertas y efectos de sonido estan por defecto pero no suenan....
como lo hago?
:(
Gracias por sus datos.

Otra consulta,,,,como instalo una tema de sonido despues de descargarlo???

Estimado podrías poner una captura (pantallazo) de tu configuración de audio? Ya que al parecer es solo un tema de configuración del canal de reproducción.

Saludos

---

### Post by dcorrea on 2009-06-30
ahi van las capturas.
Espero que sean las solicitadas...

[http://www.servidor-imagenes.com/show-image.php?id=ffa956151911f265c3ac2a23de0303d0](http://www.servidor-imagenes.com/show-image.php?id=ffa956151911f265c3ac2a23de0303d0)


[http://www.servidor-imagenes.com/show-image.php?id=60815aa0dcf275d52ba1b899d85c40f7](http://www.servidor-imagenes.com/show-image.php?id=60815aa0dcf275d52ba1b899d85c40f7)


...donde alojan uds. las imagenes?...no hubo caso solo pude copiar el link...
pero no pude insertar la imagen :(

---

### Post by moreback on 2009-06-30
Parece que tu tema de sonido está malo, a mi por lo menos me sale en nombre "Ubuntu" en la segunda imagen que posteaste.

---

### Post by dcorrea on 2009-06-30
> **moreback said:**
> Parece que tu tema de sonido está malo, a mi por lo menos me sale en nombre "Ubuntu" en la segunda imagen que posteaste.

...lo revise...le puse el tema Ubuntu...y sigue el problema

---

### Post by dcorrea on 2009-06-30
uff no he podido hacerlo....
lo más raro es que los MP3 y los wav suenan bien....
pero al personalizar los sonidos del sistema o probar los que vienen por defecto..suena solo ruido...un zumbido.
Y pensar que tenia mi ubuntu impeque :(
¿Es recomedable instalar todas las actualizaciones que aparecen?
creo que después de una actualización vino el fallo, porque no he instalado ningún programa recientemente...

---

### Post by kamus on 2009-06-30
> **dcorrea said:**
> ahi van las capturas.
Espero que sean las solicitadas...

[http://www.servidor-imagenes.com/show-image.php?id=ffa956151911f265c3ac2a23de0303d0](http://www.servidor-imagenes.com/show-image.php?id=ffa956151911f265c3ac2a23de0303d0)


[http://www.servidor-imagenes.com/show-image.php?id=60815aa0dcf275d52ba1b899d85c40f7](http://www.servidor-imagenes.com/show-image.php?id=60815aa0dcf275d52ba1b899d85c40f7)


...donde alojan uds. las imagenes?...no hubo caso solo pude copiar el link...
pero no pude insertar la imagen :(

Puedes adjuntarlo en el mismo foro no necesitas subir a sitios externos jeje, en la reproducción de sonidos la primera casilla presiona el boton "Probar", debería sonar un pitido, de lo contrario anda jugando con las opciones que te da hasta que escuches el sonido y luego cuenta como te fue ;)

Saludos

---

### Post by dcorrea on 2009-07-01
Ok, tendré que revisar la opción de  insertar imagenes directamente desde el foro.
Volviendo al problema de los sonidos del sistema, fui probando uno a uno las opciones de los dispositivos de sonidos. Los tengo todo en la opción PulseAudio Sound Server y sonaron todos menos la opciòn "Captura de Sonido".

Que será?

Saludos y gracias!

---

### Post by moreback on 2009-07-01
La captura de sonido no creo que suene ya que está relacionada con los micrófonos.

Por lo visto no tienes problemas en la reproducción de sonidos, así que creo que el problema es de tu tema, no está bien configurado.

Revisa el archivo de sonido para cada evento y fíjate que apunte al archivo correcto. Por ejemplo, para el tema Ubuntu, los sonidos están en el directorio /usr/share/sound/ubuntu/stereo.

Saludos!

---

### Post by dcorrea on 2009-07-01
ya, revise todo e incluso personalize algunos sonidos...
pero al intentar reproducirlos en Preferencias -> Sonidos, pestaña sonidos
suena solo ruido.
En cambio en la carpeta donde esta el archivo, este se produce sin problemas..
Estoy sin sonidos de sistema :(

---

### Post by Carlos C on 2009-07-01
Por favor verifica que esté instalado el paquete "pulseaudio-esound-compat".
Saludos.

---

### Post by dcorrea on 2009-07-01
> **Carlos C said:**
> Por favor verifica que esté instalado el paquete "pulseaudio-esound-compat".
Saludos.

No, no esta instalado lo verifique a traves de synaptic...
lo instalo?
me salen dos. el otro se llama igual pero termina en -dbg

---

### Post by Carlos C on 2009-07-01
Si, instala ese paquete. El que tiene "dbg" en el nombre no es necesario que lo instales.
Saludos.

---

### Post by moreback on 2009-07-01
Yo revisaría si tiene instalado el paquete **gstreamer0.10-plugins-ugly** también.

Saludos.

---

### Post by dcorrea on 2009-07-01
instale el primer paquete "pulseaudio-esound-compat" y nada
...reinstale el segundo paquete "gstreamer0.10-plugins-ugly"  y nada...

:(

---

### Post by kamus on 2009-07-01
> **dcorrea said:**
> instale el primer paquete "pulseaudio-esound-compat" y nada
...reinstale el segundo paquete "gstreamer0.10-plugins-ugly"  y nada...

:(

Probaste jugando con las opciones de reproduccion de sonido, en el menu de configuracion de audio?

---

### Post by dcorrea on 2009-07-14
...sigo con el problema...
:(
seguire buscando...

---

