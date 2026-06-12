---
title: "java version 6 update 17"
date: 2009-11-12
forum: Software
---

### Post by drazhe on 2009-11-12
hay alguna manera o paquete deb de instalar la version 6 update 17 de Java? el comando por todos conocidos

sudo aptitude install sun-java6-fonts sun-java6-jre sun-java6-plugin
o 
sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin

me instala el update15 y estoy teniendo problemas con una pagina, 

baje un .bin de la pagina de java, que decia ser un ejecutable, pero al hacer lo primero que dice que hay que hacer para instalarlo ya me tira error...

---

### Post by josecuervo86 on 2009-11-12
Hay alguna razon por la que quieras los debs? Fijate que tambien vas a tener que tener las dependencias satisfechas. De cualquier manera, lo que pedis lo tenes:

[sun-java6-jre]("http://mirrors.kernel.org/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-15-1_all.deb")
[sun-java6-plugin]("http://mirrors.kernel.org/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6-15-1_i386.deb")
[sun-java6-fonts]("http://mirrors.kernel.org/ubuntu/pool/multiverse/s/sun-java6/sun-java6-fonts_6-15-1_all.deb")

---

### Post by drazhe on 2009-11-12
Gracias, pero los archivos que me esas pasando ya los tengo instalados y con esa versión del java tengo algunos problemas.. el Opera se me queda un buen rato cargando y finalmente me tira error del plugin y el firefox directamente se cuelga y tengo que forzar el cierre...

---

### Post by euzkoarima on 2009-11-13
> **drazhe said:**
> baje un .bin de la pagina de java, que decia ser un ejecutable, pero al hacer lo primero que dice que hay que hacer para instalarlo ya me tira error...

Por qué no comentás que error te dio a ver si se te puede dar una mano con eso.
Sin saber cuál es, lo primero que es me ocurre es: le diste permiso de ejecución al .bin ?

Saludos,
Eduardo

---

### Post by drazhe on 2009-11-13
pues, baje el archivo de java.com es un .bin, cuando sigo las instrucciones de la misma pagina para instalarlo (mas abajo pongo parte de las instrucciones y la pagina de donde las saque), al dar al 1er comando

su
y poner mi pass, ya me tira 
su: Fallo de autenticación



algo de las instrucciones son algo asi:
Para instalar el archivo Linux (autoextraíble) Siga estas instrucciones:
En el terminal: Escriba:
su
Escriba la contraseña de usuario root.
Cambie al directorio en el que desee efectuar la instalación. Escriba:
cd <ruta de acceso al directorio>
Por ejemplo, para instalar el software en el directorio /usr/java/, escriba:
cd /usr/java/

Nota acerca del acceso de usuario root: Para instalar el JRE en una ubicación accesible desde todo el sistema, como /usr/local, deberá iniciar la sesión como usuario root para obtener los permisos necesarios. Si no tiene acceso de usuario root, instale el JRE en su directorio de inicio o en un subdirectorio para el que disponga de pe
NOTA: SIGUEN.... para mas datos
[http://www.java.com/es/download/help/5000010500.xml#selfextracting](http://www.java.com/es/download/help/5000010500.xml#selfextracting)

---

### Post by josecuervo86 on 2009-11-13
Ok, en vez de hacer lo que te dice, hace esto que basicamente es similar: Movete al directorio donde tenes el .bin. Suponiendo que sea en el escritorio...

```
cd Escritorio
```

Dale permisos de ejecución

```
chmod +x jre-6u<versión>-linux-i586.bin
```

Ejecuta el .bin

```
sudo ./jre-6u<versión>-linux-i586.bin
```

---

### Post by drazhe on 2009-11-13
ok, pero con eso, solo lo descomprimo en el escritorio, ahora como hago para ponerlo en la carpeta donde debería ir?

---

### Post by drazhe on 2009-11-13
bueno, logre mover esa carpeta a un lugar que no sea el escritorio, el tema es que no consigo eliminar la carpeta que ya esta en el escritorio... me podrian ayudar con eso...

---

### Post by euzkoarima on 2009-11-13
Estaba por decirte que cambiaras
cd Escritorio

por
cd carpeta-donde-quieras-instalar

Raro que no te deje borrar la carpeta anterior. Supongo que es porque instalaste ahí y luego copiaste. Si es así no estoy seguro que la copia funcione bien (tema de links, etc)

Para borrar la carpeta que te quedó en el escritorio probá desde una terminal, parado en el Escritorio el siguiente comando
```
sudo rm -R nombre-carpeta-a-borrar
```

Saludos,
Eduardo

---

### Post by drazhe on 2009-11-13
Muchas gracias a todos! conseguí instalar la ultima versión del java, y ahora funciona todo perfectamente, también conseguí eliminar la carpeta que me aparecía en el escritorio... 

nuevamente gracias a todos los que me ayudaron!

---

### Post by thedarkmedjai on 2009-12-27
A mi me funcionó muy bien este metodo
 

Siguiendolo paso a pasito, logré mi proposito

Tuve que desinstalar la version anterior que tengo de JDK
 
Abrí synaptics y busqué JDK
Di click derecho a todo lo de sun-java6-xxx (bin,jre,etcetera) y seleccioné desinstalar completamente
 
El JDK que utilizé lo descargué de aqui
[http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)
 
cd NombreCarpetaDescarga
chmod +x jdk-6u17-linux-i586.bin
sudo ./jdk-6u17-linux-i586.bin
 mv jdk1.6.0_17 /usr/lib/jvm
 
sudo update-alternatives &#8211;install &#8220;/usr/bin/java&#8221; &#8220;java&#8221; &#8220;/usr/lib/jvm/bin/java&#8221; 1
 sudo update-alternatives &#8211;set java /usr/lib/jvm/bin/java
 
y luego ¡vualá]!
java -version
java version &#8220;1.6.0_17?
Java(TM) SE Runtime Environment (build 1.6.0_17-b04)

