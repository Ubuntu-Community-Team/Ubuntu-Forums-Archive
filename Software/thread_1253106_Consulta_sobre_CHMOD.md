---
title: "Consulta sobre CHMOD"
date: 2009-08-29
forum: Software
---

### Post by z37a on 2009-08-29
Gente les tengo una consulta. Estoy organizando mi Fileserver para que este prolijo el tema de lso permisos, a todo esto no se me ocurrio mejor idea que darle a la carpeta un chmod 775 -R, por lo cual Todo el contenido ahora es ejecutable. Lo que necesito hacer es ejecutar un chmod que me permita sacarle lso permisos de ejecucion a TODO MENOS directorios, esto es asi ya que necesito dejarle los permisos a los subdirectorios. Alguna idea de como puedo hacer para diferenciar los directorios de archivos mediante el chmod?

---

### Post by gmunioz on 2009-08-29
Hola z37....:

Previamente te recuerdo que existe el comando man.

Con la orden en una terminal:

man chmod

Tendrás abundante información al respecto, tal como:

Con el comando chmod, lo que haces es darle permisos a los
archivos y directorios.

Estos permisos, tienen la misión de dar, respecto de los
archivos y directorios las posibilidades de:

    Lectura
    Escritura
    Ejecución

Mediante el comando ls, se obtiene la información de los
archivos y directorios mediante diferentes campos de 
información, referente a los permisos es la primer columna
que nos informa acerca de los permisos, por ejemplo:

   -rwxr-x--- 

Estas letras obrantes en la primer columna nos informan
quien puede accionar y que permisos tiene el archivo

Estas letras están agrupadas en tres grupos con tres posiciones 
cada uno de ellos, más una primera posición que informa acerca de 
que clase de archivo se trata (d) directorios, o (-) archivos comunes
En el ejemplo la primera posición es (-) con lo cual es un archivo  
comun de datos ya sea binario o ejecutable, en este ejemplo.

Tipos de archivo
Contenido    Significado
-            Archivo común
d            Directorio
c            Dispositivo de caracteres (tty o impresora)
b            Dispositivo de Bloque (usualmente disco rígido o CD-ROM)
l            Enlace simbólico
s            Socket
p            Pipe



El primer grupo de tres, que en el ejemplo son rwx informa acerca de
que clase de permisos tiene el dueño del archivo, (u) user/owner
El segundo grupo de tres, que en el ejemplo son r-x informa acerca de
que clase de permisos tiene el grupo del fichero (g) group
el tercer grupo de tres, que en el ejemplo son ---  informa acerca de 
que clase de permisos tienen todos los demás usuarios fichero (o) others.

    r :equivale a permiso de lectura
    w :equivale a permiso de escritura
    x :equivale a permiso de ejecución

Para cambiar el dueño del archivo se usa el comando chmod
    
    chmod permisos archivo

Los permisos se pueden especificar de diferentes formas por  ejemplo;

chmod ugo+rwx archivo     (da permisos rwx a todos, user,group,others)
chmod ugo-x archivo       (quita permiso x (ejecucion) a todos, user,group,others)
chmod o-rwx archivo       (quita permisos rwx a others)
chmod u=rwx,g=rx archivo  (da permisos rwx a user y rx a group)

Existe otra forma que es utilizando números:

Para establecer el permiso habrá que sumar los dígitos octales de acuerdo a una tabla 

Número octal  Permiso
4000          Establece el número de identificación de usuario al ejecutarse SUID [a]
2000          Establece el número de identificación de grupo al ejecutarse SGID[a]
1000          Establece el bit adhesivo[a]
0400          Lectura por parte del dueño
0200          Escritura por parte del dueño
0100          Ejecución por parte del dueño
0040          Lectura por parte del grupo
0020          Escritura por parte del grupo
0010          Ejecución por parte del grupo
0004          Lectura por parte de los otros
0002          Escritura por parte de los otros
0001          Ejecución por parte de los otros

