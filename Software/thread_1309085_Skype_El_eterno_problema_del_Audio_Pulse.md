---
title: "Skype El eterno problema del Audio Pulse"
date: 2009-11-01
forum: Software
---

### Post by jpoeta on 2009-11-01
Hola Amigos del Argentina Loco Team ayer me instale Karmic Koala, que realmente está increible, de clase Mundial!
Instale tambien Skype pero en las opciones de configuración de Audio 
solo aparece Pulse como opción y no me reconoce ningún Microfono.
Alguien conoce de una solución o conoce de algun programa nativo en Linux que supla al skype y que tambien se pueda usar en windows?
Mi antigua solución, la que use en Jaunty no funciona en karmic lamentablemente, es por eso que quisiera saber su opinión.
Gracias de Antemano
Jorgepoeta  

El skype que uso es el beta 2.1 pero tambien proble el estable y problema es el mismo.

---

### Post by guillermolisi on 2009-11-01
Hay muchos casos reportados con problemas en el audio, algunos pocos resueltos pero no muy claramente como para que se pueda repetir el procedimiento con exito, asi que me parece que este tema sera solucionado en los proximos dias, con algun bug fix update. Be patient.

---

### Post by aledruetta on 2009-11-01
Hay una versión de Skype en los repositorios Medibuntu, creo que la static, que al menos en Jaunty, servía para superar los problemas con PulseAudio.

---

### Post by DrKenobi on 2009-11-01
> **jpoeta said:**
> Alguien conoce de una solución o conoce de algun programa nativo en Linux que supla al skype y que tambien se pueda usar en windows?

Podrias usar [Ekiga]("http://ekiga.org/"), que hay una [version para Windows]("http://wiki.ekiga.org/index.php/Windows_Users"). En este caso no podes usar la cuenta de Skype, tenes que sacar una SIP-Address que podes conseguir [aqui]("https://www.ekiga.net/").

---

### Post by guillermolisi on 2009-11-02
> **DrKenobi said:**
> Podrias usar [Ekiga]("http://ekiga.org/"), que hay una [version para Windows]("http://wiki.ekiga.org/index.php/Windows_Users"). En este caso no podes usar la cuenta de Skype, tenes que sacar una SIP-Address que podes conseguir [aqui]("https://www.ekiga.net/").
Y quienes quieras contactar via Ekiga deberian tambien estar usando este sistema, cierto ?

---

### Post by DrKenobi on 2009-11-02
> **guillermolisi said:**
> Y quienes quieras contactar via Ekiga deberian tambien estar usando este sistema, cierto ?

Ambos deberian estar usando una SIP Address o H.323 ([link]("http://wiki.ekiga.org/index.php/Documentation#Call_a_contact")) pero no tiene que ser si o si de Ekiga.net. Pero Ekiga no es compatible con Skype.

---

