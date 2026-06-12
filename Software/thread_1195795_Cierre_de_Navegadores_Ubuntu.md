---
title: "Cierre de Navegadores Ubuntu"
date: 2009-06-24
forum: Software
---

### Post by AlvaroV on 2009-06-24
Me interesa saber si alguien conoce alguna solución para evitar los permanentes cierres de los navegadores (me ocurre con practicamente todos) en Ubuntu. Al parecer todo señala que tiene que ver con problemas con Flash. Es un tema que he tratado de resolver desde Dapper hasta la 9.04 pero ha sido imposible, he probado todo lo que he encontrado en la web: cambiar versiones de Flash, de navegador, etc y nada. 

De hecho ya me resigne a que durante una hora de navegación con firefox debo estar preparado para reabrir el software a lo menos unas cinco o seis veces. Y para que hablar de youtube con suerte logro ver un video y de ahi chao. Solo Opera es un poco más estable, sin embargo, tambien despues de ver un par de videos, no se cierra, pero deja de reproducirlo.

Alguien tiene alguna novedad al respecto.

---

### Post by CdK1 on 2009-06-24
La verdad tenía el mismo problema, sobre todo en amd64, hice dos cosas:

1.- Cambiar el pluggins
2.- Probar otro navegador

Conclusiones: Me corre mejor el flash en Opera, aunque ultimamente no he tenido ningún cierre con Firefox:

CdK1@Caturra:~/checkout/gnome2/jhbuild/modulesets$ dpkg -l | grep flash
ii  flashplugin-nonfree                  1:2.6                        Adobe Flash Player - browser plugin
CdK1@Caturra:~/checkout/gnome2/jhbuild/modulesets$ 

Prueba con Opera... y éste pluggins...

---

### Post by AlvaroV on 2009-06-24
> **CdK1 said:**
> 
CdK1@Caturra:~/checkout/gnome2/jhbuild/modulesets$ dpkg -l | grep flash
ii  flashplugin-nonfree                  1:2.6                        Adobe Flash Player - browser plugin
CdK1@Caturra:~/checkout/gnome2/jhbuild/modulesets$ 

Prueba con Opera... y éste pluggins...

No entiendo como ejecutaste eso.

---

### Post by AlvaroV on 2009-06-24
Digo sin el signo $

---

### Post by Psycopatologic on 2009-06-24
CdK1@Caturra:~/checkout/gnome2/jhbuild/modulesets$ dpkg -l | grep flash
ii  flashplugin-nonfree                  1:2.6                        Adobe Flash Player - browser plugin

ahi el ejecuto un CD para cambiar al directorio ~/checkout/gnome2/jhbuild/modulesets  (fijate que el $ esta al final de la ruta)...vas a la carpeta que te sugirieron y ejecutas

$ sudo dpkg -l | grep flash ii  flashplugin-nonfree                  1:2.6                        Adobe Flash Player - browser plugin

y opera se supone que lo tienes...una pregunta...tu sistema es de 64 bits? sigues en Jaunty o estas en otra distribucion?

saludos

---

### Post by AlvaroV on 2009-06-25
> **Psycopatologic said:**
> CdK1@Caturra:~/checkout/gnome2/jhbuild/modulesets$ dpkg -l | grep flash
ii  flashplugin-nonfree                  1:2.6                        Adobe Flash Player - browser plugin

ahi el ejecuto un CD para cambiar al directorio ~/checkout/gnome2/jhbuild/modulesets  (fijate que el $ esta al final de la ruta)...vas a la carpeta que te sugirieron y ejecutas

$ sudo dpkg -l | grep flash ii  flashplugin-nonfree                  1:2.6                        Adobe Flash Player - browser plugin

y opera se supone que lo tienes...una pregunta...tu sistema es de 64 bits? sigues en Jaunty o estas en otra distribucion?

saludos

Disculpa pero no entiendo que porpone que haga, que instale un live cd y ejecute desde el algo ?. Tengo 9.04 y Opera también tiene problemas.

---

