---
title: "Error de paquete roto en synaptic"
date: 2009-06-16
forum: Software
---

### Post by rapidgarcha on 2009-06-16
hola... soy nuevo en el foro y en ubuntu... tengo un problemilla que no me deja hacer nada.

Cuando quiero instalar algún programa, ejemplo el flash player para el mozilla... me tira un error... dice que hay un paquete roto, así que entro con sudo synaptic, uso el filtro paquete roto y encuentro este:
nspluginwrapper
le quiero dar a reparar o eliminar, aplico cambios y me tira error:

"dpkg: error de tratamiento en el fichero '/var/lib/dpkg/status' cerca de la línea  paquete 'ia32-libs' : falta versión."

les pase estos comandos:

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install -f
sudo apt-get autoremove

y sigue con el error.

en una pagina decia que podia editar el fichero: "/var/lib/dpkg/status" y donde decia broken, cambiarlo por install ok installed, pero solo habia un  install ok not installed, entonces lo cambie, y creo que ahi la embarre mas:D

Ayudaaa!!!! gracias.

Espero no haberlos aburrido.

---

### Post by bichopro on 2009-06-16
Devuelve "/var/lib/dpkg/status" tal como estabay despues haz esto:

Prueba a hacer lo siguiente en un termianl:

# sudo mv /var/lib/dpkg/info/ /var/lib/dpkg/info_moved

# sudo mkdir /var/lib/dpkg/info

<instala un paquete cualquiera>

# sudo mv /var/lib/dpkg/info/* /var/lib/dpkg/info_moved

# sudo rm /var/lib/dpkg/info

# sudo mv /var/lib/dpkg/info_moved /var/lib/dpkg/info

---

### Post by rapidgarcha on 2009-06-16
Que respuesta tan rápida.

Hice los primeros 3 pasos, pero al querer instalar un nuevo paquete me tira este error:

El índice de software está dañado

Este es un fallo importante en su sistema de gestión de software. Por favor, compruebe si existen paquetes rotos con synaptic, compruebe los permisos y la corrección del archivo «/etc/apt/sources.list» y vuelva a cargar la información del software con: «sudo apt-get update» y «sudo apt-get install -f».

Soy muy nuevo en Ubuntu (se debe notar), si existe la forma de instalar todo el synaptic desde cero no hay problema, total todavia no pude instalar paquetes nuevos, salvo el EnvyNG.

Gracias por responder tan rápido!

---

### Post by armandoesqueda on 2010-07-21
Excelente respuesta. Yo tenía un problema similar y lo único que hice fue fijarme en la línea que me indicaba. Por lo que ví, no era necesario lo que estaba escrito, lo borré y guardé mi sources list y con eso se corrigió el problema. (antes de eso guardé el texto íntegro por si la regaba :p

Saludos!

---

