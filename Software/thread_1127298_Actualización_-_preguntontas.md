---
title: "Actualización - preguntontas"
date: 2009-04-16
forum: Software
---

### Post by xsergei on 2009-04-16
Hola a todos, tal vez mi pregunta sea un tanto tonta, pero que pasa cuando actualizamos Ubuntu ya sea por synaptic o consola,
específicamente me refiero pasar a Jaunty Jackalope el sistema de archivos cambiará a Ext4 o no queda otra que realizar una instalación limpia? justamente ese sistema de archivos es el que permitirá entre otras cosas la rapidez del boot sinó leí mal.
el grub también se modifica automáticamente?
gracias de antemano. 
Sergei

---

### Post by luks911 on 2009-04-16
Según leí, porque todavía no hice ninguna actualización a Jaunty ni lo instalé más que un pendrive, la posibilidad de usar ext4 aparece sólo en instalaciones nuevas. También es válido para instalaciones sobre versiones anteriores, pero usarías ext4 sólo en las particiones que formatees. Por ejemplo, si tenés / y /home aparte, podés aplicarlo a /. 
Hay dando vuelta por allí instrucciones para convertir una partición ext3 a ext4 sin fomatear ([http://www.google.com.ar/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=ubuntu+transformar+partici%C3%B3n+de+ext3+a+ext4](http://www.google.com.ar/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=ubuntu+transformar+partici%C3%B3n+de+ext3+a+ext4)). Aunque parece bastante arriesgado, sólo recomendable con previo backup.
De todos modos, la velocidad de booteo en Jaunty está mejorada incluso para el sistema ext3.

---

### Post by pablo.s on 2009-04-16
> **xsergei said:**
> pasar a Jaunty Jackalope el sistema de archivos cambiará a Ext4

No cambia automaticamente a Ext4. 
Ese tipo de cambios no los hará nunca
de forma desatendida. 

> **xsergei said:**
> o no queda otra que realizar una instalación limpia?

Yo recomiendo hacer instalación
limpia en cada lanzamiento nuevo.
Pero también se puede hacer una
actualización con
**sudo apt-get install dist-upgrade**

> **xsergei said:**
> justamente ese sistema de archivos es el que permitirá entre otras cosas la rapidez del boot sinó leí mal.

No es asi, se ha optimizado en
general la velocidad de arranque
al priorizar ciertos servicios en
paralelo y/o en orden de ejecución.
La velocidad del sistema Ext4 se 
debe a mejoras de la indexación,
prealocación y asignación del
espacio de disco.

> **xsergei said:**
> el grub también se modifica automáticamente?
gracias de antemano. Sergei

Grub se va a modificar casi seguro
porque este tipo de lanzamientos
traen núcleos actualizados para
activar las mejoras. Entre otras cosas.
Saludos

---

### Post by xsergei on 2009-04-16
Sinceramente es un placer participar del foro, cada vez que pregunté algo siempre tarde o temprano encontré una respuesta, y buscando en las preguntas de los demás usuarios aprendí tantas cosas que hoy me puedo considerar un entendido en el sistema linux, obvio que no soy experto ni nada por el estilo pero si sigo así..... 
muchas gracias a todos!!!

---

### Post by EnriqueK on 2009-04-17
Podes hacer una instalación en limpio pero totalmente automatizada o desatendida y esto se logra uando la información de paquetes instalados que te brinda por ejemplo usando Synaptic , para ello entras a Synaptic--> Abrir-->Guardar seleciones como--> le das un nombre y marcas el casillero Guardar el estado completo no solo los cambios . Esto te va a generar un archivo plano con el nombre de todos los paquetes instalados con la particularidad de que solo contiene los nombres de los paquetes sin especificar las versiones de los mismos, por lo que esta información te va a permitir instalar todos esos paquetes para una versión igual o diferente de Ubuntu , para ello instala la nueva versión, entras a Synaptic --> Abrir--> Leer selecciones--> Pulsa el botón Aplicar y a a esperar a que se descarguenen todos los nuevos paquetes y luego los instale, la espera puede ser larga, a mi me lleva unas 15 horas.
Para este método se requieren básicamente dos cosas, una es usar repositorios equivalentes y la otra es tener una muy buena conexión a Internet y no te olvidés de asegurarte de portar el listado de paquetes para la nueva instalación y tomar nota de los repositorios usados para así activar repositorios equivalentes.
Usando este método he pasado de la versión 7.04 a la 8.04 (sin pasar para nada por la 7.10) y últimamente instalé la 8.10 64 bits basado en una lista de paquetes de una instalación de 8.10 32 bits que me pasó un amigo.
El éxito del proceso esta asegurado por que todo queda bajo el directo control de APT (en donde demuestra toda su potencia), lo que garantiza el extricto control de dependencias.
Otra cosa, el sistema de archivos que elijas para la nueva instalación es totalmente independiente de este método.

---

### Post by sajnox on 2009-04-17
> **xsergei said:**
> específicamente me refiero pasar a Jaunty Jackalope el sistema de archivos cambiará a Ext4 o no queda otra que realizar una instalación limpia?

Entiendo que no te queda otra ya que para cambiar el sistema de archivos tenes que formatear el disco, y para formatear el disco hay que desmontarlo y no vas a podes desmonar el disco que cargo el sistema

Saludos

---

### Post by xsergei on 2009-04-19
[QUOTE=EnriqueK;7087497]Podes hacer una instalación en limpio pero totalmente automatizada o desatendida...

Muy buena tu explicación!!!
ya me imprimí el post para usarlo en 4 días :D

una duda mas, porqué la nueva versión Jaunty, comienza con 9.04 y no 9.0?

---

### Post by luks911 on 2009-04-19
> **xsergei said:**
> una duda mas, porqué la nueva versión Jaunty, comienza con 9.04 y no 9.0?

El primer número siempre corresponde al año del lanzamiento y el segundo al mes. 9, por 2009, y 04, por abril. Por eso también es 9.04 y no 9.4.

:lolflag:

---

