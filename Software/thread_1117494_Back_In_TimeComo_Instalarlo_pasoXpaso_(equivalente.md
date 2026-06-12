---
title: "Back In Time:Como Instalarlo pasoXpaso (equivalente a Time Machine en Ubuntu)"
date: 2009-04-06
forum: Software
---

### Post by juancarlospaco on 2009-04-06
[CENTER]**[SIZE="6"][COLOR="Sienna"]Back In Time: Como Instalarlo paso X paso [/COLOR][/SIZE]**
*(equivalente a Time Machine en Ubuntu)*[/CENTER]

[IMG]http://www.clydecaldwell.com/jpgs/photos/sandiego01/time_machine2.jpg[/IMG]


***[SIZE="3"][COLOR="Sienna"]Que es Back In Time?[/COLOR][/SIZE]***
Back In Time es un programa de backup por Snapshots Inteligentes para uso en Desktop,
con funcion similar al Time Machine de OS X Leopard*+*
permite tener copia de seguridad de tus datos importantes de manera sencilla y eficiente.


***[SIZE="3"][COLOR="Sienna"]Como funciona?[/COLOR][/SIZE]***
[B]El programa toma Snapshots automaticas incrementales, inteligentes y silenciosas, del estado actual de una locacion definida, 
respaldando tus imagenes, musica, películas, documentos o cualquier cosa que le asignes respaldar.[/B]

Por el lado tecnico hace uso del avanzado FileSystem EXT3 / EXT4 y de la Herramienta Unix de bajo nivel RSync,
combinado con un sistema de Gestion de Snapshots muy bien logrado.

Cualquier medio de almacenamiento que se pueda leer/escribir directamente sirve para guardar los Snapshots,
**no importa el FileSystem del medio de almacenamiento de Snapshots o si es Extraible o no lo es.**

De manera tal que los Snapshots no ocupan mucho espacio en el disco, 
sumado a que** una Snapshot solo hace backup de los datos que han cambiado**, mateniendo permisos y estado de los datos.


***[SIZE="3"][COLOR="Sienna"]Se me va a llenar el Disco?[/COLOR][/SIZE]***
No, con Back In Time nunca se quedara sin espacio el Disco,
tiene un sistema de Eliminacion Inteligente de Snapshots:
[B]mantiene todas las Snapshot de hoy y ayer,
mantiene como minimo una Snapshot de la ultima semana y otra para hace dos semanas,
mantiene como minimo una Snapshot por mes para todos los meses previos de este mismo año,
mantiene como minimo una Snapshot por año para todos los años previos a este mismo año.[/B]

Asi mismo permite configuraciones manuales como eliminar si en el medio de almacenamiento queda menos de determinada cantidad de espacio,
o si son mas antiguas que determinada fecha, 
tambien la opcion de no eliminar nunca una Snapshot re/nombrada manualmente por el usuario.

Puede configurarse para guardar configuraciones personales del sistema, ademas de datos, 
haciendo posible restaurar configuraciones del pasado, o usarlos en otros equipos con Ubuntu.

Tambien permite Excluir archivos y carpetas por Patrones personalizables, por ejemplo excluir :
[LIST]
[*]*.exe
[*]Musica/
[*]backup.*
[/LIST]


***[SIZE="3"][COLOR="Sienna"]Cuando hay que usarlo?[/COLOR][/SIZE]***
Luego de configurado, no hay que prestarle atencion, 
no requiere intervencion del usuario, los Snapshots son Desatendidos y Automaticos, 
ademas de correr en Background en Baja Prioridad, cediendo recursos si otra aplicacion los requiere,
[B]Back In Time realiza Snapshots de los datos cada:
Nunca, 5 minutos, 10 minutos, 1 hora, 1 dia, 1 semana, 1 mes.
[/B]

***[SIZE="3"][COLOR="Sienna"]Tengo que apagar/reiniciar y estoy usando Back In Time para hacer una Snapshot que pasa?[/COLOR][/SIZE]***

**El programa detiene el proceso de copiado y recuerda dónde se encuentra**, 
para retomarlo cuando sea abierto o cuando sea tiempo de una Snapshot segun las configuraciones,
sincroniza lo ya copiado, distinguiendo que sirve y que debe copiar de nuevo.


***[SIZE="3"][COLOR="Sienna"]Quiero restaurar algo, como hago?[/COLOR][/SIZE]***
**Entra en el navegador de archivos de Back In Time*** (muy similar al Nautilus)*, 
**elije en que etapa del pasado** buscar los archivos que necesitas *(en la Columna "Instantaneas")*,
y simplemente usa los botones grandes de la barra *(o el menu del click derecho)*
para Copiar al portapapeles, Restaurar al presente, o Abrir directamente tu archivo, 
tambien puedes simplemente **hacer Drag&Drop desde el pasado al presente. ** 
Back In Time puede restaurar archivos, carpetas y configuraciones. 


**[SIZE="3"]Back In Time en accion, realizando una Instantanea :[/SIZE]**

[IMG]http://img214.imageshack.us/img214/7963/actionback.gif[/IMG]





**[SIZE="3"]Proceso de Instalacion :[/SIZE]**

Descargar estos dos paquetes :

[LIST=1]
[*][B][http://backintime.le-web.org/download/backintime/backintime-common-0.9.18_all.deb](http://backintime.le-web.org/download/backintime/backintime-common-0.9.18_all.deb)

[*][http://backintime.le-web.org/download/backintime/backintime-gnome-0.9.18_all.deb](http://backintime.le-web.org/download/backintime/backintime-gnome-0.9.18_all.deb)[/B]
[/LIST]

Si estas leyendo esto mucho despues del Marzo de 2009, fijate si no hay versiones nuevas aqui, 
las versiones mas nuevas son las de numero mas alto en el nombre del paquete :

[LIST]
[*][Index of /download/backintime](http://backintime.le-web.org/download/backintime/)
[/LIST]


Abrir una Terminal en la carpeta donde estan los dos archivos descargados, copiar, pegar en la terminal y darle ENTER :

[CENTER][CENTER]**[SIZE="4"]sudo dpkg -i *.deb[/SIZE]**[/CENTER][/CENTER]


**[SIZE="3"]Proceso de Instalacion en un GIF :[/SIZE]**

[IMG]http://img15.imageshack.us/img15/1292/instalacionback3.gif[/IMG]


Listo, esta instalado, lo podes encontrar en :
**Aplicaciones ---> Herramientas del Sistema ---> Back In Time**


**[SIZE="3"]Configurando las Preferencias la primera vez :[/SIZE]**

[IMG]http://img141.imageshack.us/img141/7387/preferencias.gif[/IMG]

**[SIZE="4"]IMPORTANTE : [/SIZE]***Tener en cuenta...*

[LIST]
[*]Tenes que tener permiso de lectura/escritura en la carpeta que vallas a usar para las Instantaneas o snapshots.
[*]La carpeta de Instantaneas NO puede estar dentro de las carpetas a respaldar por las Instantaneas, pero puedes ponerla como "Excluir".
[/LIST]


**[SIZE="3"]Podes crear un icono en el Panel para ejecutar el programa:[/SIZE]**

[IMG]http://img403.imageshack.us/img403/8282/iconeyq.jpg[/IMG]

Con el pasar de los meses veras que se van formando solas las nuevas instantaneas,
permitiendote viajar aun mas hacia atras en el tiempo por si necesitas algun archivo que ya no esta.



:p

---

### Post by faktorqm on 2009-04-07
Hola, no hay version en consola? comparativa con bacula? que pasa si tengo 4 snapshots y pierdo la original? es libre? 
Mucha fotito poco tecnicismo....

---

### Post by juancarlospaco on 2009-04-07
[B]backintime-common ---> version de consola
backintime-gnome ---> version gnome (front-end)
backintime-kde ---> version kde (front-end)[/B]

No hay comparativa con Bacula, 
sencillamente por que es otra cosa, no comparar Apples con System76's ;P
[B]Bacula ---> Servers
Back In Time ---> Desktops[/B]

Restauras desde las Snapshots, para tener mas idea de como es, entrar aca:
[http://www.apple.com/es/macosx/features/timemachine.html]("http://www.apple.com/es/macosx/features/timemachine.html")
es un muy buen reemplazo de eso, pero Libre, permite mas flexibilidad que ese, 
sin incluir las boludeces de animaciones, dejemono de joder tamos grandes para eso.

El programa es GPL, o sea es bastante Libre.

Se basa en el filesystem EXT3/4, Rsync, Diff, Meld, si queres tecnicismos lee acerca de esos programas.

---

### Post by guisheca on 2009-04-07
Excelente tutorial juancarlospaco!!!!!!!!! lo voy a tener en cuenta!!!!
Muchas gracias por el esfuerzo.
Un saludo.

---

### Post by faktorqm on 2009-04-07
ok esta todo dicho. Lo unico que te voy a corregir en algo, bacula es para servers y desktops. Gracias por el aporte, parece que a algunos les sirvio. Saludos!

---

### Post by sinozzuke on 2009-06-20
Wolas:
Y cómo se hace para poner el icono en el tray? No soy capaz! :) Si lo ejecuto, sólamente si doy a copia de respaldo me aparece el iconito en el panel superior. Pero si cierro el programa, no hay icono! No se si está ejecutandose o no, la verdad...

---

### Post by juancarlospaco on 2009-06-20
*mmm...* yo lo que hice fue agarrar el icono del escritorio y 
lo arrastre hasta donde queria que quede, ...y ahi quedo  :)

---

### Post by sinozzuke on 2009-06-22
> **juancarlospaco said:**
> *mmm...* yo lo que hice fue agarrar el icono del escritorio y 
lo arrastre hasta donde queria que quede, ...y ahi quedo  :)

:)

Gracias, pero no me refería al acceso directo del programa en la barra superior, sino al icono del tray, que está el programa en ejecución. Me da la sensación de que no está ejecutandose como proceso de fondo, si cierro el programa se cierra completamente, no como el amarok q se queda ahí funcionando o el emesene o cualquier otro... No se si me explico.

---

### Post by juancarlospaco on 2009-06-22
> **sinozzuke said:**
> :)

