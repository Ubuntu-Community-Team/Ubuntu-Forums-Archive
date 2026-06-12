---
title: "Actualizar distribucion por consola"
date: 2010-09-27
forum: Software
---

### Post by javierlinux1 on 2010-09-27
Buenas noches, estoy buscando (y no encuientro) la forma de actualizar la version de Ubuntu de Karmic a Lucid, pero en un sistema de consola. No tengo instalada la grafica y quiero actualizar la version.
Creia que con "apt-get dist-upgrade" se hacia, pero lo ejecute y al hacer un cat /etc/issue me sigue mostrando "Ubuntu 9.10 /n /l"

Si alguien me indica, agradecido
Saludos

Javier

---

### Post by guillermolisi on 2010-09-27
Publicado en [Ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu:Lucid"):

> Upgrading Jaunty or Karmic to Lucid

Also see the official Ubuntu desktop upgrade documentation.

There are several methods for upgrades from the command-line interface (Terminal) (which can be used for both the desktop and server editions of Ubuntu/Kubuntu).

This is the preferred method:
```
sudo apt-get install update-manager-core
sudo do-release-upgrade

```You can also use the update-manager (all editions):
```
sudo apt-get install update-manager
sudo update-manager -d

```You can also use:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```(Note: the first two lines simply make sure your current distribution is current before upgrading the entire distribution, and are optional.

---

### Post by javierlinux1 on 2010-09-28
Gracias Guille, con las dos primeras lineas quedó solucionado, hace 5 minutos que comenzó la actualización.

Lo que me llama la atención es que el apt-get dist-upgrade lo habia probado varias veces y siempre devolvía "0 paquetes para actualizar, 0 para instalar, 0 para remover" y de ahi salia al prompt, sin hacer nada.

Gracias de nuevo y saludos

---

