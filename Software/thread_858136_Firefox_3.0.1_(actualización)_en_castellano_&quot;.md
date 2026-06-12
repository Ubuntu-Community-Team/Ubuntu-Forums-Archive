---
title: "Firefox 3.0.1 (actualización) en castellano &quot;como&quot;"
date: 2008-07-13
forum: Software
---

### Post by atari130xe on 2008-07-13
Resulta que al iniciar Ubuntu se actualizaron un par de paquetes en mi PC entre ellos el del Navegador Forefox 3.0 a 3.0.1, eh aqui que al reiniciar el navegador quedó en Inglés, no hay drama con eso pero quería dejarlo como estaba, así que Googleando encontré esta solución para forzar la compatibilidad de Add-ons pero que automáticamente dejó el navegador como estaba (en Castellano).

> Pasos:

   1. Desinstalar las extensiónes compatibles con Firefox 2 y reiniciar el navegador
   2. En el cuadro de dirección introducir: about:config
   3. Click con el botón derecho en cualquier parte y seleccionar &#8220;Nuevo &#8211;> boolean&#8220;.
   4. Introducir: extensions.checkCompatibility
   5. Ponerle el valor &#8220;false&#8220;
   6. reiniciar Firefox
   7. Ir a la web para descargar las extensiónes y pulsar en &#8220;don&#8217;t check version&#8220;

Listo ;) 

Fuente [COLOR="Blue"]http://danydr.wordpress.com/2008/06/27/forzar-extensiones-firefox-2-en-firefox-3/[/COLOR] Espero les sirva. :)

---

### Post by Vulcano on 2008-07-13
Muchas gracias por tu aporte. Lo hice y salió excelente!!!! :lolflag:


> **atari130xe said:**
> Resulta que al iniciar Ubuntu se actualizaron un par de paquetes en mi PC entre ellos el del Navegador Forefox 3.0 a 3.0.1, eh aqui que al reiniciar el navegador quedó en Inglés, no hay drama con eso pero quería dejarlo como estaba, así que Googleando encontré esta solución para forzar la compatibilidad de Add-ons pero que automáticamente dejó el navegador como estaba (en Castellano).



Fuente [COLOR="Blue"]http://danydr.wordpress.com/2008/06/27/forzar-extensiones-firefox-2-en-firefox-3/[/COLOR] Espero les sirva. :)

---

### Post by nomentero on 2008-07-13
Bueno aunque es una "solucion"momentanea entraña muchos riesgos,Te lo digo por malas experiencias.Si quieres bajarte el archivo compatible para la traduccion al castellano de la version 3.0.1 te lo puedes bajar de la ftp de
Firefox(a mi me llevo tiempo encontrarla:biggrin:)
Si es problema con algun plugin es cuestion de tiempo que salga actualizado e incluso tienes herramientas para hacer dichos plugin "compatibles".

El archivo de traduccion al Español te lo descargas de:```
http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.1/linux-i686/xpi/es-ES.xpi
```

El archivo de traduccion Español-Argentina:```
http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.1/linux-i686/xpi/es-AR.xpi
```

 
 Salu2

---

### Post by atari130xe on 2008-07-13
> **nomentero said:**
> Bueno aunque es una "solucion"momentanea entraña muchos riesgos,Te lo digo por malas experiencias.Si quieres bajarte el archivo compatible para la traduccion al castellano de la version 3.0.1 te lo puedes bajar de la ftp de
Firefox(a mi me llevo tiempo encontrarla:biggrin:)
Si es problema con algun plugin es cuestion de tiempo que salga actualizado e incluso tienes herramientas para hacer dichos plugin "compatibles".

El archivo de traduccion al Español te lo descargas de:```
http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0rc1/linux-i686/xpi/es-ES.xpi
```

El archivo de traduccion Español-Argentina:```
http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0rc1/linux-i686/xpi/es-AR.xpi
```

 
 Salu2

Gracias, me habia olvidado de la advertencia en cuanto al uso de plugins de versiones anteriores y su posible inestabilidad, pero usè esta forma ùnicamente para este caso. :)

---

