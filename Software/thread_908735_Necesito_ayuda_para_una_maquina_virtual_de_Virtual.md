---
title: "Necesito ayuda para una maquina virtual de Virtual Box"
date: 2008-09-02
forum: Software
---

### Post by pablerque on 2008-09-02
Buenas, el problema es el siguiente:

Tengo una maquina virtual en el virtual box con el sistema windows xp que lo uso cada vez que lo necesito (con dos discos virtuales: uno el del sistema propiamente dicho y otro para otros proyectos)y cuando termino mi trabajo dentro de la maquina, en vez de apagarla, la suspendo (para evitar los tiempos de inicio y cierre).

El problema es que al reintalar ubuntu, me canbiaron el orden de las particiones reales de mi disco y las configuraciones de la maquina virtual siguen siendo las anteriores a la reinstalacion y ahora no puedo inicializar mi sistema xp huesped y pierdo todo mi trabajo.

El error que me da virtual vox es el siguiente:

Shared folder host path /media/sda2/Directorio compartido is not accesible

En realidad, mi directorio compartido esta en el sd4 (cambiaron el orden de las pariciones al reinstalar ubuntu)

Creo que hay dos posibles soluciones:
Cambiar el nombre sda4 por sda2 y visceversa o entrar al archivo del virtual vox y editar manualmente esa ruta ya que con la maquina suspendida no puedo realizar ningun cambio de configuracion.

Espero sugerencias.

Saludos.

---

