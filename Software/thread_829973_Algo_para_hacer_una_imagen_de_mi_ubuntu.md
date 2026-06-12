---
title: "Algo para hacer una imagen de mi ubuntu?"
date: 2008-06-15
forum: Software
---

### Post by pol666 on 2008-06-15
Hola, quiero saber si hay algun programa que me permita hacer un Live CD haciendo una imagen de el ubuntu que tengo instalado en este momento, de manera que cuando corra el CD tenga los mismos programas, el mismo theme, etc.

Probe con Reconstructor, UCK, pero no me satisfacen esos programas, estoy buscando que directamente COPIE el sistema instalado

---

### Post by EnriqueK on 2008-06-15
Recomiendo el Remastersys, realmente excelente, yo creé un Live DVD de mi instalación en un par de clicks, realmente no puede ser mas simple, al principio creía que no me iba a servir por tener apena 512 megas de ram, pero no fue así, pude correr perfectamente el Live DVD , solo un para de cosas antes de crear la ISO, limpiar el cache y además desmontar todas las otras particiones.
[http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com)

---

### Post by pol666 on 2008-06-15
> **EnriqueK said:**
> Recomiendo el Remastersys, realmente excelente, yo creé un Live DVD de mi instalación en un par de clicks, realmente no puede ser mas simple, al principio creía que no me iba a servir por tener apena 512 megas de ram, pero no fue así, pude correr perfectamente el Live DVD , solo un para de cosas antes de crear la ISO, limpiar el cache y además desmontar todas las otras particiones.
[http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com)

No lo probe y ay me convensiste  :shock: estudias publicidad? jajaja

Gracias vamos a ver

---

