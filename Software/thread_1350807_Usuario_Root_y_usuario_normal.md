---
title: "Usuario Root y usuario normal"
date: 2009-12-09
forum: Software
---

### Post by aledruetta on 2009-12-09
Hola Comunidad!

Estoy intentando entender lo siguiente:

Cuando uno instala Ubuntu, lo hace con un nombre de usuario al cual le asigna una contraseña. Ese usuario no es usuario root, pero puede usar su contraseña por medio de sudo para realizar cualquier tarea administrativa. 

La cuenta root viene desactivada por defecto para preservar la seguridad del equipo.

Bien. Entonces, lo que quiero es activar la cuenta root y quitarle los privilegios administrativos al usuario normal para que cualquiera que use el equipo bajo ese usuario no pueda usar la contraseña para realizar... desastres.

Para activar la cuenta root:
```
sudo passwd root
```
Coloco la seña del usuario normal, y a continuación la nueva seña que será la seña root.

Luego, voy a Sistema --> Administración --> Usuarios y Grupos, y al usuario normal le quito los privilegios de administración. Me fijo que no forme parte de los grupos "adm", "admin".
Haciendo:
```
groups usuario
```
Me devuelve:
```
usuario : usuario dialout cdrom plugdev lpadmin sambashare
```

Eso fui haciendo siguiendo mi lógica (que muchas veces a demostrado no ser la lógica de Ubuntu)

El problema es el siguiente:

Cuando ejecuto alguna aplicación que requiere de privilegios de administración, si coloco la contraseña del usuario común, lógicamente, no me lo acepta; pero tampoco me acepta la contraseña de root.

¿Qué hago entonces? ¿Solamente saliendo de la cuenta y entrando en root puedo hacerlo?

---

### Post by biale on 2009-12-09
Encuentro que la logica de Ubuntu esta demasiado preparada como para que el usuario "1000" "no" se toque.

Lo mas sencillo es directamente crear usando la GUI un segundo usuario y que este nuevo usuario (por ejemplo) no sea "sudoer". La computadora de casa tiene en este momento 4 usuarios definidos y solo uno administra.

Si alguno de esos usuarios necesita hacer algo especial, modifico el archivo sudoers lo estrictamente necesario. Ejemplo: arrancar firestarter

Y si queres administrar (solo administrar) usando la cuenta de root en modo muy espartano, no hay inconvenientes en hacerlo.

Saludos

---

### Post by aledruetta on 2009-12-09
> **biale said:**
> Encuentro que la logica de Ubuntu esta demasiado preparada como para que el usuario "1000" "no" se toque.

Lo mas sencillo es directamente crear usando la GUI un segundo usuario y que este nuevo usuario (por ejemplo) no sea "sudoer". La computadora de casa tiene en este momento 4 usuarios definidos y solo uno administra.

Si alguno de esos usuarios necesita hacer algo especial, modifico el archivo sudoers lo estrictamente necesario. Ejemplo: arrancar firestarter

Y si queres administrar (solo administrar) usando la cuenta de root en modo muy espartano, no hay inconvenientes en hacerlo.

Saludos

Entiendo el punto de vista, pero el problema es que yo necesito compartir mi usuario. Lo que yo pretendía es dejar el usuario sin privilegios y ver alguna forma de realizar las tareas delicadas usando la contraseña de root, pero sin salir de la sesión del usuario común.

Pero bueno, a veces uno quiere cosas que no se pueden... ¿no se puede? ¿no hay algún método? Por ejemplo, si a un administrador de sistemas de una empresa, el contador le pide que le habilite tal o cual cosa, el tipo ¿cierra la sesión del contador, abre la de root o la administrativa, modifica lo que tiene que modificar y vuelve a la sesión del contador? ¿No tiene otra opción?

---

### Post by gmunioz on 2009-12-09
Hola ale.....:

En GnuLinux en general y en Ubuntu en particular todo se puede.

Para habilitar el usuario root en sesiones gráficas 

Editar el archivo /etc/gdm/gdm.conf, en una consola ejecutas

sudo gedit /etc/gdm/gdm.conf

Busca la línea que dice 

AllowRoot=false

La cambias por

AllowRoot=true

Guarda el archivo.

Cierra gedit

Establece la contraseña de root

sudo passwd root

Reinicia GDM

sudo /etc/init.d/gdm restart

Logueate como root

Administra el sistema con muchísimo cuidado, no

navegues como root, y que la contraseña no sea
1234, admin, r44t, r00t, ni ale.

---

### Post by sebastianabate on 2009-12-09
Podés usar gksu con el modificador -u que especifica el usuario con el que querés ejecutar el comando. Apretás alt+F2 y escribís

