---
title: "Problema con Gestor de Actualizaciones"
date: 2010-11-20
forum: Software
---

### Post by ketzelleshelle on 2010-11-20
Desde que instalé 10.10 tengo un problema:
En primer lugar, las actualizaciones no se anuncian, o sea si no abro el gestor manualmente no me entero que hay actualizaciones.

En segundo lugar, cada vez que quiero actualizar me sale el error:

[B][I]Se requiere la instalación de paquetes no confiables
La acción puede necesitar la instalación de paquetes de fuentes no autenticadas[/I][/B]

En este caso la fuente no autenticada sería libpst4

Y no me deja actualizar...

Alguna ayuda?

Gracias!

---

### Post by hectorivand on 2010-11-20
> **ketzelleshelle said:**
> Desde que instalé 10.10 tengo un problema:
En primer lugar, las actualizaciones no se anuncian, o sea si no abro el gestor manualmente no me entero que hay actualizaciones.

En segundo lugar, cada vez que quiero actualizar me sale el error:

[B][I]Se requiere la instalación de paquetes no confiables
La acción puede necesitar la instalación de paquetes de fuentes no autenticadas[/I][/B]

En este caso la fuente no autenticada sería libpst4

Y no me deja actualizar...

Alguna ayuda?

Gracias!

Proba cambiando el repositorio, desde orígenes de software.

Saludos
Nacho

---

### Post by ketzelleshelle on 2010-11-20
> **hectorivand said:**
> Proba cambiando el repositorio, desde orígenes de software.

Saludos
Nacho

Podrías explicarme un poco más? O sea: lo cambio por cuál repositorio?
Gracias!

---

### Post by alfplayer on 2010-11-20
Es raro, porque ese paquete está en los repositorios de Ubuntu. Cambiaste algún repositorio?

---

### Post by estebe on 2010-11-27
Vaya!     Hoy, sin cambiar    nada de los repositorios a mi tampoco me deja  actualizar y me sale el mismo error.

---

### Post by guillermolisi on 2010-11-27
> **hectorivand said:**
> Proba cambiando el repositorio, desde orígenes de software.

Saludos
Nacho
En realidad donde dice "repositorio" lease "mirror server" o "servidor de replicacion/espejo" (no se como han traducido el termino). Los repositorios no habria que tocarlos, por ahora.

---

### Post by guillermolisi on 2010-11-27
> **ketzelleshelle said:**
> Desde que instalé 10.10 tengo un problema:
En primer lugar, las actualizaciones no se anuncian, o sea si no abro el gestor manualmente no me entero que hay actualizaciones.

En segundo lugar, cada vez que quiero actualizar me sale el error:

[B][I]Se requiere la instalación de paquetes no confiables
La acción puede necesitar la instalación de paquetes de fuentes no autenticadas[/I][/B]

En este caso la fuente no autenticada sería libpst4

Y no me deja actualizar...

Alguna ayuda?

Gracias!

Mostra el contenido de /etc/apt/sources.list y /etc/apt/sources.list.d

---

### Post by ketzelleshelle on 2010-11-28
> **guillermolisi said:**
> Mostra el contenido de /etc/apt/sources.list y /etc/apt/sources.list.d

Sources.list:

[IMG]http://i689.photobucket.com/albums/vv259/linkimagen/Pantallazo-Orgenesdelsoftware.png[/IMG]


Sources.list.d:

[IMG]http://i689.photobucket.com/albums/vv259/linkimagen/Sourceslistd.png[/IMG]


Está bien esta data?

---

### Post by ndiosque on 2010-12-27
SOLUCION!!!!... (creo.. jeje)
Hola. es la primera vez q entro para usar este foro y estoy usando Ubuntu hace apenas 3 dias, asi q pido disculpas por adelatado si algo me pifio.

Bueno respecto al problema, a mi me estaba ocurriendo lo mismo, y en este foro no encontre la solucion, no se si sea q no supe buecar pero bueno.
Lo importante es q solucione el problema cambiando la configuracion del 
"Centro de software de Ubuntu" -> "Editar" -> "origenes de software" 
y ahi en la solapa de "software de ubuntu" cambie donde dice "descargar desde" estaba seleccionado "servidor para argentina" y yo lo puse a "servidor principal"

Despues entre de nuevo normalmente a intentar instalar y todo marcho bien (ya no me salto el error)

Aclaro que tengo instalada la version Ubuntu 10.10 - Maverick Meerkat 32 bits para PC de escritorio
y el programa q intentaba instalar era el "Wammu"

Espero q sirva, y cualquier comentario critica o sugerencia sera bienvenida.

Saludos

---

### Post by asterix77 on 2010-12-28
Lo que indica ndiosque soluciona el problema cuando el servidor por defecto se ha caido. Por el mensaje que le aparece a ketzelleshelle me dá la impresión de que no se trataría de este caso, ya que hay una respuesta del servidor.

¿has intentado o siguiente?.

$sudo dpkg --configure -a

$sudo apt-get update

$sudo apt-get upgrade


Saludos


PD: Si usas Maverick, deberías eliminar de tu sources.list los repositorios de karmic (desmarcarlos)

---

### Post by guillermolisi on 2010-12-28
ketzelleshelle

Si estas usando la version 10.10 no deberias tener habilitados repositorios de la 10.04.

O deshabilitas los de 10.04 o los actualizas para que tomen contenidos para la 10.10.

---

### Post by guillermolisi on 2010-12-30
> **seli33 said:**
> Hola a tod@s:
He empezado hace unos dias con esta nueva experiencia que es ubuntu, todabia no se mucho pero intento aprender.
El problema que tengo es que instale el 7zip desde el centro de software de ubuntu y me dice que esta instalado quiero descomprimir archivos en rar y no puedo ya que no encuentro la aplicacion por ningun lado. 
un saludo de un novato
Movido a un [nuevo thread]("http://ubuntuforums.org/showthread.php?t=1656377") en la seccion Software ya que no es especifico de este, es software pero referido a otra cosa.

EDIT: Thread borrado por double posting.

---

### Post by riveravaldez on 2012-02-18
Qué tal, estoy desde un Xubuntu 11.10 Oneiric y he tenido exactamente los mismos síntomas que ha citado quien inició el post, y efectivamente se ha solucionado modificando el origen de "Argentina" a "Servidor principal", de modo que tal vez sea un issue en el servidor "Argentina".
Saludos!

---

