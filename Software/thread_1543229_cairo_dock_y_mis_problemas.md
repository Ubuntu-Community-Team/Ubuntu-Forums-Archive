---
title: "cairo dock y mis problemas"
date: 2010-07-31
forum: Software
---

### Post by drazhe on 2010-07-31
Hola, conseguí instalar Cairo dock y viendo las distintas características que tiene me mande una y ahora no lo abre, pero Ubuntu se vuelve terriblemente lento cuando lo intento abrir, al extremo de tener que reiniciar para que deje de funcionar.

como puedo hacer para volver a la configuración anterior? intenté borrar la carpeta **.cairo** pero no hay nada que se le parezca en mi carpeta personal, y al intentar des-instalarlo desde **synaptic** y al volver a instalarlo sigue haciendo lo mismo.

Lo último que intenté hacer fue ver las distintas posiciones que trae y se quedó colgado en la 3era opción, no recuerdo si era abanico y arco-iris...

ayuda!:confused::cry:

---

### Post by drazhe on 2010-08-03
Hola, aunque sea díganme como eliminar por completo y que no quede rastro de que alguna vez estuvo instalado el cairo dock, así comienzo de nuevo.
Cuando intento eliminarlo desde **synaptic** al volver a instalarlo es como que me guardara la configuración que tenía y me sigue dando el problema del cuelgue.

---

### Post by guillermolisi on 2010-08-04
Desde Synaptic lo marcas para removerlo completamente (Mark for complete removal), asi borras programa, librerias que solo use este y archivos de configuracion.

---

### Post by drazhe on 2010-08-04
pues, hice eso la primera vez y como que me guarda algo, ya que al volver a instalarlo tiene las aplicaciones que yo cargue y los problemas que tengo en este instante.. jejeje

---

### Post by guillermolisi on 2010-08-04
En Synaptic podes ver la lista de archivos y sus path una vez instalado un paquete.

Si te armas de paciencia y cuidado, podes borrarlos manualmente para volver a empezar.

No uso dock alguno, asi que salvo esto que mencione y la posibilidad de que en el sitio del desarrollador haya mas documentacion y lo que Google obtenga ante una consulta especifica sobre como borrarlo completamente y/o recuperarlo, no se me ocurre otra cosa.

---

### Post by sebastianabate on 2010-08-05
El tema es que Synaptic te puede eliminar todas las configuraciones globales de los programas (generalmente guardadas en /etc), pero no te elimina las personales de cada usuario (en el home de cada uno). En tu caso el problema es la configuración que quedó guardada en tu home, y por lo general las aplicaciones guardan su configuración dentro del directorio /home/usuario/.nombre_de_aplicacion o en el caso de las aplicaciones que siguen el lineamiento de Gnome en /home/usuario/.config/nombre_de_aplicacion.

La otra cosa que podés hacer es buscar en tu home todos los archivos y directorios que contengan la palabra "cairo" en su nombre, y así identificarlo más facilmente; esto lo hacés ejecutando en una terminal parado en el directorio home de tu usuario el comando

find . -name *cairo*

este comando lo que hace es buscar (find) en el directorio donde estás parado y todos sus subdirectorios (.) todos los archivos cuyo nombre contenga cairo  en cualquier parte del mismo (-name *cairo*)

Una vez que encontrás el directorio donde el dock guarda su configuración, lo borrás (o mejor lo renombrás) y volvés a ejecutar el programa.

---

### Post by drazhe on 2010-08-06
**sebastianabate** gracias! eliminé desde **synaptic** lo mas que pude encontrar detallado como **cairo** o **cairo-dock** y en mi carpeta

*/home/mi usuario/.config *

apareció otra carpeta **cairo-dock** con la configuración que me estaba dando problemas, al eliminarla, y reinstalar la aplicación, ya no dió mas problemas!

gracias a todos por la ayuda!

---

