---
title: "Instalar solo el grub."
date: 2008-09-24
forum: Software
---

### Post by h9005 on 2008-09-24
Buenas se me daño el mbr por un virus en windows y al sobreescribirlo murio el grub. Como hago para instalar solo este componente? Porque desde el dvd de ubuntu studio la instalacion de grub implica aparentemente instalar todo el SO.

---

### Post by Mauro22 on 2008-09-24
Arranca con un livecd.

Una vez ahi, abris una consola y pones:

```
sudo grub
```Te va a quedar algo asi

```
grub>
```Ahi pones esto:

```
find /boot/grub/stage1
```y te va devolver algo como esto:

```
(hdx,y)
```Ahora pones:

```
root (hdx,y) *O sea usando los datos que te dio antes
```y por ultimo:

```
setup (hdx)
```Listo!:guitar:

Ejemplo:

sudo grub
grub> find /boot/grub/stage1
(hd0,1)
root (hd0,1)
setup (hd0)

---

### Post by h9005 on 2008-09-24
Ok gracias voy a probarlo. Quien es la chica de la foto?

---

### Post by leo_rockway on 2008-09-24
> **h9005 said:**
> Quien es la chica de la foto?

Francesca Lee y no tiene absolutamente nada que ver con Mozilla. La foto está GIMPeada.

EDIT: estaba aburrido y... arregle la foto xD. Ahora es GPL (?)
Qué manera de hijackear un thread la mía.

---

### Post by h9005 on 2008-09-25
Tiene una cara de monja barbara esa chica la foto es de alguna publicación eclesiastica?

---

### Post by lega on 2008-09-26
> **leo_rockway said:**
> 
EDIT: estaba aburrido y... arregle la foto xD. Ahora es GPL (?)
Qué manera de hijackear un thread la mía.

jajaja me encantó!!!! que maestro!

---

### Post by faktorqm on 2008-09-27
perdoname, pero quien le va a mirar el dibujito de la remera?!?!?! jajajaj

---

### Post by leo_rockway on 2008-09-27
> **faktorqm said:**
> perdoname, pero quien le va a mirar el dibujito de la remera?!?!?! jajajaj

Y... antes nadie porque no era GPL...

---

### Post by feche_mza on 2008-10-08
> **faktorqm said:**
> perdoname, pero quien le va a mirar el dibujito de la remera?!?!?! jajajaj
[B][I]
lo interesante es lo que esta detrás de la remera[/I][/B]

---