Gracias, pero no me refería al acceso directo del programa en la barra superior, sino al icono del tray, que está el programa en ejecución. Me da la sensación de que no está ejecutandose como proceso de fondo, si cierro el programa se cierra completamente, no como el amarok q se queda ahí funcionando o el emesene o cualquier otro... No se si me explico.

*Es que...*
no está ejecutandose como proceso de fondo,
de eso se encarga don **Cron**. :)

---

### Post by harlock74 on 2009-07-10
A ver si alguien me puede ayudar. Ya lo tengo instalado, y configurado, pero.... cuando le hago backup, no guarda nada.  Selecciono el snapshot que crea, y me dice:  This Folder doesn't exist in snapshot.  Que estoy haciendo mal? Veo que si hace los folders del backup, pero ya dentro de donde deberian de estar mis archivos, etc...no hay nada.  Esta vacio.  ayuda por favor :(

---

### Post by juancarlospaco on 2009-07-10
La palabra clave es **Permisos de Archivos y Carpetas.**

*a mi me paso lo mismo *:)

---

### Post by harlock74 on 2009-07-10
Si me supuse que era algo con eso, pero estoy revisando y por ejemplo:

1. Creo un folder "backup" en mi home (aparece con permisos para escribir mi user)
2. Le digo a backintime que lo utilize como target.
3. Selecciono a resguardar un folder que existe en mi home y que lo cambie a chmod 777 para aseguarme (ademas yo soy el dueño y esta en mi grupo)

Resultado:  El mismo mensajito del que escribí anteriormente....

En que estoy fallando, no entiendo. :(

Gracias por la ayuda.

---

### Post by juancarlospaco on 2009-07-11
folder de snapshot no debe estar en la folder de backup,
yo uso una carpeta en /var/backup/backintime/
que soy el dueño y tiene chmod 777

---

