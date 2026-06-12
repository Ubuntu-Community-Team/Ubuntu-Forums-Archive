---
title: "Problemas en  Kubuntu 13.04 para instalar compiz y efectos extras"
date: 2013-09-05
forum: Software
---

### Post by leonardomdq on 2013-09-05
Hola chicos, de vuelta despues de mucho tiempo que estube alejado de la tecnologia y de linux. :D
Ayer instale en mi maquina Kubuntu 13.04, anda de maravillas la verdad pero tengo **problemas para instalar compiz-fusion y los efectos burn y demas**. Conclusion termine de desinstalando todos los paquetes.
Podrian darme una mano para poder instalar y configurar compiz? desde ya muchas gracias. ):P

La grafica que tengo es una placa Asus 210 Silent (GeForce) 1 gb DDR3

---

### Post by gmunioz on 2013-09-07
Abre una terminal.
Ejecuta en ella:
> sudo su
apt-get install compiz compizconfig-settings-manager compiz-kde compiz-fusion-plugins-main compiz-fusion-plugins-extra emerald librsvg2-common fusion-icon

> K menu -- System Settings -- Advanced -- Session Manager -- Window Manager -- Compiz 
K menu -- Settings -- CompizConfig Settings Manager 
K menu -- System -- Compiz Fusion Icon 
Fuente: [http://ubuntuguide.org/wiki/Kubuntu_Precise_Desktop_Add-ons#Compiz_Fusion](http://ubuntuguide.org/wiki/Kubuntu_Precise_Desktop_Add-ons#Compiz_Fusion)

---

### Post by leonardomdq on 2013-09-07
Hola, gracias por responder, me tira que no encuentra los paquetes.

root@Kubuntu:/home/leonardo# sudo apt-get install compiz compizconfig-settings-manager compiz-kde compiz-fusion-plugins-main compiz-fusion-plugins-extra emerald librsvg2-common fusion-icon
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se ha podido localizar el paquete compiz-kde
E: No se ha podido localizar el paquete compiz-fusion-plugins-main
E: No se ha podido localizar el paquete compiz-fusion-plugins-extra
E: No se ha podido localizar el paquete emerald

---

### Post by dirty fingers on 2013-10-23
Igual con compiz en entorno KDE se te descontrola todo y luego de hacerlo andar vas a terminar sacándolo. Quedate con el Kwin que tiene buenos efectos y esta perfectamente diseñado para el resto.

---

