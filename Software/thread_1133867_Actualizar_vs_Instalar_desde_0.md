---
title: "Actualizar vs Instalar desde 0"
date: 2009-04-23
forum: Software
---

### Post by leo_liet on 2009-04-23
Hola, queria preguntarles que me convenia mas. Si instalar desde 0 la nueva version de ubuntu o actualizar la que tengo,ya que luego de leer en varios lados, estoy confundido. 
Y si tengo que instalar desde 0, como hago para poder tener todos los paquetes que tengo ahora.

          Saludos

---

### Post by Tobi-fp on 2009-04-23
Es re simple..
Primero haces un backup, despues actualisas.
Si todo esta bien, no hagues mas.

Si hay muchas problemas, grabas un cd de 9.04 y instalas desde 0.
Entonces tienes tú backup..

No puedes tener tus paquetes que tenes ahora con un instalacion desde 0, pero no es tan dificil instalar todas las paquetes.. Pero si actualisas, tus paquetes actualisan tambien.

---

### Post by leo_liet on 2009-04-23
Gracias tobi, el backup que tengo que hacer, que archivos me recomendas que ponga?

---

### Post by juancarlospaco on 2009-04-23
Reinstala conservando el /home
En la parte de la instalacion de las Particones elegi "Manual", 
eleji las particiones Linux, pero a la " / " no le tildes " Format "
borra todas las carpetas excepto la /home y instala.

---

### Post by EnriqueK on 2009-04-23
Aqyí te pongo un método para hacer una instalación den limpio pero automatizada que comenté en otro hilo y que para mi es la mejor forma de hacerlo por que está basasdo en la lista de los paquetes que tenés instalados  por lo que podrás usarlo hasta para instalar una versión muy distinta de la que tenés, por ejemplo si tenés Intrepid 32 bits, podrías usarlo para por ejemplo instalarlar  Jaunty de 64 bits e inclusive si tenés una conexión pobre de internet podés sacar la lista de URLs de los paquetes  para así descargar en otro equipo con mejor conexión y ni hablemos que todo está bajo el directo y exclusivo control de APT lo que garantiza plenamente el proceso.
```
Podes hacer una instalación en limpio pero totalmente automatizada o desatendida y esto se logra uando la información de paquetes instalados que te brinda por ejemplo usando Synaptic , para ello entras a Synaptic--> Abrir-->Guardar seleciones como--> le das un nombre y marcas el casillero Guardar el estado completo no solo los cambios . Esto te va a generar un archivo plano con el nombre de todos los paquetes instalados con la particularidad de que solo contiene los nombres de los paquetes sin especificar las versiones de los mismos, por lo que esta información te va a permitir instalar todos esos paquetes para una versión igual o diferente de Ubuntu , para ello instala la nueva versión, entras a Synaptic --> Abrir--> Leer selecciones--> Pulsa el botón Aplicar y a a esperar a que se descarguenen todos los nuevos paquetes y luego los instale, la espera puede ser larga, a mi me lleva unas 15 horas.
Para este método se requieren básicamente dos cosas, una es usar repositorios equivalentes y la otra es tener una muy buena conexión a Internet y no te olvidés de asegurarte de portar el listado de paquetes para la nueva instalación y tomar nota de los repositorios usados para así activar repositorios equivalentes.
Usando este método he pasado de la versión 7.04 a la 8.04 (sin pasar para nada por la 7.10) y últimamente instalé la 8.10 64 bits basado en una lista de paquetes de una instalación de 8.10 32 bits que me pasó un amigo.
El éxito del proceso esta asegurado por que todo queda bajo el directo control de APT (en donde demuestra toda su potencia), lo que garantiza el extricto control de dependencias.
Otra cosa, el sistema de archivos que elijas para la nueva instalación es totalmente independiente de este método.
```

---

### Post by leo_liet on 2009-04-23
Gracias a todos por sus respuestas :) una cosa mas. me conviene usar el sistema de archivos ext4? o dejar el que uso ext3? y por ultimo mi pc soporta 64 bits, si instalo la version de 64 en lugar que la de 32, en que cosas se va a notar una diferencia? o es practicamente lo mismo.
     

      gracias de nuevo :)

