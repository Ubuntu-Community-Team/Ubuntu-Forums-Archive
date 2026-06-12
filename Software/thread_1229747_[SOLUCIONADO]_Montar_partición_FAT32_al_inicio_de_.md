---
title: "[SOLUCIONADO] Montar partición FAT32 al inicio de sesión"
date: 2009-08-02
forum: Software
---

### Post by ivisdrek on 2009-08-02
Hola a todos. Tengo una partición FAT32 que utilizo para compartir algunos archivos con Windows. La pregunta es: ¿existe alguna manera de montar esta partición al inicio de sesión de Ubuntu?

Saludos y gracias.

---

### Post by Carlos C on 2009-08-05
Si, puedes hacerlo añadiendola a tu archivo "/etc/fstab". Primero debes saber como es nombrada tu partición. PAra eso escribe en el terminal:
```
sudo fsdisk -l
```
Supongamos que tu partición es "/dev/sdb1". Necesitas montar esa partición en una carpeta. Crea una carpeta en dónde quieras montar de ahí en adelante la partición. Supongamos que lo quieres hacer en /media/Fat32:
```
sudo mkdir /media/Fat32
```
Basta que entonces edites el archivo fstab:
```
sudo gedit /etc/fstab
```
Luego añadir en la tabla de particiones:
```
/dev/sdb1 /media/Fat32 vfat iocharset=utf8,umask=000 0 0
```
Tienes que cambiar los parámetros por los valores correspondientes a tu ruta del disco y la carpeta que hayas creado.
Saludos.

---

### Post by ivisdrek on 2009-08-05
Muchas gracias, Carlos, he logrado hacerlo, aunque el comando 

sudo fsdisk -l

no me ha funcionado, pero ha sido fácil solucionarlo desde el Editor de Particiones. 
Sin embargo me he encontrado con el problema de que ahora no puedo poner enlaces en el escritorio... Cuando intento crear un enlace me sale un mensaje avisándome de que esa acción no está permitida. ¿Sabes si he podido hacer algo mal o si hay alguna forma de solucionarlo?

Gracias otra vez

Saludos

---

### Post by Carlos C on 2009-08-05
Hola. El comando no te funcionó porque lo escribí mal. El comando correcto es:
```
sudo fdisk -l
```
Sobre el error, ¿cómo tratas de hacer el enlace?

---

### Post by radixs on 2009-08-05
> **Carlos C said:**
> 
```
/dev/sdb1 /media/Fat32 vfat iocharset=utf8,umask=000 0 0
```Tienes que 

Carlos C veo que dejesta el  ultimo valor en default ```
 0 
```
en caso que el sistema se apagara de forma incorrecta al monentor de iniciar el sistema es cheque las particiones, como estan en default con valor 0, con esto la particion no s chequearia, Pienso (yo Radixs) que lo correcto seria integrarla al chequeo.

Como se hace para integrarla, si miran el ftab, la particion raiz tiene como valor 0 1, si ademas tienes la particion /home separada de / esta tendra como valor 0 2, por ende siguiendo la secuencia deberia estar con valor 0 3

ej: yo tengo montada un 3ª particion montada en mi casi con nombre Datos, ais esta integrada en mi ftab

```
/dev/sda7       /media/datos    ext3    defaults        0 3
```

Bueno eso es segun mi punto de vista ;)

---

### Post by 3nG3ndR0 on 2009-08-07
bueno lo lo realizo asi, es tan fácil como modificar un archivo  y escribimos en el terminal,

```
$ sudo gedit /etc/hal/fdi/policy/preferences.fdi
```

buscamos la linea **<merge key="storage.automount_enabled_hint" type="bool">false</merge>** y al final cambiamos **false** por **true** y listo. Cuando reiniciamos nuestras unidades se cargaran automáticamente.

```
**<merge key="storage.automount_enabled_hint" type="bool">true</merge>** 
```

---

### Post by ivisdrek on 2009-08-09
Gracias a todos por la ayuda. He probado todas las sugerencias y me funcionan, pero sigo sin poder crear enlaces. Me pone esto:

Hubo un error al crear el enlace simbólico en /media/Compartido.
Y luego en detalles:
Error al crear el enlace simbólico: Operación no permitida

En fin, ¿se les ocurre por qué me sucede esto?

Un saludo

---

### Post by Sanctus119 on 2009-08-09
Antes de intentar montar una particion en /media/Compartido, tienes que ir a /media y crear la carpeta Compartido.

---

### Post by gmunioz on 2009-08-10
Hola ivi....:

si lo que quieres, es crear un enlace

simbólico, en una partición fat, pues

simplemente no se puede.

¿Por qué?

Porque los enlaces simbólicos y duros,

son propios y particulares de los sistemas

de archivos GnuLinux.

---

### Post by ivisdrek on 2009-08-10
Gracias[COLOR=Black] guminioz, pues tendré que abandonar mi proyecto de tener todas mis carpetas a un solo click en el escritorio...[URL="http://ubuntuforums.org/member.php?u=252237"]
[/URL][/COLOR]

---

### Post by EnriqueK on 2009-08-10
Si se puede crear un enlace simbólico de carpetas y/o archivos que se encuentren en cualquier partición que esté montada.
Para crear enlaces simbólicos en el escritorio empleo el siguiente método que está basado en que cuando arrastras al terminal un archivo o carpèta cualquiera situada en cualquier partición montada, ocurre que escribe su ruta absoluta en el terminal, basado en esto, haz lo siguiente
abre terminal y pones **ln -s** dejas un espacio, navega hasta la carpeta o archivo al que le quieras crear un enlace y lo arrastras al terminal, finalmente entra al **menú Lugares**, arrastras al terminal el ícono de E·scritorio -->Enter y ya