y para configurar javac hize lo siguiente
 sudo update-alternatives &#8211;install &#8220;/usr/bin/javac&#8221; &#8220;javac&#8221; &#8220;/usr/lib/jvm/bin/javac&#8221; 1
 sudo update-alternatives &#8211;set javac /usr/lib/jvm/bin/javac
 y obtuve lo siguiente

Utilizando `/usr/lib/jvm/bin/javac&#8217; para proveer `javac&#8217;.
 al final obtuve exito
root@darkmedjai-desktop:/# javac -version
javac 1.6.0_17
 
Y otra cosa para instalar el JRE plugin para que me lo reconociera firefox hize lo siguiente
 
sudo su (para ir a root)
cd /usr/lib/firefox/plugins/
para eliminar el plugin anterior de java
rm libjavaplugin.so (o parecido, no me acuerdo si fue este)
 
y lo sustituí por este
ln -s /usr/lib/jvm/jre/plugin/i386/ns7/libjavaplugin_oji.so
 
nota: puede ser este plugin o el que está en la carpeta ns7-gcc29 si el firefox fue compilado con gcc29
 
y también eliminé el plugin que está en la carpeta mozilla
cd /usr/lib/mozilla/plugins/
rm libjavaplugin.so
 
y también lo sustituí por el mismo
ln -s /usr/lib/jvm/jre/plugin/i386/ns7/libjavaplugin_oji.so
 
y para checar que se puso el direccionamiento
ls -l
 
y para verificar que se instaló el plugin
[r=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.28-17-generic...]("http://www.java.com/en/download/installed.jsp?jre_version=1.6.0_17&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.28-17-generic")
 
Ese fue todo mi viaje, que a todos los que vean este link los ayude.
 
Paginas de ayuda
[-ubuntulinux-9-10/#comment-26...]("http://banpetheblog.wordpress.com/2009/12/26/instalar-java6-u17jdk-o-jre-ubuntulinux-9-10/#comment-26")
 y la guia en inglés para instalar el JRE plugin esta aqui
[linux.html...]("http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html")
 Read more: [.html?showComment=1261896729987_AIe9_BHtDdUARCDmmYFj45M7dv37HdWD_kfPpYc68n5eimxWFCqkKAKjE_7k1AeSvBzB-9ndiRYLancl6U8lmyOQzRChiLObbaV0SNtdsDJonZOToUYCYZcUV17mEzY1f5D5STpOfu-x-5l-4ZOS1elHgiXb7gnIuwSox0390s3oEtjGSGGaPMwKByB-i2OehVCGaIzN7qmFAuI7nb47aDH6JZXTh65Vuj9gTLD47ZEM2qFV9yZPQmo#c5304048804925035327#ixzz0arybBMOv...]("http://www.linux-noa.com.ar/2009/04/instalar-java-se-runtime-environment.html?showComment=1261896729987_AIe9_BHtDdUARCDmmYFj45M7dv37HdWD_kfPpYc68n5eimxWFCqkKAKjE_7k1AeSvBzB-9ndiRYLancl6U8lmyOQzRChiLObbaV0SNtdsDJonZOToUYCYZcUV17mEzY1f5D5STpOfu-x-5l-4ZOS1elHgiXb7gnIuwSox0390s3oEtjGSGGaPMwKByB-i2OehVCGaIzN7qmFAuI7nb47aDH6JZXTh65Vuj9gTLD47ZEM2qFV9yZPQmo#c5304048804925035327#ixzz0arybBMOv")
 

If you think you know everything, someone come's up with more knowledge

---

