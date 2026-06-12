---
title: "Que me recomiendan instalar?"
date: 2009-03-25
forum: Software
---

### Post by Pampa78 on 2009-03-25
Hola gente! Qué tal? Cómo están? Tengo una vieja pc tirada (Celeron 500 mhz, Mother Pc Chips 755, 128 de RAM y HD de 5 gigas, jamás en mi vida use Linux y quiero empezar a conocerlo, que versión de Linux me recomiendan instalarle? Me bajé una versión de Xubuntu que ahora mismo no recuerdo si es la live o la alternate.
Probé instalar dicha y en un momento luego de esperar varios minutos que desaparezca una pantalla azul con una barra blanca debajo apareció una leyenda que decía que no podía montar el cd rom, trataré de imprimir la pantalla o algo parecido para explicar mejor.
Gracias!
Salu2
Sebastián

---

### Post by Dan_Dranath999 on 2009-03-25
Con tan poco RAM, (menos de 256) no puedes usar el Live CD, tienes que instalar desde el ALTERNATE...

si puedes conseguir una pastilla de ram extra hazlo... (Puedes instalar una distro más pequeña como DamnSmallLinux o Puppy Linux que van con menos de 60 Mb de RAM, pero Xubuntu es que es muy buena opción -yo lo uso en el trabajo en una máquina virtual y estoy pensando instalarlo de verdad)

---

### Post by totolinux on 2009-03-26
hola yo te recomiendo fluxbuntu: 
Fluxbuntu es una distribución GNU/Linux basada en Ubuntu que utiliza el gestor de ventanas Fluxbox, caracterizado por el bajo consumo de recursos necesario para su funcionamiento, en lugar de GNOME. Esto hace adecuada a esta distribución para el uso en máquinas antiguas o con pocos recursos de hardware. (copia de [http://www.guia-ubuntu.org/index.php?title=Fluxbuntu](http://www.guia-ubuntu.org/index.php?title=Fluxbuntu)).
bajalo de aquí 
[http://releases.fluxbuntu.org/7.10/rc/](http://releases.fluxbuntu.org/7.10/rc/)

---

### Post by Pampa78 on 2009-03-26
El cd que me bajé es el altenate, el problema es que me dice que no detecta el cd-rom. alguna vez te pasó lo de la pantalla azul con la franja blanca debajo?, quizá sea el cd que se grabó mal, lo raro es que lo bajé desde la página oficial.

---

### Post by NickCis on 2009-03-26
El problema de fluxbuntu, es que esta desactualizado, usa la vercion 7.10 d ubuntu que dejo de tener soporte...

Te recomiendo Ubuntu Lite, que usa parte de Entorno de LXDE (usa Openbox como window manager y otras cosas).

Ak esta link: [http://u-lite.org/?q=node/2](http://u-lite.org/?q=node/2)

El problema es que el script de instalacion tiene un pequeño problema. Explico como arreglar el problema. Fuente: [http://u-lite.org/?q=node/268](http://u-lite.org/?q=node/268)

Bajamos el script como dice la pagina, pero antes de ejecutarlo.
Nos posicionamos en la carpeta donde esta el archivo y tipeamos en consola "nano install_ubuntulite_nouveau". (Explicacion, nano es un editor de textos de consola si no anda pueden usar el editor "vi")

En el editor figura el siguiente texto:
> #!/bin/bash
#

echo -n "Createing /tmp/ubuntulite for install logs . . ."
sleep 1
mkdir /tmp/ubuntulite
cd /tmp/ubuntulite
echo "[OK]"

echo -n "Testing if your version is supported . . . "
sleep 1
if test $(lsb_release -cs) = "hardy"
then
echo "[OK]"
sleep 1
echo -n "Installing ubuntulite-repository_0.1~ubuntulite~ppa2_all.deb . . ."
sleep 1
wget -q **[COLOR="Red"]http://launchpadlibrarian.net/15491334/ubuntulite-repository_0.1%7Eubuntulite%7Eppa2_all.deb[/COLOR]**
dpkg -i **[COLOR="Red"]ubuntulite-repository_0.1~ubuntulite~ppa2_all.deb[/COLOR]** > repo_log
echo "[OK]"
else
echo "[FAILED]"
exit 1
fi

echo -n "Updating APT package information . . . "
sleep 1
apt-get -y --force-yes update > update_log
echo "[OK]"

echo -n "Updating base packages before installing Ubuntulite . . . "
sleep 1
apt-get -y --force-yes upgrade > upgrade_log
echo "[OK]"

echo -n "Installing Ubuntulite default packages . . . "
sleep 1
apt-get -y --force-yes install ubuntulite-desktop > install_log
echo "[OK]"

echo "Reboot to complete the process."


Lo que esta en rojo es lo que esta mal. Lo primero lo tienen que reemplazar con: 
```
http://ppa.launchpad.net/ubuntulite/ubuntu/pool/main/u/ubuntulite-repository/ubuntulite-repository_0.1-0ubuntulite1_all.deb
``` 
y lo segundo por 
```
ubuntulite-repository_0.1-0ubuntulite1_all.deb
```

Y les quedaria algo asi:

> #!/bin/bash
#

echo -n "Createing /tmp/ubuntulite for install logs . . ."
sleep 1
mkdir /tmp/ubuntulite
cd /tmp/ubuntulite
echo "[OK]"

echo -n "Testing if your version is supported . . . "
sleep 1
if test $(lsb_release -cs) = "hardy"
then
echo "[OK]"
sleep 1
echo -n "Installing ubuntulite-repository_0.1~ubuntulite~ppa2_all.deb . . ."
sleep 1
wget -q **[COLOR="Black"]http://ppa.launchpad.net/ubuntulite/ubuntu/pool/main/u/ubuntulite-repository/ubuntulite-repository_0.1-0ubuntulite1_all.deb[/COLOR]**
dpkg -i **ubuntulite-repository_0.1-0ubuntulite1_all.deb** > repo_log
echo "[OK]"
else
echo "[FAILED]"
exit 1
fi

echo -n "Updating APT package information . . . "
sleep 1
apt-get -y --force-yes update > update_log
echo "[OK]"

echo -n "Updating base packages before installing Ubuntulite . . . "
sleep 1
apt-get -y --force-yes upgrade > upgrade_log
echo "[OK]"

echo -n "Installing Ubuntulite default packages . . . "
sleep 1
apt-get -y --force-yes install ubuntulite-desktop > install_log
echo "[OK]"

echo "Reboot to complete the process."


Despues siguen las instrucciones de la pagina y listo.

Saludos.

---