### Post by nomentero on 2008-07-13
Las gracias están de mas;aqui estamos todos para compartir experiencias.
En cuanto a los plugins no deberian de dar problemas en principio los que estan adaptados a la versión 3.0 entre estos y la nueva version 3.0.1 no hay
cambios significativos.pero si te podría dejar K.O el navegador, el que instalases un plugin solo compatibles con  versiones inferiores 2.xx.Eso puede pasar fácilmente si editas esa opción y al tener la verificacion de versiones de plugins desactivada;la instalas sin darte cuenta.
Por lo cual teniendo en cuenta esta advertecia,te explico como instalar plugins que te funcionen en la versión 3.0 para que sean compatibles también en la 3.0.1
Instala el plugin Nightly Tester Tools:```
https://addons.mozilla.org/es-ES/firefox/downloads/file/27794/nightly_tester_tools-2.0.2-fx+tb+sm.xpi
```
Bueno una vez instalado Nightly Tester Tools reinicias firefox te vas a: Herramientas- complementos--extensiones pinchas sobre la extensión compatible con la versión 3.0.....pero que la puñetera dice que no es con la 3.0.1 botón derecho del ratón,y le das a la opción de buscar actualización.Si hay actualización la descarga ,y sino hay simplemente adapta dicha extensión para que sea compatible.
:lolflag:

Ampliando me en lo de la traducción del firefox al castellano seria recomendable editar otro par de cositas con about:config
general.useragent.locale es-ES
spellchecker.dictionary  es-ES

ya que por defecto estan esas entradas a ingles USA. en-US

Ya que por defecto aunque tengamos traducido el firefox a español si tenemos el diccionario tambien instalado de español, si queremos hacer una corrección ortográfica firefox tirara de diccionario ingles como primera opción.Así lo arreglamos
El diccionario español esta en:```
https://addons.mozilla.org/es-ES/firefox/addon/3554
```
Saludos desde España

---

### Post by lozaneti on 2008-07-19
cuando lo instalo, me dice que ese xpi no es compatible con 3.0.1, solo hasta la 3.0.
Pero bueno, ya pondran la traduccion

---

### Post by lozaneti on 2008-07-19
Ya la he encontrado, es esta (directo de mozilla.org):
[http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.1/linux-i686/xpi/es-ES.xpi](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.1/linux-i686/xpi/es-ES.xpi)

---

### Post by fedeavila on 2008-07-23
> **atari130xe said:**
> Resulta que al iniciar Ubuntu se actualizaron un par de paquetes en mi PC entre ellos el del Navegador Forefox 3.0 a 3.0.1, eh aqui que al reiniciar el navegador quedó en Inglés, no hay drama con eso pero quería dejarlo como estaba, así que Googleando encontré esta solución para forzar la compatibilidad de Add-ons pero que automáticamente dejó el navegador como estaba (en Castellano).

hey me decis como hiciste para arreglar lo de los "addons" ??
yo tengo el firefox 3.0 y no se como actualizarlo al 3.0.1
y trato de agregarle extensiones o temas pero no me deja!
o sea, hago click en el botoncito de "Add to Firefox" y no hace nada... 
Como que esta muerto el boton...

No se que pasa :S Como hiciste para arreglar eso?

Graxxx

---

### Post by atari130xe on 2008-07-24
> **fedeavila said:**
> hey me decis como hiciste para arreglar lo de los "addons" ??
yo tengo el firefox 3.0 y no se como actualizarlo al 3.0.1
y trato de agregarle extensiones o temas pero no me deja!
o sea, hago click en el botoncito de "Add to Firefox" y no hace nada... 
Como que esta muerto el boton...

No se que pasa :S Como hiciste para arreglar eso?

Graxxx

El tema de la actualización deberia ser automático siempre y cuando tengas los repositorios al día y los necesarios. En mi caso tengo las actualizaciones al día porque tengo TODOS los repositorios tildados, eso tiene sus incovenientes tmb porque por ej; al habilitar el de "ubuntu proposed" se te instalá lo último de lo último pero como todavia no esta muy estable puede que tengas algunos cuelgues, pero si te las arreglás va bien.

---

### Post by Gustaffson on 2008-08-04
Gracias, no podía encontrar el link con la actualización del idioma. Saludos desde Chile

---

