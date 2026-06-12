---
title: "Backup"
date: 2009-04-24
forum: Software
---

### Post by Vero1 on 2009-04-24
Hola a todos,

Tengo en mi equipo 2 discos duros. En uno Ubuntu y en el otro XP.
Ahora estoy usando Intrepid Ibex, pero en cuanto reciba el CD instalo Jaunty.

La cuestión es saber si se puede hacer backup de mi home, marcadores de Firefox y alguna otra cosa que me interese y guardarlo en el disco donde está XP. Si se puede, pregunto: hay que hacer primero una partición en ext3?

Qué programa uso o qué comandos necesito para hacer ese backup?

Aclaro que nunca hice backup hasta ahora, por lo tanto en ese terreno soy novata.

Agradezco desde ya la orientación que me puedan dar.

Saludos

---

### Post by pablo.s on 2009-04-24
> **Vero1 said:**
> 
La cuestión es saber si se puede hacer backup de mi home, marcadores de Firefox y alguna otra cosa que me interese y guardarlo en el disco donde está XP. Si se puede, pregunto: hay que hacer primero una partición en ext3?

Qué programa uso o qué comandos necesito para hacer ese backup?


Podés comprimir todo /home con File Roller,
como si fuera un archivo mas. En Nautilus,
hacés clic derecho sobre la carpeta /home/vero
(supongamos que es asi) y elegís "crear archivo"
Le das un nombre al archivo, le decís donde 
guardarlo y ya está, se puede grabar, se puede
pasar a la partición de windows o a un pendrive.
Dentro de ese archivo están en .mozilla los
marcadores.
Saludos.

---

### Post by Vero1 on 2009-04-25
Gracias por tu respuesta pablo s. pero al hacer click derecho sobre mi home, me la abre directamente.
Si abro Archivo puedo hacer una nueva carpeta pero no figura para nada crear archivo.

Qué me podés decir?

saludos

---

### Post by EnriqueK on 2009-04-25
Varias cosas:
1.- No hace falta formatear para crear un respaldo en .tar , por lo que perfectamente podés crearlo en tu partición de Xp.
2.- Tené en cuenta que lo que podés llegar a tener en /home no tiene límites, por lo que para respaldarla va a ser necesario estudiar bien el caso, personalemen yo tengo solamente configuraciones y archivos que luego serán volcados a DVD y luego borraqdos de mi  carpeta de usuario.
3.- yo creo periódicamente respaldos en una carpeta que denomino 12345 ubicada en la partición D y loa comandos que uso son (uno y luego el otro), te va a crear respaldo de todas las carpetas de usuario
```
cd /home
sudo tar czvf /media/D/12345/home_bk.tgz *
``` 
4.- Cuando toque reponer uso el Live CD de instalación y mediante el comando sudo nautilus navego hasta /home , borro ni carpeta de usuario anterior , muevo allí el respado , lo descomprimo allí mismo y luego borro el archivo comprimido.

---

### Post by pablo.s on 2009-04-25
> **Vero1 said:**
> Gracias por tu respuesta pablo s. pero al hacer click derecho sobre mi home, me la abre directamente.

El otro boton derecho, el que
está al lado...

#####    ######
#       #[COLOR=Silver]##[/COLOR]#        #
#       #[COLOR=Silver]##[/COLOR]#        #_________este botón
#       #[COLOR=Silver]##[/COLOR]#        #
#####[COLOR=Silver]##[/COLOR]#####
.           .
.           .__________________rueda del mouse
___________________________botón izquierdo

---

### Post by josecuervo86 on 2009-04-25
> **pablo.s said:**
> el otro boton derecho, el que
está al lado...

#####    ######
#       #[color=silver]##[/color]#        #
#       #[color=silver]##[/color]#        #_________este botón
#       #[color=silver]##[/color]#        #
#####[color=silver]##[/color]#####
.           .
.           .__________________rueda del mouse
___________________________botón izquierdo

:lolflag:

---

### Post by Vero1 on 2009-04-27
Gracias EnriqueK, 

Tomo nota.

saludos

pablo.s o_0

En mi mouse hay 2 teclas, mas la rueda. No entiendo eso del "otro" botón derecho O_O

Vos tenés 4 botones mas la rueda????;-)

saludos

---

### Post by Vero1 on 2009-04-27
Hola EnriqueK,

Quise hacer una prueba de backup.
Primero monté la unidad.
Despues creé un archivo en mi home llamado Prueba de backup.
Despues en consola puse tu instrucción y me contestó ésto:

