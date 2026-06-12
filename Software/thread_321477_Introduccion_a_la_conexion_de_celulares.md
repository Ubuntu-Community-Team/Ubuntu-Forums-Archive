---
title: "Introduccion a la conexion de celulares"
date: 2006-12-19
forum: Software
---

### Post by DuckMan on 2006-12-19
Bueno, visto q he logrado poder bajar y subir fotos, musica, etc a mi celular (motorola c235), hago una mini guia con datos utiles, quizas!

Para conectarme use el moto4lin, se baja de synaptic, existe uno llamado kmobiletools o algo asi, q sirvio tmb, pero con ese ves la agenda, los sms, mandas sms, etc; lo recomiendo tmb.

Enchufen el celular por USB, y habran el moto4lin, indispensable el sudo:

```
sudo moto4lin
```Uno de los problemas fue saber donde aparecia el celular dentro de /dev/ , el mio esta en /dev/ttyACM0 , no se si es algo personal o de ubuntu. Por eso en la config de moto4lin, en Connection >> ACM Device , mandan "/dev/ttyACM0" o lo q les toq. Si no saben cual es, mandan este comando por consola:

```
dmesg
```Y buscan algo como esto:

```
[17219779.908000] cdc_acm 2-3:1.0: **ttyACM0**: USB ACM device

```Ahi se vera q esta conectado el celular, y q esta montado en ttyACM0, si es otro, usen ese.

Se supone q debe estar todo bien, pueden conectarse y ver en una lista de directorios un poco rustica pero completa, donde podran bajar y subir todo tipo de informacion al celular, si no se conecta, deberian jugar con las opciones q da el programa.


[list][size=4]Para usuarios Ubuntu Dapper 6.06 LTS[/size] (gracias **lavaramano**):[/list]

[http://ubuntuforums.org/showpost.php?p=2036161&postcount=4](http://ubuntuforums.org/showpost.php?p=2036161&postcount=4)



No tengo muchas precisiones sobre el tema, por eso agradeceria cualquier comentario de algun sabiondo y yo edito agregando la informacion.

---

### Post by beuno on 2007-01-18
Muy bueno.

---

### Post by BlackHero on 2007-01-19
si la verdad muy bien aporte argentino :)

---

### Post by lavaramano on 2007-01-19
el programita ese se la banca bastante, es el que uso.
o sea, el p2ktools era un quilombo para hacerlo funcionar con win, pero este. es instalarlo y sale corriendo.

si usan dapper (como yo)
hay que agregar esto al sources.list:
```

deb http://ubuntu.geole.info/ dapper universe multiverse

```

y la apt-key:
```

wget http://www.geole.info/fileadmin/data/misc/geole.info-apt-key.gpg
sudo apt-key add geole.info-apt-key.gpg

```

eso es segun la pagina para "sistemas debian" [http://moto4lin.sourceforge.net/wiki/Debian_Packages](http://moto4lin.sourceforge.net/wiki/Debian_Packages)

ah, por cierto.

[http://www.gnokii.org/](http://www.gnokii.org/) en esta pagina hay un programita similar, pero para telefonos Nokia.

salutes

---

### Post by matog on 2007-01-21
Alguien tiene idea como conectar el maldito Sony Ericsson K300???

Gracias!

---

### Post by godzeus on 2007-01-21
> **matog said:**
> Alguien tiene idea como conectar el maldito Sony Ericsson K300???

Gracias!

yo tengo un SE W800i, y no tengo problemas, lo conecto por usb, y Ubuntu(6.10) me lo detecta como disco removible y le puedo cargar lo que quiera.:cool:

---

### Post by matog on 2007-01-21
Claro, ese anda bien. Este es un modelo un poquito mas viejo. Y no hay caso....

---

### Post by godzeus on 2007-01-22
> **matog said:**
> Claro, ese anda bien. Este es un modelo un poquito mas viejo. Y no hay caso....

comenta un poco cual es el problema, no te lo detecta?8-)

---

### Post by jajajavi on 2007-01-25
Anda todo bien pero me lo detecta como **New audio playback device**, es un v300 cagado a palos. Es raro, aunque aun no generó ningún conflicto...

---

### Post by atari130xe on 2007-01-26
No instalé el moto4lin pero lo probaré con mi Sony Ericsson Z520a si alguno tiene una idea del como, posteenlo asi lo compartimos :D

---

### Post by matog on 2007-01-27
> **godzeus said:**
> comenta un poco cual es el problema, no te lo detecta?8-)