### Post by kamus on 2009-06-26
> **AlvaroV said:**
> Disculpa pero no entiendo que porpone que haga, que instale un live cd y ejecute desde el algo ?. Tengo 9.04 y Opera también tiene problemas.

Se supone que deberias tener instalado ese paquete que es la libreria para poder reproducir archivos flash (al menos con firefox es llegar,instalar y usar) no se si habra que enlazar la libreria o alguna trucheria con Opera porque no lo ocupo. Un comportamiento con firefox/flash por ejemplo cuando tienes mas de una libreria flash instalada por ejemplo gnash no siempre se comporta de la manera que uno espera el browser, alfinal la unica solucion es que debes desisntalarla y solo dejar la flash-nonfree, de todas maneras para ver los paquetes instalados relacionados con flash ejecuta en una terminal:

```

kamus@sid:~$ dpkg -l | grep flash
ii  flashplugin-installer                     10.0.22.87ubuntu2                         Adobe Flash Player plugin installer
ii  flashplugin-nonfree              10.0.22.87ubuntu2                         Adobe Flash Player plugin installer (transit

```

En mi caso devuelve esto ya que ocupo el plugin oficial de adobe y me funciona relativamente bien estable, si no los tienes instalalos y elimina las otras librerias.

Saludos

---

### Post by AlvaroV on 2009-06-27
En realidad mi pregunta iba por el lado de casi una duda existencial porque doy por hecho que el tema del cierre de navegadores al enfrentarse a flash no tiene solución en Ubuntu, sólo quería saber si alguien tiene algun dato al respecto que yo no tenga. Ya que yo lo he probado todo.

---

### Post by CdK1 on 2009-06-27
Has probado Opera+flashplayer-nonfree? o Firefox+flashplayer-nonfree?

---

### Post by moreback on 2009-06-27
A mi no se me cae el flash ni firefox y eso que tengo ubuntu de 64 bits

---

### Post by AlvaroV on 2009-06-28
> **moreback said:**
> A mi no se me cae el flash ni firefox y eso que tengo ubuntu de 64 bits

Lo cual prueba mi sospecha de que es un problema que no se da en todas las arquitecturas de hardware. es decir no es un problema de Flash con firefox, sino de Flash + Firefox + ¿Atlhon, AMd? ¿N vidia? o que se yo.

---

### Post by Carlos C on 2009-06-29
No creo que sea algo tan simple como decir que fifefox+flash+amd es lo que causa el problema. No es un comportamiento común y si fuera lo que tu crees a mi también me pasaría. Me parece que es un problema puntual de tu equipo, algún hardware está fallando o es un modelo específico que tiene problemas de compatibilidad.
Cuando se cierre firefox prueba escribiendo en el terminal:
```
dmesg
```

---

### Post by moreback on 2009-06-29
lo otro sería algún plugin de firefox como el flashblock u otro que hiciera conflicto, también revisaría si tuviera instalado el gnash o swfdecod (o como sea).

La página [about:plugins]("about:plugins") da información de que plugins tienes habilitado.

---

### Post by Patriciologico on 2009-06-29
Prueba correr firefox a prueba de fallos (recuerda marcar descativacion de addons cuando comience )

```
firefox -safe-mode
```

saludos!

---

### Post by AlvaroV on 2009-06-30
> **Carlos C said:**
> Me parece que es un problema puntual de tu equipo, algún hardware está fallando o es un modelo específico que tiene problemas de compatibilidad.
Cuando se cierre firefox prueba escribiendo en el terminal:

Te estas comportando como el chiste del soporte de Microsoft, ese de ¿por qué se necesitan tres ingenieros para cambiar una ampolleta en Microsoft". te aconsejo que coloques en Google "firefox se cierra solo".

---

### Post by Carlos C on 2009-06-30
> **AlvaroV said:**
> Te estas comportando como el chiste del soporte de Microsoft, ese de ¿por qué se necesitan tres ingenieros para cambiar una ampolleta en Microsoft". te aconsejo que coloques en Google "firefox se cierra solo".
Por muy frustrado que el tema te tenga te voy a pedir que te tomes con calma mis sugerencias o las de cualquier otra persona. El próximo comentario de ese tipo lo voy a tomar como una infracción al CoC y cerraré el thread.

