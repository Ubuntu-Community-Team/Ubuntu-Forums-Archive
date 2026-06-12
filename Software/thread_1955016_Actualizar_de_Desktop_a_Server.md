---
title: "Actualizar de Desktop a Server"
date: 2012-04-09
forum: Software
---

### Post by Brath-ga on 2012-04-09
Hola a todos.

Tengu un PC de sobremesa perfectamente configurado con Ubuntu Desktop 10.10.

Mañana dia 10 de Abril termina la vida útil de esta distro y quisiera actualizar a Ubuntu Server 10.10 para no perder nada sabiendo que le quedan aún 3 años de soporte.

Tengo "googleado" buscando información de como hacerlo y encontré soluciones discrepantes.

Podríais aclararme los pasos necesarios para dicha actualización.

---

### Post by gmunioz on 2012-04-09
Te sugiero actualizarte a Ubuntu 12.04, o esperas la salida definitiva o utilizas el daylibuild alternate, que poco le falta para ser definitivo.
Aqui los cds de hoy:
[http://cdimage.ubuntu.com/daily/current/precise-alternate-amd64.iso](http://cdimage.ubuntu.com/daily/current/precise-alternate-amd64.iso)
(64 bits)
[http://cdimage.ubuntu.com/daily/current/precise-alternate-i386.iso](http://cdimage.ubuntu.com/daily/current/precise-alternate-i386.iso)
(32 bits)
El procedimiento consiste en:
Bajar la imagen.
Grabarla con la opción grabar cd, en un dvd de preferencia.
Desactivar el salvapantallas y el gestor de energía
Reintroducir el cd/dvd, estando conectado a Internet.
Aceptar las sugerencias de actualizar el sistema y bajar los paquetes faltantes de internet.
En mi caso, con Xubuntu, con 1900 paquetes, en 6 horas a unos 50 kb/s, tenía el sistema actualizado y funcionante.
Si se corta la luz durante la bajada, solo se pierde tiempo.
Si se corta, durante la actualizaciòn de los paquetes, se puede perder el sistema, hay que trabajar en consola con dpkg y apt-get para recuperarlo.
Si no aceptas bajar paquetes de internet, se actualiza parcialmente y mucho más rápido, requiriendo synaptic o apt-get posterior para completar la actualizaciòn de los paquetes.
11.10 y 12.04 traen Unity y Gnome 3, si no te agradan, Xubuntu es bastante parecido al tradicional Gnome, en ese caso debes instalar xubuntu-desktop, reiniciar con el y utilizar el alternate de xubuntu
[http://cdimage.ubuntu.com/xubuntu/daily/current/precise-alternate-amd64.iso](http://cdimage.ubuntu.com/xubuntu/daily/current/precise-alternate-amd64.iso)
(64 bits)
[http://cdimage.ubuntu.com/xubuntu/daily/current/precise-alternate-i386.iso](http://cdimage.ubuntu.com/xubuntu/daily/current/precise-alternate-i386.iso)
(32 bits)
Lo estoy usando sin más problema que actualizar paquetes cada 3 o 4 días en aproximadamente 60 á 90 megas.

---

### Post by hictio on 2012-04-09
> **Brath-ga said:**
> Hola a todos.

Tengu un PC de sobremesa perfectamente configurado con Ubuntu Desktop 10.10.

Mañana dia 10 de Abril termina la vida útil de esta distro y quisiera actualizar a Ubuntu Server 10.10 para no perder nada sabiendo que le quedan aún 3 años de soporte.

Tengo "googleado" buscando información de como hacerlo y encontré soluciones discrepantes.

Podríais aclararme los pasos necesarios para dicha actualización.

Pero la prolongación del soporte que obtenés es para Server, las aplicaciones que usás día a día en un Desktop normal (browsers, clientes de email, IM, etc) tienen update?

---

### Post by guillermolisi on 2012-04-09
> **Brath-ga said:**
> Hola a todos.

Tengu un PC de sobremesa perfectamente configurado con Ubuntu Desktop 10.10.

Mañana dia 10 de Abril termina la vida útil de esta distro y quisiera actualizar a Ubuntu Server 10.10 para no perder nada sabiendo que le quedan aún 3 años de soporte.

Tengo "googleado" buscando información de como hacerlo y encontré soluciones discrepantes.

Podríais aclararme los pasos necesarios para dicha actualización.
Me parece que no es asi como pensas.

En la [wiki de Ubuntu]("https://wiki.ubuntu.com/Releases") que documenta el ciclo de soporte de cada version no dice que la 10.10 Server tenga 3 años de soporte (ademas, en el mejor de los casos son 3 años a partir de su fecha de lanzamiento, no desde que fue instalado).

Las unicas versiones con soporte mayor a 18 meses son las LTS y la 10.10 no es de esa clase, sea o no server, a menos que haya interpretado mal la informacion que se brinda.

---

### Post by guillermolisi on 2012-04-10
> **hictio said:**
> Pero la prolongación del soporte que obtenés es para Server, las aplicaciones que usás día a día en un Desktop normal (browsers, clientes de email, IM, etc) tienen update?

Solamente si la actualizacion involucra una cuestion de seguridad.

---

### Post by Brath-ga on 2012-04-10
Tienes razón Guillermo.

Revisando los ciclos de vida de Ubuntu, acabo de comprobar que solo la versión Server de las LTS tienen una vida de 5 años, Las otras Server duran lo mismo que las Desktop.

Esperaré a que salga la 12.04 e instalaré la versión Desktop con "gnome-fallback".

Gracias por vuestras aportaciones.

---

### Post by EnriqueK on 2012-04-10
Pienso que después de 18 neses de soporte, no creo que sean necesarias actualizaciones para corregir defectos, por eso sugiero que veas la alternativa de cambiar los repositorios a old-releases, de esa manera vas a poder seguir instalando paquetes nuevos, aunque no tendrás actualizaciones, para el caso de Maverick , cambia su /etc/sources.list por la siguiente.
    deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) maverick main restricted universe multiverse
    deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) maverick main restricted universe multiverse

    deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) maverick-updates main restricted universe multiverse
    deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) maverick-updates main restricted universe multiverse

    deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) maverick-security main restricted universe multiverse
    deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) maverick-security main restricted universe multiverse

    deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
    deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse 

Yo al menos pienso hacer esto cuando se acabe el soporte de la 10.04 LTS que será dentro de 1año ya que no pienso tener Unity ni Gnome3, ambos dos son inaceptables para equipos de escritorio.

---

### Post by Lemuriano on 2012-04-10
Actualicé de 10.04 a 12.04, luego le instalé el escritorio de xubuntu y  estoy bien satisfecho, especialmente con el nivel de personalización  que permite Xubuntu.

---

