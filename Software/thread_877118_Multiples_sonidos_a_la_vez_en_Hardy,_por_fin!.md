---
title: "Multiples sonidos a la vez en Hardy, por fin!"
date: 2008-08-01
forum: Software
---

### Post by atari130xe on 2008-08-01
Gente buscando buscando encontré este post para poder (finalmente) escuchar múltiples sonidos en Ubuntu Hardy.

[http://ubuntuforums.org/showthread.php?t=843012&highlight=multiple+sounds]("http://ubuntuforums.org/showthread.php?t=843012&highlight=multiple+sounds")

Probé con cuanto post encontré y no habia caso, inclusive yo mismo habia posteado una "solución" a medias porque arruinaba el sonido en las aplicaciones que corria con Wine.

Esta solución se basa en retrotraer el sistema de sonido a la configuracion de Ubuntu 7.10 (eliminando PulseAudio e instalando ESD) seguí al pié de la letra el thread y ahora estoy más que feliz escuchando TODO a la vez sin que se me "cuelgue" ninguna aplicación o me diga "resourse is busy". Entiendo que no es la mejor solución pero por el momento a mi al menos no me sirve PulseAudio hasta que esté más "maduro" o realmente las cosas funcionen mejor.


ESTA es la parte del thread que utilicé:

> These are the steps to configure 8.04 the same way as 7.10:

   1. In System-->Preferences-->Sound, set all devices to ALSA (instead of Autodetect). Disable system sounds but leave software mixing enabled.
   2. In Synaptic, mark "esound" for installation and "pulseaudio" for removal. "pulseaudio-esound-compat" and "ubuntu-desktop" will automatically be marked for removal as well. Apply the changes.
   3. Reboot.

   1. En Sistema-->Preferencias-->Sonido, elegir ALSA en todas las opciones (en lugar de autodetectar). Deshabilitar "sonidos del sistema" pero dejar habilitado "mezcla por software".
   2. En Synaptic, marcar "esound" para ser instalado y "pulseaudio" para remover. "pulseaudio-esound-compat" y "ubuntu-desktop" quedarán automáticamente marcados para su desinstalación. aplicar los cambios.
   3. Reiniciar

( y disfrutar....) 


Nota: si tenias PulseAudio seguramente en casos como Audacious tendrás que cambiar el plugin de reproducción en las preferencias: Cambiar PulseaAudio por ALSA y así con otras aplicaciones que requieran elegir el plugin de salida.

Solo me resta ahora solucionar el problema de flash player y las "Ñ's" y acéntos.

Toy contento!!! :lolflag:

---

### Post by pol666 on 2008-08-01
posta no te sirve pulceaudio? yo desder que entendi como usarlo es la mejor invencion del mundo nada de asound.conf ni esd.conf :D 

Igual gracias,  4 meses atras me hubiera servido

---

### Post by atari130xe on 2008-08-01
> **pol666 said:**
> posta no te sirve pulceaudio? yo desder que entendi como usarlo es la mejor invencion del mundo nada de asound.conf ni esd.conf :D 

Igual gracias,  4 meses atras me hubiera servido

Creeme intentè de todo, lo que encontraba lo probaba (asi re instale el sistema como 15 veces) pero nada me sirvio por eso al menos ahora funciona perfecto.

---

### Post by pol666 on 2008-08-02
y que placa tenes?

---

### Post by atari130xe on 2008-08-02
> **pol666 said:**
> y que placa tenes?

Genius Soundmaker value 5.1 PCI pero si vieras las cosas que probe solo una tuve suerte que logre escuchar todo pero ese tipo de arreglo me arruinaba el sonido en Wine (lo advertian), en el mother tengo una integrada de 8 canales de audio que en XP y con sus drivers funcan muy bien pero en Ubuntu me pasa lo mismo que con la PCI pero con un agregado, como el sistema me lo toma como USB la mayor parte de los programas (juegos, etc.) no funcionan asi que bueno...

---

### Post by Miki_Loz on 2008-08-28
Como funcione, vamos, te pinto un cuadro presidencial:guitar::lolflag:

---

### Post by atari130xe on 2008-08-29
Pinte nomàs a mi funciona en 3 pc`s jejeje hay una cosa por pulir con las pc que tienen mas de un usuario pero ya posteè la pregunta veremos como solucionamos el pequeño inconveniente :)

PD: el cuadro con marco de madera y haciendo click aca mismo en la medallita que hay abajo a la derecha jejeje ("thanks") :lolflag:

No te olvides de destildar "sonidos del sistema" en preferencias ----> sonido sino se te va a colgar olìmpicamente.

---

### Post by MeduZa on 2008-08-31
yo realmente nunca voy a entender este problema que tienen algunos, siempre tuve sonido a la vez por todos lados (en mi pc y en las muchas que instale ubuntu), pulseaudio a mi pc, asi como llego lo vole, porque me traia problemas y no aportaba nada nuevo que yo neceiste, estoy con ALSA como viene de fabrica, TODO me anda de 10

es raro :S

---

### Post by atari130xe on 2008-08-31
> **MeduZa said:**
> yo realmente nunca voy a entender este problema que tienen algunos, siempre tuve sonido a la vez por todos lados (en mi pc y en las muchas que instale ubuntu), pulseaudio a mi pc, asi como llego lo vole, porque me traia problemas y no aportaba nada nuevo que yo neceiste, estoy con ALSA como viene de fabrica, TODO me anda de 10

es raro :S

Sip es el problema, resulta que antes de ayer hice un post en multimedia & video acà mismo en ubuntu forums, preguntando cual o cuales son los motivos por los cuales no encuentran una "soluciòn" con el tema del sonido en Ubuntu, el porquè no se puede tener el sonido funcionando "de una" sin tener que empezar a configurar cosas elementales como el echo de hacer que 2 aplicaciones puedan sonar simultaneamente sin tener que borrar paquetes (como PulseAudio) que deberia funcionar con solo instalar en limpio la distro. Markbuntu me respondiò que no se toman el tiempo de colocar todos los paquetes y ensamblarlos de manera que funcione como debe. Me orientò un poco màs con el tema de PulseAudio y reinstalè al menos en la PC de mi Hna. a ver que onda, ahora conseguì sonidos simultaneos pero por ejemplo con Wine es un parto, o tengo sonido entrecortado con ALSA o directamente nada (ESD o OSS), es frustrante pero sigo intentandolo. En el caso de eliminar PulseAudio en mi PC pude hacer funcionar ALSA como en Gutsy (sonidos de sistema y todas las aplicaciones simultaneamente) pero en la de mi Hna. no hay caso si dejo ALSA se queda sin sonidos de sistema (se cuelga al inicio). En fin a esperar alguna soluciòn.

Este es el Link que posteè en Multimedia & Video con las respuestas que le pueden servir a otros:
[http://ubuntuforums.org/showthread.php?t=904678]("http://ubuntuforums.org/showthread.php?t=904678")

---

### Post by latencianeuronal on 2008-12-02
Pues parece que al fin se tiene una solución al problema, y es manteniendo a pulseaudio, parece que en algún tiempo se va a tener una actualización que lo componga, pero por le momento lo único que tenemos es el siguiente link (en inglés):

[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

o la versión que traduje (obvio al español y solo para 8.04... después traduzco la parte para 8.10):

[http://lagneuronal.wordpress.com/2008/12/03/solucionar-sonido-multiple-en-ubuntu/]("http://lagneuronal.wordpress.com/2008/12/03/solucionar-sonido-multiple-en-ubuntu/")

---

### Post by guisheca on 2008-12-02
Pero poniendo todo en ALSA no se solucionaba?? yo lo tenía así y funcionaba todo al mango.

---

### Post by Kabezon on 2008-12-03
Ni idea a qué se deban estos dramas. Yo uso PulseAudio porque fue la solución que encontré en su momento, y corre todo lo más bien, así que no toco más nada. Bueno, el único problema que tengo, y ni siquiera sé si sea debido al PulseAudio, es que en la última reinstalación (Intrepid me dio un gran dolor de cabeza con el video, el cual no pienso matarme en solucionar ya que con Hardy soy feliz, así que resintalé dicha versión) es que el KaraFun (programa de karaoke mediante Wine) no me funciona... Igual es rarísimo, porque antes de instalar Intrepid también tenia Hardy con PulseAudio y andaba lo más bien el KaraFun :S Ahora abre y todo pero no reproduce nada -.- Un bajón, no más viernes de Karaoke con amigos :P
> **atari130xe said:**
> Gente buscando buscando encontré este post para poder (finalmente) escuchar múltiples sonidos en Ubuntu Hardy.

[http://ubuntuforums.org/showthread.php?t=843012&highlight=multiple+sounds]("http://ubuntuforums.org/showthread.php?t=843012&highlight=multiple+sounds")
Solo me resta ahora solucionar el problema de flash player y las "Ñ's" y acéntos.

Toy contento!!! :lolflag:
Qué drama tenés con las tildes y demás caracteres? Tenés teclado ingles, por ejemplo? Si ese es el caso, yo también, y es simpe:

[QUOTE=quekabeza.blogspot.com] System > Preferences > Keyboard > Layouts y escoger US English en su variante “International (with dead keys)” y activarla. Luego, ahí mismo, vamos a Layout Options y bajo “Compose key position” seleccionamos “Right Alt is compose.” Después de hacer esto, con simplemente hacer Alt+a, e, i, o, u, n obtendremos el caracter deseado =]
[/QUOTE]

---

### Post by atari130xe on 2008-12-03
> **Kabezon said:**
> Ni idea a qué se deban estos dramas. Yo uso PulseAudio porque fue la solución que encontré en su momento, y corre todo lo más bien, así que no toco más nada. Bueno, el único problema que tengo, y ni siquiera sé si sea debido al PulseAudio, es que en la última reinstalación (Intrepid me dio un gran dolor de cabeza con el video, el cual no pienso matarme en solucionar ya que con Hardy soy feliz, así que resintalé dicha versión) es que el KaraFun (programa de karaoke mediante Wine) no me funciona... Igual es rarísimo, porque antes de instalar Intrepid también tenia Hardy con PulseAudio y andaba lo más bien el KaraFun :S Ahora abre y todo pero no reproduce nada -.- Un bajón, no más viernes de Karaoke con amigos :P

[COLOR="DarkRed"]Qué drama tenés con las tildes y demás caracteres? Tenés teclado ingles, por ejemplo? Si ese es el caso, yo también, y es simpe:
[/COLOR]

En realidad es algo que noto me pasa en TODAS las instalaciones de Ubuntu. Si entro en alguno de los tantos chats que utilizan Java (ingresando mediante firefox) , ahi es donde empiezan los problemas con los tildes y las Ñ`s o tampoco puedo "copy pastear" un texto en la ventanita donde se ingresa el texto para chatear cosa que si puedo si lo hago en XP, que serà? la menor idea, entre en Sun fui al foro posteè un thread y nada, no saben que puede ser, debo ser el ùnico "alienìgena" a quien le pasan estas cosas :p
PD: mi teclado es Genius normalito con 101 teclas (latinamericano), y me pasa con cualquiera de los 3 teclados que tengo.

---

### Post by z37a on 2008-12-04
Mil gracias, si no veía este post jamas iba a tener al audio funcionando como debe ser, jajaja, la verdad nunca me preocupe mucho pro el audio, peor ahora que lo vi ya esta solucionado y de paso aprendí algo nuevo en Ubuntu!!!

---

### Post by atari130xe on 2008-12-05
> **z37a said:**
> Mil gracias, si no veía este post jamas iba a tener al audio funcionando como debe ser, jajaja, la verdad nunca me preocupe mucho pro el audio, peor ahora que lo vi ya esta solucionado y de paso aprendí algo nuevo en Ubuntu!!!

de nada me alegro que te haya servido... la medallita al costado izquierdo, hacè un click agradecido :)

---

### Post by z37a on 2008-12-05
> **atari130xe said:**
> de nada me alegro que te haya servido... la medallita al costado izquierdo, hacè un click agradecido :)

Y bien merecida la tenes!!!!! jajajaja

Lo chistoso es que yo venia usando las cosas con diferentes drivers, en ves de alsausaba en el skype oss y en el resto pulse y asi funcaba, o sea tenia un desastre configurado el sonido, peor por que tampoco le daba importancia.

---

