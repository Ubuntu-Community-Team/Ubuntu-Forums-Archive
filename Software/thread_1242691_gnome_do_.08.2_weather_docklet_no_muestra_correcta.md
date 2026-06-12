---
title: "gnome do .08.2 weather docklet no muestra correctamente el clima"
date: 2009-08-17
forum: Software
---

### Post by granjero on 2009-08-17
les comento lo que sucede:

al final actualice a 0.8.2 agregando estas dos líneas al sources list

```
deb http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main 
deb-src http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main
```

y después corroborando la key con


```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys (nºque está en la pag de gnome-do)
```

al final

```

sudo apt-get install gnome-do
sudo apt-get install gnome-do-plugins
```

les cuento que me resulta muy cómodo gnome do y el skin docky me gusta más que AWN que es la barra que usaba antes.

pero les quiero preguntar si alguien sabe por que el weather docklet siempre muestra una luna en vez de mostrar el estado del clima?

no importa la hora del día ni el estado del clima... siempre tengo una luna llena...

si pongo otras locaciones muestra las nubes o el sol o la tormenta. pero si configuro buenos aires argentina sin importar el proveedor siempre tengo una luna...

en el chat de #gnome-do en freenode me dijeron que reporte el bug. lo cual hice aqui.
[https://bugs.launchpad.net/do-plugins/+bug/413316](https://bugs.launchpad.net/do-plugins/+bug/413316) 

Así es como se hace?


muchas gracias!

---

### Post by granjero on 2009-09-17
hola gente...  por un problema en el disco rígido (gracias a winxp) tuve que formatear y volver a instalar todo! dios guarde mi backup eternamente!

pensé que al reinstalar el tema del weather docklet se solucionaría pero sigo teniendo el mismo problema...

creo que el dock por algún motivo cree que es siempre de noche porque me muestra la luna en vez del sol cuando lo hay


o una luna nublada en vez del sol con nubes....

los muchachos de launchpad no me atendieron con el bugreport que hice...

alguien de buenos aires que use el docky tiene el mismo problema?


salud!

---

