---
title: "Desktop Art y caratulas"
date: 2010-05-20
forum: Software
---

### Post by joseluis on 2010-05-20
Desktop Art.  Sin embargo, bajo el plug in, hago todo tal cual, lo activo desde rhythmbox, todo bien; me muestra el icono en el escritorio...PERO NO ME MUESTRA LA CARATULA...
alguien sabe???

---

### Post by leonardomdq on 2010-05-20
Si buscas algo como el skin de la captura de [este]("http://img413.imageshack.us/img413/3636/pantallazoat.png") escritorio no es Desktop Art el plugin para Rhythmbox, se llama Covergloobus que soporta muchos reproductores, MPD, Rhythmbox, Exaile, Banshee entre otros.

---

### Post by joseluis on 2010-05-20
bien...gracias!
(y gracias por mover el hilo también)
el plug Desktop Art veo que me funciona con colecciones de mp3, ahi si me pone la carátula.
Baje el Covergloobus, pero ...¿como lo agrego como plug in? es un archivo comprimido que lo descompromí y ahora ni idea..

---

### Post by leonardomdq on 2010-05-20
Una cosa es el plugin para Rhythmbox llamado Desktop Art y otra es Covergloobus (este ultimo es el que uso).

En Ubuntu 10.04 Lucid Lynx podes agregar el repositorio, para eso abris una consola:
```
sudo add-apt-repository ppa:gloobus-dev/covergloobus
```Y luego en la misma consola lo instalas asi:
```
sudo apt-get install covergloobus
```Una ves instalado vas a Aplicaciones -> Accesorios -> Covergloobus para ejecutarlo.

Una ves que te aparece en tu escritorio, te posas sobre el skin, con el boton derecho vas a configurar y podes elegir con que reproductor de música vas a usarlo, los temas visuales y entre otras configuraciones.

Los themes de Covergloobus se guardan en:

```

 /usr/share/covergloobus/themes 

```Si queres usar algun theme en especial que no viene por default lo instalas en ese directorio.
Tengo algunos themes hechos por mi para Covergloobus, podes encontrarlos [aca]("http://leonardomdq.deviantart.com/").

Saludos.

---

### Post by Piti on 2010-05-20
No se si será el mismo caso que el mío, pero a mi me andaban muy pocas caratulas con Desktop Art.

Me dí cuenta que sólo tomaba las que se llaman folder.jpg (o alguna otra, por lo menos esa seguro). En mi caso renombrando todo anduvo perfecto.

---

### Post by joseluis on 2010-05-23
gracias leonardomdq, voy a entrar a ver tus themes. El coverglobus anda barbaaro....

---

### Post by joseluis on 2010-05-23
> **joseluis said:**
> gracias leonardomdq, voy a entrar a ver tus themes. El coverglobus anda barbaaro....
solo que me parece..que la ventaja de Desktop Art es que se inicia con el programa de audio y covergloobe hay que iniciarlo aparte del reproductor.

---

### Post by NickCis on 2010-05-23
> **joseluis said:**
> solo que me parece..que la ventaja de Desktop Art es que se inicia con el programa de audio y covergloobe hay que iniciarlo aparte del reproductor.

Podrias modificar el acceso qe inicia el reproductor para que tmb inicie el coovergloobe,, o poner que inicie cuando arranca la pc.. (Sitema/Preferencia/Aplicaciones al Inicio)..

Lo unico malo que le encontre, fue que cuando usas el boton de "escritorio" (mostrar escritorio) de la barra de Gnome, te lo minimiza tmb,, Pequeño detalle xD jajaj..

Lo podes revivir de dos maneras, volviendo a tocar el boton de escritorio, o en el syspanel, segundo boton sobre el icono del coverGloobus y click en "acerca de" =P

Saludos.

---

### Post by Leandro17 on 2010-06-01
> **leonardomdq said:**
> Una cosa es el plugin para Rhythmbox llamado Desktop Art y otra es Covergloobus (este ultimo es el que uso).

En Ubuntu 10.04 Lucid Lynx podes agregar el repositorio, para eso abris una consola:
```
sudo add-apt-repository ppa:gloobus-dev/covergloobus
```Y luego en la misma consola lo instalas asi:
```
sudo apt-get install covergloobus
```Una ves instalado vas a Aplicaciones -> Accesorios -> Covergloobus para ejecutarlo.

Una ves que te aparece en tu escritorio, te posas sobre el skin, con el boton derecho vas a configurar y podes elegir con que reproductor de música vas a usarlo, los temas visuales y entre otras configuraciones.

Los themes de Covergloobus se guardan en:

```


 /usr/share/covergloobus/themes 

```Si queres usar algun theme en especial que no viene por default lo instalas en ese directorio.
Tengo algunos themes hechos por mi para Covergloobus, podes encontrarlos [aca]("http://leonardomdq.deviantart.com/").

Saludos.

cuando quiero instalar me aparece el siguiente mensaje:

No se pudo encontrar el paquete covergloobus

que problema hay?

---

### Post by guillermolisi on 2010-06-01
No tenes agregado y/o habilitado el repo ppa de Coverglobus, tal como se indica en el primer paso del tutorial que envio Leonardomdq, es una buena razon para que salga ese mensaje.

---

### Post by Leandro17 on 2010-06-01
osea la siguiente linea?

sudo add-apt-repository ppa:gloobus-dev/covergloobus
si la agregue al principio... puede ser que el servidor donde bajo no la tenga?

---

### Post by Leandro17 on 2010-06-01
probando nuevamente logré instalarlo, creo que faltó un sudo apt-get update o algo por el estilo... la cuestion es que no puedo cambiar la ubicacion de la imagen.. voy a configurar - window - start position y no reconoce los cambios, que puedo hacer?

---

### Post by leonardomdq on 2010-06-01
> **Leandro17 said:**
> probando nuevamente logré instalarlo, creo que faltó un sudo apt-get update o algo por el estilo... la cuestion es que no puedo cambiar la ubicacion de la imagen.. voy a configurar - window - start position y no reconoce los cambios, que puedo hacer?
Te faltaba lo mas importante, actualizar por eso no se instalo al principio.
Covergloobus podes arrastrarlo con el mouse hacia la ubicación que quieras y si no podes fijate con el boton derecho de mouse destilda la opción "stick on desktop" y luego movelo a donde mas te guste.

---

### Post by ALEXEX on 2010-06-02
ya descarge algunas caratulas de leonardo, se le agradece.

---

