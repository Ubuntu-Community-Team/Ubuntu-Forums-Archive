---
title: "problemas graficon con ubuntu 10.04"
date: 2010-05-19
forum: Software
---

### Post by salvadorpanich on 2010-05-19
tengo la siguiente duda con respecto a mi ubuntu: cuando lo instale sobre windows no tube ningun problema, pero cuando se ubo instalado y comence, a explorar el SO pasaron como 10 minutos y empesaron a aparecer rallas en la pantalla, como de error grafico, las letras no se distinguian los colores se despixelaban, entre otros... alguien me pueda ayudar..

PD: descargue el ubuntu 10.04 de la pagina oficial

---

### Post by Carlos C on 2010-05-19
Necesitamos más datos. Por favor escribe en el terminal el comando "lspci" y copia acá su resultado.
Saludos.

---

### Post by salvadorpanich on 2010-05-21
ya miren...........
adjunto el documento que me pidieron y saque algunos pantallasos.... las imagenes ablan por si mismo...

espero sea suficiente informacion para poder diagnosticar.
:confused::confused:

---

### Post by nechus on 2010-05-25
Tengo (o más bien, "tuve") exactamente el mismo problema con Lucid en mi Acer Aspire 5738.  A veces la mitad de la pantalla se volvía puras rayas. Lo fome es que yo trataba de tomar pantallazos y las malditas rayas desaparecían.

Este Acer tiene video integrado Intel, nada especial, así que no entiendo por qué tanto problema, aunque tiempo atrás, (con Jaunty, creo) hubo problemas con gráfico de Intel y Compiz no funcionaba.

La verdad es que Lucid tampoco me gustó mucho, así que reinstalé Karmic y se acabó el problema. Además, al eliminar el menú Me en el panel de Gnome también desaparecía el ícono del volumen, y eso de los botones a la izquierda es muy incómodo porque soy diestro. Y más encima, aunque arrancaba bastante rápido, no era TANTO más que Karmic, y siempre arrancaba con una pantalla negra y alguno que otro texto, harto feo.

Así que mejor espero hasta Maverick, a ver si lo pulen otro poquito.

---

### Post by Carlos C on 2010-05-27
Primero ve si en Sistema-->Administración-->Controladores de Hardware existe algun driver disponible para tu tarjeta. Si no es así puedes intentar con los parámetros que sugieren en este thread:

[http://ubuntuforums.org/showthread.php?t=1095102](http://ubuntuforums.org/showthread.php?t=1095102)

Por supuesto para eso necesitas crear un archivo Xorg.conf. Las intrsucciones sobre cómo hacerlo las puedes ver aquí:

[http://ubuntuforums.org/showpost.php?p=8820771&postcount=7](http://ubuntuforums.org/showpost.php?p=8820771&postcount=7)

Saludos.

---

### Post by salvadorpanich on 2010-05-28
osea que... es mi pc el que tiene dramas con la compatibilidad:confused:
miren tengo una [COLOR=Red]ati radeon[/COLOR] [COLOR=Red]9000 [COLOR=Black]256(mb)[/COLOR][/COLOR].

y tengo un amigo que tiene un macintosh. y le salen las mismas rallas...

---

### Post by Carlos C on 2010-05-28
Cuéntanos si las sugerencias te sirvieron de algo.

Saludos.

---

