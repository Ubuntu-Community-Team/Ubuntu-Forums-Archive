---
title: "Linuxs en pendriver"
date: 2009-05-14
forum: Software
---

### Post by Lokkete on 2009-05-14
Hola tengo un pendriver de 32gb y quiero hacerlo booteable para tener varios instaladores de sistemas operativos

basicamente quiero tener varios isos (un par de linux y bue winxp por necesidad no por gusto) y que me aparezca un menue eligiendo que iso quiero que levante....

o si o si tengo que crear varias particiones en el pendriver?


la ida principal es tener unos live de un par de linux, y un par de win

como herramienta para reparaciones.....

---

### Post by emiliano_raso on 2009-05-15
> **Lokkete said:**
> Hola tengo un pendriver de 32gb y quiero hacerlo booteable para tener varios instaladores de sistemas operativos

basicamente quiero tener varios isos (un par de linux y bue winxp por necesidad no por gusto) y que me aparezca un menue eligiendo que iso quiero que levante....

o si o si tengo que crear varias particiones en el pendriver?


la ida principal es tener unos live de un par de linux, y un par de win

como herramienta para reparaciones.....

Jujuju... Eso estaría genial. Pero, como elegis cuando booteas que OS arrancar desde el pen? Tendria que tener un grub propio el pen xD
Tecnicamente es posible, tomando al pendrive como un disco rigido.

Una vez hice eso con kolibrios ([http://es.wikipedia.org/wiki/KolibriOS](http://es.wikipedia.org/wiki/KolibriOS)) pero el problema que tuve es que la transferencia por usb es muy lenta y termina siendo peor.
En kolibrios no me paso, teniendo en cuenta que es un OS que pesa menos de 1mb.
Me pasó cuando en un pen de 2gb instalé DSL.

---

### Post by staar on 2009-05-15
se podría hacer, instalando grub en el MBR del pendrive (si, se puede), pero no se si con 'instaladores', con distros linux completas si, y no se como vendría la mano con los win$...

obligatoriamente tendrías que particionar el pendrive...

saludos

---

### Post by emiliano_raso on 2009-05-15
> **staar said:**
> se podría hacer, instalando grub en el MBR del pendrive (si, se puede), pero no se si con 'instaladores', con distros linux completas si, y no se como vendría la mano con los win$...

obligatoriamente tendrías que particionar el pendrive...

saludos

Como se particiona un pendrive? Me interesó el tema. Quiero hacerlo yo tambien xD

---

### Post by staar on 2009-05-15
igual que cualquier disco, con gparted (Editor de particiones) en ubuntu (tiene que estar desmontado, obvio como cualquier disco)...

saludos

---