### Post by jpoeta on 2009-11-03
Probe Equiga pero mi computadora tiene aun mas problemas con el que con skype el sonido es terrible y me sigue desconociendo el microfono:(
Jpoeta

---

### Post by DrKenobi on 2009-11-03
> **jpoeta said:**
> Probe Equiga pero mi computadora tiene aun mas problemas con el que con skype el sonido es terrible y me sigue desconociendo el microfono:(
Jpoeta

jpoeta lo que podes probar es usar google talk. Aqui necesitas una cuenta de gmail. Y creo que el programa que podes usar es Empathy.

Otra opcion es usar lo que usan las macs, con una cuenta de aol, y creo que tambien podes usar el Empathy.

Por experiencia de usar Mac y Aol las comunicaciones son excelentes, lo mismo que con google, pero siempre lo probe desde una mac.

---

### Post by jpmorelli on 2009-11-03
Yo uso la version 2.0 de skype y funciona, quise probar con la 2.1 beta y no me tomaba el mic asi que volvi a la 2.0
En algunos foros dicen que para la 2.1 beta antes de iniciar el programa skype tenés que poner:

sudo killall pulseaudio

y con eso algunos lo pudieron hacer funcionar bien, pero yo lo intente y nada.
Asi que por ahora sigo con mi 2.0 que funciona perfecto.

---

### Post by michi6278 on 2009-11-03
Hola!

También tengo problemas con Skype en Ubuntu 9.10 x64. Tanto en la versión estable como en la beta de Skype, sólo tengo como opción lo de Pulseaudio y el micrófono no es reconocido, al hacer la llamada de prueba no sale el sonido del micrófono.
Recuerdo que para Ubuntu 9.04 (32 bits) había encontrado una solución en internet en la que sí lograba que salga sonido por el micrófono (aunque al llamar a un TE de línea no me escuchaban o me escuchaban terriblemente cortado) y además recuerdo que en la configuración de sonido tenía varias opciones que ahora no. No pude encontrar esa modificación que había aplicado. Creo que era algo relacionado a Alsa.
Qué mal que esto no tenga ya una solución. Lamentablemente no puedo pasarme a otro soft de VOIP porque uso Skype Out. Cada vez que necesito hacer una llamada, tengo que pasarme a Windows, es muy molesto jeje.
Si alguien sabe o encuentra alguna configuración le agradecería que me pase el link, yo seguiré buscando.

):P

---

### Post by mama21mama on 2009-11-03
a si lo tengo yo y me anda perfecto:

[CENTER][IMG]http://h.imagehost.org/0214/Pantallazo-Preferencias_de_sonido.png[/IMG]

[IMG]http://a.imagehost.org/0249/Pantallazo-Opciones.png[/IMG][/CENTER]

---

### Post by DrKenobi on 2009-11-04
> **michi6278 said:**
> Hola!

También tengo problemas con Skype en Ubuntu 9.10 x64. Tanto en la versión estable como en la **beta** de Skype, sólo tengo como opción lo de Pulseaudio y el micrófono no es reconocido, al hacer la llamada de prueba no sale el sonido del micrófono.


Skype para Linux es tooooodo Beta.
No nos dan mucha bola los tipos estos.
Las versiones windows o mac son mucho mejores.

Podrias usar otr servicio para hacer llamadas a fijos.
Ekiga.net te permite hacer llamadas a fijos, no solo con skype uno puede hacer llamadas a fijos o celulares

---

### Post by aledruetta on 2009-11-04
> **DrKenobi said:**
> Skype para Linux es tooooodo Beta.
No nos dan mucha bola los tipos estos.
Las versiones windows o mac son mucho mejores.

Podrias usar otr servicio para hacer llamadas a fijos.
Ekiga.net te permite hacer llamadas a fijos, no solo con skype uno puede hacer llamadas a fijos o celulares

Anda circulando la noticia de que liberarían el código de Skype. No del protocolo, pero sí de la aplicación. Lo cual permitiría que la comunidad desarrollara una mejor aplicación para cada distribución.

Ojalá sea cierto.

---

### Post by michi6278 on 2009-11-04
> **DrKenobi said:**
> Skype para Linux es tooooodo Beta.
No nos dan mucha bola los tipos estos.
Las versiones windows o mac son mucho mejores.

Podrias usar otr servicio para hacer llamadas a fijos.
Ekiga.net te permite hacer llamadas a fijos, no solo con skype uno puede hacer llamadas a fijos o celulares

Claro pero el tema es que ya tengo pago el abono con Skype... jeje, por eso decía que estoy "atada" a este soft.
Qué mal que haya una versión Linux pero que al final sea "a medias"...

Les dejo captura de cómo sale mi hard de sonido en las preferencias de sonido. Y lo que me sale en Skype y que no tengo más opción que el Pulseaudio.

[IMG]http://img35.imageshack.us/img35/4691/pantallazo1dj.png[/IMG]
[IMG]http://img198.imageshack.us/img198/3440/pantallazo2k.png[/IMG]

):P

---

### Post by rojojuan on 2009-11-04
> **aledruetta said:**
> Hay una versión de Skype en los repositorios Medibuntu, creo que la static, que al menos en Jaunty, servía para superar los problemas con PulseAudio.

Instalé esta versión y anda de diez.

---

### Post by joshzam on 2009-11-05
Me pasó lo mismo con Karmic y Pulse y Skype y el micro...

Al instalar 'padevchooser', se solucionó todo.