veronica@veronica-Intrepid:~$ cd /home
veronica@veronica-Intrepid:/home$ sudo tar czvf /media/disk/dev/sda5/home/Prueba de backup_bk.tgz
tar: de: No se puede stat: No existe el fichero ó directorio
tar: backup_bk.tgz: No se puede stat: No existe el fichero ó directorio
tar: /media/disk/dev/sda5/home/Prueba: No se puede open: No existe el fichero ó directorio
tar: El error no es recuperable: salida ahora
tar: Child returned status 2
tar: Salida con error demorada desde errores anteriores

Dónde está el error? Es porque se trata de un archivo nada mas y no es un directorio? Tendría que haber sido todo el home? No tengo gran cosa en home.

Perdón pero nunca hice backup antes y no tengo idea.

Agradeceré tus comentarios.

Saludos

---

### Post by pablo.s on 2009-04-27
Muy bien explicado [aqui]("http://linuxcordoba.org:8080/node/88").

---

### Post by EnriqueK on 2009-04-27
Hacé una cosa, abrí un terminal y arrastra a este terminal la carpeta donde querés que se almacene el respaldo y lo posteas acá, lo que pasa es que ocurren varias cosas, en primer lugar la ruta que has puesto a la carpeta no es la correcta y además te has olvidado de poner el asterisco al final del comando o sea al final debes poner **home_bk.tgz ***.
Otra cosa, cuando indicas la ruta en el terminal esta debe contener carpetas y archivos de un solo nombre o sea que no tengan espacios , en caso de no poder evitarse, a los nombres compuestos debes ponerlo entre comillas, por todo esto lo mas simple es que hagas lo que te dije al principio o sea arrastra al terminal la carpeta contenedora y así sabré la ruta y trataré de crear el comando completo y de paso a esa carpeta ponele un nombre de una sola palabra.

---

### Post by juancarlospaco on 2009-04-27
Por que no le hacen usar una GUI como **Back In Time** o **Deja Dup** ?

---

### Post by pablo.s on 2009-04-27
Porque no.

Que ella haga lo que le sirva,
aca le estamos sugiriendo
opciones...

Todo bien, señor paco.

---

### Post by pablo.s on 2009-04-27
Vero, lo que te comentaba, es que
creo que estás haciendo clic izquierdo
en lugar de clic derecho, como te
escribí en el post... Espero que te
sirva el método, porque es muy simple.

---

### Post by Vero1 on 2009-04-28
Hola Pablo.s

Gracias por lo que me informás. Lo veré.

En cuanto al click, te aseguro que usé el click derecho pero es como te dije en post anterior.

saludos :)

---

### Post by Vero1 on 2009-04-28
Hola EnriqueK,

Es cierto, no puse el asterisco. Cosas de novata en materia de backup :)

En cuanto pueda hago lo que me decís y te lo posteo.

Gracias.

saludos

---

### Post by Vero1 on 2009-05-31
Hola EnriqueK,

Perdón por la tardanza en seguir el hilo, pero tuve ciertos inconvenientes personales.

A ver si ésto estaría bien:

cd /home

sudo tar czvt /media/D/resp.ubuntu/home_bk.tgz *

Aclaro que ya creé en win-disco D, la carpeta resp.ubuntu.

Ahora, tengo una duda. En /home con ctrl+h salen las carpetas ocultas, entre las cuales están .evolution y .mozilla, que son las dos que me interesa hacer backup, mejor dicho de mozilla lo que me interesa es hacer backup de los marcadores nada mas.

Con tu comando, se hace backup de todo /home? 
Cuando descomprimo, se descomprime todo o sea, en este caso, .mozilla. No se va a mezclar con el FF que trae Jaunty? y cómo hago con los marcadores que es lo que me interesa?

Disculpa tanta pregunta.

Saludos.

---

### Post by Air23 on 2009-05-31
> **Vero1 said:**
> Ahora, tengo una duda. En /home con ctrl+h salen las carpetas ocultas, entre las cuales están .evolution y .mozilla, que son las dos que me interesa hacer backup, mejor dicho de mozilla lo que me interesa es hacer backup de los marcadores nada mas.

Con tu comando, se hace backup de todo /home? 
Cuando descomprimo, se descomprime todo o sea, en este caso, .mozilla. No se va a mezclar con el FF que trae Jaunty? y cómo hago con los marcadores que es lo que me interesa?
Si queres resguardar tus marcadores:
1. Abri Firefox
2. Marcadores > Organizar marcadores
3. Importar y resguardar. 
Aca los podes resguardar o exportar en HTML y te genera un pequeño archivo que podes guardar en un pendrive o mandar por mail o lo que quieras hacer.

Cuando quieras restaurar los marcadores, haces los mismos pasos pero seleccionando dentro de organizar marcadores "Restaurar" (si tus marcadores los resguardaste) o "Importar HTML" (si los exportaste)

