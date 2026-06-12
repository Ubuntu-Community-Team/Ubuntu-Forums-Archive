---
title: "problemas con ubuntu-netbook-remix en karmic"
date: 2010-04-04
forum: Software
---

### Post by donmatas on 2010-04-04
Hola a tod@s

estoy habilitando un toshiba nb200 (netbook) con ubuntu. Tras muchas dificultades, instalé karmic desde jaunty para luego poner algunos apletts de la distro UNR (no pude instalar directametne ubuntu-netbook-remix 9.10 pues da un problema con el núcleo). El más importante es el launcher-launcher. El problema es que pese a que lo tengo entre las "aplicaciones al inicio" algunas veces simplemente no carga y tengo que reiniciar la máquina ya qeu si lo lanzo dice que ya está corriendo (de hecho antes de reinicarse aparece el escritorio del applet)

¿alguien tiene idea como solucionar esta vaina?
saludos 

DM

---

### Post by donmatas on 2010-04-04
> **donmatas said:**
> Hola a tod@s

estoy habilitando un toshiba nb200 (netbook) con ubuntu. Tras muchas dificultades, instalé karmic desde jaunty para luego poner algunos apletts de la distro UNR (no pude instalar directametne ubuntu-netbook-remix 9.10 pues da un problema con el núcleo). El más importante es el launcher-launcher. El problema es que pese a que lo tengo entre las "aplicaciones al inicio" algunas veces simplemente no carga y tengo que reiniciar la máquina ya qeu si lo lanzo dice que ya está corriendo (de hecho antes de reinicarse aparece el escritorio del applet)

¿alguien tiene idea como solucionar esta vaina?
saludos 

DM

Holanda:

lo solucioné instalando unr completo y luego purgando ubuntu-desktop

```
sudo apt-get install netbook-launcher ubuntu-netbook-remix
```

reinicia

```
sudo apt-get purge ubuntu-desktop
```

reinicia

salud
DM

---

