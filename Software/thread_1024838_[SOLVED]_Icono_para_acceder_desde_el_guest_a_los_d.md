---
title: "[SOLVED] Icono para acceder desde el guest a los directorios del host"
date: 2008-12-29
forum: Software
---

### Post by mecdem on 2008-12-29
Soy usuaria no informática.
__________________

Mi sistema es Kubuntu 8.04 (host)
Tengo instalado como guest WinXP virtual.
Soft de virtualizaciòn: Sun xVM VirtualBox.
__________________

En el escritorio del guest tenìa un ícono que me permitía acceder al directorio home/minombredeusuario en Kubuntu.

Ese icono fue borrado accidentalmente.

Para recuperalo estoy haciendo esto:

Abro el virtualBox.
elijo la maquina virtual.
Configuración > Directorios Compartidos > add news shared folders.
Elijo el directorio a compartir (home/minombredeusuario).
Acepto.

Se crea un ìcono, pero no aparece en el escritorio de Win virtual, lo que me hace sospechar que hay una parte del procedimiento a realizar en Win del que no sé o no puedo recordar los pasos a seguir.

Este es el punto de mi consulta:
¿Cómo hago para que el ìcono se vea en el escritorio del guest WinXP?
__________________

Tratè de encontrar alguna ayuda vía Google/Linux sin éxito.
Si ya hay algo vinculado al tema en este foro, favor disculpar la reiteraciòn de la consulta, pero he cliqueado en "check if already posted" tambièn sin éxito, y no sé si hay otra forma de bùsqueda. Si hubiera ya alguna soluciòn para mi consulta en otro post, por favor indicarme el enlace y yo leeré lo que allí se haya dicho
__________________

Muchas gracias por la ayuda.
Saludos.

---

### Post by sebastianabate on 2008-12-29
Todo depende de cómo hayas configurado las "Shared Folders" de tu VM. Si por ejemplo creaste una carpeta compartida apuntado a tu home (/home/tu_nombre_de_usuario) y la nombraste como "tu_nombre_de_usuario", lo que tenés que hacer para recuperar el acceso directo es:

1) click derecho en una parte vacía del escritorio de tu XP Guest.
2) click a "Nuevo"->"acceso directo"
3) en donde dice "Escriba la ubicación del elemento" ponés "\\vboxsvr\[U]tu_nombre_de_usuario"  y le das click al botón "siguiente"
4) donde dice "Escriba un nombre para este acceso directo" ponés lo que quieras (que identifique a la carpeta compartida, como por ejemplo "Mi Home en Ubuntu")
5) click en finalizar, y listo, ya tenés tu acceso directo recreado

PD: Todo lo que está entre comillas lo tenés que tipear sin las comillas.
[/U]

---

### Post by mecdem on 2008-12-29
> **sebastianabate said:**
> Todo depende de cómo hayas configurado las "Shared Folders" de tu VM....
______________________________

Sebastián, muchísimas gracias.

Recojo tus instrucciones ahora, aunque no podré poner manos a la obra hasta mañana.

Una vez que lo haya hecho, vuelvo para contarte cómo me fue.

Cordial saludo.

---

### Post by sebastianabate on 2008-12-29
Perdón, no te aclaré lo esencial, las "Shared Folders" de VirtualBox son una forma de acceder a carpetas del Host sin necesidad de tener configurada la red del Guest; esto quiere decir que, aunque el Guest (el XP en tu caso" no pueda pinguear al Host (Ubuntu en tu caso) igual puede acceder a una carpeta compartida por CIFS (el sistema por el que windows comparte las carpetas en la red).

Pero esto lo podés evitar configurando la interfaz de red del guest en modo "host interface", de esta forma el Guest interactúa con el Host y con las otras máquinas que estén en red en tu ambiente de forma directa (como si fuera una máquina real conectada por cable a las demás); y con esta configuración podés no solo acceder a una carpeta compartida, además podés acceder a todos los servicios que tengas corriendo en tu Host, como por ejemplo un servidor web (Apache o THTTPD), un servidor SSH (OpenSSH), una base de datos (PostgreSQL o MySQL), una carpeta compartida real (SAMBA o NFS), etc.

Esto es muy fácil con la última versión de VirtualBox (2.1.0); lo único que tenés que hacer es seleccionar "Host Interfaz" en el apartado "Attached to" de la configuración de red del  Guest; y debajo en la sección "Host Interfaces" elegir el dispositivo de tu placa de red real, por lo general "eth0"; luego en el Guest XP configurás la placa de red con una dirección IP del mismo rango que la de tu Host, y listo, ya tenés la red entre las dos máquinas funcionando sin problemas.

Espero que esto haya sido más clarificador que "enquilombador". Cualquier cosa preguntá lo no hayas entendido.

---

### Post by mecdem on 2009-01-06
Hola Sebastián.

Tardé en volver por aquí porque con tanto feriado no había podido poner en práctica tu instructivo. Lo hice y anduvo PER-FEC-TO. Muchísimas gracias.
   ):P

NOTA: Tu primera respuesta la entendí lo más bien. La segunda... ¡me asustó!! ¡Menos mal que no ví hasta recién! Si no, me hubiese quedado paralizada en estado de pánico... Ojo con usuarios no informáticos como yo, que un poquito más de lo que nos da la e-mollera (que no es mucho) ...y morimos de sobredosis.
:lolflag:

Bueno, igual copio y guardo tus indicaciones. Todavía no las entiendo, pero en algún momento voy a lograr entenderlas y ponerlas en práctica.

Te estoy muy agradecida por tu ayuda.
Cordial saludo.

---