### Post by sergiom99 on 2008-06-15
no se si sirve para hacer LiveCd, pero yo hice una imagen de mi disco la primera vez que instale GG (porq costaba un poco hacer andar algunas cosas) con [http://www.sysresccd.org/](http://www.sysresccd.org/) y [http://www.partimage.org/](http://www.partimage.org/)
Fue muy facil y pude hacer la imagen y mandarla por red a la otra PC para grabarla.

espero te sirva (o a alguno que quiera guardar su instalacion)

---

### Post by rober-mpp on 2008-06-15
yo conozco Garfio. Es desarrollado y utilizado por la gente de [tuquito]("http://www.tuquito.org.ar") para hacer su live cd. No lo probe personalmente, pero no debe ser muy complicado, ya que vi que tienen una guia para hacerlo en 10 minutos :P. El sistema te queda tal cual lo tenes ahora en un livecd, y ademas es instalable.

[http://garfio.org.ar/](http://garfio.org.ar/)

---

### Post by Mauro22 on 2008-06-23
Yo habia puesto esto hace rato ya:

[http://ubuntuforums.org/showthread.php?t=746760](http://ubuntuforums.org/showthread.php?t=746760)


No es ningun programa ni nada, solo comandos.

---

### Post by EnriqueK on 2008-06-24
Acabo de hacer el siguiete experimento
1.- Creo un Live DVD de mi instalación con Remastersys sin datos personales, o sea que no tenga mi carpeta de usuario.
2.- Formateo mi pendrive en EXT3 y allí grabo una copia de mi carpeta personal
3.- Arranco el Live DVD y lógicamente no contiene mis datos personales ni mis configuraciones, creo un nuevo usuario con el nombre de mi carpeta personal y mi contraseña.
4.- Hago sudo nautilus entro al /home y borro la carpeta del nuevo usuario y en este mismo lugar hago un enlace simbólico a mi carpeta de usuario que grabé anteriormente en mi memoria flash usb , cierro todas las ventanas abiertas y cambio de usuario , el sistema arranca con mi configuración y datos personales y puedo seguir guardando archivos que no se borrarán por que serán almacenados en el pendrive.

---

### Post by donmatas on 2009-10-07
> **EnriqueK said:**
> Recomiendo el Remastersys, realmente excelente, yo creé un Live DVD de mi instalación en un par de clicks, realmente no puede ser mas simple, al principio creía que no me iba a servir por tener apena 512 megas de ram, pero no fue así, pude correr perfectamente el Live DVD , solo un para de cosas antes de crear la ISO, limpiar el cache y además desmontar todas las otras particiones.
[http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com)

Compa: ¿cómo es eso de desmontar otras particiones? ¿te refieres a la partición donde está el /home? Y limpiar cual caché, el del navegador de internet?


saludos
DM

---

### Post by guillermolisi on 2009-10-07
> **donmatas said:**
> Compa: ¿cómo es eso de desmontar otras particiones? ¿te refieres a la partición donde está el /home? Y limpiar cual caché, el del navegador de internet?


saludos
DM
Me imagino que se refiere al cache del Apt (repositorios de paquetes).

---

### Post by donmatas on 2009-10-07
> **guillermolisi said:**
> Me imagino que se refiere al cache del Apt (repositorios de paquetes).
y cómo hago eso?

saludos
M

---

### Post by EnriqueK on 2009-10-07
Se trata del caché de paquetes descargados que se alojan en** /var/cache/apt/archives** , en mi caso por ejenplo, la suma total de estos paquetes rondan por  los 2 gigas, lo cual con seguridad va a ser un problema para crear la ISO d el Live DVD, tenés varias posibles soluciones
1.- Si no te interesa conservar estos paquetes de respaldo, basta con hacer un **sudo apt-get clean**
2.- Podés respaldar en un DVD y luego borrarlos 
3.- Lo mismo que lo anterior pero haciendo el respaldo usando **sptoncd** y luego los borrás.
3.- Lo que yo hago es previamente mover la carpeta archives a la partición /home , pero ojo, no a la carpeta de usuario, sino a /home , debo aclarar que tengo la /home en partición separada y seguidamente creo un enlace simbólico , los pasos serrían los siguientes
[B]sudo mv /var/cache/apt/archives /home
sudo ln -s /home/archives /var/cache/apt[/B]
De esta manera la carpeta archives estará físicamente eb /home , pero al estar enlazada al sistema, este la asume como propia, por lo que el funcionamiento del sistema seguirá igual, con la salvedad de no tener físicamente en el mismo la carpeta archives que puede pesar mucho.

---

### Post by donmatas on 2009-10-08
> **EnriqueK said:**
> Se trata del caché de paquetes descargados que se alojan en** /var/cache/apt/archives** , en mi caso por ejenplo, la suma total de estos paquetes rondan por  los 2 gigas, lo cual con seguridad va a ser un problema para crear la ISO d el Live DVD, tenés varias posibles soluciones
1.- Si no te interesa conservar estos paquetes de respaldo, basta con hacer un **sudo apt-get clean**
2.- Podés respaldar en un DVD y luego borrarlos 
3.- Lo mismo que lo anterior pero haciendo el respaldo usando **sptoncd** y luego los borrás.
3.- Lo que yo hago es previamente mover la carpeta archives a la partición /home , pero ojo, no a la carpeta de usuario, sino a /home , debo aclarar que tengo la /home en partición separada y seguidamente creo un enlace simbólico , los pasos serrían los siguientes
[B]sudo mv /var/cache/apt/archives /home
sudo ln -s /home/archives /var/cache/apt[/B]
De esta manera la carpeta archives estará físicamente eb /home , pero al estar enlazada al sistema, este la asume como propia, por lo que el funcionamiento del sistema seguirá igual, con la salvedad de no tener físicamente en el mismo la carpeta archives que puede pesar mucho.

Gracias compa

tuve una pésima experiencia con el programita. Le puse que hiciera un backup, estuvo como 3 hrs en eso y después me dijo que no había espacio suficiente. Para peor, me arruino una serie de aplicaciones (firefox, la barra del panel, etc). Tuve que reinstalar (por suerte tengo el /home en partición separada) y olvidarme del chiche

saludos
DM

---

### Post by emiliano_raso on 2009-10-09
Una pregunta: remastersys te guarda absolutamente todas las aplicaciones y configuraciones?

---

### Post by EnriqueK on 2009-10-09
> **emiliano_raso said:**
> Una pregunta: remastersys te guarda absolutamente todas las aplicaciones y configuraciones?

Casi todas si es que usas la opción de respaldo completo, o sea que incluya tu carpeta de usario, pero esta opción tiene el limitante de que solo sería factible si tenés a esta carpeya en un valor pequeño ya que la ISO resultamte final  no puede superar al tamaño de un DVD normal , por eso es preferible usar la opción distribuible que solo respalda el sistema sin configuraciones personales, la carpeta de usuario la podés respaldar aparte.De todas maneras no te va a respaldar todo lo que sean controladores de la gráfica, esto es hecho a propçosito para que el Live DVD pueda correr en cualquier otro equipo.
Un par de comentarios finales
1.- Asegurate de tener espacio suficiente para que pueda almacenar los archivos que se generan en el proceso y que por defecto estos se alojarán en /home , en caso de no tenerlo , prueba con usar otra partición.
2.- Una vez terminado el proceso y grabado el Live DVD, debes limpiar los archivos temporales por que suelen ser bastante pesados, todos esto se puede hacer desde las opciones de Remastersys.

---

