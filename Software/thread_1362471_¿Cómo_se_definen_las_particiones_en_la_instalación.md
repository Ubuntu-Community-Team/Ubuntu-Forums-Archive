---
title: "¿Cómo se definen las particiones en la instalación del Ubuntu?"
date: 2009-12-23
forum: Software
---

### Post by mano negra on 2009-12-23
[COLOR=#000000][FONT=times new roman]Buenas,
       Les escribo porque no funciona me el entorno gráfico. Se los comento porque en algún momento me gustaría saber que pudo haber pasado. Actualmente tengo instalado el Ubuntu 8.10 
Yo no se mucho sobre Linux, así que la solución que tengo rápida por el momento es formatearla. De paso puedo aprovechar para instalar el Ubuntu 9.10. La cuestión es que tengo un montón de particiones debido a otras veces que instalé el Ubuntu, y lo bueno sería eliminarlas en la instalación, menos una donde tengo todas mis cosas. 
Por lo que estuve viendo, en la guía de instalación se presenta la opción para definir las particiones en forma manual, eliminando y/o dejando las que se desee.
Desde guía-ubuntu.org dicen que hay que definir tres particiones: la swap, "/" y "/home". Pero me parece que son solo la raíz y la Swap las que hay que crear. También me pide: si son lógicas o primarias, el punto de montaje y el tamaño. El disco rígido tiene 250 Gb y la partición con archivos, que no puedo eliminar, 197 Gb apróx. 
MI consulta es si me pueden explicar como se hace la configuración de las particiones.
Espero haber sido claro. Cualquier cosa diganmé.
Saludos.

  [/FONT][/COLOR]

---

### Post by euzkoarima on 2009-12-23
Efectivamente en un caso así lo mejor es hacer particionado manual.
Si tu disco estuviese vacío tenés que cear todas las particiones, incluso /home.
En tu caso entiendo que tenés una partición de 197 Gb que querés mantener y que es tu home.
Las otras, se pueden borrar y formatear.

Te recomiendo que antes de comenzar identifiques tus particiones, si perdiste el entorno gráfico lo podés hacer con el comando
```
sudo fd -l
```

Después cuando instalás borrás todas las que ya no te sirven y en ese espacio creas swap y /
swap ya la tenés creada y seguro la podes reutilizar, para eso no la borres y luego indicás que el uso a darle es swap.

Cuando te pide punto de montaje (para todas las no swap) es justamente si va a ser root o /home u otro directorio.
Primaria o lógica es porque el particionado tipo DOS solo admite hasta 4 particiones primarias. Teniendo 3 en tu caso, yo las haría todas primarias.

Saludos,
Eduardo

---

### Post by juancarlospaco on 2009-12-23
En realidad tiene que haber una / 
Es el unico requisito, inclusive si no hay Swap anda igual, aunque no es recomendable.

---

### Post by gmunioz on 2009-12-23
Hola man.....:

Mi sugerencia es:
a- Que bajes el live-cd versión desktop de Jaunty. Karmic esta por
demás cargosa, comenzando por los errores del Grub2.

b- Que inicies la instalación y al llegar a particionamiento elijas
manual.
1- A continuación elimina todas las particiones Linux 83 y 82, menos
la de 197 gigas con tus archivos.
2- En el espacio libre crea al menos tres particiones
Una primaria, activa, sistema de archivos ext4, de 16 gigas, punto de montaje /
Una lógica, sistema de archivos intercambio, de 1 giga, montaje por defecto
Una lógica, sistema de archivos ext4, del resto de los gigas libres, punto de montaje /home
A la partición de archivos, preexistente de 197 gigas, la montas, utilizando su sistema de archivos original, sin dar formato, en forma manual donde mas te guste, por ejemplo /home/usuario/datos

c- Terminada la instalación el grub por defecto en el mbr.

d- Al iniciar el sistema desde el rígido, desmonta, da permisos de lectura escritura y monta la partición de datos, ejecutando en consola:
sudo su
umount /home/usuario/datos
chmod -Rf 777 /home/usuario/datos
mount -a

---

### Post by mano negra on 2009-12-23
Uhhh!...Paso a dar algún detalle. Por ahí es redundante. La partición de 197 Gb la heredé de cuando tenía el windows, y la mantuve porque no podía hacer un backup. Y ahora estoy en la misma, cuando lo haga supongo que podré cambiar eso. El sistema de archivos es el ntfs. Y se me montaba en /media. Ese lo puedo dejar así?
Para resumir:
- en el espacio libre creo
  * Partición Swap, que el montaje es por defecto.
  * Partición primaria raiz, punto de montaje "/". Le tengo que dar unos 30 Gb porque uso el Virtual Box. ¿A partir de aquí usa toda la memoria, no? 
  * Partición lógica con punto de montaje /home, para el resto de la memori que me queda libre.
  * La otra partición con archivos no la toco y que siga montándose en media. Por el momento no quiero meter mano.

Va bien así? 

Salud!

---

### Post by gmunioz on 2009-12-23
Hola man....:

Si perfecto y correcto, la partición la montas donde más te guste.
/media es un lugar adecuado.
Si es ntfs, te conviene montarla al iniciar el sistema y dejarla
sin montar durante la instalación, ya que requiere de ntfs-3g y fuse-utils.
Solo una corrección, no es memoria es espacio en disco. 8)

---

### Post by juancarlospaco on 2009-12-23
> **gmunioz said:**
> 
chmod -Rf 777 /home/usuario/datos


Disculpame que te contradiga..., 
pero hacer ejecutables todos los archivos del /home no sirve de nada.
Despues cualquier cosa que abra le va a preguntar si quiere ejecutarlo.

---

### Post by gmunioz on 2009-12-24
hola jua....:

Pues si no los quieres ejecutables
cambia 777 por 666 

Pero si guardas scripts, tendrás que
adjudicarle los permisos uno por uno.

---

