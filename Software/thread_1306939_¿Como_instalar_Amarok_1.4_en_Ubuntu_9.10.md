---
title: "¿Como instalar Amarok 1.4 en Ubuntu 9.10?"
date: 2009-10-30
forum: Software
---

### Post by emiliano_raso on 2009-10-30
Hola gente. Acabo de instalar Ubuntu 9.10, pero como hago para instalar Amarok 1.4?
Porque desde los repositorios me instalar Amarok2 y realmente no me gusta nada.

Gracias. Saludos...

---

### Post by BlackHero on 2009-10-30
hola proba bajandolo 

[amarok-1.4]("http://ftp.us.debian.org/debian/pool/main/a/amarok/amarok_1.4.10-2_i386.deb")

en el caso de que no funcione el .deb instalate el engine

sudo aptitude install amarok-arts
sudo aptitude install amarok-engines


saludos

---

### Post by Carlos C on 2009-10-30
Prueba con este PPA:

[https://launchpad.net/~bogdanb/+archive/amarok14](https://launchpad.net/~bogdanb/+archive/amarok14)

ignoro si resultará en Karmic, pero hasta Jaunty no daba problemas e incluso podías tener amarok 2 instalado al mismo tiempo.

Saludos.

---

### Post by emiliano_raso on 2009-11-02
Hola muchachos, gracias por responder.

@BlackHero: No funcionó. Al querer instalarlo hay fallas de dependencias, y al resolverlas, me instala Amarok2. Lo desinstalo y vuelvo al mismo punto de partida, y termina siendo un ciclo infinito.

@Carlos C: Perdon mi ignorancia, pero cuales serian los pasos para instalarlo?

Gracias.

---

### Post by guillermolisi on 2009-11-02
> **emiliano_raso said:**
> Hola muchachos, gracias por responder.

@Carlos C: Perdon mi ignorancia, pero cuales serian los pasos para instalarlo?

Gracias.
Considerando que Carlos C habla de un PPA, se me ocurre que la instalacion de esa version de Amarok se realizaria via Gestor de Software al haber incluido ese repositorio presonal a la lista de repos de tu maquina (es asi Carlos ?)

---

### Post by emiliano_raso on 2009-11-02
AH! YA ESTÁ!
Tenía que clickéar en la flechita de "Technical details about this PPA" :-P

No sabia que podes usar los repositoriso de versiones viejas de Ubuntu en las mas nuevas.

Cuando le pongo para agregar la clave me hace lo siguiente:

```
emiliano@emiliano-laptop:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \ 0x1d7e9dd033e89ba781e32a24b9f1c432ae74ae63
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com  0x1d7e9dd033e89ba781e32a24b9f1c432ae74ae63
gpg: solicitando clave AE74AE63 de hkp servidor keyserver.ubuntu.com
```

Y ahi se queda. :-S

Saludos

EDIT: Listo, ya está. Tardó casi un minuto en agregar la clave :-S Pero lo hizo.

---

### Post by emiliano_raso on 2009-11-02
Ya lo instalé.
**Para instalar Amarok 1.4 en Ubuntu 9.10 es el mismo procedimiento que para Ubuntu 9.04**
El tema es que no sabía que podias agregar los repositorios de 9.04 en 9.10.
Gracias Carlos.

PD: Puse en negrita esa frase por si alguien llega a este thread, que no se lea todo :-P
PD2: Guille, marcá como solved nomas.

---

### Post by Carlos C on 2009-11-08
Perdón por no responder en su momento, estuve muy ocupado. De todas maneras me alegro que mi intervención no resultó fundamental y lo solucionaron.

Saludos.

---

