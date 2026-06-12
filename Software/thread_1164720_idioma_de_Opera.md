---
title: "idioma de Opera"
date: 2009-05-19
forum: Software
---

### Post by drazhe on 2009-05-19
esto es algo que nunca me habia pasado, instale el browser Opera en mi ubuntu 9.04 y al igual que cuando lo hice en la 8.04 y 8.10 el programa estaba en ingles, asi que me baje el archivo con el lenguaje y con esto deberia haverse solucionado, pero ahora esta mitad y mitad, parte del programa en castellano y parte en ingles, alguien sabe que paso??? y como solucionarlo?

adjunto una imagen para mostrar el problema... 

[http://www.subirimagenes.com/otros-pantallazo-2569823.html](http://www.subirimagenes.com/otros-pantallazo-2569823.html)

---

### Post by staar on 2009-05-19
que versión de opera es? de donde bajaste archivo del lenguaje? reiniciaste opera?

saludos

---

### Post by emiliano_raso on 2009-05-19
No no no no. El archivo de idioma viene con el .deb que instalas y bajas de la pagina.

Andá a:
- Herramientas
- Opciones
- Donde está para buscar el idioma clickeá DETALLES
- Te va a aparecer una ventana para buscar un archivo. Buscá este:
/usr/share/opera/locale/es-ES/espanol-espana.lng
Antes tenias el que está en ingles.
Simplemente tenes que cambiar eso y TARAN. Ya está en castellano.

No se ahoguen en un vaso de agua muchachos xD Cuando fuiste a buscar el archivo que bajaste de internet, tuviste qeu ver que el archivo de idioma en ingles estaba en "/usr/share/opera/locale/ (...)" y ahi tenias que buscar el que está en español.

A veces las cosas son mas faciles de lo que parecen.

---

### Post by drazhe on 2009-05-20
taaaaaaannn tonto no soy, uso el opera 9.64, y baje el archivo del lenguaje desde opera.com, fui a herramientas>detalles y esos lugares donde me dijeron y me quedo el opera mitad y mitad, en el foro de opera me dijeron que es un bugs de la version 10, pero la que yo uso no es la 10, sino la 9.04, en mi pc de escritorio tengo instalado ubuntu 8.10 y tambien instale opera, este estaba en ingles, y despues de bajar y cargar el archivo de lenguaje, este se puso totalmente en castellano, pero en la notbuk me quedo mitad y mitad... por eso pregunto.... 
pero gracias por la ayuda!

---

### Post by Hei Ku on 2009-05-20
En la notebook el lenguaje del sistema esta tambien en español?

---

### Post by sp33d3rs on 2009-05-20
Nose si me pasa a mi, o es en opera en general... es muy loco, pero cuando copio algo (sea "crtl+c" o "click derecho copiar") después no puedo pegar en ningun otro software que no se opera.
Yo utilizo USD para descargas, queria copiar unos link de rapishare desde opera, y cuando los queria pegar en el USD no lo pegaba. Probe desp en prosesadores de texto, en cualquier lado.. de culaquier programa de la pc, funciona, pero desde opera no.

Saben por que?

---

### Post by staar on 2009-05-20
cerrás el opera antes de pegar el texto? mira que en linux el portapapeles no funciona igual que en win (ejemplo, para copiar, solo seleccionar o 'pintar' el texto y hacer click con el botón del medio donde se quiere pegar) el USD no es un programa de Ventanas? lo usas con Wine?

saludos

---

### Post by drazhe on 2009-05-21
> **Hei Ku said:**
> En la notebook el lenguaje del sistema esta tambien en español?

Si, el Ubuntu 9.04 esta en castellano...


segun SISTEMA > ADMINISTRACION > SOPORTE DE IDIOMAS

tengo:

para mis menus y ventanas usar Español, Castellano (Argentina)
y para
Cualquiera en inicio, ventana, usar igual
Español, Castellano (Argentina)

lo raro es que hice lo mismo que hice cuando instale la 8.04 y la actualice a la 8.10, ahi tambien instale el opera, se me habia puesto en ingles, baje y cargue el parche de idiomas de la pagina de opera.com y en las versiones 8.04 y 8.10 de ubuntu, el opera quedo impecable, en castellano y con todos los chiches, aca me quedo mitad y mitad despues de hacer eso, creo que fue despues de instalar el plugin de flash... porque hubo un tiempo minimo que tube el opera en castellano antes de bajar el plugin... 
sera problema con la version 9.04 de ubuntu?

---

### Post by staar on 2009-05-21
probá borrando (o cambiando de nombre) la carpeta de configuraciones de opera, está en tu home, se llama .opera, es una carpeta oculta...

cuando vuelvas a abrir opera, se te va a crear una nueva con las configuraciones por defecto...

saludos

---

### Post by sp33d3rs on 2009-05-22
> **staar said:**
> cerrás el opera antes de pegar el texto? mira que en linux el portapapeles no funciona igual que en win (ejemplo, para copiar, solo seleccionar o 'pintar' el texto y hacer click con el botón del medio donde se quiere pegar) el USD no es un programa de Ventanas? lo usas con Wine?

saludos

Si, lo utilizo con wine, aun no me acostumbro al jdownloader. Lo del boton del medio no lo sabia, lo voy a probar.

---

### Post by drazhe on 2009-05-22
> **sp33d3rs said:**
> Si, lo utilizo con wine, aun no me acostumbro al jdownloader. Lo del boton del medio no lo sabia, lo voy a probar.

porque usas opera desde wine? si hay una version para linux en todos sus sabores?????

---

### Post by drazhe on 2009-05-22
Bueno gente, hice lo que me dijeron en unos mensajes anteriores, borre la parpeta .opera que estaba dentro de home>mi usuario>.opera (si mal no recuerdo) y cuando volvi a abrir el programa este me tiro el contrato de llicencia y fue como si abriera el programa por 1era vez, cargue el parche de idioma y todo se puso en castellano como debia ser y no mitad y mitad como estaba antes, estuve probando la pagina de youtube.com y adobe.com para probar si tenias los plugines para ver si andaba y todo funciona 10puntos, gracias a todos por la ayuda!

Lo unico que advierto al prox. que le pase algo asi es que se pierden todas las configuraciones y favoritos del programa, asi que si van a hacerlo asegurense de guardar sus favoritos antes de borrar la carpeta .opera

Saludos y nuevamente gracias!

---

### Post by sp33d3rs on 2009-05-25
> **drazhe said:**
> porque usas opera desde wine? si hay una version para linux en todos sus sabores?????
No hombre, hablo del USD.. jeje, que por cierto pase al "Tucan", que funciona mejor.

---

