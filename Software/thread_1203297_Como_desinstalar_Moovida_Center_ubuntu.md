---
title: "Como desinstalar Moovida Center ubuntu"
date: 2009-07-03
forum: Software
---

### Post by AlvaroV on 2009-07-03
Lo instale para probarlo, no me funciono bien y ahora no se como desintalarlo (no aparece en Synaptic)..

---

### Post by moreback on 2009-07-03
Si no dices como lo instalaste no podemos ayudarte en como desinstalarlo. Y por lo visto no fue una instalación estándar ya que dices que no aparece en Synaptic.

---

### Post by RafaelG on 2009-07-03
> **AlvaroV said:**
> Lo instale para probarlo, no me funciono bien y ahora no se como desintalarlo (no aparece en Synaptic)..


Debieras revisar como dice Moreback  la instalacion Standar, Moovida tiene conflictos con versiones previas de Elisa, por eso te recomiendo leas este Link de como instalar Moovida:

[http://www.moovida.com/wiki/Distribution/LinuxPackages](http://www.moovida.com/wiki/Distribution/LinuxPackages)

Saludos

---

### Post by radixs on 2009-07-03
> **AlvaroV said:**
> Lo instale para probarlo, no me funciono bien y ahora no se como desintalarlo (no aparece en Synaptic)..

Puedes buscar el paquete y desintalarlo

```
apt-cache search *nombre del paquete*
```

Y despues lo quitas ;)

---

### Post by AlvaroV on 2009-07-03
La verdad que no recuerdo como lo instale, lo que si me acuerdo fue que agregue al source list sus repositorios y luego parece que hice un sudo aptitude ....

de todas maneras la busqueda me da:

xxx@xxxxx:~$ apt-cache search Moovida
python-moovida - media center solution - Python library
moovida - media center solution - runtime executables
moovida-plugins-bad - Moovida plugins from the "bad" set
moovida-plugins-good - Moovida plugins from the "good" set
moovida-plugins-ugly - Moovida plugins from the "ugly" set
casa@casa-desktop:~$

---

### Post by radixs on 2009-07-04
> **AlvaroV said:**
> La verdad que no recuerdo como lo instale, lo que si me acuerdo fue que agregue al source list sus repositorios y luego parece que hice un sudo aptitude ....

de todas maneras la busqueda me da:

xxx@xxxxx:~$ apt-cache search Moovida
python-moovida - media center solution - Python library
moovida - media center solution - runtime executables
moovida-plugins-bad - Moovida plugins from the "bad" set
moovida-plugins-good - Moovida plugins from the "good" set
moovida-plugins-ugly - Moovida plugins from the "ugly" set
casa@casa-desktop:~$

para desintalar

```
# apt-get remove *nombre del paquete*
```

---

### Post by CdK1 on 2009-07-04
sudo apt-get autoremove moovida

Ysí, sabemos cual es tu $USER;

xxx@xxxxx:~$ apt-cache search Moovida
casa@casa-desktop:~$

;)

---

### Post by AlvaroV on 2009-07-05
Gracias se desintalo. Lo sorprendente es que era una orden tan fácil.  

Con respecto al User, bueno que le vamos a hacer se caen los aviones y no me voy a a caer yo.:p

---

### Post by Patriciologico on 2009-07-06
> **AlvaroV said:**
> Con respecto al User, bueno que le vamos a hacer se caen los aviones y no me voy a a caer yo.:p

:lolflag: lo simpático es que ocultabas "casa" yo pensé que era algo mas indiscreto

---

