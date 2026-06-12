---
title: "Problema con Skype Ubuntu 9"
date: 2009-06-06
forum: Software
---

### Post by josecardenasvejar on 2009-06-06
Hola!

Estoy comenzando en linux, especificamente en ubuntu 9 de 64 bits. En windows, uso un programa que me sirve mucho en mi trabajo, Skype. Logré instalarlo en Ubuntu 9, pero al llamar, escucho a quien llamo, pero no lo que yo hablo. En configuracion de sonido de skype, están todas las opciones en DEFAULT.


Tengo un pavilion dv6921la

Agradezco mucho su ayuda!;-)

):P

---

### Post by Patriciologico on 2009-06-07
¿Viste los niveles de volumen, en el control de volumen ubicado al costado del reloj?

---

### Post by josecardenasvejar on 2009-06-07
Si,   los niveles de audio están todos altos, todos activados, el docking y el internal mic. 

Me aparecen 2 dispositivos. El HDA Nvidia (alsa mixer) y el Conexant CX20561 (hermosa) (oss mixer). por defecto está la primera

Saludos

José :p

---

### Post by aledruetta on 2009-06-07
Hola José,

No sé si es tu caso, pero yo también tuve muchos problemas para hacer funcionar Skype en Ubuntu. Finalmente, lo único que me dio resultado fue instalar la versión skype-static-oss que está en los repositorios medibuntu. Supuestamente, mi problema era con Pulse Audio, y esta versión usa oss.

Ahora, el único problema que tengo es que cuando abro virtualbox, ahí deja de funcionar el audio en Skype. Pero bueno, lo que hago es anular el audio en virtualbox y ya está.

Espero que te sirva,
saludos,
Alejandro.

---

### Post by Patriciologico on 2009-06-08
[Mira este Blog]("http://www.soccio.it/michelinux/2009/05/24/perfect-skype-setup-on-dell-studio-xps-with-ubuntu-jaunty/en/") puede servir.

Saludos

---

### Post by radixs on 2009-06-08
La solución que aplique yo para que me funcionara de forma correcta Skype fue remover pulse audio, para aplicar esta solución se tipea en una terminal:

sudo apt-get remove pulseaudio

después de ello tienes que ver el control de volumen, seleccionar que la sea entrada de micrófono y no de una entrada de audio, ademas verificar que el micrófono no este silenciado.

también en la configuración de audio de skype solo dejar la configuraciones por defecto.

Nota: Un solo problema al remover pulse audio, si por esas casualidades ocupas Team Speak no volverá a funcionar, ya que necesita de pulse audio para su ejecución.

---

### Post by moreback on 2009-06-08
mmh... no es buena idea remover PulseAudio, tiene que existir otra solución mejor.

---

### Post by kamus on 2009-06-08
> **radixs said:**
> La solución que aplique yo para que me funcionara de forma correcta Skype fue remover pulse audio, para aplicar esta solución se tipea en una terminal:

sudo apt-get remove pulseaudio

después de ello tienes que ver el control de volumen, seleccionar que la sea entrada de micrófono y no de una entrada de audio, ademas verificar que el micrófono no este silenciado.

también en la configuración de audio de skype solo dejar la configuraciones por defecto.

Nota: Un solo problema al remover pulse audio, si por esas casualidades ocupas Team Speak no volverá a funcionar, ya que necesita de pulse audio para su ejecución.

Yo no recomendaria remover pulse audio a primera ni ultima instancia. Simplemente si no te funciona, no lo ocupas :P. 

Te recomiendo antes de empezar a llamar, ejecutar el asistente de configuracion de audio y video de skype, con esto podras depurar y ver en que estas fallando exactamente. Ha todo esto que version de Skype estas ocupando? almenos yo tengo la 2.0 y solo tuve un problema con el audio de mi microfono que lo solucione dentro de las mismas opciones de audio Skype.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=116926&stc=1&d=1244493267[/IMG]

---

### Post by josecardenasvejar on 2009-06-08
Tengo la versión de skype 2.0. Pero acabo de reiniciar mi pc y me inicia en modo silencioso, cosa que no pasaba antes uff

Saludos

---

### Post by aledruetta on 2009-06-08
No quiero ser pesado, pero les aseguro que hice de todo para hacer funcionar Skype, y lo único que funcionó fue el paquete de medibuntu. Es cuestión de probar y ver.

Lo que no tengo idea es si ese paquete viene para la arquitectura de 64 bits.

Saludos,
Alejandro.

---

### Post by radixs on 2009-06-08
> **aledruetta said:**
> No quiero ser pesado, pero les aseguro que hice de todo para hacer funcionar Skype, y lo único que funcionó fue el paquete de medibuntu. Es cuestión de probar y ver.

Lo que no tengo idea es si ese paquete viene para la arquitectura de 64 bits.

Saludos,
Alejandro.

Yo estoy ocupando Jaunty en x64 y te dire que lo instale desde los repositorios de medibuntu y funciona sin ningun problema en jaunty x64, pero insisto, yo tengo que remover pulse audio para que funcione correctamente ya sea en 32bits o 64 bits

---

### Post by aledruetta on 2009-06-10
> **radixs said:**
> Yo estoy ocupando Jaunty en x64 y te dire que lo instale desde los repositorios de medibuntu y funciona sin ningun problema en jaunty x64, pero insisto, yo tengo que remover pulse audio para que funcione correctamente ya sea en 32bits o 64 bits

¿Pero estás seguro que instalaste la versión oss? (skype-static-oss), porque es esa la que, al no usar pulse audio, resuelve el problema. Y creo que son tres las versiones que están en medibuntu. 

Saludos, 
Alejandro.

---

### Post by giov on 2009-06-11
Les cuento mi historia.
Baje el deb de la web oficial de skype y lo instale   biennn
pero al probarlo con las opciones de audio en default nunca me funciono, por lo que tuve que porbar una a una las opciones que entrega, en eso pille que las primeras de cada una funcionan perfectamente, no se si les puede ayudar pero a mi caso las opciones en default nunca me funcionaron, no se que pasa...    pero a mi caso le funciono...


Para quien kiera puede probarlo asi solo se va a perder un poco de tiempo si no funciona, pero si funciona ya saben lo que ganan 
Giov

---

### Post by nopersona on 2009-06-11
> **giov said:**
> Les cuento mi historia.
Baje el deb de la web oficial de skype y lo instale   biennn
pero al probarlo con las opciones de audio en default nunca me funciono, por lo que tuve que porbar una a una las opciones que entrega, en eso pille que las primeras de cada una funcionan perfectamente, no se si les puede ayudar pero a mi caso las opciones en default nunca me funcionaron, no se que pasa...    pero a mi caso le funciono...


Para quien kiera puede probarlo asi solo se va a perder un poco de tiempo si no funciona, pero si funciona ya saben lo que ganan 
Giov

Tema solucionado?  que el autor edite el titulo.

---

### Post by giov on 2009-06-11
> **nopersona said:**
> Tema solucionado?  que el autor edite el titulo.

Ojo que no era yo el del problema   yo solo conte que ocurrio en mi caso

---

