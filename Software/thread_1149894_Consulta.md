---
title: "Consulta ??"
date: 2009-05-05
forum: Software
---

### Post by javier-2714 on 2009-05-05
Hace rato no andaba por acá saludos a todos.
Yo antes usaba ubuntu feisty y cuando tenia algún programa binario copiaba la carpeta en /opt y creaba un enlace sinbolico en /usr/bin para llamarlo desde la consola y ahora un ubuntu hardy no me funciona, tampoco si voy a /opt y hago dle clik sobre el no abre el programa , pero si esta en el home si abre, me podrían decir la forma correcta de hacerlo.

Para que quede claro lo que quiero es instalar un programa binario que no se instala solo se lanza, pero no lo quiero tener en el home lo quiero poner en /opt y poder llamarlo desde la consola,agradeseria sus consejos.

Javier saludos.

---

### Post by Mauro22 on 2009-05-05
Por lo que tengo entendido, podes ponerlo directamente en /usr/bin y darle permisos de ejecucion y listo.

Si no en el home (aunque no queres) podes crear una carpeta llamada bin (o sea /home/tuusuario/bin y ahi tiras todos los programas)

---

### Post by javier-2714 on 2009-05-05
Si lo pongo directamente en /usr/bin  me hace lo mismo no pasa nada le doy permiso de ejecución lectura y escritura pero no pasa nada lo pongo en home y funciona ja la consola me devuelve esto:

javier@javier-desktop:~$ phun
ldd: ./phun.bin: No existe el fichero ó directorio
/usr/bin/phun: 14: ./phun.bin: not found
javier@javier-desktop:~$

---

### Post by josecuervo86 on 2009-05-05
Che y si probas ejecutarlo desde terminal a traves de la ruta, por ejemplo un archivo en **/usr/bin** llamado **prueba.tipo**

```
$ cd /usr/bin
$ ./prueba.tipo
```

Fijate que error tira la terminal

---

