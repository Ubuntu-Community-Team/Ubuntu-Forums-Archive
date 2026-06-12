---
title: "Como cambiar de mirror ?"
date: 2010-04-30
forum: Software
---

### Post by drazhe on 2010-04-30
Hola, acabo de instalar desde 0 la nueva y tan esperada versión 10.04 LTS Lucid Lynx de Ubuntu, y al ponerme a instalar drivers propietarios, plugins, java, vlc, audaciuos y otras yerbas noto que horrorosamente lenta la descarga, por ejemplo el controlador de la placa de video tardo 1 hora en descargarse e instalarse, el vlc unos 30min... 
mi conexión a Internet es de 1mb y mientras descargaba, probé si era mi conexión la lenta bajando algún que otra cosa de Internet y desde megaupload y rapidshare bajaba normalmente a unos 95kbps mas o menos, pero de los repositorios si llegaba a 15kbps era cuando bajaba rápido... lo mismo note mientras que se instalaba, que los paquete de idiomas y actualizaciones tardaron muchisimo mas de lo habitual.
Alguno notó algo similar? sabe de que se trata?

---

### Post by harryscode on 2010-04-30
> **drazhe said:**
> Hola, acabo de instalar desde 0 la nueva y tan esperada versión 10.04 LTS Lucid Lynx de Ubuntu, y al ponerme a instalar drivers propietarios, plugins, java, vlc, audaciuos y otras yerbas noto que horrorosamente lenta la descarga, por ejemplo el controlador de la placa de video tardo 1 hora en descargarse e instalarse, el vlc unos 30min... 
mi conexión a Internet es de 1mb y mientras descargaba, probé si era mi conexión la lenta bajando algún que otra cosa de Internet y desde megaupload y rapidshare bajaba normalmente a unos 95kbps mas o menos, pero de los repositorios si llegaba a 15kbps era cuando bajaba rápido... lo mismo note mientras que se instalaba, que los paquete de idiomas y actualizaciones tardaron muchisimo mas de lo habitual.
Alguno notó algo similar? sabe de que se trata?

Fijate desde que mirror estas bajando.. porque los de argentina hace rato que vienen funcionando asi.. yo los cambie por uno de brasil y anda muy bien. Tambien tengo una conexiòn de 1mb. Suerte
Otra cosa.. acordate que como vos.. son muchos los que estan haciendo lo mismo.

---

### Post by drazhe on 2010-04-30
> **harryscode said:**
> Fijate desde que mirror estas bajando.. porque los de argentina hace rato que vienen funcionando asi.. yo los cambie por uno de brasil y anda muy bien. Tambien tengo una conexiòn de 1mb. Suerte
Otra cosa.. acordate que como vos.. son muchos los que estan haciendo lo mismo.

Si lo mismo pensé, en estos dias, deben ser muchisimos los que estamos bajando estos archivos, pero nunca me pasó que tardara tanto. los servers de donde bajan segun la terminal me imagino que son de argentina, ya que dicen ar.vayaunoasaberelnombre.com/blablabla... 

me podes decir como cambiar los repositorios por los de brasil como dijiste? soy bastante novatoide en el asunto Linux y Ubuntu...

---

### Post by juancarlospaco on 2010-04-30
borra el **ar.**

:)

---

### Post by harryscode on 2010-04-30
> **drazhe said:**
> Si lo mismo pensé, en estos dias, deben ser muchisimos los que estamos bajando estos archivos, pero nunca me pasó que tardara tanto. los servers de donde bajan segun la terminal me imagino que son de argentina, ya que dicen ar.vayaunoasaberelnombre.com/blablabla... 

me podes decir como cambiar los repositorios por los de brasil como dijiste? soy bastante novatoide en el asunto Linux y Ubuntu...