---

### Post by EnriqueK on 2009-05-31
> **Vero1 said:**
> 

sudo tar czvt /media/D/resp.ubuntu/home_bk.tgz *


Hay un error en la expresión, aunque lo mas probable es que sea por tipeo al postear en el foro, debes poner **czvf** en vez de **czvt**.
Esfectivamente esta expresión es para respaldar toda la /home, incluyendo a todas las carpetas de usuario que se tengan allí, yo la uso por que solo tengo configuraciones en mi carpeta de usuario, los documentos los pongo en otra particiñon exclusiva para este fin y así el procesp de respaldar mi /home es muy rápido.
Si solo te interesa respaldar las configuraciones de Firefox, simplemente entra a tu carpeta de usuario  y mediante un Copy & Paste  respalda las carpets oculta **.mozilla** , la** .mozilla-thunderbird**    y así  s la carpeta de configuraciones que quieras.
Si solo te interesa respaldar los marcadores, hay varias maneras de hacerlo, una es la que te nombraron arriba, otra es que instales la extensión o complemento** Febe**, el cual te va a permitir respaldar las extensiones, otra forma es usar un servicio de almacenamiento on-line de tus marcadores (nunca lo usé), etc.
Como veo que uas además windows es posible que quieras sincronizar los marcadores y las cookies entre ambas instalaciones, te podría dar los detalles para hacerlo, es muy simple pero se hace largo de explicar en palabras, solo mencionaré que a partir de Firefox 3.0 , los marcadores se almacenan en el archivo **places.sqlite ** que se encuentra dentro de la carpeta del perfil.

---

### Post by sebastianabate on 2009-05-31
No se olviden de la "p" en el comando para mantener los permisos y usuario:grupo de los archivos. El comando tendría que ser

sudo tar czvfp /media/D/resp.ubuntu/home_bk.tgz *

---

### Post by Vero1 on 2009-06-02
Gracias a los tres.

saludos :-)

---

### Post by Vero1 on 2009-06-02
Hola,

Al ejecutar el comando que me diste Enrique K, me sale lo siguiente:

veronica@veronica-Intrepid:~$ cd /home
veronica@veronica-Intrepid:/home$ 
veronica@veronica-Intrepid:/home$  sudo tar czvf /media/D/resp.ubuntu/home_bk.tgz *
tar: /media/D/resp.ubuntu/home_bk.tgz: No se puede open: No existe el fichero ó directorio
tar: El error no es recuperable: salida ahora

Qué es lo que está mal?
Yo creé una carpeta en el disco D (windows) con el tìtulo de resp.ubuntu. Por qué no lo encuentra?

saludos

---

### Post by EnriqueK on 2009-06-02
Que raro, hice la prueba en crear una carpeta resp.ubuntu en mi partición D y seguidamente apliqué exactamente los misos comandos que indicas en tu mensaje, el resultado fué correcto, tal vez tu partición D no la tengas montada o tengas un error en el nombre de tu carpeta.
Te paso otro método un poco mas entendible y lo mas aeindoseau posible.
1.- Abre un terminal y pones **cd** dejas un espacio, seguidamente navega por tu partición D y **arrastras la carpeta resp.ubuntu ak termina**l --> Enter y con esta acción tendrás abierto el terminal dentro de tu carpeta resp.ubuntu.
2.- Seguidamwente, en ese mismo terminal pones
**sudo tar czvf vero.tar** dejas un espacio , luego navega por el sistema de archivos de Ubuntu , entras a la carpeta /home y seguidamente **arrastra al terminal tu carpeta de usuario ** ->-Enter y comienza el proceso, al finalizar vas a tener dentro de resp.ubuntu un archivo denominado vero.tar . este archivo no lo vas a poder descomprimir en la partición de windoes, para hacerlo debes copiarlo o moverlo a por ejemplo tu escritorio.

---

### Post by juancarlospaco on 2009-06-02
OMG usen una GUI... :)

---

### Post by Vero1 on 2009-06-04
Hola Enrique K,

Mirá, me fuí directamente a la partición de Windows para comprobar que efectivamente la carpeta fue creada(le cambié el nombre por respaldoubuntu) y sí, está en la partición D, pero aunque monte la unidad en Ubuntu, no me acepta igual.

Tendrá algo que ver que si veo gparted indica que esa partición es /dev/sdb2/ o sea, en el comando no debería figurar así en lugar de /D/?

Tal vez sea una preguntonta pero me pregunto èsto porque no acepta el comando que tenga D.

En mi home figuran las particiones de windows pero como Soportes, no dice unidad de disco, al contrario del CDRom que sí dice unidad de CDRom y no sé la razón. Tendrá algo que ver en todo ésto?

