---
title: "No puedo desinstalar Google Earth 5.2"
date: 2010-06-18
forum: Software
---

### Post by atari130xe on 2010-06-18
Hola gente hacía mucho que no entraba al foro, acá estoy con algo que nunca me pasó hasta ahora. bajé el paquete binario del sitio de Google: Google Earth versión 5.2 el tema es que tenía instalada la versión anterior (5.1) que está en los repositorios, sin darme cuenta no desinstalé esta última e instalé la 5.2 comienza a abrir y se cierra el programa, quise desinstalarlo pero no aparece como "instalado" en Synaptics, ¿como deberia proceder? Gracias!

---

### Post by joseluis on 2010-06-18
¿purge --remove? y nombre del paquete

---

### Post by EnriqueK on 2010-06-19
Lo que haría es 
1.- sudo sh '/opt/google-earth/uninstall'  ---> con esto desinstalas el .bin
2.- Reinstala desde los repositorios y luego lo desinstalas
3.- Vuelve a instalar el archivo .bin

---

### Post by atari130xe on 2010-06-19
Gracias a ambos, me estoy dando cuenta que al bajar paquetes binarios me ocurre lo mismo caso p7zip que por alguna razòn no me funciona como deberia (el que se instala desde el repositorio la version 9.04) bajè el binario de la versiòn 9.13 del sitio de 7zip e instalè con ./install.sh y funciona de maravillas pero al buscarlo en sypnatics o tratar de desinstalarlo por consola con sudo apt-get --purge remove xxxx aparece como no instalado, este procedimiento es vàlido para cualquier soft no instalado de la manera "usual"? llàmese sypnatics, centro de soft. etc.? gracias!

---

