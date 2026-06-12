---
title: "Necesito ayuda para instalar LX-Viewer"
date: 2009-02-13
forum: Software
---

### Post by GGsalas on 2009-02-13
Hola [LX-Viewer]("http://lx-viewer.sourceforge.net/download.php") es un programa libre para poder ver documentos DWG (archivos de Autocad)

No lo pude encontrar en los repositorios. 

La [instalación es desde un archivo .tar.gz]("http://sourceforge.net/project/showfiles.php?group_id=30996&package_id=23055&release_id=315630")

Además hay que instalar las [librerías DWG]("http://www.opendwg.org/"). El link lleva a la web de Open Design Alliance, pero estoy perdido sobre como instalar estas librerias.

Necesito instalarlo. Luego, no estaría mal solicitar que incorporen este programa en los repositorios, pero no se donde se pide eso.

Saludos.

---

### Post by guillermolisi on 2009-02-16
> **GGsalas said:**
> Hola [LX-Viewer]("http://lx-viewer.sourceforge.net/download.php") es un programa libre para poder ver documentos DWG (archivos de Autocad)

No lo pude encontrar en los repositorios. 

La [instalación es desde un archivo .tar.gz]("http://sourceforge.net/project/showfiles.php?group_id=30996&package_id=23055&release_id=315630")

Además hay que instalar las [librerías DWG]("http://www.opendwg.org/"). El link lleva a la web de Open Design Alliance, pero estoy perdido sobre como instalar estas librerias.

Necesito instalarlo. Luego, no estaría mal solicitar que incorporen este programa en los repositorios, pero no se donde se pide eso.

Saludos.
Segun lo que lei en el site de la ODA, para obtener esas librerias DWG y otras piezas de software relacionadas tenes que suscribirte como miembro.

---

### Post by GGsalas on 2009-02-16
> **guillermolisi said:**
> Segun lo que lei en el site de la ODA, para obtener esas librerias DWG y otras piezas de software relacionadas tenes que suscribirte como miembro.

Eso es muy raro, porque para wndows (si no recuerdo mal, voy a verificarlo) te bajás un .exe y ya tenés funcioando LX-Viewer

---

### Post by guillermolisi on 2009-02-16
> **GGsalas said:**
> Eso es muy raro, porque para wndows (si no recuerdo mal, voy a verificarlo) te bajás un .exe y ya tenés funcioando LX-Viewer
Ellos publican software para suscriptos/miembros y para publico en general.
Para este ultimo caso, solo algunos productos, para el primero caso, todos, incluidos los liberados para los no miembros.

Me parece perfecto que lo verifiques porque no estoy exento de equivocarme y haber mal interpretado lo que lei.

---

### Post by GGsalas on 2009-03-05
[SIZE="4"]Encontré la solución [/SIZE](al menos a mi me funcionó)
[RIGHT](con la ayuda de [este hilo en ubuntu-es]("http://www.ubuntu-es.org/index.php?q=node/64050"))
[/RIGHT]

1. Descargar el paquete rpm [ viewer-0.99f-1.mandrake90.i586.rpm...]("http://fr.rpmfind.net/linux/sourceforge/l/lx/lx-viewer/viewer-0.99f-1.mandrake90.i586.rpm")

2. Instalar alien, si no está ya instalado.

3. Generar el paquete .deb    

```
# alien viewer-0.99f-1.mandrake90.i586.rpm
```

4. Instalar el paquete .deb (con doble click) 

5. Ejecutar el programa:
```
cd /usr/local/bin
```
```
viewer
```

Notas:
En mi caso recibí el siguiente error:
```
error while loading shared libraries: libstdc++.so.5:
```

Lo solucioné como se recomienda en [este post]("http://ubuntuforums.org/showpost.php?p=425462&postcount=3"):

- Buscar en Sinaptyc e insalar "libstdc++5"

Yo ya hice el archivo .deb ¿sirve para cualquier computadora, o sólo para la mia? si es así lo subio a mi web. 

Saludos.

---