Sistema - Administración - Origenes del Software - Pestaña Software de Ubuntu - Descargar desde (abris menú) - Otro - y ahi tenes para elegir varios, yo intentè con Chile y me resultò igual que los de Argentina, los de brasil me andan muy bien. Creo que el que elegì es el primero que sale en la lista deplegable de Brasil. Exitos

---

### Post by drazhe on 2010-05-01
> **harryscode said:**
> Sistema - Administración - Origenes del Software - Pestaña Software de Ubuntu - Descargar desde (abris menú) - Otro - y ahi tenes para elegir varios, yo intentè con Chile y me resultò igual que los de Argentina, los de brasil me andan muy bien. Creo que el que elegì es el primero que sale en la lista deplegable de Brasil. Exitos

gracias! use el primero que dijiste, que se llama

**br.archive.ubuntu.com** y ahora las descargas de las actualizaciones vuelan!, se ve que el problema está en los servers Argentinos.... no habrá sido obra del ballmer ese que vino de visita? jejeje, saludos y nuevamente gracias por la ayuda!

---

### Post by chronos00 on 2010-05-04
no habria q reportarle a alguien q los repos de argentina estan andando mal?

---

### Post by guillermolisi on 2010-05-04
> **chronos00 said:**
> no habria q reportarle a alguien q los repos de argentina estan andando mal?
Quienes tienen que saberlo, ya lo saben.

El problema no son los servers, es la pobre calidad del enlace internacional y el poco ancho de banda local que usan las troncales de esos servidores.

---

### Post by chronos00 on 2010-05-04
> **guillermolisi said:**
> 
El problema no son los servers, es la pobre calidad del enlace internacional y el poco ancho de banda local que usan las troncales de esos servidores.

Si, lei sobre los problemas q hay con CABASE.
Sinembargo, estoy probando estos mirrors desde Speedy, Fibertel e iPlan, y en todos los casos me anda igual de mal. Bah... es verdad q con Speedy me anda peor aun.

Desde que ISPs se supone que tiene buena conectividad este mirror?

---

### Post by drazhe on 2010-05-04
> **chronos00 said:**
> Si, lei sobre los problemas q hay con CABASE.
Sinembargo, estoy probando estos mirrors desde Speedy, Fibertel e iPlan, y en todos los casos me anda igual de mal. Bah... es verdad q con Speedy me anda peor aun.

Desde que ISPs se supone que tiene buena conectividad este mirror?


la lentitud en los repositorios la comencé a notar desde Karmic hace meses, pero con Lucid fue extrema, y tengo 2 ISP, uno es broadbandtech y el otro fibertel, en ambos notè la lentitud, pero hasta donde se BBTech compra y re-vende ancho de banda a Fibertel, así que mas o menos seria siempre Fibertel mi ISP, jejeje... 
De cualquier manera pasándome a los servers de brasil como dije antes, todo volvió a la normalidad.

saludos!

---

### Post by chronos00 on 2010-05-05
el problema q me surge es q cuando quiero instalar ubuntu, la instalacion selecciona automaticamente el repositorio de argentina (q anda lento).
Desde la instalacion normal, o la instalacion en modo texto (alternativa), nunca me da la opcion de cambiar los repos.

Alguien sabe como cambiar los repos durante la instalacion?
Algun comando de consola o algo q me permita elegir los repos mas rapidos, por ejemplo.

---

### Post by guillermolisi on 2010-05-08
> **chronos00 said:**
> el problema q me surge es q cuando quiero instalar ubuntu, la instalacion selecciona automaticamente el repositorio de argentina (q anda lento).
Desde la instalacion normal, o la instalacion en modo texto (alternativa), nunca me da la opcion de cambiar los repos.

Alguien sabe como cambiar los repos durante la instalacion?
Algun comando de consola o algo q me permita elegir los repos mas rapidos, por ejemplo.
Si, elegis otro pais de residencia y toma los repos del mirror de ese pais. Si no existen elige el central o el que resuelva automaticamente.

Despues de instalar podes ajustar el pais que corresponda y elegis el mirror que mas te convenga.

---

