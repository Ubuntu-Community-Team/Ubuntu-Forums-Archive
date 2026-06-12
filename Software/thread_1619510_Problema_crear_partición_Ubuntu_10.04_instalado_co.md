---
title: "Problema crear partición Ubuntu 10.04 instalado con Wuby"
date: 2010-11-11
forum: Software
---

### Post by myqp on 2010-11-11
Buenas noches. Agradecería si me pueden ayudar.
tengo una notebook lenovo con un disco de 160 gb con windows xp instalado.
En el mismo disco sin particionar, le instale ubuntu 10.04 para probarlo y funciona de maravilla.:popcorn:
Ahora quiero instalar definitivamente ubuntu en una partición y aparte hacer otra para los documentos.

Ejecute el instalador de ubuntu desde un pendrive y fui a la opción de crear particiones manualmente, me aparece el disco de 160 pero no me aparece espacio "sin asignar" ni me deja la opción para cambiar el tamaño de la partición existente.
Me baje una iso del gparted 0.7.0.4 y lo ejecute en el pendrive pero no me dejaba cambiar el tamaño porque decía que habia sectores erroneos en el disco, tenia que pasar el chkdsk /f/r y reiniciar dos veces.
Lo hice, también repare el disco con el programa HHD regenerator 1.6 que detecto un sector erroneo y dice que lo reparó.

Luego de todo esto, el gparted desde el pendrive sigue diciendo que el disco tiene errores q pase el chkdsk dos veces y nose que.
Sin embargo, desde el ubuntu wuby le instale el gparted y me dice que el disco está sano PERO TAMPOCO ME DEJA REDIMENSIONARLO NI NADA porque me dice que el disco está montado y no me deja desmonarlo porque esta en uso.

En definitiva, que tengo que hacer para desmontar la particion y poder liberar espacio????

Tengo algún problema en el disco duro?
O es el pendrive que esta j****o de tanto que lo formatie???:confused::confused::confused:

Espero no haber aburrido con un relato tan largo y tan impreciso. Espero q la idea general se haya captado.

cualquier dato adicional que necesiten respecto a la maq o configuración me avisan.

gracias de antemano. Saludos

---

### Post by guillermolisi on 2010-11-11
Cuando se quiere hacer lo que vos comentas primero se debe reorganizar toda la particion que queres redefinir para obtener espacio libre y asi marcar una nueva para instalar Ubuntu.

Hasta tanto esa particion no este reorganizada y verificada con chkdsk, no podras trabajar, ni se recomienda hacerlo, con un particionador.

No hace falta recurrir a particionadores de terceras partes. El Gparted es muy bueno y confiable.

Una vez acondicionada la particion a reformular podras usar el Gparted para redimensionar esa unica particion achicandola para que te quede espacio sin asignar que usaras despues con Ubuntu.

---

### Post by myqp on 2010-11-11
Hola guillermolisi, muchas gracias por responder tan rápido. Perdoname que te consulte, pero no se como hacer para "reorganizar" toda la partición. yo desfragmenté el disco desde las propiedades de MIPC en xp, lo desfagmenté tambien con el tuneup utilities, le pase el chkdsk, el /f, el /r, pero no logre ningún resultado.

me podrás indicar que paso debo seguir o donde puedo consultar un tutorial sobre como hacerlo?

Estaria infinitamente agradecido:guitar:
Saludos

---

### Post by gmunioz on 2010-11-12
Para redimensionar una partición NTFS

Desde Windows ejecuta
defrag
chkdks /f 
y cierra correctamente la sesión

Inicia el ordenador con Ubuntu conectado a la red
Verifica que se encuentren instalados gparted ntfs-config
ntfsprogs fuse-utils
Si no estan los instalas

Si la partición ntfs esta montada desmontala
Carga gparted 
Selecciona el disco rígido, por ejemplo /dev/sda
Alli verás la partición NTFS /dev/sda1
Pulsas el botón derecho sobre ella y seleccionas 
Resize/Move    Redimensionar/Mover 
Indica el nuevo tamaño de la partición, como lo desees
y se pueda
Pulsas en el botón Resize   Redimensionar 
Luego pulsas en el botón Apply   Aplicar
Te pedirá confirmación. 
Mucho Cuidado
Luego de haber confirmado, comenzarán las operaciones en el disco rígido. 
No se debe interrumpir por ninguna circunstancia
el proceso luego de haber pulsado Apply aplicar Aceptar o se
perderan todos los datos del disco.
Cuando la operación haya terminado, es conveniente salir y 
reiniciar Windows para que se adapte al nuevo tamaño de su 
partición y si no corre por su cuenta, corre chkdsk /f, cierra
correctamente y ya puedes iniciar la instalación de Ubuntu.

