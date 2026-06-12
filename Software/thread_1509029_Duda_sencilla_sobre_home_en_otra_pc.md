---
title: "Duda sencilla sobre /home en otra pc"
date: 2010-06-13
forum: Software
---

### Post by guillermon on 2010-06-13
Hola, como lego pero siempre aprendiendo (y sin perder la curiosidad), y además en esta oportunidad he tenido la buena suerte (¿?) de comprarme por fin una notebook, que está super super! :popcorn:
  Ahora bien, la pregunta es cuál es la mejor manera de trasladar el home que usaba al de ahora, pues hay varias alternativas. Mi sentido común me dice, copio todo "." y listo (por ejemplo .openoffice.org). La duda que tuve antes de hacer esto es si habría inconvenientes con el sistema... Quizás sea una duda tonta... En mi caso he llamado igual al home, pero el nombre del sistema es diferente (he notado, pues uno se llama guille-desktop y la nueva guille-laptop, por defecto)...
  Si alguien tiene consejos, los acepto con gusto. Por lo pronto he hecho Respaldo de ajustes de Evolution, de bookmarks de firefox,exporté la biblioteca de Zotero (con la que no me fue bien así,por lo que voy a intentar la sincronización)... Estoy pensando en dar curso a Ubuntu One... 

   Bueno, desde ya muchas gracias, saludos a todos. Tengo algunas preguntas de hardware, pero abriré otro post. Saludos

---

### Post by alfplayer on 2010-06-13
Si las versiones de ubuntu son iguales y solo hay un usuario con el mismo nombre (el que se crea en la instalación) se puede borrar todo el nuevo home y copiar todo lo del viejo home preservando los atributos de los archivos (por ejemplo con la opción -p del comando cp). No estoy seguro que funcione perfectamente porque nunca lo realizé. Hay que pensar seriamente en tomar precauciones como hacer backup.

La diferencia en los nombres de sistema no debería causar problemas serios.

---

### Post by EnriqueK on 2010-06-14
Supongamos que tenés un pendrive de capacidad suficiente para contener tu carpeta personal comprimida, , lo  conectñas a la pc origen de datos y een un termunal ponés
```
sudo -i
cd /media/pendrive
tar -zcvf casa.tar.gz /home/usuario 
```
en donde pendrive será el punto de montaje que tendrá el mismo en esa pc origen de datos, por lo que debes verifiarlo y usuario es el nombre de tu carpeta personal
Al terminar vas a tener en el pendrive una copia comprimida de tu carpeta personal.
Luego vas al nuevo equipo en donde debes tener hecha la instalación con el mimo nombre, conectas el pendrive. abres un terminal y pones
```
sudo -i
rm -Rf /home/usuario
cd /media/pendrive
tar -zxvf casa.tar.gz --directory /
```
Con esto habrás completado la tarea y solo queda reiniciar sesión, seguramente habrán que hacerle ajustes, pero eso es lo de menos.
Referente a las claves, nombre de equipo, etc, etc, se alojan en el directorio /etc, por lo que no debes preocuparte ya que ni siquiera la clave de usuario hace falta que sea la misma  para hacer esta operación, o sea puedes tener otra sin problemas, lo importante es el nombre de usuario que será el titular de la carpeta personal.

---

### Post by guillermon on 2010-06-15
> **EnriqueK said:**
> Supongamos que tenés un pendrive de capacidad suficiente para contener tu carpeta personal comprimida, , lo  conectñas a la pc origen de datos y een un termunal ponés
```
sudo -i
cd /media/pendrive
tar -zcvf casa.tar.gz /home/usuario 
```
en donde pendrive será el punto de montaje que tendrá el mismo en esa pc origen de datos, por lo que debes verifiarlo y usuario es el nombre de tu carpeta personal
Al terminar vas a tener en el pendrive una copia comprimida de tu carpeta personal.
Luego vas al nuevo equipo en donde debes tener hecha la instalación con el mimo nombre, conectas el pendrive. abres un terminal y pones
```
sudo -i
rm -Rf /home/usuario
cd /media/pendrive
tar -zxvf casa.tar.gz --directory /
```
Con esto habrás completado la tarea y solo queda reiniciar sesión, seguramente habrán que hacerle ajustes, pero eso es lo de menos.
Referente a las claves, nombre de equipo, etc, etc, se alojan en el directorio /etc, por lo que no debes preocuparte ya que ni siquiera la clave de usuario hace falta que sea la misma  para hacer esta operación, o sea puedes tener otra sin problemas, lo importante es el nombre de usuario que será el titular de la carpeta personal.
Muchas gracias a ambos por la respuesta. He aquí una forma muy sencilla de hacerlo! Para poder usarla fuí haciendo el camino largo... :( Ahora puedo hacerlo todo de una vez. Muchas gracias de nuevo! Hasta pronto
Guillermo

---