Mira en Applications > Sound and Video > PulseAudio Volume Control [lo siento, lo tengo en inglés] y haz click sobre el Recording tab. Si realizas una llamada en Skype, debe salir los niveles del sonido del input (el micro). Si no, puedes cambiar el input "on the fly". Puedes mirar también en el Input Devices tab para configurar tu micro.

Espero que te funcione.

---

### Post by X-Tornado on 2009-11-16
yo en mi ubuntu 9.10 lo tenia todo en pulse (configuracion del skype no del ubutnu) y hiba el audio como el ****,micro no hiba (solo durante la llamada ,cuando colgava el pulse me detectava perfectamente el audio del micro) y al final kite todo del pulse y en mi caso (puede varriar segun tarjeta) seleccione en ves de pulse su controlador respectivo  y todo ok. Olvidate de pulse (bueno yo lod eje en lo  de LLamando ya que vi ke esto no afectava en nada, solo se cambiava audio y micro cunado cambiaba lo otro asi ek lod eje haci y no em causa problema alguno )
Ejemplo:
[IMG]http://img94.imageshack.us/img94/8250/pantallazoopcionesskypev.png[/IMG]
(como ya dije antes esto varia depende de la tarjeta)

---

### Post by omunozsj on 2010-01-20
Karmic + Skype 2.1

In Karmic, one problem is the Volume Control GUI as it don't show all the controls for the hardware, at least not for my HP 1220.

What I do, reading here & there is open a terminal and write:
% alsamixer -V all

And there, I can see and choose my "Atapi Mic" and set "Capture" to on.
Bad news is settings are forgotten each session. So I have to do it every time I do a Cold boot.

---

### Post by Tosh78 on 2010-01-20
> Karmic + Skype 2.1

In Karmic, one problem is the Volume Control GUI as it don't show all the controls for the hardware, at least not for my HP 1220.

What I do, reading here & there is open a terminal and write:
% alsamixer -V all

And there, I can see and choose my "Atapi Mic" and set "Capture" to on.
Bad news is settings are forgotten each session. So I have to do it every time I do a Cold boot.

Please, post in Spanish, as this a Spanish speakers forum. If your Spanish is not so good you can use Google Translate.

---

### Post by Kabezon on 2010-01-21
Aparentemente Skype no está mas en los repositorios de Medibuntu :( Alguien que me lo confirme? Agregué dichos repos y no me sale el paquete...

---

### Post by Kabezon on 2010-01-22
OK, como ya habían mencionado, el problema es que la versión 2.1 no reconoce los dispositivos correctamente. Busqué un poco y encontré **[COLOR="RoyalBlue"][este deb]("http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb")[/COLOR]** para Debian de la versión 2.0.0.72 y funciona perfectamente en Jaunty, por lo cual supongo que en Karmic tampoco dará problemas; lo único que tienen que hacer, una vez instalado skype, es ir a la opciones y configurar los dispositivos de sonido.

---

### Post by rojojuan on 2010-01-22
Me acabp de fijar y sí está.

> **Kabezon said:**
> Aparentemente Skype no está mas en los repositorios de Medibuntu :( Alguien que me lo confirme? Agregué dichos repos y no me sale el paquete...

---

### Post by rojojuan on 2010-01-22
Noticia fresquita: En este link 
[http://www.noticiasubuntu.com/skype-2-1-beta-2-disponible-para-descargar/](http://www.noticiasubuntu.com/skype-2-1-beta-2-disponible-para-descargar/)
 
se encuentra un comentario a la nueva versión de Skype. Refiere que soluciona algunos problemas, entre ellos el pulseaudio





> **Kabezon said:**
> OK, como ya habían mencionado, el problema es que la versión 2.1 no reconoce los dispositivos correctamente. Busqué un poco y encontré **[COLOR="RoyalBlue"][este deb]("http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb")[/COLOR]** para Debian de la versión 2.0.0.72 y funciona perfectamente en Jaunty, por lo cual supongo que en Karmic tampoco dará problemas; lo único que tienen que hacer, una vez instalado skype, es ir a la opciones y configurar los dispositivos de sonido.

---