---

### Post by ivisdrek on 2009-08-11
Estimado Enriquek, muchas gracias por tu ayuda, pero la verdad es que mis conocimientos de informática son bastante limitados y ya lo de trabajar con la terminal tengo que ir muy poco a poco. Te agradecería mucho que me explicaras mejor lo de navegar hasta la carpeta y luego arrastrar hasta el terminal.

De nuevo gracias y saludos

---

### Post by gmunioz on 2009-08-11
Hola ivi....:

Entonces no es que quieres crear un enlace simbólico

**en** la partición fat

Sino que quieres crear un enlace simbólico **a** la partición

fat en tu escritorio.

Pulsa: aplicaciones - accesorios - terminal

En la consola escribe:

sudo ln -s /media/Compartida /home/tuusuario/Escritorio/Compartida

---

### Post by EnriqueK on 2009-08-11
Si has logrado montar la particón al inicio. debes de tener un ícono lanzador de la misma en tu escritorio, al parecer si esto no es así, es por que no jas logrado el montaje al inicio , en este caso te sugiero unstales **Disk Manager** m este paquete no se encuentra en los repositorios de Jaunty , pero si figura en los de Intrepid, de allí lo descargué y funciona muy bien, este programa se encarga del montaje de particiones sin mas trámites que el de indicar cuales son las particiones que quieres montar, ñp puedes descargar de 
```
http://mirrors.kernel.org/ubuntu/pool/universe/d/disk-manager/disk-manager_1.0.1-2_all.deb
```
Una vez montadas la particiónes te aparexerán los lanzadores en el escritorio  las particiones montadas y de allí podrás navegar y así crear los enlaces simbólicos de las carpetas que queras en tu escritorio.
Solo recalcar que uso Jaunty y a pesar de que Disk Manager  no figura en sus repositorios, lo instalé manualmente y funciona muy bien.

---

### Post by ivisdrek on 2009-08-12
Finalmente he solucionado el problema. El volumen FAt32 me aparece automáticamente al inicio de sesión y he creado los enlaces correspondientes y me funcionan a la perfección.

¡Gracias a todos por la ayuda!

Lamento no haberme expresado bien y haber tenido que dar tantas vueltas para encontrar la solución. Por si a alguien se le plantea algo parecido, resumo los pasos que he dado:

Para saber el nombre de la partición en el sistema:

                                  Code:
 sudo fdisk -l 

 Luego es necesario crear una carpeta donde montar la partición. Si lo queremos hacer, por ejemplo, en  /media/Fat32 (yo la creé en otra ruta, pero valga ésta como ejemplo):



  Code:
 sudo mkdir /media/Fat32

 A continuación editamos el archivo fstab:
  

  Code:
 sudo gedit /etc/fstab

Luego se añade una última linea con el código:
  

  Code:
 /dev/sdb1 /media/Fat32 vfat iocharset=utf8,umask=000 0 3

La partición aparecerá montada al inicio de sesión.


     Pero veremos que si queremos crear un enlace en el Escritorio el sistema no lo va a admitir. Hay que crear un enlace simbólico.
     Entonces escribimos en el Terminal:
 
sudo ln -s 

     Se deja un espacio y se arrastra hasta esa fórmula la carpeta o archivo de la que se quiera crear un enlace. Al arrastrar la carpeta se crea un comando automáticamente en el terminal, como este:
 

 sudo ln -s '/media/Fat32/archivo' 

     A continuación vamos a Lugares y arrastramos hasta el Terminal el icono Escritorio y nos da un comando parecido a éste:  
 

 sudo ln -s '/media/Fat32/archivo' '/media/Escritorio' 
 

 Pulsamos enter y repetimos la operación con cualquier otra carpeta o archivo que deseemos.




De verdad, muchas gracias a todos.


¡SOLUCIONADO!!!!!

---

### Post by EnriqueK on 2009-08-12
No debes poner **sudo** por que estás creando un enlace en tu escritorio que se encuentra dentro de tu carpeta de usuario,  o sea el comado siguiedo tu ejemplo sería 

ln -s '/media/Fat32/archivo' '/media/Escritorio' 

Cuando quieras crear un enlace simbólico dentro del directorio raiz / , en ese caso si debes poner **sudo**

---

### Post by ivisdrek on 2009-08-12
Hola, Enriquek, pues yo lo he hecho con sudo y me ha funcionado... Los aspectos técnicos la verdad es que no los entiendo bien, para mí todavía están en otra dimensión. Todos los avances que hago con Ubuntu los anoto en una especie de guía que me voy confeccionando; anoto tu observación. Ya probaré la diferencia de hacerlo de un modo o de otro.

Pero por ahora estoy contento con el resultado.

Un saludo!

---

### Post by ivisdrek on 2009-08-12
Oye, el comando completo que utilicé fue éste:

                                 sudo ln -s '/home/personal/Fat32/archivo' '/home/personal/Escritorio'  [FONT=monospace]

¿Te referías a eso?

Entonces la guía que he publicado está mal...:(

Lo siento...
[/FONT]

---

### Post by Carlos C on 2009-08-12
Basta con saber que no es necesario usar sudo. Te recomiendo tener claro para qué sirve sudo, por lo mismo te sugiero que leas esta página:

[http://www.guia-ubuntu.org/index.php?title=Sudo](http://www.guia-ubuntu.org/index.php?title=Sudo)

Saludos.

---

