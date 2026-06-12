---
title: "Crear dos Particiones para Win y Linux"
date: 2009-05-03
forum: Software
---

### Post by &quot;DanieLinux&quot; on 2009-05-03
[SIZE=3]hola Antes de hacer particiones necesitaria que me respondieran una pregunta.

Mi disco es de 20Gbs , primero Instalaria Windows Xp con 11Gbs y luego instalaria en el resto 8gbs a Ubuntu. obviamente al iniciarse la PC directamente iniciaria Xp por que esta instalado en "C", (Y asi me gustaria) ¿pero como hago para iniciar ubuntu y no XP? 

QUien tenga a los dos S.O en un solo Disco me puede decir como se hace gracias...
[/SIZE]

---

### Post by staar on 2009-05-03
lo que tendrías que hacer es:

-crear la partición para windos, en instalarlo, dejando el espacio destinado a ubuntu sin particionar...

-instalar ubuntu, y en el paso de las particiones, seleccionar 'usar el espacio libre' (o algo así :-P) para que el instalador te cree solito las particiones donde se instalará ubuntu (por defecto, son dos, una para el sistema de archivos y otra para swap o intercambio)...

-para cargar sistemas operativos, se necesita un cargador de arranque o bootloader (que se instala al instalar (!) el SO), windos tiene el suyo, que no lo ves, pero que está ahí, y ubuntu usa uno que se llama GRUB, que es capaz de iniciar muchos SOs, incluido windos...
el mismo instalador de ubuntu, va a detectar que windos está instalado, y al instalar GRUB, lo va a agregar a su lista...
después, al prender la pc, te va a aparecer un menú para seleccionar que sistema querés iniciar...

saludos

EDIT: OJO, al instalarse ubuntu, la opción que queda por defecto para iniciar automáticamente es ubuntu, eso después se puede modificar, que windos este instalado en el C: no significa nada, ese es el nombre que ese sistema le da a la partición del disco (que es capaz de reconocer, a las particiones de ubuntu ni te las va a mostrar al no ser capaz de leerlas), ubuntu la llamará de otra forma, tipo /dev/sda1 o similar (en ubuntu si vas a poder usar tus datos de win ;-) )

EDIT2: el foro de ubuntu-ar está subdividido en tres subforos, Hardware, Software y Comunidad, por favor la proxima vez postea en la categoría correspondiente, en este caso sería Software, para mantener el orden y ahorrarle trabajo a los mods ;-)...

---

