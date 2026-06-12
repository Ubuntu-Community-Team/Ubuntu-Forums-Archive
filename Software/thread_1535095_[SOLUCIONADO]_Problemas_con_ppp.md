---
title: "[SOLUCIONADO] Problemas con ppp"
date: 2010-07-20
forum: Software
---

### Post by Primo-de-google on 2010-07-20
bueno tengo este pequeño problema de no poder conectarme a internet

1-hadware implicado: realtek rtl8139/810x family Fast Ethernet Nic
2-vercion de ubuntu: 10.4
3-nombre y vercion del sofware: rp-pppoe v3.8p y pppd 2.4.5
4-como surgio? : al actualizar ubuntu si no me equivoco, el comando apt-get update

y me pregunto si hay aguna forma de volver a instalar ppp atraves del dvd o restaurar el anterior.

ya probe la soluciones como, [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by Patriciologico on 2010-07-21
Hola Primo-de-google

Te recomiendo leer [http://ubuntuforums.org/showthread.php?t=1319475](http://ubuntuforums.org/showthread.php?t=1319475) ya que ingresas a una comunidad nueva es bueno que sigas el orden que llevamos. Tu post fue movido.

Saludos

---

### Post by Carlos C on 2010-07-24
Desde synaptic puedes remover el paquete pppoeconf y chequear la opción que te permite remover incluso los archivos de configuración. Luego la instalación del mismo puede ser igualmente por synaptic. Desde el terminal tienes también más de una opción.
```
sudo apt-get --purge pppoeconf
```

o

```
sudo dpkg --purge pppoeconf
```

---

### Post by Primo-de-google on 2010-07-29
gracias  pero creo que era mas simple 
busque en este mismo foro en ingle i encontre la solucion el tipo tenia el mismo problema 

onda 

sudo /etc/inid.d/networking restart

y listo santo remedio funsiona !

---

