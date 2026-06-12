---
title: "Problemas para actualizar de 9.10 a 10.04"
date: 2010-05-11
forum: Software
---

### Post by Rodrigo6375 on 2010-05-11
Hola, estoy queriendo actualizar desde el Gestor de Actualizaciones a Ubunto 10.04 LTS pero me informa que algunos paquetes no pueden ser descargados.  

Cuando intento buscar esos paquetes manualmente me parece el mensage "Forbidden" en el navegador.

Alguien sabrá como solucionar esto? y de paso pregunto, los contenidos de mis carpetas (documentos, música, etc) se conserva luego de la actualización? Es la primera vez que actualizo así, las veces anteriores formatee la PC.

Transcribo el mensaje que me pone el Gestor de Actualizaciones:

Failed to fetch [http://ar.archive.ubuntu.com/ubuntu/pool/universe/n/nautilus-cd-burner/libnautilus-burn4_2.25.3-0ubuntu4_i386.deb](http://ar.archive.ubuntu.com/ubuntu/pool/universe/n/nautilus-cd-burner/libnautilus-burn4_2.25.3-0ubuntu4_i386.deb) 403  Forbidden
Failed to fetch [http://ar.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-pptp/network-manager-pptp_0.8-0ubuntu3_i386.deb](http://ar.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-pptp/network-manager-pptp_0.8-0ubuntu3_i386.deb) 403  Forbidden
Failed to fetch [http://ar.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-pptp/network-manager-pptp-gnome_0.8-0ubuntu3_i386.deb](http://ar.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-pptp/network-manager-pptp-gnome_0.8-0ubuntu3_i386.deb) 403  Forbidden
Failed to fetch [http://ar.archive.ubuntu.com/ubuntu/pool/main/p/policykit-desktop-privileges/policykit-desktop-privileges_0.1_all.deb](http://ar.archive.ubuntu.com/ubuntu/pool/main/p/policykit-desktop-privileges/policykit-desktop-privileges_0.1_all.deb) 403  Forbidden
Failed to fetch [http://ar.archive.ubuntu.com/ubuntu/pool/main/t/ttf-kacst-one/ttf-kacst-one_3.0-1ubuntu2_all.deb](http://ar.archive.ubuntu.com/ubuntu/pool/main/t/ttf-kacst-one/ttf-kacst-one_3.0-1ubuntu2_all.deb) 403  Forbidden
Failed to fetch [http://ar.archive.ubuntu.com/ubuntu/pool/main/t/ttf-takao/ttf-takao-pgothic_003.02.01-2ubuntu1_all.deb](http://ar.archive.ubuntu.com/ubuntu/pool/main/t/ttf-takao/ttf-takao-pgothic_003.02.01-2ubuntu1_all.deb) 403  Forbidden

---

### Post by guillermolisi on 2010-05-11
Cambia de mirror. Los de Argentina funcionan mal. Proba con alguno de Brasil o con los centrales.

---

### Post by chivuntu on 2010-05-11
Tengo el mismo problema, pero cuando quiero cambiar de origen no me deja, insiste con el servidor de Argentina. Es porque tiene un paquete a medio bajar???

---

### Post by Rodrigo6375 on 2010-05-11
Y cómo cambio los mirror? a dónde voy? y cuáles son los de brasil?

Gracias!!

> **guillermolisi said:**
> Cambia de mirror. Los de Argentina funcionan mal. Proba con alguno de Brasil o con los centrales.

---

### Post by guillermolisi on 2010-05-11
> **Rodrigo6375 said:**
> Y cómo cambio los mirror? a dónde voy? y cuáles son los de brasil?

Gracias!!
[En este thread]("http://ubuntuforums.org/showthread.php?t=1466816") se explica como proceder al cambio y como saber de donde son los mirrors.

---

### Post by Rodrigo6375 on 2010-05-11
Muchisimas Gracias!!!



> **guillermolisi said:**
> [En este thread]("http://ubuntuforums.org/showthread.php?t=1466816") se explica como proceder al cambio y como saber de donde son los mirrors.

---

### Post by guillermolisi on 2010-05-11
Contanos como te fue asi vemos si damos por resuelto el thread.

---

### Post by Rodrigo6375 on 2010-05-12
El problema se soluciono, en realidad quedaban muy pocos paquetes por descargar, así que fue rápido.

Lo único que noté, que no se si es importante o no, es que cuando cambié los orígenes de Soft y se actualizaron, todos los que figuraban como Traslation-es me daban fail. 

La actualización se llevo a cabo perfectamente, salvo por un error de mi parte, al momento de elegir la partición donde poner el grub, me equivoque y no marque la que era :(

[Dejo la cita de otro Thred, por si alguien pode darme una mano es ese.]("http://ubuntuforums.org/showthread.php?p=9286990#post9286990")

Gracias


> **Rodrigo6375 said:**
> Tengo un problema con el GRUB:

Acabo de actualizar de 9.10 a 10.04 y en la parte donde me dice que elija en que partición instalarlo, me equivoqué. :(

Luego de terminar y reiniciar, me devuelve una linea de comando que menciona que no encuentra no se que del GRUB.

Alguien sabe como puedo arreglar esto desde la linea de comando, o de alguna otra forma? :confused:

No quiero perder los contenidos de las carpetas de Ubuntu ni una unstalación de WinXP que conservo por temas laborales.

Muchas Gracias

---

### Post by Rodrigo6375 on 2010-05-13
Resolví el tema del GRUB con el Super GRUB Disk, [dejo el enlace]("http://ubuntuforums.org/showpost.php?p=9292250&postcount=7").

Hoy por la noche voy a hacer la actualización de mi netbook (Asus) haciendo la modificación del origen de soft desde el arranque, y luego comento.

---

### Post by Rodrigo6375 on 2010-05-17
El fin de semana actualicé el Ubuntu de mi netbook (Asus eeePC 1000HA)

Hice el cambio de orígenes de soft, pero con una variación. En la pantalla de selección de servidor (Sistema/Administración/Origenes de sift / descargar desde... / Otro ...) Hay un botón que dice "Seleccionar mejor servidor"

Este botón lo que hace es hacer pings a todos los servidores y elegir el que da mejor respuesta.

No recuerdo haber visto este botón la primera vez, pero seguro fue distracción mía.

como resultado eligió el nuevo servidor que realizó la descarga de 1631 paquetes (casi 700mb) en una conexión de 1mega (cableada no wifi) en 30 minutos. En total la actualización llevó 3.35 hs.

Un éxito total.

Y como dato extra, ahora me aparecen 3 opciones de servidores para argentina, uno es de la UBA, habrá que probar si son mejores.

Vuelvo a agradecer por la ayuda.

Rodrigo



P.D.: Todavía no entiendo como pude usar windows alguna vez :P :lolflag:

---