---

### Post by AlvaroV on 2009-07-02
> **Carlos C said:**
> Por muy frustrado que el tema te tenga te voy a pedir que te tomes con calma mis sugerencias o las de cualquier otra persona. El próximo comentario de ese tipo lo voy a tomar como una infracción al CoC y cerraré el thread.


[LIST=1]
[*]Insultar o descalificar a otro miembro del foro.
[*]Escribir usando deformaciones del lenguaje, utilizando la" k" en sustitución de "q" y "c", con constantes abreviaciones, modismos muy locales, faltas constantes de ortografía o todo aquello que dificulte leer o comprender el tema.
[*]Escribir groserías.
[*]Responder con comentarios del tipo "RTFM".
[*]Crear más de un Thread para preguntar por el mismo tema.
[*]Utilizar letras muy grandes o demasiado pequeñas, textos llenos de colores y resaltados, emoticons de manera exagerada o todo aquello que vaya en contra de la claridad del texto.
[*]Escribir títulos con palabras grotescas, groserías o del tipo "Quien me ayuda??", "cómo hago esto", "socorro!!!", etc.
[*]Pedir que te respondan por PM (mensajes personales), crea un nuevo thread, así todos se benefician.
[*]Introducir SPAM en el foro, promover sitios, ofrecer servicios, ventas, negocios o cualquier tipo de publicidad.
[*]Escribir en el Sub Foro incorrecto (no son más que 4, no cuesta tanto). :wink:
[*]Preguntar por más de un tema en un thread.
[/LIST]
Me interesa saber cual de las normas que te público no cumplí, porque si no lo haces con precisión tengo el derecho a suponer que sólo estas abusando de tu condición de administrador con tu amenaza.

---

### Post by Carlos C on 2009-07-02
Lo que rige al foro es el Código de Conducta. La primera norma del código es bastante clara:

> Be respectful of all users at all times. This means please use etiquette and politeness. Treat people with kindness and gentleness. If you do this the rest of the code of conduct won't need more than a cursory mention.Lo básico aquí es que si mantienes una actitud agresiva voy a cerrar tus threads. Si consideras que estoy abusando de mi posición de moderador te sugiero que leas el resto del CoC.

---

### Post by CdK1 on 2009-07-02
Volviendo al tema del thread y dejando de lado una dispusta innecesaria, te señalo:

De hard? mmm podría ser en amd64, aunque yo tengo iceweasel -aka firefox- más el flashplugin-nonfree y no tengo cierres de ese tipo, sólo cuando tengo abierto una cantidad de videos demasiado grande, aunque Opera se maneja mejor en eso...

---

### Post by moreback on 2009-07-03
> **CdK1 said:**
> Has probado Opera+flashplayer-nonfree? o Firefox+flashplayer-nonfree?

El paquete oficial es flashplugin-installer, el flashpugin-nonfree es sólo transitorio por lo que en el futuro va a desaparecer.

---

### Post by AlvaroV on 2009-07-03
Dejando atras una disputa innecesaria. Vuelvo al tema. Efectivamente mi pregunta no era una exacta solicitud de soporte, ya que realmente he probado todo y el problema de los cierres de los Navegadores se repetía sin importar la versión de Ubuntu. Por lo cual mi interés iba más por el lado de saber si exstía alguna novedad en el tema. 

Ahora sin embargo, voy a tener la oportunidad de probar si mi teoría , de que sea un conflicto Ubuntu + una arquitectura Hard, es cierta, ya que instale Ubuntu además, en un noteboockr HP de mi pega y podré comparar. Y mantendré información al respecto.

---

### Post by moreback on 2009-07-03
Los cuelgues de Firefox debido a Flash son única y exclusivamente producidos por el plugin de Adobe Flash, el cual te recuerdo es software privativo, por lo que la Comunidad de Ubuntu no puede hacer mucho por mejorarlo.

Desde la versión 8.10 que esto ha mejorado bastante con la aparición del Flash 10.0 el cual fue compilado de mejor forma para Linux por parte de Adobe.

Saludos.

---

