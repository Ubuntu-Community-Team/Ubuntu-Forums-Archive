---
title: "ayuda para remover ubuntu"
date: 2008-10-27
forum: Software
---

### Post by julianch89 on 2008-10-27
hola a todos ,paso a contarles mi problema , yo antes tenia windows en la maquina , con una sola particion , osea toda de windows , dps instale ubuntu y le puse la mitad del disco de mi maquina a ubuntu , ahora la compu se la tengo que pasar a mi viejo y mi viejo no va a usar ubuntu , por eso necesito de su ayuda para decirme bien los pasos para desinstalar ubuntu y volver a la unica particion que tenia con windows. desde ya muchas gracias , el que me pueda ayudar viene bien :P .

---

### Post by vampichoke on 2008-10-27
si tus archivos ya los resguardaste o pasaste y nomas queres asesinar a ubuntu...

desde windows. partition magic... suprimi la particion (formateala y crea una en el hueco q queda q sea ntfs. y listo). 

no hagas todo 1 sola ya q tenes el espacio dejalo pero para win como un disco para DATOS. por las dudas q win te traicione como simpre =)

ubuntu style:
corre el live cd. y con el editor de particiones lo mismo. suprimis la particion, creas una nueva en ntfs o... podes estirar la de win.. q no lo recomiendo =/

---

### Post by Kantier on 2008-10-27
idem vampichoke. ya que tenés una partición separada de la que usa windows, usala para guardar cosas (documentos, música, etc.) ahi así cuando el malvado te traiciona te salvás.

---

### Post by atatiducken on 2008-10-28
guarda que al borrar ubuntu desde win, al reiniciar la proxima vez podria querer iniciar el grub y al no encontrar ubuntu se quedaria dura sin hacer nada, por lo menos a mi me paso en la maq de un amigo :(

---

### Post by santiagoward2000 on 2008-10-28
> **atatiducken said:**
> guarda que al borrar ubuntu desde win, al reiniciar la proxima vez podria querer iniciar el grub y al no encontrar ubuntu se quedaria dura sin hacer nada, por lo menos a mi me paso en la maq de un amigo :(

Seguramente va a pasar eso (excepto a que hallas instalado el GRUB en otro lado y sigas usando el arranque de Windows). Para arreglarlo, ponés el CD de Windows, arrancás el instalador, y cuando te pregunta qué querés hacer seleccionás reparar instalación. (Aunque por alguna razón la vez que quise hacerlo no me anduvo).
Suerte!

---

### Post by EnriqueK on 2008-10-28
Descarga el Super Grub Disk , con el elige la opción de "arreglar el arranque de windows o algo así , esto mata al grub y pone el gestor de arranque de windows, luego entrando a windows usa el partition magic o similares y formatea la partición de Ubuntu, un consejo, deja esa partición independiente, no la unas a la de windows.

---

### Post by faktorqm on 2008-10-28
Lo mas facil es

1.Arrancas desde el CD de instalación de win.
2.Cuando te lo pida apreta la letra "R" (consola de recuperacion)
3.Seleccionas la instalación de win (generalmente opción 1).
4.Escribis: FIXMBR y apretas Enter. Esto restaura el MBR para que arranque win.

Salu2!

---

### Post by julianch89 on 2008-10-29
gracias por las respuestas ...como no tengo el cd de instalacion de windows .. me voy a bajar el super grub disk y le voy a poner que arranque windows y dps formateo la particion de ubuntu , igual no se preocupen es por q se la paso la maquina a mi viejo , ya voy a volver con ubuntu :P jaja ... como no tengo internet en mi casa me voy a ir fijando como me va .. y voy posteando cualquier problema .. gracia

---

### Post by EnriqueK on 2008-10-29
Antes de borrarlo podés usar Remastersys y así creas un Live DVD de la actual instalación y así la instalas en el equipo de tu casa. 
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by c4d0rn4 on 2008-10-29
Al fin dios escuchó mis plegarias! En algunos días me pongo a probar Remastersys, Si anda ya a va ser una GRAN ayuda, pero necesito correr el "live dvd custom" desde un pendrive y eso si sería la frutilla del postre.

Aunque tengo la mala sensación que no va a entrar en 2gigas (mi pendrive) ¬¬

---

### Post by EnriqueK on 2008-10-29
> **c4d0rn4 said:**
> Al fin dios escuchó mis plegarias! En algunos días me pongo a probar Remastersys, Si anda ya a va ser una GRAN ayuda, pero necesito correr el "live dvd custom" desde un pendrive y eso si sería la frutilla del postre.


Hace  un tiempo hice el siguiente experimento con todo éxito
1.- Creo un Live DVD de mi instalación con Remasrtersys sin datos personales, o sea que no tenga mi carpeta de usuario.
2.- Formateo mi pendrive en EXT3 y allí grabo una copia de mi carpeta personal
3.- Arranco el Live DVD y lógicamente no contiene mis datos personales ni mis configuraciones, creo un nuevo usuario con el nombre de mi carpeta personal y mi contraseña.
4.- Hago sudo nautilus entro al /home y borro la carpeta del nuevo usuario y en este mimo lugar hago un enlace simbólico a mi carpeta de usuario que grabé anteriormente en mi memoria flash usb , cierro todas las ventanas abiertas y cambio de usuario , el sistema arranca con mi configuración y datos personales y puedo seguir guardando archivos y modificar configuraciones que no se borrarán por que serán almacenados en el pendrive.
Resumiendo, esta sería tal vez una  alternativa a tener toda una instalación en USB, tal vez sea mejor por que en la USB solo tendrías la carpeta de usuario y no todo el sistema.

---

