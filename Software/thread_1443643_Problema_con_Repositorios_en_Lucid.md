---
title: "Problema con Repositorios en Lucid"
date: 2010-03-31
forum: Software
---

### Post by juancho_777 on 2010-03-31
Hola amigos...
les cuento que desde que acualice mi karmic a lucid, tengo el siguiente error en los repositorios... y seguro es una pavada, pero no logro descular como solucionarlo :)

> Imposible obtener [http://ppa.launchpad.net/c-korn/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/c-korn/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Imposible obtener [http://ppa.launchpad.net/kmess-packages/kmess-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/kmess-packages/kmess-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.

desde ya muchas gracias! un abrazo!

---

### Post by guillermolisi on 2010-03-31
Que mirror estas usando, de donde es ?

---

### Post by juancho_777 on 2010-03-31
estoy usando el mirror de la UBA que hasta ahora es el único que me da una tasa de transferencia de 400kbps.

> [http://ftp.ccc.uba.ar/pub/linux/ubuntu/lucid](http://ftp.ccc.uba.ar/pub/linux/ubuntu/lucid) main 

---

### Post by guillermolisi on 2010-03-31
> **juancho_777 said:**
> estoy usando el mirror de la UBA que hasta ahora es el único que me da una tasa de transferencia de 400kbps.
Te sugiero uses uno aprobado por Canonical.
Por ejemplo
> **South America**
[LIST]
[*][http://mirror.globo.com/ubuntu/releases/]("http://mirror.globo.com/ubuntu/releases/10.04/") (Brazil)
[*][http://mirror.pop-sc.rnp.br/mirror/ubuntu/]("http://mirror.pop-sc.rnp.br/mirror/ubuntu/10.04/") (Brazil)
[*][http://mirror.pop-sc.rnp.br/mirror/ubuntu-releases/]("http://mirror.pop-sc.rnp.br/mirror/ubuntu-releases/10.04/") (Brazil)
[*][http://ubuntu.c3sl.ufpr.br/releases/]("http://ubuntu.c3sl.ufpr.br/releases/10.04/") (Brazil)
[*][http://cl.releases.ubuntu.com/]("http://cl.releases.ubuntu.com/10.04/") (Chile)
[*][http://espelhos.edugraf.ufsc.br/ubuntu-releases/]("http://espelhos.edugraf.ufsc.br/ubuntu-releases/10.04/") (Brazil)
[/LIST]
extractado de [http://www.ubuntu.com/testing/lucid/beta1](http://www.ubuntu.com/testing/lucid/beta1)

---

### Post by juancho_777 on 2010-03-31
el problema continúa (ya probe con cada uno de esos mirrors)...
pero hay que notar que el error que me esta dando no es del mirror de la UBA... sino del repo ppa.launchpad.net (ver primer post)

Gracias igual por la ayuda! :)

---

### Post by guillermolisi on 2010-03-31
Si, vi que por donde viene el error pero no seria ni la primera ni la ultima vez que algun paquete en el mirror que estes usando no este consistente. De hecho con los problemas de los mirrors de Argentina estoy usando los de Brasil y desde entonces las actualizaciones han dejado de tener problemas.

Suponiendo que en el mirror este todo bien, habria que ver si no estan trabajando sobre esos paquetes, es decir, como son repos daily build estan en continua modificacion. Tal vez mas adelante se normalicen y dejen de dar error, pero lo que digo son conjeturas basadas en experiencia personal, no necesariamente este caso debe coincidir.

---

### Post by sebastianabate on 2010-04-01
El problema es que esos repos que tenés activos todavía no tienen paquetes para lucid, y por eso te tira error al tratar de descargar el listado de los mismos. Para confirmar esto tenés que copiar en firefox la dirección del repo sin la parte que hace referencia a lucid, si usamos como ejemplo este repo

[http://ppa.launchpad.net/kmess-packages/kmess-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/kmess-packages/kmess-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz)

tenés que copiar esa dirección, pegarla en firefox y borrarle todo lo que está después de dists, te quedaría así

[http://ppa.launchpad.net/kmess-packages/kmess-stable/ubuntu/dists/](http://ppa.launchpad.net/kmess-packages/kmess-stable/ubuntu/dists/)

cuando le das enter te va a mostrar un listado de directorios con los nombres de las distribuciones para los que tiene paquetes, en este caso Intrepid, Jaunty y Karmic, pero no Lucid.

Para solucionarlo tenés dos opciones:

1) Deshabilitar los mirrors
Y esperar hasta que tengan paquetes para Lucid para volverlos a reactivar.

2) Modificar el sources.list
Y reemplazar lucid por karmic, de esta forma vas a tener los paquetes disponibles, pero corrés el riesgo de tener problemas con las dependencias.

---