Agradezco tu orientación.

saludos

---

### Post by staar on 2009-06-04
el problema es que el disco D de windos no se monta por defecto en /media/D, se montaría ahi si la etiqueta de la partición fuera esa, 'D', pero, lo más común, es que no se etiquete a los discos (no se les 'cambia el nombre'), asi que supongo que ese será tu caso...

los discos sin etiquetar son montados en /media/disk para el primero, /media/disk-1 para el segundo, y asi sucesivamente...

te recomendaría que, luego de montado el disco, vayas hasta la carpeta /media y verifiques el nombre correcto del punto de montaje y lo sustituyas en el comando...

de otra forma, apoyo lo que dice juan carlos, usá algún programa con interfaz gráfica, que hay varios (deja dup, back in time, etc) y son muy simples, asi te ahorras tanto lio...

saludos

---

### Post by Vero1 on 2009-06-04
Hola staar,

Gracias por tu intervención.
He montado esa partición y me indica que está en /media/disk. 
Entonces el comando correcto sería:

cd home
sudo tar czvfp /media/disk/respaldoubuntu/home_bk.tgz *    ??

Gracias de antemano.

Saludos

---

### Post by staar on 2009-06-04
exacto, ese mismo...

saludos

---

### Post by EnriqueK on 2009-06-04
A ver,  lo primero que te recomiendo es hacer que tu partición se monte automáticamente al inicio y si además esa partición está en formato  NTFS, vas a requerir que tenga atributoss de escritura, ya que al parecer estás usando Intrepid, podeés instalar desde los repositorios el paquete** disk-manager** y adeás  debés instalar el paquete **ntfs-3g** .
Una vez instalado lo anterior, abre ter,omal y pones** killall-nautilus**, luego ya queda habilitado el disk-manager y podés acceder a el  desde el menú  sistema--> Administración-->Administrador de disco -->XConfiguraciín avanzada, marcas las particones que quieras se monten al inicio y luego pulsas Editar para habilitar los atributos de escritura (ntfs-3g).
Una vez cumplido lo anterior, ya podrás navegar desde Ubuntu en la partición montada , por lo que sería bueno que abras un terminal y arrastres a dicho terminal la carpeta en donde quieras almacenar tu respaldo, esta acción hace que en el terminal aparezca la ruta a dicha carpeta y luego la posteas aca.

---

### Post by Vero1 on 2009-06-05
Gracias staar  :D

saludos

---

### Post by Vero1 on 2009-06-05
Hola EnriqueK,

Seguiré tus instrucciones.

Muchas gracias por todo.

saludos :D

---

### Post by Vero1 on 2009-06-05
Hola,

Instalé el Disk-Manager. ntfs-3g ya estaba instalado.

Terminal no acepta el comando killall-nautilus,dice: orden no encontrada,  pero pude usar igual el disk-manager y monté las dos particiones de windows y edité la partición que nos interesa. Ya estaba indicado lectura-escritura.

Trasladé la carpeta respaldoubuntu a Terminal y me salió ésto:

veronica@veronica-Intrepid:~$ '/media/sda5/respaldoubuntu'

EnriqueK, entonces ésta sería la ruta a poner en el comando?

saludos

---

