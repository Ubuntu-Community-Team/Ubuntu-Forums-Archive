---
title: "Problemas para ver vídeos de YouTube embebidos"
date: 2010-06-09
forum: Software
---

### Post by mecdem on 2010-06-09
Hola amigos.

Equipos:   Toshiba Satellite A105-S4384
           Toshiba NB 105-SP2802A
           
Sistema:   Ubuntu 9.04 (32 bits)
Navegador: Mozilla Firefox

Desde hace un tiempo no puedo ver los vídeos de YouTube que están embebidos en un website. Conjeturo que ha sido a partir de alguna actualización, porque eso comenzó a suceder en la misma época en los dos equipos que menciono arriba.

En esta imagen puede verse el mensaje que arroja no bien se pide ejecutar el vídeo.

[http://picasaweb.google.com/mecdem/Botica#5480883451292624146](http://picasaweb.google.com/mecdem/Botica#5480883451292624146)

Tomo como referencia mi blog ([http://www.elblogdemec.blogspot.com/):](http://www.elblogdemec.blogspot.com/):) puedo ver bien los vídeos embebidos de TED y Vimeo. Para ver los de YouTube tengo que ir al sitio de YouTube. Lo mismo me ocurre en cualquier otro website.

Un dato: en mi blog puedo ver bien los embebidos de YouTube... con Windows :cry: (lo tengo virtualizado).

Hice alguna búsqueda en el foro ([http://ubuntuforums.org/search.php?searchid=73731087](http://ubuntuforums.org/search.php?searchid=73731087), y alguna otra consulta que no puedo reproducir ahora porque con las mismas palabras me envía al foro en inglés) pero no logro ni arrimar una solución.

Agradezco desde ya la ayuda.

---

### Post by aleperno on 2010-06-10
Como andas mecdem, a mi me pasaba exactamente lo mismo.
En mi caso era que el compiz y el flash no se llevan bien, viste aveces como son los chicos en el jardin que se pelean con por un juguetito? Algo asi

Hace lo siguiente, abri una pag con un video embebido.
apreta Alt+F2, escribi > Metacity --replace(esto desactiva el compiz)
volve a la pagina con el video embebido, dale refresh, y ahi ya vas a poder verlo (si es el caso como el mio).
Para volver a activar el compizcon > Compiz --replace alcanza.

Avisa si te funciona
saludos

---

### Post by mecdem on 2010-06-13
Hola Aleperno!!
Agradezco tu respuesta, y paso a contarte.
__________

Estas maquinitas están embrujadas.
Me puse primero con la pequeña, Toshibita.
Antes de seguir tus instrucciones, fui a mirar nuevamente los vídeos embebidos, en mi blog y en otros.
Y ¡¡milagro!! no tiraron el mensaje de error. Pero no tanta alegría: funcionan leeentos, pesadísimos, y de una manera extraña. Cliqueo en la flechita que apunta a la derecha para que inicien la reproducción y empieza el sonido, pero la imagen permanece congelada y el botoncito de arranque sigue mostrando la flecha, en vez de las dos barritas verticales. Después de un rato estas aparecen. Cliqueando, se sigue escuchando el sonido por unos segundos hasta que se decide a finalizar.
__________

Ahora vamos a las instrucciones.
Intento ejecutar Metacity --replace
No lo logro: "No se puede abrir el lugar... No existe el fichero o directorio".
Imagen del mensaje en [http://picasaweb.google.com/mecdem/Botica#5482325611184668546](http://picasaweb.google.com/mecdem/Botica#5482325611184668546)  

¿Tengo instalado ese Metacity? ¡Claro que sí!
Imagen que no me deja mentir en [http://picasaweb.google.com/mecdem/Botica#5482325627746678738](http://picasaweb.google.com/mecdem/Botica#5482325627746678738)
__________

Ahora voy a ver qué pasa en Toshiba.
Por ahora lo que vi es que los YouTube embebidos siguen tirando el mensaje de error.
Después te cuento que pasa por allí.
Hasta luego.
__________

Otra vez: muchas gracias.

---

### Post by mecdem on 2010-06-13
¡¡Toshiba y Toshibita se han complotado...!!  :evil:

Toshiba hace las mismas canalladas cuando quiero ejecutar Metacity --replace!! Tira igual mensaje y dice que no existe el fichero o directorio. Metacity está instalado.

La única diferencia es lo de la lentitud: el navegador en Toshiba anda bien, en Toshibita, como dije antes, lentíiiiisimo.

Ambas tienen 2 GB de RAM.
__________

aleperno, lamento no poder decirte "solved".

Aguardo nuevas instrucciones, que agradezco desde ya.
Un abrazo.

---

### Post by aleperno on 2010-06-13
Un detalle que me olvide.
es "metacity" si pones "Metacity" no te lo va a tomar,
si lo pones en minusculas estoy 99% seguro que te va a funcionar.
Espero que ahora si puedas decir solved :D

acordate
"metacity --replace"
y si queres volver a activar el compiz
"compiz --replace"

saludosss

---

### Post by mecdem on 2010-06-15
:(    [-(    :cry:

“Todo está como era entonces,
La casa, la calle, el río..."
Y Toshiba y Toshibita
siguen haciéndonos lío...

Aaay, mi querido Aleperno, hice exactamente lo que me indicaste:
Abrí un sitio con vídeo YouTube embebido; ejecuté metacity --replace (con la "m" minúscula funcionó); recargué la página... y todo siguió igual.
Por las dudas limpié la caché -no sé que tenga que ver, pero bueh, por las dudas-, volví a recargar... y el mensaje "an error ocurred, please try again later" siguió tozudo en su lugar. Eso en Toshiba. En Toshibita, que por cuenta propia había dejado de lanzar ese mensaje, se escucha el sonido pero continúa la imagen congelada, y además pega saltos: vuelve a atrás y reinicia el vídeo, o repite y repite tramos pequeños.

Un lío.
](*,)    :-k

¿Me darás otras instrucciones?
Las espero, y agradezco tu paciencia.

Un abrazo.

---

### Post by mecdem on 2010-07-23
...el problema es que ahora la cosa se puso peor.

Hoy hubo una actualización importante. A partir de ahí ya no pude ver los vídeos de YouTube ni embebidos ni en el sitio YouTube. Tampoco puedo ver vídeos de ningún origen en ninguna parte.

Si he mirado y entendido los mensajes, el problema está en el adobe-flashplugin. Lo he desinstalado, vuelto a instalar, con el Synaptic y con el archivo que está en Adobe para Ubuntu 9.04. Nada.

La duda ahora es:
¿Sigo la consulta aquí o en el foro de Mozilla?

Agradezco la respuesta.
Saludos.

---

### Post by mecdem on 2010-07-23
Agrego: la imagen de lo que aparece en cada espacio donde hay un vídeo, está en [http://picasaweb.google.com/mecdem/Botica#5497153655941437970](http://picasaweb.google.com/mecdem/Botica#5497153655941437970)

---

### Post by z37a on 2010-07-24
Hace la prueba de descargar la ultima versión de flash del sitio de adobe, el tar.gz, descomprimirlo y copiarlo en /usr/lib/mozilla/plugins

Me falto aclarar que todo esto desinstalando todo lo que este instalado de flash!!!

---

### Post by guillermolisi on 2010-07-25
Tuve ese problema practicamente durante todo el mes del mundial de futbol pero en una sola de las maquinas que uso y como no es algo prioritario para mi tarea diaria, lo deje sin mayor pena ni gloria hasta que un dia decidi ver por que sucedia e hice lo que recomienda z37a.

Funciono e inclusive, despues de una actualizacion de flash, siguio sin mayores problemas.

El paquete que removi completamente antes de instalar el tarball de Adobe se llama flashplugin-installer. Luego de la primer actualizacion volvio todo a la normalidad, inclusive la instalacion de ese paquete.

---

### Post by mecdem on 2010-07-25
¡Cáspita! Me encuentro con las respuestas de dos caballeros, uno de ellos un Ubuntu Member... ¡¡de lujo!!

Gracias Guillermo, gracias Juan Manuel.
Paso a contarles.

Como dije por allá arriba, son dos las máquinas con el mismo problema: Toshiba y Toshibita.
_______

**_Toshibita_**
 
Elijo comenzar con Toshibita porque en ésta no descargué la última actualización, que fue la que en Toshiba agravó los "síntomas". 

Desinstalé completamente adobe-flash plugin. No había nada más que sonara a flash, y aclaro para Guillermo: el flashplugin-installer no estaba instalado.

Ya tenía descargada la ultima versión de flash del sitio de adobe, el tar.gz. Lo descomprimí y lo copié en el subdirectorio /usr/lib/mozilla*-firefox*/plugins. Indico en cursiva una diferencia de nombre con el que puso JM (espero que sea el mismo). Ese subdirectorio, previamente, estaba vacío.

No se indicó si tengo que volver a instalar el adobe-flash plugin. No lo he instalado.

_**Estado de situación**_:    :cry:

Vídeos de YouTube, embebidos en un sitio o en el propio sito de YouTube: inician el sonido por un lado, la imagen por otro. El sonido da saltitos hacia atrás, la imagen progresa lentísima y también a saltitos. En algún momento, todo se detiene y no anda más. O -por el contrario- pulsando el botón para detenerlo, sigue andando.

Vídeos de Vimeo, Ted: donde deberían estar, el espacio está en blanco.

Vídeos de Blip TV: donde deberían estar, el espacio muestra un cuadro negro.

Lector Scribd: en su lugar se ve un cuadro celeste, no se ve el texto.

Todo esto lo veo en mi blog, elblogdemec.blogspot.com, pero yendo a los sitios de donde se toman los vídeos pasa lo mismo.

**Música** (en el frame de la derecha, abajo):

R.Subirana: se escucha entrecortada.
Magnatune: se escucha normal.
Jamendo: ocurre algo extraño. Hay tres cuadros de Jamendo cada uno con una obra diferente. En este momento veo tres cuadros, pero muestran los tres la misma imagen y un mismo titulo, distintos de los que se supone que tengo enlazados.

Último: mi sito web, casanas.com.ar, se inicia con un flash (lo que me ha valido múltiples cascotazos de la comunidad :|). No se ve. Después del tiempo que tardaría en verse, entra a la página siguiente.

Una acotación: en Toshibita se inicia Firefox y durante unos minutos funciona a velocidad normal, pero luego se pone muy pesada, da una sensación como si se comiera toda la RAM (2 GB), pero si corro otra aplicación fuera de internet el desempeño es normal. No sé si tenga algo que ver, pero en la duda lo comento.
____

En otra entrada les cuento qué pasa en Toshiba.
____

Muchas gracias por la ayuda y la paciencia.
Besos.

---

### Post by guillermolisi on 2010-07-25
Mecdem, debo confesar que no tuve en cuenta que no estabas usando 10.04, por eso mi comentario sobre flashplugin.

Ya sabemos que version de Ubuntu estas usando, ahora que version de FireFox estas utilizando ?

El tarball de Flash que bajas del site de Adobe, si no recuerdo mal, tiene un instalador (shell script). Es decir, me parece que no es solo mover/copiar archivos.

OT: Por que estas con una version anterior a la 10.04 ?

---

### Post by mecdem on 2010-07-25
> **guillermolisi said:**
> Ya sabemos que version de Ubuntu estas usando, ahora que version de FireFox estas utilizando ?

Firefox 3.6.7

> El tarball de Flash que bajas del site de Adobe, si no recuerdo mal, tiene un instalador (shell script). Es decir, me parece que no es solo mover/copiar archivos.

Cuando se descomprime solo aparece un archivo, el "libflashplayer.so" y por lo que ví en el foro Mozilla Hispano, es para copiar.

> OT: Por que estas con una version anterior a la 10.04 ?

Cuando salió la versión 9.10 la instalamos en Toshibita y tenía muchos problemas con Open Office. Volví a 9.04.
____

Mañana paso info sobre Toshiba.
Gracias. Beso.

---

### Post by guillermolisi on 2010-07-26
Ok. Oportunamente, hace unas tres semanas, desinstale flashplugin y copie el archivo de flah que mencionas. Ahi comenzo a funcionar per a lospocos dias salio una actualizacion de Flash que aplique y ahi, recien, comenzo a funcionar todo normalmente.

Pase de no poder ver, a poder ver pero cuando terminaba o interrumpia el video se colgaba FFox, lo que me obligaba a matar el proceso para volver a usarlo, y luego a ver videos y seguir utilizando Ffox sin problemas.

Tambien hubo por lo menos una actualizacion de Ffox entre tanto, asi que posiblemente la solucion haya sido la combinacion de acciones.

---

### Post by z37a on 2010-07-27
Proba una cosita mas, peor mas que nada para darnmos informacion adicional.

Ingresa al firefox, en la barra de direcciones, sin www ni http ni nada de eso, coloca "about:plugins" sin las comillas, y comenta que dice en la seccion de shockwave flash player(o si no aparece esta misma!)

PD: Es " about : plugins ", pero me sale un smile y no se desactivarlo!!!

---

### Post by mecdem on 2010-07-29
> **z37a said:**
> Proba una cosita mas... Ingresa al firefox, en la barra de direcciones...

¡Eso ya lo hice!!
(Psss... ¿con quién se cree que está hablando? :D

Lo que no hice fue comentar aquí el resultado del paseo, me olvidé. Y es algo que me desconcierta.

El "aboutplugins" informa esto:
Shockwave Flash
    Archivo: libflashplayer.so
    Versión: Shockwave Flash 7.0 r69

Pero si miro en Synaptic, donde Shockwave Flash no es Shockwave Flash sino Adobe Flashplugin, dice:

adobe flashplugin 10.1.53.64-1jaunty1

La versión 10 es la que instalé y reinstalé, pero el "aboutplugins" insiste  :(  en mencionar la versión 7.

¿Eso da alguna pista?
____

> ...me sale un smile y no se desactivarlo!!!

¡¡Bueno!! Una oportunidad de hacer un pequeño aporte, aunque no sirva para la consola:

Debajo del form para postear, hay un título grandote, en rojo, "Additional Options", en cuyo primer cuadro "Miscellaneous Options" hay tres casillas de opción.
La tercera dice "Disable smilies in text".
____

Sigo en mi lucha con las TICs
Gracias. Abrazo.

---

### Post by mama21mama on 2010-07-29
en youtube podes usar [html5]("http://www.youtube.com/html5") y abajo de todo habilitas html5 y le dices chauuuuu a adobe :D

Si no te funciona eso te bajas el firefox 3.6.8 de la web oficial
y lo colocas en /opt/firefox


luego editas en el panel el icono del firefox y le agregas la nueva ruta

```
/opt/firefox/firefox
```


proba y me cuentas.
Saludos

---

