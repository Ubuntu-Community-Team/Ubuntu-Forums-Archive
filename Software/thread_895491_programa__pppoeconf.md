---
title: "programa  pppoeconf"
date: 2008-08-20
forum: Software
---

### Post by felagund72 on 2008-08-20
Hola amigos del foro: Tengo ubuntu 8.04 hardy  y un modem Hwawei smart 810, se que tengo que configurarlo y encontre un post  que t edice como, asi que de a poco lo voy haciendo (soy muy novato y me cuesta un Perú)
 Gogleando encontre  que hay un programa que se llama "pppoeconf" que permite la conexion sin tener que configurar  para el modem. Es asi? En mi maquina tengo los dos SO y ya me quiero pasar porque XP y Bill me hartan.
Un saludo desde Santiago del Estero

---

### Post by kornykyano on 2008-08-20
Este es  un tutorial que me lo mando nouserfound (supongo que tenes ubuntu 8.04 y i386 aunque también sirve para AMD64)
En consola:

```
lsmod | grep eagle

```

deberia dar algo asi

```
ueagle_atm             34744  0 
usbatm                 20608  2 ueagle_atm
usbcore               146028  7 usb_storage,libusual,ueagle_atm,usbatm,ehci_hcd,ohci_hcd

```

Si lo que obtenemos es eagle-usb, tendríamos que actualizar el kernel o instalar el nuevo driver. Otra opción, es actualizar el sistema operativo. Pero si lo que obtenemos es ueagle-atm quiere decir que estamos en lo correcto.

Si el driver existe, la distro no viene con el firmware. Por lo tanto, habrá que bajarlo, descomprimirla y luego copiarla a la carpeta /lib/firmware/ueagle-atm. Si la carpeta no existe, habrá que crearla dentro de /lib/firmware.
El firmware se obtiene de: [http://eagle-usb.org/ueagle-atm/non-free/ueagle-data-1.1.tar.gz](http://eagle-usb.org/ueagle-atm/non-free/ueagle-data-1.1.tar.gz)
Suponiendo que lo bajamos al escritorio:
Logueo como root o uso sudo antes de cada comando.

```
cd /lib/firmware/
```

```
mkdir ueagle-atm
```

```
cd /home/USUARIO/Escritorio
```
USUARIO=Debes colocar el tuyo
```
tar -zxvf ueagle-data-1.1.tar.gz
```

```
cd ueagle-data-1.1
```

```
cp * /lib/firmware/ueagle-atm
```

Una vez que tenemos el módulo correcto y el firmware en su lugar, lo cargamos con el siguiente comando (como root o con sudo):

```
modprobe ueagle-atm
```

En la consola nos informará que el modulo ha sido cargado.

Hasta aqui tenemos el driver y el firmware listos. Ahora a configurar y conectar:

   1. Necesitamos br2684ctl. Lo descargamos de: [http://packages.ubuntu.com/hardy/i386/br2684ctl/download](http://packages.ubuntu.com/hardy/i386/br2684ctl/download)... y lo instalamos.
   2. Levantamos el módulo br2684 (como root o con sudo):

      ```
modprobe br2684
```
   3. Configuramos VPI y VC (como root o sudo):

      ```
br2684ctl -c 0 -b -a 0.33
```

      Para Arnet son 0 y 33. Por eso "0.33"
      Para Speedy son 8 y 35. Tendríamos que poner "8.35"
   4. Levantamos la interfaz de red:

      ```
ifconfig nas0 up
```
   5. Abrimos los siguientes archivos:

      ```
gedit /etc/ppp/pap-secrets
```

      ```
gedit /etc/ppp/chap-secrets
```

      y colocamos, cambiando con nuestros datos por supuesto, lo siguiente adentro:

      "usuario@proveedorinternet" * "contraseña"

      Guardamos y listo. 

Una vez realizados todos estos pasos, ahora queda hacer la conexión con el comando:

```
pppoeconf
```

Va a aparecer nas0 como interfaz de color azul, en un momento te va a pedir el "usuario@proveedorinternet" y la "contraseña" , a todo la das Aceptar.

en teoria ya deberias estar conectado. sino reinicia el sistema.

Ahora cada vez que inici sesion no deberas hacer todo esto para conectarte, entonces: Abri gedit y copia esto:

```
#!/bin/sh
#ESTE ARCHIVO INICIA LA CONEXION A ARNET!!! NO BORRAR
# CARGAR MODULOS DEL MODEM
sudo modprobe ueagle-atm
sudo modprobe br2684
#CARGAR CONFIGURACION DE ARNET
sudo br2684ctl -c 0 -b -a 0.33
#SUBIR CONEXION USB
sudo ifconfig nas0 up
#INICIAR CONEXION
sudo pon dsl-provider
```

lo guardas donde vos quieras y con el nombre que quieras, luego da click en propiedades>permiso y le tilads en ejecutar como programa, esto te permitira que cada ves que hagas click te de la opcion de ejecutar en terminal. Luego poner la contraseña y listo!!

Atencion!: Verifica que el paquete build-essential este instalado, si no esta lo podes instalar desde liveCd con Synaptic, te vas en editar>Añadir CD lo buscas y lo instalas, de lo contrario no va a funcionar.


Recuerda todo con SUDO!

Cualquier cosa me avisas

---

### Post by faktorqm on 2008-08-20
Buscaste en google pero no buscaste aca en el foro.....
en la seccion hardware, hay un post mio con un script super ultra automatico que hace todo y no necesitas tantas cosas como posteo aca kornykyano, sin desmerecerlo por supuesto.
Lo mio es un paquete que lo descomprimis, te pregunta empresa, usuario, password y listo el pollo. Salis con internet. Salu2!!

---

### Post by felagund72 on 2008-08-21
MUchas gracias !!! ahora empiezo

---

