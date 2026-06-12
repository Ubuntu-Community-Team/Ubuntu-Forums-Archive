---
title: "Desaparecio Kubuntu lucid Lynx"
date: 2010-05-21
forum: Software
---

### Post by matias_tati on 2010-05-21
Hola bueno les acerco esto que me paso:
Estaba chateando con Kmess, Navegando con Google Chrome y de repente se tildo la pc. a lo que presione ctrl+alt+supr y me abrio el menu para cerrar sesion a lo que puse que si, mientras se estaba cerrando vi que la pc volvio a responder asi que cancele el cierre de sesion, de todas formas se reinicio y que veo cuando vuelve a iniciar? OOppsss`es GNOME???? Que paso?
Una captura.

[[img]http://a.imagehost.org/t/0167/instant_nea8.jpg[/img]](http://a.imagehost.org/view/0167/instant_nea8)


Debo reinstalar? Justo cuando me empezaba a gustar KDE...

Gracias

---

### Post by matias_tati on 2010-05-22
Mi unica opcion es reistalar entonces? eso me suena a Bill Gates.

---

### Post by guillermolisi on 2010-05-22
Mmmm ... hablas de Kubuntu pero inicia Gnome ... en realidad tenes dual boot (Ubuntu - Kubuntu) o los dos escritorios graficos en una sola instalacion de Ubuntu ?

---

### Post by matias_tati on 2010-05-26
> **guillermolisi said:**
> Mmmm ... hablas de Kubuntu pero inicia Gnome ... en realidad tenes dual boot (Ubuntu - Kubuntu) o los dos escritorios graficos en una sola instalacion de Ubuntu ?

Reinstale y me volvio a pasar lo mismo.
No, solo instale Kubuntu Lucid. Y en un momento reinicio y se me va el entorno KDE pero me queda con todas sus aplicaciones.

[[img]http://h.imagehost.org/t/0839/instant_nea1.jpg[/img]](http://h.imagehost.org/view/0839/instant_nea1)

---

### Post by alfplayer on 2010-05-26
No conozco Kubuntu, pero obviamente Gnome está instalado. El error cargando la miniaplicación es muy común y no es grave.

Dos cosas para chequear: qué escritorio carga el display manager (la pantalla de inicio de sesión), y si el display manager es el mismo. Si Kubuntu usa KDM, se pudo cambiar a otro como GDM.

---

### Post by guillermolisi on 2010-05-26
Si, sin duda Gnome esta instalado y se carga al iniciar la sesion.

Habria que ver a que llamas "reinstalar" y, lo mas importante, como llegaste a tener Kubuntu en esa maquina porque creo que ahi esta la clave.

---

### Post by matias_tati on 2010-05-26
> **guillermolisi said:**
> Si, sin duda Gnome esta instalado y se carga al iniciar la sesion.

Habria que ver a que llamas "reinstalar" y, lo mas importante, como llegaste a tener Kubuntu en esa maquina porque creo que ahi esta la clave.

Borre la particion asi que empeze de cero nuevamente bajeel cd de Kubuntu y cree una particion y lo volvi a instalar. Puede ser que me aparezca eso por instalar alguna aplicacion de Gnome? La verdad estoy perdido.

---

### Post by guillermolisi on 2010-05-26
> **matias_tati said:**
> Borre la particion asi que empeze de cero nuevamente bajeel cd de Kubuntu y cree una particion y lo volvi a instalar. Puede ser que me aparezca eso por instalar alguna aplicacion de Gnome? La verdad estoy perdido.
Si la aplicacion se empaqueto con Gnome-Desktop, instalaste Gnome.

Tango varias aplicaciones de Gnome en uso con Kubuntu y nunca me ha pasado tal cosa.

---

### Post by matias_tati on 2010-05-27
No instale Gnome instale KDE..........No me aparece asi de una arrancaba bien con KDE hasta que un dia reinicio y me aparece esto:...

Es la segunda vez seguida que me pasa, que es recomendable en este caso?

---

### Post by guillermolisi on 2010-05-28
Si instalas un paquete que fue vinculado con Gnome-desktop como requerido, al instalar ese paquete tambien estaras instalando Gnome como escritorio. Ahora se entiende a que me refiero ?

Quedo claro que no instalaste Gnome voluntariamente y tambien que Gnome no aparece automagicamente si instalas Kubuntu.

Revisaria que paquetes de Gnome tenes instalados. De todas formas eso no explica porque no se activa KDE.

Que pasa si en una consola/terminal ingresas ```
sudo /etc/init.d/kdm start
```

---

### Post by matias_tati on 2010-05-29
```
matias@matias-desktop:~$ sudo /etc/init.d/kdm start
[sudo] password for matias: 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service kdm start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start kdm
matias@matias-desktop:~$ 

```

---

### Post by guillermolisi on 2010-05-29
> **matias_tati said:**
> ```
matias@matias-desktop:~$ sudo /etc/init.d/kdm start
[sudo] password for matias: 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service kdm start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start kdm
matias@matias-desktop:~$ 

```
Bueno, y probaste lo que recomienda el mensaje ? (start kdm)

---

### Post by matias_tati on 2010-05-30
```
matias@matias-desktop:~$ start kdm
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.34" (uid=1000 pid=1509 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
matias@matias-desktop:~$ 


```

---

### Post by guillermolisi on 2010-05-30
> **matias_tati said:**
> ```
matias@matias-desktop:~$ start kdm
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.34" (uid=1000 pid=1509 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
matias@matias-desktop:~$ 


```
Verifica que exista kdm ```
ls -al /etc/init.d/kdm

``` que te deberia dar una salida como ```
lrwxrwxrwx 1 root root 21 2010-05-05 23:24 /etc/init.d/kdm -> /lib/init/upstart-job
``` y si verifica corre ```
sudo start kdm
``` Si no verifica la existencia de /etc/init.d/kdm el tema es mas complejo y casi te diria que da para reinstalar KDE-desktop.

Edit: Tambien podes verificar la existencia de los paquetes de KDE con Synaptic y/o Aptitude

---

### Post by matias_tati on 2010-05-30
```
matias@matias-desktop:~$ ls -al /etc/init.d/kdm
lrwxrwxrwx 1 root root 21 2010-05-24 14:09 /etc/init.d/kdm -> /lib/init/upstart-job
matias@matias-desktop:~$ sudo start kdm
[sudo] password for matias: 
start: Job is already running: kdm
matias@matias-desktop:~$ 

```

---

### Post by guillermolisi on 2010-05-30
> **matias_tati said:**
> ```
matias@matias-desktop:~$ ls -al /etc/init.d/kdm
lrwxrwxrwx 1 root root 21 2010-05-24 14:09 /etc/init.d/kdm -> /lib/init/upstart-job
matias@matias-desktop:~$ sudo start kdm
[sudo] password for matias: 
start: Job is already running: kdm
matias@matias-desktop:~$ 

```
Ok, Buenisimo, ahora probaria de reiniciar KDM ```
sudo restart kdm
```a ver que efecto produce.

Antes, cerra la sesion de Gnome y mejor si podes parar GDM ```
sudo stop gdm
``` El reinicio de KDM lo tendras que hacer via una consola.

Si KDM no aparece, me fijaria en /var/log/dmesg a ver que anotaciones se produjeron ademas del feedback que te dara la operacion en linea de comando en consola.

---

### Post by matias_tati on 2010-05-30
Wow que pavada que era...... cerre la sesion gnome y en la pantalla de login fue tan facil como seleccionar que iniciara con KDE, lo que no se es porque se inicializaba Gnome si no cambie nada. Bueno Muchas gracias.

---

