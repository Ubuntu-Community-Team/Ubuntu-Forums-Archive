---
title: "Problemas con Chromium-Ubuntu 14.04-32 bits"
date: 2016-11-15
forum: Software
---

### Post by Vero1 on 2016-11-15
Buenos días,

Previo a Trusty tenía ubuntu 12.04.
Debido a que tuve problemas con la gráfica y la lentidud, me sugirieron pasarme a ubuntu 14.04. Hice un upgrade directamente desde 12.04. Posteriormente actualicé todo e inclusive instalé algunas cosas que sugirieron en Blogs conocidos en la Web.
En ubuntu 12.04 usaba Firefox y lo seguì usando pero seguía teniendo problemas. Entonces me recomendaron pasarme a Chromium por ser mas liviano.
Aclaro que tengo 2 Gib de Ram y 3.6 GHz, Pentium IV, dual core.
La situación no ha mejorado ya que sigo con problemas. Trabajo con fotos y videos.

Me salió esta mañana un aviso que me recomienda actualizar pero me sale lo siguiente: 


Fallo al renombrar [http://dl.google.com/linux/chrome/deb/dists/stable/Release:](http://dl.google.com/linux/chrome/deb/dists/stable/Release:) No se pudo encontrar la entrada esperada «main/binary-i386/Packages» en el archivo «Release» (entrada incorrecta en «sources.list» o fichero mal formado)
W: Fallo al renombrar [http://ppa.launchpad.net/bsundman/themes/ubuntu/dists/precise/main/binary-i386/Packages:](http://ppa.launchpad.net/bsundman/themes/ubuntu/dists/precise/main/binary-i386/Packages:) 404  Not Found
W: Fallo al renombrar [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/trusty/main/binary-i386/Packages:](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/trusty/main/binary-i386/Packages:) 404  Not Found
W: Fallo al renombrar [http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu/dists/precise/main/binary-i386/Packages:](http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu/dists/precise/main/binary-i386/Packages:) 404  Not Found
E: Algunos archivos de índice fallaron al descargar. Se han ignorado, o se han utilizado unos antiguos en su lugar
E: No se pudo reconstruir el almacén de paquetes

Evidentemente hay un problema con Chrome.

Qué me pueden sugerir que haga?

Gracias
P.D. Mi ubuntu es 64 bits

---

### Post by Dennis N on 2016-11-15
There is no longer a 32-bit version of Chrome. You need to use the 64-bit version, which means you need the 64-bit version of Ubuntu 14.04.

32-bit Chromium however is available in the regular Ubuntu repository (no PPA needed).

---

### Post by Vero1 on 2016-11-15
Thanks for your reply. 

I have no Crome, I have Chromium. My Ubuntu 14.04 is i686 = 64bits . I had 32 bits with ubuntu 12.04, sorry.

Anyway Chromium fails and updates are incomplete as you can see above.

Thanks.

---

### Post by Dennis N on 2016-11-15
You should install chromium-browser from the Ubuntu Repository. It offers the 32-bit version. That should work. Your source for Chromium is a PPA which seems to no longer be available.

---

### Post by Vero1 on 2016-11-15
I've installed it from Ubuntu Repository : Versión 53.0.2785.143 Built on Ubuntu , running on Ubuntu 14.04, but I don't think it is 32 bits.
I don't know how to find it out.

---

### Post by Dennis N on 2016-11-15
> P.D. Mi ubuntu es 64 bits  Yes, you would get the 64-bit version. It is possible to run 32-bit software on a 64-bit system, but normally you would not if a 64-bit version is available. 

On a 64-bit OS, 32-bit packages have :i386 added to them. So Chromium should be chromium-browser:i386

---

### Post by enriquek2 on 2016-11-19
Si no tienes una tarjeta gráfica dedicada, siempre siempre vas a tenerprobelemas de rendimiento gráfico, recomiendo una Nvidia pci-e , no  son caras 
Escritorios como Unity o Gnome-shell son muy pesados, por lo que recomiendo instaler XFCE o MATE , personalmente recomiendo este último.

sudo apt-add-repository ppa:ubuntu-mate-dev/ppa
sudo apt-add-repository ppa:ubuntu-mate-dev/trusty-mate

sudo apt-get update
sudo apt-get upgrade

sudo apt-get install mate-desktop-environment-extras

Referente a Chrome 32 bits, busca en la red si alguien posteó una descarga por que oficialmente ya no existe en el sitio oficial . Tiene que ser google-chrome -stable por que Chromium carece de pepperflash y ai la consigues por separado para usarla en chromium, seguro aue no será fácil

---

