---
title: "Configurar APT para que NO borre el caché de paquetes descargados"
date: 2010-11-11
forum: Software
---

### Post by EnriqueK on 2010-11-11
Tengo particular interés de conservar los paquetes descargados en /var/cache/apt/archives ,, en versiones anteriores a la 10.04 bastaba con indicarlo en las opciones que ofrece Synaptic, pero al parecer hay que hacer algo mas ya que cada cierto tiempo se me borran un 90% de los paquetes que allí figuran, menos mal  que tomé la precaución de respaldarlos en DVD , pero de todas maneras quisiera que esto no sea necesario y que dichos paquetes se mantengan en el caché hasta que yo decida  borrarlos.

---

### Post by hectorivand on 2010-11-12
> **EnriqueK said:**
> Tengo particular interés de conservar los paquetes descargados en /var/cache/apt/archives ,, en versiones anteriores a la 10.04 bastaba con indicarlo en las opciones que ofrece Synaptic, pero al parecer hay que hacer algo mas ya que cada cierto tiempo se me borran un 90% de los paquetes que allí figuran, menos mal  que tomé la precaución de respaldarlos en DVD , pero de todas maneras quisiera que esto no sea necesario y que dichos paquetes se mantengan en el caché hasta que yo decida  borrarlos.

¿Viste que te respondieron acá?

[http://ubuntuforums.org/showthread.php?p=10102036](http://ubuntuforums.org/showthread.php?p=10102036)

Si no te sirve, esto sí.

[http://machgeek.wordpress.com/2010/10/23/crea-y-restaura-copias-de-tus-paquetes-instalados/](http://machgeek.wordpress.com/2010/10/23/crea-y-restaura-copias-de-tus-paquetes-instalados/)

Saludos
Nacho

---

### Post by biale on 2010-11-12
Es cierto, a partir de karmic (?) ya no se guardan todos los paquetes descargados aun cuando se encuentren vigentes.

Y lo mismo sucede con aptoncd, que a su vez tampoco toma todo lo que debiera. Po ahi leí que aptoncd no esta siendo mantenido, no se si las fuentes o la versión en repositorio.

Pero hay una forma muy sencilla y que cubre bastante bien el tema. Basta con copiar/ guardar como root los archivos .deb (solo esos archivos) que se encuentran en /var/cache/apt/archives al lugar que uno quiera.

Si luego se los repone a ese lugar y se pide una actualización, todos los .deb que encuentra no los vuelve a descargar. Salvo que exista una nueva versión del paquete.

---

