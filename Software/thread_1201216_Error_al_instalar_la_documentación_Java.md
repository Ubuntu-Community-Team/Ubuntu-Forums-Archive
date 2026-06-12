---
title: "Error al instalar la documentación Java"
date: 2009-06-30
forum: Software
---

### Post by zhelo on 2009-06-30
ya chico sinceramente me toy cansandode tanto error en ubuntu se que seguramente los esoy hichando y todo eso, crei que linux seria mas facil pero ya me canse, creo que me ire a windows....

este será mi ultimo pen-ultimo problema a tratar de resolver:

taba bajando jdk por sinapotic y me aparecio esto  (esta foto des e agregar o quitar pero eso que aparace ahi e slo mismo que me aparecio en sinaptic)
[http://i39.tinypic.com/359adtg.png](http://i39.tinypic.com/359adtg.png)


luego quise bajarlo en agregar o quitar y me aprecio lo mismo de sinaptic... puse
sudo dpkg bla bla bla bla.... y me dice press retunr para trata de nuevo pero no cacho que onda... por favor un poco ams de ayuda



desde ya gracias

---

### Post by pagondel on 2009-06-30
No soy de los q le gusta hacer referencia a mi blog, pero [Aqui esta la respuest](http://pagondel.wordpress.com/2008/11/09/howto-instalar-la-documentacion-de-java-en-ubuntu/)
Saludos!

---

### Post by Patriciologico on 2009-06-30
Ya, lo que te dice es que bajes la documentación Java actualizada desde la web de Sun, que bajo un archivo que esta en /tmp, si quieres intentarlo otra vez o abortar misión. No veo problema en eso, googlea como instalar documentación Java en Ubuntu, seria muy triste (por ti) dejar un SO por no poder hacer eso. Ah y recuerda **No coloques la imagen tan grande** que descuadras el foro ¿tienes widescreen?

Saludos!

---

### Post by Patriciologico on 2009-06-30
> **pagondel said:**
> No soy de los q le gusta hacer referencia a mi blog, pero [Aqui esta la respuest](http://pagondel.wordpress.com/2008/11/09/howto-instalar-la-documentacion-de-java-en-ubuntu/)
Saludos!

Es que cuando amerita, amerita y se agredece!

---

### Post by zhelo on 2009-07-01
[http://i43.tinypic.com/axkva0.png](http://i43.tinypic.com/axkva0.png)

hicelo que decia en el bloq del compañero

---

### Post by Carlos C on 2009-07-01
zhelo, no hiciste lo que dice en el blog de pagondel. En realidad no hiciste nada. Primero, en la imagen se puede ver el archivo en el escritorio. Por otro lado en el terminal vemos que intentas darle permisos 755 al archivo, pero lo haces desde tu ~/ y resulta que el archivo no está ahí, está en ~/Escritorio. Por eso te dice que no existe.

No se trata de copiar comandos nada más, tienes que entender lo que estás haciendo. Si no comprendes para qué sirve un comando debes buscar información en google. Hasta ahora tienes una mala experiencia con Ubuntu, pero no creo que tengas una mejor experiencia con otra distribución si no pones atención.

---

### Post by zhelo on 2009-07-01
osea que debe pober "cd Escritorio"??

---

### Post by zhelo on 2009-07-01
no puedo... me insite con dpkg...

[http://i39.tinypic.com/3145v2c.png](http://i39.tinypic.com/3145v2c.png)

---

### Post by radixs on 2009-07-01
Zhelo si fuera mala onda, te diria sabes vuelve a windows, pero esta vez no sera así. Alparecer no te ah ido tan bien con ubuntu, creo que eso es solo por no entender lo que lees, no es por mala onda pero es eso... Ademas viendo lo primeros pasos que dio pagondel y haciendo solo un copy >> paste "eso esta mal"... intenta siempre escribir lo que vez asi te daras cuenta cuando contenga errores, Ademas apreciaras lo que estas realizandol y aprenderas de mejor forma

---

### Post by zhelo on 2009-07-01
> **radixs said:**
> Zhelo si fuera mala onda, te diria sabes vuelve a windows, pero esta vez no sera así. Alparecer no te ah ido tan bien con ubuntu, creo que eso es solo por no entender lo que lees, no es por mala onda pero es eso... Ademas viendo lo primeros pasos que dio pagondel y haciendo solo un copy >> paste "eso esta mal"... intenta siempre escribir lo que vez asi te daras cuenta cuando contenga errores, Ademas apreciaras lo que estas realizandol y aprenderas de mejor forma


disculpa compañero, tienes razon, no leo.... mi error estaba en el punto antes del zip...
ahora me pasa lo siguiente


[QUOTE[COLOR=Red]]zhelo@querencia:~$ cd Escritorio
zhelo@querencia:~/Escritorio$ chmod 755 jdk-6-doc.zip 
zhelo@querencia:~/Escritorio$ sudo mv jdk-6-doc.zip /tmp
zhelo@querencia:~/Escritorio$ sudo apt-get install sun-java6-doc
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
sun-java6-doc ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
11 no instalados del todo o eliminados.
Se utilizarán 0B de espacio de disco adicional después de esta operación.
Configurando libc6 (2.9-4ubuntu6) ...

Configurando sun-java6-doc (6-13-1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6u10-docs.zip jdk-6u10-docs-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] [/COLOR]
[/quote]

se arreglo?

---

### Post by radixs on 2009-07-01
> **zhelo said:**
> disculpa compañero, tienes razon, no leo.... mi error estaba en el punto antes del zip...
ahora me pasa lo siguiente


[QUOTE[COLOR=Red]]zhelo@querencia:~$ cd Escritorio
zhelo@querencia:~/Escritorio$ chmod 755 jdk-6-doc.zip 
zhelo@querencia:~/Escritorio$ sudo mv jdk-6-doc.zip /tmp
zhelo@querencia:~/Escritorio$ sudo apt-get install sun-java6-doc
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
sun-java6-doc ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
11 no instalados del todo o eliminados.
Se utilizarán 0B de espacio de disco adicional después de esta operación.
Configurando libc6 (2.9-4ubuntu6) ...

Configurando sun-java6-doc (6-13-1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6u10-docs.zip jdk-6u10-docs-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] [/COLOR]


se arreglo?[/quote]

Segun eso ya esta instalado en su version mas reciente

---

### Post by zhelo on 2009-07-01
> **radixs said:**
> 

Segun eso ya esta instalado en su version mas reciente


y por que me sigue apareciendo eso.... trate de probrar java en la terminal sin embargo no me lo reconoce y me habla de unos hago bloqueado en /var/dkpg/lib/..... (si mal no recuerdo)... trato de autoremove y me dice que hat problemas en aqueda ruta

---

### Post by radixs on 2009-07-01
> **zhelo said:**
> y por que me sigue apareciendo eso.... trate de probrar java en la terminal sin embargo no me lo reconoce y me habla de unos hago bloqueado en /var/dkpg/lib/..... (si mal no recuerdo)... trato de autoremove y me dice que hat problemas en aqueda ruta

Si lo que quieres es correr aplicaicones java no se deberia instalar asi.....:

```
sudo aptitude install sun-java6-fonts sun-java6-jre sun-java6-plugin
```

---

### Post by zhelo on 2009-07-01
> **radixs said:**
> Si lo que quieres es correr aplicaicones java no se deberia instalar asi.....:

```
sudo aptitude install sun-java6-fonts sun-java6-jre sun-java6-plugin
```

[B]
zhelo@querencia:~$ sudo aptitude install sun-java6-fonts sun-java6-jre sun-java6-plugin
[sudo] password for zhelo: 
E: dpkg se interrumpió, debe ejecutar manualmente «sudo dpkg --configure -a» para corregir el problema. 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
E: dpkg se interrumpió, debe ejecutar manualmente «sudo dpkg --configure -a» para corregir el problema. 
zhelo@querencia:~$ [/B]

---

### Post by Patriciologico on 2009-07-01
> sudo dpkg --configure -a

Vamos Zhelo, leamos los mensajes del sistema




Saludos

---

### Post by zhelo on 2009-07-01
> **Patriciologico said:**
> Vamos Zhelo, leamos los mensajes del sistema



[U]
zhelo@querencia:~$ sudo dpkg --configure -a 
[sudo] password for zhelo: 
Configurando sun-java6-doc (6-13-1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6u10-docs.zip jdk-6u10-docs-ja.zip

(choose the non-update version if this is the first installation).
Please visit

[http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort][/U]

---

### Post by Patriciologico on 2009-07-01
Este paquete es un paquete de instalación, en realidad no contienen la 
JDK documentación. Usted necesitará ir a descargar uno de los 
archivos: 

jdk-6u10-docs.zip jdk-6u10-docs-ja.zip 

(no elija la versión de actualización si  es la primera instalación). 
Por favor, visite 

[http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/) 

ahora y descarga. El archivo debe ser propiedad de root y se copiarán 
a / tmp.

---

### Post by zhelo on 2009-07-01
> **Patriciologico said:**
> Este paquete es un paquete de instalación, en realidad no contienen la 
JDK documentación. Usted necesitará ir a descargar uno de los 
archivos: 

jdk-6u10-docs.zip jdk-6u10-docs-ja.zip 

(no elija la versión de actualización si  es la primera instalación). 
Por favor, visite 

[http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/) 

ahora y descarga. El archivo debe ser propiedad de root y se copiarán 
a / tmp.


se puede decir que todo esto es por capa 8??? y que si formateo no vuelva a ocurrir?

---

### Post by Patriciologico on 2009-07-01
Se puede decir que si formateas, el error de capa 8 no desaparece :p

Abre synaptic, ve si tienes paquetes rotos y elimanalos, luego instala lo que te dijo Radixs

---

### Post by zhelo on 2009-07-01
> **Patriciologico said:**
> Se puede decir que si formateas, el error de capa 8 no desaparece :p

Abre synaptic, ve si tienes paquetes rotos y elimanalos, luego instala lo que te dijo Radixs

[http://i43.tinypic.com/1zvrc5l.png](http://i43.tinypic.com/1zvrc5l.png)

---------------------------------------------------------------------------------------------------------------------------------------------------

entonces como puedo hacerlo bien??,usha me facina este SO y quero usarlo para siempre.... de verdad quiero.. pero he tenido tanos problemas... no se si soy yo o algo mas, no se nada, solo se que toy chato de formtaer dia por medio

---

### Post by Carlos C on 2009-07-01
zhelo, hasta ahora el error es siempre relacionado con la instalación de paquetes. Te ha ocurrido algún tipo de error al copia, mover archivos, grabar cds o cualquier actividad que tenga que ver con el uso del disco duro? Quisiera descartar una posible falla del disco duro. Si te ha fallado o te suele fallar habrá que revisarlo.

---

### Post by moreback on 2009-07-01
El error que tiene ahora es por que no ha instalado bien la documentación de Java, creo que le falta renombrar el archivo zip a como sale en el mensaje ([COLOR=Red]jdk-6u10-docs.zip[/COLOR]) y ejecutar el [B]sudo dpkg --configure -a

[/B]El renombrado se hace con **mv jdk-6-doc.zip jdk-6u10-docs.zip**

---

### Post by zhelo on 2009-07-02
nunca he copiado un disco en ubuntu si en windows y al menos no he tenido problemas con eso (una vez paso algo pero ya se soluciono), en ubuntu solo he tenido problemas con la instalacion de paquetes, ya que todos vienen rotos, al mover archivos no he tenido error...

---

### Post by Carlos C on 2009-07-02
Estoy desordenando este hilo, pido disculpas por eso, pero como ya zhelo ha abierto varios threads por el mismo problema quisiera tratar de ver qué está fallando. Por lo tanto quisiera continuar el problema que tiene a la hora de instalar los paquetes en el hilo original:

[http://ubuntuforums.org/showthread.php?t=1180999](http://ubuntuforums.org/showthread.php?t=1180999)

Zhelo, por favor, seguimos el tema de los paquetes allá y en este threads nos limitamos al problema con java.
Saludos.

---

