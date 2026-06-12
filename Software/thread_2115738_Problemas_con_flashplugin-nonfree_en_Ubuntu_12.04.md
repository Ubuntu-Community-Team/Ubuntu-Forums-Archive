---
title: "Problemas con flashplugin-nonfree en Ubuntu 12.04"
date: 2013-02-13
forum: Software
---

### Post by ojoxojo on 2013-02-13
Hola!
Tengo un problema con Flashplugin-nonfree y uso Ubuntu 12.04 LTS.
Todo comenzó cuando quise instalar adobe flash player (aunque sé que ya no hay soporte) y se volvió un jolgorio... partiendo porque desde otro foro vi que podía instalar el "ubuntu-restricted-extras" y pensé que con eso se abría solucionado el problema del flash. Resulta que luego dejó de funcionarme el centro de software, dejó de abrirse, me tira error y tratando de arreglar esto por el terminal, cualquier comando que ponga para arreglar algun problema me dice que flashplugin-nonfree está inconsistente y que debe ser reinstalado. Lo eliminé, lo re instalé bajo este comando:
```
wget http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb
```

utilicé otros comandos para arreglar el problema del centro de software como estos: 
```
sudo apt-get remove --purge software-center software-center-aptdaemon-plugins
sudo apt-get clean all 
sudo apt-get autoclean 
sudo dpkg --configure -a 
sudo apt-get update && sudo apt-get dist-upgrade 
sudo apt-get install software-center
```

seguí buscando en muchos foros y nada me ha dado resultado. También me dale el círculo rojo con línea blanca en la barra superior, y lo que me dice es: "E: the package flashplugin-nonfree needs to be reinstalled, but I can't find an archive for it." luego dice que "significa que ha instalado paquetes cuyas dependencias no se han podido satisfacer."

Realmente ya no sé que hacer, porque he buscado en foros y nada me resulta. En terminal tiro los comandos para arreglar las cosas y siempre el problema es que debo reinstalar el paquete de flashplugin-nonfree. Gracias de antemano :)

---