### Post by EnriqueK on 2009-06-05
Si, esa es la ruta a tu carpeta done quieres almacenar el respado, aunque me llama un poco la atención la etiqueta que te muestra la partición , al menos a mi en las diferentes versiones de Ubuntu que instalé, siempre me las mostraba como D , sugiero (si no lo has hecho ya, que reinicies tu equipo y compruena que la partición se monte automáticamente y vuelve a repetir el proceso de arrastrar la carpeta al terminal y ver si muestra la misma ruta y de paso crea o mueve algún archivo allí  para compovar que tiene atributos de escritura, suponiendo que todo siha ugual, utilza el segundo método que te expliqué antes por que me parece mas entendible, en tu caso sería, abre un terminal y pones 
[B]cd '/media/sda5/respaldoubuntu' 
sudo tar czvf vero.tar.gz /home/veronica[/B]

---

### Post by Vero1 on 2009-06-06
Hola EnriqueK,

Reinicié varias veces para ver si se montaban los discos y sí, se montan.
Hice nuevamente el traslado de la carpeta a Terminal y sigue saliendo lo mismo de antes.
Ahora, si veo Propiedades de hda5 dice que los permisos están comprobados, pero si veo propiedades de la carpeta "respaldoubuntu" dice que pertenece a root y que yo no tengo permiso.

Para cambiar ese permiso está el comando chmod o algo así no? 
Si es así, cómo sería el comando exacto?

La ruta es:  '/media/sda5/respaldoubuntu' 


Una vez cambiados los permisos, recien podré hacer lo que me indicás.

Gracias

---

### Post by staar on 2009-06-06
sería mejor usar chown, para cambiarle el propietario a la carpeta, algo así ```
sudo chown *tuusuario* /media/sda5/respaldoubuntu
``` obviamente reemplazando *tuusuario* por tu nombre de usuario exacto...

saludos

---

### Post by Vero1 on 2009-06-07
Hola staar,

Ejecuté el comando como sigue:
 sudo chown veronica '/media/sda5/respaldoubuntu'

pero en la carpeta en cuestión sigue figurando root...

Me pregunto si no sería mas facil directamente hacer el respaldo en un CD, haciendo drag and drop de Home y Evolution y exportando los marcadores de FF ?

Si es posible, lo único que no sé es cómo instalar todo éso en Jaunty, despues.

Pido disculpas por tanta lata.

Gracias

---

### Post by EnriqueK on 2009-06-08
Parece que estás confundida, esa carpeta y todas ellas, tienen como propieario a root, lo que se requiere es que tengan atributo de lectura-escritura y si es una partición NTFS se va a requerir de ntds-3g que ya lo tienes instalado, por eso sugerí usar el programa Disl-Manager (Administrador de discos) , entonces como ya lo tienes instalado, entra al menú Sistema-->Administración-->Administración de discos --> Configuración avenzada--> selecciona la parción--> Editar-->En donde dice Controlador  selecciona  ntfs-3g (Read-write driver), adepta y eso es todo, la partición ya tendrá atributo de lectura-escritura , lo que es fundamental, ya que si no tuviera estos atributos, no podrás guardar ningún archivo nuevo.
Luego aplica los siguientes comandos (uno seguido del otro).
[B]cd '/media/sda5/respaldoubuntu'
sudo tar czvf vero.tar.gz /home/veronica[/B].

Respecto a tu intenxión de migrar a Jaunty, opino que es el momento mas apropiado para tener tu /home en particióm separada , para ello vas a requerir que tengas formateada una partición de un tamaño adecuado  en un sistema de archivos de Linux , por ejemplo ETX3 , copias allí tu carpeta de usuario y procedes a instalar Jaunty , eliges la opción de hacerlo manual  y en opciones seleccionas a la partición donde copiaste tu carpeta de usuario para que tenga como punto de montaje a /home y asegurate de **no tener marcado** el casillero para formatear, o sea no debes formatear esta parición .

---

### Post by Vero1 on 2009-06-08
Hola EnriqueK,

Todo mal, pero no por tus indicaciones si no porque no alcanzó el espacio y tuve que formatear la partición pero como ntfs estaba en gris, tuve que hacerlo como Fat32.

Mirando las propiedades dice que está habilitado para escritura pero sobre lectura no dice nada, mejor dicho no hay opción.

La partición tiene libres l.43 Gib, pero le precede una extendida de igual tamaño pero no sé cómo unificarlas, si es que se puede.
No pensé que no me iba a alcanzar el espacio...

Qué me aconsejas que haga ahora? (espero que no sea que me suicide);)

Gracias.

---

### Post by Vero1 on 2009-06-08
> **Vero1 said:**
> Hola EnriqueK,

Todo mal, pero no por tus indicaciones si no porque no alcanzó el espacio y tuve que formatear la partición pero como ntfs estaba en gris, tuve que hacerlo como Fat32.

Mirando las propiedades dice que está habilitado para escritura pero sobre lectura no dice nada, mejor dicho no hay opción.

La partición tiene libres l.43 Gib, pero le precede una extendida de igual tamaño pero no sé cómo unificarlas, si es que se puede.
No pensé que no me iba a alcanzar el espacio...

Qué me aconsejas que haga ahora? (espero que no sea que me suicide);)

Gracias.

Se me ocurrió ir a Windows y desde allí sí pude formatear la partición como ntfs, así que eso estaría solucionado.
Me faltaría saber si se puede unificar esta partición con la otra que es extendida, así tendría un total de 2.80 Gib mas o menos, cosa que tampoco sé si será suficiente.

---

### Post by EnriqueK on 2009-06-09
Entonce lo que te sugiero son dos cosas, primero que el respaldo lo hagas directamente en un pendrive , desconozco el tamaño que tenga tu carpeta de usuario, pero si a todos tus documetos, películas ,úsica, etc, etc, los grabás en CDs o mejor en DVDs  y luego los borras de tu carpeta de usuario, lo que te va a quedar son solametente configuraciones que no pesan gran cosa y caben pergectamente en un pendrive modesto, seguidamente borras tu partición de Ubuntu y hacés una redefinición creando una partición aparte que es en donde tendrás tu carpeta de usuario , hay mucha literatura de como hacerlo, pero para tu partición raiz con unos 10 gigas es suficiente, un giga para Swap y el resto para ru /homem lo que queda es instalar Jaunty de cero, pero definiendo de entrada tener tu /home separada.