Lo conecto via Usb (en Win XP funciona), pero Ubuntu no se da ni por enterado...(aclaro que el ubuntu me detectó todo lo que conecte via usb como reproductores de mp3, pendrives, camaras de fotos, etc.)

Seguramente tendré que meter un poco de mano en algún lugar, pero no soy un experto, y no tengo idea que tocar....

---

### Post by kha0s101 on 2007-09-29
[COLOR="Green"]Hola. 

Revivo el thread porque al instalar el moto4lin me reconoce correctamente mi tel como Motorola L6i al hacer update list muestra: 

**22b8 4902 motorola Inc. Motorola Phone (L6i)**

pero luego no puedo hacer el paso Switch to P2k mode, así que de momento sigo dándole a la windola para administrarlo :mad:

ACM Device: /dev/usb/acm/0
AT Vendor ID:  22b8
AT Product ID: 4902
P2K Vendor ID:  22b8
P2K Product ID: 4902

Reconoce el tel como AT pero al hacer el switch dice:
"unable to open device"
"please check preferences"

Pero sé que el tel lo reconoce bien 

Alguna sugerencia para solucionar este problema?

Gracias a todos.
Saludos.
[/COLOR]

---

### Post by santiagoward2000 on 2007-09-30
> **kha0s101 said:**
> [COLOR="Green"]Hola. 

Revivo el thread porque al instalar el moto4lin me reconoce correctamente mi tel como Motorola L6i al hacer update list muestra: 

**22b8 4902 motorola Inc. Motorola Phone (L6i)**

pero luego no puedo hacer el paso Switch to P2k mode, así que de momento sigo dándole a la windola para administrarlo :mad:

ACM Device: /dev/usb/acm/0
AT Vendor ID:  22b8
AT Product ID: 4902
P2K Vendor ID:  22b8
P2K Product ID: 4902

Reconoce el tel como AT pero al hacer el switch dice:
"unable to open device"
"please check preferences"

Pero sé que el tel lo reconoce bien 

Alguna sugerencia para solucionar este problema?

Gracias a todos.
Saludos.
[/COLOR]

Hola kha0s101,
Creo que tu problema está en el ACM device. Tratá cambiarlo por: "/dev/ttyACM0"
Espero que te sirva!

---

### Post by juanman on 2007-09-30
> **santiagoward2000 said:**
> Hola kha0s101,
Creo que tu problema está en el ACM device. Tratá cambiarlo por: "/dev/ttyACM0"
Espero que te sirva!
Y ademas tienes q cambiar el p2k product id a 4901

Aca tenes [mas info del L6 con moto4lin]("http://moto4lin.sourceforge.net/wiki/L6")

Para otros modelos soportados y su configuracion pueden ver en el wiki de moto4lin ([aca]("http://moto4lin.sourceforge.net/wiki/Category:Models"))

Yo tengo funcionando un motorola c650 con el moto4lin y funciona, aunq a veces se cuelga el programa. No es muy estable, lastima q parece q no se sigue su desarrollo...
El kmobiletools si funciona de 10 y se sigue desarrollando

---

### Post by kha0s101 on 2007-10-02
[COLOR="Green"]Gracias juanman y santiagoward2000 por responder. Voy a seguir abusando de sus conocimientos!

Les cuento mi experiencia:

En Moto4lin seteo 
ACM Driver:  /dev/ttyACM0
P2K PRODUCT ID: 4901 (que aparece por defalut como 4902)
Click en *Update List* y mi motorola aparece como 
22b8 490**2**

Al hacer click en *Switch to P2K*  la ventana de estado me informa que intenta hacer el cambio a P2K mode[/COLOR]
[COLOR="Blue"]AT E0 answer: AT E0 OK
Phone Answer: Ok
Phone is unpluged[/COLOR]