---

### Post by staar on 2009-04-23
> **leo_liet said:**
> Gracias tobi, el backup que tengo que hacer, que archivos me recomendas que ponga?

acordate de guardar configuraciones importantes, tipo /etc/xorg.conf /boot/grub/menu.lst /etc/apt/sources.list, para no tener que andar configurando todo de nuevo...

ext4 es una masa, rapido y suave :-D, en 64 bits solo algunos programas no te van a andar, pero cada ves son menos, diferencias son muy pocas...

saludos

---

### Post by gmunioz on 2009-04-23
Hola leo...:

Para actualizar, existen entre otros dos procedimientos comunes:

a- Directamente de la red mediante dist-upgrade (el más peligroso, pues ante 

una falla en el flujo de descarga, el sistema quedará inutilizable) 

b- Mediante el alternate-cd, introduciendolo simplemente en el lector,

preguntará si se quiere actualizar, tambien depende de la red para los

paquetes que no estan en el cd, pero el sistema se instalará sin 

problemas.

En mi caso particular, prefiero instalar desde cero.

La instalación siempre la hago en al menos tres particiones, una primaria

para / y dos lógicas para /home y swap, lo que me permite al no formatear 

/home mantener las configuraciones, los addons de los programss y mis 

archivos (documentos, grafivos, etc, a salvo)

Para que el sistema mantenga las aplicaciones ya instaladas:

a- Desde synaptic, en el sistema viejo, pulsando archivo, guardar 

cambios, guardar el estado completo, se genera un archivo de texto plano

con el listado de aplicaciones instaladas.

b- Guardar una copia de sources.list con solo los repositorios.

c- Una vez instalado el nuevo sistema, con las aplicaciones básicas

Edito el viejo sources.list, cambiando los nombres de la distribución

vieja por la nueva (hardy por jaunty, por ejemplo) y sobre escribo el 

nuevo archivo sources.list por este.

d- Desde synaptic, en el nuevo sistema, previo recargar el contenido de

los repositorios, pulsando en archivo, leer selecciones, aplicar, se 

restauran todas las aplicaciones anteriomente existentes, siempre y 

cuando se encuentren en los nuevos repositorios.

Saludos.

---

### Post by juancarlospaco on 2009-04-23
Che tan escribiendo cosas que no van, no todos los archivos de configuracion sirven,
un Sources.list de una version vieja si lo pones en una release nueva rompes tu administrador de paquetes.
el Xorg.conf va cambiando con las versiones, y el menu.lst tiene otros kerneles en la lista.

---

### Post by leo_liet on 2009-04-23
Gracias de nuevo, entonces me pongo a descargar la nueva version y cuando vengo del cole la instalo y comento como fue :) saludos

---

### Post by staar on 2009-04-23
> **juancarlospaco said:**
> Che tan escribiendo cosas que no van, no todos los archivos de configuracion sirven,
un Sources.list de una version vieja si lo pones en una release nueva rompes tu administrador de paquetes.
el Xorg.conf va cambiando con las versiones, y el menu.lst tiene otros kerneles en la lista.

el sources.list lo puse por los repositorios de launchpad que tenga, se cambia intrepid por jaunty y listo (no funciona con todos los ppa), me sirvio muchisimo cuando instale jaunty, no tuve que volver a buscar todos los repos de las aplicaciones que uso y me gusta mantener actualizadas, el menu.lst siempre es bueno tener un backup, y el xorg.conf no cambia tanto, yo uso el mismo desde hardy y es de la unica manera que xorg me detecta la resolución del monitor, incluso uso el mismo en arch...

saludos

---

### Post by leo_liet on 2009-04-23
Ola de nuevo, les comento que ya descargue e instale la nueva version y quedo 10 puntos :)

     Gracias

---

### Post by juancarlospaco on 2009-04-24
Buenisimo!!!

---

### Post by andy_91 on 2009-04-24
yo Tambien cambio los repositorios y actualizo los paquetes instalados :p

despues instalo el kernel por separado o uso el mismo como ahora

---

