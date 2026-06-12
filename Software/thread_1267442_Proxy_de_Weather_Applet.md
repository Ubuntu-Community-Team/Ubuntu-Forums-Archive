---
title: "Proxy de Weather Applet"
date: 2009-09-15
forum: Software
---

### Post by kabubi on 2009-09-15
Alguno tiene idea de como configurar el proxy específicamente para ese applet... 
De hecho tengo el proxy configurado dentro de ubuntu y me funciona para casi todo... excepto para esto, no puedo ver la temperatura se queda actualizando y nada.

Gracias.

---

### Post by Hei Ku on 2009-09-15
Los temas distintos van en threads aparte, gracias.

Ante cualquier duda, lee aca: [http://ubuntuforums.org/showthread.php?t=1222572](http://ubuntuforums.org/showthread.php?t=1222572)

---

### Post by kabubi on 2009-09-30
Muchas gracias por avisarme, y les pido mil disculpas.

---

### Post by Leandro17 on 2009-09-30
> **kabubi said:**
> Alguno tiene idea de como configurar el proxy específicamente para ese applet... 
De hecho tengo el proxy configurado dentro de ubuntu y me funciona para casi todo... excepto para esto, no puedo ver la temperatura se queda actualizando y nada.

Gracias.

sabes como agregar el zip de tu ciudad?

---

### Post by gmunioz on 2009-09-30
Hola lea.....:

Editar el archivo   /etc/bash.bashrc

Pulsa Aplicaciones - Accesorios - Terminal

En la consola ejecutas

```
sudo su

gedit /etc/bash.bashrc

```
Agrega las siguientes líneas al final del archivo

```
export http_proxy=http://username:password@proxyserver.net:port/
export https_proxy=http://username:password@proxyserver.net:port/
export ftp_proxy=http://username:password@proxyserver.net:port/
```

Guarda el archivo y cierra gedit

Edita el archivo  /etc/environment

Ejecuta

```
gedit /etc/environment
```

Agrega las siguientes lineas al final del archivo

```
http_proxy=http://username:password@proxyserver.net:port/
https_proxy=http://username:password@proxyserver.net:port/
ftp_proxy=http://username:password@proxyserver.net:port/
```

Guarda el archivo y cierra gedit

Edita el archivo /etc/apt/apt.conf

```
gedit /etc/apt/apt.conf
```

Agrega las siguientes líneas al final del archivo:

```
Acquire::http::Proxy "http://username:password@proxyserver.net:port";
Acquire::https::Proxy "http://username:password@proxyserver.net:port";
Acquire::ftp::Proxy "http://username:password@proxyserver.net:port";
```

Guarda el archivo y cierra gedit

cierra la consola

Nota:

username es el nombre de usuario autorizado
password es su contraseña
proxyserver.net es la dirección ip por ejemplo 10.140.110.2
port es el puerto, por ejemplo 80

Si es sin autenticación, solo van ip y puerto sin @, por ejemplo:

```
http_proxy=http://10.140.110.2:80/
```

---

### Post by Sleeping Beauty on 2009-09-30
El ZIP de tu ciudad lo sacás de la página de weather channel. Para Capital Federal es ARBA0009. Click derecho sobre el applet seleccionas ZIP Code y lo cambiás por ese o cualquier otro. demora unos segundos en darte la lectura. Espero que sea eso, a mi me pasó y lo solucioné así

---

### Post by Leandro17 on 2009-09-30
> **Sleeping Beauty said:**
> El ZIP de tu ciudad lo sacás de la página de weather channel. Para Capital Federal es ARBA0009. Click derecho sobre el applet seleccionas ZIP Code y lo cambiás por ese o cualquier otro. demora unos segundos en darte la lectura. Espero que sea eso, a mi me pasó y lo solucioné así

por eso lo preguntaba porque antes no sabia y nunca me aparecia (bahh de mi ciudad no aparece por eso pongo el clima de posadas porque estudio alla xD)...

---

