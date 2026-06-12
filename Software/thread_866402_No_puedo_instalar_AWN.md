---
title: "No puedo instalar AWN"
date: 2008-07-21
forum: Software
---

### Post by wanchan on 2008-07-21
Hola gente, como dice el titulo segui un tuto para instalar AWN, por si alguien lo quiere ver el link es:
[http://obux.wordpress.com/2007/11/25/como-instalar-avant-window-navigator-awn-ubuntu/]("http://obux.wordpress.com/2007/11/25/como-instalar-avant-window-navigator-awn-ubuntu/")

Llegue hasta el paso dos, ejecute el comando siguiente:
sudo apt-get install awn-manager-trunk awn-extras-applets-trunk

y me aparecio esto:

> Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  awn-extras-applets-trunk: Depende: libawn0-trunk (>= 0.3.0) pero no va a instalarse
                            Depende: libpango1.0-0 (>= 1.20.5) pero 1.20.1-1 va a ser instalado
  awn-manager-trunk: Depende: avant-window-navigator-trunk (>= 0.2) pero no va a instalarse
                     Depende: python-awn-trunk pero no va a instalarse
                     Depende: python-central (>= 0.6.7) pero 0.6.5ubuntu1 va a ser instalado
E: Paquetes rotos


Me parece que tengo que tener los archivos libawn0-trunk pero de version 0.3.0 en adelante, igual para los otros. Me fije por Synaptic y algunos no estan instalados y otros si pero con version anteriores de las que me dice el mensaje. Como puedo consegirlos, porque creo que con Synaptic no se consiguen.

---

### Post by luks911 on 2008-07-22
Probá de instalarlo con Synaptic, las dependencias debería marcarlas solo y están incluidas en los repositorios que agregaste.

---

### Post by wanchan on 2008-07-22
Probé instalarlo desde synaptic pero no lo instala por las dependencias. Me sale casi el mismo mensaje y no lo instala.

---

### Post by luks911 on 2008-07-22
Mmmm... primero fijate que no tengas instalado el AWN que viene en los repositorios de Ubuntu. Tiene el mismo nombre pero sin el "trunk". Si está, desinstalalo por completo. Después ejecutá 

```
sudo aptitude install avant-window-navigator-trunk  awn-manager-trunk awn-extras-applets-trunk

```

Es básicamente lo mismo que desde Synaptics. Pero para aseguarte. 

Por las versiones que está tirando la consola te debe estar pasando lo primero y las versiones son incompatibles. Y cuando ejecutaste "sudo apt-get install awn-manager-trunk awn-extras-applets-trunk" estás pidiendo que instale el manager y los applets, pero no el AWN.

---

### Post by wanchan on 2008-07-22
> **luks911 said:**
> Mmmm... primero fijate que no tengas instalado el AWN que viene en los repositorios de Ubuntu. Tiene el mismo nombre pero sin el "trunk". Si está, desinstalalo por completo. Después ejecutá 

```
sudo aptitude install avant-window-navigator-trunk  awn-manager-trunk awn-extras-applets-trunk

```

Es básicamente lo mismo que desde Synaptics. Pero para aseguarte. 

Por las versiones que está tirando la consola te debe estar pasando lo primero y las versiones son incompatibles. Y cuando ejecutaste "sudo apt-get install awn-manager-trunk awn-extras-applets-trunk" estás pidiendo que instale el manager y los applets, pero no el AWN.

Ejecute el comando que me dijiste, no se instalo y me tira esto:

> E: No se pudo bloquear /var/lib/dpkg/lock - open (11 Recurso temporalmente no disponible)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
E: No se pudo bloquear /var/lib/dpkg/lock - open (11 Recurso temporalmente no disponible)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


El AWN no lo tengo instalado, lo que tengo instalado es 
libpango1.0-0  Como ultima version instalada: 1.20.1-1

Y cuando quiero instalar avant-window-navigator-trunk desde Synaptic me salta esto:

> avant-window-navigator-trunk:
 Depende: avant-window-navigator-data-trunk pero no va a ser instalado
 Depende: libawn0-trunk pero no va a ser instalado

Cuando quiero instalar libawn0-trunk me sale esto:

> libawn0-trunk:
  Depende: libpango1.0-0 (>=1.20.5) pero se va a instalar 1.20.1-1

O sea, que me faltaria libpango1.0-0 version 1.20.5 o mas. Pero ese paquete no esta en los repositorios.

---

### Post by luks911 on 2008-07-22
El primer error te lo devuelve porque seguro al ejecutar el comando también tenías abierto el Synaptic. Para instalar por consola tiene que estar cerrado.

En cuanto a lo segundo, el libpango1.0-0 viene en Hardy en su versión 1.20.1-1, que es la que tenés instalada. Pero la 1.20.5-0, que es la que necesitás, está en el repositorio hardy-updates, por lo que supongo que lo debés tener deshabilitado. Para habilitarlo, en Synaptic vas al menú Configuración > Repositorios, ahí a la pestaña Actualizaciones y marcás la casilla "Actualizaciones recomendadas (hardy-updates)". Después de eso cerras ese diálogo y le das al botón recargar. 

Luego, probá de instalar desde Synaptic o terminal, pero uno por vez. A ver si es eso.

Saludos

---

### Post by wanchan on 2008-07-23
Era que no tenia habilitado las actualizaciones recomendadas. Ahora si se instalo AWN =D>
Muchas gracias por la ayuda, ahora voy a poder toquetear un poco.

---

### Post by luks911 on 2008-07-23
De nada, me alegro :grin:
un saludo

---

