---
title: "Is Ubuntu supposed  to be reliable? i dont think so"
date: 2012-10-02
forum: Testimonials &amp; Experiences
---

### Post by dioxholster on 2012-10-02
Crashes more than 3 times a day and everytime i log in the mouse curser freezes in its place until i ctrl alt f1 and back. What happened? its total meltdown and i only use the OS for surfing and on other thing, the unity dash displays files in its menu that i dont want it displayed! and the privacy settings dont work one bit. Now that i think of it, nothing really works. Firefox is a mess, Ubuntu One doesnt even open, Sound is f'ed and I had to do a workaround for it to not stutter, but apparently that workaround ruined the mic or something I cant even bother. If i format this system Im afraid i'll switch back to windows, it never gave me such a headache, its only crime is that it might be a tad slower. Having said that I need help about this, whats causing these crashes that usually occur when im in firefox? Java and Flash seem to be a problem and get error messages something about xml or whatever.

---

### Post by QIII on 2012-10-02
"Everything is broken" is hard to diagnose and solve.

Pick one thing at a time.  Laundry lists often cause people to move on.


This is from my straight up Ubuntu machine that I use for scientific research programs.  Reliable?  I think so.  It only goes down for kernel updates.

```

xxxxxx@xxxxxx:~$ uptime
20:23:54 up 10 days, 22:13,  1 user,  load average: 2.92, 2.84, 2.88

```

---

### Post by vasa1 on 2012-10-02
You'll have to give details: 
Ubuntu OS name and version
computer specs including CPU and RAM
Wubi install or dual-boot, etc, etc, etc

---

### Post by jeis on 2012-10-02
Introducción:
Ubuntu es un sistema operativo, que es mantenido por una empresa llamada canonical, además de la comunidad de programadores, dicho sistema utiliza un núcleo en Linux, y su origen está basado en debían, dicho sistema está orientado al usuario novel y promedio, enfocado en la facilidad de uso y mejora de experiencia del usuario, en este ensayo describiremos un poco más sobre la administración de dicho sistema.
Desarrollo:
Interfaz grafica.
Localización: Sistema > Administración > Usuarios y Grupos
Para añadir un usuario nuevo
Presiona + Añadir Usuario, esto abrirá Editor de Cuentas de Usuario. Los requisitos mínimos son el Nombre de usuario y la contraseña (automáticamente generada o a mano). Para el nombre de usuario, no uses espacios ni caracteres ASCII. En la pestaña Privilegios de Usuario, añade los privilegios a los que el nuevo usuario tendrá acceso, como por ejemplo usar dispositivos de audio. Opcionalmente puedes especificar o modificar el nombre real, la ubicación de la oficina, el teléfono de trabajo, el teléfono de casa, el grupo principal, la shell usada, el directorio personal, el ID de usuario y una lista de los grupos secundarios para el usuario.
El grupo principal, la shell usada, el directorio personal y el ID de usuario se adivinan automáticamente dependiendo del perfil seleccionado.
Para modificar un usuario existente
Selecciona el usuario que quieres modificar y pulsa el botón Propiedades. Aparecerá una ventana similar a la usada para añadir usuarios nuevos, con todos los datos del usuario, permitiéndote modificarlos.
Para borrar un usuario existente
Selecciona el usuario o usuarios que quieres borrar y pulsa el botón Borrar en la pestaña Usuarios, debido a la importancia de estos datos, se te pedirá confirmación para cada usuario que quieras borrar.
Por razones de seguridad, el directorio personal de los usuarios borrados no se borrará.
Para añadir un grupo nuevo&#8195;
Pulsa el botón Añadir en el diálogo de grupos, aparecerá una ventana nueva pidiendo los datos del grupo nuevo. Para añadir un grupo nuevo, debes proporcionar al menos el nombre del grupo y el ID del grupo. Opcionalmente puedes especificar los usuarios que pertenecerán a este grupo.
Para modificar un grupo existente&#8195;
Selecciona el grupo que quieres modificar en el diálogo de grupos y pulse el botón Propiedades. A continuación a aparecerá una ventana con los datos del grupo permitiéndote modificarlos.
Para borrar un grupo existente
Selecciona el grupo o grupos que quieres borrar en el diálogo de grupos y pulsa el botón Borrar en la solapa Grupos, debido a la importancia de estos datos, se te pedirá confirmación para cada grupo que quieras borrar.
Ficheros relacionados con la gestión de usuarios y grupos
Algunos ficheros relacionados con las cuentas de usuario son:
/etc/passwd: contiene información sobre cada usuario: ID, grupo principal, descripción, directorio de inicio, shell, etc. También contiene el password encriptado, salvo que se usen shadow passwords.
/etc/shadow: contiene los passwords encriptados de los usuarios cuando se emplean shadow passwords.
/etc/group: contiene los miembros de cada grupo, excepto para el grupo principal, que aparece en /etc/passwd.
/etc/skel: directorio que contiene el contenido del directorio de los nuevos usuarios.
Algunos grupos especiales
En el sistema existen algunos grupos especiales que sirven para controlar el acceso de los usuarios a distintos dispositivos. El control se consigue mediante los permisos adecuados a ficheros de dispositivo situados en /dev. Algunos de estos grupos son:
cdrom: dispositivos de CD–ROM. El dispositivo concreto afectado depende de donde estén conectadas las unidades de CD–ROM. Por ejemplo, /dev/hdc.
floppy: unidades de diskette, por ejemplo, /dev/fd0
dialout: puertos serie. Afecta, por ejemplo, a los modems externos conectados al sistema. Por ejemplo, /dev/ttyS1
Audio: controla el acceso a dispositivos relacionados con la tarjeta de sonido. Por ejemplo, /dev/dsp, /dev/mixer y /dev/sndstat.

Conclusión:
Ubuntu es relativamente fácil, solo es cuestión de saber un poco de los códigos principales de Ubuntu o Linux y es más que suficiente, hay muchos foros de ayuda, donde mucha gente se junta para ayudar en los problemas que tengas con dichos sistemas.

---

### Post by oldfred on 2012-10-02
@jeis Welcome to the forums. 
But we are an English speaking forum and not many will understand your post including me. 

Several Spanish sub-forums:
[http://ubuntuforums.org/forumdisplay.php?f=183](http://ubuntuforums.org/forumdisplay.php?f=183)

---

### Post by dioxholster on 2012-10-03
if these problems arent common then i dont expect a solution, linux is like a public toilet of code, no way to find the origin of the problem. I use asus netbook, as i will never trust linux on my pc, the netbook is one of those 1005pe or something close, it has 1GB ram which is slow but works fine when ubuntu chooses to work.

---

### Post by QIII on 2012-10-03
Are you actually interested in getting assistance?

---

### Post by cariboo on 2012-10-03
Moved to T&E, and closed, as this is a rant, and not a support question.

---