Te sugiero particionamiento manual
Una partición primaria, activa, sistema ext4, 20 gigas, para /
Una lógica, sistema de intercambio, 1 giga, swap
Una lógica, sistema ext4, del resto liberado, /home/usuario/datos

---

### Post by myqp on 2010-11-14
Hola. muchas gracias por las indicaciones, as voy a seguir paso a paso y mañana les comento como me fue. el q sabe sabe no hay vuelta. Gracias a todos. saludos:P:P:P:P:P:KS

---

### Post by myqp on 2010-11-16
Buenasssssssss. perdón que siga molestando con algo que para uds sea tan obvio como respirar, pero no encuentro la solucion!!!!!:mad:

Paso a detallar paso a paso lo que hice siguiendo la generosa guía de gmunioz, de modo que uds en la medida de sus posibilidades puedan indicarme donde meto la gamba:confused::

Desde windows xp abro el SIMBOLO DE SISTEMA y escribí:

**defrag c: -v**

me arrojo el informe que sigue:

                     p { margin-bottom: 0.21cm; }  *[SIZE=2]defrag c: -v[/SIZE]*
 *[SIZE=2]Desfragmentador de disco de Windows[/SIZE]*
 *[SIZE=2]Copyright (c)2001 Microsoft Corp. y Executive Software International Inc.[/SIZE]*
  
 *[SIZE=2]Informe del análisis[/SIZE]*
  
     *[SIZE=2]Tamaño del volumen                  = 149 GB[/SIZE]*
     *[SIZE=2]Tamaño de clúster                   = 4 KB[/SIZE]*
     *[SIZE=2]Espacio utilizado                   = 79,69 GB[/SIZE]*
     *[SIZE=2]Espacio libre                       = 69,35 GB[/SIZE]*
     *[SIZE=2]Porcentaje de espacio disponible    = 46 %[/SIZE]*
  
 *[SIZE=2]Fragmentación del volumen[/SIZE]*
     *[SIZE=2]Fragmentación total                 = 1 %[/SIZE]*
     *[SIZE=2]Fragmentación del archivo           = 2 %[/SIZE]*
     *[SIZE=2]Fragmentación del espacio disponible        = 0 %[/SIZE]*
  
 *[SIZE=2]Fragmentación del archivo[/SIZE]*
     *[SIZE=2]Cantidad de archivos                = 68.941[/SIZE]*
     *[SIZE=2]Tamaño promedio de archivo          = 2 MB[/SIZE]*
     *[SIZE=2]Cantidad de archivos fragmentados   = 94[/SIZE]*
     *[SIZE=2]Cantidad de fragmentos en exceso    = 5.878[/SIZE]*
     *[SIZE=2]Promedio de fragmentos por archivo  = 1,08[/SIZE]*
  
 *[SIZE=2]Fragmentación del archivo de paginación[/SIZE]*
     *[SIZE=2]Tamaño del archivo de paginación    = 1,49 GB[/SIZE]*
     *[SIZE=2]Cantidad de fragmentos              = 2[/SIZE]*
  
 *[SIZE=2]Fragmentación de carpetas[/SIZE]*
     *[SIZE=2]Cantidad de carpetas                = 7.186[/SIZE]*
     *[SIZE=2]Carpetas fragmentadas               = 5[/SIZE]*
     *[SIZE=2]Exceso de fragmentos de carpetas    = 44[/SIZE]*
  
 *[SIZE=2]Fragmentación de la tabla maestra de archivos (MFT)[/SIZE]*
     *[SIZE=2]Tamaño total de MFT                 = 83 MB[/SIZE]*
     *[SIZE=2]Cuenta de registros de MFT          = 78.421[/SIZE]*
     *[SIZE=2]Porcentaje de la MFT en uso         = 91[/SIZE]*
     *[SIZE=2]Cantidad de fragmentos de MFT       = 3[/SIZE]*
  
  
  
 *[SIZE=2]Informe de la desfragmentación[/SIZE]*
  
     *[SIZE=2]Tamaño del volumen                  = 149 GB[/SIZE]*
     *[SIZE=2]Tamaño de clúster                   = 4 KB[/SIZE]*
     *[SIZE=2]Espacio utilizado                   = 79,69 GB[/SIZE]*
     *[SIZE=2]Espacio libre                       = 69,35 GB[/SIZE]*
     *[SIZE=2]Porcentaje de espacio disponible    = 46 %[/SIZE]*
  
 *[SIZE=2]Fragmentación del volumen[/SIZE]*
     *[SIZE=2]Fragmentación total                 = 1 %[/SIZE]*
     *[SIZE=2]Fragmentación del archivo           = 2 %[/SIZE]*
     *[SIZE=2]Fragmentación del espacio disponible        = 0 %[/SIZE]*
  
 *[SIZE=2]Fragmentación del archivo[/SIZE]*
     *[SIZE=2]Cantidad de archivos                = 68.941[/SIZE]*
     *[SIZE=2]Tamaño promedio de archivo          = 2 MB[/SIZE]*
     *[SIZE=2]Cantidad de archivos fragmentados   = 3[/SIZE]*
     *[SIZE=2]Cantidad de fragmentos en exceso    = 383[/SIZE]*
     *[SIZE=2]Promedio de fragmentos por archivo  = 1,00[/SIZE]*
  
 *[SIZE=2]Fragmentación del archivo de paginación[/SIZE]*
     *[SIZE=2]Tamaño del archivo de paginación    = 1,49 GB[/SIZE]*
     *[SIZE=2]Cantidad de fragmentos              = 2[/SIZE]*
  
 *[SIZE=2]Fragmentación de carpetas[/SIZE]*
     *[SIZE=2]Cantidad de carpetas                = 7.186[/SIZE]*
     *[SIZE=2]Carpetas fragmentadas               = 1[/SIZE]*
     *[SIZE=2]Exceso de fragmentos de carpetas    = 0[/SIZE]*
  
 *[SIZE=2]Fragmentación de la tabla maestra de archivos (MFT)[/SIZE]*
     *[SIZE=2]Tamaño total de MFT                 = 83 MB[/SIZE]*
     *[SIZE=2]Cuenta de registros de MFT          = 78.421[/SIZE]*
     *[SIZE=2]Porcentaje de la MFT en uso         = 91[/SIZE]*
     *[SIZE=2]Cantidad de fragmentos de MFT       = 3[/SIZE]*
 

