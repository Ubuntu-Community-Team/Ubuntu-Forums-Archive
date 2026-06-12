---
title: "No puedo actualizar java"
date: 2013-05-15
forum: Software
---

### Post by juanovic on 2013-05-15
Buenas, me he encontrado con el problema de no poder actualizar java(tengo ubuntu 12.04). Resulta que primero me baje una version de java, y lo instale siguiendo las instrucciones de un tipo en esta pagina: [http://www.ubuntu-guia.com/2012/04/instalar-oracle-java-7-en-ubuntu-1204.html](http://www.ubuntu-guia.com/2012/04/instalar-oracle-java-7-en-ubuntu-1204.html)

lo instalé, fenómeno. Luego de un tiempo me salió un cartelito diciéndome que la versión que estaba usando era insegura, y que tenia que actualizar. Fui a la página de oracle, me bajé el java-7u21blablabla.tar.gz. Ni idea cómo instalarlo. Asi que me puse a buscar por el foro y me encontré con esto:

[http://www.duinsoft.nl/packages.php?t=en](http://www.duinsoft.nl/packages.php?t=en)  

de donde me puedo bajar un script para que se instale solo. No anduvo. Lo quise desinstalar, tampoco pude. 

siguiente opción: PPA

[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

seguí nuevamente las instrucciones, se instaló, supuestamente se actualizó, y voy a una página a donde necesito java para usar el mIRC, y nada, me sale un cartelito diciéndome que la versión es insegura etc etc. 

Alguien podría darme una mano o guiarme más o menos? desde ya muchas gracias

---

### Post by juanovic on 2013-05-15
Buenas perdón el doble post. Ahora me anda por ejemplo en cuevana, primero me aparece un cartel en el reproductor de video diciendome que no tengo java, que vaya a a pagina; arriba, justo abajo de la barra de marcadores me aparece "desea ejecutar java "siempre", "ejecutar solo esta vez"". Luego me aparecen 2 carteles, diferentes pero diciendome lo mismo: "desea ejecutar esta aplicacion? la ejecucion de esta aplicacion puede suponer un riesgo de seguridad" , y a veces me aparece 1. Será que tengo 2 java instalados?

---

### Post by EnriqueK on 2013-05-15
Necesito saber tres cosas
1.- versión de java7 actual, ejecuta 
java -version
2.-Nombre completo del archivo que descargaste
3.- ubicación de la carpeta jvm. es para poder eliminarla, yo por ejemplo lo tengo en /usr/lib . podñe ejecutar 
gnome-search-tool
y en el cuadro de bísqueda ponés jvm selecciona buscar en sistema de archivos
Con esos datos te preparo un script instalador

---

