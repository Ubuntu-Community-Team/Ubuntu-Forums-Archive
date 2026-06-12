---
title: "instalando software de gestion via red y wine en mi laburo"
date: 2010-03-20
forum: Software
---

### Post by granjero on 2010-03-20
buenas foreros!

les cuento en lo que ando....

en mi laburo logré convencer a mi jefe de probar ubuntu. trabajo en una escuela de radiodifusión. Instalamos KK para probarlo en una máquina del del estudio de televisión para disparar la parte de audio.

Ahora me dijo que si logramos hacer correr el soft de gestión de la empresa en ubuntu migramos todas las maquinas al mundo linux....

El soft se instala de la siguiente manera en win...

se crea una unidad de red **L:\** que está en el servidor con la misma letra.

eso lo hice en configurar wine > unidades: agregué unidades hasta la L:\ y le copié la dirección que me aparecía en nautilus cuando montaba la unidad L:\ del servidor con samba 

después hay que ejecutar un archivo.exe que se ejecutó sin problemas. este crea una carpeta en el árbol de wine con un único archivo.ini


pero después hay que ejecutar un script .vbs que me esta trayendo problemas....

como ejecuto los .vbs a través de wine?


desde ya muchas gracias!

---

### Post by guillermolisi on 2010-03-20
Como corren actualmente cualquier script de Visual Basic en Windows ?

---

### Post by granjero on 2010-03-20
por lo que me dijo mi jefe con doble clik!

traté de correrlo desde consola pero no logro dar con el comando correcto. el problema es que me dice que no encuentra el archivo. y la ruta que le pongo es la que leo en nautilus....

lo que voy a hacer el lunes si puedo, es instalarme un win en alguna máquina e instalar el soft a ver que info puedo recoger durante la instalación...

salud!

---

### Post by guillermolisi on 2010-03-20
> **granjero said:**
> por lo que me dijo mi jefe con doble clik!

traté de correrlo desde consola pero no logro dar con el comando correcto. el problema es que me dice que no encuentra el archivo. y la ruta que le pongo es la que leo en nautilus....

lo que voy a hacer el lunes si puedo, es instalarme un win en alguna máquina e instalar el soft a ver que info puedo recoger durante la instalación...

salud!
Bueno, mi pregunta iba para indagar mas profundamente e investigar como es la linea de comando que se ejecuta en Windows al hacer doble click sobre el acceso directo y/o archivo de script. Despues si es un solo click o dos da lo mismo, lo importante "es invisible a ciertos ojos" (cuasi parafraseando al Principito).

Tal vez haya que instalar Visual Basic en Wine, no se, o por lo menos algun runtime si aun no se hizo. Eso es lo que intento definir con la pregunta.

---

### Post by granjero on 2010-03-20
si con el script winetriks que esta disponible en la pagina de wine instalé el ultimo visual basic en wine


lo que sucede es que yo toco de oído....

pero me gusta así que voy a seguir tratando...


salud y gracias!

---

### Post by sebastianabate on 2010-03-22
Además del runtime de VB tenés que instalar el WSH (Windows Script Host) que también está listado en winetricks (wsh56). Además puede ser necesario registrar los dll a mano (**_[acá]("http://www.jsware.net/jsware/vblinux.php5")_** explican cómo poder usar scripts vbs en linux)

Pero el punto más importante es qué hace el script, porque por lo general los scripts se usan para llamar a varios programas en forma ordenada y con usa serie de parámetros predefinidos; y si vos no tenés instalados esos programas en wine (o utiliza alguna funcionalidad que todavía no está implementada en wine, como alguna API medio rara) todo esto no te va a servir de nada.

Te recomiendo primero analizar el script para tratar de entender qué es lo que hace, después instalar todo lo necesario en wine, y recién después tratar de correrlo (siempre por consola, para poder ver los errores que te tira wine)

---

### Post by granjero on 2010-03-28
gracias gente por sus respuetas.... ahora se complico todo en el laburo aunque logré que ya variaws pcs empiecen a dejar win de lado...

seguramente en unas semanas arranque con este tema de nuevo...

voy a instalar WHS para ir viendo y después les cuento...

salud!

---

### Post by granjero on 2010-07-22
he avanzado mucho en la tarea....

con un poco de ayuda se logró ejecutar el programa.

mi compañero abrió con gedit los scripts .vbs y movió todos los archivos a donde correspondían a mano.

la primera  vez que se ejecutó funcionó todo bien.

al otro día, probamos de ejecutarlo de nuevo y me tiró un error que tira en win cuando tiene problemas de permisos.

cuando me fijo los atributos de /media/ComunLABURO dice que todo pertenece a root.

les dejo la linea con la que monta el fstab


//192.168.1.1/datos/Comun\040LABURO    /media/ComunLABURO        cifs    username=pepita,password=pepita123,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0



el Comun**\040**LABURO es porque en el sever tiene espacio el nombre del directorio. Si lo ponía con el espacio en el vez de con ese 040 no lo montaba.

no me animo a mandar un chmod 777 /media/ComunLABURO

ya no se como escribir la linea esa...

gracias por su tiempo.

salud!

---

