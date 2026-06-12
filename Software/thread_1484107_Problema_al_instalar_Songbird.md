---
title: "Problema al instalar Songbird"
date: 2010-05-15
forum: Software
---

### Post by dam1977 on 2010-05-15
Como Songbird no viene en los repositorios de Ubuntu 10.04, Lo intenté descargar de Getdeb. Pero al terminar la descarga me aparecen los siguientes mensajes: > Error de GPG: [http://packages.medibuntu.org]("http://packages.medibuntu.org/") lucid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2EBC26B60C5A2783Imposible obtener cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)/dists/lucid/main/binary-i386/Packages.gz  Por favor utilice apt-cdrom para hacer que APT reconozca este CD. apt-get update  no se puede usar para agregar nuevos CDs
Imposible obtener cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)/dists/lucid/restricted/binary-i386/Packages.gz  Por favor utilice apt-cdrom para hacer que APT reconozca este CD. apt-get update  no se puede usar para agregar nuevos CDsSi alguien me puede indicar qué tengo que hacer, lo agradecería. Es mi reproductor de audio favorito....

---

### Post by guillermolisi on 2010-05-15
Me parece que tenes algun tema con la configuracion de repositorios en tu maquina porque el mensaje de error que pasaste menciona que no puede acceder al CD de Ubuntu.

Esto generalmente queda desactivado luego de haber terminado la instalacion. Fijate en Origenes de Software y revisa en la solapa Other Software que la linea que comienza con "cdrom:" este destildada.

Es raro que con un paquete .deb surja un error de clave publica. Podrias relatar con detalles como procediste y de donde bajaste el paquete ?

Por otra parte el proyecto Songbird decidio no dar mas soporte ni prioridad en el desarrollo para Linux. Como consecuencia de esto se ha generado un fork especialmente para Linux llamado Nitghtingale.

Mas informacion [aqui]("http://geeksroom.com/2010/04/04/songbird-disminuye-soporte-prioritario-para-linux/") y [aqui]("http://geeksroom.com/2010/04/07/nightingale-o-la-respuesta-de-la-comunidad-ante-songbird/")

---

### Post by dam1977 on 2010-05-16
Al paquete .deb lo descargué del sitio GetDeb. Te comento que destildé lo que me dijiste de Orígenes del Software. Y me empezó a descargar actualizaciones. Me apareció el siguiente mensaje: W: Error de GPG: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2EBC26B60C5A2783
Por favor, tendrás idea de que cosa quiere decir? Gracias por atenderme!!!

---

### Post by guillermolisi on 2010-05-16
> **dam1977 said:**
> Al paquete .deb lo descargué del sitio GetDeb. Te comento que destildé lo que me dijiste de Orígenes del Software. Y me empezó a descargar actualizaciones. Me apareció el siguiente mensaje: W: Error de GPG: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2EBC26B60C5A2783
Por favor, tendrás idea de que cosa quiere decir? Gracias por atenderme!!!

Respecto de los repositorios de Medibuntu, [aqui tenes las instrucciones para agregarlos junto con su clave de autenticacion]("https://help.ubuntu.com/community/Medibuntu") (firmas digitales).

Esta es la seccion mas importante para agregarlos:

> **Adding the Repository**

 The following bash command adds  Medibuntu's [repository]("https://help.ubuntu.com/community/Repositories")  to Ubuntu. It also adds Medibuntu's [GPG]("https://help.ubuntu.com/community/GnuPrivacyGuardHowto")  key to your keyring, which is needed to authenticate the Medibuntu  packages. 


[LIST]
[*]This command should be run in the [Terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting%20a%20Terminal")  (Applications &#8594; Accessories &#8594; Terminal): 
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
[/LIST]
Medibuntu's repository is deactivated by [upgrading to a  newer Ubuntu release]("https://help.ubuntu.com/community/UpgradeNotes"), so you should run this command again after the  release upgrade. 
You may also  wish to add the following packages. The first will cause many apps from  the Medibuntu repository to appear in Ubuntu Software Center (Ubuntu  9.10+) or Add/Remove Applications (versions prior to 9.10).  The second  will allow users to generate crash reports against Medibuntu packages  and submit them to the Medibuntu bugtracker. 
```
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
```Please note you may have to use --force-yes instead of  --yes in order for this command to succeed. Las firmas de seguridad se usan para autenticar que el origen de los paquetes que vas a bajar e instalar sea confiable.


Respecto de Songbird en Ubuntu tenes informacion en los siguientes threads que creo te seran de utilidad:

[http://ubuntuforums.org/showthread.php?t=1222041](http://ubuntuforums.org/showthread.php?t=1222041)

[http://ubuntuforums.org/showthread.php?t=1268277](http://ubuntuforums.org/showthread.php?t=1268277)

---

### Post by alfplayer on 2010-05-16
Songbird anunció hace aproximadamente un mes que no dará más soporte para linux (mensaje del anuncio: [http://blog.songbirdnest.com/2010/04/02/songbird-singing-a-new-tune/]("http://blog.songbirdnest.com/2010/04/02/songbird-singing-a-new-tune/")).

Puede ser lo mejor usar otro reproductor. Rhythmbox es muy popular.

---

### Post by guillermolisi on 2010-05-16
> **alfplayer said:**
> Songbird anunció hace aproximadamente un mes que no dará más soporte para linux (mensaje del anuncio: [http://blog.songbirdnest.com/2010/04/02/songbird-singing-a-new-tune/](http://blog.songbirdnest.com/2010/04/02/songbird-singing-a-new-tune/)).

Puede ser lo mejor usar otro reproductor. Rhythmbox es muy popular.
Go to [here]("http://ubuntuforums.org/showpost.php?p=9304306&postcount=2") :)

---

### Post by alfplayer on 2010-05-16
> **guillermolisi said:**
> Go to [here]("http://ubuntuforums.org/showpost.php?p=9304306&postcount=2") :)

Ay, perdón.

Igualmente, el proyecto Nightingale no parece estar muy avanzado :) [http://getnightingale.org/]("http://getnightingale.org/")

---

### Post by dam1977 on 2010-05-17
Muchas gracias, Guillermolisi! solucionado el asunto de las claves públicas (por lo menos parece que si)... Ahora Songbird funciona. Lamento enterarme de que a la gente que hizo un prgrama tan bueno no le interese mas que funcione en Ubuntu.

---