Para dar un ejemplo de la suma que se tendrá que realizar, tomemos un archivo con los permisos expresados en forma simbólica y realicemos la conversión. Para representar -rwxr-x---

  0400      Lectura por parte del dueño
+ 0200      Escritura por parte del dueño
+ 0100      Ejecución por parte del dueño
+ 0040      Lectura por parte del grupo
+ 0010      Ejecución por parte del grupo
-----------------------------------------
  0750      Resultado

Espero te sea de utilidad.

---

### Post by z37a on 2009-08-29
> **gmunioz said:**
> Hola z37....:

Previamente te recuerdo que existe el comando man.

Con la orden en una terminal:

man chmod

Tendrás abundante información al respecto, tal como:

Con el comando chmod, lo que haces es darle permisos a los
archivos y directorios.

Estos permisos, tienen la misión de dar, respecto de los
archivos y directorios las posibilidades de:

    Lectura
    Escritura
    Ejecución

Mediante el comando ls, se obtiene la información de los
archivos y directorios mediante diferentes campos de 
información, referente a los permisos es la primer columna
que nos informa acerca de los permisos, por ejemplo:

   -rwxr-x--- 

Estas letras obrantes en la primer columna nos informan
quien puede accionar y que permisos tiene el archivo

Estas letras están agrupadas en tres grupos con tres posiciones 
cada uno de ellos, más una primera posición que informa acerca de 
que clase de archivo se trata (d) directorios, o (-) archivos comunes
En el ejemplo la primera posición es (-) con lo cual es un archivo  
comun de datos ya sea binario o ejecutable, en este ejemplo.

Tipos de archivo
Contenido    Significado
-            Archivo común
d            Directorio
c            Dispositivo de caracteres (tty o impresora)
b            Dispositivo de Bloque (usualmente disco rígido o CD-ROM)
l            Enlace simbólico
s            Socket
p            Pipe



El primer grupo de tres, que en el ejemplo son rwx informa acerca de
que clase de permisos tiene el dueño del archivo, (u) user/owner
El segundo grupo de tres, que en el ejemplo son r-x informa acerca de
que clase de permisos tiene el grupo del fichero (g) group
el tercer grupo de tres, que en el ejemplo son ---  informa acerca de 
que clase de permisos tienen todos los demás usuarios fichero (o) others.

    r :equivale a permiso de lectura
    w :equivale a permiso de escritura
    x :equivale a permiso de ejecución

Para cambiar el dueño del archivo se usa el comando chmod
    
    chmod permisos archivo

Los permisos se pueden especificar de diferentes formas por  ejemplo;

chmod ugo+rwx archivo     (da permisos rwx a todos, user,group,others)
chmod ugo-x archivo       (quita permiso x (ejecucion) a todos, user,group,others)
chmod o-rwx archivo       (quita permisos rwx a others)
chmod u=rwx,g=rx archivo  (da permisos rwx a user y rx a group)

Existe otra forma que es utilizando números:

Para establecer el permiso habrá que sumar los dígitos octales de acuerdo a una tabla 

Número octal  Permiso
4000          Establece el número de identificación de usuario al ejecutarse SUID [a]
2000          Establece el número de identificación de grupo al ejecutarse SGID[a]
1000          Establece el bit adhesivo[a]
0400          Lectura por parte del dueño
0200          Escritura por parte del dueño
0100          Ejecución por parte del dueño
0040          Lectura por parte del grupo
0020          Escritura por parte del grupo
0010          Ejecución por parte del grupo
0004          Lectura por parte de los otros
0002          Escritura por parte de los otros
0001          Ejecución por parte de los otros

Para dar un ejemplo de la suma que se tendrá que realizar, tomemos un archivo con los permisos expresados en forma simbólica y realicemos la conversión. Para representar -rwxr-x---

  0400      Lectura por parte del dueño