### Post by zeroadrenaline on 2008-09-03
Hola, bueno, a ver si te puedo dar una manito, si entendí bién, vos antes tenias seteado para que vbox compartiera con ubuntu un directorio en /media/sda4 y ahora despues de reinstalar ese disco se monta en /media/sda2, correcto?.
Si es así, podrias probar algo mas sencillo, simplemente cambiar de lugar cada disco.
En otras palabras, desmontarlos, el sda2 y el sda4, y montarlos cambiados, el /dev/sda2 en /media/sda4 y viceversa.
Si nececitas ayuda para montar discos, [http://www.ubuntu-es.org/index.php?q=node/4028](http://www.ubuntu-es.org/index.php?q=node/4028)
Te recomendaria que no te pongas en la empreza de editar el fstab, vos solo lo nececitas una sola vez, restaura tus config's de vbox y listo.
Espero con esto soluciones, y como dice el amigazo faktorqm si te srivio la respuesta, cliquea en la medallita del costado.
P.D.: perdon por la mala ortografía!.

---

### Post by guillermolisi on 2008-09-03
Las definiciones de los Shared Folders en VBox las encontras en un archivo de extension xml y las reconoces por el tag. Ejemplo:
```
<SharedFolders>
        <SharedFolder hostPath="/home/guille" name="guille" writable="true"/>
        <SharedFolder hostPath="/media/disk" name="pendrive" writable="true"/>
      </SharedFolders>
```
En las lineas anteriores tengo dos recursos compartidos. Uno que esta en /home/guille y el otro en /media/disk.

Si editas y adecuas las referencias deberia funcionar otra vez.
Fijate que no se mencionan dispositivos sino su nombre a nivel de file system, con lo cual es una ventaja ya que te podes abstraer de los cambios de nominacion como decis que te ha pasado.

En mi caso, el archivo <nombre_de_maquina_virtual>.xml esta en /home/guille/.VirtualBox/Machines/WinXP_SP2 (la maquina se llama WinXP_SP2).

Esto depende de como hayas instalado VBox.

Confirma como te resulto.

---

### Post by pablerque on 2008-09-03
Gracias, hoy a la noche pruebo las soluciones que me dieron y mañana les cuento.

Saludos.

---

### Post by guillermolisi on 2008-09-04
> **pablerque said:**
> Gracias, hoy a la noche pruebo las soluciones que me dieron y mañana les cuento.

Saludos.

Y ?

Como fue ? Anduvo ? Como lo lograste ?

---

### Post by pablerque on 2008-09-05
No, estoy luchando porque se me complico el tema de renombrar la particion, como no quiero preguntar mucho, estoy investigando un poco mas y probando.

---

### Post by guillermolisi on 2008-09-05
> **pablerque said:**
> No, estoy luchando porque se me complico el tema de renombrar la particion, como no quiero preguntar mucho, estoy investigando un poco mas y probando.
Por lo que entendi del problema, dejaria las particiones y todo lo referido a la nueva instalacion tal como quedo y trabajaria sobre el archivo XML que tiene las definiciones de la VM.

Fijate que si lo manejas asi podes abstraerte de que donominacion tiene cada particion, solo importa el punto de montaje del recurso que queres compartir bajo VBox Shared Folders.

En lugar de luchar con un particionador laburas con un editor, cambias un par de cosas (o nada si los puntos de montaje coinciden) y listo.

Es mas, que te parece si posteas aqui el contenido del archivo que contiene las definiciones de la VM, por lo menos las definiciones de Shared Folders, y laburamos sobre algo mas concreto ?

---

### Post by pablerque on 2008-09-08
Muy bien, mañana a primera hora pongo el contenido del archivo que contiene las definiciones de la VM.

Saludos.

pd: perdonen la lentitud de mis respuestas, es que en mi casa no tengo internet asique aprovecho desde el laburo (que tiene xp) asique tardo en probar y responder.

---

### Post by pablerque on 2008-09-09
Bueno, cambie la ruta sobre el archivo xml de la maquina virtual y avance un poco mas.

La maquina intenta reiniciarse del modo suspendido con la cual la deje la ultima vez y aparece el siguiente error:

Failed to restore VM state from '/home/pablerque/.VirtualBox/Machines/Win XP uE v7/Snapshots/{a928c617-7c78-4b41-6894-65f617a51b7e}.sav'.
It may be damaged or from an older version of VirtualBox. Please discard the saved state before starting the virtual machine.
VBox status code: -1829 (VERR_SSM_UNEXPECTED_DATA).

Código Resultado: 
0x80004005
Componente: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


Espero sus comentarios.

Saludos.

---

### Post by guillermolisi on 2008-09-09
> **pablerque said:**
> Bueno, cambie la ruta sobre el archivo xml de la maquina virtual y avance un poco mas.

La maquina intenta reiniciarse del modo suspendido con la cual la deje la ultima vez y aparece el siguiente error:

Failed to restore VM state from '/home/pablerque/.VirtualBox/Machines/Win XP uE v7/Snapshots/{a928c617-7c78-4b41-6894-65f617a51b7e}.sav'.
It may be damaged or from an older version of VirtualBox. Please discard the saved state before starting the virtual machine.
VBox status code: -1829 (VERR_SSM_UNEXPECTED_DATA).

Código Resultado: 
0x80004005
Componente: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


Espero sus comentarios.

Saludos.

Por casualidad, entre tanto, cambiaste/actualizaste la version de VBox ?

Yo no borraria ese archivo. Lo renombraria o copiaria a otro lugar, probaria de iniciar la VM y verificar en que condiciones arranca.

Si esta aceptable, listo, podes seguir adelante usandola.

Si presenta perdida de informacion de acciones recientes y no se pueden volver a reproducir, se me ocurre volver a la version anterior de VBox (si es que la actualizaste), reponer previamente el archivo renombrado/copiado y volver a iniciar la VM.

Si volves a la version anterior de VBox, hacete copia de los archivos que definen la VM con XP, por las dudas, inclusive el que tiene extension .vdi que es el disco de la maquina virtual (en mi caso esta en /home/guille/.VirtualBox/VDI/nombre_de_maquina_virtual.vdi).

Edit: Estaba viendo que lo que guardaste es un snapshot de la VM estando suspendida. Pude ser o estoy errado en mi apreciacion ?

---

### Post by pablerque on 2008-09-09
En realidad no actualice el virtual box, sigo utilizando la misma version de siempre.

Con respecto a tu pregunta sobre un snapshot de la VM estando suspendida, en realidad no estoy seguro. De paso te preguto, Que es un snapshot? Capaz sin querer lo hice.

Voy a realizar lo que me recomendaste: voy a hacer respaldo del la maquina suspendida (vdi) y del archivo de snapshot (sav), y voy a borrar este archivo que esta complicando el arranque y voy a ver que sucede.

Saludos.

---

### Post by guillermolisi on 2008-09-09
> **pablerque said:**
> En realidad no actualice el virtual box, sigo utilizando la misma version de siempre.

Con respecto a tu pregunta sobre un snapshot de la VM estando suspendida, en realidad no estoy seguro. De paso te preguto, Que es un snapshot? Capaz sin querer lo hice.

Voy a realizar lo que me recomendaste: voy a hacer respaldo del la maquina suspendida (vdi) y del archivo de snapshot (sav), y voy a borrar este archivo que esta complicando el arranque y voy a ver que sucede.

Saludos.

El snapshot es una suerte de backup, de copia del estado y contenido de la VM al momento de producirlo, que permitiria volver a un estado anterior luego de haber hecho modificaciones que no te resultaron satisfactorias. En lugar de borrar/desinstalar contenido, restituis la VM al snapshot adecuado y listo.

Por ejemplo, cuando voy a probar algo nuevo, genero un snapshot antes de instalar, pruebo y si no me resulto restituo la VM a su estado inmediato previo como si nada hubiera pasado.

Fijate que hay una solapa que contiene el inventario de snapshots.

Recorda copiar todos los archivos de la VM, asi no te queda "renga" por falta de alguno de ellos (es decir, los xml tambien, ademas) solo por las dudas y aunque parezca innecesario. Despues tendras tiempo de borrar lo que te sobra/este de mas.

---

### Post by pablerque on 2008-09-10
Buenas, por fin logre arrancar el estado suspendido de la maquina virtual.

Al final lo que hice fue reinstalar el ubuntu pero montando /dev/sda4 en /media/sda2 y de esa manera la maquina virtual pudo arrancar.

Lo tuve que hacer reinstalando porque todo el sistema de archivos estaba en /dev/sda2 y no lo podia hacer desmontar manualmente (por suerte tengo el /home en otra particion)

Con respecto al snapshot, probe borrarlo/descartarlo y me aparecian diferentes carteles de errores cuando intentaba arrancar la maquina asique lamentablemnente no lo pude solucionar de esa manera.

De todas maneras estoy muy agradecido por su colaboracion desinteresada.

Saludos.

---

### Post by guillermolisi on 2008-09-10
Bueno, esta solucionado. Lastima todo el rollo de reinstalar..

Considerando que es una VM, la opcion de suspension/hibernacion no la uso. Dejo minimizada la maquina virtual corriendo y listo. En las maquinas que uso no tiene mayor impacto negativo.
De hecho, XP lo inicio solo cuando necesito usarlo, sino esta siempre apagado.

---

### Post by ariel on 2008-09-11
-

---

