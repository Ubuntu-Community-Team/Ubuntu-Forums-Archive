---
title: "Setear variable LD_LIBRARY_PATH"
date: 2009-12-09
forum: Software
---

### Post by euzkoarima on 2009-12-09
En un server 8.04 con tomcat y postgresql necesito instalar unas librerías para conexión con SAP (librfccm.so y libsapjcorfc.so)

Según las intrucciones de SAP: póngalas donde quiera y luego agregue el path a la variable LD_LIBRARY_PATH.

Ok, si se logueara algun usuario, la podría poner, p. ej, en su .bash_profile

Ahora, como arranca todo como servicio, no se loguea nadie, lo único que se me ocurre es ponerla en /etc/profile

Alguna sugerencia al respecto ?

Saludos,
Eduardo

---

### Post by guillermolisi on 2009-12-09
Si es un servicio, no se inicia como si fuera root su propietario ?

Al margen de ello, que pasa si armas dentro del script que inicia ese servicio la definicion de las variables de entorno ?

Todo esto sin conocer en detalle como es realmente el tema con SAP.

---

### Post by juancarlospaco on 2009-12-09
para dejarla en blanco:

NOMBRE_DE_VARIABLE=

para setearla:

NOMBRE_DE_VARIABLE=valor

*desde bash como root.*

---

### Post by euzkoarima on 2009-12-09
> **guillermolisi said:**
> Si es un servicio, no se inicia como si fuera root su propietario ?

Al margen de ello, que pasa si armas dentro del script que inicia ese servicio la definicion de las variables de entorno ?

Todo esto sin conocer en detalle como es realmente el tema con SAP.

Creo que si, que ejecuta como root, así que una posibilidad sería ponerlo en /root/.bashrc o /root/.profile

Voy a estar hoy con este tema. Si llego a alguna conclusión que valga la pena la cuento

---

### Post by euzkoarima on 2009-12-12
Bueno, les cuento como terminó esta historia:

Primero definí en /root/.bashrc (y en la cuenta del administrador también para probar):

```
export LD_LIBRARY_PATH=/ruta/a-las.so
```

Y seguía sin andar, daba el siguiente error

```
jfruxadmin@jfrux-server:~$ java -jar sapjco.jar
java.lang.ExceptionInInitializerError: JCO.classInitialize(): Could not load middleware layer 'com.sap.mw.jco.rfc.MiddlewareRFC'
JCO.nativeInit(): Could not initialize dynamic link library sapjcorfc [/usr/local/lib/libsapjcorfc.so: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory]. java.library.path [/usr/lib/jvm/java-6-sun-1.6.0.17/jre/lib/i386/server:/usr/lib/jvm/java-6-sun-1.6.0.17/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.17/jre/../lib/i386:/usr/local/lib:/usr/java/packages/lib/i386:/lib:/usr/lib
```

Un compañero googlió un rato y parece que había que instalar libstdc++2.10-glibc2.2_2.95 pero con apt en hardy parece que no está.

Al final se arregló con:

```
wget mirrors.kernel.org/ubuntu/pool/universe/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-24_i386.deb
sudo dpkg --install libstdc++2.10-glibc2.2_2.95.4-24_i386.deb
```

tambien puede ser (lo probé un otro hardy con GUI) bajando la de debian

[http://ftp.br.debian.org/debian/pool/main/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb](http://ftp.br.debian.org/debian/pool/main/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb)

Dejo esto acá por si algún otro se cruza con esto.

Saludos,
Eduardo

---

