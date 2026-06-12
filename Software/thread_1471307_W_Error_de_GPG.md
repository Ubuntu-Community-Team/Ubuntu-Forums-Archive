---
title: "W: Error de GPG:"
date: 2010-05-03
forum: Software
---

### Post by prostata on 2010-05-03
a la hora de instalar pero sobre todo al desinstalar algo en el nuevo Lucid, o simplemente de recargar los repos de Sinaptyc, me manda el siguiente error, he mirado por la red pero no encuentro como solucionarlo, ¿alguien sabe cómo.

W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY E2548F216D8739DC

Saludos

---

### Post by santiagoward2000 on 2010-05-03
Hola!
¿Agregaste algún repositorio PPA? Parece que eso es lo que está molestando. Probá desactivarlo desde **Software Sources** y recargar los repositorios de nuevo.
Saludos!

---

### Post by prostata on 2010-05-03
Gracias, tenía uno de getdeb hice la prueba y funciono. No obstante sigo con otro problema en Synaptic, que no es otro que al instalar alguna cosa, por ejemplo gimp-plugin-register de gimp, me responde con otro error:

E: No se pudo tratar el archivo de paquetes /var/lib/apt/lists/es.archive.ubuntu.com_ubuntu_dists_lucid_main_i18n_Translation-es (2)
E: No se ha podido bloquear el directorio de descargas

y también miré por la red, pero algunos opinan que es un bug y otros simplemente no saben.  gracias

Saludos

---

### Post by mpsz on 2010-05-03
A mi me pasa lo mismo:

E: No se pudo bloquear /var/cache/apt/archives/lock - open (11: Recurso temporalmente no disponible)
E: No se ha podido bloquear el directorio de descargas

No puedo actualizar nada, ni con el gestor synaptic ni con el administrador de actualizaciones.

---

### Post by guillermolisi on 2010-05-03
Ese comportamiento de apt-get/Synaptic ocurre cuando se instala por lo menos Español para que el SO este en ese idioma. Es un bug que se reporto durante la Global Jam en Buenos Aires (Z37A hizo una actualizacion con la ultima version beta y venia bien hasta que agrego el paquete de Español).

Si utilizan Aptitude no tendran ese problema, podran actualizar e instalar paquetes sin inconvenientes y podran usarlo en forma similar al apt-get o a Synaptic (CLI o con menues, respectivamente).

---

### Post by mpsz on 2010-05-03
Hola,
Lo solucioné buscando en el foro de español general.

En un post pusieron el siguiente script.
No tengo idea que es lo que hace, pero me solucionó el problema.
Aparentemente es cuando se interrumpe una actualización y queda bloqueado para iniciar una nueva.

sudo mv /var/lib/dpkg/lock /var/lib/dpkg/lock.copia
sudo mv /var/lib/aptitude/lock /var/lib/aptitude/lock.copia
sudo mv /var/cache/apt/archives/lock /var/cache/apt/archives/lock.copia
sudo mv /var/lib/apt/lists/lock /var/lib/apt/lists/lock.copia
sudo mv /var/lock/aptitude /var/lock/aptitude.copia

Algunos comandos me dieron algun mensaje de error pero me funcionó.
Este es el post.
[http://www.ubuntu-es.org/?q=node/86255](http://www.ubuntu-es.org/?q=node/86255)

Saludos

---

### Post by prostata on 2010-05-04
Estimad@s, encontré la solución a casi todos los problemas, y la misma me constata que esta versión salió con demasiada prontitud y falta de testeo. No ha sido otra cosa que cambiar el idioma de todo el escritorio y se solucionó el problema. Pasé de castellano a en mi caso catalán, y todo arreglado, aunque seguro que podría también solucionarse pasando a idioma inglés, o france&#347; o algo por el estilo.

Saludos

---

