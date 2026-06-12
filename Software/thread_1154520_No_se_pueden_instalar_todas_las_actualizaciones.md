---
title: "No se pueden instalar todas las actualizaciones"
date: 2009-05-09
forum: Software
---

### Post by rubioo on 2009-05-09
Hola amigos ubunteros:P acá vengo con otro problema.
 Resulta que actualizando mi sistema(como hago todas las semanas), me aparece una ventana que dice esto:

 >         No se pueden instalar todas las actualizaciones
        
           Ejecute una actualización parcial, para instalar tantas
           actualizaciones como sea posible.

           Esto puede deberse a:
           *Una actualización anterior que no se completó correctamente.
           *Problemas con algún programa instalado.
           *Paquetes de software no oficiales, no proporcionados por
            Ubuntu.
           *Cambios normales de una versión de desarrollo de Ubuntu
 
                           Actualización parcial   |   Cerrar
            


 Y si pongo actualización parcial me sale esto

> 
   No se ha podido calcular la actualización

 An unresolvable problem occurred while calculating the upgrade:
 E:No se pudieron corregir los problemas, usted ha retenido paquetes
 rotos.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

 Probablemente sea un problema transitorio, inténtelo de nuevo más tarde. 

 Me llamó la atención, porque hace varios días que me esta pasando esto.
 Probé desinstalando el único paquete que yo instale en estos días, pero sigue igual. :(
 Bueno, eso es todo.

       Gracias y saludos

---

### Post by pablo.s on 2009-05-09
No pasa nada con el mensaje
de alerta, es muy probable que
se deba a que tenés habilitados
los repositorios de backports y
proposed. Es asi?

---

### Post by EnriqueK on 2009-05-09
Esto te está pasando por que seguramente tenés habilitadas las actualizaciones aún no publicadas , te aconsejo que deshabilites esas actualizaciones que son fuente de conflictos y de mal funcionamiento del sistema, abre Synaptic --> Configuración--> Repositorios --> Actualizaciones y allí desmarcás las actualizaciones aún no publicadas y finalmente recargas , seguramente ya no te aparecerá ese mensaje.

---

### Post by rubioo on 2009-05-09
Pablo: los repositorios backports no los tengo habilitados
 Enrike: tengo desactivados esos repositorios, sólo tengo activados los de actualizaciones importantes de seguridad y actualizaciones recomendadas

 :confused::confused:

---

### Post by pablo.s on 2009-05-09
Desactivá actualizaciones recomendadas.

---

### Post by rubioo on 2009-05-09
Sigue pasando, aunque desactive las recomendadas :(

---

### Post by pablo.s on 2009-05-09
Estás usando 9.04 actualizada de Intrepid
o instalada de cero?

En Synaptic, buscá con el filtro los paquetes
rotos y desinstalalos.

---

### Post by rubioo on 2009-05-09
Si estoy usando JJ actualizada de II, pero ahora puse para actualizar desde synaptic y parece que va queriendo :)
 > En Synaptic, buscá con el filtro los paquetes
rotos y desinstalalos. 
 Como hago eso? :(

---

### Post by pablo.s on 2009-05-09
> **rubioo said:**
>  Como hago eso? :(

**[COLOR=DarkGreen]sudo apt-get install -f[/COLOR]**

---

### Post by EnriqueK on 2009-05-09
Paquetes rotos no creo por que en ese caso no te dejará usar Synaptic hasta que lo arregles , puede que el problema sea por que están caídos algunos servidores de índices, probá con cambiar el  origen de los servidores, sugiero los de Brasil (br) , o los de Alemania (de) , estos últimos a mi nunca me fallaron.

---

### Post by rubioo on 2009-05-09
Pude actualizar desde synaptic, pero como hago para actualizar como hago normalmente?

---

### Post by EnriqueK on 2009-05-09
En Synaptic no aparece ningún mensaje de alerta en estas situaciones, por lo que la actualizaciones se hacen sin mas trámites, por eso mejor siempre hacelo con el gestor de acualizaciones.

---

### Post by rubioo on 2009-05-10
Entonces hice algo que no tendria que haber hecho?? :(

---