+ 0200      Escritura por parte del dueño
+ 0100      Ejecución por parte del dueño
+ 0040      Lectura por parte del grupo
+ 0010      Ejecución por parte del grupo
-----------------------------------------
  0750      Resultado

Espero te sea de utilidad.

Te agradezco tu respuesta, pero ya consulte el man y el problema que me encuentro es que no encuentro forma de diferenciar los archivos de las carpetas a la hora de aplicar los permisos. Es mas te comento que en el man esta faltando un dato que en mi caso es el que mas uso y es el uso de "chmod a+x file" en donde el A del a+x es para aplicarle el permiso a TODOS sin necesidad de hacer ugo. Basicamente lo que necesitaria hacer es a una carpeta, con subcarpetas ejecutarle un "chmod a-x {folder} -R" y luego algun comando para permitir un "chmod a+x" solo a las subcarpetas, pero no a los archivos.

---

### Post by oktubrer on 2009-08-30
Quizas hay otras opciones más eficientes, pero lo que se me ocurre es que listes solamente los directorios y tomar esa salida como entrada para el comando chmod.
Una manera de listar solo los directorios es
```
find . -type d
```
Esto lista recursivamente todos los directorios dentro del path donde te encuentres.  Si queres que sean TODOS, reemplazas el "." por "/"
Para tomar la salida como entrada para chmod, usas XARGS
```
find / -type d | xargs chmod a+x 
```

Espero que te sirva, por las dudas leete la documentación para asegurarte de no hacer una macana.

---

### Post by gmunioz on 2009-08-30
Hola z37...:

Efectivamente falta detallar el parámetro

     a: todos los tipos de usuario (dueño, grupo y otros)

Y faltan detallar

Las opciones típicas:

    -R recursivo, para que aplique en los subdirectorios de la ruta.
    -v informa sobre cada archivo procesado
    -c es como -v, pero informa solo acerca de los archivos modificados
    -f no informa nada, modo silencioso

Respecto de tu planteo:

"...chmod a+x solo a las subcarpetas, pero no a los archivos..."

Estimo que todo se puede en GnuLinux, pero ¿subdirectorios ejecutables?

no me imagino ejecutando un subdirectorio. O quizás te refieres a dar

permisos de ejecución a los archivos contenidos en los subdirectorios

sin otorgarselos a los archivos contenidos en el directorio que los

aloja.

Si es así entonces esto te puede servir:

# Encontrar directorios (-type d) en el directorio actual (.) y darles
# acceso 755
find . -type d -exec chmod 755 {} \;

# Encontrar archivos (-type f) en el directorio actual (.) y darles
# acceso 644
find . -type f -exec chmod 644 {} \;

# Encontrar archivos (-type f) html (-name '*.htm*') en el subdirectorio
# web (./web) y darles acceso 644
find ./web -type f -name '*.htm*' -exec chmod 644 {} \;

# Encontrar archivos/directorios con permiso 777 (-perm 777) en el
# directorio actual (.) y darles acceso 755. La opción -print entrega
# más información sobre el resultado
find . -perm 777 -exec chmod 755 {} \; -print

Saludos.

---

### Post by z37a on 2009-08-30
> **gmunioz said:**
> 
# Encontrar directorios (-type d) en el directorio actual (.) y darles
# acceso 755
find . -type d -exec chmod 755 {} \;


Mil gracias este era el comando justo, el unico cambio lo hize 775 en vez de 755, pero me sirvio, y ahora ya entendi como hacer para organizar mejor los permisos con estas lineas!!!!!

oktubrer, el find con el xargs no me funciono a la hora de aplicar los permisos me dice que no encuentra el directorio.

---

### Post by gmunioz on 2009-08-30
Hola z37....:

Felicitaciones por haber conseguido loque buscabas.

Ahora:

1- Pon solved al post.

2- si te interesa aprender sobre el tema

visita este sitio:

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

