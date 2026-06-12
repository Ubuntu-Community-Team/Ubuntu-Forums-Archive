---
title: "Kubuntu 11.04 no guarda mi configuracion de video."
date: 2011-06-16
forum: Software
---

### Post by zeroadrenaline on 2011-06-16
La cuestion es simple: configuré todo mi desktop con dual monitor, para que tenga barras locas a los costados, que use un monitor como principal, que use ciertos efectos, etc.

Todo esto desde preferencias del sistema.

Una vez finalizaza la config en la sección monitores di en la opcion:

Guardar como predeterminado -> Guardar como predeterminado.

Hecho esto todos eramos felices, hasta que :

restart kdm

PUUUUFFFFF!!!!!! Nunca guardo la config de mi escritorio.

Esto me trae muchos trastornos y me gustaría saber 2 cosas:

1_ si se puede guardar la config de alguna forma porque es bastante molesto?.
2_ si es un bug reportado, como hacer para saber si es un bug reportado, o como reportarlo en el lugar que corresponde. (kde org, kubuntu, linux foundation, fsf, al anses o donde corno sea)?.

Hardware info: 

Notebook asus k42f

zeroadrenaline@cerebro:~/Documentos$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 18
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:42 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:e080(size=8)

---

### Post by guillermolisi on 2011-06-16
Creo que la mejor forma de guardar esa configuracion es via /etc/X11/xorg.conf. Ahi declaras los dos monitores y la forma en que los queres usar.

Otra para probar: Invoca el utilitario que configura en KDE los dos monitores pero desde consola usando sudo. No vaya a ser cosa que no los guarde por cuestiones de permisos.

Que version de KDE estas usando ? Te recomiendo actualizar a la ultima si aun no lo hiciste (se hace desde un ppa especifico para Kubuntu) porque han solucionado cantidad de bugs e introducido muchas mejoras relacionadas con funcionalidad, estabilidad y consumo de recursos).

---

### Post by zeroadrenaline on 2011-06-16
Voy a probarlo al final del día y te cuento como anduvo. Gracias por la data.

---

### Post by zeroadrenaline on 2011-06-16
Ya agregue el ppa, pero no se a quepaquete hacer referencia para que acutalize. Sabes?. onda, sudo apt-get upgrade y va a descargar la version mas reciente o le pedis algun paquete en particular?.

---

### Post by zeroadrenaline on 2011-06-16
Ya esta, es un sudo apt-get update; sudo apt-get upgrade y se barre con todo, pero me da miedito :S. Es la máquina de la oficina. A las 18 lo pongo, cosa de irme a casa sabiendo que mañana tengo que arreglarlo :D:D:D.

---

### Post by guillermolisi on 2011-06-16
> **zeroadrenaline said:**
> Ya esta, es un sudo apt-get update; sudo apt-get upgrade y se barre con todo, pero me da miedito :S. Es la máquina de la oficina. A las 18 lo pongo, cosa de irme a casa sabiendo que mañana tengo que arreglarlo :D:D:D.
Siempre te conviene un apt-get dist-upgrade por si hay alguna dependencia nueva que agregar.

Vengo haciendo upgrade de KDE desde la version 4.2, que tenia sus cositas aun, pero las ultimas veces resultaron siempre procesos confiables.

Eso si, Synaptic y Aptitude siguen siendo mejores que Kpackagekit. Este ultimo a veces se marea y te da trabajo adicional.

---

### Post by zeroadrenaline on 2011-06-17
Bueno: les cuento que actualicé kde con el repo ppa de kubuntu y resolvió PARTE del problema. Sigue sin guardar algunas configuraciones pero al menos ya toma el dual monitor como corresponde.

Como lo hice?: 

sudo apt-add-repository ppa:kubuntu-ppa

sudo apt-get update

sudo apt-get upgrade

De todas formas, cuando hago:

sudo systemsettings

aparecen algunos errores de permisos, así como un directório faltante. Los agregúe manualmente con mkdir y chown como correspondía y al parecer los errores ya no saltan al principio. Voy a tratar de debugear esto un poco pero ya podemos pasar el hilo a SOLVED ya que los mas crítico esta resuelto.

---