[COLOR="Green"]Hago entonces Update List nuevamente y ahora muestra mi motorola como 22b8 490**1**

Cierro y vuelvo a iniciar. La ventana de estado informa[/COLOR] 
[COLOR="Blue"]Phone pluged as P2K
Phone is unpluged[/COLOR]

[COLOR="Green"]Si intento conectar da error:[/COLOR]
[COLOR="Black"]Try to conect[/COLOR]
[COLOR="Red"][error] No phone found. Check Preferences for AT Vendor/Product ID
[error] Unable to connect[/COLOR]

[COLOR="Green"]Voy a Preferences y está todo como si nunca hubiese cambiado nada. Hago los cambios que me indicaron (/dev/tty - 4901) y cuando hago click en *Update List* o* Switch to P2K*, aparece de el mensajde error:[/COLOR]
[COLOR="Red"][error]Unable to open device
[error]Please check Preferences[/COLOR]

[COLOR="Green"]He cambiado de puertos usb y la mecánica es la misma. Cualquier ayuda será muy muy bienvenida :)

Muchas gracias. Salud0s,
Kha0s101.

[/COLOR]

---

### Post by santiagoward2000 on 2007-10-02
Hola kha0s,
Te cuento que yo tambien tuve ese problema un par de veces. Lo que hago para que reconozca mi c650 es tocar "Reboot" y esperar que el cel se prenda de nuevo. Una vez que se prendio anda lo mas bien.

> **kha0s101 said:**
> [COLOR="Green"]Gracias juanman y santiagoward2000 por responder. Voy a seguir abusando de sus conocimientos!
[/COLOR]
No se si es el caso de juanmar, pero yo estoy recien empezando con Linux, ayudo en lo que puedo, pero no soy ningun experto...

---

### Post by kha0s101 on 2007-10-02
[COLOR="Green"]Pues, santiago, con más razón mi agradecimiento. Yo también soy nuevo con Ubuntu y con Linux en general, aunque siempre "le tuve ganas".

Lamentablemente, solo puedo estar de modo esporádico con Ubuntu pero cada día me gusta más y espero poder pasarme del todo antes de fin de año y dejar atrás las ventanitas...