```
gksu -u root /usr/bin/comando_a_ejecutar
```te va a pedir una contraseña y ponés la de root.

La otra forma de hacer lo que necesitás es ejecutar los comandos administrativos desde una terminal previo cambio al usuario root. Desde una terminal ejecutás.

```
su root
```y cuando te pide la contraseña tenés que poner la contraseña de root que ya seteaste previamente. A partir de ese momento vas a ver que el prompt de la terminal cambia el $ por el #

```
usuario@nombre_de-PC:~$ su root
``````
root@nombre_de_PC:~#
```esto quiere decir que todo lo que ejecutes desde esa terminal lo ejecutás como root. Entonces podés ejecutar cualquier comando administrativo que necesites sin problemas. Por ejemplo podés ejecutar

```
root@nombre_de_PC:~#/usr/bin/software-center
```y va a arrancar el nuevo "Ubuntu Software Center" para poder instalar cualquier aplicación; o

```
root@nombre_de_PC:~#/usr/bin/time-admin
```y te va a permitir cambiar la hora y la fecha del sistema sin que necesites desbloquear la aplicación.

---

### Post by aledruetta on 2009-12-10
Gracias Gabriel y Sebastián!

El método "su root" funciona. Pero el método "gksu -u root", no. Me abre una ventana donde pide que introduzca la contraseña para realizar tareas administrativas. Si coloco la de root, dice que la contraseña está errada (y no está errada); si coloco la del usuario común, dice que el usuario no está autorizado.
```
No se pudo ejecutar /usr/sbin/gparted como usuario root.

 El mecanismo de autorización subyacente (sudo) no le permite ejecutar este programa. Contacte con el administrador del sistema.
```
¿Qué estoy haciendo mal?

---

### Post by sebastianabate on 2009-12-10
A lo mejor tu problema tiene que ver con la modificación que hiciste del usuario 1000 (el que creás durante la instalación). Probá esto: en una terminal pasate a root (con su root) y ejecutá

```
gksu-properties
```

se abre un cuadro donde podés elegir el método de autenticación de gksu, cambiá sudo por su, cerrá el cuadro de diálogo y volvé a probar el comando gksu.

---

### Post by aledruetta on 2009-12-10
Gracias Sebastián, pero ya tenía "su" como valor... Debe ser alguna otra cosa...

---

### Post by aledruetta on 2009-12-10
Bueno, y algo que no sé si tendrá que ver. Cuando ejecuto "gksu -u root comando", sale:
```
root@karmic-laptop:/home/aled# gksu-properties
Falló en GConf: Falló al contactar con el servidor de configuraciones; algunas de las posibles causas son que necesite activar TCP/IP en ORBit, o que tiene bloqueos de NFS debidos a una caída de sistema. Consulte http://www.gnome.org/projects/gconf/ para más información. (Detalles -  1: Falló al obtener la conexión con la sesión: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

```
El mensaje está repetido varias veces.

---

### Post by aledruetta on 2009-12-10
Creo que lo solucioné!!!

Es como dice Sebastián, pero no hay que entrar como root (con "su root") hay que ejecutar "gksu-properties" como usuario común y corriente, y ahí sí, cambiar "sudo" por "su".

Ahora si hago click en cualquier aplicación del menú de Administración, me pide la contraseña de root, si coloco la del usuario común, simplemente se cierra y no pasa nada.

La única duda que me queda es lo del mensaje de error de Gconf ¿Qué será? ¿Abro otro hilo?

---

### Post by guillermolisi on 2009-12-10
> **aledruetta said:**
> 
La única duda que me queda es lo del mensaje de error de Gconf ¿Qué será? ¿Abro otro hilo?
Sin duda es algo para otro thread.

---

### Post by EGKaltenmeier on 2010-05-31
Perdonen que me meta, pero también tengo algunas preguntas sobre la super-cuenta de root. Tengo un ubuntu separado de todo que quería usar para probarlo y destrozarlo si es necesario, reinstalo y listo, no hay drama. Quería hacer cosas tan inocentes como cambiarle la música de inicio, o instalar un controlador que tenía en el ubuntu de uso sin tener que descargarlo de internet. Pero resulta que la única carpeta en la que puedo hacer algo es en home. Leí los posteos previos, pero pasa que además soy absolutamente novato y ni idea tengo de cómo manejar las terminales. Alguno puede darme una breve noción de cómo hacer? O si ya hay tutorial en el foro, me lo indican? Saludos Gracias

---

### Post by Trupus on 2011-02-09
Llevo como un mes usando Ubuntu, mi intensión es entender la introducción a su funcionamiento y luego usar Ubuntu Server. Pero me tienen mareados los permisos de root. 
Considero que esta discución sirve muuucho. Gracias!

---

