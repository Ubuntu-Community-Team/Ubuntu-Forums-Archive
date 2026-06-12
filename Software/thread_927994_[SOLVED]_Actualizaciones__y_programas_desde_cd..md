---
title: "[SOLVED] Actualizaciones  y programas desde cd."
date: 2008-09-23
forum: Software
---

### Post by valucha on 2008-09-23
[COLOR="DarkOrchid"]Hola!... Tengo una duda, ¿Es posible guardar todas las actualizaciones que salieron para una distro (en este caso Ubuntu Hardy) en un cd y después insertarlo y que el synaptic las tome de allí en lugar de tomarlas desde internet?.
De ser así ¿Cómo se hace? porque en internet solo encunetro como upgradear una distro cosa que es fácil, pero no como conseguir todas las actualizaciones y como agregarlas a los repositorios.

Por otro lado... esto es seguro?, es decir, ¿Es lo mismo que instalarlo bajandolas?.

y ¿podré también bajar programas y que el synaptic me instale todo: actualizaciones y programas (con sus librerias bajadas) sin bajar absolutamente nada?..


Necesitaría hacerlo porque le formatie la compu a mi tía y tengo que ponerle a punto Ubuntu en muy poco tiempo, y ella tiene una conexión medio lenta y voy a tardar mucho.. Así podría bajar las cosas en mi casa tranquila y llevar el cd/dvd con TODO TODO TODO y dejar corriendo el synaptic un rato y voilá, no bajar nada.


Espero que se pueda, realmente me ahorraría un gran dolor de cabeza..

Besos y gracias nuevamente... Vale[/COLOR]

---

### Post by Air23 on 2008-09-23
Me parece que esto se acerca bastante a lo que buscas:

APTonCD ([http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)). Esta en los repos de ubuntu.