### Post by javier-2714 on 2009-05-05
Haber el programa es [http://www.phunland.com/wiki/Home](http://www.phunland.com/wiki/Home) comprimido en .tgz lo descomprimo en /opt quedaría /opt/Phun yo me explique mal el lanzador del programa no es el .bin sino phun que es un script en shell yo lo que hacia antes era crear un enlace simbolico de phun que es un script en shell el lanzador del programa en /usr/bin de esta forma yo ponia el acceso en aplicaciones,o desde la consola ponia 
$phun 
y el programa abría pero eso en feisty en hardy no me deja si pongo en consola:
javier@javier-desktop:~$ cd /opt/Phun
javier@javier-desktop:/opt/Phun$ phun
si abre el programa yo lo que quiero es que quede como antes entrar en consola poner $ phun y abra o simplemente poner el acceso en aplicaciones>juegos cuando lo creo le doy en examinar le muestro el camino /opt/Phun/phun no se lanza no se si me explico bien gracias .

---

### Post by guillermolisi on 2009-05-07
> **javier-2714 said:**
> Haber el programa es [http://www.phunland.com/wiki/Home](http://www.phunland.com/wiki/Home) comprimido en .tgz lo descomprimo en /opt quedaría /opt/Phun yo me explique mal el lanzador del programa no es el .bin sino phun que es un script en shell yo lo que hacia antes era crear un enlace simbolico de phun que es un script en shell el lanzador del programa en /usr/bin de esta forma yo ponia el acceso en aplicaciones,o desde la consola ponia 
$phun 
y el programa abría pero eso en feisty en hardy no me deja si pongo en consola:
javier@javier-desktop:~$ cd /opt/Phun
javier@javier-desktop:/opt/Phun$ phun
si abre el programa yo lo que quiero es que quede como antes entrar en consola poner $ phun y abra o simplemente poner el acceso en aplicaciones>juegos cuando lo creo le doy en examinar le muestro el camino /opt/Phun/phun no se lanza no se si me explico bien gracias .
Me da la impresion que, en caso de no haber problemas de permisos, el tema se reduce a como esta compuesto el path del entorno del usuario que estas utilizando.

Si mostras la salida del comando env te vas a dar cuenta que /opt/Phun no esta en la lista de la variable path. Proba agregando ese camino a la variable path del archivo .profile de tu user.

Fijate en el siguiente bloque ya que podes agregarlo ahi o aparte, duplicandolo, para mantener .profile original.
```
# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}":**/opt/Phun**
fi
```

Sugiero esto para no tocar los archivos con definicion por defecto de Bash que estan en /etc.

Notese que en elbloque que muestro se incluye un directorio bin dentro del home del usuario, que tambien podria servir, como ya indicaron.

Tambien seria interesante ver como estan los permisos de /opt y /opt/Phun, por las dudas (con la salida de ls -al de cada nivel de directorio alcanzaria).

---

### Post by javier-2714 on 2009-05-07
Hola guillermolisi el .profile no lo encuentro en mi home no esta y los permisos creo que estan bien ahí pongo el resultado de ls -al:

javier@javier-desktop:/opt$ ls -al
total 20
drwxr-xr-x  5 root  root   4096 2009-05-05 15:19 .
drwxr-xr-x 22 root  root   4096 2009-05-06 23:24 ..
drwxr-xr-x  5 10490 floppy 4096 2009-04-30 19:27 Adobe
drwxr-xr-x  8 root  root   4096 2009-05-05 20:20 Phun
drwxr-xr-x  6 root  root   4096 2009-03-20 19:48 picasa

javier@javier-desktop:/opt/Phun$ ls -al
total 8904
drwxr-xr-x 8 root   root      4096 2009-05-05 20:20 .
drwxr-xr-x 5 root   root      4096 2009-05-05 15:19 ..
-rw-rw-r-- 1 javier javier    1045 2009-02-23 12:25 autoexec.cfg
-rw-rw-r-- 1 javier javier    7095 2009-05-05 23:34 config.cfg
-rw-rw-r-- 1 javier javier     372 2009-03-19 10:43 Credits.txt
drwxrwxr-x 6 root   root      4096 2009-05-05 15:19 data
drwxrwxr-x 2 root   root      4096 2009-05-05 15:19 lib
-rw-rw-r-- 1 javier javier    2189 2009-03-19 10:30 LICENSE.txt
-rw-rw-r-- 1 javier javier   23465 2009-05-05 23:34 Logfile.txt
drwxrwxr-x 2 root   root      4096 2009-05-05 15:19 materials
-rwxr-xr-x 1 root   root       408 2009-05-05 15:20 phun
-rwxr-xr-x 1 root   root   8970440 2009-03-31 09:02 phun.bin
-rw-rw-r-- 1 javier javier   34390 2009-03-31 06:04 README.txt
drwxrwxr-x 3 root   root      4096 2009-05-05 15:39 scenes
drwxrwxr-x 2 root   root      4096 2009-02-13 12:26 screenshots
-rwxrwxr-x 1 javier javier     157 2009-03-31 09:02 startbrowser.sh
drwxrwxr-x 2 root   root      4096 2009-05-05 15:19 textures
-rw-rw-r-- 1 javier javier    1376 2009-03-12 09:33 thyme.cfg

lo curioso es que si le doy doble clik a phun si se lanza,el problema viene al querer crear el enlace simbólico, no se que pasa no soy un usuario muy avanzado en feisty me salia todo fasil en hardy cambiaron las cosas me pone mas trabas cambiaron las formas de hacer las cosas el /opt no estaba tuve que crearlo me gusta instalar ahí lo que no es de la distribución para no tocar el sistema bueno te agradezco cualquier ayuda  saludos.

---

### Post by guillermolisi on 2009-05-07
> **javier-2714 said:**
> Hola guillermolisi el .profile no lo encuentro en mi home no esta y los permisos creo que estan bien ahí pongo el resultado de ls -al:

javier@javier-desktop:/opt$ ls -al
total 20
drwxr-xr-x  5 root  root   4096 2009-05-05 15:19 .
drwxr-xr-x 22 root  root   4096 2009-05-06 23:24 ..
drwxr-xr-x  5 10490 floppy 4096 2009-04-30 19:27 Adobe
drwxr-xr-x  8 root  root   4096 2009-05-05 20:20 Phun
drwxr-xr-x  6 root  root   4096 2009-03-20 19:48 picasa

javier@javier-desktop:/opt/Phun$ ls -al
total 8904
drwxr-xr-x 8 root   root      4096 2009-05-05 20:20 .
drwxr-xr-x 5 root   root      4096 2009-05-05 15:19 ..
-rw-rw-r-- 1 javier javier    1045 2009-02-23 12:25 autoexec.cfg
-rw-rw-r-- 1 javier javier    7095 2009-05-05 23:34 config.cfg
-rw-rw-r-- 1 javier javier     372 2009-03-19 10:43 Credits.txt
drwxrwxr-x 6 root   root      4096 2009-05-05 15:19 data
drwxrwxr-x 2 root   root      4096 2009-05-05 15:19 lib
-rw-rw-r-- 1 javier javier    2189 2009-03-19 10:30 LICENSE.txt
-rw-rw-r-- 1 javier javier   23465 2009-05-05 23:34 Logfile.txt
drwxrwxr-x 2 root   root      4096 2009-05-05 15:19 materials
-rwxr-xr-x 1 root   root       408 2009-05-05 15:20 phun
-rwxr-xr-x 1 root   root   8970440 2009-03-31 09:02 phun.bin
-rw-rw-r-- 1 javier javier   34390 2009-03-31 06:04 README.txt
drwxrwxr-x 3 root   root      4096 2009-05-05 15:39 scenes
drwxrwxr-x 2 root   root      4096 2009-02-13 12:26 screenshots
-rwxrwxr-x 1 javier javier     157 2009-03-31 09:02 startbrowser.sh
drwxrwxr-x 2 root   root      4096 2009-05-05 15:19 textures
-rw-rw-r-- 1 javier javier    1376 2009-03-12 09:33 thyme.cfg

lo curioso es que si le doy doble clik a phun si se lanza,el problema viene al querer crear el enlace simbólico, no se que pasa no soy un usuario muy avanzado en feisty me salia todo fasil en hardy cambiaron las cosas me pone mas trabas cambiaron las formas de hacer las cosas el /opt no estaba tuve que crearlo me gusta instalar ahí lo que no es de la distribución para no tocar el sistema bueno te agradezco cualquier ayuda  saludos.

Parece que no es tema de permisos, no solo por lo que contas sino por lo que se ve como salida del ls.

Podrias mostrarnos como llevas a cabo y con que usuario la operacion para crear el link de /opt/Phun/phun a /usr/bin ?

---

### Post by javier-2714 on 2009-05-07
Asi pongo en consola :

sudo ln -s /opt/Phun/phun /usr/bin

luego verifico,navego en forma grafica al directorio /usr/bin y lo creo correctamente pongo en consola:

javier@javier-desktop:~$ phun
ldd: ./phun.bin: No existe el fichero ó directorio
/usr/bin/phun: 14: ./phun.bin: not found

saludos.

---

### Post by Hei Ku on 2009-05-07
No debería ser: sudo ln -s /opt/Phun/phun /usr/bin/phun

Y qué es el phun.bin? Asi se llama el ejecutable? No es simplemente phun?

---

### Post by javier-2714 on 2009-05-07
Si perdón me falto el final lo ice asi:

sudo ln -s /opt/Phun/phun /usr/bin/phun

el que llama es phun solo como bien dices 

saludos.

---

### Post by gceli on 2009-05-17
Javier probaste hacer un enlace simbolico con otro programa?

---

