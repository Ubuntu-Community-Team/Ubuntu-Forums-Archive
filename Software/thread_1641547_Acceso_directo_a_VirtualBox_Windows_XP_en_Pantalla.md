---
title: "Acceso directo a VirtualBox Windows XP en Pantalla Completa"
date: 2010-12-09
forum: Software
---

### Post by kabeza on 2010-12-09
Buenas gente
Resulta que mi viejo no se adapta a Ubuntu, y como todo viejo terco, no hay forma -ni explicandole con paciencia- de hacerle entender que es para mejor.

Se me ocurrió una idea:
- instalar virtualbox
- instalar windows xp home con la licencia de la notebook

Pero ahora tengo una duda

[B]Se podrá crear en el escritorio un acceso directo que permita arrancar dicha maquina virtual en virtualbox en pantalla completa?
[/B]
Desde ya muchas gracias

---

### Post by biale on 2010-12-11
Fijate si este comando hace lo que queres hacer (no lo probe):

VBoxSDL -fullscreen -vm YourVirtualMachine

Si no queres necesariamente una pantalla completa, este es el arranque que uso en un boton del panel:

VirtualBox -startvm  Nombre-de-la-vM

---

### Post by kabeza on 2010-12-13
buenisimo @biale
Funciono de maravillas. Ahora los de Virtualbox deberian hacer un atajo de teclado para minimizar la VM porque al darle CTRL(der)+F cada vez que quiero alternar con Ubuntu, medio que los graficos se c***n un poco (AWN, compiz) pero se restaura todo facilmente al acceder a las propiedades de los themes

---

### Post by guillermolisi on 2010-12-13
Suspende Compiz antes de iniciar la VM, cosa que podes incluir en el lanzador mismo, y te evitas ese inconveniente visual.

---

### Post by kabeza on 2010-12-13
> **guillermolisi said:**
> Suspende Compiz antes de iniciar la VM, cosa que podes incluir en el lanzador mismo, y te evitas ese inconveniente visual.


Alguna forma de hacer un "batch" que haga eso? En el lanzador mismo se puede? Como? osea, 

- desactivar compiz
- ejecutar la VM
- si sale de la vm o cierra la vm, reactivar compiz

estaria bueno que fuese todo automatico, pero quiza ya estoy pidiendo demasiado :P

---

### Post by Wiredfixer on 2010-12-15
Que tan potente es la maquina de tu viejo?

Porque no usas SeamlessRDP...

Esto lo puedes buscar aqui en el foro.. esta bastante bueno y eso uso yo para la empresa donde laboro.. :D

---

### Post by kabeza on 2010-12-16
Por ahora la maquinita se la banca. Puede tener varias apps corriendo en ubuntu y arrancar la maquina virtual de windows sin ningun problema a full screen y correr lo basico, firefox, office, etc. sin trabarse.

Voy a buscar a ver de que trata SeamlessRDP.

---