Mas info: [http://www.guia-ubuntu.org/index.php?title=APTonCD](http://www.guia-ubuntu.org/index.php?title=APTonCD)

---

### Post by EnriqueK on 2008-09-23
El siguiente método es el que empleaba cuando tenía una conexión teléfonica a 14.4 kbps, pero a pesar de tan miserable conexión podía instalar todo lo que quería, desde los repositorios que quería.
Ni por casualidad usaba esta conexión para instalar paquetes, lo que hacía es usarla solamente para instalar y mantener actualizados los** índices de repositorios** y una vez hecho esto, si toca actualizar abro Synaptic y en la parte inferior izquierda pulso el **botón estado** aparece arriba varias opciones y elijo **instalados (actualizables)** , aparecen todas las actualizaciones disponibles, ahora voy al menú Editar -> Marcar todas las actualizaciones , seguidamente voy al menú Abrir -> Crear un Script de descagas de paquetes  (o algo así, no estoy en Ubuntu ahora)  , le pones un nombre cualquiera y esto va a generar el Script en la carpeta del usuario , luego a dicho Script lo copias a un Pen Drive en donde ademas debes instalar **Firefox Portable** con las siguientes extensiones **DownThemAll** (es un gestor de descargas) y **Linkification ** (convierte texto `plano en Link) , una vez terminado lo anterior, puedes ir a por ejem un Cyber que tenga Xp , abres el Firefox Portable del Pen Drive , luego ve al menu Archivo -> Abrir Archivo y busca al Script creado en Ubuntu , esta acción hará que abra con las URLS reconocidas como hipervínculos (por acción de la extensión Linkification) , solo quedando entrar a Herramientas -> DownThem All , luego de una adecuada configuración de la carpeta de descargas, solo queda pulsar el botón adecuado para que comiencen las descargas .

Una vez descargados los paquetes , copia la carpeta de descargas al pen Drive y lo llevas a Ubuntu y copias dicha carpeta en la carpeta del usuario , luego abres **Synaptic -> Abrir-> Instalar paquetes descargados marcas (un click) la carpeta de descargas y abajo del Synaptic pulsa Abrir (no sirve hacer doble click )** , luego acepta todo lo que pida y comienza la instalación y no para hasta terminar.

Aunque parezca largo, es todo mu simple y rápido, para instalar paquetes de programas es un proceso muy similar en que solo difiere en que en Synaptic usa el menú buscar , elige los paquetes y cuado termines de buscar y marcar todos los paquetes, recién generas el Script.

Una recomendación final, antes de generar el Script de descargas, actualiza los repositorios para así evitarse problemas que justo un paquete tuvo una actualización y ya no está disponible para descargas- 

Este método es para mi el mas correcto y a prueba de cualquier pretexto, en mi opinión mucho mejor que usar APTonCD por que para que este funcione se tienen que cumplivarios requisitos , el mas importante sin dudas es el de no haber borrado nunca el caché a paquetes descargados, yo al menos siempre lo borro, prefiero guardar en un DVD todos los paquetes que voy descargando con el método explicado y cuando toque reinstalar, todo lo que se requiere es tener el mismo Sources.list ,actualizar los indices de repositorios y aplicar el método.

---

### Post by valucha on 2008-09-24
[COLOR="DarkOrchid"]Millones de gracias por sus respuestas.
Realmente ambos métodos me parecen convenientes pero el tema es que necesito llevar todo de mi casa sin tener que "salir" de la casa de mi tía. Es decir, tal vez pierda más tiempo (y dinero) haciendo lo del pen drive que bajandolas en la casa de mi tía. LO voy a adoptar para tener un backup de mi compu, pero realmente prefiero el atponcd. Si hay otras opciones todavía sigo abiertas a ellas. gracias :)[/COLOR]

---

### Post by valucha on 2008-09-24
[COLOR="DarkOrchid"]Me surgio una duda. ¿Cómo sé que mis paquetes van a ser los que necesita la máquina y no van a romper su Ubuntu?... está bien que sea una instalación en limpio, pero por ejemplo él tiene otra placa de video (encima Nvidia), otra mother, otro modem, parlantres, mouse, impresora, etc... ¿No se le van a instalar mis paquetes y a arruinar todo? ¿O directamente los ignora?.

Gracias ed nuevo[/COLOR]

---

### Post by kornykyano on 2008-09-24
Este es otra forma, no lo he probado pero debe funcionar 

[http://www.guia-ubuntu.org/index.php?title=Crea_CD/DVD_con_los_paquetes_descargados]("http://www.guia-ubuntu.org/index.php?title=Crea_CD/DVD_con_los_paquetes_descargados")

Aunque yo prefiero aptoncd.

---

### Post by EnriqueK on 2008-09-24
> **valucha said:**
> [COLOR="DarkOrchid"]Me surgio una duda. ¿Cómo sé que mis paquetes van a ser los que necesita la máquina y no van a romper su Ubuntu?... está bien que sea una instalación en limpio, pero por ejemplo él tiene otra placa de video (encima Nvidia), otra mother, otro modem, parlantres, mouse, impresora, etc... ¿No se le van a instalar mis paquetes y a arruinar todo? ¿O directamente los ignora?.


Con el método que expliqué tenés garantizado que no vas atener problemas por que el pedido de instalación de paquetes sale del equipo de tu tía, que inclusive puede no tener instalación a internet , en cambio tu equipo solo tendrá a su cargo las descargas de paquetes que solicita el otro PC y que este ya a gestionado con su APT, como menciono, este método lo he venido usando y las descargas las hacía en un Cyber que tenía Xp.
Ahora tal vez la mejor opción que tenés para instalar todo de un saque y dejarlo tal cual como lo tienes en tu equipo es usando Remastersys .
```
http://www.remastersys.klikit-linux.com/
```
Con Remastersys creas un Live DVD de toda tu instalación que podrás usarlo para instalar tu Ubuntu en el otro PC . Si la ISO la creas con la opción "distribuible", solo contendrá los programas instalados y no tendrá información personal por que no va a incluir en la ISO tu carpeta personal. Lo único a tener en cuenta es que antes de crear la ISO debes borrar el caché de paquetes instalados ( sudo aptitude clean && sudo apt-get clean), esto para aliviuaanar en todo lo posible la ISO a crear, por lo que aquí si es muy aconsejable usar APTonCD solo con fines de respaldos de estos paquetes y además debes desmontar todas las particiones que tengas, lo mismo la red (si la tuvieras). Con Remastersys no vas a tener problemas con las tarjetas gráficas, ya que este simplemente no toma en cuenta su instalación, por que es la forma de que sea posible la instalación de Ubuntu con cualquier equipo.
A mi no me gusta usar APTonCD por que requiere de varios codionamientos, en primer lugar el de no haber borrado nunca el caché de paquetes descargados, tampoco debes de haber borrado repositorios de tu sources.list y además no me gusta el hecho de tener que usar dpkg -i *deb  , el uso de dpkg se hace sin el control de dependencias de APT, lo que puede causar problemas a futuro, el uso de dpkg es reservado en mi opinión solo para expertos pàra evitar caer en el llamado "infierno dpkg".

---

### Post by faktorqm on 2008-09-24
Los paquetes de instalacion se guardan en /var/cache/apt/archives, lo unico que tendrias que hacer es armarte un cd con las ultimas versiones de cada paquete (ya que alli se guardan todas las versiones) y luego en la instalacion nueva volver a copiar los paquetes a esa ubicacion, tonces cuando actualiza los cuenta como descargados, y simplemente descomprime y configura. salu2!

---

### Post by sajnox on 2008-09-24
Valucha,

APTonCD no te sobrescribe los paquetes de la maquina destino, sino que en tu maquina busca los paquetes que hayas descargado y genera una iso que podes quemar a un CD/DVD

En la maquina destino (la de tu tia) al instalar APTonCD y poner el CD que trajiste de tu casa tomara al CD como un repositorio. 

No hara una instalacion de todo lo que llevas a la maquina destino. 

De esta manera no tenes por que preocuparte por que no rompes nada.

---

### Post by EnriqueK on 2008-09-24
Como bien dicen el APTonCd usa los paquetes almacenado en /var/cache/apt/archives , allí se conservan los paquetes de acuerdo a los índices de repositorios, o sea no se conservan todos los paquetes,  el problema está en que que si en algún momento hiciste limpieza de /var/cache/apt/archives, fuiste, resumiendo, el APTonCD no es mas que una aplicación que facilita copiar a un CD esos paquetes y que los convierte en repositorio, todo esto se puede hacer manualmente, pero las serias limitaciones que presenta su uso, no me resaulta del todo confiable, a menos que se tenga la plena seguridad que se cumplen plenamente las condiciones, de ninguna manera es para tomarlo a libro cerrado.
Por otra parte, si usas los CDs/DVDs creados con el APTonCd como repositorio, corres el riesgo de que es posible que fuerces al otro equipo a instalar paquetes que no le sean propios, por eso, si creas los respaldos usando aptoncd, lo mejor es usar a estos como simples contenedores de paquetes y que teniendo los índices de repositorios completos y actualizados puedes entrar a Synaptic -> Archivo-> Añadir paquetes descargados -> ubicas la carpeta contenedora de paquetes y pulsas Abrir , así si tendrás control pleno de dependencias que estará dado por APT basado en los índices de repositorios, solo de esta manera tendrás la certeza de que no se instalarán paquetes indebidos, en cambio si habilitas al CD como repositorio, lo que estas haciendo es engañar APT para tomar como bueno a todos los paquetes que allí se contengan y esto puede llegar a ser hasta peligroso, por ejemplo si tienes una gráfica nvidia y el otro equipo una ati, al crear al cd como repositorio estás forzando a unstalar drivers nvidia en un equipo que tiene ati y seguro que vas a tener problemas.

---

### Post by valucha on 2008-09-26
[COLOR="DarkOrchid"]BUeno, usé el APTonCD y la verdad que me sorprendió lo bueno que es. Se crea sin problemas y cuando lo ponés en la otra compu te lo abre automáticamente. Es genial!...


BUeno, otro solved por acá.[/COLOR]

---

### Post by sajnox on 2008-09-26
cada dia me queda mas claro que muchas cosas en Linux son cada dia mas simples

Me alegro que haya funcionado!!!

---

