---
title: "preguntas sobre LUBUNTU"
date: 2010-05-02
forum: Software
---

### Post by joseluis on 2010-05-02
hola...espero que sea éste el lugar, ya que no hay o no encuentro aun un foro es castellano de lubuntu.
Instalé la versión test final release, una maravilla..un trabajo hermoso de la gente de Lubuntu,  a quienes de verdad agradezco y felicito..

Me surgen algunas preguntas acostumbrado a ubuntu y que acá no encuentro.

1. no veo de donde dar la orden de actualizar equipo, el equivalente a "gestor de actualizaciones".

2. en el File Manager hay una opcion que dice "Ir/ unidades de red" y muesstra un icono de Red de Windows. Pero no se activa, es decir, si le hago click no pasa nada. Esto para mi es importante, porque trabajo en red con otras maquinas. me pregunto si instalando nautilus se podria ver, ya que nautilus sÍ muesstra las maquinas ¿instalando nautilus perdería velocidad y la maquina se haria mas pesada? No querría resignar justamente la caracteristica de lubuntu de ser agil y rapido.

3. No me anda flash, esto es porque, imagino, no está el paquete "universe multiverse etc.....extras restringidos de ubuntu y demas....¿conviene instalarlo? nuevamente: no quiero resignar la velocidad y agilidad. Y de no instalar los extras.... ¿como meter este tema de flash? aclaro que no meti ni FF ni Opera, ni nada, Me quede con el chromium que me parece barbaro...

bueno...por ahora aca va todo....me encantó esta distro

---

### Post by alfplayer on 2010-05-04
1. Según [https://wiki.ubuntu.com/Lubuntu/DocumentationHelp#Keep%20Lubuntu%20up-to-date](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp#Keep%20Lubuntu%20up-to-date), recomiendan usar Synaptic o el Gestor de actualizaciones. Para usar el Gestor de actualizaciones primero debe instalarse (que puede hacerse con Synaptic).

2. No se porqué no te está funcionando. La velocidad de la máquina es igual, pero nautilus es más lento que pcmanfm.

3. Como con Nautilus, la velocidad de la máquina es igual.

Los programas o aplicaciones que se instalan no hacen más lenta a la computadora. Pero algunos paquetes instalan servicios o agregan programas para que se autoinicien después que se inicia linux o después que se inicia el escritorio. Algunos de los servicios o programas que se autoinician sí pueden hacer más lenta a la computadora. Si no son necesarios los programas que se autoinician se pueden deshabilitar.

Flash no instala programas para que se autoinicien. Nautilus puede instalar alguno pero la computadora no debería hacerse más lenta.

---

### Post by joseluis on 2010-05-04
Muchas gracias alfplayer..
¿puedo un par de preguntas mas?
1. ¿como se llama para encontrar el "gestor de actualizacions" para instalarlo desde synaptic?

2. Veo, veo..la red, pero no puede abrir las carpetas, veo las maquinas, pero a pesar de estar compartidos los recursos..nada...nopasa nada, no abre.

En fin...veré de meter nautilus a ver qué pasa y probar.

gracias

---

### Post by alfplayer on 2010-05-05
> **joseluis said:**
> Muchas gracias alfplayer..
¿puedo un par de preguntas mas?
1. ¿como se llama para encontrar el "gestor de actualizacions" para instalarlo desde synaptic?

2. Veo, veo..la red, pero no puede abrir las carpetas, veo las maquinas, pero a pesar de estar compartidos los recursos..nada...nopasa nada, no abre.

En fin...veré de meter nautilus a ver qué pasa y probar.

gracias

1. update-manager es el nombre del paquete. Los que aparecen listados en Synaptic son los paquetes de Ubuntu.

2. No se. Se puede crear otro tema con este problema por si otra persona puede aportar.

---

### Post by guillermolisi on 2010-05-08
Para que no te desalientes, para Octubre, cuando se lance la 10.10, se supone que Lubuntu sera un sabor Ubuntu oficialmente reconocido y esto deberia mejorar varios aspectos funcionales, como el que comentas de la red (si es que no se resuelve ahora con alguna actualizacion). El comentario se hizo en la ultima Ubuntu [Open Week en Español]("http://u.nu/9jjb9")

---

### Post by joseluis on 2010-05-09
Gracias por el link...viene más que interesante el proyecto Lubuntu, creo que está creciendo mucho y que dará a mucha gente la posibilidad de tener linux en maquinas antiguas..grande

edit: BUENO...pude lograr ver las maquinas de red!!!! pero no puedo montar las unidades compartidas.... ;(( 
Tengo instalado SAMBA, asi que imagino que no seria algo tan dificil ahora que puedo ver la red...uso el programa pyNeighborhood que viene con lubuntu para ver las unidades de red, pero aun no las monta.
si puede ayudarme...gracias

---

### Post by EdwardR on 2010-05-10
Disculpe, pero no hablo bien el español. El pyNeighborhood no funcionó para mí. Instalé el nautilus y podía ver mis máquinas de XP inmediatamente y comparitr archivos. Mi computadora lubuntu ahora tiene el nautilus y pcmanfm. Mi computadora tiene un Pentium III de 500 Mhz y 512 MB de memoria, el nautilus es un poco más lento que el pcmanfm, pero funciona muy bien para mí.  Despues de conectar en el red con nautilus, el pcmanfm luego peude ver y compartir con las otras máquinas.

---

### Post by joseluis on 2010-05-14
comparto esa experiencia, me sucedió lo mismo. Puedo operar la red desde nautilus...
Espero, imagino, que esto se resolverá con alguna actualizacion o con la 10.10. De todos modos, vemos que estas fallas o imperfecciones pueden encontrar un modo de resolución.

---

### Post by joseluis on 2010-06-19
> **alfplayer said:**
> 1. update-manager es el nombre del paquete. Los que aparecen listados en Synaptic son los paquetes de Ubuntu.

2. No se. Se puede crear otro tema con este problema por si otra persona puede aportar.

hola..el tema es que este paquete es para Ubuntu, y cargando el lubuntu con librerias de ubuntu ya se transformaria en ubuntu.
creo que usando el synaptic esta bien...¿no te parece?

---

### Post by alfplayer on 2010-06-20
> **joseluis said:**
> hola..el tema es que este paquete es para Ubuntu, y cargando el lubuntu con librerias de ubuntu ya se transformaria en ubuntu.
creo que usando el synaptic esta bien...¿no te parece?

No probé Update Manager en el escritorio de Lubuntu. Aparentemente se puede usar en Lubuntu como se usa en Ubuntu.

No entiendo qué significa que se "transforma en Ubuntu". Cuando se instala cualquier paquete (como update-manager) se instalan los paquetes de librerías necesarias que no están instalados.

No veo una diferencia importante entre usar uno o el otro.

---