[B]No entiendo mucho pero veo que sigue diciendo como que hay archivos  carpetas fragmentados, tendré que ejecutar de nuevo hasta que quede en cero???????

[/B]En fin, luego escribí lo que sigue:

                     p { margin-bottom: 0.21cm; }  **[SIZE=2]chkdsk /f[/SIZE]**

**Y **me salio el siguiente mensaje:

[B][SIZE=2]
[/SIZE][/B]
 *[SIZE=2]El tipo del sistema de archivos es NTFS.[/SIZE]*
 *[SIZE=2]No se puede bloquear la unidad actual.[/SIZE]*
  
 *[SIZE=2]CHKDSK no se puede ejecutar porque otro proceso ya está utilizando el[/SIZE]*
 *[SIZE=2]volumen. ¿Desea que se prepare este volumen para que sea comprobado[/SIZE]*
 *[SIZE=2]la próxima vez que se inicie el sistema? (S/N)[/SIZE]*
 Como que el disco está en uso y que la comprobación se hace cdo se reinicia. Le pongo S, y al cual, al reiniciar windows hace un control de 3 pasos, no pego el informe porque apenas me dejo verlo:(.

Luego apago el equipo e inicio en ubuntu conecado a internet con un modem claro 3g, no se si influye pero bue.

Verifico que esten instalados los paquetes de este modo.

[B]sistema - administracion - gestor de paquetes synaptic

[/B]gparted est{a insalado
ntfs-config no lo tengo asi que lo instalo
ntfsprogs est{a instalado
 fuse-utils no lo tengo, lo instalo

hecho esto me aparece en el menu sistema- administracion - la opcion **HERRAMIENTA DE CONFIGURACION NTFS**

QUE EN LA CONFIGURAC AVANZADA me permite tildar MODIFICAR DEV/SDA1.

De esa única manera pude desmontar la unidad, otra forma no encontré.

Luego abro gparted y efectivamente no me aparece mas la llave junto al volumen y habilita la flechita como para cambiar tamaño, pero nuevamente **aparece la advertencia como que el disco tiene un sector defectuoso, que tengo que hacer chkndsk f dos veces y ejecutar** ntfsresize con la opción bad-sector y toda la sarasa del ppio.

En realidad, cuando el volumen /dev/sda1 esta montado en /host_ el gparted me lo muestra como que no tiene errores el disco, dice el espacio usado y espacio libre, pero [B]no deja redimencionar poque dice que el dispositivo esta ocupado.
[/B]Pero si le doy desmontar, ahí no me muestra mas el espacio libre, y aparece el msj que tiene un sector erroneo.

En **sistema - administracion - administracion de discos hay una opcion de autocomprobacion SMART **que la pase en modo extendido y me dice EL DISCO ESTA SANO. Desde windows con el hhd regenerator tampoco me detecta ese secor erroneo.

O sea, estoy en un circulo vicioso y cada vez me entierro mas!!!!!

si alguien conoce el camino de la luz, o bien, si mi disco está roto y no tienesolución.

En última instancia elijo la instalación que borra los datos existente, mi miedo es que si el disco está roto me borre todo y no me complete la nstalación y al final me quede sin nada:(

Ayudaaaaaaaaaaaaaaaaaa

---

### Post by biale on 2010-11-18
El programa chkdsk deja un evento "winlogon" en el registro de eventos de Windows con los resultados de la corrida. Es muy importante que postees esos resultados.

Y asegurate que haya corrido con la opción de verificar datos y *espacio libre*

Suponiendo que corras Gparted desde un arranque con live cd, no debería mostrar un signo de admiración sobre la partición NTFS. ¿Lo muestra?

---

### Post by myqp on 2010-11-18
Buenas noches. gracias otra vez por su ayuda.

Busqué en el visor de sucesos, APLICACION y aparece un winlogon. Es ese el reporte que debo postear? De ser así lo reproduzco más abajo. Si no, por favor si me podrían indicar como consultar ese reporte de winlogon con mucho gusto lo subo.
De todas maneras pude realizar la partición como explicaré seguidamente pero tengo miedo que el disco tenga errores y windows no los detecte.
Corrí gparted desde el wuby, desde el pendrive de instalación de ubuntu y desde la live cd descargada de la página oficial de gparted, en todas me salía el signo de advertencia.

gracias a todos por molestarse y tratar de encontrar soluciones a problemas ajenos desinterezadamente, un abrazo:P:P:P




Tipo de suceso:    Información
Origen del suceso:    Winlogon
Categoría del suceso:    Ninguno
Id. suceso:    1001
Fecha:        18/11/2010
Hora:        05:57:17 p.m.
Usuario:        No disponible
Equipo:    LENOVO3000
Descripción:
Comprobando el sistema de archivos en E:
El tipo del sistema de archivos es NTFS.
La etiqueta de volumen es .


Uno de los discos necesita ser comprobado para ver coherencias . Se
puede cancelar la comprobación de disco, pero se recomienda
que continúe.
Windows comprobará ahora el disco.                                         
Limpiar incoherencias sin importancia en la unidad.
Liberando 4 entradas de índice no usadas del índice $SII del archivo 0x9.
Liberando 4 entradas de índice no usadas del índice $SDH del archivo 0x9.
Liberando 4 descriptores de seguridad no usados.

     97652 KB de espacio total en disco.
         0 KB en 3 archivos.
        12 KB en 11 índices.
         0 KB en sectores defectuosos.
     66000 KB en uso por el sistema.
El archivo de registro ha ocupado      65536 kilobytes.
     31640 KB disponibles en disco.

      4096 bytes en cada unidad de asignación.
     24413 unidades de asignación en disco en total.
      7910 unidades de asignación disponibles en disco.

Información interna:
30 00 00 00 19 00 00 00 18 00 00 00 00 00 00 00  0...............
00 00 00 00 00 00 00 00 0b 00 00 00 00 00 00 00  ................
d0 12 13 00 00 00 00 00 ec 60 21 00 00 00 00 00  .........`!.....
38 9c 1c 00 00 00 00 00 00 00 00 00 00 00 00 00  8...............
00 00 00 00 00 00 00 00 bc 81 5b 07 00 00 00 00  ..........[.....
99 9e 36 00 00 00 00 00 a0 38 07 00 03 00 00 00  ..6......8......
00 00 00 00 00 00 00 00 00 00 00 00 0b 00 00 00  ................


Para obtener más información, vea el Centro de ayuda y soporte técnico en [http://go.microsoft.com/fwlink/events.asp](http://go.microsoft.com/fwlink/events.asp).

---

### Post by myqp on 2010-11-18
Como anticipe, finalmente instale un programa **EASEUS PARTITION MANAGER** y **desde windows** me permitió modificar el tamaño la partición ntfs en dos sin mostrarme ningún error ni nada por el estilo, de modo que por fin me apareció el tan deseado "espacio libre"
Luego, con el pendreive de instalación de ubuntu 10.04 pude crear las particiones en ese espacio libre tal como indican los tutoriales y finalmente pude insalar ubuntu en el disco.
Incluso pude entrar a internet con el modem 3g de claro q es mas dificil q ganarse la loteria. de modo que mañana me bajo los paquetes q faltan y cuando lo tenga configurado borro el wuby y el xp para limpiar definitivamente el disco.
Cual habrá sido el problema? quien sabe!!!!
Nuevamente gracias a todos por su ayuda, confío sepan disculpar mi ignorancia respecto a temas básicos pero bueno, a los golpes se aprende;)
Saludos y graciassssssssssss:P:P:P

---

### Post by biale on 2010-11-19
Si, el reporte que mencione era exactamente ese y los resultados muy buenos...

---

### Post by myqp on 2010-11-19
> **biale said:**
> Si, el reporte que mencione era exactamente ese y los resultados muy buenos...

Ahora duermo sin frazada:popcorn: jeje, gracias por la respuestra tranquilizadora. saludos:p

---