Estuve tocando un poco, siguiendo tu consejo. Finalmente moto4lin guardó la configuración del teléfono. Al iniciar muestra:[/COLOR]
[COLOR="Blue"][info] Phone pluged as P2K
[info] Phone is unpluged
[/COLOR]
[COLOR="Green"]Luego de eso, no puedo hacer nada con el programa, es decir, no puede conectar con el teléfono (no reinicia ni conecta o muestra las seems... :confused:

Seguiré intentando. Lo que me llama la atención es que al ir a Preferences no muestra (mantiene) la config aunque supongo que la guarda en alguna parte porque inicia con el puerto como P2K, aunque luego se desconecte.

Como siempre, cualquier sugerencia es bienvenida. Muchas gracias por la ayuda.

Salud0s,
Kha0s.
[/COLOR]

---

### Post by santiagoward2000 on 2007-10-02
> **kha0s101 said:**
> [COLOR="Green"]Les cuento mi experiencia:

En Moto4lin seteo 
ACM Driver:  /dev/ttyACM0
P2K PRODUCT ID: 4901 (que aparece por defalut como 4902)
Click en *Update List* y mi motorola aparece como 
22b8 490**2**[/COLOR]

Estuve revisando mi configuración, yo yo no tuve que cambiar el P2K PRODUCT ID, lo dejé como 4902. ¿Por qué no probás así y depués nos decís qué pasa?

---

### Post by kha0s101 on 2007-10-05
[COLOR="Green"]Hmmm, creo que probé y no funcionó pero no recuerdo con  total seguridad. Así que pruebo y aviso.

Muchas gracias.

Slaud0s.[/COLOR]

---

### Post by basfo on 2007-10-18
Yo tengo exactamente el mismo problema que kha0s101, es decir, seteo el ACM en /dev/ttyACM0,  el p2kvendor 22b8 y el p2kproductid en 4901, sin embargo cuando pongo switch to pk2 me sale esto

[info] Switching device /dev/ttyACM0 to P2K mode...
[info] AT E0 answer: AT E0 OK 
[info] Phone answer: OK 
[info] Phone is unpluged

despues le doy a connect y dice:

[error] No phone found. Check preferences for AT Vendor/Product ID
[error] Unable to connect

Lo loco es que el dispositivo /dev/ttyACM0 desaparece una vez apretado el switch to p2k. deja de listarse en un ls. Si tiro un lsusb, antes de apretarBus 
 "switch..." da esto

Bus 002 Device 038: ID 22b8:4902 Motorola PCS E398 GSM Phone

y despues de apretarlo da.

002 Device 037: ID 22b8:4901 Motorola PCS 

El comando p2ktest falla tambien

Switching to P2K...
P2k Phone found

(E_p2k_openPhone.-1: no p2k phone)
(E_p2k_sendControl.-6: no connection)
(E_p2k_getPhoneName.-14: E001)
Can not get phone model
(E_p2k_sendControl.-6: no connection)
(E_p2k_getDriveName.-14: E001)
Can not get drive name
(E_p2k_sendControl.-6: no connection)
(E_p2k_freeSpace.-14: E001)
Can not get free space(E_p2k_sendControl.-6: no connection)
(E_p2k_fileCount.-14: E001)
Can not get file count(E_p2k_sendControl.-6: no connection)
(E_p2k_fileCount.-14: E001)
(E_p2k_fileList.-14: E000)

sin embargo, si lo hago luego de switch to pk2 da el listado de archivos del celular

P2k Phone found

Phone Model: V360
Drive: /a&#65533;/c
Free space: 1355861 bytes
File count: 283 bytes
   1    300  40   4 /a/ALARMCLOCK
   2   5392   2   0 /a/default_wml.css
   3    248   2   0 /a/bullet_circle.gif
   4    701   7   2 /a/phonebook_loading_30x30_c.gif
   5  85714   7  68 /a/custgoodbye.gif
y sigue


 esto es algo que acabo de descubrir mientras escribia esto. Es decir que tengo conexion con el celular, pero el moto4lin no logra conectarse. interesante... Espero que le sirva a alguien que logre determinar el problema

---

### Post by basfo on 2007-10-21
Bueno, luego de mucho probar, he logrado hacerlo andar. Estos son los datos con los que me funciono.  Les recuerdo que es un Motorola V360 y los valores seguramente cambien para otros telefonos. A mi no me funcionaba hasta que instale el Kmobiletools mencionado en este post mas arriba... no creo que tenga nada que ver, pero por las dudas lo comento, si quieren sacarse la duda pueden instalarlo

sudo apt-get kmobiletools
 
Antes de hacer nada, fijense que el telefono este configuradop para funcionar como modem fax, si esta como tarjeta de memoria no funcionara todo esto. Se cambia desde Programacion/ConexionConfiguraciones USB/Conexion Predeterminada 

Primero cargar el modulo cdc-acm si no etsa cargado

sudo modprobe cdc-acm

Ejecutar el moto4lin con permisos de root

sudo moto4lin

ir a preferences y setear estos datos

ACM DEVICE  /dev/ttyACM0
AT VENDOR ID 22b8
AT PRODUCT ID 4617  * este se supone que es un numero aleatorio, pongo ese porque me funciono
PK VENDOR ID 22b8
PK PRODUCT ID 4901

a pesar de que el programa reporta al dispositivo con el PK Prod. ID  4902, si ponemos 4901 funciona.  De hecho, a mi me anda con cualquiera de los 2.

Apretar Switch to P2K y en el sector inferior de la aplicacion principal se deberian leer los siguientes mensajes:

[info] Switching device /dev/ttyACM0 to P2K mode...
[info] AT E0 answer: AT E0 OK 
[info] Phone answer: OK 
[info] Phone pluged as P2K

Si esto es asi, ya estamos, solo le tenemos que dar a conbnect y presto. 

[info] Phone connected as P2K

Apretar "update List" para que liste los directorios que hay en el telefono. Yo me acuerdo que me funciono luego de tocar algunas opciones  del filemanager en preferences, aunque no creo que tenga nada que ver.

Algunas cosas que he aprendido son:

Todo se sube en /c/algo Las imagenes las lee directamente con solo subirlas en /c/mobile/picture mientras que para que nos tome los audios como ringtones no alcanza subirlas en /c/mobile/audio/, ademas hay que borrar dos archivos (MYToneDB.db y TempToneDB.db) de /a/mobile/audio/

Para cargar aplicaciones JAVA necesitaran habilitar esa opcion, en el seem editor escriban (si no viene por defecto ya) Seem: 0032 0001, presionen en read seem. Vayan a la fila 0004_, columna 3. Debajo, donde dice bit editor, fijarse que este tildado el 0.  Apretar el boton Write  seem. Reiniciar el telefono y en programacion/configuracion de java deberia aparecer "cargador de app java". Luego de presionar ahi nos pedira conectar el cable, si ya esta conectado lo desenchufamos y lo volvemos a enchufar. Finalmente con el linjal (el otro a mi no me funciono pero son libres de probarlo, es el midletload) escribimos

cd /carpetadondedescomprimimosellinjal/
sudo ./linjal -d /dev/ttyACM0 nomredelaaplicacion.jad

Traten de copiar el jad y el jar a lamisma carpeta del linjal. Da errores con nombres de archivo con espacios.
No se pueden subir archivos .jar, solo los jad que contiene informacion referente al jar como tamaño, proovedor y ejecutable principal. A mi, personalmente, me resulto bastante inestable pero funciona. Vean que les parece a uds.

----------------------------------------------------------
Basfo
[http://simpaticoelmocoso.blogdns.com](http://simpaticoelmocoso.blogdns.com)
-----------------------------------------------------------

---

### Post by sartrejp on 2008-09-12
Alguno sabe como puedo solucionar este error? tengo un v3, se conecta el moto 4 lin, pero me dice que no puede conseguir el nombre del telefono, ni el driver, ni nada.
Por la consola sale asi

(E_getPhoneName: E001)
(E_getDriveName: E001)
(E_fileCount: E002)
(E_getDriveName: E001)


si alguno sabe.... gracias

---

### Post by sergiom99 on 2008-09-12
v3 cuanto? yo tengo el black, V3re, y NO anda con moto4lin.

---

### Post by sartrejp on 2008-09-12
v3 black, aunque a esta altura no se, porque lo liberé, lo flasheé y le hice tantas cosas que sabe dios que cosas tiene adentro.
Pero es un bajón reiniciar la pc para ir a windows para conectar el celular...
Tal vez deba abrir un nuevo post en vez de seguir aca....

---

### Post by sergiom99 on 2008-09-12
lo mismo me pasa a mi, dualboot para eso y el iPod.

buscaste en los foros en ingles? tampoco parecen tener solucion, creo que el moto4lin esta desactualizado.

---

### Post by sartrejp on 2008-09-13
Para el Ipod no podés con Ubuntu? que ipod es? porque he viste gente que los usa.

---

### Post by sergiom99 on 2008-09-13
Ipod nano 3G black 8gb
con amarok algo puedo hacer, pero he tenido problemas.

---

### Post by sartrejp on 2008-09-13
probaste esto?
[http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

---

### Post by sergiom99 on 2008-09-13
si, funcionar funciona ok con amarok, pero no hace todo lo que hace itunes (covers, fotos, videos, etc.) Gracias.

Igual me preocupa mas que no puedan hacer andar el moto4lin con el V3re.

---

### Post by feche_mza on 2008-09-15
> **kha0s101 said:**
> [COLOR="Green"]Hmmm, creo que probé y no funcionó pero no recuerdo con  total seguridad. Así que pruebo y aviso.

Muchas gracias.

Slaud0s.[/COLOR]

***al moto4lin tenes que ejecutarlo como superusuario, en terminal si para hacerlo andar pones moto4lin tenes que poner ***> gksu moto4lin ***o*** > sudo moto4lin

---

### Post by sartrejp on 2008-10-05
sergiom, probaste con el floola para el ipod? Está en getdeb

[http://www.getdeb.net/app/Floola](http://www.getdeb.net/app/Floola)

En una de esas....

---