---

### Post by juancarlospaco on 2009-06-09
[I]Quiero UbuntuOne yaaaaaaaaaaa... 
asi guardo mis cosas arriba de una Nube, encriptadas y firmadas con SeaHorse.[/I]

---

### Post by Hei Ku on 2009-06-09
Utiliza DropBox, que no es beta.

---

### Post by juancarlospaco on 2009-06-09
Nu..., quiero UbuntuOne, 
*Mientras tanto uso un disco IDE viejito con Back In Time.*

---

### Post by pablo.s on 2009-06-09
Hay una cola de 25 mil
personas"(*) esperando Ubuntu One.
Como diria Hei Ku, anda
buscando un almohadoncito...

(*)No es exageración.

---

### Post by juancarlospaco on 2009-06-09
[I]Donde ves la cola de personas anotadas pablo.s ???
o es una aproximacion tuya?[/I]

Me parece perfecto, 
quiere decir que hay mucha gente interesada en Ubuntu y sus Servicios.

---

### Post by pablo.s on 2009-06-09
> **juancarlospaco said:**
> [I]Donde ves la cola de personas anotadas pablo.s ???
o es una aproximacion tuya?[/I]


Tengo fuentes... bah,
los chavales que están
programando el cliente 
de Ubuntu One son todos
argentinos, preguntale
a Beuno sino.

---

### Post by Vero1 on 2009-06-09
Enrique K,

Lamento pero no tengo pendrive y tampoco lectora de DVD.

Parece que mi /home es grande porque todo está metido allí. Debe tener cerca de 2 Gib o mas.

Por éso preguntaba si no se podía unificar /dev5 con la partición extendida que le precede, ya que tendría un total de mas o menos 2.80 Gib. Pero la extendida no aparece en los device que figuran en Equipo.

Intenté comprimir /home como lo indicó pablo.s (creo) y meterlo en un CD pero me contesta que no tengo permiso en el lugar de destino...

Bueno, estoy como cuando empecé :-(

saludos

---

### Post by pablo.s on 2009-06-09
> **Vero1 said:**
> 
Intenté comprimir /home como lo indicó pablo.s (creo) y meterlo en un CD pero me contesta que no tengo permiso en el lugar de destino...

Bueno, estoy como cuando empecé :-(

saludos

Intenta hacer lo mismo
pero que el destino sea
dentro de tu /home.

---

### Post by Vero1 on 2009-06-09
pablo.s

Tu idea es que comprima mi home dentro de mi home y que luego trate de grabarlo en el CD ?



saludos

---

### Post by EnriqueK on 2009-06-09
Probá con crear el respaldo comprimido en la carpeta /tmp del sistema, si tenés espacio suficiente la vas a poder crear, pero tenés que respaldarla en CD por que se borrará en el próximo reinicio del sistema.

[B]cd /tmp
sudo tar czvf vero.tar.gz /home/veronica[/B]

Puede ser que tengas espacio eb tu partición donde tenés Xp , en ese caso seguí lo explicado antes o sea montar y dar atributos de escritura y si no estoy mal, el comando sería 

[U]cd '/media/sda1/respaldoubuntu'
sudo tar czvf vero.tar.gz /home/veronica[/U]

---

### Post by juancarlospaco on 2009-06-10
**raid+lvm** :)

---

### Post by Hei Ku on 2009-06-10
> **juancarlospaco said:**
> **raid+lvm** :)

Off-topic. Estan hablando de backup, no de alta disponibilidad. No aporta a la discusión.

Si usas raid+lvm como backup, avisame dónde es, que ahí no guardo mis datos. ;)

---

### Post by juancarlospaco on 2009-06-10
Y si los discos estan en Mirroring son un clon constante uno de otro, 
como no vas a tener copia redundante de los datos.

El mismo nombre lo dice **Redundant** Array of *Inexpensive* Disks
luego renombrado a
**Redundant** Array of *Independent* Disks
Ademas no es un Array fisico, 
como los viejos Array SCSI,
las cosas son por software.

*redoblo la apuesta:*
**RAID+LVM+Cifrado+SSD**

Si perdes datos asi, yo creo que estamos en problemas

---

### Post by Vero1 on 2009-06-10
Hola EnriqueK,

en tmp entró perfectamente pero lamentablemente no fue así en win.
A pesar de la compresión no alcanzaron los 1.4 Gib.

La verdad es que hay demasiadas cosas en mi home, como te dije antes, está todo allí.

Lástima lo de Evolution. No se puede respaldar nada mas que los correos y los contactos?

Y los marcadores de FF se pueden exportar y luego importar en forma de html como me indicaste.

Despues vería qué me interesa de /home y trataría de grabar en CD.

Qué opinás?

saludos

---

### Post by Hei Ku on 2009-06-10
> **juancarlospaco said:**
> Y si los discos estan en Mirroring son un clon constante uno de otro, 
como no vas a tener copia redundante de los datos.

El mismo nombre lo dice **Redundant** Array of *Inexpensive* Disks
luego renombrado a
**Redundant** Array of *Independent* Disks
Ademas no es un Array fisico, 
como los viejos Array SCSI,
las cosas son por software.

*redoblo la apuesta:*
**RAID+LVM+Cifrado+SSD**

Si perdes datos asi, yo creo que estamos en problemas

El backup se hace en otro medio. No dependes de los mismos discos, porque un día se rompen los dos y fuiste.

O sea, un buen backup implica guardar las cosas en cinta, DVD, etc. y cada tanto llevarse una de esas copias a otro lugar.

Aca tenes el ejemplo de alguien que confió en RAID: [http://www.datacenterknowledge.com/archives/2009/05/15/data-loss-no-backups-for-flight-sim-site/](http://www.datacenterknowledge.com/archives/2009/05/15/data-loss-no-backups-for-flight-sim-site/)

---

### Post by guillermolisi on 2009-06-10
> **Hei Ku said:**
> El backup se hace en otro medio. No dependes de los mismos discos, porque un día se rompen los dos y fuiste.

O sea, un buen backup implica guardar las cosas en cinta, DVD, etc. y cada tanto llevarse una de esas copias a otro lugar.

Aca tenes el ejemplo de alguien que confió en RAID: [http://www.datacenterknowledge.com/archives/2009/05/15/data-loss-no-backups-for-flight-sim-site/](http://www.datacenterknowledge.com/archives/2009/05/15/data-loss-no-backups-for-flight-sim-site/)
Agrego.

No solo en otro medio fisico distinto e independiente del original sino almacenado, luego de su generacion, en otro lugar fisico diferente de donde residen los medios fisicos originales.

Ademas, hay criterios y politicas de backup segun sus contenidos, su importancia, el grado de respaldo que se quiera lograr, etc., y estos factores no estan presentes en un RAID, de la clase que sea, porque son cosas distintas con finalidades distintas que se complementan como parte de un esquema de continuidad de negocio.

RAID apunta a una continuidad funcional de servicios. El backup apunta a preservar los datos a traves del tiempo (como si fuera una foto).

---

### Post by juancarlospaco on 2009-06-10
un RAID es otro medio fisico INDEPENDIENTE, en el nombre lo dice.
un RAID no implica que sean dos discos, pueden ser muchos mas.

El link que me pasaste es de Microsoft Flight Simulator, 
estaban usando Windows en ese Servidor, yo a Windows no le confio mis datos nunca.

---

### Post by Hei Ku on 2009-06-11
Juan Carlos, cualquier administrador serio te dice lo mismo. RAID es para disponibilidad, no para backup. Tenes cualquier problema dentro de la maquina y podes perder todos los discos al mismo tiempo. 2, 4, 6, los que tengas. Si hay una tormenta y pega un rayo, te quemó la fuente, los discos y todo lo demas, y fuiste.
RAID no es una solucion de backup. El backup se hace a medios que se sacan de la maquina, y se sacan del lugar donde esta la computadora. Eso, al menos, hace la gente responsable.

---

### Post by guillermolisi on 2009-06-11
> **juancarlospaco said:**
> un RAID es otro medio fisico INDEPENDIENTE, en el nombre lo dice.
un RAID no implica que sean dos discos, pueden ser muchos mas.

El link que me pasaste es de Microsoft Flight Simulator, 
estaban usando Windows en ese Servidor, yo a Windows no le confio mis datos nunca.
Ese termino "independiente" en el nombre RAID, es independiente de que cosa ?

Podes tener una caja con discos hot swap en RAID, fuente redundante por todos lados, logica redundante, conexiones redundantes, BIOS con backup, etc., etc. y asi y todo las mejores practicas siguen recomendando hacer backup a disco y luego a medios removibles.

Ante un siniestro, los discos, fuentes, logicas, cables, BIOS, etc., se reponen en terminos de dias, un par de semanas. Recuperar los datos de una empresa cuya actividad comenzo hace años (y que actualmente no considera soporte ni procesos administrativos alternativos, en un gran mayoria por lo menos en Argentina) tambien lleva dias .... unos 365, por ejemplo :)

---

### Post by fmsismo on 2009-06-11
Raid no sirve como backup porque ante un error humano sobre el sistema, intrución o un bug perdes todo.  El backup debe ser en un dispositivo separado y si tenes información crítica, deberías tener una copia en otra ubicación respecto a la que están los equipos.

Ahora, si usas el raid para guardas las fótos digitales de la familia, podes considerarte seguro con un raid 1 :-P  (Yo igual hago backup trimestrales en dvd)

Saludos

---

### Post by EnriqueK on 2009-06-11
Vero
Por lo que puedo apreciar, tenés tu partición raiz con bastante espacio , al menos es capaz de contener tu carpeta de usuario y además una copia comprimida de la misma, te recomiemdo que instalés el programa **gparted** , no para usarlo como editor de particiones, sino para que te muestre las mismas en forma gráfica y así le sacás un pantallazo lo subís a **Imageshack** y pegás asá el enlace para así rener mejor información** [http://imageshack.us/](http://imageshack.us/).**
Por otra parte, si a tu carpeta de usuario le borras los documentos, y carpetas no ocultas previo respaldo de las mismas en CDs, te va a quedar bastante reducida, en mi caso así lo hago y el tamaño comprimida es de unos 160 megas.
Otra cosa, podés respaldar a tu Firefox , simplemente  copiando tu carpeta oculta** .mozilla** , lo mismo con la carpeta** .evolution**.

---

### Post by sergiom99 on 2009-06-11
Para hacer backup de mi perfil de Firefox, yo uso una extension del mismo, FEBE (Firefox Environment Backup Extension) [1].
Muy util, se usa dentro del mismo FF y podes programar que te haga la copia automaticamente. Con eso voy moviendo mis preferencias de PC a PC.
Suerte! -Sergio

[1] [https://addons.mozilla.org/en-US/firefox/addon/2109](https://addons.mozilla.org/en-US/firefox/addon/2109)

---

### Post by juancarlospaco on 2009-06-12
> **Hei Ku said:**
> Juan Carlos, cualquier administrador serio te dice lo mismo. RAID es para disponibilidad, no para backup. Tenes cualquier problema dentro de la maquina y podes perder todos los discos al mismo tiempo. 2, 4, 6, los que tengas. Si hay una tormenta y pega un rayo, te quemó la fuente, los discos y todo lo demas, y fuiste.
RAID no es una solucion de backup. El backup se hace a medios que se sacan de la maquina, y se sacan del lugar donde esta la computadora. Eso, al menos, hace la gente responsable.

**Coincido. **
*Ahora si lo explicaste bien.*

---

### Post by Vero1 on 2009-06-21
EnriqueK,

Perdón por la tardanza pero esperé a que me instalaran la grabadora de DVD para hacer los respaldos y luego me quedé sin conexión...

Como me sugeriste copié las carpetas de .evolution y .mozilla. Hasta aquí, todo bien.

Ahora mi problema está en que no puedo usar ese DVD porque a Jaunty no se le ocurre montar la unidad(bueno, es un modo de decir):D

Hace dos días instalé Jaunty y la verdad es que me está trayendo diversos problemas, dos de los cuales ya están solucionados por suerte.

Bueno, como digo, no se puede montar el CD-RW/DVD-RW. Ya estuve googleando pero sin llegar a una solución práctica. La cuestión es que si abro Equipo aparece pero cuando le pido montar me contesta que no se puede montar el lugar ni el archivo... 

Envío un paste de mi fstab, para que veas.

[http://pasto.elefantesrosas.com.ar/pastos/view/25/fstab](http://pasto.elefantesrosas.com.ar/pastos/view/25/fstab)

Desde ya agradezco las sugerencias que me puedas dar.

Saludos

---

### Post by EnriqueK on 2009-06-22
El análisis del fstab no es precísamente my fuerte, por lo ue no es gran cosa lo que te puedo ayudar en este punto, pero me llama un poco la atención es la última linea (17) , me parece que está mal. probá con ponerle una almoadilla # al comienzo y reiniciá el sistema, ¿cuantas unidades ópticas tenés?.
Veo que ahora solo tienes Ubuntu y que configuraste con /home separada, ¿que espacio dedicaste a cada partición?

---

### Post by Vero1 on 2009-06-22
Posiblemente esté mal, ya me lo habían comentado pero no me dieron solución.
Voy a postear un nuevo thread con el problema del montaje.

Tengo 2 unidades òpticas. Una grabadora de CD y una de CD-RW/DVD-RW.

No tengo solamente ubuntu. Tengo 2 discos. En uno está Ubuntu y en el otro Windows.

En Ubuntu le asigné 20 Gib a / 1.88 a Swap y 54 a Home.

saludos y gracias por tu ayuda.

---

